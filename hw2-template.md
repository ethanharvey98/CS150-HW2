---
title: "CS-150 Generative Models -- Homework 2"
geometry: margin=1.5cm
output: pdf_document
---
**Name**: Ethan Harvey

# 1. Instructions

This assignment has two writing questions and two coding questions. Question 3 and 4 are in the two jupyter notebooks in the same package. For all questions except Q1, you should check with an LLM first. You can use the content of an LLM in your answer, but \underline{1) you should fully understand the answers/solutions you have provided; and 2) you are solely reponsible for} \underline{your answers/solutions}.

* Deadline: 10pm, 10/20/2025
* Submission: please put all answers to a single pdf WITH THE QUESTION ORDER and submit it to GradeScope.  

Q1 (5 points). *Please discussion the relationship between the following two methods of fitting a model. Which method to you prefer to use in your understanding? Please give the reason.*   

* *assuming that there is a true distribution and minimizing the KL-divergence from the true distribution to the model distribution*
* *maximizing the log-likelihood of the data under the model*

**Answer:** \textcolor{white}{[If you write your answer with hand, you can adjust the space as needed by changing the value in vspace. If you type in/paste your answer here, PLEASE REMOVE this line and the vspace below]}

\vspace{2.5in}


Q2. (5 points). *Suppose we have a set of observations $(x_i: i = 1, \ldots, n)$, and each $x_i \in \mathbb{R}$. Please use a Gaussian distribution with a fixed variance $\sigma^2$ to fit the data with Maximum Likelihood Estimation (MLE).*    

**Answer:** 

The likelihood of the data under the Gaussian model is the product of of the individual densities $\prod_{i=1}^n \mathcal{N}(x_i \mid \mu, \sigma^2)$ which can be written as
```math
\begin{align*} 
L(\mu) = \prod_{i=1}^n \frac{1}{\sqrt{2 \pi \sigma^2}} \exp \left( -\frac{(x_i - \mu)^2}{2 \sigma^2} \right).
\end{align*}
```

It is often easier to work with the log-likelihood $\sum_{i=1}^n \log \mathcal{N}(x_i \mid \mu, \sigma^2)$ which simplifies to
```math
\begin{align*} 
\ell(\mu) = -\frac{n}{2} \log \sqrt{2 \pi \sigma^2} - \frac{1}{2 \sigma^2} \sum_{i=1}^n (x_i - \mu)^2.
\end{align*}
```

To find the maximum, we differentiate $\ell(\mu)$ with respect to $\mu$
```math
\frac{\partial \ell}{\partial \mu} = - \frac{1}{\sigma^2} \sum_{i=1}^n (x_i - \mu).
```

Setting $\frac{\partial \ell}{\partial \mu} = 0$ and solving for $\mu^*$, we get
```math
\mu^* = \frac{1}{n} \sum_{i=1}^n x_i.
```

The second derivative is $\frac{\partial^2 \ell}{\partial \mu^2} = -\frac{n}{\sigma^2} < 0$, so this critical point is a maximum.
