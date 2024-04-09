
# Comscanner mini whitepaper

This is a mini whitepaper.

### [Requirements](#background)
The following requirements outline the criteria for identifying potential long and short trading opportunities in crypto futures contracts.

### [Long Opportunities](#background)
example 
- Price Range: The contract's price should fall within the range of $0.9 to $2.99 USDT.
- Volume Threshold: The trading volume must exceed 1 million USDT.
- Price Acceleration: A minimum price acceleration of 2% within a maximum time frame of 3 minutes. For instance, if the price starts at $1.00 at 8:00 PM, it should reach $1.02 by 8:03 PM.
- Buyer Volume Surge: The volume of buyers should exhibit a noticeable increase above the average within the 3-minute interval.

### [Short Opportunities](#background)
- Price Range: The contract's price should fall within the range of $0.9 to $2.99 USDT.
- Volume Threshold: The trading volume must exceed 1 million USDT.
- Price Decrease: A minimum price decrease of 2% within a maximum time frame of 3 minutes. For instance, if the price starts at $1.02 at 8:00 PM, it should decrease to $1.00 by 8:03 PM.
- Seller Volume Surge: The volume of sellers should exhibit a noticeable increase above the average within the 3-minute interval.

The scanner should meticulously filter and present only those contracts that fulfill all the specified criteria for long and short opportunities. Additionally, ensure that the system efficiently captures and processes real-time data to facilitate prompt decision-making for traders.


## [Trading Bot Development Specification](#background)
### [Requirements](#background)
The trading logic for both Long and Short positions follows a consistent approach, with distinct criteria for positive and negative market movements. The logic is detailed below:
#### Acceleration Threshold:
A Long position is initiated when a contract demonstrates a positive price acceleration of 2%.
#### Pullback Condition:
Following the 2% acceleration, a Pullback is expected to occur; however, the pullback should not exceed a decrease of 1%.
#### Position Entry Conditions:
The trading position is opened only when the subsequent candle, post-pullback, breaks upward beyond the opening price of the pullback candle.

#### Position Delay Mechanism:
If the trading position has not been opened, and the candle following the pullback registers a decrease beyond the 1% mark, the position is withheld. Even if prices subsequently rise and breach the opening price of the pullback candle, the position remains unopened.

### Closing the Long Position with Gain:
To efficiently close a Long position with a gain, the bot should incorporate user-defined parameters. These parameters empower users to specify the percentage of the position they wish to close and at what percentage increase in price. For instance, the system will offer users options to close 25%, 50%, 75%, or 100% of the position at predefined percentage increments.

### User-Defined Parameters:
Users can set parameters to close a portion of the position (e.g., 25%, 50%, 75%) when the price increases by a specified percentage from the open position price.
Example: Close 25% of the position when prices increase by 0.5% from the open position price, close 50% when prices increase by 1%, and so forth until 100% of the position is closed.
If the price fails to increase to the user-defined level and returns to the open position price, the bot should automatically close the entire position to prevent losses.

### Closing the Long Position with Losses:
In the event of an immediate price decrease from the opening price, resulting in a breach of the bottom of the pullback candle, the bot should promptly close the Long position at 100%.



