This is a simple demo of applying deep learning algo in financial market. It mainly shows how to use the transformer architecture to model the distribution of price in a short term future.<br>
<br>
# Data Introduction
The original data is from a public source, Esunny 9.5 or Eploestar9.5. The data columns are shown below. The instrument is a commodity named low-sulfur fuel oil.Its tag in SHFE(or INE) is LU. The data is intraday and ranged from 2024/11/22 to 2024/12/3.
<br>
# Feature Engineering
The feature engineering part may contain some sensitive information. The feature enginneering part is censored here. But I can give a breif introduction about the high frequency factors used. The factors can be mainly described as several types, factors of order book structures, factors of order flow analysis, factors of trend, factors of volatility and some trivIal factors as suppliment. The data after processing contains 289 columns. There are 287 features as our X and 2 target features as our Y.The target features are the mean and standard deviation of price distribution in a short time future.
<br>
# Model 
The architecture is showed in diagram.<br>
![image](https://github.com/user-attachments/assets/4f7e151a-8a27-45b0-8ddb-6b53bd32df26)

<br>
I utilize the simplest architecture to demonstrate the model's workflow. Even with this minimal architectural design, the model still achieves a not bad performance. I use the last positon of encoder output as the input of final distributional head. This is also the simplest way. The model performance would be inproved with other tricks. (like imbalance mapping the embeddings into the self attention part, due the natural sense that the fromer market information has less impact to present. Or use not the last position but a smart combination of last several positions as input to distributional head, etc..)

# Performance
![image](https://github.com/user-attachments/assets/01a7d1b0-d2a0-47b8-aa49-5d87f234ff1f)
<br>
The green line is the exact midprice at present. The blue line is the price mean in next short period.And the orange line is the model's prediction.<br>
<br>
The model makes the reliable predictions before the large midprice jumps with few mistakes. The attention mechanism and transformer architecture have indeed demonstrated strong modeling capabilities in short-term prediction for specific commodities. Of course, the factor construction in the feature engineering part is also an important reason why the model can deliver decent performance without complex modifications.

