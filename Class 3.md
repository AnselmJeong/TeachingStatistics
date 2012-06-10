


# Class 3 #

---

# Review #

---
* Preparing data in csv format (excel)
* Importing data set from csv.
* Calling variables
* Using **attach()** function
* Telling apart **numeric variables** and **factor variable**
* Using **str()** function
* Using **mean(), median(), sd(), range(), min(), max()** functions
* Storing result in a new variable
* Using **summary()** function
* Getting subset of the data: **subset()** function

---

# 1. More on factors #

---
### Converting to and from factor ###

* Whis is the distinction between numeric and factor variable important?

<pre class="knitr"><div class="source"><span class="symbol">cscore</span> <span class="assignement">&lt;-</span> <span class="functioncall">read.csv</span><span class="keyword">(</span><span class="string">"Class.score.csv"</span><span class="keyword">)</span>
<span class="functioncall">par</span><span class="keyword">(</span><span class="argument">mfrow</span><span class="argument">=</span><span class="functioncall">c</span><span class="keyword">(</span><span class="number">1</span><span class="keyword">,</span><span class="number">2</span><span class="keyword">)</span><span class="keyword">)</span>
<span class="functioncall">plot</span><span class="keyword">(</span><span class="symbol">cscore</span><span class="keyword">$</span><span class="symbol">class</span><span class="keyword">,</span> <span class="symbol">cscore</span><span class="keyword">$</span><span class="symbol">score</span><span class="keyword">)</span>
<span class="functioncall">plot</span><span class="keyword">(</span><span class="functioncall">as.factor</span><span class="keyword">(</span><span class="symbol">cscore</span><span class="keyword">$</span><span class="symbol">class</span><span class="keyword">)</span><span class="keyword">,</span> <span class="symbol">cscore</span><span class="keyword">$</span><span class="symbol">score</span><span class="keyword">)</span>
</div><img src="figure/unnamed-chunk-1.png" class="plot" />
</pre>


---
<pre class="knitr"><div class="source"><span class="functioncall">round</span><span class="keyword">(</span><span class="functioncall">coef</span><span class="keyword">(</span><span class="functioncall">summary</span><span class="keyword">(</span><span class="functioncall">lm</span><span class="keyword">(</span><span class="symbol">score</span><span class="keyword">~</span><span class="symbol">class</span><span class="keyword">,</span> <span class="argument">data</span><span class="argument">=</span><span class="symbol">cscore</span><span class="keyword">)</span><span class="keyword">)</span><span class="keyword">)</span><span class="keyword">,</span> <span class="number">3</span><span class="keyword">)</span>
</div><div class="output">##             Estimate Std. Error t value Pr(>|t|)
## (Intercept)   74.613      3.125   23.88    0.000
## class         -0.015      0.504   -0.03    0.976
</div><div class="source"><span class="functioncall">round</span><span class="keyword">(</span><span class="functioncall">coef</span><span class="keyword">(</span><span class="functioncall">summary</span><span class="keyword">(</span><span class="functioncall">lm</span><span class="keyword">(</span><span class="symbol">score</span><span class="keyword">~</span><span class="functioncall">as.factor</span><span class="keyword">(</span><span class="symbol">class</span><span class="keyword">)</span><span class="keyword">,</span> <span class="argument">data</span><span class="argument">=</span><span class="symbol">cscore</span><span class="keyword">)</span><span class="keyword">)</span><span class="keyword">)</span><span class="keyword">,</span> <span class="number">3</span><span class="keyword">)</span>
</div><div class="output">##                    Estimate Std. Error t value Pr(>|t|)
## (Intercept)            70.4      4.447  15.830    0.000
## as.factor(class)2      -1.4      6.290  -0.223    0.824
## as.factor(class)3       9.8      6.290   1.558    0.123
## as.factor(class)4      10.2      6.290   1.622    0.108
## as.factor(class)5      11.9      6.290   1.892    0.062
## as.factor(class)6      -4.0      6.290  -0.636    0.526
## as.factor(class)7       7.1      6.290   1.129    0.262
## as.factor(class)8      -0.2      6.290  -0.032    0.975
## as.factor(class)9       4.1      6.290   0.652    0.516
## as.factor(class)10      3.8      6.290   0.604    0.547
</div></pre>

---
* How can we make factors?

<pre class="knitr"><div class="source"><span class="comment"># We have this character variable names 'ses'</span>
<span class="symbol">ses</span> <span class="assignement">&lt;-</span> <span class="functioncall">c</span><span class="keyword">(</span><span class="string">"low"</span><span class="keyword">,</span> <span class="string">"middle"</span><span class="keyword">,</span> <span class="string">"low"</span><span class="keyword">,</span> <span class="string">"low"</span><span class="keyword">,</span> <span class="string">"low"</span><span class="keyword">,</span> <span class="string">"low"</span><span class="keyword">,</span> <span class="string">"middle"</span><span class="keyword">,</span> <span class="string">"low"</span><span class="keyword">,</span> <span class="string">"middle"</span><span class="keyword">,</span> <span class="string">"middle"</span><span class="keyword">,</span> <span class="string">"middle"</span><span class="keyword">,</span> <span class="string">"middle"</span><span class="keyword">,</span> <span class="string">"middle"</span><span class="keyword">,</span> <span class="string">"high"</span><span class="keyword">,</span> <span class="string">"high"</span><span class="keyword">,</span> <span class="string">"low"</span><span class="keyword">,</span> <span class="string">"middle"</span><span class="keyword">,</span> <span class="string">"middle"</span><span class="keyword">,</span> <span class="string">"low"</span><span class="keyword">,</span> <span class="string">"high"</span><span class="keyword">)</span>

<span class="symbol">ses.factor</span><span class="assignement">&lt;-</span><span class="functioncall">factor</span><span class="keyword">(</span><span class="symbol">ses</span><span class="keyword">)</span>
<span class="symbol">ses.factor</span>
</div><div class="output">##  [1] low    middle low    low    low    low    middle low    middle middle
## [11] middle middle middle high   high   low    middle middle low    high  
## Levels: high low middle
</div></pre>

---
* Why is the factor level "high, low, middle" not "low, middle, high"?

<pre class="knitr"><div class="source"><span class="comment"># ordered factor</span>
<span class="symbol">ses.ordered</span><span class="assignement">&lt;-</span><span class="functioncall">ordered</span><span class="keyword">(</span><span class="symbol">ses</span><span class="keyword">,</span> <span class="argument">levels</span><span class="argument">=</span><span class="functioncall">c</span><span class="keyword">(</span><span class="string">'low'</span><span class="keyword">,</span> <span class="string">'middle'</span><span class="keyword">,</span> <span class="string">'high'</span><span class="keyword">)</span><span class="keyword">)</span>
<span class="symbol">ses.ordered</span>
</div><div class="output">##  [1] low    middle low    low    low    low    middle low    middle middle
## [11] middle middle middle high   high   low    middle middle low    high  
## Levels: low < middle < high
</div><div class="source">
<span class="symbol">cscore</span><span class="keyword">$</span><span class="symbol">class</span><span class="assignement">&lt;-</span><span class="functioncall">ordered</span><span class="keyword">(</span><span class="symbol">cscore</span><span class="keyword">$</span><span class="symbol">class</span><span class="keyword">,</span> <span class="argument">levels</span><span class="argument">=</span><span class="number">1</span><span class="keyword">:</span><span class="number">10</span><span class="keyword">)</span>
<span class="symbol">cscore</span><span class="keyword">$</span><span class="symbol">class</span>
</div><div class="output">##   [1] 1  2  3  4  5  6  7  8  9  10 1  2  3  4  5  6  7  8  9  10 1  2  3 
##  [24] 4  5  6  7  8  9  10 1  2  3  4  5  6  7  8  9  10 1  2  3  4  5  6 
##  [47] 7  8  9  10 1  2  3  4  5  6  7  8  9  10 1  2  3  4  5  6  7  8  9 
##  [70] 10 1  2  3  4  5  6  7  8  9  10 1  2  3  4  5  6  7  8  9  10 1  2 
##  [93] 3  4  5  6  7  8  9  10
## Levels: 1 < 2 < 3 < 4 < 5 < 6 < 7 < 8 < 9 < 10
</div></pre>

---
* How can we treat a factor variable as a numeric variable?

<pre class="knitr"><div class="source"><span class="functioncall">as.numeric</span><span class="keyword">(</span><span class="symbol">cscore</span><span class="keyword">$</span><span class="symbol">class</span><span class="keyword">)</span>
</div><div class="output">##   [1]  1  2  3  4  5  6  7  8  9 10  1  2  3  4  5  6  7  8  9 10  1  2  3
##  [24]  4  5  6  7  8  9 10  1  2  3  4  5  6  7  8  9 10  1  2  3  4  5  6
##  [47]  7  8  9 10  1  2  3  4  5  6  7  8  9 10  1  2  3  4  5  6  7  8  9
##  [70] 10  1  2  3  4  5  6  7  8  9 10  1  2  3  4  5  6  7  8  9 10  1  2
##  [93]  3  4  5  6  7  8  9 10
</div></pre>

---

# 2. Correlation #

---
* What is correlation?
: How much of the total variation is explained by co-variation?

<pre class="knitr"><div class="source"><span class="symbol">a</span><span class="assignement">&lt;-</span><span class="number">1</span><span class="keyword">:</span><span class="number">100</span>
<span class="symbol">b</span><span class="assignement">&lt;-</span><span class="symbol">a</span><span class="keyword">+</span><span class="functioncall">rnorm</span><span class="keyword">(</span><span class="number">100</span><span class="keyword">,</span> <span class="number">0</span><span class="keyword">,</span> <span class="functioncall">sqrt</span><span class="keyword">(</span><span class="symbol">a</span><span class="keyword">)</span><span class="keyword">)</span>
<span class="symbol">sample</span><span class="assignement">&lt;-</span><span class="functioncall">data.frame</span><span class="keyword">(</span><span class="symbol">a</span><span class="keyword">,</span><span class="symbol">b</span><span class="keyword">)</span>
<span class="functioncall">plot</span><span class="keyword">(</span><span class="symbol">sample</span><span class="keyword">)</span>
</div><img src="figure/unnamed-chunk-6.png" class="plot" />
</pre>


---
<pre class="knitr"><div class="source"><span class="symbol">c</span><span class="assignement">&lt;-</span><span class="functioncall">cov</span><span class="keyword">(</span><span class="symbol">sample</span><span class="keyword">)</span>
<span class="symbol">c</span><span class="keyword">[</span><span class="number">1</span><span class="keyword">,</span><span class="number">2</span><span class="keyword">]</span><span class="keyword">/</span><span class="keyword">(</span><span class="functioncall">sqrt</span><span class="keyword">(</span><span class="symbol">c</span><span class="keyword">[</span><span class="number">1</span><span class="keyword">,</span><span class="number">1</span><span class="keyword">]</span><span class="keyword">)</span><span class="keyword">*</span><span class="functioncall">sqrt</span><span class="keyword">(</span><span class="symbol">c</span><span class="keyword">[</span><span class="number">2</span><span class="keyword">,</span><span class="number">2</span><span class="keyword">]</span><span class="keyword">)</span><span class="keyword">)</span>
</div><div class="output">## [1] 0.9765
</div><div class="source"><span class="functioncall">cor</span><span class="keyword">(</span><span class="symbol">sample</span><span class="keyword">)</span>
</div><div class="output">##        a      b
## a 1.0000 0.9765
## b 0.9765 1.0000
</div></pre>


---


* Correlation among multiple variables

<pre class="knitr"><div class="source"><span class="functioncall">require</span><span class="keyword">(</span><span class="symbol">ISwR</span><span class="keyword">)</span>
<span class="functioncall">data</span><span class="keyword">(</span><span class="symbol">cystfibr</span><span class="keyword">)</span>
<span class="functioncall">require</span><span class="keyword">(</span><span class="symbol">ellipse</span><span class="keyword">)</span>
<span class="functioncall">plotcorr</span><span class="keyword">(</span><span class="functioncall">cor</span><span class="keyword">(</span><span class="symbol">cystfibr</span><span class="keyword">)</span><span class="keyword">)</span>
</div><img src="figure/unnamed-chunk-9.png" class="plot" />
</pre>

---
<pre class="knitr"><div class="source"><span class="functioncall">pairs</span><span class="keyword">(</span><span class="symbol">cystfibr</span><span class="keyword">,</span> <span class="argument">lower.panel</span><span class="argument">=</span><span class="symbol">panel.smooth</span><span class="keyword">,</span> <span class="argument">upper.panel</span><span class="argument">=</span><span class="symbol">panel.cor</span><span class="keyword">)</span>
</div><img src="figure/unnamed-chunk-10.png" class="plot" />
</pre>

---

# 3. Simple Linear Regression #

---
* Independent variable & Dependent variable
* Explanatory variable or Predictor variable

* How can we **explain** or **predict** dependent variables from **independent variables**?
---
* **Formula notation**
  * independent variable ~ dependent variable(1) + dependent variable(2)....
---
<pre class="knitr"><div class="source"><span class="functioncall">plot</span><span class="keyword">(</span><span class="symbol">sample</span><span class="keyword">)</span>
</div><img src="figure/unnamed-chunk-11.png" class="plot" />
</pre>

---
<pre class="knitr"><div class="source"><span class="symbol">model</span><span class="assignement">&lt;-</span><span class="functioncall">lm</span><span class="keyword">(</span><span class="symbol">b</span><span class="keyword">~</span><span class="symbol">a</span><span class="keyword">,</span> <span class="argument">data</span><span class="argument">=</span><span class="symbol">sample</span><span class="keyword">)</span>
<span class="functioncall">round</span><span class="keyword">(</span><span class="functioncall">coef</span><span class="keyword">(</span><span class="functioncall">summary</span><span class="keyword">(</span><span class="symbol">model</span><span class="keyword">)</span><span class="keyword">)</span><span class="keyword">,</span> <span class="number">3</span><span class="keyword">)</span>
</div><div class="output">##             Estimate Std. Error t value Pr(>|t|)
## (Intercept)    0.623      1.291   0.482    0.631
## a              0.996      0.022  44.882    0.000
</div><div class="source"><span class="functioncall">plot</span><span class="keyword">(</span><span class="functioncall">density</span><span class="keyword">(</span><span class="symbol">b</span><span class="keyword">-</span><span class="functioncall">mean</span><span class="keyword">(</span><span class="symbol">b</span><span class="keyword">)</span><span class="keyword">)</span><span class="keyword">,</span> <span class="argument">ylim</span><span class="argument">=</span><span class="functioncall">c</span><span class="keyword">(</span><span class="number">0</span><span class="keyword">,</span><span class="number">0.07</span><span class="keyword">)</span><span class="keyword">,</span> <span class="argument">main</span><span class="argument">=</span><span class="string">'Density of b and residuals'</span><span class="keyword">)</span>
<span class="functioncall">lines</span><span class="keyword">(</span><span class="functioncall">density</span><span class="keyword">(</span><span class="functioncall">resid</span><span class="keyword">(</span><span class="symbol">model</span><span class="keyword">)</span><span class="keyword">)</span><span class="keyword">,</span> <span class="argument">col</span><span class="argument">=</span><span class="string">'red'</span><span class="keyword">)</span>
<span class="functioncall">text</span><span class="keyword">(</span><span class="number">50</span><span class="keyword">,</span> <span class="number">0.04</span><span class="keyword">,</span> <span class="functioncall">paste</span><span class="keyword">(</span><span class="string">'var='</span><span class="keyword">,</span> <span class="functioncall">round</span><span class="keyword">(</span><span class="functioncall">var</span><span class="keyword">(</span><span class="symbol">b</span><span class="keyword">-</span><span class="functioncall">mean</span><span class="keyword">(</span><span class="symbol">b</span><span class="keyword">)</span><span class="keyword">)</span><span class="keyword">,</span><span class="number">0</span><span class="keyword">)</span><span class="keyword">)</span><span class="keyword">)</span>
<span class="functioncall">text</span><span class="keyword">(</span><span class="number">50</span><span class="keyword">,</span> <span class="number">0.035</span><span class="keyword">,</span> <span class="functioncall">paste</span><span class="keyword">(</span><span class="string">'var='</span><span class="keyword">,</span> <span class="functioncall">round</span><span class="keyword">(</span><span class="functioncall">var</span><span class="keyword">(</span><span class="functioncall">resid</span><span class="keyword">(</span><span class="symbol">model</span><span class="keyword">)</span><span class="keyword">)</span><span class="keyword">,</span><span class="number">0</span><span class="keyword">)</span><span class="keyword">)</span><span class="keyword">,</span> <span class="argument">col</span><span class="argument">=</span><span class="string">'red'</span><span class="keyword">)</span>
</div><img src="figure/unnamed-chunk-12.png" class="plot" />
</pre>

