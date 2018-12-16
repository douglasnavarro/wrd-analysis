# Wrangle Report

This document describes the data wrangling procedure done to increase the qualiy of the data contained in the `twitter-archive-enchanced.csv` and `image_prediction.tsv` files as well as additional data gathered using the Twitter API and stored in the `tweet_json.txt` file. The IPython environment along with the Pandas library were the main tools used in the process.

## Comments on the gathering step

This step consisted of reading the `twitter-archive-enchanced.csv` and `image_prediction.tsv` files as well as gathering fresh data for tweets contained in these datasets.

Reading the .csv and .tsv files was straightforward using Pandas' `read_csv` method. However, using the Twitter API to produce an updated dataset using the ids from the `twitter-archive-enhanced` dataset required a bit of exception handling as some tweets were unavailable after being deleted or because of some other unkown reason.

## Comments on the assessment step

The assessment step was a bit overwhelming at first because the dataset had multiple issues. However, setting a mental goal of what insights I wanted to produce from the data helped me figure out what issues should be prioritized.

No external software was used besides the Jupyter Notebook for visual assessment. The Dataframe `.info()` method and `dtypes` attribute were the main programmatic ways of assessing the data.

## Comments on the cleaning step

As recommended the cleaning step was conducted by a sequence of **define**, **code** and **test** steps. Due to the relatively large number of issues, the **define** step was taken only once, listing all the definitions at once and then the **code** steps included a comment header that reminds the reader of what issue will be addressed by that code.

By the middle of the cleaning step I realized there was a limitation when converting long floats to strings, which were being converted with scientific notation (such as 8.3534e+10). Then I tried to make a conversion to integers **before** converting to string, but there was an overflow issue with those conversions until I found out I had to use the `int64` type from Numpy. But in the end everything worked out.

Another tough part was figuring out how to fix the "dog stage columns" issue. I tried to used the `melt` method but, in the end, manually splitting the dataframe and concatenating it back together was easier for me.

## Comments on the analysis and visualization step

The analysis and visualization step relied totally on bar charts to show to which dog breeds, names and stages the community reacts the most.