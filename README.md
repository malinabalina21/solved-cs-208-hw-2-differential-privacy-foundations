Download Link: https://assignmentchef.com/product/solved-cs-208-hw-2-differential-privacy-foundations
<br>
<ol>

 <li><strong>Mechanisms: </strong>Consider the following mechanisms <em>M </em>that takes a dataset <em>x </em>∈ [0<em>,</em>1]<em><sup>n </sup></em>and returns an estimate of the mean ¯ .

  <ul>

   <li>, for <em>Z </em>∼ Lap(2<em>/n</em>), where for real numbers <em>y </em>and <em>a </em>≤ <em>b</em>, [<em>y</em>]<em><sup>b</sup><sub>a </sub></em>denotes the</li>

  </ul></li>

</ol>

<table width="366">

 <tbody>

  <tr>

   <td width="284">“clamping” function:</td>

   <td width="82"> </td>

  </tr>

  <tr>

   <td width="284"><em>a</em><em>b</em>[<em>y</em>]<em><sub>a </sub></em>=       <em>y</em><em>b</em></td>

   <td width="82">if <em>y &lt; a </em>if <em>a </em>≤ <em>y </em>≤ <em>b .</em>if <em>y &gt; b</em></td>

  </tr>

 </tbody>

</table>

<ul>

 <li>, for <em>Z </em>∼ Lap(2<em>/n</em>). iii</li>

</ul>

(

1      w.p. <em>x</em>

<em>M</em>(<em>x</em>) =<em>.</em>

0      w.p. 1 − <em>x.</em>

iv <em>M</em>(<em>x</em>) = <em>Y </em>where <em>Y </em>has probability density function <em>f<sub>Y </sub></em>given as follows:

if <em>y </em>∈ [0<em>,</em>1]<em>.</em>

0                                if <em>y /</em>∈ [0<em>,</em>1]<em>.</em>

(This is an instantiation of a continuous version of the exponential mechanism.)

<ul>

 <li>Which of the above mechanisms meet the definition of (<em>,</em>0)-differential privacy for a finite value of , and what is the smallest value of (possibly as a function of <em>n</em>) for which they do?</li>

 <li>For those that do not meet the definition, calculate the smallest value of <em>δ </em>(again possibly as a function of <em>n</em>) for which they satisfy (<em>,δ</em>) differential privacy for a finite value of .</li>

 <li>Describe how you would modify the algorithms to have tunable privacy parameters (and <em>δ </em>in case of mechanisms that require it) and tunable data domain [<em>a,b</em>] (rather than [0<em>,</em>1]).</li>

 <li>Which of these algorithms do you consider to be “best” for releasing a mean and why?</li>

</ul>

(There is not a single “right” answer for this problem.)

<ol start="2">

 <li><strong>Evaluating DP Algorithms with Synthetic Data: </strong>Consider a dataset <em>x </em>∈ N<em><sup>n </sup></em>drawn from a Poisson process, which has probability distribution Pr[<em>x<sub>i </sub></em>= <em>k</em>] = 10<em><sup>k</sup>e</em><sup>−<a href="#_ftn1" name="_ftnref1">[1]</a>0</sup><em>/k</em>! for natural numbers <em>k </em>(where we consider <em>k </em>= 0 to be a natural number and define 0! = 1).

  <ul>

   <li>Write a <em>data generating process </em>(DGP) function that generates a dataset <em>x </em>∈ N<em><sup>n </sup></em>according the above Poisson process.</li>

   <li>Pick one of your differentially private mechanisms from question 1 (generalized to allow for arbitrary choices of and data range [<em>a,b</em>] as parameters) that releases an estimate of ¯<em>x</em>. Implement this mechanism as a function which is given a vector of values <em>x </em>∈ [<em>a,b</em>]<em><sup>n </sup></em>and an <em> </em>and makes a differentially private release. You can assume the sample size <em>n </em>is public knowledge. To apply your mechanism to unbounded data <em>x </em>∈ R<em><sup>n</sup></em>, you will have to clamp <em>x </em>to a chosen range [<em>a,b</em>]. For simplicity, we will fix <em>a </em>= 0 and only consider the effect of varying <em>b</em>.</li>

   <li>Recall the discussion on clamping from class; if the range is large, the sensitivity increases, so noise increases and utility drops. However, if you clip the values too aggressively the answer will be biased, and again utility will drop. For <em>n </em>= 200 and 5, plot the root mean squared error as a function of the upper bound <em>b</em>. Identify the approximate optimal value <em>b</em><sup>∗ </sup>of <em>b </em>for this data distribution.</li>

   <li>Suppose we have an actual (not synthetic) dataset <em>x </em>∈ N<em><sup>n </sup></em>for which we want to release a differentially private mean, and we don’t know the underlying distribution of <em>x</em>. Again, we need to select the parameter <em>b </em>and want to do so in a way that minimizes the error. A natural idea is to use a <em>(nonparametric) bootstrap</em><sup>1 </sup>to generate many datasets that are “similar” to <em>x </em>in place of the data-generating process above, and optimize the choice of <em>b </em>as above. Once we find an optimal value <em>b</em><sup>∗</sup>, we then do our differentially private release on the dataset <em>x </em></li>

  </ul></li>

</ol>

Explain why this approach is not safe in general and may violate differential privacy.

<ul>

 <li>Propose some alternative methods for determining a good upper bound <em>b </em>for a given sensitive dataset <em>x</em>, while continuing to satisfying the definition of differential privacy.</li>

</ul>

<ol start="3">

 <li><strong>Regression: </strong>Consider a dataset where each of its <em>n </em>rows is a pair of real numbers (<em>x<sub>i</sub>,y<sub>i</sub></em>), where <em>x<sub>i </sub></em>is drawn from a Poisson distribution as in Problem 2, and <em>y<sub>i </sub></em>is then a noisy linear function of <em>x<sub>i</sub></em>, specifically:</li>

</ol>

<em>y<sub>i </sub></em>= <em>βx<sub>i </sub></em>+ <em>α </em>+ <em>ν<sub>i</sub></em>;                 <em>ν<sub>i </sub></em>∼ N(0<em>,σ</em><a href="#_ftn2" name="_ftnref2"><sup>[2]</sup></a>)                                                          (1)

for unknown parameters <em>α,β,σ</em>.

One simple way to estimate the parameters <em>α </em>and <em>β </em>without privacy is by a simple linear regression, using the following estimators:

(2)

<em>α</em>ˆ = ¯<em>y </em>− <em>β</em><sup>ˆ</sup><em>x</em>¯;                                                                                                       (3)

<ul>

 <li>In class and section, we saw an algorithm and implementation to produce a differentially private version of <em>β</em><sup>ˆ</sup>.<sup>2 </sup>Augment this implementation to also produce a differentially private version of ˆ<em>α</em>, so that the overall method for computing both ˆ<em>α </em>and -DP, for an input parameter . If your algorithms use several basic differentially private algorithms as subroutines, divide the overall privacy budget of among them evenly. You can clamp both the <em>x<sub>i</sub></em>’s and <em>y<sub>i</sub></em>’s using reasonable values of your choosing (perhaps following your choice from Problem 2 for <em>x</em>). Describe the reasoning behind your choice in your write up.</li>

 <li>Evaluate the performance of your algorithm using a Monte Carlo simulation with synthetic data as in Problem 2 Parts (a)–(c), for the parameters = 1 and <em>n </em>= 1000.</li>

</ul>

Measure utility by the mean-squared residuals:

<em> .</em>

(The non-private method for simple linear regression described above is chosen to minimize this quantity, hence the term “least-squares regression”.) Plot and compare the distributions of mean-squared residuals you get with your differentially private simple linear regression and with a non-private simple linear regression.

<ul>

 <li>Now, run experiments to see if there is a different partition of your privacy budget in your algorithm that yields better utility. Use a grid search<a href="#_ftn3" name="_ftnref3"><sup>[3]</sup></a> to explore different partitions of <em> </em>and see if you find one that is convincingly better (in terms of mean-squared residuals) than an equal partition under the given data distribution. Show and explain your results.</li>

</ul>

<ol start="4">

 <li><strong>DP vs. Reconstruction Attacks: </strong>Suppose <em>M </em>: {0<em>,</em>1}<em><sup>n </sup></em>→ Y is an (<em>,δ</em>)-DP mechanism and <em>A </em>: Y → {0<em>,</em>1}<em><sup>n </sup></em>is an adversary that is trying to reconstruct the sensitive bits in the dataset <em>x </em>∈ {0<em>,</em>1}<em><sup>n </sup></em>from the output <em>M</em>(<em>x</em>). Suppose the dataset is a random variable <em>X </em>= (<em>X</em><sub>1</sub><em>,…,X<sub>n</sub></em>) consisting of <em>n </em>iid draws from a Bernoulli(<em>p</em>) distribution, for a known value of <em>p</em>. Prove that the expected fraction of bits that the adversary successfully reconstructs is not much larger than the trivial bound of max{<em>p,</em>1 − <em>p</em>} (which can be achieved by guessing the all-zeroes or all-ones dataset). Specifically:</li>

</ol>

E[#

(Hint: write the quantity inside the expectation as an average of indicator random variables, and for each <em>i</em>, consider running <em>M </em>on the dataset <em>X</em><sup>(<em>i</em>) </sup>where we replace the <em>i</em>’th row of <em>X </em>with the fixed value 0.)


