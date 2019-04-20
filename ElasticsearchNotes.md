# Elasticsearch Notes

## Scoring

Elasticsearch first reduces the candidate documents down by applying a boolean test. The Boolean model simply applies the AND, OR, and NOT conditions expressed in the query to find all the documents that match.

Elasticsearch runs Lucene under the hood so by default it uses Lucene's Practical Scoring Function. This is a similarity model based on Term Frequency (tf), Inverse Document Frequency (idf), and also uses the Vector Space Model (vsm) for multi-term queries.

Note that term frequency, inverse document frequency, and field-length normalization are stored for each document at index time. These are used to determine the weight of a term in a document

score(query q, document d) = queryNorm(q) * coord(q,d) * SUM (tf(t in d), idf(t)^2, t.getBoost(), norm(t,d)) for each (term t in q)

 1. queryNorm(q) is the query normalization factor
  - queryNorm = 1 / sqrt(sumOfSquaredWeights)
  - The sumOfSquaredWeights is calculated by adding together the IDF of each term in the query, squared.
  - Used so that different queries can be compared. For any individual query, however, it uses the same score for every document, therfore doesn't have an overall impact on a specific result

 2. coord(q,d) is the coordination factor
  - Counts the number of terms from the query that appear in the document.

 3. The sum of the weights for each term t in the query q for document d.
  a. tf(t in d) is the term frequency for term t in document d.
    - tf = sqrt(termfreq)
    - calculated at indexing time, you can configure the field to ignore term frequency during indexing
    - not-analyzed fields (typically those where you expect an exact match) will automatically have term frequency turned off.

  b. idf(t) is the inverse document frequency for term t.
    - idf = 1 + log(maxDocs/(docFreq + 1))

  c. t.getBoost() is the boost that has been applied to the query.
    - query boosting indicates that some parts of the query are more important than other parts

  d. norm(t,d) is the field-length norm, combined with the index-time field-level boost, if any.
    - norm = 1/sqrt(numFieldTerms)
    - a term match found in a field with a low number of total terms is going to be more important than a match found in a field with a large number of terms
    - you can choose to not implement field length norms in a document
    - not-analyzed fields will have field length normalization disabled by default

# Indexes and Settings
  - content 'quality'
  - analyzers
    - char filter
    - tokenizer
    - filters
      - synonyms
      - stop words
      - stemming
  - mappings
    - fields

# Features to consider for relevancy tuning
The following table lists GSA features to consider for relevancy tuning.

## Feature Comment

1. Source biasing - By using pattern matching, bias one source over another.

2. Date biasing, metadata biasing - Bias documents, which have specific metadata attached.

3. KeyMatches - Use KeyMatches to promote documents for certain queries.

4. Query expansion - Use a query expansion policy to expand search queries terms into other terms (synonyms).

5. Self-Learning scorer - When Advanced Search Reporting is enabled, the GSA uses the self-learning Scorer feature to analyze click stream data and promote certain search results over time. As an example, for a given search query, if users consistently click the second result on the page instead of the first, that result will eventually move up to overtake the first position on the page.

6. Host crowding/filtering - GSA filters out any combination of:
  - Results from the same path
  - Results with duplicate titles and snippets

7. Ranking framework - Specify a per-URL biasing.Note that this is a very complex solution to manage and should only be tried as a last resort.

8. Stopwords (introduced in GSA 6.10) - Use stopwords to prevent certain terms in the query from being used in performing search. Take care when using this feature as this can have wide ranging implications if used as a solution to a particular problem.

9. Collections - Break content into different collections to restrict the document corpus available to a search query.

10. Exposing metadata and/or Entities in Dynamic Navigation for a richer user experience - Instead of tuning GSA relevance, consider enriching the user experience by adding additional dynamic navigation categories for metadata sources or Entities that were defined in Entity Recognition. Although not really a relevancy tuning option, Dynamic Navigation may have the benefit of enriching user experience so that a user can drill down into the results set to find the results they are looking for.
