



# 1. Introduce the protocol, their product offering and make an evaluation of their company (Community and Financial metrics)

# 2. Introduce the AMM mechanic (general explanation, and intuition, then deeper mathematical explanation)

# 3. Describe a few use cases where this AMM model is useful or optionally, if you have the expertise, some suitable trading strategies

In a pair $X-Y$, X is called trhe *base* token and Y the *quote* token. Let $B$ and $Q$ be the amounts of base and quote tokens in the pool, and $B_{0}$ and $Q_{O}$ be the amounts that had been initially deposited in the pool by the liquidity providers. The current amount of both token in the pool are different than the initial amounts that had been deposited by liquidity providers, as the number of each token chenges each time a trader uses the pool to execute a swap. $B_{0}$ and $Q_{0}$ are called the *regression targets$*, i.e. the amounts that the pool is trying to remain as close as possible to. 

The aim of a proactive market maket such as DODODex is to keep the actual number of tokens ($B$ and $Q$) as close as possible to the initial amounts ($B_{0}$ and $Q_{0}$), in order to avoid impermanent loss. To do so, it is necessary to incentivize arbitragers to make trades that push the number of tokens in the pool toward the initial amounts deposited. 

The price setting mechanism relies on both an oracle and a mathematical model, that pushes arbitragers to trade in the way we want them to trade. The marginal price proposed by the pool is as follows : 

$$P=iR$$

, where $i$ is a price provided by an oracle, and $R$ is a price that adapts to the pool situation i.e. wether there are less $Q$ or $B$ than initially, and adjusts the marginal price proposed by the pool in order to incentivize people to execute swap that will bring the amount closer to the initial amount deposited. Coefficient $R$ adapts the following way : 

If $B < B_{0}$, then : $$R=1-k+(\frac{B_{0}}{B})^{2}k$$
If $Q < Q_{0}$, then : $$R=1/(1-k+(\frac{Q_{0}}{Q})^{2}k)$$


# 4. Conclude with some thoughts on your experience of collaborating on Github (what works well, challenges, learnings)
