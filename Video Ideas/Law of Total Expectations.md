![[spider_fly_problem.png]]





## Script
#### Intro
While going through the course material for a class at my university I stumbled upon this problem. I tried long and hard to solve this but it seemed like I always overcomplicated the train of thought.
A thing about solving such problems is to build a proper intuition through practice. This problem introduced me to the beautiful concept of Total expectation theorem.

Since you are watching this video, I expect that you have a basic idea of what probability theory is. Basic concepts like random variables and their expectations.
But to summarize once again.
- a random variable refers to the outcome of a random experiment.
- Now this experiment is sampled from the event space containing all possible events/scenarios. each scenario leads to an outcome.
- Now given a random variable X with a probability distribution , we can write the expectation of X: $$E(X) = \sum_{w \in F} x.p(x) \ $$
- In simple words, the expected value of X can be said to be the average value of X you will get given you conduct this random experiment a LARGE number of times.

### Total Expectation Theorem
It states that the expectation of random variable X is equal to the sum of the conditional expectations weighted by their respective probabilities.
While a formal proof is beyond the scope on this video, the intuitive way of thinking about it would be to think of a weighted average the same way we thought of the definition of the expectation.
Any outcome