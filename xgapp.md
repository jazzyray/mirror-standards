# Platts CCP Pipeline
The purpose of this document is to provide a high-level overview of this pipeline: what it is and how it works. It is aimed at users who wish to have a glimpse at the text-processing technology behind NOW and TAG without going into too many technical details.

## About
This is a [GATE](https://gate.ac.uk/overview.html) text-processing pipeline. GATE is a platform for developing text-processing components and combining them together into so-called pipelines. GATE distinguishes between two types of resources:
* language resources: documents and corpora
* processing resources: text-processing components and pipelines

A document in GATE terms is any text and the structured metadata associated with it, expressed as features and annotations. A feature is simply a key-value pair. An annotation is a portion of the text, expressed by a start and an end position, and any features associated with it. A corpus is simply a collection of documents.

Each text-processing component takes a document as input, performs some text analysis, thereby changing the features and annotations of the document, and returns the changed document. A pipeline is a *sequence of components* which are executed one after another in a specific order, so that the output of each component becomes the input to the next component. Thus, each component in a pipeline *may depend* on any previous components.

## Main components
Although different pipelines may use different components, depending on their exact purpose (e.g. what they extract, what types of documents they process, what language the documents are in), all pipelines that perform named-entity extraction, such as this one, follow the same generic structure. The purpose of this section is to describe this generic structure, thereby giving you a high-level overview of how this particular pipeline works, too.

### Preprocessing
Every text-processing pipeline starts with some preprocessing components. The term "preprocessing" typically refers to all the menial text-processing tasks which must be accomplished before any real "processing" can take place. These may include:
* [text normalization](https://en.wikipedia.org/wiki/Text_normalization): ensuring the text is easily machine-readable (e.g. proper encoding, no unicode combining characters, no extra invisible characters, etc)
* text cleaning: removing any irrelevant parts of the text that may hinder later text-processing (e.g. metadata)
* [tokenization](https://en.wikipedia.org/wiki/Text_segmentation#Word_segmentation): splitting the text into basic meaningful units (e.g. words, numbers, punctuation characters in some cases)
* [sentence-splitting](https://en.wikipedia.org/wiki/Sentence_boundary_disambiguation): splitting the text into larger meaningful units (sometimes also paragraph-splitting is needed)
* [orthographic](https://en.wikipedia.org/wiki/Orthography) analysis: analyse how tokens are written (e.g. case: lowercase, uppercase, titlecase, mixed case; or hyphenation: yes, no)
* [part-of-speech tagging](https://en.wikipedia.org/wiki/Part-of-speech_tagging): assign a part-of-speech tag to each token, denoting its part-of-speech (e.g. DT for determiner, NN for noun, NNP for proper noun, etc)
* [shallow syntactic parsing](https://en.wikipedia.org/wiki/Shallow_parsing): identifying noun and verb phrases (sometimes also complete [syntactic parsing](https://en.wikipedia.org/wiki/Parsing) is needed)
* [stemming](https://en.wikipedia.org/wiki/Stemming): removing any inflectional affixes from words (sometimes also [lemmatization](https://en.wikipedia.org/wiki/Lemmatisation) and other morphological analysis is needed)

Though these tasks may seem menial, they are crucial for any text-processing pipeline, since all further components depend on them. Most of these tasks are language-specific, except for text cleaning, which is specific to the types of texts you want to process.

### Gazetteer lookup
A gazetteer is a text-processing component which looks up parts of the text in a dictionary. GATE gazetteers then create "Lookup" annotations for the parts of the text that matched dictionary entries and may also add features conveying additional information from the dictionary. For example, a person-name gazetteer may match names of persons in the text and may also add a feature denoting the gender of the person.

Pipelines typically contain different gazetteers for different purposes. Most pipelines have a stopword gazetteer which identifies stopwords in the text. [Stopwords](https://en.wikipedia.org/wiki/Stop_words) are tokens that are semantically irrelevant to the text, such as function words or any other tokens that only add noise. Other typical examples of gazetteers are person-name gazetteer, as already mentioned, company-affix gazetteer, etc.

A very important type of gazetteer is the *Ontotext Linked Data Gazetteer*. This is the core component of any Ontotext named-entity extraction pipeline, such as this one. Like any other GATE gazetteer, it performs lookups in the text, creating "Lookup" annotations and adding features to those annotations. Unlike other GATE gazetteers, its dictionary is populated from a [GraphDB](http://graphdb.ontotext.com/) repository. It queries the repository for all the entities that we are interested in, then stores the URI of each entity, all its labels (e.g. preferred label and alternative labels) and any additional properties of the entity that we are also interested in. It is a much more advanced gazetteer, capable of looking up millions of entities, each with many possible labels, anywhere in the text with minimal memory footprint and extreme performance.

Another important advantage of the *Ontotext Linked Data Gazetteer* is that it lets you customize the matching logic. Simple string-matching is often too strict for our purposes. Suppose we have the entity "http://some-ontology.com/entity/oil" with the label "Oil" in our repository and the sentence "You may find that some oils have distinctive flavors, so try different types to discover which ones you like.". We would like our gazetteer to annotate "oils" as a mention of "http://some-ontology.com/entity/oil" but "oils" is not the same string as the label "Oil" - it starts with a lowercase "o" and is in plural. Most gazetteers have an option to perform case-insensitive lookup, which would solve the first problem, however solving the second problem is not so trivial. The *Ontotext Linked Data Gazetteer* solves it by allowing you to match features of the tokens, rather than the tokens themselves. We typically use this to match the stems of the tokens and thus eliminate differences in inflection.

### Disambiguation

### Postprocessing

## Resources
Some relevant external resources:
* [official GATE documentation](https://gate.ac.uk/sale/tao/split.html)
