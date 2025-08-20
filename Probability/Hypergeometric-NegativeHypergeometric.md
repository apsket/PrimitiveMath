# Hypergeometric and Negative Hypergeometric Distributions

**The Hypergeometric Distribution**

The hypergeometric distribution's story consists of fixing a number $n$ as size of subset to observe out of a universe of $N$ binary elements, and then count how many of the selected elements are succeses.

Let $N$ objects be classified as either success or failure, with the number of succeses being $K$ and the number of failures being $W$. Draw $n$ objects out at random without replacement. Let $X$ be the number of succeses in the sample. The probability of observing $X = k$ succeses in the drawn sample is:

```math
P(X = k) = \frac{{K \choose k}{N - K \choose n - k}}{N \choose n}
```

It's possible to arrive at the expression by a sequential procedure where the probability of each draw is considered and then scaled according to multipicity of the obtained sequence. However, a more direct approach is to not reference the sampling procedure, but to count the ways of constructing the desired sample and then scale against all possible samples of the specified size.

There are exactly $K \choose k$ ways to select $k$ successes out of a total of $K$. There are $N - K \choose n - k$ ways to select the remaining $n - k$ failures out of a total of $N - K$ available. Since these selections are independent, there are a total of ${K \choose k}{N - K \choose n - k}$ selections with the required successes and the required failures. To get the probability of this observation, one must divide by the total number of samples of size $n$ out of $N$ available objects, i.e. $N \choose n$. Introducing $w$ and $W$ to denote the sampled and total number of failures, respectively:

```math
P(X = k) = \frac{{K \choose k}{W \choose w}}{N \choose n}
```

One could argue that there is only $1$ way of selecting $k$ successes out of $K$ _indistinguishable_ elements. Similarly, there would be $1$ way of selecting $n-k$ failures out of $N-K$ _indistinguishable_ elements available. One can overcome this by considering all elements as distinguishable, but only care about their _success/failure_ property when studying the final sample. Alternatively, one could keep considering the elements as indistinguishable but consider $K \choose k$ and $N - K \choose n - k$ as a measure of the likelihood.

To show that the same distribution is obtained by sequential events:

```math
P(X=k) = \frac{K}{N} \cdot \frac{K-1}{N-1} \cdot\cdot\cdot \frac{K-(k-2)}{N-(k-2)} \cdot \frac{K-(k-1)}{N-(k-1)} \cdot \frac{W}{N-(k-1)-1} \cdot \frac{W-1}{N-(k-1)-2} \cdot\cdot\cdot \frac{W-(w-1)}{N-(k-1)-1-(w-1)} \cdot {n \choose k}
```

For the denominator, observe that the product is a partial factorial of $N$, the smallest factor being $N-(k-1)-1-(w-1) = N - (k+w-1) = N - (n-1)$. Extend the denominator to the full factorial and correct with the corresponding denominator, resulting in:

$$N\cdot (N-1) \cdot\cdot\cdot (N-(n-1)) \cdot \frac{(N-n)!}{(N-n)!} = \frac{N!}{(N-n)!}$$

Something similar can be done to the numerator:

$$K\cdot (K-1) \cdot (K-2) \cdot\cdot (K-(k-2)) \cdot (K-(k-1)) = \frac{K!}{(K-k)!}$$

and

$$W\cdot (W-1) \cdot (W-2) \cdot\cdot (W-(w-2)) \cdot (W-(w-1)) = \frac{W!}{(W-w)!}$$

then the probability can be expressed as:

```math
P(X=k) = \frac{\frac{K!}{(K-k)!} \cdot \frac{W!}{(W-w)!}}{\frac{N!}{(N-n)!}} \cdot {n \choose k} = \frac{\frac{K!}{(K-k)!} \cdot \frac{W!}{(W-w)!}}{\frac{N!}{(N-n)!}} \cdot \frac{n!}{k!(n-k)!}
```

Re-ordering factors and noting $n-k = w$:
```math
P(X=k) = \frac{\frac{K!}{k!(K-k)!} \cdot \frac{W!}{w!(W-w)!}}{\frac{N!}{n!(N-n)!}} = \frac{{K \choose k} \cdot {W \choose w}}{N \choose n}
```

**The Negative Hypergeometric Distribution**

In contrast with the hypergeometric distribution's story, the negative hypergeometric describes a scenario where the universe of $N$ binary elements is unchanged, but the sample is selected in such a way that the number of elements is not static. Subsets of any size are considered so long as they include a fixed number $w$ of failures.

Let $N$ objects be classified as either success or failure, with $K$ and $W$ being the total counts of successes and failures, respectively. Objects are drawn out at random without replacement until $w$ failures are observed. Let $X$ be the number of succeses in the sample. The probability of observing $k$ succeses in the drawn sample is:

```math
P(X = k) = \frac{{k+w-1 \choose k}{N-w-k \choose K-k}}{N \choose K}
```

The classical way of obtaining the distribution is through direct application of the hypergeometric distribution by requiring the first $(k+w-1)$ draws to include exactly $k$ successes. Then, one multiplies this probability by the probability that the last selection is a failure.

```math
P(X = k) = \frac{{K \choose k}{N-K \choose w-1}}{N \choose k+w-1} \cdot \frac{N-K-(w+1)}{N-(k-w-1)}
```

where the rightmost probability comes from having $N-K-(w+1)$ available failure elements out of a total $N-(k-w-1)$ remaining. After doing some algebra, one can arrive at the standard form of the distribution.

There is, however, another way to construct the distribution that results in the standard form of the pmf without the need for algebra.

Consider the $N$ elements as distinct but initially not tagged with _success/failure_. Now split them into the observed sample (of cardinality $k+w$) and the remaining elements. As the elements are untagged this process does not contribute to the probability. Now tag $k$ elements in the observed sample as _success_. This can be done in ${k+w-1} \choose k$ ways. The $1$ is deducted from the available elements because one of the elements in the observed sample is identified from the rest as being the last failure. The remaining ${w-1}$ elements are tagged as _failure_, and this can only be done in one way. From the un-observed set of $(N-(k+w))$ remaining, tag $K-k$ of them as _success_, and the remaining as _failure_. This is done to have $K$ elements in total tagged as _success_. The total number of ways to have created a successful sample is then ${{k+w-1} \choose k} \cdot {N-k-w \choose K-k}$. Now, the total number of ways the objects could have been tagged is $N \choose K$, which is a tagging prior to splitting the universe into observed and un-observed sample. The probability is then given by the division:

```math
P(X = k) = \frac{{k+w-1 \choose k}{N-w-k \choose K-k}}{N \choose K}
```
