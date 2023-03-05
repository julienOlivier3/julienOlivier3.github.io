---
layout: page
title: x-language coding
description: A simple demonstration of coding with Python and R within the same IDE using Quarto.
img: assets/img/R_python2.png
importance: 1
category: fun
---


<html xmlns="http://www.w3.org/1999/xhtml" lang="en" xml:lang="en"><head>

<meta charset="utf-8">
<meta name="generator" content="quarto-1.1.149">

<meta name="viewport" content="width=device-width, initial-scale=1.0, user-scalable=yes">

<meta name="author" content="Julian Oliver Dörr">

<style>
table.fixed {table-layout:fixed; width:90px;}/*Setting the table width is important!*/
table.fixed th {width:150px;}/*Setting the width of th columns*/


:root {
    --color_rgb: 225, 254, 224;
}


table {
  border-collapse: collapse;
  width: 100%;
  margin-bottom: 30px;
}

th, td {
  text-align: left;
  padding: 8px;  
  
}

tr:nth-child(even){background-color: #f2f2f2; color: black !Important}
tr:nth-child(even) td{color: black !Important}

th {
  text-align: left;
  background-color: rgba(var(--color_rgb), 1);
  color: black !Important;
  /* #089c04 */
  
  
}

/* The scrollable part */

.scrollable {
  height: 500;
  overflow-x: scroll;
  overflow-y: hidden;
  border-bottom: 1px solid #ddd;
  margin-bottom: 30px;
  
}


</style>

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
    <div class="quarto-title-meta-heading"><i>Author</i></div>
    <div class="quarto-title-meta-contents">
             <p><i>Julian Oliver Dörr </i></p>
    </div>
</div>
  



<section id="quarto" class="level2">
<h2 class="anchored" data-anchor-id="quarto">Quarto</h2>
<p><a href="https://quarto.org/">Quarto</a> weaves together narrative text and code to produce elegantly formatted output. Most interestingly, Quarto executes code written in different languages. The following gives an illustration of cross-language coding in Quarto (here using R and Python - other languages, e.g. Julia, are supported as well).</p>
</section>
<section id="cross-language-coding" class="level2">
<h2 class="anchored" data-anchor-id="cross-language-coding">Cross-language coding</h2>
<section id="r" class="level3">
<h4 class="anchored" data-anchor-id="r">R</h4>
<p>R code chunks are written and executed just as we would do it in R Markdown. So, for users of R Markdown this should be very familiar.</p>


<div class="cell">
<div class="sourceCode cell-code" id="cb1"><pre class="sourceCode r code-with-copy"><code class="sourceCode r"><span id="cb1-1"><a href="#cb1-1" aria-hidden="true" tabindex="-1"></a><span class="cf">if</span> (<span class="sc">!</span><span class="fu">require</span>(<span class="st">"pacman"</span>)) <span class="fu">install.packages</span>(<span class="st">"pacman"</span>)</span></code>
<code class="sourceCode r"><span id="cb4-1"><a href="#cb4-1" aria-hidden="true" tabindex="-1"></a>pacman<span class="sc">::</span><span class="fu">p_load</span>(tidyverse, palmerpenguins, reticulate, viridis)</span></code>
</pre></div>
</div>


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
<p><img src="/assets/img/quarto_img1.png" class="img-fluid" width="750"></p>
</div>
</div>
</section>

<section id="python" class="level3">
<h4 class="anchored" data-anchor-id="python">Python</h4>

<p>The beauty comes into play when we add Python chunks of code.</p>


<div class="jp-Cell jp-CodeCell jp-Notebook-cell jp-mod-noOutputs  ">
<div class="jp-Cell-inputWrapper">
<div class="jp-InputArea jp-Cell-inputArea">

<div class="jp-CodeMirrorEditor jp-Editor jp-InputArea-editor" data-type="inline">
     <div class="CodeMirror cm-s-jupyter">
<div class=" highlight hl-ipython3">
<pre>
<span class="kn">import</span> <span class="nn">pandas</span> <span class="k">as</span> <span class="nn">pd</span>
<span class="kn">from</span> <span class="nn">sklearn.model_selection</span> <span class="kn">import</span> <span class="n">train_test_split</span>
<span class="kn">from</span> <span class="nn">sklearn.ensemble</span> <span class="kn">import</span> <span class="n">RandomForestClassifier</span>
<span class="kn">from</span> <span class="nn">sklearn.metrics</span> <span class="kn">import</span> <span class="n">classification_report</span>
</pre>
</div>

</div>
</div>
</div>
</div>
</div>


<div class="jp-Cell jp-CodeCell jp-Notebook-cell   ">
<div class="jp-Cell-inputWrapper">
<div class="jp-InputArea jp-Cell-inputArea">

<div class="jp-CodeMirrorEditor jp-Editor jp-InputArea-editor" data-type="inline">
<div class="CodeMirror cm-s-jupyter">
<div class=" highlight hl-ipython3"><pre><span></span><span class="n">penguins</span> <span class="o">=</span> <span class="n">r</span><span class="o">.</span><span class="n">penguins</span> <span class="c1"># here the R tibble turns into a pandas DataFrame</span>
<span class="n">penguins</span><span class="o">.</span><span class="n">head</span><span class="p">(</span><span class="mi">3</span><span class="p">)</span>
</pre></div>

</div>
</div>
</div>
</div>
</div>


<div class="scrollable">
<table border="1">
  <thead>
    <tr>
      <th>species</th>
      <th>island</th>
      <th>bill_length_mm</th>
      <th>...</th>
      <th>body_mass_g</th>
      <th>sex</th>
      <th>year</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>Adelie</td>
      <td>Torgersen</td>
      <td>39.1</td>
      <td>...</td>
      <td>3750</td>
      <td>male</td>
      <td>2007</td>
    </tr>
    <tr>
      <td>Adelie</td>
      <td>Torgersen</td>
      <td>39.5</td>
      <td>...</td>
      <td>3800</td>
      <td>female</td>
      <td>2007</td>
    </tr>
    <tr>
      <td>Adelie</td>
      <td>Torgersen</td>
      <td>40.3</td>
      <td>...</td>
      <td>3250</td>
      <td>female</td>
      <td>2007</td>
    </tr>
  </tbody>
</table>
</div>


<p>We simply switched from R to Python working on the <em>penguins</em> data set.</p>
<p>Now, let us train a simple classifier using the <code>scikit-learn</code> module in Python.</p>



<div class="jp-Cell-inputWrapper">
<div class="jp-InputArea jp-Cell-inputArea">

<div class="jp-CodeMirrorEditor jp-Editor jp-InputArea-editor" data-type="inline">
<div class="CodeMirror cm-s-jupyter">
<div class=" highlight hl-ipython3"><pre>
<span class="n">y</span> <span class="o">=</span> <span class="n">penguins</span><span class="p">[</span><span class="s1">&#39;species&#39;</span><span class="p">]</span>
<span class="n">X</span> <span class="o">=</span> <span class="n">penguins</span><span class="p">[</span><span class="s1">&#39;bill_length_mm&#39;</span><span class="p">,</span><span class="s1">&#39;bill_depth_mm&#39;</span><span class="p">,</span><span class="s1">&#39;flipper_length_mm&#39;</span><span class="p">,</span><span class="s1">&#39;body_mass_g&#39;</span><span class="p">]</span>
<span class="n">X_train</span><span class="p">, </span><span class="n">X_test</span><span class="p">, </span><span class="n">y_train</span><span class="p">, </span><span class="n">y_test</span> <span class="o">=</span> <span class="n">train_test_split</span><span class="p">(</span><span class="n">X</span><span class="p">,</span> <span class="n">y</span><span class="p">,</span> <span class="n">test_size</span><span class="o">=</span><span class="mi">0.2</span><span class="p">,</span> <span class="n">random_state</span><span class="o">=</span><span class="mi">333</span><span class="p">)</span>

<span class="n">classifier</span> <span class="o">=</span> <span class="n">RandomForestClassifier</span><span class="p">(</span><span class="p">)</span><span class="o">.</span><span class="n">fit</span><span class="p">(</span><span class="n">X_train</span><span class="p">,</span> <span class="n">y_train</span><span class="p">)</span>
<span class="n">y_test_pred</span> <span class="o">=</span> <span class="n">classifier</span><span class="o">.</span><span class="n">predict</span><span class="p">(</span><span class="n">X_test</span><span class="p">)</span>

<span class="nb">print</span><span class="p">(</span><span class="n">classification_report</span><span class="p">(</span><span class="n">y_test</span><span class="p">,</span> <span class="n">y_test_pred</span><span class="p">)</span><span class="p">)</span>
</pre></div>

</div>
</div>
</div>
</div>


<div class="scrollable">
<table border="1" class="fixed">
  <thead>
    <tr>
      <th></th>
      <th>Precision</th>
      <th>Recall</th>
      <th>F1-Score</th>
      <th>Support</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>Adelie</th>
      <td>1.00</td>
      <td>0.95</td>
      <td>0.98</td>
      <td>22</td>
    </tr>
    <tr>
      <th>Chinstrap</th>
      <td>1.00</td>
      <td>1.00</td>
      <td>1.00</td>
      <td>15</td>
    </tr>
    <tr>
      <th>Gentoo</th>
      <td>0.97</td>
      <td>1.00</td>
      <td>0.98</td>
      <td>30</td>
    </tr>
    <tr>
      <th>Average/Total</th>
      <td>0.99</td>
      <td>0.99</td>
      <td>0.99</td>
      <td>67</td>
    </tr>
  </tbody>
</table>
</div>

</section>
</section>
<section id="conclusion" class="level2">
<h2 class="anchored" data-anchor-id="conclusion">Conclusion</h2>
<p>Great, with Quarto it is possible to write reports, presentations, … using different languages. Here, we have made use of R's <code>tidyverse</code> for data preprocessing and visualization and Python's Machine Learning frameworks (<code>scikit-learn</code> in this example). So, Quarto really enables you to pick the best of both worlds.</p>
</section>



</main>
<!-- /main column -->

</div> <!-- /content -->



</body></html>
