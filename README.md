# ElasticSearch dictionary files for island.is project

## Release
Because of the way we handle versions of these dictionary files in the indexer/migration project we *must* keep an incremental single part versioning scheme.

Releases must then contain at least the .tar.gz file.

## Files

File names *MUST* satisfy this pattern [a-z0-9], i.e. no punctuation or whitespace and *MUST NOT* exceed 23 in length.
As this can cause issues in AWS ES when these files are added as a package and associated to the domain.

### stopwords.txt
List of words that should not be indexed (by default)

Format: one word per line, with all inflections.

Examples: https://github.com/apache/lucene-solr/tree/master/lucene/analysis/common/src/resources/org/apache/lucene/analysis/snowball

### keywords.txt
Words that should not be stemmed.

Format: one word per line


### synonyms.txt
Synonyms of words.

Format: We use the solr format. See https://www.elastic.co/guide/en/elasticsearch/reference/7.4/analysis-synonym-tokenfilter.html

Examples: https://github.com/alphagov/search-api/blob/master/config/schema/synonyms.yml


### stemmer.txt
A stemmer dictionary.

See https://www.elastic.co/guide/en/elasticsearch/reference/7.4/analysis-stemmer-override-tokenfilter.html

We generate icelandic stemmer.txt from the Augmented Format of the BÍN database (https://bin.arnastofnun.is/DMII/LTdata/k-format/ ).
More information about the generation itself later.


### hyphenpatterns.txt
A precomputed hyphenation pattern file.

Which uses XML-based hyphenation patterns to find potential subwords in compound words.

.txt is used in the filename due to limitation in AWS ES and package association, but this is file contains valid XML which
the analyzer will recognise regardless of the filename ending.

See https://www.elastic.co/guide/en/elasticsearch/reference/current/analysis-hyp-decomp-tokenfilter.html

More information about this functionality and source later.


### hyphenwhitelist.txt
A whitelist for tokens produced in hyphenation decompounder token filter.

See https://www.elastic.co/guide/en/elasticsearch/reference/current/analysis-hyp-decomp-tokenfilter.html

We generate icelandic hyphenwhitelist.txt from the Augmented Format of the BÍN database (https://bin.arnastofnun.is/DMII/LTdata/k-format/ ).
More information about the generation itself later.
