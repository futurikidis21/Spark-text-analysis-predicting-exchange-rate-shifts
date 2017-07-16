# Predicting shifts in GBP-EUR exchange rates based on the content of UK parliamentary debates: A pySpark application
 
 
The pySpark code presented in this notebook aims to construct a modelling process, which tests if shifts in GBP-EUR exchange rates can be predicted on the basis of political speech. More specifically, the code implements a process that involves the following steps:

(a) It scrapes the (almost daily) reports that record debates at the House of Commons and the House of Lords, as published on the UK Government website. The reports (available in PDF format) are converted into txt files and common (usually uninformative) words, numeric figures, and punctuation symbols are removed. File names and the remainder text content are converted into a data-frame and the content is tokenised and hashed, before computing term frequencies (TFs) and inverse document frequencies (IDFs) for the hashes.

(b) It scrapes the (almost daily) EUR-GBP exchange rates, published on the Bank of England website. The content is written in a text file, which is then processed to remove blank space and to calculate the difference between each GBP-EUR exchange-rate value and its immediately previous exchange-rate value (i.e. the exchange-rate shift). Dates and exchange-rate shifts are then converted into a second data-frame.

(c) It links the data frames constructed at (a) and (b) together, so that the content of the debate reports at a certain date is appended to the shift in GBP-EUR exchange rates recorded the day after. This new data-frame serves as the analytical input on the basis of which the main analysis is conducted.

(d) Finally, it constructs a machine learning pipeline, whereby the linear regression models are trained, validated, and tested to predict exchange-rate shifts based on either the TF or the IDF of the (tokenised and hashed) content of the debate reports. Alternative parameterisation options are explored using a grid.

The processes of data collection embedded in (a) and (b) depend on the format at which relevant data are published on the UK Government and the Bank of England websites. For this study, we collect data from 01/06/2016 onwards, and the functionality of the code that collects the data was last confirmed on 23/04/2017. However, future functionality can be affected by future changes in the way that information is published. Along with this notebook, we provide the datafiles scraped on 23/04/2017, so that the analysis can be repeated when this code is used / assessed by others.

The findings of the analysis are highlighted throughout the annotation in this notebook. Overall (and perhaps unsurprisingly), the findings suggest that political speech at the House of Lords and the House of commons is unsuccessful in predicting complex and dynamic macroeconomic financial-market parameters, such as the GBP-EUR exchange-rate shifts.
Given the time-series nature of the data that this analysis considers, we have (partially) addressed the issue of autocorrelations when using linear regression analysis by focusing the analysis on the prediction of exchange-rate shifts (rather than the prediction of exchange rate values). We suggest that the analysis is revisited in the future using perhaps more appropriate analytical techniques, such as Autoregressive Integrated Moving Average time-series models.

See IPython Notebook: [Ipython Notebook](https://github.com/futurikidis21/Spark-text-analysis-predicting-exchange-rate-shifts/blob/master/INM432_Nalmpantis_Kyriakopoulos_Big_Data_Part_II.ipynb)
