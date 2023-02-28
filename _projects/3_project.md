---
layout: page
title: accessing web archives
description: Creating a panel dataset of historical website information from web archives.
img: assets/img/webarchive2.png
importance: 2
category: work
---


<html>
<head><meta charset="utf-8" />
<meta name="viewport" content="width=device-width, initial-scale=1.0, user-scalable=ye">

<title>Create_Web_Panel</title><script src="https://cdnjs.cloudflare.com/ajax/libs/require.js/2.1.10/require.min.js"></script>


<style>
table {
  border-collapse: collapse;
  width: 100%;
  margin-bottom:30px;
}

th, td {
  text-align: left;
  padding: 8px;
}

tr:nth-child(even){background-color: #f2f2f2}

th {
  text-align: left;
  background-color: #089c04;
  color: white;
}

/* The scrollable part */

.scrollable {
  height: 500;
  overflow-x: scroll;
  overflow-y: hidden;
  border-bottom: 1px solid #ddd;
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
    <div class="quarto-title-meta-heading">Author</div>
    <div class="quarto-title-meta-contents">
             <p>Julian Oliver Dörr </p>
    </div>
</div>


<div class="jp-Cell-inputWrapper"><div class="jp-InputPrompt jp-InputArea-prompt">
</div><div class="jp-RenderedHTMLCommon jp-RenderedMarkdown jp-MarkdownOutput " data-mime-type="text/markdown">
<p>This blog post shows how to create <strong>Dynamic Web Panels</strong> for corporate companies spanning a horizon of over 10 years of archived web data. The proposed framework uses web data archived on <a href="https://commoncrawl.org/">Common Crawl</a> and the <a href="https://archive.org/">Internet Archive</a>. For illustration purposes, a web panel of the DAX 30 companies comprising web data over more than 10 years is created.</p>

</div>
</div>
<div class="jp-Cell-inputWrapper"><div class="jp-InputPrompt jp-InputArea-prompt">
</div><div class="jp-RenderedHTMLCommon jp-RenderedMarkdown jp-MarkdownOutput " data-mime-type="text/markdown">
<h2>Why corporate websites?</h2>
Company websites pose an important source of economic data used by firms to spread product and service information (related to establishing a public image), to conduct transactions (e-business processes) and to ease opinion sharing (electronic word-of-mouth) (<a href="https://doi.org/10.1016/j.techfore.2017.07.027">Balzquez &amp; Domenech, 2018</a>). Recent economic studies have used corporate website data to:</p>
<ul>
<li>predict firm innovativeness (<a href="10.1007/s11192-014-1434-0">Gök et al., 2015</a>, <a href="https://doi.org/10.1371/journal.pone.0249071">Kinne &amp; Lenz, 2021</a>; <a href="https://doi.org/10.1371/journal.pone.0249583">Axenbeck &amp; Breithaupt, 2021</a>)</li>
<li>examine market entry strategies (<a href="https://doi.org/10.1007/s11192-013-0950-7">Arora et al., 2013</a>)</li>
<li>examine enterprise growth (<a href="10.1016/j.technovation.2016.01.002">Li et al., 2016</a>)</li>
<li>monitor firm export orientation (<a href="https://doi.org/10.3846/20294913.2016.1213193">Balzquez &amp; Domenech, 2017</a>)</li>
<li>track crisis impacts on the corporate sector (<a href="http://dx.doi.org/10.2139/ssrn.3924887">Dörr et al., 2021</a>)</li>
<li>...</li>
</ul>

</div>
</div>
<div class="jp-Cell-inputWrapper"><div class="jp-InputPrompt jp-InputArea-prompt">
</div><div class="jp-RenderedHTMLCommon jp-RenderedMarkdown jp-MarkdownOutput " data-mime-type="text/markdown">
<h2>Why panel data?</h2>
Firm characteristics, diffusion processes such as technological advances and adoption as well as business relations are clearly not static but evolve over time. It requires a continuous monitoring of corporate websites to capture this information. Most research studies require long time spans to derive meaningful insights and to control for unobserved heterogeneity across firms. For this reason, this post shows how to create a panel dataset of unstructured firm website information using <a href="https://commoncrawl.org/">Common Crawl</a>. Common Crawl is an open repository of web data crawled from the universe of websites worldwide over the last 12 years. The Common Crawl corpus contains 'petabytes of [...] raw web page data, metadata extracts and text extracts' and is freely accessible to anybody.</p>

</div>
</div>
<div class="jp-Cell-inputWrapper"><div class="jp-InputPrompt jp-InputArea-prompt">
</div><div class="jp-RenderedHTMLCommon jp-RenderedMarkdown jp-MarkdownOutput " data-mime-type="text/markdown">
<p>In the following, we show how to create website information of a company at different points in time given its URL. For this purpose, we use <a href="https://github.com/cocrawler/cdx_toolkit/blob/master/README.md">cdx_toolkit</a> a Python module for querying the Common Crawl corpus.</p>

</div>
</div>
<div class="jp-Cell-inputWrapper"><div class="jp-InputPrompt jp-InputArea-prompt">
</div><div class="jp-RenderedHTMLCommon jp-RenderedMarkdown jp-MarkdownOutput " data-mime-type="text/markdown">
<p>First, we start to load the required Python modules:</p>

</div>
</div><div class="jp-Cell jp-CodeCell jp-Notebook-cell jp-mod-noOutputs  ">
<div class="jp-Cell-inputWrapper">
<div class="jp-InputArea jp-Cell-inputArea">

<div class="jp-CodeMirrorEditor jp-Editor jp-InputArea-editor" data-type="inline">
     <div class="CodeMirror cm-s-jupyter">
<div class=" highlight hl-ipython3"><pre><span></span><span class="kn">import</span> <span class="nn">pandas</span> <span class="k">as</span> <span class="nn">pd</span>
<span class="kn">import</span> <span class="nn">cdx_toolkit</span>
</pre></div>

     </div>
</div>
</div>
</div>

</div>
<div class="jp-Cell-inputWrapper"><div class="jp-InputPrompt jp-InputArea-prompt">
</div><div class="jp-RenderedHTMLCommon jp-RenderedMarkdown jp-MarkdownOutput " data-mime-type="text/markdown">
<p>Next, for demonstration purposes we create a sample list of corporate URLs:</p>

</div>
</div><div class="jp-Cell jp-CodeCell jp-Notebook-cell jp-mod-noOutputs  ">
<div class="jp-Cell-inputWrapper">
<div class="jp-InputArea jp-Cell-inputArea">

<div class="jp-CodeMirrorEditor jp-Editor jp-InputArea-editor" data-type="inline">
     <div class="CodeMirror cm-s-jupyter">
<div class=" highlight hl-ipython3"><pre><span></span><span class="n">urls</span> <span class="o">=</span> <span class="p">[</span><span class="s1">&#39;zew.de/*&#39;</span><span class="p">,</span> <span class="s1">&#39;sap.com/*&#39;</span><span class="p">,</span> <span class="s1">&#39;otaro-shop.com/*&#39;</span><span class="p">]</span> <span class="c1">#zew.de/*, will return captures for any page on zew.de, e.g. zew.de/presse. Remove * to restrict captures to zew.de only</span>
</pre></div>

     </div>
</div>
</div>
</div>

</div>
<div class="jp-Cell-inputWrapper"><div class="jp-InputPrompt jp-InputArea-prompt">
</div><div class="jp-RenderedHTMLCommon jp-RenderedMarkdown jp-MarkdownOutput " data-mime-type="text/markdown">
<p>Instantiate the CDXFetcher() which allows to search Common Crawl's corpus for entries of a given corporate URL. Note that cdx_toolkit also allows querying the <a href="https://archive.org/">Internet Archive</a>, a collection of archived web data ranging even further back in time than Common Crawl (more on this later).</p>

</div>
</div><div class="jp-Cell jp-CodeCell jp-Notebook-cell jp-mod-noOutputs  ">
<div class="jp-Cell-inputWrapper">
<div class="jp-InputArea jp-Cell-inputArea">

<div class="jp-CodeMirrorEditor jp-Editor jp-InputArea-editor" data-type="inline">
     <div class="CodeMirror cm-s-jupyter">
<div class=" highlight hl-ipython3"><pre><span></span><span class="n">client</span> <span class="o">=</span> <span class="n">cdx_toolkit</span><span class="o">.</span><span class="n">CDXFetcher</span><span class="p">(</span><span class="n">source</span><span class="o">=</span><span class="s1">&#39;cc&#39;</span><span class="p">)</span> <span class="c1"># cc stands for Common Crawl</span>
</pre></div>

     </div>
</div>
</div>
</div>

</div>
<div class="jp-Cell-inputWrapper"><div class="jp-InputPrompt jp-InputArea-prompt">
</div><div class="jp-RenderedHTMLCommon jp-RenderedMarkdown jp-MarkdownOutput " data-mime-type="text/markdown">
<p>No we can search Common Crawl's corpus for archived web data of <a href="https://www.zew.de">ZEW</a>'s website, for example.<br>
In a first step, we only extract the metadata including information such as the time of crawling (<strong>timestamp</strong>), the nature and format of the crawled document (<a href="https://developer.mozilla.org/en-US/docs/Web/HTTP/Basics_of_HTTP/MIME_types"><strong>mime</strong></a>), the HTTP status code (<a href="https://en.wikipedia.org/wiki/List_of_HTTP_status_codes"><strong>status</strong></a>) and information revealing the size of the web document in bytes (<strong>offset</strong>) and character length (<strong>length</strong>).</p>

</div>
</div>
<div class="jp-Cell-inputWrapper"><div class="jp-InputPrompt jp-InputArea-prompt">
</div><div class="jp-RenderedHTMLCommon jp-RenderedMarkdown jp-MarkdownOutput " data-mime-type="text/markdown">
<p>Note that we restrict our requests to:</p>
<ul>
<li>the year 2017</li>
<li>successful crawling attempts (HTTP-status = 200)</li>
<li>text data only (mime = text/html)</li>
<li>and only extract 10 web pages archived in 2017.</li>
</ul>

</div>
</div><div class="jp-Cell jp-CodeCell jp-Notebook-cell jp-mod-noOutputs  ">
<div class="jp-Cell-inputWrapper">
<div class="jp-InputArea jp-Cell-inputArea">

<div class="jp-CodeMirrorEditor jp-Editor jp-InputArea-editor" data-type="inline">
     <div class="CodeMirror cm-s-jupyter">
<div class=" highlight hl-ipython3"><pre><span></span><span class="n">requests</span> <span class="o">=</span> <span class="nb">list</span><span class="p">(</span><span class="n">client</span><span class="o">.</span><span class="n">iter</span><span class="p">(</span><span class="n">urls</span><span class="p">[</span><span class="mi">0</span><span class="p">],</span> <span class="n">from_ts</span><span class="o">=</span><span class="s1">&#39;201701&#39;</span><span class="p">,</span> <span class="n">to</span><span class="o">=</span><span class="s1">&#39;201712&#39;</span><span class="p">,</span> <span class="n">limit</span><span class="o">=</span><span class="mi">10</span><span class="p">,</span> <span class="n">verbose</span><span class="o">=</span><span class="s1">&#39;v&#39;</span><span class="p">,</span> <span class="nb">filter</span><span class="o">=</span><span class="p">[</span><span class="s1">&#39;=status:200&#39;</span><span class="p">,</span> <span class="s1">&#39;=mime-detected:text/html&#39;</span><span class="p">]))</span>
</pre></div>

     </div>
</div>
</div>
</div>

</div><div class="jp-Cell jp-CodeCell jp-Notebook-cell   ">
<div class="jp-Cell-inputWrapper">
<div class="jp-InputArea jp-Cell-inputArea">

<div class="jp-CodeMirrorEditor jp-Editor jp-InputArea-editor" data-type="inline">
     <div class="CodeMirror cm-s-jupyter">
<div class=" highlight hl-ipython3"><pre><span></span><span class="n">metadata</span> <span class="o">=</span> <span class="n">pd</span><span class="o">.</span><span class="n">DataFrame</span><span class="p">([</span><span class="n">r</span><span class="o">.</span><span class="n">data</span> <span class="k">for</span> <span class="n">r</span> <span class="ow">in</span> <span class="n">requests</span><span class="p">])</span>
<span class="n">metadata</span><span class="o">.</span><span class="n">head</span><span class="p">(</span><span class="mi">3</span><span class="p">)</span>
</pre></div>

     </div>
</div>
</div>
</div>

<div class="jp-Cell-outputWrapper">


<div class="jp-OutputArea jp-Cell-outputArea">

<div class="jp-OutputArea-child">




<div class="jp-RenderedHTMLCommon jp-RenderedHTML jp-OutputArea-output jp-OutputArea-executeResult" data-mime-type="text/html">
<div>







<div class="scrollable">
<table border="1">
  <thead>
    <tr>
      <th>urlkey</th>
      <th>timestamp</th>
      <th>url</th>
      <th>mime</th>
      <th>mime-detected</th>
      <th>status</th>
      <th>digest</th>
      <th>length</th>
      <th>offset</th>
      <th>filename</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>de,zew)/</td>
      <td>20171211154120</td>
      <td>http://www.zew.de/</td>
      <td>text/html</td>
      <td>text/html</td>
      <td>200</td>
      <td>DFB4ZBE4QT4Y7CWATCK7Q7G5SSCBQHY6</td>
      <td>18082</td>
      <td>508576778</td>
      <td>crawl-data/CC-MAIN-2017-51/segments/1512948513...</td>
    </tr>
    <tr>
      <td>de,zew)/</td>
      <td>20171212155354</td>
      <td>http://www.zew.de/</td>
      <td>text/html</td>
      <td>text/html</td>
      <td>200</td>
      <td>OXTU2HOXOSJ2YBYRPFDIED77WJ543HBS</td>
      <td>17904</td>
      <td>495470327</td>
      <td>crawl-data/CC-MAIN-2017-51/segments/1512948517...</td>
    </tr>
    <tr>
      <td>de,zew)/das-zew/aktuelles/gruendungen-in-baden...</td>
      <td>20171212095717</td>
      <td>http://www.zew.de/das-zew/aktuelles/gruendunge...</td>
      <td>text/html</td>
      <td>text/html</td>
      <td>200</td>
      <td>EDPWOZEBDOJ7L2A4TQ2JACYA4FXP3XKG</td>
      <td>14557</td>
      <td>491201284</td>
      <td>crawl-data/CC-MAIN-2017-51/segments/1512948515...</td>
    </tr>
  </tbody>
</table>
</div>


<div class="jp-Cell-inputWrapper"><div class="jp-InputPrompt jp-InputArea-prompt">
</div><div class="jp-RenderedHTMLCommon jp-RenderedMarkdown jp-MarkdownOutput " data-mime-type="text/markdown">
<p>As it can be seen the metadata information provides an overview of what sort of archived web data is available for the given URL. Most importantly note, that only websites successfully archived in 2017 that include textual content have been requested. We have not yet download the actual content found on the website but only inspected the respective metadata. In the next step we will download the textual content found on the respective web page at the given point of time.</p>

</div>
</div>
<div class="jp-Cell-inputWrapper"><div class="jp-InputPrompt jp-InputArea-prompt">
</div><div class="jp-RenderedHTMLCommon jp-RenderedMarkdown jp-MarkdownOutput " data-mime-type="text/markdown">
<p>For this purpose, we import BeautifulSoup which allows to easily parse the HTML code of the web page.</p>

</div>
</div><div class="jp-Cell jp-CodeCell jp-Notebook-cell jp-mod-noOutputs  ">
<div class="jp-Cell-inputWrapper">
<div class="jp-InputArea jp-Cell-inputArea">

<div class="jp-CodeMirrorEditor jp-Editor jp-InputArea-editor" data-type="inline">
     <div class="CodeMirror cm-s-jupyter">
<div class=" highlight hl-ipython3"><pre><span></span><span class="kn">from</span> <span class="nn">bs4</span> <span class="kn">import</span> <span class="n">BeautifulSoup</span>
<span class="n">textdata</span> <span class="o">=</span> <span class="n">pd</span><span class="o">.</span><span class="n">DataFrame</span><span class="p">([</span><span class="n">BeautifulSoup</span><span class="p">(</span><span class="n">r</span><span class="o">.</span><span class="n">content</span><span class="p">,</span> <span class="s1">&#39;html.parser&#39;</span><span class="p">)</span><span class="o">.</span><span class="n">get_text</span><span class="p">(</span><span class="n">strip</span><span class="o">=</span><span class="kc">True</span><span class="p">)</span> <span class="k">for</span> <span class="n">r</span> <span class="ow">in</span> <span class="n">requests</span><span class="p">],</span> <span class="n">columns</span><span class="o">=</span><span class="p">[</span><span class="s1">&#39;text&#39;</span><span class="p">])</span>
</pre></div>

     </div>
</div>
</div>
</div>

</div><div class="jp-Cell jp-CodeCell jp-Notebook-cell   ">
<div class="jp-Cell-inputWrapper">
<div class="jp-InputArea jp-Cell-inputArea">

<div class="jp-CodeMirrorEditor jp-Editor jp-InputArea-editor" data-type="inline">
     <div class="CodeMirror cm-s-jupyter">
<div class=" highlight hl-ipython3"><pre><span></span><span class="n">pd</span><span class="o">.</span><span class="n">concat</span><span class="p">([</span><span class="n">metadata</span><span class="p">,</span> <span class="n">textdata</span><span class="p">],</span> <span class="n">axis</span><span class="o">=</span><span class="mi">1</span><span class="p">)[[</span><span class="s1">&#39;timestamp&#39;</span><span class="p">,</span> <span class="s1">&#39;text&#39;</span><span class="p">]]</span>
</pre></div>

     </div>
</div>
</div>
</div>

<div class="jp-Cell-outputWrapper">


<div class="jp-OutputArea jp-Cell-outputArea">

<div class="jp-OutputArea-child">




<div class="jp-RenderedHTMLCommon jp-RenderedHTML jp-OutputArea-output jp-OutputArea-executeResult" data-mime-type="text/html">
<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1">
  <thead>
    <tr>
      <th>timestamp</th>
      <th>text</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>20171211154120</td>
      <td>Zentrum für Europäische Wirtschaftsforschung (...</td>
    </tr>
    <tr>
      <td>20171212155354</td>
      <td>Zentrum für Europäische Wirtschaftsforschung (...</td>
    </tr>
    <tr>
      <td>20171212095717</td>
      <td>ZEW-Aktuell: Gründungen in Baden-Württemberg m...</td>
    </tr>
    <tr>
      <td>20171212100700</td>
      <td>ZEW-Aktuell: Neue Daten für eine effiziente Ve...</td>
    </tr>
    <tr>
      <td>20171211154059</td>
      <td>ZEW-Aktuell: Schüler-Teams zum regionalen YES!...</td>
    </tr>
    <tr>
      <td>20171213020528</td>
      <td>ZEW-Aktuell: ZEW Wirtschaftsforum 2016 – Markt...</td>
    </tr>
    <tr>
      <td>20171212102529</td>
      <td>404Zur Navigation springenZum Seiteninhalt spr...</td>
    </tr>
    <tr>
      <td>20171217114955</td>
      <td>AnfahrtZur Navigation springenZum Seiteninhalt...</td>
    </tr>
    <tr>
      <td>20171215102245</td>
      <td>Aktuelle Meldungen - ZEW MannheimZur Navigatio...</td>
    </tr>
    <tr>
      <td>20171214063116</td>
      <td>ZEW-Aktuell: 19. ZEW Summer Workshop – Gestalt...</td>
    </tr>
  </tbody>
</table>


<div class="jp-Cell-inputWrapper"><div class="jp-InputPrompt jp-InputArea-prompt">
</div><div class="jp-RenderedHTMLCommon jp-RenderedMarkdown jp-MarkdownOutput " data-mime-type="text/markdown">
<p>We see that with the framework introduced here it is convenient to extract textual content found on corporate websites for a given timestamp. In the example, we have extracted webtexts of <a href="https://www.zew.de">ZEW</a> for the year 2017. With Common Crawl one can go further back in past extracting the web content of a company up until 2008. In doing so one can even be more precise in the date. We have restricted the search to the year 2017 only, but one could even be more restrictive extracting webdata archived in a specific month or even on a specific day (if the website has been crawled on this day). The internet does not forget! In this way, it is easily possible to obtain historical webdata of German corporations contained in the Mannheim Web Panel.</p>

</div>
</div>
<div class="jp-Cell-inputWrapper"><div class="jp-InputPrompt jp-InputArea-prompt">
</div><div class="jp-RenderedHTMLCommon jp-RenderedMarkdown jp-MarkdownOutput " data-mime-type="text/markdown">
<p>With this approach it is easy to extend the panel going even further back in time. We will use web data archived in the Internet Archive for this purpose.</p>

</div>
</div><div class="jp-Cell jp-CodeCell jp-Notebook-cell jp-mod-noOutputs  ">
<div class="jp-Cell-inputWrapper">
<div class="jp-InputArea jp-Cell-inputArea">

<div class="jp-CodeMirrorEditor jp-Editor jp-InputArea-editor" data-type="inline">
     <div class="CodeMirror cm-s-jupyter">
<div class=" highlight hl-ipython3"><pre><span></span><span class="n">client</span> <span class="o">=</span> <span class="n">cdx_toolkit</span><span class="o">.</span><span class="n">CDXFetcher</span><span class="p">(</span><span class="n">source</span><span class="o">=</span><span class="s1">&#39;ia&#39;</span><span class="p">)</span> <span class="c1"># "ia" stands for Internet Archive, alternatively "cc" for Common Crawl</span>
</pre></div>

     </div>
</div>
</div>
</div>

</div><div class="jp-Cell jp-CodeCell jp-Notebook-cell   ">
<div class="jp-Cell-inputWrapper">
<div class="jp-InputArea jp-Cell-inputArea">

<div class="jp-CodeMirrorEditor jp-Editor jp-InputArea-editor" data-type="inline">
     <div class="CodeMirror cm-s-jupyter">
<div class=" highlight hl-ipython3"><pre><span></span><span class="kn">from</span> <span class="nn">tqdm</span> <span class="kn">import</span> <span class="n">tqdm</span> <span class="c1"># allows to monitor progress of the execution</span>
<span class="n">df</span> <span class="o">=</span> <span class="n">pd</span><span class="o">.</span><span class="n">DataFrame</span><span class="p">()</span>
<span class="k">for</span> <span class="n">y</span> <span class="ow">in</span> <span class="n">tqdm</span><span class="p">(</span><span class="nb">range</span><span class="p">(</span><span class="mi">2010</span><span class="p">,</span><span class="mi">2017</span><span class="p">)):</span>
    <span class="n">requests</span> <span class="o">=</span> <span class="nb">list</span><span class="p">(</span><span class="n">client</span><span class="o">.</span><span class="n">iter</span><span class="p">(</span><span class="n">urls</span><span class="p">[</span><span class="mi">0</span><span class="p">],</span> <span class="n">from_ts</span><span class="o">=</span><span class="nb">str</span><span class="p">(</span><span class="n">y</span><span class="p">),</span> <span class="n">to</span><span class="o">=</span><span class="nb">str</span><span class="p">(</span><span class="n">y</span><span class="p">),</span> <span class="n">limit</span><span class="o">=</span><span class="mi">10</span><span class="p">,</span> <span class="n">verbose</span><span class="o">=</span><span class="s1">&#39;v&#39;</span><span class="p">,</span> <span class="nb">filter</span><span class="o">=</span><span class="p">[</span><span class="s1">&#39;status:200&#39;</span><span class="p">,</span> <span class="s1">&#39;mime:text/html&#39;</span><span class="p">]))</span>
    <span class="n">df_temp</span> <span class="o">=</span> <span class="n">pd</span><span class="o">.</span><span class="n">concat</span><span class="p">([</span><span class="n">pd</span><span class="o">.</span><span class="n">DataFrame</span><span class="p">([</span><span class="n">r</span><span class="o">.</span><span class="n">data</span> <span class="k">for</span> <span class="n">r</span> <span class="ow">in</span> <span class="n">requests</span><span class="p">]),</span> <span class="n">pd</span><span class="o">.</span><span class="n">DataFrame</span><span class="p">([</span><span class="n">BeautifulSoup</span><span class="p">(</span><span class="n">r</span><span class="o">.</span><span class="n">content</span><span class="p">,</span> <span class="s1">&#39;html.parser&#39;</span><span class="p">)</span><span class="o">.</span><span class="n">get_text</span><span class="p">(</span><span class="n">strip</span><span class="o">=</span><span class="kc">True</span><span class="p">)</span> <span class="k">for</span> <span class="n">r</span> <span class="ow">in</span> <span class="n">requests</span><span class="p">],</span> <span class="n">columns</span><span class="o">=</span><span class="p">[</span><span class="s1">&#39;text&#39;</span><span class="p">])],</span> <span class="n">axis</span><span class="o">=</span><span class="mi">1</span><span class="p">)</span>
    <span class="n">df_temp</span><span class="p">[</span><span class="s1">&#39;year&#39;</span><span class="p">]</span> <span class="o">=</span> <span class="n">df_temp</span><span class="o">.</span><span class="n">timestamp</span><span class="o">.</span><span class="n">apply</span><span class="p">(</span><span class="k">lambda</span> <span class="n">x</span><span class="p">:</span> <span class="nb">str</span><span class="p">(</span><span class="n">x</span><span class="p">)[</span><span class="mi">0</span><span class="p">:</span><span class="mi">4</span><span class="p">])</span>
    <span class="n">df_temp</span> <span class="o">=</span> <span class="n">df_temp</span><span class="p">[[</span><span class="s1">&#39;year&#39;</span><span class="p">,</span> <span class="s1">&#39;text&#39;</span><span class="p">]]</span>
    <span class="n">df</span> <span class="o">=</span> <span class="n">df</span><span class="o">.</span><span class="n">append</span><span class="p">(</span><span class="n">df_temp</span><span class="p">,</span> <span class="n">ignore_index</span><span class="o">=</span><span class="kc">True</span><span class="p">)</span>
</pre></div>

     </div>
</div>
</div>
</div>

<div class="jp-Cell-outputWrapper">


<div class="jp-OutputArea jp-Cell-outputArea">

<div class="jp-OutputArea-child">

    
    <div class="jp-OutputPrompt jp-OutputArea-prompt"></div>


<div class="jp-RenderedText jp-OutputArea-output" data-mime-type="application/vnd.jupyter.stderr">
<pre>100%|█████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████| 7/7 [01:24&lt;00:00, 12.11s/it]
</pre>
</div>
</div>

</div>

</div>

</div>
<div class="jp-Cell-inputWrapper"><div class="jp-InputPrompt jp-InputArea-prompt">
</div><div class="jp-RenderedHTMLCommon jp-RenderedMarkdown jp-MarkdownOutput " data-mime-type="text/markdown">
<p>If we take a look at the data, we see that now we have 10 additional snapshots of <a href="https://www.zew.de">ZEW</a>'s website for the years 2010-2022.</p>

</div>
</div><div class="jp-Cell jp-CodeCell jp-Notebook-cell   ">
<div class="jp-Cell-inputWrapper">
<div class="jp-InputArea jp-Cell-inputArea">

<div class="jp-CodeMirrorEditor jp-Editor jp-InputArea-editor" data-type="inline">
     <div class="CodeMirror cm-s-jupyter">
<div class=" highlight hl-ipython3"><pre><span></span><span class="n">df</span>
</pre></div>

     </div>
</div>
</div>
</div>

<div class="jp-Cell-outputWrapper">


<div class="jp-OutputArea jp-Cell-outputArea">

<div class="jp-OutputArea-child">





<div class="jp-RenderedHTMLCommon jp-RenderedHTML jp-OutputArea-output jp-OutputArea-executeResult" data-mime-type="text/html">
<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1">
  <thead>
    <tr>
      <th>year</th>
      <th>text</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>2010</td>
      <td>Zentrum für Europäische Wirtschaftsforschung G...</td>
    </tr>
    <tr>
      <td>2010</td>
      <td>Zentrum für Europäische Wirtschaftsforschung G...</td>
    </tr>
    <tr>
      <td>2010</td>
      <td>Zentrum für Europäische Wirtschaftsforschung G...</td>
    </tr>
    <tr>
      <td>2010</td>
      <td>Zentrum für Europäische Wirtschaftsforschung G...</td>
    </tr>
    <tr>
      <td>2010</td>
      <td>Zentrum für Europäische Wirtschaftsforschung G...</td>
    </tr>
    <tr>
      <td>...</td>
      <td>...</td>
    </tr>
    <tr>
      <td>2022</td>
      <td>ZEW - Zentrum für Europäische Wirtschaftsforsc...</td>
    </tr>
    <tr>
      <td>2022</td>
      <td>ZEW - Zentrum für Europäische Wirtschaftsforsc...</td>
    </tr>
    <tr>
      <td>2022</td>
      <td>ZEW - Zentrum für Europäische Wirtschaftsforsc...</td>
    </tr>
    <tr>
      <td>2022</td>
      <td>ZEW - Zentrum für Europäische Wirtschaftsforsc...</td>
    </tr>
    <tr>
      <td>2022</td>
      <td>ZEW - Zentrum für Europäische Wirtschaftsforsc...</td>
    </tr>
  </tbody>
</table>


<div class="jp-Cell-inputWrapper"><div class="jp-InputPrompt jp-InputArea-prompt">
</div><div class="jp-RenderedHTMLCommon jp-RenderedMarkdown jp-MarkdownOutput " data-mime-type="text/markdown">
<p>Overall, with the proposed framework we could extend the panel for <a href="https://www.zew.de">ZEW</a> comprising now web data from 2010 to 2022. A coverage of 13 years suits much more for economic research that looks at the diffusion of technologies over time, for instance.</p>

</div>
</div>
<div class="jp-Cell-inputWrapper"><div class="jp-InputPrompt jp-InputArea-prompt">
</div><div class="jp-RenderedHTMLCommon jp-RenderedMarkdown jp-MarkdownOutput " data-mime-type="text/markdown">
<h2 id="Scaling-up-further:-Extract-historic-web-data-for-more-than-just-one-company">Scaling up further: Extract historic web data for more than just one company<a class="anchor-link" href="#Scaling-up-further:-Extract-historic-web-data-for-more-than-just-one-company"></a></h2>
</div>
</div>
<div class="jp-Cell-inputWrapper"><div class="jp-InputPrompt jp-InputArea-prompt">
</div><div class="jp-RenderedHTMLCommon jp-RenderedMarkdown jp-MarkdownOutput " data-mime-type="text/markdown">
<p>Of course we can scale up the above approach to retrieve web content for a larger number of firms. Let us do so for the DAX 30 companies.</p>

</div>
</div><div class="jp-Cell jp-CodeCell jp-Notebook-cell jp-mod-noOutputs  ">
<div class="jp-Cell-inputWrapper">
<div class="jp-InputArea jp-Cell-inputArea">

<div class="jp-CodeMirrorEditor jp-Editor jp-InputArea-editor" data-type="inline">
     <div class="CodeMirror cm-s-jupyter">
<div class=" highlight hl-ipython3"><pre><span></span><span class="kn">from</span> <span class="nn">tqdm</span> <span class="kn">import</span> <span class="n">tqdm</span>
<span class="kn">from</span> <span class="nn">bs4</span> <span class="kn">import</span> <span class="n">BeautifulSoup</span>
<span class="kn">import</span> <span class="nn">requests</span>
<span class="kn">import</span> <span class="nn">re</span>
</pre></div>

     </div>
</div>
</div>
</div>

</div>
<div class="jp-Cell-inputWrapper"><div class="jp-InputPrompt jp-InputArea-prompt">
</div><div class="jp-RenderedHTMLCommon jp-RenderedMarkdown jp-MarkdownOutput " data-mime-type="text/markdown">
<p>First we get the URLs of the DAX 30 companies. These are available on the internet. See, for example. <a href="https://disfold.com/top-companies-germany-dax/">here</a>. For convenience I scrape them in the following lines of code.</p>

</div>
</div><div class="jp-Cell jp-CodeCell jp-Notebook-cell jp-mod-noOutputs  ">
<div class="jp-Cell-inputWrapper">
<div class="jp-InputArea jp-Cell-inputArea">


<div class="jp-CodeMirrorEditor jp-Editor jp-InputArea-editor" data-type="inline">
     <div class="CodeMirror cm-s-jupyter">
<div class=" highlight hl-ipython3"><pre><span></span><span class="n">landing</span> <span class="o">=</span> <span class="s1">&#39;https://disfold.com/top-companies-germany-dax/&#39;</span>
<span class="n">page</span> <span class="o">=</span> <span class="n">requests</span><span class="o">.</span><span class="n">get</span><span class="p">(</span><span class="n">landing</span><span class="p">)</span>
<span class="n">html</span> <span class="o">=</span> <span class="n">BeautifulSoup</span><span class="p">(</span><span class="n">page</span><span class="o">.</span><span class="n">content</span><span class="p">,</span> <span class="s1">&#39;html.parser&#39;</span><span class="p">)</span>
<span class="n">dax30</span> <span class="o">=</span> <span class="n">html</span><span class="o">.</span><span class="n">find</span><span class="p">(</span><span class="s1">&#39;div&#39;</span><span class="p">,</span> <span class="n">class_</span><span class="o">=</span><span class="s1">&#39;entry-content&#39;</span><span class="p">)</span><span class="o">.</span><span class="n">find_all</span><span class="p">(</span><span class="s1">&#39;a&#39;</span><span class="p">,</span> <span class="n">target</span><span class="o">=</span><span class="s1">&#39;_blank&#39;</span><span class="p">,</span> <span class="n">href</span><span class="o">=</span><span class="kc">True</span><span class="p">)</span>
<span class="n">urls</span> <span class="o">=</span> <span class="p">[</span><span class="n">re</span><span class="o">.</span><span class="n">search</span><span class="p">(</span><span class="sa">r</span><span class="s1">&#39;\..{1,}\.(?:com|de|rwe)&#39;</span><span class="p">,</span> <span class="n">d</span><span class="p">[</span><span class="s1">&#39;href&#39;</span><span class="p">])</span><span class="o">.</span><span class="n">group</span><span class="p">(</span><span class="mi">0</span><span class="p">)[</span><span class="mi">1</span><span class="p">:]</span> <span class="o">+</span> <span class="s1">&#39;/*&#39;</span> <span class="k">for</span> <span class="n">d</span> <span class="ow">in</span> <span class="n">dax30</span><span class="p">]</span>
</pre></div>

     </div>
</div>
</div>
</div>

</div>
<div class="jp-Cell-inputWrapper"><div class="jp-InputPrompt jp-InputArea-prompt">
</div><div class="jp-RenderedHTMLCommon jp-RenderedMarkdown jp-MarkdownOutput " data-mime-type="text/markdown">
<p>Let us have a quick glimpse on the URLs of all DAX 30 companies.</p>

</div>
</div><div class="jp-Cell jp-CodeCell jp-Notebook-cell   ">
<div class="jp-Cell-inputWrapper">
<div class="jp-InputArea jp-Cell-inputArea">

<div class="jp-CodeMirrorEditor jp-Editor jp-InputArea-editor" data-type="inline">
     <div class="CodeMirror cm-s-jupyter">
<div class=" highlight hl-ipython3"><pre><span></span><span class="n">urls</span>
</pre></div>

     </div>
</div>
</div>
</div>

<div class="jp-Cell-outputWrapper">


<div class="jp-OutputArea jp-Cell-outputArea">

<div class="jp-OutputArea-child">

    
    




<div class="jp-RenderedText jp-OutputArea-output jp-OutputArea-executeResult" data-mime-type="text/plain">
<pre>[&#39;thyssenkrupp.com/*&#39;,
 &#39;covestro.com/*&#39;,
 &#39;lufthansa.com/*&#39;,
 &#39;merckgroup.com/*&#39;,
 &#39;wirecard.com/*&#39;,
 &#39;heidelbergcement.com/*&#39;,
 &#39;group.rwe/*&#39;,
 &#39;db.com/*&#39;,
 &#39;deutsche-boerse.com/*&#39;,
 &#39;eon.com/*&#39;,
 &#39;freseniusmedicalcare.com/*&#39;,
 &#39;infineon.com/*&#39;,
 &#39;vonovia.de/*&#39;,
 &#39;beiersdorf.com/*&#39;,
 &#39;fresenius.com/*&#39;,
 &#39;continental-corporation.com/*&#39;,
 &#39;munichre.com/*&#39;,
 &#39;henkel.com/*&#39;,
 &#39;dpdhl.com/*&#39;,
 &#39;adidas-group.com/*&#39;,
 &#39;bmw.com/*&#39;,
 &#39;bayer.com/*&#39;,
 &#39;daimler.com/*&#39;,
 &#39;basf.com/*&#39;,
 &#39;telekom.com/*&#39;,
 &#39;volkswagenag.com/*&#39;,
 &#39;siemens.com/*&#39;,
 &#39;allianz.com/*&#39;,
 &#39;lindeplc.com/*&#39;,
 &#39;sap.com/*&#39;]</pre>
</div>

</div>

</div>

</div>

</div>
<div class="jp-Cell-inputWrapper"><div class="jp-InputPrompt jp-InputArea-prompt">
</div><div class="jp-RenderedHTMLCommon jp-RenderedMarkdown jp-MarkdownOutput " data-mime-type="text/markdown">
<p>Given the URLs, we can now construct a web data panel set for the DAX 30 companies applying the introduced framework in this blog post.</p>

</div>
</div><div class="jp-Cell jp-CodeCell jp-Notebook-cell jp-mod-noOutputs  ">
<div class="jp-Cell-inputWrapper">
<div class="jp-InputArea jp-Cell-inputArea">

<div class="jp-CodeMirrorEditor jp-Editor jp-InputArea-editor" data-type="inline">
     <div class="CodeMirror cm-s-jupyter">


</div>
</div>
</div>
</div>

</div><div class="jp-Cell jp-CodeCell jp-Notebook-cell jp-mod-noOutputs  ">
<div class="jp-Cell-inputWrapper">
<div class="jp-InputArea jp-Cell-inputArea">

<div class="jp-CodeMirrorEditor jp-Editor jp-InputArea-editor" data-type="inline">
     <div class="CodeMirror cm-s-jupyter">
<div class=" highlight hl-ipython3"><pre><span></span><span class="n">df</span> <span class="o">=</span> <span class="n">pd</span><span class="o">.</span><span class="n">DataFrame</span><span class="p">()</span>
<span class="k">for</span> <span class="n">c</span> <span class="ow">in</span> <span class="n">tqdm</span><span class="p">(</span><span class="n">urls</span><span class="p">):</span>
    <span class="k">for</span> <span class="n">y</span> <span class="ow">in</span> <span class="p">(</span><span class="nb">range</span><span class="p">(</span><span class="mi">2010</span><span class="p">,</span><span class="mi">2022</span><span class="p">)):</span>
        <span class="n">requests</span> <span class="o">=</span> <span class="nb">list</span><span class="p">(</span><span class="n">client</span><span class="o">.</span><span class="n">iter</span><span class="p">(</span><span class="n">c</span><span class="p">,</span> <span class="n">from_ts</span><span class="o">=</span><span class="nb">str</span><span class="p">(</span><span class="n">y</span><span class="p">),</span> <span class="n">to</span><span class="o">=</span><span class="nb">str</span><span class="p">(</span><span class="n">y</span><span class="p">),</span> <span class="n">limit</span><span class="o">=</span><span class="mi">10</span><span class="p">,</span> <span class="n">verbose</span><span class="o">=</span><span class="s1">&#39;v&#39;</span><span class="p">,</span> <span class="nb">filter</span><span class="o">=</span><span class="p">[</span><span class="s1">&#39;status:200&#39;</span><span class="p">,</span> <span class="s1">&#39;mime:text/html&#39;</span><span class="p">]))</span>
        <span class="n">df_temp</span> <span class="o">=</span> <span class="n">pd</span><span class="o">.</span><span class="n">concat</span><span class="p">([</span><span class="n">pd</span><span class="o">.</span><span class="n">DataFrame</span><span class="p">([</span><span class="n">r</span><span class="o">.</span><span class="n">data</span> <span class="k">for</span> <span class="n">r</span> <span class="ow">in</span> <span class="n">requests</span><span class="p">]),</span> <span class="n">pd</span><span class="o">.</span><span class="n">DataFrame</span><span class="p">([</span><span class="n">BeautifulSoup</span><span class="p">(</span><span class="n">r</span><span class="o">.</span><span class="n">content</span><span class="p">,</span> <span class="s1">&#39;html.parser&#39;</span><span class="p">)</span><span class="o">.</span><span class="n">get_text</span><span class="p">(</span><span class="n">strip</span><span class="o">=</span><span class="kc">True</span><span class="p">)</span> <span class="k">for</span> <span class="n">r</span> <span class="ow">in</span> <span class="n">requests</span><span class="p">],</span> <span class="n">columns</span><span class="o">=</span><span class="p">[</span><span class="s1">&#39;text&#39;</span><span class="p">])],</span> <span class="n">axis</span><span class="o">=</span><span class="mi">1</span><span class="p">)</span>
        <span class="k">if</span> <span class="ow">not</span> <span class="n">df_temp</span><span class="o">.</span><span class="n">empty</span><span class="p">:</span>
            <span class="n">df_temp</span><span class="p">[</span><span class="s1">&#39;year&#39;</span><span class="p">]</span> <span class="o">=</span> <span class="n">df_temp</span><span class="o">.</span><span class="n">timestamp</span><span class="o">.</span><span class="n">apply</span><span class="p">(</span><span class="k">lambda</span> <span class="n">x</span><span class="p">:</span> <span class="nb">str</span><span class="p">(</span><span class="n">x</span><span class="p">)[</span><span class="mi">0</span><span class="p">:</span><span class="mi">4</span><span class="p">])</span>
            <span class="n">df_temp</span><span class="p">[</span><span class="s1">&#39;id&#39;</span><span class="p">]</span> <span class="o">=</span> <span class="n">c</span>
            <span class="n">df_temp</span> <span class="o">=</span> <span class="n">df_temp</span><span class="p">[[</span><span class="s1">&#39;id&#39;</span><span class="p">,</span> <span class="s1">&#39;year&#39;</span><span class="p">,</span> <span class="s1">&#39;text&#39;</span><span class="p">]]</span>
            <span class="n">df</span> <span class="o">=</span> <span class="n">df</span><span class="o">.</span><span class="n">append</span><span class="p">(</span><span class="n">df_temp</span><span class="p">,</span> <span class="n">ignore_index</span><span class="o">=</span><span class="kc">True</span><span class="p">)</span>
</pre></div>

     </div>
</div>
</div>
</div>

</div>
<div class="jp-Cell-inputWrapper"><div class="jp-InputPrompt jp-InputArea-prompt">
</div><div class="jp-RenderedHTMLCommon jp-RenderedMarkdown jp-MarkdownOutput " data-mime-type="text/markdown">
<p>In the table below we see how many distinct web pages for each of the 30 DAX companies in each of the years could have been retrieved with the proposed framework. Note that we have set the depth limit to 10 distinct webpages per company and year. Typically, for large companies, such as publivly listed firms, there are many more webpages archived.</p>

</div>
</div><div class="jp-Cell jp-CodeCell jp-Notebook-cell   ">
<div class="jp-Cell-inputWrapper">
<div class="jp-InputArea jp-Cell-inputArea">

<div class="jp-CodeMirrorEditor jp-Editor jp-InputArea-editor" data-type="inline">
     <div class="CodeMirror cm-s-jupyter">
<div class=" highlight hl-ipython3"><pre><span></span><span class="n">df</span><span class="o">.</span><span class="n">rename</span><span class="p">(</span><span class="n">columns</span><span class="o">=</span><span class="p">{</span><span class="s1">&#39;id&#39;</span><span class="p">:</span> <span class="s1">&#39;DAX 30 company&#39;</span><span class="p">,</span> <span class="s1">&#39;year&#39;</span><span class="p">:</span> <span class="s1">&#39;Year&#39;</span><span class="p">,</span> <span class="s1">&#39;text&#39;</span><span class="p">:</span> <span class="s1">&#39;Number of webpages&#39;</span><span class="p">})</span><span class="o">.</span><span class="n">pivot_table</span><span class="p">(</span><span class="n">index</span><span class="o">=</span><span class="s1">&#39;DAX 30 company&#39;</span><span class="p">,</span> <span class="n">columns</span><span class="o">=</span><span class="s1">&#39;Year&#39;</span><span class="p">,</span> <span class="n">aggfunc</span><span class="o">=</span><span class="nb">len</span><span class="p">,</span> <span class="n">fill_value</span><span class="o">=</span><span class="mi">0</span><span class="p">)</span>
</pre></div>

     </div>
</div>
</div>
</div>

<div class="jp-Cell-outputWrapper">


<div class="jp-OutputArea jp-Cell-outputArea">

<div class="jp-OutputArea-child">




<div class="jp-RenderedHTMLCommon jp-RenderedHTML jp-OutputArea-output jp-OutputArea-executeResult" data-mime-type="text/html">
<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead tr th {
        text-align: left;
    }

    .dataframe thead tr:last-of-type th {
        text-align: right;
    }
</style>
<table border="1">
  <thead>
    <tr>
      <th>Year</th>
      <th>2010</th>
      <th>2011</th>
      <th>2012</th>
      <th>2013</th>
      <th>2014</th>
      <th>2015</th>
      <th>2016</th>
      <th>2017</th>
      <th>2018</th>
      <th>2019</th>
      <th>2020</th>
      <th>2021</th>
    </tr>
    <tr>
      <th>DAX 30 company</th>
      <th colspan="12" style="text-align:center">Number of webpages</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>adidas-group.com/*</th>
      <td>10</td>
      <td>10</td>
      <td>10</td>
      <td>10</td>
      <td>10</td>
      <td>10</td>
      <td>10</td>
      <td>10</td>
      <td>10</td>
      <td>10</td>
      <td>10</td>
      <td>10</td>
    </tr>
    <tr>
      <th>allianz.com/*</th>
      <td>10</td>
      <td>10</td>
      <td>10</td>
      <td>9</td>
      <td>10</td>
      <td>10</td>
      <td>1</td>
      <td>10</td>
      <td>10</td>
      <td>10</td>
      <td>10</td>
      <td>10</td>
    </tr>
    <tr>
      <th>basf.com/*</th>
      <td>10</td>
      <td>10</td>
      <td>10</td>
      <td>10</td>
      <td>10</td>
      <td>10</td>
      <td>10</td>
      <td>10</td>
      <td>10</td>
      <td>10</td>
      <td>10</td>
      <td>10</td>
    </tr>
    <tr>
      <th>bayer.com/*</th>
      <td>10</td>
      <td>10</td>
      <td>10</td>
      <td>10</td>
      <td>10</td>
      <td>10</td>
      <td>10</td>
      <td>10</td>
      <td>10</td>
      <td>10</td>
      <td>10</td>
      <td>10</td>
    </tr>
    <tr>
      <th>beiersdorf.com/*</th>
      <td>10</td>
      <td>10</td>
      <td>10</td>
      <td>10</td>
      <td>10</td>
      <td>10</td>
      <td>10</td>
      <td>10</td>
      <td>10</td>
      <td>10</td>
      <td>10</td>
      <td>10</td>
    </tr>
    <tr>
      <th>bmw.com/*</th>
      <td>10</td>
      <td>10</td>
      <td>10</td>
      <td>10</td>
      <td>10</td>
      <td>10</td>
      <td>10</td>
      <td>10</td>
      <td>10</td>
      <td>10</td>
      <td>10</td>
      <td>10</td>
    </tr>
    <tr>
      <th>continental-corporation.com/*</th>
      <td>0</td>
      <td>5</td>
      <td>10</td>
      <td>10</td>
      <td>10</td>
      <td>10</td>
      <td>10</td>
      <td>10</td>
      <td>10</td>
      <td>10</td>
      <td>0</td>
      <td>0</td>
    </tr>
    <tr>
      <th>covestro.com/*</th>
      <td>7</td>
      <td>0</td>
      <td>0</td>
      <td>1</td>
      <td>0</td>
      <td>10</td>
      <td>10</td>
      <td>10</td>
      <td>10</td>
      <td>10</td>
      <td>10</td>
      <td>10</td>
    </tr>
    <tr>
      <th>daimler.com/*</th>
      <td>10</td>
      <td>10</td>
      <td>10</td>
      <td>10</td>
      <td>10</td>
      <td>10</td>
      <td>10</td>
      <td>10</td>
      <td>10</td>
      <td>10</td>
      <td>10</td>
      <td>10</td>
    </tr>
    <tr>
      <th>db.com/*</th>
      <td>10</td>
      <td>10</td>
      <td>10</td>
      <td>10</td>
      <td>10</td>
      <td>10</td>
      <td>10</td>
      <td>10</td>
      <td>10</td>
      <td>10</td>
      <td>10</td>
      <td>10</td>
    </tr>
    <tr>
      <th>deutsche-boerse.com/*</th>
      <td>10</td>
      <td>10</td>
      <td>10</td>
      <td>10</td>
      <td>10</td>
      <td>10</td>
      <td>10</td>
      <td>10</td>
      <td>10</td>
      <td>10</td>
      <td>10</td>
      <td>10</td>
    </tr>
    <tr>
      <th>dpdhl.com/*</th>
      <td>10</td>
      <td>0</td>
      <td>0</td>
      <td>10</td>
      <td>10</td>
      <td>10</td>
      <td>10</td>
      <td>10</td>
      <td>10</td>
      <td>10</td>
      <td>10</td>
      <td>10</td>
    </tr>
    <tr>
      <th>eon.com/*</th>
      <td>10</td>
      <td>10</td>
      <td>10</td>
      <td>10</td>
      <td>10</td>
      <td>10</td>
      <td>10</td>
      <td>10</td>
      <td>10</td>
      <td>10</td>
      <td>10</td>
      <td>10</td>
    </tr>
    <tr>
      <th>fresenius.com/*</th>
      <td>5</td>
      <td>10</td>
      <td>10</td>
      <td>10</td>
      <td>10</td>
      <td>10</td>
      <td>10</td>
      <td>10</td>
      <td>10</td>
      <td>10</td>
      <td>10</td>
      <td>10</td>
    </tr>
    <tr>
      <th>freseniusmedicalcare.com/*</th>
      <td>0</td>
      <td>2</td>
      <td>0</td>
      <td>2</td>
      <td>1</td>
      <td>10</td>
      <td>10</td>
      <td>10</td>
      <td>10</td>
      <td>10</td>
      <td>10</td>
      <td>10</td>
    </tr>
    <tr>
      <th>group.rwe/*</th>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>10</td>
      <td>10</td>
      <td>10</td>
      <td>10</td>
    </tr>
    <tr>
      <th>heidelbergcement.com/*</th>
      <td>10</td>
      <td>10</td>
      <td>10</td>
      <td>10</td>
      <td>10</td>
      <td>10</td>
      <td>10</td>
      <td>10</td>
      <td>10</td>
      <td>10</td>
      <td>10</td>
      <td>10</td>
    </tr>
    <tr>
      <th>henkel.com/*</th>
      <td>10</td>
      <td>10</td>
      <td>10</td>
      <td>10</td>
      <td>10</td>
      <td>10</td>
      <td>10</td>
      <td>10</td>
      <td>10</td>
      <td>10</td>
      <td>10</td>
      <td>10</td>
    </tr>
    <tr>
      <th>infineon.com/*</th>
      <td>10</td>
      <td>10</td>
      <td>10</td>
      <td>10</td>
      <td>10</td>
      <td>10</td>
      <td>10</td>
      <td>10</td>
      <td>10</td>
      <td>10</td>
      <td>10</td>
      <td>10</td>
    </tr>
    <tr>
      <th>lindeplc.com/*</th>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>10</td>
      <td>1</td>
      <td>0</td>
      <td>0</td>
    </tr>
    <tr>
      <th>lufthansa.com/*</th>
      <td>10</td>
      <td>10</td>
      <td>10</td>
      <td>10</td>
      <td>10</td>
      <td>10</td>
      <td>10</td>
      <td>10</td>
      <td>10</td>
      <td>10</td>
      <td>10</td>
      <td>10</td>
    </tr>
    <tr>
      <th>merckgroup.com/*</th>
      <td>0</td>
      <td>10</td>
      <td>10</td>
      <td>10</td>
      <td>10</td>
      <td>10</td>
      <td>10</td>
      <td>10</td>
      <td>10</td>
      <td>10</td>
      <td>10</td>
      <td>10</td>
    </tr>
    <tr>
      <th>munichre.com/*</th>
      <td>10</td>
      <td>10</td>
      <td>10</td>
      <td>10</td>
      <td>10</td>
      <td>10</td>
      <td>10</td>
      <td>10</td>
      <td>10</td>
      <td>10</td>
      <td>10</td>
      <td>10</td>
    </tr>
    <tr>
      <th>sap.com/*</th>
      <td>10</td>
      <td>10</td>
      <td>10</td>
      <td>10</td>
      <td>10</td>
      <td>10</td>
      <td>10</td>
      <td>10</td>
      <td>10</td>
      <td>10</td>
      <td>10</td>
      <td>10</td>
    </tr>
    <tr>
      <th>siemens.com/*</th>
      <td>10</td>
      <td>10</td>
      <td>10</td>
      <td>10</td>
      <td>10</td>
      <td>10</td>
      <td>10</td>
      <td>10</td>
      <td>10</td>
      <td>10</td>
      <td>10</td>
      <td>10</td>
    </tr>
    <tr>
      <th>telekom.com/*</th>
      <td>10</td>
      <td>10</td>
      <td>10</td>
      <td>10</td>
      <td>10</td>
      <td>10</td>
      <td>10</td>
      <td>10</td>
      <td>10</td>
      <td>10</td>
      <td>10</td>
      <td>10</td>
    </tr>
    <tr>
      <th>thyssenkrupp.com/*</th>
      <td>10</td>
      <td>10</td>
      <td>10</td>
      <td>10</td>
      <td>10</td>
      <td>10</td>
      <td>10</td>
      <td>10</td>
      <td>10</td>
      <td>10</td>
      <td>10</td>
      <td>10</td>
    </tr>
    <tr>
      <th>volkswagenag.com/*</th>
      <td>10</td>
      <td>10</td>
      <td>10</td>
      <td>10</td>
      <td>10</td>
      <td>10</td>
      <td>10</td>
      <td>10</td>
      <td>10</td>
      <td>10</td>
      <td>10</td>
      <td>10</td>
    </tr>
    <tr>
      <th>vonovia.de/*</th>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>10</td>
      <td>10</td>
      <td>10</td>
      <td>10</td>
      <td>10</td>
      <td>10</td>
      <td>10</td>
    </tr>
    <tr>
      <th>wirecard.com/*</th>
      <td>10</td>
      <td>10</td>
      <td>10</td>
      <td>10</td>
      <td>10</td>
      <td>10</td>
      <td>10</td>
      <td>10</td>
      <td>10</td>
      <td>10</td>
      <td>10</td>
      <td>10</td>
    </tr>
  </tbody>
</table>
</div>
</div>

</div>

</div>

</div>

</div>
<div class="jp-Cell-inputWrapper"><div class="jp-InputPrompt jp-InputArea-prompt">
</div><div class="jp-RenderedHTMLCommon jp-RenderedMarkdown jp-MarkdownOutput " data-mime-type="text/markdown">
<p>Overall we could build a web panel of DAX 30 companies spanning the last 12 years. The size of the web panel comprises</p>

</div>
</div><div class="jp-Cell jp-CodeCell jp-Notebook-cell   ">
<div class="jp-Cell-inputWrapper">
<div class="jp-InputArea jp-Cell-inputArea">

<div class="jp-CodeMirrorEditor jp-Editor jp-InputArea-editor" data-type="inline">
     <div class="CodeMirror cm-s-jupyter">
<div class=" highlight hl-ipython3"><pre><span></span><span class="kn">import</span> <span class="nn">sys</span>
<span class="nb">print</span><span class="p">(</span><span class="nb">str</span><span class="p">(</span><span class="n">sys</span><span class="o">.</span><span class="n">getsizeof</span><span class="p">(</span><span class="n">df</span><span class="p">)</span><span class="o">/</span><span class="mi">1000000</span><span class="p">)</span> <span class="o">+</span> <span class="s1">&#39; MB&#39;</span><span class="p">)</span>
</pre></div>

     </div>
</div>
</div>
</div>

<div class="jp-Cell-outputWrapper">


<div class="jp-OutputArea jp-Cell-outputArea">

<div class="jp-OutputArea-child">

    
    <div class="jp-OutputPrompt jp-OutputArea-prompt"></div>


<div class="jp-RenderedText jp-OutputArea-output" data-mime-type="text/plain">
<pre>35.980528 MB
</pre>
</div>
</div>

</div>

</div>

</div>
<div class="jp-Cell-inputWrapper"><div class="jp-InputPrompt jp-InputArea-prompt">
</div><div class="jp-RenderedHTMLCommon jp-RenderedMarkdown jp-MarkdownOutput " data-mime-type="text/markdown">
<p>This blog post has shown how to create a panel of web data using archived websites on Common Crawl or the Internet Archive. Web content changes over time and without the preservation efforts of these organizations information from the web would get lost. Resembling past information from the web in a structured way allows to analyze dynamics and changing themes on the world wibe web.</p>

</div>
</div>









</body></html>