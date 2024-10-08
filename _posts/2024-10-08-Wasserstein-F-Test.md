---
title: 'Wasserstein F-tests and confidence bands for the Frechet regression of density response curves'
date: 2024-10-08
permalink: /posts/2024/10/Wasserstein-F-Test/
tags:
  - Density function
  - F test
  - Functional data analysis
  - Frechet regression
  - Confidence bands
---


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





  <div class="crossnote markdown-preview  ">

    <h1 id="abstract">Abstract</h1>
    <p>This is the report from my point of view on the paper <em>Wasserstein
        <span class="math inline">\(F\)</span>-Tests and Confidence Bands for
        the Frechet Regression of Density Response Curves</em> <span class="citation"
        data-cites="petersenWasserstein$F$testsConfidence2021">(<a href="#ref-petersenWasserstein$F$testsConfidence2021"
          role="doc-biblioref">Petersen, Liu, and Divani 2021</a>)</span>.</p>
    <p>In many applications, density curves appear as functional response
      objects in a regression model with vector predictors. It is important to
      understand the so-called “density-predictor” relationship. In this case,
      the conditional mean is defined as the <strong>conditional Fréchet
        means</strong> under a suitable metric.</p>
    <p><span class="citation" data-cites="petersenWasserstein$F$testsConfidence2021">Petersen, Liu,
        and Divani (<a href="#ref-petersenWasserstein$F$testsConfidence2021" role="doc-biblioref">2021</a>)</span>
      considered the Fréchet regression
      of density curve responses and developed tests for global and partial
      effects, as well as the simultaneous confidence bands for estimated
      conditional mean densities.</p>
    <h1 id="introduction">Introduction</h1>
    <p>In this paper, <span class="citation" data-cites="petersenWasserstein$F$testsConfidence2021">Petersen, Liu,
        and Divani (<a href="#ref-petersenWasserstein$F$testsConfidence2021" role="doc-biblioref">2021</a>)</span> study
      a regression model with
      density functions as response variables under the Wasserstein geometry,
      with predictors being Euclidean vectors. They assume a global regression
      model that does not require any smoothing or other tuning parameter to
      fit.</p>
    <h1 id="preliminaries">Preliminaries</h1>
    <p>We begin with a brief definition of the Wasserstein metric in the
      language of <strong>optimal transport</strong>.</p>
    <p>Let <span class="math inline">\(\mathcal{D}\)</span> be the
      <strong>class of univariate probability density functions</strong> <span class="math inline">\(f\)</span> that
      satisfy <span class="math inline">\(\int_{\mathbb{R}} u^2 f(u) \mathrm{d} u &lt;
        \infty\)</span>, i.e.&nbsp;absolutely continuous distributions on with a
      finite second moment.
    </p>
    <p>For <span class="math inline">\(f\)</span>, <span class="math inline">\(g \in \mathcal{D}\)</span>, consider the
      collection of maps <span class="math inline">\(\mathcal{M}_{f,g}\)</span> such that, if <span
        class="math inline">\(U \sim f\)</span> and <span class="math inline">\(M \in \mathcal{M}_{f,g}\)</span>, then
      <span class="math inline">\(M(U) \sim g\)</span>. The squared Wasserstein
      distance between these two distributions is <span class="math display">\[
        \begin{equation*}
        d_{\mathrm{W}}^{2}(f, g) \coloneqq \inf_{M \in \mathcal{M}_{f,g}}
        \int_{\mathbb{R}} \left(M(u) - u\right)^2 f(u) \mathrm{d} u.
        \end{equation*}
        \]</span></p>
    <p>It is well known that the infimum above is attained by the optimal
      transport map <span class="math inline">\(M_{f,g}^{\textrm{opt}} =
        G^{-1} \circ F\)</span>, where <span class="math inline">\(F\)</span>
      and <span class="math inline">\(G\)</span> are the cumulative
      distribution functions of <span class="math inline">\(f\)</span> and
      <span class="math inline">\(g\)</span>, respectively, leading to the
      closed forms <span class="math display">\[
        \begin{equation}\label{eq: wass2}
        d_{\mathrm{W}}^{2}(f, g) = \int_\mathbb{R}
        \left(M_{f,g}^{\textrm{opt}}(u) - u\right)^2 f(u) \mathrm{d} u =
        \int_0^1 \left(F^{-1}(t) - G^{-1}(t)\right)^2\mathrm{d} t,
        \end{equation}
        \]</span> where the last equality follows by the change of variables
      <span class="math inline">\(t = F(u).\)</span>
    </p>
    <div style="padding: 0.8rem 1rem; border-radius: 6px; margin: 1rem 0; background-color:#e2daf1">
      <p style="position: relative; top: -0.6rem;">
        ✋
        <strong style="color: #38225d; position: relative; top: -0rem;">Note</strong>
      </p>
      <p style="margin: 0;position: relative; top: -1rem; text-align: left; margin-bottom: -1rem;line-height:1.3;">
        In this circumstance, the Wasserstein distance can be calculated using
        the quantile functions of the two distributions.
      </p>
    </div>
    <h2 id="random-densities">Random densities</h2>
    <p>A <strong>random density <span class="math inline">\(\mathfrak{F}\)</span></strong> is a random
      variable taking its values almost surely in <span class="math inline">\(\mathcal{D}\)</span>.</p>
    <p>It will also be useful to refer to the corresponding random cdf <span class="math inline">\(F\)</span>, quantile
      function <span class="math inline">\(Q = F^{-1}\)</span> and <strong>quantile
        density</strong> <span class="math inline">\(q = Q^{\prime} =
        1/(\mathfrak{F} \circ Q)\)</span> <span class="citation" data-cites="parzenNonparametricStatisticalData1979">(<a
          href="#ref-parzenNonparametricStatisticalData1979" role="doc-biblioref">Parzen 1979</a>)</span>.</p>
    <p>For clarity:</p>
    <ol type="1">
      <li><span class="math inline">\(u,v \in \mathbb{R}\)</span> will
        consistently be used as density and cdf arguments throughout,
        whereas</li>
      <li><span class="math inline">\(s, t \in[0,1]\)</span> will be used as
        arguments for the quantile and quantile density functions.</li>
    </ol>
    The Wasserstein–Fréchet (or simply Wasserstein) mean and variance of
    <span class="math inline">\(\mathfrak{F}\)</span> are <span class="math display">\[
      \begin{equation}\label{eq: wMeanVar}
      f_{\oplus}^{*} \coloneqq \argmin_{f \in \mathcal{D}}
      E\left(d_{\mathrm{W}}^{2}(\mathfrak{F}, f)\right), \quad
      \mathrm{Var}_\oplus(\mathfrak{F})\coloneqq
      E\left(d_{\mathrm{W}}^{2}(\mathfrak{F}, f_{\oplus}^{*})\right).
      \end{equation}
      \]</span>
    <div style="padding: 0.8rem 1rem; border-radius: 6px; margin: 1rem 0; background-color:#e2daf1">
      <p style="position: relative; top: -0.6rem;">
        ✋
        <strong style="color: #38225d; position: relative; top: -0rem;">Note</strong>
      </p>
      <p style="margin: 0;position: relative; top: -1rem; text-align: left; margin-bottom: -1rem;line-height:1.3;">
        The Wasserstein mean is the minimizer of the expected squared
        Wasserstein distance between the random density and a fixed density in
        <span class="math inline">\(\mathcal{D}\)</span>. Apparently, <span
          class="math inline">\(f_{\oplus}^{*}\)</span> is still a density
        function while the <span class="math inline">\(\mathrm{Var}_\oplus(\mathfrak{F})\)</span> is a
        scalar.
      </p>
    </div>
    <p>In the regression setting, we model the distribution of <span class="math inline">\(\mathfrak{F}\)</span>
      conditional on a vector
      <span class="math inline">\(X \in \mathbb{R}^p\)</span> of predictors,
      where the pair <span class="math inline">\((X, \mathfrak{F})\)</span> is
      distributed according to a probability measure <span class="math inline">\(\mathcal{G}\)</span> on the product
      space <span class="math inline">\(\mathbb{R}^p \times \mathcal{D}.\)</span>
    </p>
    <div style="padding: 0.8rem 1rem; border-radius: 6px; margin: 1rem 0; background-color:#d2f9d2">
      <p style="position: relative; top: -0.6rem;">
        💡
        <strong style="color: #094409; position: relative; top: -0rem;">Tip</strong>
      </p>
      <p style="margin: 0;position: relative; top: -1rem; text-align: left; margin-bottom: -1rem;line-height:1.3;">
        The density of random <span class="math inline">\(\mathfrak{F}\)</span>
        is kind of “density of densities”, the domain is <span class="math inline">\(\mathcal{D}\)</span>.
      </p>
    </div>
    <p>In this sense, the objects in \eqref{eq: wMeanVar} are the marginal
      Fr'echet mean and variance of <span class="math inline">\(\mathfrak{F}.\)</span> Let <span
        class="math inline">\(\mathfrak{S}_X\)</span> denote the support of the
      marginal distribution of <span class="math inline">\(X.\)</span> Our
      interest is in the Fr'echet regression function, or function of
      conditional Fréchet means, <span class="math display">\[
        \begin{equation}\label{eq:condWMean}
        f_{\oplus}(x) := \argmin_{f \in \mathcal{D}}
        E\left[d_{\mathrm{W}}^{2}(\mathfrak{F}, f) | X = x\right], \quad x \in
        \mathfrak{S}_X.
        \end{equation}
        \]</span> Next, we define the conditional Fréchet variance:</p>
    <p>Let</p>
    <ul>
      <li><span class="math inline">\(F_{\oplus}(x)\)</span> be the cdf of
        <span class="math inline">\(f_{\oplus}(x).\)</span>
      </li>
      <li><span class="math inline">\(Q_{\oplus}(x)\)</span> be quantile of
        <span class="math inline">\(f_{\oplus}(x).\)</span>
      </li>
      <li><span class="math inline">\(q_{\oplus}(x)\)</span> be quantile
        density functions of <span class="math inline">\(f_{\oplus}(x).\)</span></li>
    </ul>
    <p>We will use the notation <span class="math inline">\(f_{\oplus}(x,u)\)</span> to denote the value of
      the conditional mean density <span class="math inline">\(f_{\oplus}(x)\)</span> at argument <span
        class="math inline">\(u \in \mathbb{R},\)</span> and similary for <span
        class="math inline">\(F_{\oplus}(x,u),\)</span> <span class="math inline">\(Q_{\oplus}(x,t)\)</span>, and <span
        class="math inline">\(q_{\oplus}(x,t),\)</span> <span class="math inline">\(t \in [0,1].\)</span></p>
    <div style="padding: 0.8rem 1rem; border-radius: 6px; margin: 1rem 0; background-color:#d2f9d2">
      <p style="position: relative; top: -0.6rem;">
        💡
        <strong style="color: #094409; position: relative; top: -0rem;">Tip</strong>
      </p>
      <p style="margin: 0;position: relative; top: -1rem; text-align: left; margin-bottom: -1rem;line-height:1.3;">
        To help to understand, let <span class="math inline">\(z^{*}\sim
          f_{\oplus}(x)\)</span>, then <span class="math inline">\(f_{\oplus}(x,u)
          = f_{\oplus}(x)|_{z^{*}=u}\)</span>.
      </p>
    </div>
    <p>For a pair <span class="math inline">\((X,\mathfrak{F})\)</span>,
      define <span class="math inline">\(T = Q \circ F_{\oplus}(X)\)</span> to
      be the optimal transport map from the conditional mean <span class="math inline">\(f_{\oplus}(X)\)</span> to the
      random density <span class="math inline">\(\mathfrak{F}.\)</span> By \eqref{eq: wass2}, it
      must be that <span class="math inline">\(E(Q(t)|X=x) =
        Q_{\oplus}(x,t),\)</span> so that <span class="math inline">\(E(T(u) |X
        = x) = u\)</span> for <span class="math inline">\(u\)</span> such that
      <span class="math inline">\(f_{\oplus}(x,u) &gt; 0.\)</span> Then the
      conditional Fréchet variance is <span class="math display">\[
        \begin{equation}\label{eq: condWVar}
        \begin{split}
        \mathrm{Var}_{\oplus}(\mathfrak{F}|X= x) &amp; =
        E\left[d_{\mathrm{W}}^{2}(\mathfrak{F}, f_{\oplus}(x))|X = x\right] =
        \int_\mathbb{R} E\left[(T(u) - u)^2|X=x\right]f_{\oplus}(x,u)\mathrm{d}
        u \\
        &amp; = \int_\mathbb{R}
        \mathrm{Var}(T(u)|X=x) f_{\oplus}(x,u) \mathrm{d} u.
        \end{split}
        \end{equation}
        \]</span>
    </p>
    <p>In these developments, we have assumed that the marginal and
      conditional Wasserstein mean densities exist and are unique. However,
      this is not automatic and some conditions are needed. The assumptions
      (A1)–(A3) in <span class="citation" data-cites="petersenWasserstein$F$testsConfidence2021">Petersen, Liu,
        and Divani (<a href="#ref-petersenWasserstein$F$testsConfidence2021" role="doc-biblioref">2021</a>)</span> are
      sufficient for this purpose,
      we will skip this part and discuss the regression directly.</p>
    <h2 id="global-wasserstein-fréchet-regression">Global
      Wasserstein–Fréchet regression</h2>
    <p>In order to tests for no or partial effects of the covariates <span class="math inline">\(X\)</span> and
      confidence bands for the
      conditional Wasserstein means, we consider a particular global
      regression model for the conditional Wassersteins <span class="math inline">\(f_{\oplus}(x)\)</span> defined in
      \eqref{eq:condWMean}.</p>
    <p>This model, proposed by <span class="citation" data-cites="petersenFrechetRegressionRandom2019">Petersen and
        Müller (<a href="#ref-petersenFrechetRegressionRandom2019" role="doc-biblioref">2019</a>)</span>, is termed
      Fréchet regression, and
      takes the form of a weighted Fréchet mean <span class="math display">\[
        \begin{equation}\label{eq:Wmodel}
        f_{\oplus}(x) = \argmin_{f \in \mathcal{D}} E\left[s(X,
        x)d_{\mathrm{W}}^{2}(\mathfrak{F}, f)\right],
        \end{equation}
        \]</span> where the weight function is <span class="math display">\[
        \begin{equation*}
        s(X, x) = 1 + (X - \mu)^\top \Sigma^{-1}(x - \mu), \quad \mu = E(X),
        \, \Sigma = \mathrm{Var}(X),
        \end{equation*}
        \]</span> and <span class="math inline">\(\Sigma\)</span> is assumed to
      be positive definite. In fact, this model generalises linear regression
      to the case of density response by substituting <span class="math inline">\(\mathfrak{F}\)</span> for <span
        class="math inline">\(Y\)</span> and <span class="math inline">\((\mathcal{D},d_W)\)</span> in place of the
      usual
      metric space <span class="math inline">\((\mathbb{R}, |\cdot|)\)</span>
      implicitly used in multiple linear regression.</p>
    <p>Thus far, the regression model \eqref{eq:Wmodel} provides us with a
      formula for the conditional Wasserstein mean of <span class="math inline">\(\mathfrak{F},\)</span> whereas one
      also needs
      information on the conditional variance in order to conduct inference.
      In this section, we skip residual transport and the assumption on the
      covariance.</p>
    <h2 id="estimation">Estimation</h2>
    <p>In order to estimate the regression function <span class="math inline">\(f_{\oplus}(x),\)</span> we utilize an
      empirical
      version of the least-squares Wasserstein criterion in
      \eqref{eq:Wmodel}.</p>
    <ol type="1">
      <li>First, set <span class="math inline">\(\bar{X} = n^{-1}\sum_{i =
          1}^{n} X_i,\)</span> <span class="math inline">\(\hat{\Sigma} =
          n^{-1}\sum_{i = 1}^{n} (X_i - \bar{X})(X_i - \bar{X})^\top,\)</span> and
        compute empirical weights <span class="math inline">\(s_{in}(x) = 1 +
          (X_i - \bar{X})^\top \hat{\Sigma}^{-1}(x - \bar{X})\)</span>,</li>
      <li>Let <span class="math inline">\(\mathfrak{Q}\)</span> be the set of
        quantile functions in <span class="math inline">\(L^2[0,1].\)</span>
        With <span class="math inline">\({\left\lVert \cdot
          \right\rVert}_{L^{2}}\)</span> denoting the standard Hilbert norm on
        <span class="math inline">\(L^{2}[0,1]\)</span>, an estimator of <span
          class="math inline">\(Q_{\oplus}(x)\)</span> is <span class="math display">\[
          \begin{equation}\label{eq:Qfit}
          \hat{Q}_{\oplus}(x) = \argmin_{Q \in \mathfrak{Q}} \sum_{i = 1}^{n}
          s_{in}(x) {\left\lVert Q - Q_i \right\rVert}_{L^{2}}^{2}.
          \end{equation}
          \]</span> Implementation of this estimator is given in Algorithm 1 in
        the Appendix. In finite samples, <span class="math inline">\(\hat{Q}_{\oplus}(x)\)</span> will not necessarily
        admit a density.
      </li>
      <li>However, Lemma 2 in the Appendix guarantees that <span class="math inline">\(\hat{Q}_{\oplus}(x)\)</span>
        admits a density
        <span class="math inline">\(\hat{f}_{\oplus}(x)\in \mathcal{D}\)</span>
        for large samples with high probability. When this holds, the estimate
        <span class="math display">\[
          \begin{equation}\label{eq:fullEst}
          \hat{f}_{\oplus}(x) = \argmin_{f \in \mathcal{D}} \frac{1}{n}\sum_{i =
          1}^{n} s_{in}(x)d_{\mathrm{W}}^{2}(\mathfrak{F}_i, f).
          \end{equation}
          \]</span> is well-defined, and <span class="math inline">\(\hat{f}_{\oplus}(x)\)</span> is the density
        corresponding to the quantile estimate <span class="math inline">\(\hat{Q}_{\oplus}(x)\)</span> above. It can be
        computed in practice using Algorithm 2 in the Appendix.
      </li>
    </ol>
    <p>To consider hypothesis tests of partial effects, just do the similar
      things above in terms of part of covariates <span class="math inline">\(X\)</span>.</p>
    <h1 id="hypothese-testing">Hypothese testing</h1>
    <p>Given that we are considering the more specific case of
      density-valued response variables under the Wasserstein geometry, we are
      able to expand on these results in order to develop asymptotically
      justified tests for both global and partial null hypotheses, where
      predictors can be of any type.</p>
    <h2 id="test-of-no-effects">Test of no effects</h2>
    <p>We begin with the global null hypothesis of no effects, <span class="math inline">\(\mathcal{H}_0^G:
        f_{\oplus}(x) \equiv
        f_{\oplus}^{*}\)</span>. Given the Wasserstein variance decomposition in
      (2.7) of <span class="citation" data-cites="petersenWasserstein$F$testsConfidence2021">Petersen, Liu,
        and Divani (<a href="#ref-petersenWasserstein$F$testsConfidence2021" role="doc-biblioref">2021</a>)</span>,
      under <span class="math inline">\(\mathcal{H}_0^G\)</span> we have <span
        class="math inline">\(\mathrm{Var}_{\oplus}(f_{\oplus}(X)) =
        E\left(d_{\mathrm{W}}^{2}(f_{\oplus}(X), f_{\oplus}^{*})\right) =
        0.\)</span> This motivates <span class="math display">\[
        \begin{equation}\label{eq:globalF}
        F^{*}_G = \sum_{i = 1}^n d_{\mathrm{W}}^{2}(\hat{\mathfrak{F}}_{i},
        \hat{f}_{\oplus}^{*})
        \end{equation}
        \]</span> as a test statistic, where <span class="math inline">\(\hat{\mathfrak{F}}_{i} =
        \hat{f}_{\oplus}(X_i)\)</span> are the fitted densities and <span class="math inline">\(\hat{f}_{\oplus}^{*} =
        \hat{f}_{\oplus}(\bar{X})\)</span> is the sample Wasserstein mean. This
      can be viewed as a generalization of the numerator of the global <span class="math inline">\(F\)</span>-test in
      multiple linear regression, and
      we thus refer to <span class="math inline">\(F^{*}_G\)</span> in
      \eqref{eq:globalF} as the (global) Wasserstein <span class="math inline">\(F\)</span>-statistic.</p>
    <p>In order to establish the asymptotic null distribution of <span class="math inline">\(F^{*}_G,\)</span> we
      require the assumptions
      (T1)–(T4) (skipped here).</p>
    <div
      style="position: relative; border: 2px solid#ff8618; background-color: #f9f9f9; padding: 15px; margin: 20px 0; font-family: Arial, sans-serif; box-shadow: 2px 2px 10px rgba(0, 0, 0, 0.1); border-radius: 8px;">
      <div
        style="position: absolute; top: -0.85em; left: 15px; background-color:#ff8618; padding: 0 5px; font-weight: bold; color: #f9f9f9; border: 2px solid#ff8618;">
        <span id="theorem:global">Theorem 1</span>
      </div>
      <div style="font-style: italic; margin-top: 0.7em;">
        Suppose assumptions (T1)–(T4) hold. Then <span class="math display">\[
          \begin{equation*}
          F^{*}_G | X_1,\ldots,X_n \overset{D}{\rightarrow} \sum_{j=1}^{\infty}
          \lambda_j \omega_j \quad \text{almost surely,}
          \end{equation*}
          \]</span> where <span class="math inline">\(\omega_j\)</span> are
        i.i.d.&nbsp;<span class="math inline">\(\chi^{2}_{p}\)</span> random
        variables and <span class="math inline">\(\lambda_{j}\)</span> are the
        eigenvalues in (3.2) of <span class="citation" data-cites="petersenWasserstein$F$testsConfidence2021">Petersen,
          Liu,
          and Divani (<a href="#ref-petersenWasserstein$F$testsConfidence2021" role="doc-biblioref">2021</a>)</span>.
      </div>
      <div
        style="position: absolute; bottom: 10px; right: 10px; text-align: right; font-size: 20px; color:#ff8618; margin-top: 1px;">
        ♥
      </div>
    </div>
    <p>The limiting distribution obtained in <a href="#theorem:global"><span style="color: #3c71b7;">Theorem
          1</span></a> depends on unknown
      parameters, namely the eigenvalues <span class="math inline">\(\lambda_j\)</span>, that must be approximated to
      formulate a rejection region.</p>
    <p>A simple calculation reveals that <span class="math inline">\(C_Q(s,t) =
        K(Q_{\oplus}^{*}(s),Q_{\oplus}^{*}(t)),\)</span> so that <span class="math inline">\(\lambda_j\)</span> are also
      the eigenvalues of
      <span class="math inline">\(C_Q,\)</span> which can be estimated by
      <span class="math display">\[
        \begin{equation}\label{eq: CqEst}
        \hat{C}*Q(s, t) = \frac{1}{n} \sum*{i = 1}^{n} (Q_i(s) -
        \hat{Q}_{i}(s))(Q_i(t) - \hat{Q}_{i}(t)),
        \end{equation}
        \]</span> where <span class="math inline">\(\hat{Q}_{i}\)</span> are the
      fitted quantile functions corresponding to densities <span class="math inline">\(\hat{\mathfrak{F}}_{i}\)</span>.
      Let <span class="math inline">\(\hat{\lambda}_j\)</span> be the corresponding
      eigenvalues of <span class="math inline">\(\hat{C}_Q.\)</span>
    </p>
    <p>One can consistently approximate the conditional null distribution of
      <span class="math inline">\(F^{*}_G\)</span> as follows.
    </p>
    <ol type="1">
      <li>For <span class="math inline">\(\alpha \in (0,1)\)</span> and
        eigenvalue estimates <span class="math inline">\(\hat{\lambda}_j\)</span>, let <span
          class="math inline">\(\hat{b}_\alpha^G\)</span> be the <span class="math inline">\(1-\alpha\)</span> quantile
        of <span class="math inline">\(\sum_{j = 1}^{\infty}
          \hat{\lambda}_j\omega_j\)</span>, where <span class="math inline">\(\omega_j\)</span> are as in <a
          href="#theorem:global"><span style="color: #3c71b7;">Theorem
            1</span></a>.</li>
      <li>Computation of this critical value is outlined in Algorithm 3 of the
        Appendix.</li>
      <li>The following result on the conditional power <span class="math inline">\(\beta_n^G = P_{\mathbb{X}}(F_{G}^{*}
          &gt;
          \hat{b}_\alpha^G)\)</span> follows from <a href="#theorem:global"><span style="color: #3c71b7;">Theorem
            1</span></a>.</li>
      <li>Let <span class="math inline">\(\mathfrak{G}\)</span> denote the
        collection of distributions on <span class="math inline">\(\mathbb{R}^p
          \times \mathcal{D}\)</span> such that model \eqref{eq:Wmodel}
        holds.</li>
    </ol>
    <div
      style="position: relative; border: 2px solid#ff8618; background-color: #f9f9f9; padding: 15px; margin: 20px 0; font-family: Arial, sans-serif; box-shadow: 2px 2px 10px rgba(0, 0, 0, 0.1); border-radius: 8px;">
      <div
        style="position: absolute; top: -0.85em; left: 15px; background-color:#ff8618; padding: 0 5px; font-weight: bold; color: #f9f9f9; border: 2px solid#ff8618;">
        <span id="corollary:Gsize">Corollary 1</span>
      </div>
      <div style="font-style: italic; margin-top: 0.7em;">
        If <span class="math inline">\(\mathcal{G} \in \mathfrak{G}\)</span>
        satisfies <span class="math inline">\(\mathcal{H}_0^G\)</span> and
        (T1)–(T4) hold, then <span class="math inline">\(\beta_n^G \rightarrow
          \alpha\)</span> almost surely.
      </div>
      <div
        style="position: absolute; bottom: 10px; right: 10px; text-align: right; font-size: 20px; color:#ff8618; margin-top: 1px;">
        ♥
      </div>
    </div>
    <p>The paper also introduces the <strong>Test of partial
        effects</strong> and <strong>Alternative testing approximation</strong>,
      we will skip these parts and move to the confidence bands.</p>
    <h1 id="confidence-bands">Confidence bands</h1>
    <p>We now develop methodology for producing a confidence set for <span class="math inline">\(f_{\oplus}(x),\)</span>
      where <span class="math inline">\(x\)</span> is considered to be fixed.</p>
    <p>Let <span class="math inline">\(g\)</span> be a generic functional
      parameter of interest, where we assume that <span class="math inline">\(g\)</span> is bounded. Given an estimator
      <span class="math inline">\(\hat{g},\)</span> a typical approach to
      formulating a simultaneous confidence band is to show that <span class="math inline">\(b_n(\hat{g}(u) -
        g(u))/a(u)\)</span> converges
      weakly to a limiting process (usually Gaussian) in the space of bounded
      functions under the uniform metric, where <span class="math inline">\(a&gt;0\)</span> is a scaling function and
      <span class="math inline">\(b_n^{-1}\)</span> is the rate of convergence. By
      an application of the continuous mapping theorem, one can then obtain a
      confidence band for <span class="math inline">\(g\)</span> of the form
      <span class="math display">\[
        \begin{equation*}
        \{g^{*}: \hat{g}(u) - ca(u)b_n^{-1} \leq g^{*}(u) \leq \hat{g}(u) +
        ca(u)b_n^{-1}\,\, \textrm{for all }u\}.
        \end{equation*}
        \]</span> This band corresponds to all functions that are almost
      everywhere between the lower and upper bounds, and is the closest one
      can get to a confidence interval in function space.
    </p>
    <p><span class="citation" data-cites="petersenWasserstein$F$testsConfidence2021">Petersen, Liu,
        and Divani (<a href="#ref-petersenWasserstein$F$testsConfidence2021" role="doc-biblioref">2021</a>)</span>
      explore two different approaches
      to formulating simultaneous confidence bands. The first arises naturally
      from the Wasserstein geometry, and provides a distributional band for
      either <span class="math inline">\(Q_{\oplus}(x)\)</span> or <span class="math inline">\(F_{\oplus}(x)\)</span>,
      but not the density
      parameter. In the second approach, they strengthen the convergence
      results and utilize the delta method to construct a simultaneous
      confidence band for <span class="math inline">\(f_{\oplus}(x)\)</span>.
      For more details, please refer to Section 4 of the paper <span class="citation"
        data-cites="petersenWasserstein$F$testsConfidence2021">(<a href="#ref-petersenWasserstein$F$testsConfidence2021"
          role="doc-biblioref">Petersen, Liu, and Divani 2021</a>)</span>. The
      Algorithm of the confidence band is given in the Appendix, see Algorithm
      7.</p>
    <p>Furthermore, the authors also provide the <code>R</code> package <a
        href="https://github.com/cran/WRI"><code>WRI</code></a>. The package is
      designed to provide a comprehensive set of tools for the analysis of
      density-valued response data under the Wasserstein geometry. The package
      is available on CRAN and can be installed using the command
      <code>install.packages("WRI")</code>.
    </p>
    <h1 class="unnumbered" id="reference">Reference</h1>
    <div id="refs" class="references csl-bib-body hanging-indent" data-entry-spacing="0" role="list">
      <div id="ref-parzenNonparametricStatisticalData1979" class="csl-entry" role="listitem">
        Parzen, Emanuel. 1979. <span>“Nonparametric <span>Statistical Data
            Modeling</span>.”</span> <em>Journal of the American Statistical
          Association</em> 74 (365): 105–21. <a
          href="https://doi.org/10.2307/2286734">https://doi.org/10.2307/2286734</a>.
      </div>
      <div id="ref-petersenWasserstein$F$testsConfidence2021" class="csl-entry" role="listitem">
        Petersen, Alexander, Xi Liu, and Afshin A. Divani. 2021.
        <span>“Wasserstein $<span>F</span>$-Tests and Confidence Bands for the
          <span class="nocase">Fr<span class="nocase">é</span>chet</span>
          Regression of Density Response Curves.”</span> <em>The Annals of
          Statistics</em> 49 (1). <a href="https://doi.org/10.1214/20-AOS1971">https://doi.org/10.1214/20-AOS1971</a>.
      </div>
      <div id="ref-petersenFrechetRegressionRandom2019" class="csl-entry" role="listitem">
        Petersen, Alexander, and Hans-Georg Müller. 2019.
        <span>“Fr<span>é</span>chet Regression for Random Objects with
          <span>Euclidean</span> Predictors.”</span> <em>The Annals of
          Statistics</em> 47 (2). <a href="https://doi.org/10.1214/17-AOS1624">https://doi.org/10.1214/17-AOS1624</a>.
      </div>
    </div>

  </div>
