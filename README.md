# nlp-benchmarks
Benchmark datasets for NLP tasks

This repo contains simple, preprocessed versions of several benchmark NLP datasets. All of them are available online and widely used, but the actual dataset files are surprisingly difficult to track down and format. Having put in the time to organize these once, I decided to save future me some time by putting them in a repo and including the appropriate citations (in bibtex format).

The analogies datasets are in the usual "quad" format: four words to the line, separated by spaces, with lines separated into sections by ": SECTION_NAME" lines. The task is to complete the analogy by inferring the last word from the first three.

The semantic similarity datasets are generally in a "word1 word2 score" format, with the words and score separated by spaces. The score is usually the average of similarity scores for the pair from several human raters, though this may differ by dataset.
