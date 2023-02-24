


# 1.Introduction:
DODODex is a decentralized exchange (DEX) that uses a type of automated market maker (AMM) called Proactive AMM (pAMM). Unlike traditional centralized exchanges that use an order book to match buyers and sellers, DEXs use AMMs to determine the price of assets and execute trades. AMMs use algorithms to set the price based on the ratio of assets in a liquidity pool. pAMMs take this a step further by using real-time market data to adjust the price more proactively. They dynamically change the pool weights based on market conditions to provide better pricing accuracy and liquidity. The use of pAMMs can provide more accurate pricing and reduce the impact of large trades on the market. 

# 2.Product offering:
DODO offers a range of features and tools to enhance the trading experience for users.
One of the main features of DODO is its liquidity provision mechanism, which is based on pAMMs.
In addition to its liquidity provision mechanism, DODO also offers a range of other features to enhance the trading experience for users. These include flash loans, which allow users to borrow funds without collateral for a very short period of time, limit orders, which allow users to set specific prices at which they want to buy or sell assets, and stop-loss orders, which allow users to limit their losses in case of adverse price movements.

# 3.Evaluation:

While the protocol is still in its early stages, there are several metrics that can be used to evaluate the company's community and financial performance.

###### Community Metrics:

DODO has an active and growing community of users and developers. The DODO protocol has been well received in the decentralized finance (DeFi) community, and the team has been actively engaging with users and developers to improve the protocol. Some of the community metrics for DODO include:

   + Over 28,000 followers on Twitter
   + Over 10,000 members on Telegram
   + Over 1,000 followers on Medium

###### Financial Metrics:

There are several metrics that can be used to evaluate the company's financial performance, including（February 2023）:

   + Market Cap: DODO's market capitalization is over $300 million USD.
   + Trading Volume: the platform's trading volume is over $300 million USD.
   + Liquidity: DODO's liquidity provision mechanism is one of its main features, DODO's liquidity pools have a total value locked (TVL) of over $1 billion USD.

DODO has shown strong community engagement and has established itself as a promising decentralized exchange protocol in the DeFi space. While it is still a relatively new protocol, DODO's financial metrics demonstrate its potential to compete with other leading DEXs in the industry.

# 4. Proactive Market Marker mechanisms

Let $B$ and $Q$ be the amounts of base and quote tokens in the pool (in a pair X-Y, X is called the *base* token and Y the *quote* token), and $B_{0}$ and $Q_{O}$ be the amounts that had been initially deposited in the pool by the liquidity providers. $B_{0}$ and $Q_{0}$ are called the *regression targets$*, i.e. the amounts that the pool is trying to remain as close as possible to. 

The aim of a proactive market maket such as DODODex is to keep the actual number of tokens ($B$ and $Q$) as close as possible to the initial amounts ($B_{0}$ and $Q_{0}$), in order to avoid impermanent loss. To do so, it is necessary to incentivize arbitragers to make trades that push the number of tokens in the pool toward the initial amounts deposited. 

The price setting mechanism relies on both an oracle and a mathematical model, that pushes arbitragers to trade in the way we want them to trade. The marginal price proposed by the pool is as follows : 

$$P=iR$$

, where $i$ is a price provided by an oracle, and $R$ is a price that adapts to the pool situation i.e. wether there are less $Q$ or $B$ than initially, and adjusts the marginal price proposed by the pool in order to incentivize people to execute swap in the desired way. Coefficient $R$ adapts the following way : 

If $B < B_{0}$, then : $$R=1-k+(\frac{B_{0}}{B})^{2}k$$
If $Q < Q_{0}$, then : $$R=1/(1-k+(\frac{Q_{0}}{Q})^{2}k)$$

As we see in those equations, the more actual quantity $B$ is becoming smaller than the initial quantity $B_{0}$, the more $R$ is becoming higher than 1, and the more the marginal price $P$ is becoming higher than the external price $i$, incentivizing arbitragers to sell $B$ for $Q$, and bringing quantity $B$ closer to its initial amount. On the other hand, the more $Q$ is decreasing, and becoming smaller than $Q_{0}$, the more $R$ is becoming less than 1, and then $P$ is becoming lower than the external market. This way the arbitragers buy $B$ for $Q$, and $Q$ grows to come back closer to $Q_{0}$. 

Finally, note that the term $k \in [0,1]$, that is adjustable, controls the impact of trades on the price. The closer to 0 $k$ is, the more *liquid* is the pool, meaning that big trades have small impact on the price, which makes the pool more attractive for traders (i.e. less slippage). We should note that an extreme case of $k$ equal to O means no slippage at all (but also no mechanism to avoid impermanent loss), and a $k$ equal to $1$ means the exact same slippage than a classical AMM. 


# 5. Use cases 

The primary use case of such a model is a classical pAMM, with $k < 1$, that enables the price to adapt dynamically to trades, while proposing lower slippage than classical constant product AMM, and also limit impermanent loss for liquidity providers. 

On the other hand, the way pAMM work enable to create pools with any number of tokens of both base and quote, so that this can be used by new projects to build what is called a vending machine, which means a pool with 100% token from the project, that enables projects to raise fund very easily. 

Furthermore, this model enables to build very customisable liquidity pools, and then gives to market makers the ability to create their own pool, and to adjust parameter $k$ according to their market making strategy, modifying very easily the level of liquidity (i.e. slippage) they propose to traders. 

Finally, this model can recreate more classical pools, such as constant product classical AMM (with $k=1$) or curve-like stablecoins pools (with k very close to 0). 


# 6. Conclusion

To conclude, DODODex, and pAMM in general enable to create fully customizable liquidity pool, that can be tuned to create elaborates pools that solve (partially) both the problems of slippage for traders, and impermanent loss for liquidity providers. Moreover, the flexible design of pAMM also enables anyone to deposit any amount of each token, enabling people having only one type of token to stake them, whereas classical AMM requires deposit of both types of token in some proportions. 

This type of market maker seems to be more efficient than classical AMM in most situations, however we should not forget that it implies an oracle, which is a new attack vector, and introduces a new type of risk for liquidity providers. 


