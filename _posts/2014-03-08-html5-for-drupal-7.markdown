title: HTML5 for Drupal 7
tags:
  - Drupal
  - PHP
id: 70
categories:
  - Development
date: 2014-03-08 14:22:23
---

<span style="line-height: 1.5;">Relatively recently it was announced that [Drupal is running on more than a million websites](https://drupal.org/project/usage/drupal). The office where I work is quite fond of Drupal, though it has some problems and one of them is HTML validation. </span>Drupal 7 is using XHTML+RDFa by default, though at this point lots of us prefer HTML5 and unfortunately changing this is not a straight forward task. Surprisingly even Drupal.org [did not manage to fix all validation errors](http://validator.w3.org/check?uri=https%3A%2F%2Fdrupal.org%2F&amp;charset=%28detect+automatically%29&amp;doctype=Inline&amp;group=0) after switching to HTML5\. So here's a tutorial to fix this, based on [W3C Validation for Drupal 7 HTML5 + RDFa](http://www.phase2technology.com/blog/w3c-validation-for-drupal-7-html5-rdfa/ "Permalink to W3C Validation for Drupal 7 HTML5 + RDFa") with few improvements.<!--more-->

## Fixing HTML5 markup for Drupal 7

First of all you have to make changes to _html.tpl.php_ file, basically you should change only 3 lines (doctype, html, head):
<pre>&lt;!DOCTYPE html&gt;
&lt;html xmlns="http://www.w3.org/1999/xhtml" xml:lang="&lt;?php print $language-&gt;language; ?&gt;" lang="&lt;?php print $language-&gt;language; ?&gt;" dir="&lt;?php print $language-&gt;dir; ?&gt;" &lt;?php print $rdf_namespaces; ?&gt;&gt;
&lt;head&gt;
....
&lt;/head&gt;</pre>
In addition to this, you have to add a few functions to your _template.php_ file. The main purpose of the code below code is to convert the XHTML syntax (xmlns:name=”http://url”) into HTML5 (prefix=”name: url …”) syntax.
<pre>/**
 * Implements hook_preprocess_html()
 */
function themename_preprocess_html(&amp;$vars) {
  $prefixes = array();
  $namespaces = explode("\n", trim($vars['rdf_namespaces']));
  foreach ($namespaces as $name) {
    list($key,$url) = explode('=', $name, 2);
    list($xml,$space) = explode(':',$key, 2);
    $url = trim($url, '"');
    if (!empty($space) &amp;&amp; !empty($url)) {
      $prefixes[] = $space . ': ' . $url;
    }
  }
  $prefix = implode(" ", $prefixes);
  $vars['rdf_namespaces'] = 'prefix="' . $prefix . '"';
}</pre>
RDF Extensions module sometimes generates blank attributes which cause validation errors, the code below will fix this:
<pre>/**
 * Implements hook_preprocess_node()
 */
function themename_preprocess_node(&amp;$vars) {
  foreach($vars['title_attributes_array'] as $key =&gt; $value) {
    if(empty($value)) {
      unset($vars['title_attributes_array'][$key]);
    }
  }
}</pre>
Another problem is with entities, Drupal sometimes generates duplicate "classes" and empty "typeof" attributes. The code below merges classes arrays into one, removes duplicate and empty attributes.
<pre>/**
 * Implements hook_preprocess_entity()
 */
function themename_preprocess_entity(&amp;$vars) {
  if (!empty($vars['classes_array']) &amp;&amp; !empty($vars['attributes_array']['class'])) {
    $vars['classes_array'] = array_merge($vars['classes_array'], $vars['attributes_array']['class']);
    unset($vars['attributes_array']['class']);
  }
  foreach($vars['attributes_array'] as $key =&gt; $value) {
    if(empty($value)) {
      unset($vars['attributes_array'][$key]);
    }
  }
}</pre>
Check with [W3 Validator](http://validator.w3.org/) and you should be all set.

### Conclusions

You might run into other markup issues depending upon what other Drupal modules you are using. In most cases you can solve those issues via similar pre-processing tricks. Hopefully [Drupal 8](https://drupal.org/drupal-8.0) will generate HTML5 markup out of the box with other great features.