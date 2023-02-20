



# 1. Introduce the protocol, their product offering and make an evaluation of their company (Community and Financial metrics)

Introduction:
DODODex is a decentralized exchange (DEX) that uses a type of automated market maker (AMM) called Proactive AMM (pAMM) to facilitate trades.
Unlike traditional centralized exchanges that use an order book to match buyers and sellers, DEXs use AMMs to determine the price of assets and execute trades. AMMs use algorithms to set the price based on the ratio of assets in a liquidity pool.pAMMs take this a step further by using real-time market data to adjust the price more proactively. They dynamically change the pool weights based on market conditions to provide better pricing accuracy and liquidity. This helps prevent slippage and reduces the impact of large trades on the market.
Proactive Automated Market Makers (pAMMs) are a type of automated market maker (AMM) that uses real-time market data to adjust the pricing and liquidity of assets. pAMMs dynamically change the weights of assets in their liquidity pools based on market conditions, which provides more accurate pricing and reduces the impact of large trades on the market.
The use of pAMMs can provide more accurate pricing and reduce the impact of large trades on the market. This makes them a popular choice for decentralized exchanges (DEXs) that want to provide better liquidity and pricing for their users. 

In summary, DODODex uses pAMMs to provide a more efficient and accurate trading experience for its users. The DODO decentralized exchange is one example of a DEX that uses pAMMs to provide more efficient trading for its users.

Protocol: 
The DODO protocol uses pAMMs to optimize liquidity and reduce slippage. By proactively adjusting the weights of assets in the liquidity pools, DODO ensures that users can trade at prices that accurately reflect the current market conditions, even during periods of high volatility.
In addition, the DODO protocol uses a unique price discovery algorithm called "CrowdPooling" to set the initial price of assets in its liquidity pools. This algorithm combines the principles of an initial coin offering (ICO) with an AMM, allowing users to pool their funds together and determine the initial price of the asset.
The DODO protocol also features a number of other tools and features to enhance the trading experience for users, such as flash loans, limit orders, and stop-loss orders.

Overall, the DODO protocol's use of pAMMs and innovative price discovery algorithm make it a promising decentralized exchange for users looking for efficient and reliable trading on the blockchain.

Product offering:
DODO offers a range of features and tools to enhance the trading experience for users.
One of the main features of DODO is its liquidity provision mechanism, which is based on pAMMs.
DODO also offers a unique price discovery mechanism called "CrowdPooling", which combines the principles of an initial coin offering (ICO) with an AMM. This allows users to pool their funds together and determine the initial price of the asset.
In addition to its liquidity provision mechanism, DODO also offers a range of other features to enhance the trading experience for users. These include flash loans, which allow users to borrow funds without collateral for a very short period of time, limit orders, which allow users to set specific prices at which they want to buy or sell assets, and stop-loss orders, which allow users to limit their losses in case of adverse price movements.
Overall, DODO's product offering is designed to provide users with efficient, cost-effective, and reliable trading on the blockchain, with features and tools that cater to the needs of both retail and institutional traders.

Evaluation:

While the protocol is still in its early stages, there are several metrics that can be used to evaluate the company's community and financial performance.

Community Metrics:

DODO has an active and growing community of users and developers. The DODO protocol has been well received in the decentralized finance (DeFi) community, and the team has been actively engaging with users and developers to improve the protocol. Some of the community metrics for DODO include:

    Over 28,000 followers on Twitter
    Over 10,000 members on Telegram
    Over 1,000 followers on Medium

Financial Metrics:

DODO is a decentralized protocol, and therefore does not have traditional financial metrics like revenue or profit. However, there are several metrics that can be used to evaluate the company's financial performance, including:

    Market Cap: According to CoinGecko, as of February 2023, DODO's market capitalization is over $300 million USD.
    Trading Volume: According to DODO's own data, the platform's trading volume has been steadily increasing, with over $300 million USD in trading volume in the last 24 hours as of February 2023.
    Liquidity: DODO's liquidity provision mechanism is one of its main features, and as of February 2023, DODO's liquidity pools have a total value locked (TVL) of over $1 billion USD, according to DeFi Pulse.

Overall, DODO has shown strong community engagement and has established itself as a promising decentralized exchange protocol in the DeFi space. While it is still a relatively new protocol, DODO's financial metrics demonstrate its potential to compete with other leading DEXs in the industry.

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
