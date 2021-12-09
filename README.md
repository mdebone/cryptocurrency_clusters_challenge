# cryptocurrency_clusters_challenge

Downloaded csv of data, created readme, no assignment name given so called cryptocurrency_clusters_challenge. Cloaned to local, added wip.ipynb file.

Data Preperation

Read the crypto_data.csv into a dataframe no problem, and then began all of the preprocessing and cleaning. First Step was to remove all of the Cryptos that are not
being traded, so that was "IsTrading" false, and after those were removed and only the true remained removed the entire IsTrading column. Check. Remove all the rows
with null values, easily enough, used a for loop and a print statement that told which column names had null values. 

I am no in search of TotalCoinsMined, its the only one. Did a dropna(axis=0, how='any' and that got those gone, reran the nifty print statement just because
I was pleased with myself at having written it and it did, indeed, show that of the columns that remained there were no null values. Got stuck on the filter coins greater than zero,
for some reason I misread it and thought that it was refering to TotalCoinSupply and so did like 30 permutations to try to get the zeros out of there, nothing worked without killing 
the entire dataframe minus the column headers. Reread it, and realized that I was not looking for TotalCoinSupply but TotalCoinMined, and once that was sorted I had my five columns.

Dropping CoinName was easy enough, and I realized that the next steps were to convert the two text Algorithm and Prooftype to numeric but it said nothing about the unnamed: 0 column, which
I took to be more or less the stock-tickers of the different coins, thats not the right terminology but close enough and I could use it as an index and so set it as such.

Got hung up on df['Algorithm'] and df['ProofType']. did value_counts() of both and then tried to append each individually to the original df, but that didn't work as well, 
I think it was because I was trying to get rid of the Algorithm column in the same line, for whatever reason. Nor did the pd. X_dummies that we used in the class activity work, 
because it turned the numeric columns into multi columns, well really only the TotalCoinsMined since those are e to the 5th, 6th, 8th notation and it didn't recognize them as numeric.

Took a step back, just called X, pd.get_dummies(df, columns['both'] and that worked a whole lot better then attempting to do it indiviudally and it preserved the numeric/but scientific notation columns 
as actual numeric, so success! X_scaled and standardScaler worked with fit_transform(x).

Dimensionality Reduction
I thought with 100 columns turning it into 5 was a reasonable number of n_components, but it didn't like that and later in the instructions suggested 3. And no my fetch the explained variance a = pca.explained
is showing like 0.068 when its supposed to be .9 or .8, so clearly need to rewatch that bit and I thought that the K-means clustering was supposed to come before the T_SNE, but I guess I am miss remembering.
