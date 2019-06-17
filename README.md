# nlp-benchmarks
Benchmark datasets for NLP tasks

This repo contains simple, preprocessed versions of several benchmark NLP datasets. All of them are available online and widely used, but the actual dataset files are surprisingly difficult to track down and format. Having put in the time to organize these once, I decided to save future me some time by putting them in a repo and including the appropriate citations. See `references.bib` for the original papers, authors and the current dataset download / homepage links.

The semantic similarity datasets are generally in a "word1 word2 score" format, with the words and score separated by spaces. The score is usually the average of similarity scores for the pair from several human raters, though this may differ by dataset.

The Google and MSR analogies datasets are [pair-based](https://aclweb.org/aclwiki/Analogy_(State_of_the_art)#Analogy_tasks): the task is to complete the analogy by inferring the last word from the first three. These datasets are in the usual "quad" format: four words to the line, separated by spaces, with lines separated into sections by `: SECTION_NAME` lines. 

The BATS dataset is [set-based](https://aclweb.org/aclwiki/Analogy_(State_of_the_art)#Analogy_tasks) rather than pair-based. That is, given a set of `word:word*` pairs which describe the analogy relation and an additional query word `w`, the goal is to find the matching word `w*` which completes the analogy. Each section of the BATS file (separated by the same `: SECTION_NAME` lines as above) consists of such a set. (Using the data in practice relies on sampling: one might, for instance, split a section into train and test sets, use a leave-one-out approach of attempting to complete each pair from the others, or use other strategies.)

The BATS dataset was extracted into one file from the original download by the following shell snippet:
```
for i in *; do
    for j in $i/*; do
        echo ": $i - $(basename "${j%.*}")" >> bats_3_0.txt
        echo "$(cat "$j" | sed -e 's/      / /g')" >> bats_3_0.txt
    done;
done
```

