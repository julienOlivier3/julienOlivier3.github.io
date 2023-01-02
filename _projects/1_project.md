---
layout: page
title: x-language coding
description: A simple demonstration of using Python and R syntax within the same script using Quarto.
img: assets/img/quarto.png
importance: 1
category: fun
---


<html xmlns="http://www.w3.org/1999/xhtml" lang="en" xml:lang="en"><head>

<meta charset="utf-8">
<meta name="generator" content="quarto-1.1.149">

<meta name="viewport" content="width=device-width, initial-scale=1.0, user-scalable=yes">

<meta name="author" content="Julian Oliver Dörr">

<title>Hello, Quarto</title>
<style>
code{white-space: pre-wrap;}
span.smallcaps{font-variant: small-caps;}
div.columns{display: flex; gap: min(4vw, 1.5em);}
div.column{flex: auto; overflow-x: auto;}
div.hanging-indent{margin-left: 1.5em; text-indent: -1.5em;}
ul.task-list{list-style: none;}
ul.task-list li input[type="checkbox"] {
  width: 0.8em;
  margin: 0 0.8em 0.2em -1.6em;
  vertical-align: middle;
}
pre > code.sourceCode { white-space: pre; position: relative; }
pre > code.sourceCode > span { display: inline-block; line-height: 1.25; }
pre > code.sourceCode > span:empty { height: 1.2em; }
.sourceCode { overflow: visible; }
code.sourceCode > span { color: inherit; text-decoration: inherit; }
div.sourceCode { margin: 1em 0; }
pre.sourceCode { margin: 0; }
@media screen {
div.sourceCode { overflow: auto; }
}
@media print {
pre > code.sourceCode { white-space: pre-wrap; }
pre > code.sourceCode > span { text-indent: -5em; padding-left: 5em; }
}
pre.numberSource code
  { counter-reset: source-line 0; }
pre.numberSource code > span
  { position: relative; left: -4em; counter-increment: source-line; }
pre.numberSource code > span > a:first-child::before
  { content: counter(source-line);
    position: relative; left: -1em; text-align: right; vertical-align: baseline;
    border: none; display: inline-block;
    -webkit-touch-callout: none; -webkit-user-select: none;
    -khtml-user-select: none; -moz-user-select: none;
    -ms-user-select: none; user-select: none;
    padding: 0 4px; width: 4em;
    color: #aaaaaa;
  }
pre.numberSource { margin-left: 3em; border-left: 1px solid #aaaaaa;  padding-left: 4px; }
div.sourceCode
  {   }
@media screen {
pre > code.sourceCode > span > a:first-child::before { text-decoration: underline; }
}
code span.al { color: #ff0000; font-weight: bold; } /* Alert */
code span.an { color: #60a0b0; font-weight: bold; font-style: italic; } /* Annotation */
code span.at { color: #7d9029; } /* Attribute */
code span.bn { color: #40a070; } /* BaseN */
code span.bu { color: #008000; } /* BuiltIn */
code span.cf { color: #007020; font-weight: bold; } /* ControlFlow */
code span.ch { color: #4070a0; } /* Char */
code span.cn { color: #880000; } /* Constant */
code span.co { color: #60a0b0; font-style: italic; } /* Comment */
code span.cv { color: #60a0b0; font-weight: bold; font-style: italic; } /* CommentVar */
code span.do { color: #ba2121; font-style: italic; } /* Documentation */
code span.dt { color: #902000; } /* DataType */
code span.dv { color: #40a070; } /* DecVal */
code span.er { color: #ff0000; font-weight: bold; } /* Error */
code span.ex { } /* Extension */
code span.fl { color: #40a070; } /* Float */
code span.fu { color: #06287e; } /* Function */
code span.im { color: #008000; font-weight: bold; } /* Import */
code span.in { color: #60a0b0; font-weight: bold; font-style: italic; } /* Information */
code span.kw { color: #007020; font-weight: bold; } /* Keyword */
code span.op { color: #666666; } /* Operator */
code span.ot { color: #007020; } /* Other */
code span.pp { color: #bc7a00; } /* Preprocessor */
code span.sc { color: #4070a0; } /* SpecialChar */
code span.ss { color: #bb6688; } /* SpecialString */
code span.st { color: #4070a0; } /* String */
code span.va { color: #19177c; } /* Variable */
code span.vs { color: #4070a0; } /* VerbatimString */
code span.wa { color: #60a0b0; font-weight: bold; font-style: italic; } /* Warning */
</style>





</head>

<body class="fullcontent">

<div id="quarto-content" class="page-columns page-rows-contents page-layout-article">

<main class="content" id="quarto-document-content">





<div class="quarto-title-meta">
    <div class="quarto-title-meta-heading">Author</div>
    <div class="quarto-title-meta-contents">
             <p>Julian Oliver Dörr </p>
    </div>
</div>
  



<section id="quarto" class="level2">
<h2 class="anchored" data-anchor-id="quarto">Quarto</h2>
<p><a href="https://quarto.org/">Quarto</a> weaves together narrative text and code to produce elegantly formatted output. Most interestingly, Quarto executes code written in different languages. The following gives an illustration of cross-language coding in Quarto (here using <strong><code>R</code></strong> and <strong><code>Python</code></strong> - other languages, e.g. Julia, are supported as well).</p>
</section>
<section id="cross-language-coding" class="level2">
<h2 class="anchored" data-anchor-id="cross-language-coding">Cross-language coding</h2>
<section id="r" class="level3">
<h4 class="anchored" data-anchor-id="r">R</h4>
<p><strong><code>R</code></strong> code chunks are written and executed just as we would do it in R Markdown. So, for users of R Markdown this should be very familiar.</p>
<div class="cell">
<div class="sourceCode cell-code" id="cb1"><pre class="sourceCode r code-with-copy"><code class="sourceCode r"><span id="cb1-1"><a href="#cb1-1" aria-hidden="true" tabindex="-1"></a><span class="fu">data</span>(penguins, <span class="at">package =</span> <span class="st">"palmerpenguins"</span>)</span>
<span id="cb1-2"><a href="#cb1-2" aria-hidden="true" tabindex="-1"></a>penguins <span class="ot">&lt;-</span> penguins[<span class="fu">complete.cases</span>(penguins),]</span>
<span id="cb1-3"><a href="#cb1-3" aria-hidden="true" tabindex="-1"></a></span>
<span id="cb1-4"><a href="#cb1-4" aria-hidden="true" tabindex="-1"></a><span class="fu">ggplot</span>(penguins, </span>
<span id="cb1-5"><a href="#cb1-5" aria-hidden="true" tabindex="-1"></a>       <span class="fu">aes</span>(<span class="at">x =</span> flipper_length_mm, <span class="at">y =</span> bill_length_mm)) <span class="sc">+</span></span>
<span id="cb1-6"><a href="#cb1-6" aria-hidden="true" tabindex="-1"></a>  <span class="fu">geom_point</span>(<span class="fu">aes</span>(<span class="at">color =</span> species, <span class="at">shape =</span> species)) <span class="sc">+</span></span>
<span id="cb1-7"><a href="#cb1-7" aria-hidden="true" tabindex="-1"></a>  <span class="fu">scale_color_viridis</span>(<span class="at">discrete =</span> <span class="fu"></span>TRUE) <span class="sc">+</span></span>
<span id="cb1-8"><a href="#cb1-8" aria-hidden="true" tabindex="-1"></a>  <span class="fu">labs</span>(</span>
<span id="cb1-9"><a href="#cb1-9" aria-hidden="true" tabindex="-1"></a>    <span class="at">title =</span> <span class="st">"Flipper and bill length"</span>,</span>
<span id="cb1-10"><a href="#cb1-10" aria-hidden="true" tabindex="-1"></a>    <span class="at">subtitle =</span> <span class="st">"Dimensions for penguins at Palmer Station LTER"</span>,</span>
<span id="cb1-11"><a href="#cb1-11" aria-hidden="true" tabindex="-1"></a>    <span class="at">x =</span> <span class="st">"Flipper length (mm)"</span>, <span class="at">y =</span> <span class="st">"Bill length (mm)"</span>,</span>
<span id="cb1-12"><a href="#cb1-12" aria-hidden="true" tabindex="-1"></a>    <span class="at">color =</span> <span class="st">"Penguin species"</span>, <span class="at">shape =</span> <span class="st">"Penguin species"</span></span>
<span id="cb1-13"><a href="#cb1-13" aria-hidden="true" tabindex="-1"></a>  ) <span class="sc">+</span></span>
<span id="cb1-14"><a href="#cb1-14" aria-hidden="true" tabindex="-1"></a>  <span class="fu">theme_light</span>()</span></code></pre></div>
<div class="cell-output-display">
<p><img src="/assets/img/quarto_img1.png" class="img-fluid" width="672"></p>
</div>
</div>
</section>
<section id="python" class="level3">
<h4 class="anchored" data-anchor-id="python">Python</h4>
<p>The beauty comes into play when we add <strong><code>Python</code></strong> chunks of code.</p>
<div class="cell">
<div class="sourceCode cell-code" id="cb2"><pre class="sourceCode python code-with-copy"><code class="sourceCode python"><span id="cb2-1"><a href="#cb2-1" aria-hidden="true" tabindex="-1"></a>penguins <span class="op">=</span> r.penguins</span>
<span id="cb2-2"><a href="#cb2-2" aria-hidden="true" tabindex="-1"></a>penguins.head(<span class="dv">3</span>)</span></code></pre></div>
<div class="cell-output cell-output-stdout">
<pre><code>species     island      bill_length_mm  ...    body_mass_g      sex     year
Adelie      Torgersen   39.1            ...    3750             male    2007  
Adelie      Torgersen   39.5            ...    3800             female  2007  
Adelie      Torgersen   40.3            ...    3250             female  2007</code></pre>
</div>
</div>
<p>We simply switched from <strong><code>R</code></strong> to <strong><code>Python</code></strong> working on the <em>penguins</em> data set.</p>
<p>Now, let us train a simple classifier using the <code>scikit-learn</code> module in <strong><code>Python</code></strong>.</p>
<div class="cell">
<div class="sourceCode cell-code" id="cb4"><pre class="sourceCode python code-with-copy"><code class="sourceCode python"><span id="cb4-1"><a href="#cb4-1" aria-hidden="true" tabindex="-1"></a>y <span class="op">=</span> penguins[<span class="st">'species'</span>]</span>
<span id="cb4-2"><a href="#cb4-2" aria-hidden="true" tabindex="-1"></a>X <span class="op">=</span> penguins[[<span class="st">'bill_length_mm'</span>,  <span class="st">'bill_depth_mm'</span>,  <span class="st">'flipper_length_mm'</span>, <span class="st">'body_mass_g'</span>]]</span>
<span id="cb4-3"><a href="#cb4-3" aria-hidden="true" tabindex="-1"></a>X_train, X_test, y_train, y_test <span class="op">=</span> train_test_split(X, y, test_size <span class="op">=</span> <span class="fl">0.2</span>, random_state <span class="op">=</span> <span class="dv">333</span>)</span>
<span id="cb4-4"><a href="#cb4-4" aria-hidden="true" tabindex="-1"></a></span>
<span id="cb4-5"><a href="#cb4-5" aria-hidden="true" tabindex="-1"></a>classifier <span class="op">=</span> RandomForestClassifier().fit(X_train, y_train)</span>
<span id="cb4-6"><a href="#cb4-6" aria-hidden="true" tabindex="-1"></a>y_test_pred <span class="op">=</span> classifier.predict(X_test)</span>
<span id="cb4-7"><a href="#cb4-7" aria-hidden="true" tabindex="-1"></a></span>
<span id="cb4-8"><a href="#cb4-8" aria-hidden="true" tabindex="-1"></a><span class="bu">print</span>(classification_report(y_test, y_test_pred))</span></code></pre></div>
<div class="cell-output cell-output-stdout">



<pre><code>             precision    recall  f1-score   support

     Adelie       1.00      0.95      0.98        22
  Chinstrap       1.00      1.00      1.00        15
     Gentoo       0.97      1.00      0.98        30

avg / total       0.99      0.99      0.99        67</code></pre>
</div>
</div>
</section>
</section>
<section id="conclusion" class="level2">
<h2 class="anchored" data-anchor-id="conclusion">Conclusion</h2>
<p>Great, with Quarto it is possible to write reports, presentations, … using different languages. Here, we have made use of <strong><code>R</code></strong>’s <code>tidyverse</code> for data preprocessing and visualization and <strong><code>Python</code></strong>’s Machine Learning frameworks (<code>scikit-learn</code> in this example). So, Quarto really enables you to pick the best of both worlds.</p>
</section>



</main>
<!-- /main column -->

</div> <!-- /content -->



</body></html>
