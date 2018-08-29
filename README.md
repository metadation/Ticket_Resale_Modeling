## Ticket Resale Market Modeling

The purpose of this project is to create a predictive model of the ticket arbitrage market to forecast Stubhub listing prices, and determine which events are projected to resell higher than current market or wholesale price.

In other words, our goal is to provide a tool that can help ticket resellers make investment decisions in the ticket resale market, and effectively weigh risk and reward.


### Methodology

**Data** 

We compiled data from Ticketmaster and Stubhub on event characteristics and price/ticket quantity fluctuations over time. 2 primary training metrics were engineered to represent risk and reward:

1. Return - *(mean resale price - wholesale price) / wholesale price*

This is the difference between the original purchase price for that event (wholesale price) vs. the mean of all current listing prices, representing opportunity. 

2. Risk - *(today's ticket count - tomorrow's ticket count) / today’s ticket count*

This is the difference between the amount of listed tickets today vs. the amount of tickets listed tomorrow, representing likelihood of ticket sale.

**Model**

The metrics are used to train a 2 layer ensemble model:

1. Layer 1 is a Gradient Boosting Classifier which relied on many of the static event features such as genre, location and artist to determine whether an event had the potential to peak above a certain risk/return threshold;

2. Layer 2 is a set of weighted ARIMA models forecasting the exact values of the risk/return metris for Layer 1's events of interest

You can review the notebook, presentation deck and presentation notes provided in this repository for more details or reach out with questions


## Contents

*stubhub_api.ipynb* - notebook containing code and notes on data pulls from Stubhub

*ticketmaster_api.ipynb* - notebook containing code and notes on data pulls from Ticketmaster

*ticket_market_model.ipynb* - notebook containing code and notes on model development and training

*ticket_market_data.db* - original DB used to build and train model

*Ticket_Market_Model.pdf* - presentation on intial draft

*presentation_notes.pdf* - presentation notes


## Development Pipeline

\** Develop scalable .py modules for replicability

\** Automate and scale data pulls in AWS

\** Automate and productize ARIMA model forecasts

\** Engineer Twitter stream sentiment analysis feature
