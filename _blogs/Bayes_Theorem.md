---
layout: default
title: "Bayes' Theorem?? Explanation by an Example"
date:    2023-09-15 14:00:00
selected: true
---


# Bayes’ Theorem (Rule of Inverse Probability)

&nbsp;

<div style="text-align: center;">
  <img src="../images/Bayes.png" alt="Bayes' Rule" width="300">
</div>


&nbsp;

Bayes’ Theorem is an extension of conditional probability that helps to update the estimate of the prior probability based on the posterior probability.

**Prior Probability** -> **New Probability** -> **Application of Bayes’ Theorem** -> **Posterior Probability**

<div style="border: 1px solid; padding: 10px; display: inline-block;">
  $$P(H \mid E) = \frac{P(H) \cdot P(E \mid H)}{P(E)}$$
</div>

&nbsp;

**P(H)**: Probability a hypothesis is true (Before any evidence)

**P(E \| H)**: Probability of seeing the evidence if the hypothesis is true

**P(E)**: Probability of seeing the evidence

**P(H \| E)**: Probability a hypothesis is true given by some evidence
&nbsp; 

## Understanding Bayes' Theorem with an Example
&nbsp;

Consider a population and let Cancer denote the people suffering from the Cancer disease and Smoking denotes people who smoke. Now, let us assume the probability $$
P(\text{Cancer} \mid \text{Smoking}) = 0.6
$$
Here, we can infer that some of the people are suffering from cancer.

Now, can we find the probability of the people that are smoking? We can find it according to the Bayes’ rule if we have a prior probability of the people suffering from cancer P(Cancer) and people who smoke P(Smoking). 
Suppose we have the following probabilities:

$$
P(\text{Smoking}) = 0.3
$$

$$
P(\text{Cancer}) = 0.2
$$

$$
P(\text{Cancer} \mid \text{Smoking}) = 0.6
$$

Now, we want to find the probability of a person smoking given that they have cancer:

$$
P(\text{Smoking} \mid \text{Cancer}) = ?
$$

According to Bayes' Theorem, we have:

$$
P(\text{Smoking} \mid \text{Cancer}) = \frac{P(\text{Smoking}) \cdot P(\text{Cancer} \mid \text{Smoking})}{P(\text{Cancer})}
$$

Now, substituting the given values:

$$
P(\text{Smoking} \mid \text{Cancer}) = \frac{0.3 \times 0.6}{0.2}
$$

Calculating this gives:

$$
P(\text{Smoking} \mid \text{Cancer}) = 0.9
$$

This suggests that people who have cancer are strongly involved in smoking. 

This does not end here!!! 

Now let us assume that **P(Cancer)**= 0.4 among people. 

Using Bayes’ Theorem, we can calculate the probability of smoking given cancer:

$$
P(\text{Smoking} \mid \text{Cancer}) = \frac{P(\text{Smoking}) \cdot P(\text{Cancer} \mid \text{Smoking})}{P(\text{Cancer})}
$$

Substituting the given values:

$$
P(\text{Smoking} \mid \text{Cancer}) = \frac{0.3 \times 0.6}{0.4}
$$

Calculating this gives:

$$
P(\text{Smoking} \mid \text{Cancer}) = 0.45
$$

### Do you see the difference?

We could conclude that there was a strong relationship between cancer and smoking when the probability of cancer was quite rare.

Now, when the probability of cancer was quite common among people, it was not conclusive about the relationship of cancer with smoking.

You can tweak the values and understand the concept of probability. You can definitely see the cause and effect of the tweak of the values. 



## References

1. *Probabilistic Graphical Models* by **Daphne Koller** and **Nir Friedman** 

2. *Probability and Statistics for Engineers* by **Tek Bahadur Budhathoki** 

3. *Bayes' Theorem* by **3Blue1Brown** (Grant Sanderson)
