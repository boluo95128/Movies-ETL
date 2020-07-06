# Movies-ETL
## Analysis Statement
### Assumptions in Movies Analysis
#### Wiki movies file must be in JSON format. If the Wiki file is not in a parseable JSON format there's no point in further operation and the program should exit.
#### Tables may or may not exist. If the tables exist we must clear them (without deleting the tables), if they don't exist we must create them when importing the data.
#### Both Wiki and Kaggle metadata must include the IMDB id for each movie, and these ids should match for the metadata merge to work.
#### Ratings should be keyed by the same id as Kaggle metadata (kaggle_id), otherwise the ratings wouldn't match the correct movie.
#### Amounts not prefixed with "$" are very small part of the data set. We only parse budget values that start with "$" sign and drop everything else. Supporting multiple different currencies would require significantly more complicated processing while the amount of such entries is very low compared to the total data set.
#### Budgets and box office values are denominated consistently. We're using the same regular expressions to parse the budget and the box office amounts assuming they will be using the same currency denomination. This is a reasonable assumption, since denominating those in different currencies would make it harder to compare and much more complicated to process.
#### Database location is local on port 5432, which is the default postgres port.
