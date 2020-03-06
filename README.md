# Global Company Sales breakdown
## Introduction

This is a repository for Global Company Sales breakdown work flow. This project goal is to retrieve all the constituents of any global stock market and returns the sales breakdown for each company and region.

## What is constituents?

Based on [Investopeida web site](https://www.investopedia.com/terms/c/constituent.asp), a constituent is a company with shares that are part of an index like the S&P 500 or Dow Jones Industrial Average. It is a component or a member of the index. The aggregate of the shares of all constituents are used to calculate the value of the index.

Each constituent has to meet certain requirements pertaining to capitalization, market exposure, and liquidity before being added to an index.

## API
Using [Eikon Data API](https://developers.refinitiv.com/eikon-apis/eikon-data-api).
์
Note: This is not a full coding project repository yet.

## Research

### DataStream fields
This model uses Worldscope Geographic Segment data for sales to display the key countries and regions for the constituents of an index. The template then aggregates the data so users can see the breakdown for the index itself.

Core Worldscope Items used in the model are:
- Geographic Segment 1 Sales: ```WC19601```
- Geographic Segment 2: ```WC19611```
- Geographic Segment 3: ```WC19621```
- Geographic Segment 4: ```WC19631```
- Geographic Segment 5: ```WC19641```
- Geographic Segment 6: ```WC19651```
- Geographic Segment 7: ```WC19661```
- Geographic Segment 8: ```WC19671```
- Geographic Segment 9: ```WC19681```
- Geographic Segment 10: ```WC19691```

### Anwser from DataStream

This is probably a data setting, as there isn�t any Worldscope data available for this company as of today, if you run the request with a historical date � im sure you will get data back on those items.  Alternativly use the pad function to pull the last values forward.

Yes that is correct latest value for 926288 is for 2018 year end.

### Anwer from Eikon Data API

The fields providing geographic breakdown of the company�s fundamentals are listed in DIB under Content Classification -> Reuters Fundamentals -> Business and Geographic Segments - Geographic Segment.
Here�s an example:
ek.get_data('AAPL.O', ['TR.BGS.GeoTotalRevenue.segmentName', 'TR.BGS.GeoTotalRevenue'])

As for retrieving the list of stock RICs for a company, you could try using get_symbology method with ISIN as input and bestMatch parameter set to False, but the result is not going to fully match what you see in Eikon application. I cannot think of any way to use EDAPI to get the list of RICs for a company stock that would be as good as what you see in Eikon application.

## Development Status

- Datastream DSWS: Get data now but cannot find any detail regarding the **Geographic Segment** fields meaning. Need to check with Datastream team.
- Some RICs (STAN.L example) does not have TR.BGS.GeoTotalRevenue or TR.BGS.GeoTotalRevenue.segmentName values. Do not know why. Need to further check.
- It seems that I need to subscribe each Geographic Segment Desciption to verify each region information




