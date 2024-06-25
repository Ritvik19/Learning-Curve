# Feature Engineering 101

[Source](https://twitter.com/marktenenholtz/status/1605911055170822145)

Feature engineering is the most important part of building great models for tabular data.

Note that the most important thing is to always start with what makes sense from your EDA and error analysis.

Also, make sure to cross-validate anything you try here to see if it actually helps!

### Let’s get started with NaN handling:

**Option #1:** Fill them with a value that makes sense

If "NaN sales" means there was simply an absence of transactions, then filling with zero makes perfect sense.

**Option #2:** Let your model handle it!

Many popular gradient-boosting libraries like XGBoost or LightGBM can handle NaN’s, so you can try that too.

This often provides the best performance.

**Option #3:** Fall back to a default method

For continuous features:

- Filling with the mean
- Filling with the median
- Filling with zero

For categorical features:

- Filling with the mode
- Filling with a negative value (for tree models)
- Frequency encoding

Once you’ve imputed, consider adding a corresponding binary column that indicates whether the other column was missing in that row.

### Now let’s talk transforming values:

**For categorical data:**

- Using a GBDT/RF? Try label encoding.
- Linear model/SVM/similar model? Try dummy encoding.
- Using a neural net? Try label encoding and using embedding layers.

**For continuous data:**

- If you’re using a tree-based model, you probably don’t need to do anything unless you're linear boosting.
- Otherwise, try standardizing or normalizing.
- If a variable has a weird distribution, try a log or sqrt transformation, or even something like Box-Cox.

### Now let’s talk about creating features.

This is a bit less structured, and a lot more about having a large arsenal of ideas and deploying them as necessary.

- If you have a date column, extract all of the useful components, like day of week, week of year, hour of day, etc.
- Similarly, addresses can be decomposed into state, city, latitude, longitude, etc.
- If your data has a time-series aspect, try creating rolling window calculations (usually mean and standard deviation are sufficient) as well as lag features.
- Try splitting categorical data into multiple fields, or combining multiple categorical fields into one.
- Create interaction terms between columns, such as subtracting or multiplying them. Tree-based models have a hard time picking up on these sorts of interactions.
- Have group fields like product hierarchy data, dates, cities, etc.? Try creating aggregations on those groups (mean, median, stddev, etc.) This is often where most of your opportunities lie. You can slice-and-dice grouped data in many ways.
- Try running clustering like k-means on your data and adding each row’s cluster label as a feature.
- Try running PCA on your data and either building a model on those features or adding the PCA features to your original dataset. (or any other dimensionality-reduction technique)
- Stacking is certainly a form of feature engineering! You can add predictions from a baseline model (like linear regression).
- A common technique in RecSys is adding similarity features even from a neural network-type model like Word2Vec.
