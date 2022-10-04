# Ethereum-Price-Prediction-
Time series forecasting by using the Prophet library

# Prophet Library
The Prophet library developed by Facebook is a popular library that is used specifically for forecasting time series data.
I used Prophet to make a simple forecast.

# Getting the data

I used the yfinance library to get the data on Ethereum prices. 
The yfinance library is a Yahoo! Finance market data downloader.
I used today function from datetime library to make sure the date of today will be updated automaticlly.


I set the start date as 2017-01-01, below is the first five rows of data I just got: 

<img width="508" alt="Screen Shot 2022-10-04 at 4 06 13 AM" src="https://user-images.githubusercontent.com/109259282/193767429-063482a2-4467-408b-8c82-6bcff713fc57.png">

The columns of data are date, open, high, low, close, adjusted close price, and volume.

I used the open price as price value of Ethereum coin. 

# Data cleaning

Firstly, I need to deal with null values.
I used info() to get the summary of the data and find the number of null values of the data.

<img width="496" alt="Screen Shot 2022-10-04 at 4 14 59 AM" src="https://user-images.githubusercontent.com/109259282/193769133-044735ea-54d3-44c9-8fb2-f1cc559a9fb7.png">

<img width="149" alt="Screen Shot 2022-10-04 at 4 16 47 AM" src="https://user-images.githubusercontent.com/109259282/193769466-edb4ec81-d695-4a81-8bbb-fea134907250.png">

Fortunately, I think there is no need to clean the data.

To successful use Prophet, I need to set date as a column of the data. 

<img width="682" alt="Screen Shot 2022-10-04 at 4 20 26 AM" src="https://user-images.githubusercontent.com/109259282/193770279-2f9d003f-8cad-4438-9523-a8e5e06bd5e7.png">

I found the date was not indexed in the data. So I need to reset the index.

<img width="762" alt="Screen Shot 2022-10-04 at 4 21 54 AM" src="https://user-images.githubusercontent.com/109259282/193770553-c6795df9-1c79-40ab-8b78-7cd71cecefda.png">

# Visualization of the price column

The prophet library requires only two columns in the data frame — “ds” and “y”, which is the date and open columns respectively.
Therefore, I reorganized the data and got:

<img width="387" alt="Screen Shot 2022-10-04 at 4 24 26 AM" src="https://user-images.githubusercontent.com/109259282/193771117-4d1406d6-0ec5-4e30-8273-1ee32a8ddd00.png">

I used plotly library to visualiza the data which can provided a quick interactivit:

<img width="928" alt="Screen Shot 2022-10-04 at 4 32 40 AM" src="https://user-images.githubusercontent.com/109259282/193772833-35355aa9-20c5-41eb-be0d-cedb89416df6.png">

The prices illustrate an upward trend with increasing vintage and more dramatic price fluctuations. Serveral spicks that might be influential on the prophet model.

# Setting the Prophet model

Because of how cryptocurrency prices fluctuate on an annual basis, which also means that the seasonal component varies with the trend, I can assume that it is a multiplicative time series. In the code I set the seasonality pattern to "multiplicative".

<img width="861" alt="Screen Shot 2022-10-04 at 4 49 35 AM" src="https://user-images.githubusercontent.com/109259282/193776570-bc4572ff-2508-407b-93ba-283ff1f56832.png">

Then, I create an entire years worth of date data for the prophet model to make predictions

<img width="471" alt="Screen Shot 2022-10-04 at 4 50 45 AM" src="https://user-images.githubusercontent.com/109259282/193776831-e22c9861-b76b-4ef2-8fb8-3402956d66de.png">

# Model predictions

I used predict function to get predictions: 

<img width="519" alt="Screen Shot 2022-10-04 at 4 52 25 AM" src="https://user-images.githubusercontent.com/109259282/193777176-325feb27-c367-4d0a-af09-9880300ff0a9.png">

% Forcast Polts

<img width="925" alt="Screen Shot 2022-10-04 at 4 56 42 AM" src="https://user-images.githubusercontent.com/109259282/193778154-bd32b248-8492-41c0-a10a-cd1feeda55b8.png">

The forecasting model also includes growth curve trend, weekly seasonal, and yearly seasonal components which can be visualized as below:

<img width="905" alt="Screen Shot 2022-10-04 at 4 57 52 AM" src="https://user-images.githubusercontent.com/109259282/193778415-efdd3ae4-247c-4f2b-acae-85b43f06239d.png">

The model shows:

1. There will be an downward trend for the price of Ethereum.
2. The price of ETH is lowest around November on a Thursday.
3. ETH is most expensive around October on a Thursday.










