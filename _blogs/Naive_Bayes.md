---
layout: default
title: "Exploring Conditional Independence in Naive Bayes"
date:    2023-09-15 14:00:00
selected: true
---

## Naive Bayes Model
&nbsp;

<div style="display: flex; justify-content: space-between;">
    <div style="flex: 1; text-align: center;">
        <img src="../images/Naive_Bayes.png" alt="Breaks" width="40%">
        <!-- <br>
        <p><b>Fig: Network Graph for Naive Bayes Model</b></p> -->
    </div>
</div>
<br>


&nbsp;
## Introduction

Naive Bayes model is a simple and efficient classification algorithm based on Bayes' Theorem. It is called "naive" because it assumes that the features (or input variables) are conditionally independent of each other, given the class label. Before diving deep, here is a simple explanation of the topics that the Naive Bayes model is built upon.

Our goal is to represent a joint distribution \( P \) over some set of random variables $$ X = \{ X_1, ....., X_n \} $$.

There are $$ 2^{n} - 1 $$ numbers required to represent the joint distribution. However, the explicit representation of the joint distribution is unmanageable because it contains a large number of parameters.

In this case, the independence properties in the distribution can be used to represent such quantities in a more compact manner.


### Conditional Parameterization

Before jumping into the Naive Bayes model, it is important to understand conditional parameterization. Let us consider an example having two variables: College Success (S) and High School GPA (G), where a college wants to predict the chances of a student being successful in college. Here, the joint probability has four distributions.

<div align="center">

$$ 
\begin{array}{ccc}
S & G & P(S, G) \\
s_{0} & g_{0} & 0.30 \\
s_{0} & g_{1} & 0.20 \\
s_{1} & g_{0} & 0.10 \\
s_{1} & g_{1} & 0.40 \\
\end{array}
$$

Table: Joint Probability Distribution of \( S \) and \( G \)

</div>

Using the rule of conditional probability, we can have:

$$
P(S, G) = P(G) \cdot P(S \mid G)
$$

Using above equation, we can represent the joint probability distribution in an alternative way.

Let's represent the above table using the prior distribution over GPA \(G\) and the conditional probability distribution of College Success \(S\) given GPA \(G\).
<div align="center">

$$
\begin{array}{|c|c|}
\hline
G & P(G) \\
\hline
g_{1} & 0.6 \\
\hline
g_{0} & 0.4 \\
\hline
\end{array}
$$

Table: Marginal Probability Table of \( G \) (High School GPA)

</div>
<br>
To calculate the marginal probabilities of \(G\), we sum the values of \(G\) over all values of \(S\).

$$
P(g_1) = P(s_1, g_1) + P(s_0, g_1) = 0.40 + 0.20 = 0.6
$$

$$
P(g_0) = P(s_1, g_0) + P(s_0, g_0) = 0.10 + 0.30 = 0.4
$$

Now, the conditional probability of college success \(S\) given GPA \(G\).

<div align="center">

$$
\begin{array}{|c|c|c|}
\hline
 & S = s_0 & S = s_1 \\
\hline
G = g_0 & 0.75 & 0.25 \\
\hline
G = g_1 & 0.33 & 0.67 \\
\hline
\end{array}
$$

Table: Joint Probability Table of College Success \(S\) and High School GPA \(G\)

</div>

To calculate the conditional probability of college success \(S\) given GPA \(G\), these steps were taken:

$$
P(s_1 \mid g_1) = \frac{P(s_1, g_1)}{P(g_1)} = \frac{0.4}{0.6} = 0.67
$$

$$
P(s_0 \mid g_1) = \frac{P(s_0, g_1)}{P(g_1)} = \frac{0.2}{0.6} = 0.33
$$

$$
P(s_1 \mid g_0) = \frac{P(s_1, g_0)}{P(g_0)} = \frac{0.1}{0.4} = 0.25
$$

$$
P(s_0 \mid g_0) = \frac{P(s_0, g_0)}{P(g_0)} = \frac{0.3}{0.4} = 0.75
$$

From here, we can represent using 3 values of distributions: $$ P(G) $$, $$ P(S \mid g_0) $$, and $$ P(S \mid g_1) $$.


Here, we learned how we can show the independence properties in variables. Now, I think we are ready to explore **Naive Bayes Model**.


### Naive Bayes Model

The Naive Bayes Model assumes that the number of features $$ X_1, ..... , X_n $$ are conditionally independent given the instance’s class. Based on the assumption of independence, we can factorize as:

$$
P(C, X_1, \ldots, X_n) = P(C) \prod_{i=1}^{n} P(X_i \mid C)
$$

Now, let's understand how using Naive Bayes can help to represent probability with a smaller number of parameters.

### Without the Naive Bayes Assumption

Suppose we need to represent the joint probability distribution of $$ P(C, X_1, X_2, X_3) $$.  
Let us assume that the class variable $$ C $$ is binary and the three features $$ X_1, X_2, X_3 $$ also take binary values (either 0 or 1).  
Since $$ C, X_1, X_2, X_3 $$ are all binary, there can be $$ 2^4 = 16 $$ possible combinations of values.


Here, the combinations can be shown as follows:

<div align="center">

$$
\begin{array}{|c|c|c|c|c|}
\hline
C & X_1 & X_2 & X_3 & P(C, X_1, X_2, X_3) \\
\hline
0 & 0 & 0 & 0 & P(0, 0, 0, 0) \\
0 & 0 & 0 & 1 & P(0, 0, 0, 1) \\
0 & 0 & 1 & 0 & P(0, 0, 1, 0) \\
0 & 0 & 1 & 1 & P(0, 0, 1, 1) \\
0 & 1 & 0 & 0 & P(0, 1, 0, 0) \\
0 & 1 & 0 & 1 & P(0, 1, 0, 1) \\
0 & 1 & 1 & 0 & P(0, 1, 1, 0) \\
0 & 1 & 1 & 1 & P(0, 1, 1, 1) \\
1 & 0 & 0 & 0 & P(1, 0, 0, 0) \\
1 & 0 & 0 & 1 & P(1, 0, 0, 1) \\
1 & 0 & 1 & 0 & P(1, 0, 1, 0) \\
1 & 0 & 1 & 1 & P(1, 0, 1, 1) \\
1 & 1 & 0 & 0 & P(1, 1, 0, 0) \\
1 & 1 & 0 & 1 & P(1, 1, 0, 1) \\
1 & 1 & 1 & 0 & P(1, 1, 1, 0) \\
1 & 1 & 1 & 1 & P(1, 1, 1, 1) \\
\hline
\end{array}
$$

Table: Joint Probability Distribution of \( C \) and \( (X_1, X_2, X_3) \)

</div>

There are 16 probabilities to specify in total. Here, the sum of all the probabilities must be equal to one (1), so only 15 probabilities are independent. Hence, we need 15 independent parameters to specify the joint distribution.

### With the Naive Bayes Assumption

What Naive Bayes states is that the features $$ X_1, X_2, X_3 $$ are conditionally independent given the class $$(C)$$.  
So, the joint distribution can be factorized into:

$$
P(C, X_1, X_2, X_3) = P(C) \times P(X_1 \mid C) \times P(X_2 \mid C) \times P(X_3 \mid C)
$$


If we observe carefully, we need to specify the following probabilities:

- $$ P(C) $$: The prior probability of the class variable $$ C $$, which requires only 1 parameter.  
  - Since $$ P(C = 0) $$ can be derived as $$ 1 - P(C = 1) $$, we only need to specify one probability.

Similarly, we can look at the **conditional probabilities** as:

- $$ P(X_1 \mid C) $$: The conditional probability of $$ X_1 $$ given $$ C $$.<br>
  $$ P(X_1 = 1 \mid C = 0) $$ <br>
  $$ P(X_1 = 1 \mid C = 1) $$ <br>
  The probabilities for $$ P(X_1 = 0 \mid C = 0) $$ and $$ P(X_1 = 0 \mid C = 1) $$ are $$ 1 - P(X_1 = 1 \mid C = 0) $$ and $$ 1 - P(X_1 = 1 \mid C = 1) $$, respectively.  <br>
    **Hence**, we only need two values to specify the possible probabilities in $$ P(X_1 \mid C) $$.

- $$ P(X_2 \mid C) $$: The conditional probability of $$ X_2 $$ given $$ C $$. <br>
  $$ P(X_2 = 1 \mid C = 0) $$ <br>
  $$ P(X_2 = 1 \mid C = 1) $$ <br>
    **Hence**, we only need two values to specify the possible probabilities in $$ P(X_2 \mid C) $$. 

- $$ P(X_3 \mid C) $$: The conditional probability of $$ X_3 $$ given $$ C $$. <br>
  $$ P(X_3 = 1 \mid C = 0) $$ <br>
  $$ P(X_3 = 1 \mid C = 1) $$  <br>
    **Hence**, we only need two values to specify the possible probabilities in $$ P(X_3 \mid C) $$.


Now, if you count the total number of parameters required to represent the joint distribution, it reduces to **7** parameters: \( 1 + 2 + 2 + 2 \).

### Conclusion

Now, you can clearly see that we have represented the joint distribution in a factorized and compact manner. However, one of the limitations of the Naive Bayes model is that it assumes the features are conditionally independent given the class.

### References
1. *Probabilistic Graphical Models* by **Daphne Koller** and **Nir Friedman** 

2. *Probability and Statistics for Engineers* by **Tek Bahadur Budhathoki** 

