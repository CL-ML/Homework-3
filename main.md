



# 1. Introduce the protocol, their product offering and make an evaluation of their company (Community and Financial metrics)


textbf{The Protocol}: 

# 2. Proactive Market Marker mechanisms


Let $B$ and $Q$ be the amounts of base and quote tokens in the pool (in a pair X-Y, X is called the *base* token and Y the *quote* token), and $B_{0}$ and $Q_{O}$ be the amounts that had been initially deposited in the pool by the liquidity providers. The current amount of both token in the pool are different than the initial amounts that had been deposited by liquidity providers, as the number of each token chenges each time a trader uses the pool to execute a swap. $B_{0}$ and $Q_{0}$ are called the *regression targets$*, i.e. the amounts that the pool is trying to remain as close as possible to. 

The aim of a proactive market maket such as DODODex is to keep the actual number of tokens ($B$ and $Q$) as close as possible to the initial amounts ($B_{0}$ and $Q_{0}$), in order to avoid impermanent loss. To do so, it is necessary to incentivize arbitragers to make trades that push the number of tokens in the pool toward the initial amounts deposited. 

The price setting mechanism relies on both an oracle and a mathematical model, that pushes arbitragers to trade in the way we want them to trade. The marginal price proposed by the pool is as follows : 

$$P=iR$$

, where $i$ is a price provided by an oracle, and $R$ is a price that adapts to the pool situation i.e. wether there are less $Q$ or $B$ than initially, and adjusts the marginal price proposed by the pool in order to incentivize people to execute swap that will bring the amount closer to the initial amount deposited. Coefficient $R$ adapts the following way : 

If $B < B_{0}$, then : $$R=1-k+(\frac{B_{0}}{B})^{2}k$$
If $Q < Q_{0}$, then : $$R=1/(1-k+(\frac{Q_{0}}{Q})^{2}k)$$

As we see in those equations, the more actual quantity $B$ is becoming smaller than the initial quantity $B_{0}$, the more $R$ is becoing higher than 1, and the more the marginal price $P$ is becoming higher than the external price $i$, incentivizing arbitragers to sell $B$ for $Q$, and bringing quantity $B$ closer to its initial amount. On the other hand, the mode $Q$ is decreasing, and becoming smaller than $Q_{0}$, the more $R$ is becoming less than 1, and then $P$ is becoming lower than the external market. This way the arbitragers buy $B$ for $Q$, and $Q$ grows to come back closer to $Q_{0}$. 

Finally, note that the term $k \in [0,1]$, that is adjustable, controls the impact of trades on the price. The closer to 0 $k$ is, the more *liquid* is the pool, meaning that big trades have small impact on the price, which makes such a pool more attractive for traders (i.e. less slippage). We should note that an extreme case of $k$ equal to O means no slippage at all (but also no mechanism to avoid impermanent loss), and a $k$ equal to $1$ means the exact same slippage than a classical AMM. 


# 3. Describe a few use cases where this AMM model is useful or optionally, if you have the expertise, some suitable trading strategies

# 4. Conclude with some thoughts on your experience of collaborating on Github (what works well, challenges, learnings)

Big advantages compared to AMM : 
- Less slippage i.e. better liquidity, as $k$ is small (a pool with $k=1$ has exactly the same slippage than an AMM)
- No impermanent lost 
- Possibility to deposit only one type of token

But : 
- Price setting mechanism relies on an oracle, which introduces another risk, which is an attack (or simply a bug) in the oracle price setting, whcih can lead to huge losses of liquidity providers. 
