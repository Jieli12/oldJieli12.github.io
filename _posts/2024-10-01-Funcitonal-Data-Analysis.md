---
title: 'Functional Data Analysis for Density Functions by Transformation to a Hilbert Space'
date: 2024-10-01
permalink: /posts/2024/10/Functional-Data-Analysis/
tags:
  - Density function
  - Hilbert space
  - Functional data analysis
---

  <script type="text/javascript">
    window.MathJax = ({ "tex": { "tags": "ams", "tagSide": "right", "tagIndent": "0.8em", "inlineMath": [["$", "$"], ["\\(", "\\)"]], "displayMath": [["$$", "$$"], ["\\[", "\\]"]] }, "options": {}, "loader": {} });
  </script>
  <script type="text/javascript" async="" src="https://cdn.jsdelivr.net/npm/mathjax@3/es5/tex-mml-chtml.js"
    charset="UTF-8"></script>






  <style>
    code[class*=language-],
    pre[class*=language-] {
      color: #333;
      background: 0 0;
      font-family: Consolas, "Liberation Mono", Menlo, Courier, monospace;
      text-align: left;
      white-space: pre;
      word-spacing: normal;
      word-break: normal;
      word-wrap: normal;
      line-height: 1.4;
      -moz-tab-size: 8;
      -o-tab-size: 8;
      tab-size: 8;
      -webkit-hyphens: none;
      -moz-hyphens: none;
      -ms-hyphens: none;
      hyphens: none
    }

    pre[class*=language-] {
      padding: .8em;
      overflow: auto;
      border-radius: 3px;
      background: #f5f5f5
    }

    :not(pre)>code[class*=language-] {
      padding: .1em;
      border-radius: .3em;
      white-space: normal;
      background: #f5f5f5
    }

    .token.blockquote,
    .token.comment {
      color: #969896
    }

    .token.cdata {
      color: #183691
    }

    .token.doctype,
    .token.macro.property,
    .token.punctuation,
    .token.variable {
      color: #333
    }

    .token.builtin,
    .token.important,
    .token.keyword,
    .token.operator,
    .token.rule {
      color: #a71d5d
    }

    .token.attr-value,
    .token.regex,
    .token.string,
    .token.url {
      color: #183691
    }

    .token.atrule,
    .token.boolean,
    .token.code,
    .token.command,
    .token.constant,
    .token.entity,
    .token.number,
    .token.property,
    .token.symbol {
      color: #0086b3
    }

    .token.prolog,
    .token.selector,
    .token.tag {
      color: #63a35c
    }

    .token.attr-name,
    .token.class,
    .token.class-name,
    .token.function,
    .token.id,
    .token.namespace,
    .token.pseudo-class,
    .token.pseudo-element,
    .token.url-reference .token.variable {
      color: #795da3
    }

    .token.entity {
      cursor: help
    }

    .token.title,
    .token.title .token.punctuation {
      font-weight: 700;
      color: #1d3e81
    }

    .token.list {
      color: #ed6a43
    }

    .token.inserted {
      background-color: #eaffea;
      color: #55a532
    }

    .token.deleted {
      background-color: #ffecec;
      color: #bd2c00
    }

    .token.bold {
      font-weight: 700
    }

    .token.italic {
      font-style: italic
    }

    .language-json .token.property {
      color: #183691
    }

    .language-markup .token.tag .token.punctuation {
      color: #333
    }

    .language-css .token.function,
    code.language-css {
      color: #0086b3
    }

    .language-yaml .token.atrule {
      color: #63a35c
    }

    code.language-yaml {
      color: #183691
    }

    .language-ruby .token.function {
      color: #333
    }

    .language-markdown .token.url {
      color: #795da3
    }

    .language-makefile .token.symbol {
      color: #795da3
    }

    .language-makefile .token.variable {
      color: #183691
    }

    .language-makefile .token.builtin {
      color: #0086b3
    }

    .language-bash .token.keyword {
      color: #0086b3
    }

    pre[data-line] {
      position: relative;
      padding: 1em 0 1em 3em
    }

    pre[data-line] .line-highlight-wrapper {
      position: absolute;
      top: 0;
      left: 0;
      background-color: transparent;
      display: block;
      width: 100%
    }

    pre[data-line] .line-highlight {
      position: absolute;
      left: 0;
      right: 0;
      padding: inherit 0;
      margin-top: 1em;
      background: hsla(24, 20%, 50%, .08);
      background: linear-gradient(to right, hsla(24, 20%, 50%, .1) 70%, hsla(24, 20%, 50%, 0));
      pointer-events: none;
      line-height: inherit;
      white-space: pre
    }

    pre[data-line] .line-highlight:before,
    pre[data-line] .line-highlight[data-end]:after {
      content: attr(data-start);
      position: absolute;
      top: .4em;
      left: .6em;
      min-width: 1em;
      padding: 0 .5em;
      background-color: hsla(24, 20%, 50%, .4);
      color: #f4f1ef;
      font: bold 65%/1.5 sans-serif;
      text-align: center;
      vertical-align: .3em;
      border-radius: 999px;
      text-shadow: none;
      box-shadow: 0 1px #fff
    }

    pre[data-line] .line-highlight[data-end]:after {
      content: attr(data-end);
      top: auto;
      bottom: .4em
    }

    html body {
      font-family: 'Helvetica Neue', Helvetica, 'Segoe UI', Arial, freesans, sans-serif;
      font-size: 16px;
      line-height: 1.6;
      color: #333;
      background-color: #fff;
      overflow: initial;
      box-sizing: border-box;
      word-wrap: break-word
    }

    html body>:first-child {
      margin-top: 0
    }

    html body h1,
    html body h2,
    html body h3,
    html body h4,
    html body h5,
    html body h6 {
      line-height: 1.2;
      margin-top: 1em;
      margin-bottom: 16px;
      color: #000
    }

    html body h1 {
      font-size: 2.25em;
      font-weight: 300;
      padding-bottom: .3em
    }

    html body h2 {
      font-size: 1.75em;
      font-weight: 400;
      padding-bottom: .3em
    }

    html body h3 {
      font-size: 1.5em;
      font-weight: 500
    }

    html body h4 {
      font-size: 1.25em;
      font-weight: 600
    }

    html body h5 {
      font-size: 1.1em;
      font-weight: 600
    }

    html body h6 {
      font-size: 1em;
      font-weight: 600
    }

    html body h1,
    html body h2,
    html body h3,
    html body h4,
    html body h5 {
      font-weight: 600
    }

    html body h5 {
      font-size: 1em
    }

    html body h6 {
      color: #5c5c5c
    }

    html body strong {
      color: #000
    }

    html body del {
      color: #5c5c5c
    }

    html body a:not([href]) {
      color: inherit;
      text-decoration: none
    }

    html body a {
      color: #08c;
      text-decoration: none
    }

    html body a:hover {
      color: #00a3f5;
      text-decoration: none
    }

    html body img {
      max-width: 100%
    }

    html body>p {
      margin-top: 0;
      margin-bottom: 16px;
      word-wrap: break-word
    }

    html body>ol,
    html body>ul {
      margin-bottom: 16px
    }

    html body ol,
    html body ul {
      padding-left: 2em
    }

    html body ol.no-list,
    html body ul.no-list {
      padding: 0;
      list-style-type: none
    }

    html body ol ol,
    html body ol ul,
    html body ul ol,
    html body ul ul {
      margin-top: 0;
      margin-bottom: 0
    }

    html body li {
      margin-bottom: 0
    }

    html body li.task-list-item {
      list-style: none
    }

    html body li>p {
      margin-top: 0;
      margin-bottom: 0
    }

    html body .task-list-item-checkbox {
      margin: 0 .2em .25em -1.8em;
      vertical-align: middle
    }

    html body .task-list-item-checkbox:hover {
      cursor: pointer
    }

    html body blockquote {
      margin: 16px 0;
      font-size: inherit;
      padding: 0 15px;
      color: #5c5c5c;
      background-color: #f0f0f0;
      border-left: 4px solid #d6d6d6
    }

    html body blockquote>:first-child {
      margin-top: 0
    }

    html body blockquote>:last-child {
      margin-bottom: 0
    }

    html body hr {
      height: 4px;
      margin: 32px 0;
      background-color: #d6d6d6;
      border: 0 none
    }

    html body table {
      margin: 10px 0 15px 0;
      border-collapse: collapse;
      border-spacing: 0;
      display: block;
      width: 100%;
      overflow: auto;
      word-break: normal;
      word-break: keep-all
    }

    html body table th {
      font-weight: 700;
      color: #000
    }

    html body table td,
    html body table th {
      border: 1px solid #d6d6d6;
      padding: 6px 13px
    }

    html body dl {
      padding: 0
    }

    html body dl dt {
      padding: 0;
      margin-top: 16px;
      font-size: 1em;
      font-style: italic;
      font-weight: 700
    }

    html body dl dd {
      padding: 0 16px;
      margin-bottom: 16px
    }

    html body code {
      font-family: Menlo, Monaco, Consolas, 'Courier New', monospace;
      font-size: .85em;
      color: #000;
      background-color: #f0f0f0;
      border-radius: 3px;
      padding: .2em 0
    }

    html body code::after,
    html body code::before {
      letter-spacing: -.2em;
      content: '\00a0'
    }

    html body pre>code {
      padding: 0;
      margin: 0;
      word-break: normal;
      white-space: pre;
      background: 0 0;
      border: 0
    }

    html body .highlight {
      margin-bottom: 16px
    }

    html body .highlight pre,
    html body pre {
      padding: 1em;
      overflow: auto;
      line-height: 1.45;
      border: #d6d6d6;
      border-radius: 3px
    }

    html body .highlight pre {
      margin-bottom: 0;
      word-break: normal
    }

    html body pre code,
    html body pre tt {
      display: inline;
      max-width: initial;
      padding: 0;
      margin: 0;
      overflow: initial;
      line-height: inherit;
      word-wrap: normal;
      background-color: transparent;
      border: 0
    }

    html body pre code:after,
    html body pre code:before,
    html body pre tt:after,
    html body pre tt:before {
      content: normal
    }

    html body blockquote,
    html body dl,
    html body ol,
    html body p,
    html body pre,
    html body ul {
      margin-top: 0;
      margin-bottom: 16px
    }

    html body kbd {
      color: #000;
      border: 1px solid #d6d6d6;
      border-bottom: 2px solid #c7c7c7;
      padding: 2px 4px;
      background-color: #f0f0f0;
      border-radius: 3px
    }

    @media print {
      html body {
        background-color: #fff
      }

      html body h1,
      html body h2,
      html body h3,
      html body h4,
      html body h5,
      html body h6 {
        color: #000;
        page-break-after: avoid
      }

      html body blockquote {
        color: #5c5c5c
      }

      html body pre {
        page-break-inside: avoid
      }

      html body table {
        display: table
      }

      html body img {
        display: block;
        max-width: 100%;
        max-height: 100%
      }

      html body code,
      html body pre {
        word-wrap: break-word;
        white-space: pre
      }
    }

    .markdown-preview {
      width: 100%;
      height: 100%;
      box-sizing: border-box
    }

    .markdown-preview ul {
      list-style: disc
    }

    .markdown-preview ul ul {
      list-style: circle
    }

    .markdown-preview ul ul ul {
      list-style: square
    }

    .markdown-preview ol {
      list-style: decimal
    }

    .markdown-preview ol ol,
    .markdown-preview ul ol {
      list-style-type: lower-roman
    }

    .markdown-preview ol ol ol,
    .markdown-preview ol ul ol,
    .markdown-preview ul ol ol,
    .markdown-preview ul ul ol {
      list-style-type: lower-alpha
    }

    .markdown-preview .newpage,
    .markdown-preview .pagebreak {
      page-break-before: always
    }

    .markdown-preview pre.line-numbers {
      position: relative;
      padding-left: 3.8em;
      counter-reset: linenumber
    }

    .markdown-preview pre.line-numbers>code {
      position: relative
    }

    .markdown-preview pre.line-numbers .line-numbers-rows {
      position: absolute;
      pointer-events: none;
      top: 1em;
      font-size: 100%;
      left: 0;
      width: 3em;
      letter-spacing: -1px;
      border-right: 1px solid #999;
      -webkit-user-select: none;
      -moz-user-select: none;
      -ms-user-select: none;
      user-select: none
    }

    .markdown-preview pre.line-numbers .line-numbers-rows>span {
      pointer-events: none;
      display: block;
      counter-increment: linenumber
    }

    .markdown-preview pre.line-numbers .line-numbers-rows>span:before {
      content: counter(linenumber);
      color: #999;
      display: block;
      padding-right: .8em;
      text-align: right
    }

    .markdown-preview .mathjax-exps .MathJax_Display {
      text-align: center !important
    }

    .markdown-preview:not([data-for=preview]) .code-chunk .code-chunk-btn-group {
      display: none
    }

    .markdown-preview:not([data-for=preview]) .code-chunk .status {
      display: none
    }

    .markdown-preview:not([data-for=preview]) .code-chunk .output-div {
      margin-bottom: 16px
    }

    .markdown-preview .md-toc {
      padding: 0
    }

    .markdown-preview .md-toc .md-toc-link-wrapper .md-toc-link {
      display: inline;
      padding: .25rem 0
    }

    .markdown-preview .md-toc .md-toc-link-wrapper .md-toc-link div,
    .markdown-preview .md-toc .md-toc-link-wrapper .md-toc-link p {
      display: inline
    }

    .markdown-preview .md-toc .md-toc-link-wrapper.highlighted .md-toc-link {
      font-weight: 800
    }

    .scrollbar-style::-webkit-scrollbar {
      width: 8px
    }

    .scrollbar-style::-webkit-scrollbar-track {
      border-radius: 10px;
      background-color: transparent
    }

    .scrollbar-style::-webkit-scrollbar-thumb {
      border-radius: 5px;
      background-color: rgba(150, 150, 150, .66);
      border: 4px solid rgba(150, 150, 150, .66);
      background-clip: content-box
    }

    html body[for=html-export]:not([data-presentation-mode]) {
      position: relative;
      width: 100%;
      height: 100%;
      top: 0;
      left: 0;
      margin: 0;
      padding: 0;
      overflow: auto
    }

    html body[for=html-export]:not([data-presentation-mode]) .markdown-preview {
      position: relative;
      top: 0;
      min-height: 100vh
    }

    @media screen and (min-width:914px) {
      html body[for=html-export]:not([data-presentation-mode]) .markdown-preview {
        padding: 2em calc(50% - 457px + 2em)
      }
    }

    @media screen and (max-width:914px) {
      html body[for=html-export]:not([data-presentation-mode]) .markdown-preview {
        padding: 2em
      }
    }

    @media screen and (max-width:450px) {
      html body[for=html-export]:not([data-presentation-mode]) .markdown-preview {
        font-size: 14px !important;
        padding: 1em
      }
    }

    @media print {
      html body[for=html-export]:not([data-presentation-mode]) #sidebar-toc-btn {
        display: none
      }
    }

    html body[for=html-export]:not([data-presentation-mode]) #sidebar-toc-btn {
      position: fixed;
      bottom: 8px;
      left: 8px;
      font-size: 28px;
      cursor: pointer;
      color: inherit;
      z-index: 99;
      width: 32px;
      text-align: center;
      opacity: .4
    }

    html body[for=html-export]:not[[data-presentation-mode]](html-show-sidebar-toc) #sidebar-toc-btn {
      opacity: 1
    }

    html body[for=html-export]:not[[data-presentation-mode]](html-show-sidebar-toc) .md-sidebar-toc {
      position: fixed;
      top: 0;
      left: 0;
      width: 300px;
      height: 100%;
      padding: 32px 0 48px 0;
      font-size: 14px;
      box-shadow: 0 0 4px rgba(150, 150, 150, .33);
      box-sizing: border-box;
      overflow: auto;
      background-color: inherit
    }

    html body[for=html-export]:not[[data-presentation-mode]](html-show-sidebar-toc) .md-sidebar-toc::-webkit-scrollbar {
      width: 8px
    }

    html body[for=html-export]:not[[data-presentation-mode]](html-show-sidebar-toc) .md-sidebar-toc::-webkit-scrollbar-track {
      border-radius: 10px;
      background-color: transparent
    }

    html body[for=html-export]:not[[data-presentation-mode]](html-show-sidebar-toc) .md-sidebar-toc::-webkit-scrollbar-thumb {
      border-radius: 5px;
      background-color: rgba(150, 150, 150, .66);
      border: 4px solid rgba(150, 150, 150, .66);
      background-clip: content-box
    }

    html body[for=html-export]:not[[data-presentation-mode]](html-show-sidebar-toc) .md-sidebar-toc a {
      text-decoration: none
    }

    html body[for=html-export]:not[[data-presentation-mode]](html-show-sidebar-toc) .md-sidebar-toc .md-toc {
      padding: 0 16px
    }

    html body[for=html-export]:not[[data-presentation-mode]](html-show-sidebar-toc) .md-sidebar-toc .md-toc .md-toc-link-wrapper .md-toc-link {
      display: inline;
      padding: .25rem 0
    }

    html body[for=html-export]:not[[data-presentation-mode]](html-show-sidebar-toc) .md-sidebar-toc .md-toc .md-toc-link-wrapper .md-toc-link div,
    html body[for=html-export]:not[[data-presentation-mode]](html-show-sidebar-toc) .md-sidebar-toc .md-toc .md-toc-link-wrapper .md-toc-link p {
      display: inline
    }

    html body[for=html-export]:not[[data-presentation-mode]](html-show-sidebar-toc) .md-sidebar-toc .md-toc .md-toc-link-wrapper.highlighted .md-toc-link {
      font-weight: 800
    }

    html body[for=html-export]:not[[data-presentation-mode]](html-show-sidebar-toc) .markdown-preview {
      left: 300px;
      width: calc(100% - 300px);
      padding: 2em calc(50% - 457px - 300px / 2);
      margin: 0;
      box-sizing: border-box
    }

    @media screen and (max-width:1274px) {
      html body[for=html-export]:not[[data-presentation-mode]](html-show-sidebar-toc) .markdown-preview {
        padding: 2em
      }
    }

    @media screen and (max-width:450px) {
      html body[for=html-export]:not[[data-presentation-mode]](html-show-sidebar-toc) .markdown-preview {
        width: 100%
      }
    }

    html body[for=html-export]:not([data-presentation-mode]):not([html-show-sidebar-toc]) .markdown-preview {
      left: 50%;
      transform: translateX(-50%)
    }

    html body[for=html-export]:not([data-presentation-mode]):not([html-show-sidebar-toc]) .md-sidebar-toc {
      display: none
    }

    /* Please visit the URL below for more information: */
    /*   https://shd101wyy.github.io/markdown-preview-enhanced/#/customize-css */
    .markdown-preview.markdown-preview {
      font-family: sans-serif;
      font-size: 16px;
    }

    .markdown-preview.markdown-preview .r {
      background-color: #f92672;
    }

    .markdown-preview.markdown-preview .g {
      background-color: #a6e22e;
    }

    .markdown-preview.markdown-preview .b {
      background-color: #819aff;
    }

    .markdown-preview.markdown-preview .c {
      background-color: #66d9ef;
    }

    .markdown-preview.markdown-preview .m {
      background-color: #ae81ff;
    }

    .markdown-preview.markdown-preview .y {
      background-color: #e2e22e;
    }

    .markdown-preview.markdown-preview code:not(pre > code) {
      color: #ef52a0;
      background-color: aliceblue;
      padding: 0px;
      /* Adjust padding as needed */
      height: 22px;
      /* Adjust height as needed */
      line-height: 25px;
    }
  </style>
  <!-- The content below will be included at the end of the <head> element. -->
  <script type="text/javascript">
    document.addEventListener("DOMContentLoaded", function () {
      // your code here
    });
  </script>


<body for="html-export">


  <div class="crossnote markdown-preview  ">

    <h1 id="goal">Goal</h1>
    <p>This is the report from my point of view on the paper <em>Functional
        Data Analysis for Density Functions by Transformation to a Hilbert
        Space</em> <span class="citation" data-cites="petersenFunctionalDataAnalysis2016">(<a
          href="#ref-petersenFunctionalDataAnalysis2016" role="doc-biblioref">Petersen and Müller 2016</a>)</span>.</p>
    <ol type="1">
      <li>
        <p>Functional data that are nonnegative and have a constrained
          integral can be considered as samples of one-dimensional density
          function.</p>
      </li>
      <li>
        <p>The density function is nonnegative and has an integral of 1,
          hence commonly used Hilbert space based methods of functional data
          analysis are not applicable.</p>
      </li>
      <li>
        <p>To address this issue, the paper proposes a new method which maps
          the densities to a Hilbert space, where the map is a continuous and
          invertible function.</p>
      </li>
      <li>
        <p>Basic operations are implemented in the Hilbert space, then apply
          the inverse transformation to the density space.</p>
      </li>
    </ol>
    <h1 id="introduction">Introduction</h1>
    <p>The functional modeling of density functions is difficult due to the
      two constrains <span class="math inline">\(\int f(x)\,dx=1\)</span> and
      <span class="math inline">\(f \geq 0\)</span> which means that the
      densities space is <strong>not linear</strong>.
    </p>
    <p>The key idea is to map probability densities into a linear function
      space by using a suitably chosen continuous and invertible map <span class="math inline">\(\psi\)</span>.</p>
    <h1 id="preliminaries">Preliminaries</h1>
    <h2 id="density-modelling">Density modelling</h2>
    <p>Assume that data consist of a sample of <span class="math inline">\(n\)</span> (random) density functions <span
        class="math inline">\(f_1, \ldots, f_n\)</span>, where the densities are
      supported on a common interval <span class="math inline">\([0,T]\)</span> for some <span
        class="math inline">\(T&gt;0\)</span>.</p>
    <p>Denote the space of continuous and strictly positive densities on
      <span class="math inline">\([0,1]\)</span> by <span class="math inline">\(\mathcal{G}\)</span>.
    </p>
    <p>The sample consists of i.i.d. realizations of an underlying
      stochastic process, that is, each density is independently distributed
      as <span class="math inline">\(f\sim\mathfrak{F}\)</span>, where <span class="math inline">\(\mathfrak{F}\)</span>
      is an <span class="math inline">\(L^2\)</span> process on <span class="math inline">\([0,1]\)</span> taking values
      in some space <span class="math inline">\(\mathcal{F}\subset\mathcal{G}\)</span></p>
    <p>A basic assumption we make on the space <span class="math inline">\(\mathcal {F}\)</span> is:</p>
    <div
      style="position: relative; border: 2px solid#ff8618; background-color: #f9f9f9; padding: 15px; margin: 20px 0; font-family: Arial, sans-serif; box-shadow: 2px 2px 10px rgba(0, 0, 0, 0.1); border-radius: 8px;">
      <div
        style="position: absolute; top: -0.85em; left: 15px; background-color:#ff8618; padding: 0 5px; font-weight: bold; color: #f9f9f9; border: 2px solid#ff8618;">
        <span id="assumption:space_F">Assumption 1</span>
      </div>
      <div style="font-style: italic; margin-top: 0.7em;">
        For all <span class="math inline">\(f \in\mathcal{F}\)</span>, <span class="math inline">\(f\)</span> is
        continuously differentiable.
        Moreover, there is a constant <span class="math inline">\(M &gt;
          1\)</span> such that, for all <span class="math inline">\(f
          \in\mathcal{F}\)</span>, <span class="math inline">\(\Vert f
          \Vert_\infty\)</span>, <span class="math inline">\(\Vert 1/f
          \Vert_\infty\)</span> and <span class="math inline">\(\Vert f'
          \Vert_\infty\)</span> are all bounded above by <span class="math inline">\(M\)</span>.
      </div>
      <div
        style="position: absolute; bottom: 10px; right: 10px; text-align: right; font-size: 20px; color:#ff8618; margin-top: 1px;">
        ♥
      </div>
    </div>
    <p>Densities <span class="math inline">\(f\)</span> can equivalently be
      represented as:</p>
    <ol type="1">
      <li>cumulative distribution functions (c.d.f.) <span class="math inline">\(F\)</span> with domain <span
          class="math inline">\([0,1]\)</span>, hazard functions <span class="math inline">\(h=f/(1-F)\)</span>
        (possibly on a subdomain of
        <span class="math inline">\([0,1]\)</span> where <span class="math inline">\(F(x)&lt;1\)</span>).
      </li>
      <li>quantile functions <span class="math inline">\(Q=F^{-1}\)</span>,
        with support <span class="math inline">\([0,1]\)</span>.</li>
      <li>Occasionally of interest is the equivalent notion of the
        quantile-density function <span class="math inline">\(q(t)=Q'(t)=\frac{d}{dt}F^{-1}(t)= [f(Q(t))
          ]^{-1}\)</span>, from which we obtain <span class="math inline">\(f(x)=
          [q(F(x)) ]^{-1}\)</span>.</li>
    </ol>
    <p>All of these functions provide equivalent characterizations of
      distributions.</p>
    <p>In many situations, the densities themselves will not be directly
      observed. Instead, for each <span class="math inline">\(i\)</span>, we
      may observe an i.i.d. sample of data <span class="math inline">\(W_{il}\)</span>, <span class="math inline">\(l =
        1, \ldots, N_i\)</span>, that are generated by the random density <span class="math inline">\(f_i\)</span>.</p>
    <p>Thus, there are two random mechanisms at work that are assumed to be
      independent: the first generates the sample of densities and the second
      generates the samples of real-valued random data; one sample for each
      random density in the sample of densities.</p>
    <p>Hence, the probability space can be thought of as a product space
      <span class="math inline">\((\Omega_1\times\Omega_2, \mathcal{A},
        P)\)</span>, where <span class="math inline">\(P = P_1 \otimes
        P_2\)</span>.
    </p>
    <h2 id="metrics-in-the-space-of-density-functions">Metrics in the space
      of density functions</h2>
    <p>In previous applied and methodological work, it was found that a
      metric <span class="math inline">\(d_{Q}\)</span> based on quantile
      functions <span class="math inline">\({d_{Q}(f,g)^2=\int_0^1
        (F^{-1}(t)-G^{-1}(t))^2 \,\mathrm{d}t}\)</span> is particularly
      promising from a practical point of view.</p>
    <p>This quantile metric has connections to the optimal transport problem
      , and corresponds to the Wasserstein metric between two probability
      measures,</p>
    <p><span class="math display">\[
        \begin{equation}\label{eq:wass_dist}
        d_W(f,g)^2 = \inf_{X \sim f, Y \sim g}E(X - Y)^2,
        \end{equation}
        \]</span></p>
    <p>where the expectation is with respect to the joint distribution of
      <span class="math inline">\((X, Y)\)</span>. The equivalence <span class="math inline">\(d_{Q}=d_{W}\)</span> can
      be most easily seen by
      applying a covariance identity, details can be found in the
      supplementary material.
    </p>
    <p>We will develop our methodology for a general metric, which will be
      denoted by <span class="math inline">\(d\)</span> in the following, and
      may stand for any of the above metrics in the space of densities.</p>
    <h2 id="density-estimation">Density estimation</h2>
    <p>The densities themselves must first be estimated.</p>
    <p>Consider the estimation of a density <span class="math inline">\(f
        \in\mathcal{F}\)</span> from an i.i.d. sample (generated by <span class="math inline">\(f\)</span>) of size
      <span class="math inline">\(N\)</span> by an estimator <span class="math inline">\(\check{f}\)</span>. Here, <span
        class="math inline">\(N = N(n)\)</span> will implicitly represent a
      sequence that depends on <span class="math inline">\(n\)</span>, the
      size of the sample of random densities.</p>
    <p>For the theoretical results, a density estimator <span class="math inline">\(\check{f}\)</span> must satisfy the
      following
      consistency properties in terms of the <span class="math inline">\(L^2\)</span> and uniform metrics (denoted as
      <span class="math inline">\(d_2\)</span> and <span class="math inline">\(d_{\infty}\)</span>, resp.):</p>
    <ol type="1">
      <li>For a sequence <span class="math inline">\(b_N = o(1)\)</span>, the
        density estimator <span class="math inline">\(\check{f}\)</span>, based
        on an i.i.d. sample of size <span class="math inline">\(N\)</span>,
        satisfies <span class="math inline">\(\check{f}\geq0\)</span>, <span class="math inline">\(\int_0^1\check{f}(x)
          \,dx = 1\)</span> and</li>
    </ol>
    <p><span class="math display">\[
        \begin{equation}\label{eq:d1}
        \sup_{f\in\mathcal {F}} E\bigl(d_2(f, \check{f})^2
        \bigr) = O\bigl(b_N^2\bigr).
        \end{equation}
        \]</span></p>
    <ol type="1">
      <li>For a sequence <span class="math inline">\(a_N = o(1)\)</span> and
        some <span class="math inline">\(R &gt; 0\)</span>, the density
        estimator <span class="math inline">\(\check{f}\)</span>, based on an
        i.i.d. sample of size <span class="math inline">\(N\)</span>,
        satisfies</li>
    </ol>
    <p><span class="math display">\[
        \begin{equation}\label{eq:d2}
        \sup_{f \in\mathcal {F}}P\bigl(d_{\infty}(f, \check{f}) &gt; Ra_N\bigr)
        \rightarrow 0.
        \end{equation}
        \]</span></p>
    <div style="padding: 0.8rem 1rem; border-radius: 6px; margin: 1rem 0; background-color:#e2daf1">
      <p style="position: relative; top: -0.6rem;">
        ✋
        <strong style="color: #38225d; position: relative; top: -0rem;">Note</strong>
      </p>
      <p style="margin: 0;position: relative; top: -1rem; text-align: left; margin-bottom: -1rem;line-height:1.3;">
        The standard kernel density estimator does not satisfy these
        assumptions, due to boundary effects. Much work has been devoted to
        rectify the boundary effects, but the resulting estimators leave the
        density space and have not been shown to satisfy \eqref{eq:d1} and
        \eqref{eq:d2}.
      </p>
    </div>
    <p>Therefore, we introduce here a modified density estimator of kernel
      type that is guaranteed to satisfy \eqref{eq:d1} and \eqref{eq:d2}.</p>
    <p>Let $$ be a kernel that corresponds to a continuous probability
      density function and <span class="math inline">\(h &lt; 1/2\)</span> be
      the bandwidth. We define a new kernel density estimator to estimate the
      density <span class="math inline">\(f \in\mathcal {F}\)</span> on <span class="math inline">\([0,1]\)</span> from
      a sample <span class="math inline">\(W_1,\ldots,W_N \stackrel {\mathrm{i.i.d.}}{\sim}
        f\)</span> by</p>
    <p><span class="math display">\[
        \begin{equation}\label{eq:dens_est}
        \check{f}(x) = \sum_{l = 1}^N
        \kappa \biggl(\frac{x - W_l}{h} \biggr)w(x, h) \bigg/ \sum
        _{l = 1}^N \int_0^1
        \kappa \biggl(\frac{y - W_l}{h} \biggr)w(y, h) \,dy,
        \end{equation}
        \]</span></p>
    <p>for <span class="math inline">\(x \in[0,1]\)</span> and <span class="math inline">\(0\)</span> elsewhere.</p>
    <p>Here, the kernel <span class="math inline">\(\kappa\)</span> is
      assumed to satisfy the following additional conditions:</p>
    <ol type="1">
      <li>
        <p>(K1) The kernel <span class="math inline">\(\kappa\)</span> is of
          bounded variation and is symmetric about <span class="math inline">\(0\)</span>.</p>
      </li>
      <li>
        <p>(K2) The kernel <span class="math inline">\(\kappa\)</span>
          satisfies <span class="math inline">\(\int_0^1 \kappa (u) \,du&gt;
            0\)</span>, and <span class="math inline">\(\int_\mathbb{R} |u|\kappa
            (u) \,du\)</span>, <span class="math inline">\(\int_\mathbb{R}
            \kappa^2(u) \,du\)</span> and <span class="math inline">\(\int_\mathbb{R} |u|\kappa ^2(u) \,du\)</span> are
          finite.</p>
      </li>
    </ol>
    <p>The weight function</p>
    <p><span class="math display">\[
        \begin{equation}\label{eq:jackknife_kernel_weight}
        w(x, h)=
        \begin{cases}
        \biggl(\int_{-x/h}^1
        \kappa (u) \,du \biggr)^{-1}&amp; \quad \text{for } x\in[0,h), \\
        \biggl(\int_{-1}^{(1-x)/h} \kappa (u) \,du
        \biggr)^{-1},&amp;\quad \text{for } x\in (1-h,1] \\
        1 &amp; \quad \text{otherwise} \\
        \end{cases}
        \end{equation}
        \]</span></p>
    <p>is designed to remove boundary bias.</p>
    <p>The following result demonstrates that this modified kernel estimator
      indeed satisfies conditions \eqref{eq:d1} and \eqref{eq:d2}.
      Furthermore, this result provides the rate in \eqref{eq:d1} for this
      estimator as <span class="math inline">\(b_N = N^{-1/3}\)</span>, which
      is known to be the optimal rate under our assumptions, where the class
      of densities <span class="math inline">\(\mathcal {F}\)</span> is
      assumed to be continuously differentiable, and it also shows that rates
      <span class="math inline">\(a_N = N^{-c}\)</span>, for any <span class="math inline">\(c \in(0, 1/6)\)</span> are
      possible in
      \eqref{eq:d1}.
    </p>
    <div
      style="position: relative; border: 2px solid#00aef7; background-color: #f9f9f9; padding: 15px; margin: 20px 0; font-family: Arial, sans-serif; box-shadow: 2px 2px 10px rgba(0, 0, 0, 0.1); border-radius: 8px;">
      <div
        style="position: absolute; top: -0.85em; left: 15px; background-color:#00aef7; padding: 0 5px; font-weight: bold; color: #f9f9f9; border: 2px solid#00aef7;">
        <span id="proposition:prop1">Proposition 1</span>
      </div>
      <div style="font-style: italic; margin-top: 0.7em;">
        If <a href="#assumption:space_F"><span style="color: #3c71b7;">Assumption 1</span></a>, (K1) and (K2) hold,
        then the modified kernel density estimator \eqref{eq:dens_est} satisfies
        assumption \eqref{eq:d1} whenever <span class="math inline">\(h
          \rightarrow 0\)</span> and <span class="math inline">\(Nh \rightarrow
          \infty\)</span> as <span class="math inline">\(N\rightarrow
          \infty\)</span> with <span class="math inline">\(b_N^2 =h^2 +
          (Nh)^{-1}\)</span>. By taking <span class="math inline">\(h =
          N^{-1/3}\)</span> and <span class="math inline">\(a_N = N^{-c}\)</span>
        for any <span class="math inline">\(c\in(0, 1/6)\)</span>, \eqref{eq:d1}
        is also satisfied. In S1, we may take <span class="math inline">\(m(n)
          =n^r\)</span> for any <span class="math inline">\(r &gt; 0\)</span>.
      </div>
      <div
        style="position: absolute; bottom: 10px; right: 10px; text-align: right; font-size: 20px; color:#00aef7; margin-top: 1px;">
        ♠
      </div>
    </div>
    <h1 id="functional-data-analysis-for-density-process">Functional data
      analysis for density process</h1>
    <p>For a generic density function process <span class="math inline">\(f
        \sim\mathfrak{F}\)</span>, denote:</p>
    <ol type="1">
      <li>
        <p>the mean function by <span class="math inline">\(\mu(x) =
            E(f(x))\)</span>,</p>
      </li>
      <li>
        <p>the covariance function by <span class="math inline">\(G(x,y) =
            \operatorname{Cov}(f(x), f(y))\)</span>,</p>
      </li>
      <li>
        <p>the orthonormal eigenfunctions and eigenvalues of the linear
          covariance operator <span class="math display">\[
            \begin{equation}
            (Af)(t)=\int G(s,t)f(s) \,\mathrm{d}s
            \end{equation}
            \]</span></p>
      </li>
    </ol>
    <p>by <span class="math inline">\(\{\phi_k\}_{k = 1}^ \infty\)</span>
      and <span class="math inline">\(\{\lambda_k\}_{k = 1}^\infty\)</span>,
      where the latter are positive and in decreasing order.</p>
    <p>If <span class="math inline">\(f_1, \ldots, f_n\)</span> are i.i.d.
      distributed as <span class="math inline">\(f\)</span>, then by the
      Karhunen–Loève expansion, for each <span class="math inline">\(i\)</span>,</p>
    <p><span class="math display">\[
        \begin{equation}\label{eq:eq KL}
        f_i(x) = \mu(x) + \sum_{k = 1}^ \infty
        \xi_{ik} \phi_k(x),
        \end{equation}
        \]</span></p>
    <p>where <span class="math inline">\(\xi_{ik} = \int_0^1 (f_i(x) -
        \mu(x))\phi_k(x) \,\mathrm{d}x\)</span> are the uncorrelated principal
      components with zero mean and variance <span class="math inline">\(\lambda_k\)</span>. The Karhunen–Loève
      expansion
      constitutes the foundation for the commonly used FPCA technique.</p>
    <p>The next part of this section is on the estimation of the mode of
      variation, i.e., the eigenfunctions. This part is the routine part of
      the FPCA, and I will skip it.</p>
    <h1 id="transformation-approach">Transformation approach</h1>
    <ol type="1">
      <li>
        <p>The proposed transformation approach is to map the densities into
          a new space <span class="math inline">\(L^2(\mathcal {T})\)</span> via a
          functional transformation <span class="math inline">\(\psi\)</span>,
          where <span class="math inline">\(\mathcal{T} \subset\mathbb
            {R}\)</span> is a compact interval.</p>
      </li>
      <li>
        <p>Then we work with the resulting <span class="math inline">\(L^2\)</span> process <span
            class="math inline">\(X: = \psi(f)\)</span></p>
      </li>
      <li>
        <p>By performing FPCA in the linear space <span class="math inline">\(L^2(\mathcal {T})\)</span> and then
          mapping back
          to density space, this transformation approach can be viewed as an
          intrinsic analysis, as opposed to ordinary FPCA.</p>
      </li>
    </ol>
    <p>In the new space <span class="math inline">\(L^2(\mathcal{T})\)</span>:</p>
    <ul>
      <li><span class="math inline">\(\nu\)</span> and <span class="math inline">\(H\)</span> denoting the mean and
        covariance
        functions, respectively, of the process <span class="math inline">\(X\)</span>.</li>
      <li><span class="math inline">\(\{\rho_k\}_{k= 1}^\infty\)</span>
        denoting the orthonormal eigenfunctions of the covariance</li>
      <li><span class="math inline">\(\{\eta_k\}_{k= 1}^\infty\)</span> is the
        corresponding eigenvalues,</li>
    </ul>
    <p>The Karhunen–Loeve expansion for each of the transformed processes
      <span class="math inline">\(X_i = \psi(f_i)\)</span> is
    </p>
    <p><span class="math display">\[
        \begin{equation*}
        X_i(t) = \nu(t) + \sum_{k = 1}^\infty
        \eta_{ik}\rho_k(t), \qquad t \in \mathcal {T},
        \end{equation*}
        \]</span></p>
    <p>with principal components <span class="math inline">\(\eta_{ik} =
        \int_\mathcal {T} (X_i(t) - \nu(t))\rho_k(t) \,dt\)</span>.</p>
    <p><span style="background-color:yellow">Our goal is to find suitable
        transformations <span class="math inline">\(\psi: \mathcal{G}\rightarrow
          L^2(\mathcal{T})\)</span> from density space to a linear functional
        space</span>.</p>
    <p>We begin with two specific examples of relevant transformations. For
      clarity, for functions in the native density space <span class="math inline">\(\mathcal {G}\)</span> we denote the
      argument by
      <span class="math inline">\(x\)</span>, while for functions in the
      transformed space <span class="math inline">\(L^2(\mathcal{T})\)</span>
      the argument is <span class="math inline">\(t\)</span>.
    </p>
    <h2 id="the-log-hazard-transformation">The log hazard
      transformation</h2>
    <p>Since hazard functions diverge at the right endpoint of the
      distribution, which is 1, we consider quotient spaces induced by
      identifying densities which are equal on a subdomain <span class="math inline">\(\mathcal {T} = [0,
        {1_\delta}]\)</span>, where
      <span class="math inline">\({1_\delta}= 1 -\delta\)</span> for some
      <span class="math inline">\(0 &lt;\delta&lt; 1\)</span>. With a slight
      abuse of notation, we denote this quotient space as <span class="math inline">\(\mathcal {G}\)</span> as well.
    </p>
    <p>The log hazard transformation <span class="math inline">\(\psi_H:
        \mathcal{G} \rightarrow L^2(\mathcal {T})\)</span> is <span class="math display">\[
        \begin{equation*}
        \psi_H(f) (t)= \log\bigl(h(t)\bigr) = \log \biggl\{
        \frac{f(t)}{1-F(t)} \biggr\}, \qquad t \in\mathcal {T}.
        \end{equation*}
        \]</span></p>
    <p>Since the hazard function is positive but otherwise not constrained
      on <span class="math inline">\(\mathcal {T}\)</span>, it is easy to see
      that <span class="math inline">\(\psi\)</span> indeed maps density
      functions to <span class="math inline">\(L^2(\mathcal {T})\)</span>. The
      inverse map can be defined for any continuous function <span class="math inline">\(X\)</span> as</p>
    <p><span class="math display">\[
        \begin{equation*}
        \psi_H^{-1}(X) (x) = \exp \biggl\{X(x) - \int_0^x e^{X(s)} \,ds
        \biggr\} ,\qquad x \in[0,
        {1_\delta}].
        \end{equation*}
        \]</span></p>
    <p>Solving the differential equation <span class="math display">\[
        \begin{equation*}
        h(t)=\frac{f(t)}{1-F(t)}=\frac{F'(t)}{1-F(t)}
        \end{equation*}
        \]</span> for <span class="math inline">\(F(t)\)</span>, it can be shown
      that <span class="math display">\[
        \begin{equation*}
        F(t) = 1 - \exp{\left(-\int_0^t h(t) dt \right)}
        \end{equation*}
        \]</span></p>
    <p>Note that for this case one has a strict inverse only modulo the
      quotient space. However, in order to use metrics such as <span class="math inline">\(d_W\)</span>, we must choose
      a representative.
      A~straightforward way to do this is to assign the remaining mass
      uniformly, that is,</p>
    <p><span class="math display">\[
        \begin{equation*}
        \psi_H^{-1}(X) (x) = \delta^{-1}\exp{\biggl\{ -
        \int_{0}^{1_{\delta}} e^{X(s)} \,ds \biggr\}},\qquad x
        \in(1_{\delta}, 1].
        \end{equation*}
        \]</span></p>
    <h2 id="the-log-quantile-density-transformation">The log quantile
      density transformation</h2>
    <p>For <span class="math inline">\(\mathcal {T} = [0,1]\)</span>, the
      log quantile density (LQD) transformation <span class="math inline">\(\psi_Q: \mathcal {G}\rightarrow
        L^2(\mathcal{T})\)</span> is given by</p>
    <p><span class="math display">\[
        \begin{equation*}
        \psi_Q(f) (t) = \log\bigl(q(t)\bigr) = -\log\bigl\{f\bigl(Q(t)
        \bigr)\bigr\}, \qquad t \in\mathcal {T}.
        \end{equation*}
        \]</span></p>
    <p>It is then natural to define the inverse of a continuous function
      <span class="math inline">\(X\)</span> on <span class="math inline">\(\mathcal {T}\)</span> as the density given
      by
      <span class="math inline">\(\exp\{-X(F(x))\}\)</span>, where <span class="math inline">\(Q(t)=F^{-1}(t) = \int_0^t
        e^{X(s)} \,ds\)</span>.
      Since the value <span class="math inline">\(F^{-1}(1)\)</span> is not
      fixed, the support of the densities is not fixed within the transformed
      space, and as the inverse transformation should map back into the space
      of densities with support on <span class="math inline">\([0,
        1]\)</span>, we make a slight adjustment when defining the inverse
      by
    </p>
    <p><span class="math display">\[
        \begin{equation*}
        \psi_Q^{-1}(X) (x) = \theta_X\exp\bigl\{-X
        \bigl(F(x)\bigr)\bigr\},\qquad F^{-1}(t) = \theta _X^{-1}
        \int_0^t e^{X(s)} \,ds,
        \end{equation*}
        \]</span></p>
    <p>where <span class="math inline">\(\theta_X = \int_0^1 e^{X(s)}
        \,ds\)</span>. Since <span class="math inline">\(F^{-1}(1) = 1\)</span>
      whenever <span class="math inline">\(X\in\psi_Q (\mathcal {G}
        )\)</span>, this definition coincides with the natural definition
      mentioned above on <span class="math inline">\(\psi_Q (\mathcal{G}
        )\)</span>.</p>
    <p>In the transformation approach we construct modes of variation in the
      transformed space for processes <span class="math inline">\(X =
        \psi(f)\)</span> and then map these back into the density space,
      defining transformation modes of variation</p>
    <p><span class="math display">\[
        \begin{equation}\label{eq:tmodes}
        g_k(x, \alpha, \psi) = \psi^{-1} (\nu+\alpha\sqrt{\tau _k}\rho _k ) (x).
        \end{equation}
        \]</span></p>
    <p>Estimation of these modes is done by first estimating the mean
      function <span class="math inline">\(\nu\)</span> and covariance
      function <span class="math inline">\(H\)</span> of the process <span class="math inline">\(X\)</span>. Letting
      <span class="math inline">\(\widehat {X}_i =\psi(\check{f}_i)\)</span>, the
      empirical estimators are</p>
    <p><span class="math display">\[
        \begin{eqnarray}
        \label{eq:nu_est}
        \tilde{\nu}(t) &amp;= &amp;\frac{1}{n}\sum_{i=1}^nX_i(t)\quad
        \mbox{respectively}\quad \hat{\nu}(t) = \frac{1}{n}\sum
        _{i=1}^n\widehat {X}_i(t);
        \\\label{eq:H_est}
        \widetilde {H}(s,t) &amp;=&amp; \frac{1}{n}\sum_{i=1}^nX_i(s)X_i(t)
        - \tilde {\nu}(s)\tilde{\nu}(t)\quad \mbox {respectively}
        \nonumber
        \\[-8pt]
        \\[-8pt]
        \nonumber
        \widehat {H}(s,t) &amp;=&amp; \frac{1}{n}\sum_{i=1}^n
        \widehat {X}_i(s)\widehat {X}_i(t) - \hat{\nu}(s)\hat{
        \nu} (t).
        \end{eqnarray}
        \]</span></p>
    <p>Estimated eigenvalues and eigenfunctions (<span class="math inline">\(\tilde{\tau}_k\)</span> and <span
        class="math inline">\(\tilde{\rho}_k\)</span>, resp., <span class="math inline">\(\hat{\tau}_k\)</span> and
      <span class="math inline">\(\hat{\rho}_k\)</span>) are then obtained from the
      mean and covariance estimates as before, yielding the transformation
      mode of variation estimators <span class="math display">\[
        \begin{eqnarray}\label{eq:tmodes_est}
        \tilde{g}_k(x, \alpha, \psi) &amp;=&amp; \psi^{-1}(\tilde{\nu}+
        \alpha \sqrt {\tilde{\tau}_k}\tilde{\rho} _k) (x)\quad
        \mbox{respectively}
        \nonumber
        \\[-8pt]
        \\[-8pt]
        \nonumber
        \hat{g}_k(x, \alpha, \psi) &amp;= &amp;\psi^{-1}(\hat{\nu}+ \alpha
        \sqrt {\hat{\tau} _k}\hat{\rho} _k) (x).
        \nonumber
        \end{eqnarray}
        \]</span></p>
    <p>In contrast to the modes of variation resulting from ordinary FPCA in
      Section 3, the transformation modes are bona fide density functions for
      any value of <span class="math inline">\(\alpha\)</span>. Thus, for
      reasonably chosen transformations, the transformation modes can be
      expected to provide a more interpretable description of the variability
      contained in the sample of densities. Indeed, the data application in
      Section 6.2 shows that this is the case, using the log quantile density
      transformation as an example.</p>
    <p>The truncated representations of the original densities in the sample
      are then given by</p>
    <p><span class="math display">\[
        \begin{equation}\label{eq:fnt_trnc1}
        f_i(x, K, \psi) = \psi^{-1} \Biggl(\nu+
        \sum_{k = 1}^K \eta _{ik}\rho
        _k \Biggr) (x).
        \end{equation}
        \]</span></p>
    <p>Utilizing (\ref{eq:nu_est}) and the ensuing estimates of the
      eigenfunctions, the (transformation) principal components, for the case
      of fully observed densities, are obtained in a straightforward
      manner,</p>
    <p><span class="math display">\[
        \begin{equation}
        \label{eq:pc_est}
        \tilde{\eta}_{ik}= \int_\mathcal {T}
        \bigl(X_i(t) - \tilde{\nu }(t)\bigr)\tilde{\rho}_k(t)
        \,dt,
        \end{equation}
        \]</span></p>
    <p>whence <span class="math display">\[
        \begin{equation*}
        \tilde{f}_i(x, K, \psi) = \psi^{-1} \Biggl(\tilde{\nu}+
        \sum_{k =1}^K \tilde{\eta}_{ik}\tilde{\rho} _k \Biggr) (x).
        \end{equation*}
        \]</span></p>
    <p>In practice, the truncation point <span class="math inline">\(K\)</span> can be selected by choosing a cutoff
      for the fraction of variance explained. This raises the question of how
      to quantify \emph{total variance}. For the chosen metric <span class="math inline">\(d\)</span>, we propose to use
      the Frechet
      variance</p>
    <p><span class="math display">\[
        \begin{equation}\label{eq:tot_var}
        V_\infty:= E\bigl(d(f, f_\oplus )^2\bigr),
        \end{equation}
        \]</span> where $f_\oplus $ is the Frechet mean of the densities in the
      sample. which is estimated by its empirical version</p>
    <p><span class="math display">\[
        \begin{equation}\label{eq:tot_var_est}
        \tilde{V}_\infty = \frac{1}{n}\sum_{i=1}^nd(f_i, \tilde{f}_\oplus)^2,
        \end{equation}
        \]</span></p>
    <p>using an estimator $\tilde{f}_\oplus $ of the Frechet mean.
      Truncating at <span class="math inline">\(K\)</span> included components
      as in (\ref{eq:fnt_trnc1}) and denoting the truncated versions as <span class="math inline">\(f_{i,K}\)</span>,
      the variance explained by the
      first <span class="math inline">\(K\)</span> components is</p>
    <p><span class="math display">\[
        \begin{equation}\label{eq:var_ex}
        V_K:= V_\infty - E\bigl(d(f_1,
        f_{1, K})^2\bigr),
        \end{equation}
        \]</span></p>
    <p>which is estimated by</p>
    <p><span class="math display">\[
        \begin{equation}\label{eq:var_ex_est}
        \tilde{V}_K= \tilde{V}_\infty -
        \frac{1}{n}\sum_{i=1}^nd(f_i,
        \tilde{f}_{i, K})^2.
        \end{equation}
        \]</span></p>
    <p>The ratio $V_K/V_\infty $ is called the fraction of variance
      explained (FVE), and is estimated by <span class="math inline">\(\tilde{V}_K/\tilde{V}_\infty\)</span>. If the
      truncation level is chosen so that a fraction <span class="math inline">\(p\)</span>, <span
        class="math inline">\(0 &lt; p
        &lt; 1\)</span>, of total variation is to be explained, the optimal
      choice of <span class="math inline">\(K\)</span> is</p>
    <p><span class="math display">\[
        \begin{equation}
        \label{eq:choice_K} K^\ast= \min \biggl\{K : \frac{V_K}{V_\infty} &gt; p
        \biggr
        \},
        \end{equation}
        \]</span></p>
    <p>which is estimated by</p>
    <p><span class="math display">\[
        \begin{equation}\label{eq:choice_K_est}
        \tilde{K}^\ast= \min \biggl\{K : \frac{\tilde{V}_K}{\tilde{V}_\infty}
        &gt; p\biggr\}.
        \end{equation}
        \]</span></p>
    <p>As will be demonstrated in the data illustrations, this more general
      notion of variance explained is a useful concept when dealing with
      densities or other functions that are not in a Hilbert space.
      Specifically, we will show that density representations in
      \eqref{eq:fnt_trnc1}, obtained via transformation, yield higher FVE
      values than the ordinary representations, thus giving more efficient
      representations of the sample of densities.</p>
    <div style="padding: 0.8rem 1rem; border-radius: 6px; margin: 1rem 0; background-color:#e0f2ff">
      <p style="position: relative; top: -0.6rem;">
        ❗
        <strong style="color: #443309; position: relative; top: -0rem;">Important</strong>
      </p>
      <p style="margin: 0;position: relative; top: -1rem; text-align: left; margin-bottom: -1rem;line-height:1.3;">
        The R code for the transformation approach (only log density
        transformation) is available in the package <a
          href="https://cran.r-project.org/web/packages/fdadensity/index.html">fdadensity</a>.
        There is no R code for the log hazard transformation.
      </p>
    </div>
    <h1 class="unnumbered" id="reference">Reference</h1>
    <div id="refs" class="references csl-bib-body hanging-indent" data-entry-spacing="0" role="list">
      <div id="ref-petersenFunctionalDataAnalysis2016" class="csl-entry" role="listitem">
        Petersen, Alexander, and Hans-Georg Müller. 2016. <span>“Functional
          <span>Data Analysis</span> for <span>Density Functions</span> by
          <span>Transformation</span> to a <span>Hilbert Space</span>.”</span>
        <em>The Annals of Statistics</em> 44 (1): 183–218. <a
          href="https://doi.org/10.1214/15-AOS1363">https://doi.org/10.1214/15-AOS1363</a>.
      </div>
    </div>

  </div>









</body>