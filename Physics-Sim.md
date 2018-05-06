---


---

<h1 id="physics-simulation-code">Physics Simulation code</h1>
<h2 id="html">HTML</h2>
<p>In <code>index.html</code>, put this:</p>
<pre class=" language-html"><code class="prism  language-html"><span class="token doctype">&lt;!DOCTYPE html&gt;</span>
<span class="token tag"><span class="token tag"><span class="token punctuation">&lt;</span>html</span><span class="token punctuation">&gt;</span></span>
  <span class="token tag"><span class="token tag"><span class="token punctuation">&lt;</span>head</span><span class="token punctuation">&gt;</span></span>
	<span class="token tag"><span class="token tag"><span class="token punctuation">&lt;</span>meta</span>  <span class="token attr-name">charset</span><span class="token attr-value"><span class="token punctuation">=</span><span class="token punctuation">"</span>utf-8<span class="token punctuation">"</span></span><span class="token punctuation">&gt;</span></span>
	<span class="token tag"><span class="token tag"><span class="token punctuation">&lt;</span>meta</span>  <span class="token attr-name">name</span><span class="token attr-value"><span class="token punctuation">=</span><span class="token punctuation">"</span>viewport<span class="token punctuation">"</span></span>  <span class="token attr-name">content</span><span class="token attr-value"><span class="token punctuation">=</span><span class="token punctuation">"</span>width=device-width<span class="token punctuation">"</span></span><span class="token punctuation">&gt;</span></span>
  <span class="token tag"><span class="token tag"><span class="token punctuation">&lt;/</span>head</span><span class="token punctuation">&gt;</span></span>
  <span class="token tag"><span class="token tag"><span class="token punctuation">&lt;</span>body</span><span class="token punctuation">&gt;</span></span>
	<span class="token tag"><span class="token tag"><span class="token punctuation">&lt;</span>div</span>  <span class="token attr-name">id</span><span class="token attr-value"><span class="token punctuation">=</span><span class="token punctuation">'</span>ballsBouncing<span class="token punctuation">'</span></span><span class="token punctuation">&gt;</span></span><span class="token tag"><span class="token tag"><span class="token punctuation">&lt;/</span>div</span><span class="token punctuation">&gt;</span></span>
	<span class="token tag"><span class="token tag"><span class="token punctuation">&lt;</span>pre</span>  <span class="token attr-name">id</span><span class="token attr-value"><span class="token punctuation">=</span><span class="token punctuation">'</span>debugging<span class="token punctuation">'</span></span><span class="token punctuation">&gt;</span></span><span class="token tag"><span class="token tag"><span class="token punctuation">&lt;/</span>pre</span><span class="token punctuation">&gt;</span></span>
	<span class="token tag"><span class="token tag"><span class="token punctuation">&lt;</span>script</span>  <span class="token attr-name">src</span><span class="token attr-value"><span class="token punctuation">=</span><span class="token punctuation">"</span>https://d3js.org/d3.v5.min.js<span class="token punctuation">"</span></span><span class="token punctuation">&gt;</span></span><span class="token script language-javascript"></span><span class="token tag"><span class="token tag"><span class="token punctuation">&lt;/</span>script</span><span class="token punctuation">&gt;</span></span>
	<span class="token tag"><span class="token tag"><span class="token punctuation">&lt;</span>script</span>  <span class="token attr-name">src</span><span class="token attr-value"><span class="token punctuation">=</span><span class="token punctuation">"</span>https://d3js.org/d3-selection-multi.v1.min.js<span class="token punctuation">"</span></span><span class="token punctuation">&gt;</span></span><span class="token script language-javascript"></span><span class="token tag"><span class="token tag"><span class="token punctuation">&lt;/</span>script</span><span class="token punctuation">&gt;</span></span>
	<span class="token tag"><span class="token tag"><span class="token punctuation">&lt;</span>script</span>  <span class="token attr-name">src</span><span class="token attr-value"><span class="token punctuation">=</span><span class="token punctuation">'</span>vector.js<span class="token punctuation">'</span></span><span class="token punctuation">&gt;</span></span><span class="token script language-javascript"></span><span class="token tag"><span class="token tag"><span class="token punctuation">&lt;/</span>script</span><span class="token punctuation">&gt;</span></span>
	<span class="token tag"><span class="token tag"><span class="token punctuation">&lt;</span>script</span>  <span class="token attr-name">src</span><span class="token attr-value"><span class="token punctuation">=</span><span class="token punctuation">'</span>collide.js<span class="token punctuation">'</span></span><span class="token punctuation">&gt;</span></span><span class="token script language-javascript"></span><span class="token tag"><span class="token tag"><span class="token punctuation">&lt;/</span>script</span><span class="token punctuation">&gt;</span></span>
	<span class="token tag"><span class="token tag"><span class="token punctuation">&lt;</span>script</span>  <span class="token attr-name">src</span><span class="token attr-value"><span class="token punctuation">=</span><span class="token punctuation">"</span>index.js<span class="token punctuation">"</span></span><span class="token punctuation">&gt;</span></span><span class="token script language-javascript"></span><span class="token tag"><span class="token tag"><span class="token punctuation">&lt;/</span>script</span><span class="token punctuation">&gt;</span></span>
  <span class="token tag"><span class="token tag"><span class="token punctuation">&lt;/</span>body</span><span class="token punctuation">&gt;</span></span>
<span class="token tag"><span class="token tag"><span class="token punctuation">&lt;/</span>html</span><span class="token punctuation">&gt;</span></span>
</code></pre>
<h2 id="creating-the-svg">Creating the <code>svg</code></h2>
<p>In <code>main.js</code>, add this:</p>
<pre class=" language-javascript"><code class="prism  language-javascript"><span class="token keyword">const</span> scr <span class="token operator">=</span> d3<span class="token punctuation">.</span><span class="token function">select</span><span class="token punctuation">(</span><span class="token string">'#screen'</span><span class="token punctuation">)</span><span class="token punctuation">;</span>
<span class="token keyword">const</span> svg <span class="token operator">=</span> scr<span class="token punctuation">.</span><span class="token function">append</span><span class="token punctuation">(</span><span class="token string">'svg'</span><span class="token punctuation">)</span><span class="token punctuation">.</span><span class="token function">attrs</span><span class="token punctuation">(</span><span class="token punctuation">{</span>
  width<span class="token punctuation">:</span> <span class="token number">500</span><span class="token punctuation">,</span>
  height<span class="token punctuation">:</span> <span class="token number">200</span><span class="token punctuation">,</span>
<span class="token punctuation">}</span><span class="token punctuation">)</span><span class="token punctuation">;</span>
svg<span class="token punctuation">.</span><span class="token function">append</span><span class="token punctuation">(</span><span class="token string">'rect'</span><span class="token punctuation">)</span><span class="token punctuation">.</span><span class="token function">attrs</span><span class="token punctuation">(</span><span class="token punctuation">{</span>
  x<span class="token punctuation">:</span> <span class="token number">0</span><span class="token punctuation">,</span> y<span class="token punctuation">:</span> <span class="token number">0</span><span class="token punctuation">,</span>
  width<span class="token punctuation">:</span> <span class="token number">500</span><span class="token punctuation">,</span> height<span class="token punctuation">:</span> <span class="token number">200</span><span class="token punctuation">,</span>
  fill<span class="token punctuation">:</span> <span class="token string">'#DDD'</span>
<span class="token punctuation">}</span><span class="token punctuation">)</span><span class="token punctuation">;</span>
</code></pre>
<p>This will store the div with the id of <code>screen</code> in the HTML in a <code>scr</code> variable and appends an <code>svg</code> stored in the <code>svg</code> variable with a width of 500 and a height of 200.<br>
The <code>rect</code> element is to make the part of the screen that is the <code>svg</code> visible.</p>
<h2 id="drawing-the-balls">Drawing the balls</h2>
<h3 id="creating-the-balls">Creating the balls</h3>
<p>Create an array of balls, each having the properties:</p>
<ul>
<li>a <code>name</code></li>
<li>a <code>color</code></li>
<li>a <code>mass</code></li>
<li>a <code>cx</code> (center x) point</li>
<li>a <code>cy</code> (center y) point</li>
<li>a <code>vx</code> (velocity x)</li>
<li>and a <code>vy</code> (velocity y)<br>
You should end up with something like these 13 balls:</li>
</ul>
<pre class=" language-javascript"><code class="prism  language-javascript"><span class="token keyword">const</span> balls <span class="token operator">=</span> <span class="token punctuation">[</span>
  <span class="token punctuation">{</span>
    name<span class="token punctuation">:</span> <span class="token string">'Ashley'</span><span class="token punctuation">,</span>
    color<span class="token punctuation">:</span> <span class="token string">'red'</span><span class="token punctuation">,</span>
    mass<span class="token punctuation">:</span> <span class="token number">10</span><span class="token punctuation">,</span>
    cx<span class="token punctuation">:</span> <span class="token number">40</span><span class="token punctuation">,</span>
    cy<span class="token punctuation">:</span> <span class="token number">10</span><span class="token punctuation">,</span>
    vx<span class="token punctuation">:</span> <span class="token number">13.2</span><span class="token punctuation">,</span>
    vy<span class="token punctuation">:</span> <span class="token number">12.6</span><span class="token punctuation">,</span>
    elast<span class="token punctuation">:</span> <span class="token number">0.9</span><span class="token punctuation">,</span>
    r<span class="token punctuation">:</span> <span class="token number">5</span><span class="token punctuation">,</span>
  <span class="token punctuation">}</span><span class="token punctuation">,</span>
  <span class="token punctuation">{</span>
    name<span class="token punctuation">:</span> <span class="token string">'Brad'</span><span class="token punctuation">,</span>
    color<span class="token punctuation">:</span> <span class="token string">'orange'</span><span class="token punctuation">,</span>
    mass<span class="token punctuation">:</span> <span class="token number">10</span><span class="token punctuation">,</span>
    cx<span class="token punctuation">:</span> <span class="token number">80</span><span class="token punctuation">,</span>
    cy<span class="token punctuation">:</span> <span class="token number">10</span><span class="token punctuation">,</span>
    vx<span class="token punctuation">:</span> <span class="token number">19.6</span><span class="token punctuation">,</span>
    vy<span class="token punctuation">:</span> <span class="token operator">-</span><span class="token number">19.461</span><span class="token punctuation">,</span>
    elast<span class="token punctuation">:</span> <span class="token number">0.9</span><span class="token punctuation">,</span>
    r<span class="token punctuation">:</span> <span class="token number">5</span><span class="token punctuation">,</span>
  <span class="token punctuation">}</span><span class="token punctuation">,</span>
  <span class="token punctuation">{</span>
    name<span class="token punctuation">:</span> <span class="token string">'Chris'</span><span class="token punctuation">,</span>
    color<span class="token punctuation">:</span> <span class="token string">'yellow'</span><span class="token punctuation">,</span>
    mass<span class="token punctuation">:</span> <span class="token number">10</span><span class="token punctuation">,</span>
    cx<span class="token punctuation">:</span> <span class="token number">120</span><span class="token punctuation">,</span>
    cy<span class="token punctuation">:</span> <span class="token number">10</span><span class="token punctuation">,</span>
    vx<span class="token punctuation">:</span> <span class="token operator">-</span><span class="token number">12.1</span><span class="token punctuation">,</span>
    vy<span class="token punctuation">:</span> <span class="token operator">-</span><span class="token number">15.7</span><span class="token punctuation">,</span>
    elast<span class="token punctuation">:</span> <span class="token number">0.9</span><span class="token punctuation">,</span>
    r<span class="token punctuation">:</span> <span class="token number">5</span><span class="token punctuation">,</span>
  <span class="token punctuation">}</span><span class="token punctuation">,</span>
  <span class="token punctuation">{</span>
    name<span class="token punctuation">:</span> <span class="token string">'Dylan'</span><span class="token punctuation">,</span>
    color<span class="token punctuation">:</span> <span class="token string">'green'</span><span class="token punctuation">,</span>
    mass<span class="token punctuation">:</span> <span class="token number">10</span><span class="token punctuation">,</span>
    cx<span class="token punctuation">:</span> <span class="token number">160</span><span class="token punctuation">,</span>
    cy<span class="token punctuation">:</span> <span class="token number">10</span><span class="token punctuation">,</span>
    vx<span class="token punctuation">:</span> <span class="token number">1.09</span><span class="token punctuation">,</span>
    vy<span class="token punctuation">:</span> <span class="token number">9.78</span><span class="token punctuation">,</span>
    elast<span class="token punctuation">:</span> <span class="token number">0.9</span><span class="token punctuation">,</span>
    r<span class="token punctuation">:</span> <span class="token number">5</span><span class="token punctuation">,</span>
  <span class="token punctuation">}</span><span class="token punctuation">,</span>
  <span class="token punctuation">{</span>
    name<span class="token punctuation">:</span> <span class="token string">'Evan'</span><span class="token punctuation">,</span>
    color<span class="token punctuation">:</span> <span class="token string">'blue'</span><span class="token punctuation">,</span>
    mass<span class="token punctuation">:</span> <span class="token number">10</span><span class="token punctuation">,</span>
    cx<span class="token punctuation">:</span> <span class="token number">200</span><span class="token punctuation">,</span>
    cy<span class="token punctuation">:</span> <span class="token number">10</span><span class="token punctuation">,</span>
    vx<span class="token punctuation">:</span> <span class="token operator">-</span><span class="token number">2.7</span><span class="token punctuation">,</span>
    vy<span class="token punctuation">:</span> <span class="token operator">-</span><span class="token number">8.12</span><span class="token punctuation">,</span>
    elast<span class="token punctuation">:</span> <span class="token number">0.9</span><span class="token punctuation">,</span>
    r<span class="token punctuation">:</span> <span class="token number">5</span><span class="token punctuation">,</span>
  <span class="token punctuation">}</span><span class="token punctuation">,</span>
  <span class="token punctuation">{</span>
    name<span class="token punctuation">:</span> <span class="token string">'Frank'</span><span class="token punctuation">,</span>
    color<span class="token punctuation">:</span> <span class="token string">'purple'</span><span class="token punctuation">,</span>
    mass<span class="token punctuation">:</span> <span class="token number">10</span><span class="token punctuation">,</span>
    cx<span class="token punctuation">:</span> <span class="token number">225</span><span class="token punctuation">,</span>
    cy<span class="token punctuation">:</span> <span class="token number">10</span><span class="token punctuation">,</span>
    vx<span class="token punctuation">:</span> <span class="token operator">-</span><span class="token number">8.9</span><span class="token punctuation">,</span>
    vy<span class="token punctuation">:</span> <span class="token number">19.6</span><span class="token punctuation">,</span>
    elast<span class="token punctuation">:</span> <span class="token number">0.9</span><span class="token punctuation">,</span>
    r<span class="token punctuation">:</span> <span class="token number">5</span><span class="token punctuation">,</span>
  <span class="token punctuation">}</span><span class="token punctuation">,</span>
  <span class="token punctuation">{</span>
    name<span class="token punctuation">:</span> <span class="token string">'George'</span><span class="token punctuation">,</span>
    color<span class="token punctuation">:</span> <span class="token string">'black'</span><span class="token punctuation">,</span>
    mass<span class="token punctuation">:</span> <span class="token number">10</span><span class="token punctuation">,</span>
    cx<span class="token punctuation">:</span> <span class="token number">250</span><span class="token punctuation">,</span>
    cy<span class="token punctuation">:</span> <span class="token number">10</span><span class="token punctuation">,</span>
    vx<span class="token punctuation">:</span> <span class="token number">27.87</span><span class="token punctuation">,</span>
    vy<span class="token punctuation">:</span> <span class="token operator">-</span><span class="token number">10.61</span><span class="token punctuation">,</span>
    elast<span class="token punctuation">:</span> <span class="token number">0.9</span><span class="token punctuation">,</span>
    r<span class="token punctuation">:</span> <span class="token number">5</span><span class="token punctuation">,</span>
  <span class="token punctuation">}</span><span class="token punctuation">,</span>
  <span class="token punctuation">{</span>
    name<span class="token punctuation">:</span> <span class="token string">'Hoover'</span><span class="token punctuation">,</span>
    color<span class="token punctuation">:</span> <span class="token string">'red'</span><span class="token punctuation">,</span>
    mass<span class="token punctuation">:</span> <span class="token number">10</span><span class="token punctuation">,</span>
    cx<span class="token punctuation">:</span> <span class="token number">275</span><span class="token punctuation">,</span>
    cy<span class="token punctuation">:</span> <span class="token number">10</span><span class="token punctuation">,</span>
    vx<span class="token punctuation">:</span> <span class="token operator">-</span><span class="token number">10.8</span><span class="token punctuation">,</span>
    vy<span class="token punctuation">:</span> <span class="token number">4.82</span><span class="token punctuation">,</span>
    elast<span class="token punctuation">:</span> <span class="token number">0.9</span><span class="token punctuation">,</span>
    r<span class="token punctuation">:</span> <span class="token number">5</span><span class="token punctuation">,</span>
  <span class="token punctuation">}</span><span class="token punctuation">,</span>
  <span class="token punctuation">{</span>
    name<span class="token punctuation">:</span> <span class="token string">'Isabella'</span><span class="token punctuation">,</span>
    color<span class="token punctuation">:</span> <span class="token string">'orange'</span><span class="token punctuation">,</span>
    mass<span class="token punctuation">:</span> <span class="token number">10</span><span class="token punctuation">,</span>
    cx<span class="token punctuation">:</span> <span class="token number">300</span><span class="token punctuation">,</span>
    cy<span class="token punctuation">:</span> <span class="token number">10</span><span class="token punctuation">,</span>
    vx<span class="token punctuation">:</span> <span class="token number">14.6</span><span class="token punctuation">,</span>
    vy<span class="token punctuation">:</span> <span class="token operator">-</span><span class="token number">0.9</span><span class="token punctuation">,</span>
    elast<span class="token punctuation">:</span> <span class="token number">0.9</span><span class="token punctuation">,</span>
    r<span class="token punctuation">:</span> <span class="token number">5</span><span class="token punctuation">,</span>
  <span class="token punctuation">}</span><span class="token punctuation">,</span>
  <span class="token punctuation">{</span>
    name<span class="token punctuation">:</span> <span class="token string">'Jack'</span><span class="token punctuation">,</span>
    color<span class="token punctuation">:</span> <span class="token string">'yellow'</span><span class="token punctuation">,</span>
    mass<span class="token punctuation">:</span> <span class="token number">10</span><span class="token punctuation">,</span>
    cx<span class="token punctuation">:</span> <span class="token number">340</span><span class="token punctuation">,</span>
    cy<span class="token punctuation">:</span> <span class="token number">10</span><span class="token punctuation">,</span>
    vx<span class="token punctuation">:</span> <span class="token operator">-</span><span class="token number">12.7</span><span class="token punctuation">,</span>
    vy<span class="token punctuation">:</span> <span class="token number">18.74</span><span class="token punctuation">,</span>
    elast<span class="token punctuation">:</span> <span class="token number">0.9</span><span class="token punctuation">,</span>
    r<span class="token punctuation">:</span> <span class="token number">5</span><span class="token punctuation">,</span>
  <span class="token punctuation">}</span><span class="token punctuation">,</span>
  <span class="token punctuation">{</span>
    name<span class="token punctuation">:</span> <span class="token string">'Kevin'</span><span class="token punctuation">,</span>
    color<span class="token punctuation">:</span> <span class="token string">'green'</span><span class="token punctuation">,</span>
    mass<span class="token punctuation">:</span> <span class="token number">10</span><span class="token punctuation">,</span>
    cx<span class="token punctuation">:</span> <span class="token number">380</span><span class="token punctuation">,</span>
    cy<span class="token punctuation">:</span> <span class="token number">10</span><span class="token punctuation">,</span>
    vx<span class="token punctuation">:</span> <span class="token number">19.1</span><span class="token punctuation">,</span>
    vy<span class="token punctuation">:</span> <span class="token operator">-</span><span class="token number">12.2</span><span class="token punctuation">,</span>
    elast<span class="token punctuation">:</span> <span class="token number">0.9</span><span class="token punctuation">,</span>
    r<span class="token punctuation">:</span> <span class="token number">5</span><span class="token punctuation">,</span>
  <span class="token punctuation">}</span><span class="token punctuation">,</span>
  <span class="token punctuation">{</span>
    name<span class="token punctuation">:</span> <span class="token string">'Lisa'</span><span class="token punctuation">,</span>
    color<span class="token punctuation">:</span> <span class="token string">'blue'</span><span class="token punctuation">,</span>
    mass<span class="token punctuation">:</span> <span class="token number">10</span><span class="token punctuation">,</span>
    cx<span class="token punctuation">:</span> <span class="token number">420</span><span class="token punctuation">,</span>
    cy<span class="token punctuation">:</span> <span class="token number">10</span><span class="token punctuation">,</span>
    vx<span class="token punctuation">:</span> <span class="token number">12.32</span><span class="token punctuation">,</span>
    vy<span class="token punctuation">:</span> <span class="token operator">-</span><span class="token number">21.67</span><span class="token punctuation">,</span>
    elast<span class="token punctuation">:</span> <span class="token number">0.9</span><span class="token punctuation">,</span>
    r<span class="token punctuation">:</span> <span class="token number">5</span><span class="token punctuation">,</span>
  <span class="token punctuation">}</span><span class="token punctuation">,</span>
  <span class="token punctuation">{</span>
    name<span class="token punctuation">:</span> <span class="token string">'Micacarphf'</span><span class="token punctuation">,</span>
    color<span class="token punctuation">:</span> <span class="token string">'purple'</span><span class="token punctuation">,</span>
    mass<span class="token punctuation">:</span> <span class="token number">10</span><span class="token punctuation">,</span>
    cx<span class="token punctuation">:</span> <span class="token number">460</span><span class="token punctuation">,</span>
    cy<span class="token punctuation">:</span> <span class="token number">10</span><span class="token punctuation">,</span>
    vx<span class="token punctuation">:</span> <span class="token operator">-</span><span class="token number">14.18</span><span class="token punctuation">,</span>
    vy<span class="token punctuation">:</span> <span class="token operator">-</span><span class="token number">1.65</span><span class="token punctuation">,</span>
    elast<span class="token punctuation">:</span> <span class="token number">0.9</span><span class="token punctuation">,</span>
    r<span class="token punctuation">:</span> <span class="token number">5</span><span class="token punctuation">,</span>
  <span class="token punctuation">}</span><span class="token punctuation">,</span>
<span class="token punctuation">]</span><span class="token punctuation">;</span>
</code></pre>
<h3 id="drawing-the-balls-1">Drawing the balls</h3>
<p>Then, use this code to draw the balls on the <code>svg</code>:</p>
<pre class=" language-javascript"><code class="prism  language-javascript">balls<span class="token punctuation">.</span><span class="token function">forEach</span><span class="token punctuation">(</span>ball <span class="token operator">=&gt;</span> <span class="token punctuation">{</span>
  ball<span class="token punctuation">.</span>dot <span class="token operator">=</span> svg<span class="token punctuation">.</span><span class="token function">append</span><span class="token punctuation">(</span><span class="token string">'circle'</span><span class="token punctuation">)</span><span class="token punctuation">.</span><span class="token function">attrs</span><span class="token punctuation">(</span><span class="token punctuation">{</span>
    cx<span class="token punctuation">:</span> ball<span class="token punctuation">.</span>cx<span class="token punctuation">,</span>
    cy<span class="token punctuation">:</span> ball<span class="token punctuation">.</span>cy<span class="token punctuation">,</span>
    r<span class="token punctuation">:</span> ball<span class="token punctuation">.</span>r<span class="token punctuation">,</span>
    fill<span class="token punctuation">:</span> ball<span class="token punctuation">.</span>color<span class="token punctuation">,</span>
    stroke<span class="token punctuation">:</span> <span class="token string">'none'</span>
  <span class="token punctuation">}</span><span class="token punctuation">)</span><span class="token punctuation">;</span>
<span class="token punctuation">}</span><span class="token punctuation">)</span><span class="token punctuation">;</span>
</code></pre>
<h2 id="declaring-gravity-and-lastt-variables">Declaring <code>Gravity</code> and <code>lastT</code> variables</h2>
<p>Declare the variables:</p>
<ul>
<li><code>g</code> (in px/s<sup>2</sup>)</li>
<li><code>lastT</code><br>
<code>g</code> can be anything you want, but <code>lastT</code> must be equal to <code>Date.now</code>.</li>
</ul>
<pre class=" language-javascript"><code class="prism  language-javascript"><span class="token keyword">const</span> g <span class="token operator">=</span> <span class="token number">196</span><span class="token punctuation">;</span>
<span class="token keyword">var</span> lastT <span class="token operator">=</span> Date<span class="token punctuation">.</span><span class="token function">now</span><span class="token punctuation">(</span><span class="token punctuation">)</span><span class="token punctuation">;</span>
</code></pre>
<h2 id="simulating-the-balls">Simulating the balls</h2>
<p>Create an <code>update</code> function to put each of the balls to the position where they are supposed to be at that exact time:</p>
<pre class=" language-javascript"><code class="prism  language-javascript"><span class="token keyword">const</span> <span class="token function-variable function">update</span> <span class="token operator">=</span> <span class="token punctuation">(</span><span class="token punctuation">)</span> <span class="token operator">=&gt;</span> <span class="token punctuation">{</span><span class="token punctuation">}</span>
</code></pre>
<h3 id="declaring-t-and-δt-variables">Declaring <code>t</code> and <code>Δt</code> variables</h3>
<p>Create a <code>t</code> and <code>Δt</code> variable inside the <code>update</code> function with <code>t</code> being <code>Date.now</code> and <code>Δt</code> being <code>t - lastT</code>. The <code>t</code> is the current time in milliseconds since 12:00:00.000 January 1<sup>st</sup> 1970 AD. The <code>Δt</code> is the difference between <code>lastT</code> and <code>t</code>. It is a time slice with a length of 10 milliseconds.</p>
<pre class=" language-javascript"><code class="prism  language-javascript"><span class="token keyword">const</span> <span class="token function-variable function">update</span> <span class="token operator">=</span> <span class="token punctuation">(</span><span class="token punctuation">)</span> <span class="token operator">=&gt;</span> <span class="token punctuation">{</span>
  <span class="token keyword">const</span> t <span class="token operator">=</span> Date<span class="token punctuation">.</span><span class="token function">now</span><span class="token punctuation">(</span><span class="token punctuation">)</span><span class="token punctuation">;</span>
  <span class="token keyword">const</span> Δt <span class="token operator">=</span> t <span class="token operator">-</span> lastT<span class="token punctuation">;</span>
<span class="token punctuation">}</span>
</code></pre>
<h3 id="looping-through-each-ball-and-making-it-do-what-it-should-do">Looping through each ball and making it do what it should do</h3>
<p>Inside the <code>update</code> function but outside and after the <code>checkCollide</code> function, create a <code>for</code> loop that looks like this:</p>
<pre class=" language-javascript"><code class="prism  language-javascript"><span class="token keyword">for</span> <span class="token punctuation">(</span><span class="token keyword">var</span> i <span class="token operator">=</span> <span class="token number">0</span><span class="token punctuation">;</span> i <span class="token operator">&lt;</span> balls<span class="token punctuation">.</span>length<span class="token punctuation">;</span> i<span class="token operator">++</span><span class="token punctuation">)</span><span class="token punctuation">{</span><span class="token punctuation">}</span>
</code></pre>
<p>Inside the <code>for</code> loop, the first line of code to write is <code>const ball = balls[i];</code>. Then, put an <code>if</code> statement in the <code>for</code> loop. The <code>if</code> statement’s conditional should be <code>ball.cy &gt;= 195</code>. This will see if it is touching the floor. If it is, you do this <code>ball.vy = -ball.vy * ball.elast</code>, which makes it bounce. Then, add the <code>else</code> part:<code>ball.vy += g * Δt / 1000;</code>.<br>
Put this in for bouncing off the other sides (upper wall, left side and right side):</p>
<pre class=" language-javascript"><code class="prism  language-javascript"><span class="token keyword">if</span> <span class="token punctuation">(</span>ball<span class="token punctuation">.</span>cy <span class="token operator">&lt;=</span> <span class="token number">5</span><span class="token punctuation">)</span> ball<span class="token punctuation">.</span>vy <span class="token operator">=</span> <span class="token operator">-</span>ball<span class="token punctuation">.</span>vy <span class="token operator">*</span> ball<span class="token punctuation">.</span>elast<span class="token punctuation">;</span>
<span class="token keyword">if</span> <span class="token punctuation">(</span>ball<span class="token punctuation">.</span>cx <span class="token operator">&lt;=</span> <span class="token number">5</span><span class="token punctuation">)</span> ball<span class="token punctuation">.</span>vx <span class="token operator">=</span> <span class="token operator">-</span>ball<span class="token punctuation">.</span>vx <span class="token operator">*</span> ball<span class="token punctuation">.</span>elast<span class="token punctuation">;</span>
<span class="token keyword">if</span> <span class="token punctuation">(</span>ball<span class="token punctuation">.</span>cx <span class="token operator">&gt;=</span> <span class="token number">495</span><span class="token punctuation">)</span> ball<span class="token punctuation">.</span>vx <span class="token operator">=</span> <span class="token operator">-</span>ball<span class="token punctuation">.</span>vx <span class="token operator">*</span> ball<span class="token punctuation">.</span>elast<span class="token punctuation">;</span>
</code></pre>
<pre class=" language-javascript"><code class="prism  language-javascript"><span class="token keyword">const</span> t <span class="token operator">=</span> Date<span class="token punctuation">.</span><span class="token function">now</span><span class="token punctuation">(</span><span class="token punctuation">)</span><span class="token punctuation">;</span>
<span class="token keyword">const</span> Δt <span class="token operator">=</span> t <span class="token operator">-</span> lastT<span class="token punctuation">;</span>
<span class="token keyword">for</span> <span class="token punctuation">(</span><span class="token keyword">var</span> i <span class="token operator">=</span> <span class="token number">0</span><span class="token punctuation">;</span> i <span class="token operator">&lt;</span> balls<span class="token punctuation">.</span>length<span class="token punctuation">;</span> i<span class="token operator">++</span><span class="token punctuation">)</span><span class="token punctuation">{</span>
  <span class="token keyword">const</span> ball <span class="token operator">=</span> balls<span class="token punctuation">[</span>i<span class="token punctuation">]</span><span class="token punctuation">;</span>
  <span class="token keyword">if</span> <span class="token punctuation">(</span>ball<span class="token punctuation">.</span>cy <span class="token operator">&gt;=</span> <span class="token number">195</span><span class="token punctuation">)</span> ball<span class="token punctuation">.</span>vy <span class="token operator">=</span> <span class="token operator">-</span>ball<span class="token punctuation">.</span>vy <span class="token operator">*</span> ball<span class="token punctuation">.</span>elast<span class="token punctuation">;</span>
  <span class="token keyword">else</span> ball<span class="token punctuation">.</span>vy <span class="token operator">+=</span> g <span class="token operator">*</span> Δt <span class="token operator">/</span> <span class="token number">1000</span><span class="token punctuation">;</span>
  <span class="token keyword">if</span> <span class="token punctuation">(</span>ball<span class="token punctuation">.</span>cy <span class="token operator">&lt;=</span> <span class="token number">5</span><span class="token punctuation">)</span> ball<span class="token punctuation">.</span>vy <span class="token operator">=</span> <span class="token operator">-</span>ball<span class="token punctuation">.</span>vy <span class="token operator">*</span> ball<span class="token punctuation">.</span>elast<span class="token punctuation">;</span>
  <span class="token keyword">if</span> <span class="token punctuation">(</span>ball<span class="token punctuation">.</span>cx <span class="token operator">&lt;=</span> <span class="token number">5</span><span class="token punctuation">)</span> ball<span class="token punctuation">.</span>vx <span class="token operator">=</span> <span class="token operator">-</span>ball<span class="token punctuation">.</span>vx <span class="token operator">*</span> ball<span class="token punctuation">.</span>elast<span class="token punctuation">;</span>
  <span class="token keyword">if</span> <span class="token punctuation">(</span>ball<span class="token punctuation">.</span>cx <span class="token operator">&gt;=</span> <span class="token number">495</span><span class="token punctuation">)</span> ball<span class="token punctuation">.</span>vx <span class="token operator">=</span> <span class="token operator">-</span>ball<span class="token punctuation">.</span>vx <span class="token operator">*</span> ball<span class="token punctuation">.</span>elast<span class="token punctuation">;</span>
<span class="token punctuation">}</span>
</code></pre>
<p>This code is what really makes them update their position:</p>
<pre class=" language-javascript"><code class="prism  language-javascript">ball<span class="token punctuation">.</span>cx <span class="token operator">+=</span> ball<span class="token punctuation">.</span>vx <span class="token operator">*</span> Δt <span class="token operator">/</span> <span class="token number">1000</span><span class="token punctuation">;</span>
ball<span class="token punctuation">.</span>cy <span class="token operator">+=</span> ball<span class="token punctuation">.</span>vy <span class="token operator">*</span> Δt <span class="token operator">/</span> <span class="token number">1000</span><span class="token punctuation">;</span>
</code></pre>
<p>Add this code:</p>
<pre class=" language-javascript"><code class="prism  language-javascript">ball<span class="token punctuation">.</span>cy <span class="token operator">=</span> Math<span class="token punctuation">.</span><span class="token function">min</span><span class="token punctuation">(</span><span class="token number">195</span><span class="token punctuation">,</span> ball<span class="token punctuation">.</span>cy<span class="token punctuation">)</span><span class="token punctuation">;</span>
ball<span class="token punctuation">.</span>cy <span class="token operator">=</span> Math<span class="token punctuation">.</span><span class="token function">max</span><span class="token punctuation">(</span><span class="token number">5</span><span class="token punctuation">,</span> ball<span class="token punctuation">.</span>cy<span class="token punctuation">)</span><span class="token punctuation">;</span>
ball<span class="token punctuation">.</span>cx <span class="token operator">=</span> Math<span class="token punctuation">.</span><span class="token function">min</span><span class="token punctuation">(</span><span class="token number">495</span><span class="token punctuation">,</span> ball<span class="token punctuation">.</span>cx<span class="token punctuation">)</span><span class="token punctuation">;</span>
ball<span class="token punctuation">.</span>cx <span class="token operator">=</span> Math<span class="token punctuation">.</span><span class="token function">max</span><span class="token punctuation">(</span><span class="token number">5</span><span class="token punctuation">,</span> ball<span class="token punctuation">.</span>cx<span class="token punctuation">)</span><span class="token punctuation">;</span>
</code></pre>
<p>And last bit of code:</p>
<pre class=" language-javascript"><code class="prism  language-javascript">ball<span class="token punctuation">.</span>dot<span class="token punctuation">.</span><span class="token function">attrs</span><span class="token punctuation">(</span><span class="token punctuation">{</span>
  cx<span class="token punctuation">:</span> ball<span class="token punctuation">.</span>cx<span class="token punctuation">,</span>
  cy<span class="token punctuation">:</span> ball<span class="token punctuation">.</span>cy
<span class="token punctuation">}</span><span class="token punctuation">)</span><span class="token punctuation">;</span>
</code></pre>
<p>This is what your <code>update</code> function should look like:</p>
<pre class=" language-javascript"><code class="prism  language-javascript"><span class="token keyword">const</span> <span class="token function-variable function">update</span> <span class="token operator">=</span> <span class="token punctuation">(</span><span class="token punctuation">)</span> <span class="token operator">=&gt;</span> <span class="token punctuation">{</span>
  <span class="token keyword">const</span> t <span class="token operator">=</span> Date<span class="token punctuation">.</span><span class="token function">now</span><span class="token punctuation">(</span><span class="token punctuation">)</span><span class="token punctuation">;</span>
  <span class="token keyword">const</span> Δt <span class="token operator">=</span> t <span class="token operator">-</span> lastT<span class="token punctuation">;</span>
  lastT <span class="token operator">=</span> t<span class="token punctuation">;</span>
  <span class="token keyword">for</span> <span class="token punctuation">(</span><span class="token keyword">var</span> i <span class="token operator">=</span> <span class="token number">0</span><span class="token punctuation">;</span> i <span class="token operator">&lt;</span> balls<span class="token punctuation">.</span>length<span class="token punctuation">;</span> i<span class="token operator">++</span><span class="token punctuation">)</span><span class="token punctuation">{</span>
    <span class="token keyword">const</span> ball <span class="token operator">=</span> balls<span class="token punctuation">[</span>i<span class="token punctuation">]</span><span class="token punctuation">;</span>
    <span class="token keyword">if</span> <span class="token punctuation">(</span>ball<span class="token punctuation">.</span>cy <span class="token operator">&gt;=</span> <span class="token number">195</span><span class="token punctuation">)</span> ball<span class="token punctuation">.</span>vy <span class="token operator">=</span> <span class="token operator">-</span>ball<span class="token punctuation">.</span>vy <span class="token operator">*</span> ball<span class="token punctuation">.</span>elast<span class="token punctuation">;</span>
    <span class="token keyword">else</span> ball<span class="token punctuation">.</span>vy <span class="token operator">+=</span> g <span class="token operator">*</span> Δt <span class="token operator">/</span> <span class="token number">1000</span><span class="token punctuation">;</span>
    <span class="token keyword">if</span> <span class="token punctuation">(</span>ball<span class="token punctuation">.</span>cy <span class="token operator">&lt;=</span> <span class="token number">5</span><span class="token punctuation">)</span> ball<span class="token punctuation">.</span>vy <span class="token operator">=</span> <span class="token operator">-</span>ball<span class="token punctuation">.</span>vy <span class="token operator">*</span> ball<span class="token punctuation">.</span>elast<span class="token punctuation">;</span>
    <span class="token keyword">if</span> <span class="token punctuation">(</span>ball<span class="token punctuation">.</span>cx <span class="token operator">&lt;=</span> <span class="token number">5</span><span class="token punctuation">)</span> ball<span class="token punctuation">.</span>vx <span class="token operator">=</span> <span class="token operator">-</span>ball<span class="token punctuation">.</span>vx <span class="token operator">*</span> ball<span class="token punctuation">.</span>elast<span class="token punctuation">;</span>
    <span class="token keyword">if</span> <span class="token punctuation">(</span>ball<span class="token punctuation">.</span>cx <span class="token operator">&gt;=</span> <span class="token number">495</span><span class="token punctuation">)</span> ball<span class="token punctuation">.</span>vx <span class="token operator">=</span> <span class="token operator">-</span>ball<span class="token punctuation">.</span>vx <span class="token operator">*</span> ball<span class="token punctuation">.</span>elast<span class="token punctuation">;</span>
     ball<span class="token punctuation">.</span>cx <span class="token operator">+=</span> ball<span class="token punctuation">.</span>vx <span class="token operator">*</span> Δt <span class="token operator">/</span> <span class="token number">1000</span><span class="token punctuation">;</span>
    ball<span class="token punctuation">.</span>cy <span class="token operator">+=</span> ball<span class="token punctuation">.</span>vy <span class="token operator">*</span> Δt <span class="token operator">/</span> <span class="token number">1000</span><span class="token punctuation">;</span>
    ball<span class="token punctuation">.</span>cy <span class="token operator">=</span> Math<span class="token punctuation">.</span><span class="token function">min</span><span class="token punctuation">(</span><span class="token number">195</span><span class="token punctuation">,</span> ball<span class="token punctuation">.</span>cy<span class="token punctuation">)</span><span class="token punctuation">;</span>
    ball<span class="token punctuation">.</span>cy <span class="token operator">=</span> Math<span class="token punctuation">.</span><span class="token function">max</span><span class="token punctuation">(</span><span class="token number">5</span><span class="token punctuation">,</span> ball<span class="token punctuation">.</span>cy<span class="token punctuation">)</span><span class="token punctuation">;</span>
    ball<span class="token punctuation">.</span>cx <span class="token operator">=</span> Math<span class="token punctuation">.</span><span class="token function">min</span><span class="token punctuation">(</span><span class="token number">495</span><span class="token punctuation">,</span> ball<span class="token punctuation">.</span>cx<span class="token punctuation">)</span><span class="token punctuation">;</span>
    ball<span class="token punctuation">.</span>cx <span class="token operator">=</span> Math<span class="token punctuation">.</span><span class="token function">max</span><span class="token punctuation">(</span><span class="token number">5</span><span class="token punctuation">,</span> ball<span class="token punctuation">.</span>cx<span class="token punctuation">)</span><span class="token punctuation">;</span>
    ball<span class="token punctuation">.</span>dot<span class="token punctuation">.</span><span class="token function">attrs</span><span class="token punctuation">(</span><span class="token punctuation">{</span>
      cx<span class="token punctuation">:</span> ball<span class="token punctuation">.</span>cx<span class="token punctuation">,</span>
      cy<span class="token punctuation">:</span> ball<span class="token punctuation">.</span>cy
    <span class="token punctuation">}</span><span class="token punctuation">)</span><span class="token punctuation">;</span>
  <span class="token punctuation">}</span>
<span class="token punctuation">}</span><span class="token punctuation">;</span>
</code></pre>
<p>Add this code to call <code>update</code> every 10 milliseconds:</p>
<pre class=" language-javascript"><code class="prism  language-javascript"><span class="token function">setInterval</span><span class="token punctuation">(</span>update<span class="token punctuation">,</span> <span class="token number">10</span><span class="token punctuation">)</span><span class="token punctuation">;</span>
</code></pre>
<p>10 milliseconds because it is the length of <code>Δt</code>.</p>

