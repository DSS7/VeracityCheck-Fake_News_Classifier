LIAR Dataset - Fake News Classification
Description of the TSV format

Column 1: the ID of the statement ([ID].json).
Column 2: the label.
Column 3: the statement.
Column 4: the subject(s).
Column 5: the speaker.
Column 6: the speaker's job title.
Column 7: the state info.
Column 8: the party affiliation.
Column 9-13: the total credit history count, including the current statement.

9: barely-true counts.

10: false counts.

11: half-true counts.

12: mostly-true counts.

13: pants-on-fire counts.
Column 14: the context (venue / location of the speech or statement).

Dataset Overview

Class distribution for labels in the training set:

half-true 2114
false 1995
mostly-true 1962
true 1676
barely-true 1654
pants-fire 839

Length of datasets:
Train: 10240
Validation: 1284
Test: 1267

Preprocessing Steps Completed

Dropped unnecessary columns: id, context, and job_title.

Handled numerical features (barely_true, false, half_true, mostly_true, pants_fire) by dropping rows with missing values.

Encoded categorical features:

label mapped to numeric values (pants-fire → 0, false → 1, …, true → 5).

party one-hot encoded.

state cleaned for duplicates, typos, and invalid entries, then one-hot encoded.

subject vectorized using TF-IDF.

speaker converted to frequency counts.

Processed statement text: tokenized, lemmatized, and TF-IDF vectorized (max_features=5000).

Combined all features into a single sparse matrix per dataset: TF-IDF vectors of statements, TF-IDF vectors of subjects, numerical features, and one-hot encoded categorical features.

Final feature dimensions:
Train: (10238, 5258)
Validation: (1284, 5258)
Test: (1267, 5258)