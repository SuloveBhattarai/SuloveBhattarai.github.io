---
layout: default
title: "How Conditional Independence Shapes Our Understanding of Data??"
date:    2023-09-15 14:00:00
selected: true
---

## Conditional Independence

### What is conditional independence?

Conditional independence is the concept that describes that two random variables are independent given the knowledge of a third variable.

### Let’s see an example:

In Nepal, Pulchowk Campus and Thapathali Campus are two of the major institutions for teaching engineering subjects. Many students want to get admitted to these campuses, where merit-based scholarships are provided.

Now, let’s talk about the chance of a student being admitted to Pulchowk and Thapathali. We could say there is a higher chance of getting admitted to Thapathali Campus if one is admitted to Pulchowk Campus.

However, let’s introduce a third variable. Let’s assume that a student's admission to Pulchowk and Thapathali Campus is based on their grade, i.e., Grade A (if students get Grade A, there is a higher probability of getting admitted to both campuses).

With this third variable, the chance of admission to Pulchowk Campus does not affect the chance of admission to Thapathali Campus. In this case, the chance of being admitted to Thapathali is dependent on the grade (Grade A) and independent of admission to Pulchowk Campus.

Let's assume:
- **Admit Pulchowk**: The event that denotes admission to Pulchowk Campus.
- **Admit Thapathali**: The event that denotes admission to Thapathali Campus.
- **GradeA**: The event that denotes obtaining Grade A.

With the introduction of GradeA, the events **Admit Pulchowk** and **Admit Thapathali** are conditionally independent given **GradeA**.

Now, according to the theorem:
$$
P(\text{Admit Pulchowk} \mid \text{Admit Thapathali} \cap \text{GradeA}) = P(\text{Admit Pulchowk} \mid \text{GradeA}) \tag{1}
$$

We can claim that, Admission of Pulchowk is conditionally independent of Admission to Thapathali given GradeA in the probability distribution P, given as: 

$$
P \models (\text{Admit Pulchowk} \cap \text{Admit Thapathali} \mid \text{GradeA}), \text{ if } P(\text{Admit Pulchowk} \mid \text{Admit Thapathali} \cap \text{GradeA}) = P(\text{Admit Pulchowk} \mid \text{GradeA})
$$

Let’s see a Mathematical Proof: 
For computation, let’s make it easier: 
Let:
-**Admit Pulchowk**= A,
-**Admit Thapathali**= B, 
-**GradeA**= C


The following equation shows the relationship:

$$
P(A \mid B \cap C) = P(A \mid C) \tag{3}
$$

The conditional independence can be expressed as:

$$
P \models (A \cap B \mid C), \text{ if } P(A \mid B \cap C) = P(A \mid C) \text{ or if } P(B \cap C) = 0
$$
### According to the Theorem

The theorem states that:

$$
P(A \mid B \cap C) = P(A \mid C) \tag{3}
$$

Conditional independence is expressed as:

$$
P \models (A \cap B \mid C), \text{ if } P(A \mid B \cap C) = P(A \mid C) \text{ or if } P(B \cap C) = 0
$$

We can extend this to:

$$
P \text{ satisfies } (A \cap B \mid C) \text{ if and only if } P(A \cap B \mid C) = P(A \mid C) \cdot P(B \mid C) \tag{4}
$$

### Proof

From the first equation, let’s apply the formula of conditional probability:

$$
P(A \mid B \cap C) = P(A \mid C) 
$$

$$
P(A \mid B \cap C) = \frac{P(A \cap B \cap C)}{P(B \cap C)} \tag{5}
$$

$$
P(A \mid C) = \frac{P(A \cap C)}{P(C)} \tag{6}
$$

$$
P(A \cap B \cap C) = P(A \mid B \cap C) \cdot P(B \cap C) \tag{7}
$$

From the definition, we can write:

$$
P(A \mid B \cap C) = P(A \mid C)
$$

Now equation (7) becomes:

$$
P(A \cap B \cap C) = P(A \mid C) \cdot P(B \cap C)
$$

Divide both sides by $$P(B \cap C)$$:

$$
\frac{P(A \cap B \cap C)}{P(B \cap C)} = \frac{P(A \mid C) \cdot P(B \cap C)}{P(B \cap C)} \tag{8}
$$

$$
P(A \mid B \cap C) = P(A \mid C) \tag{9}
$$

Hence proved.

We can derive other results from the above equation (7):

$$
P(A \cap B \cap C) = P(A \mid C) \cdot P(B \mid C) \cdot P(C) \tag{10}
$$

Dividing both sides by $$P(C)$$, equation (10) becomes:

$$
P(A \cap B \mid C) = P(A \mid C) \cdot P(B \mid C)
$$

Therefore, equations (3) and (4) both satisfy the conditions. So, in the case of conditional probability, both equations (3) and (4) hold true:

$$
P(A \mid B \cap C) = P(A \mid C) 
$$

$$
P(A \cap B \mid C) = P(A \mid C) \cdot P(B \mid C)
$$

Hence, this is true with the introduction of the new variable GradeA:

$$
P(\text{Admit Pulchowk} \mid \text{Admit Thapathali} \cap \text{GradeA}) = P(\text{Admit Pulchowk} \mid \text{GradeA})
$$

&nbsp;

&nbsp;

&nbsp;

**Note:** Concepts have been derived from the book *Probabilistic Graphical Models: Principles and Techniques* by<span style="color:red"> **Daphne Koller** and **Nir Friedman**</span>. I am currently reading it. I love the way it makes you think about the concepts of probability.
