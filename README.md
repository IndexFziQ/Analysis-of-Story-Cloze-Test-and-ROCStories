# ROC Stories Cloze-Task(SCT) Analysis

Analysis on ROCStories and related cloze-task. History, developments and future works.

# Introduction

Firstly, Mostafazadeh et al. (2016) proposed ROCStories dataset, which is a collection of crowd-sourced complete five sentence stories through Amazon MTurk. With a theme, each Story follows a character through a fairly simple series of events to a conclusion. We usually call the first four sentences 'plot', and the last one 'ending'. There are two main tasks about ROCStories: 1, story cloze test (SCT); 2, story generation. We focus on the first one and will research on the next one.

Based on ROCStories, Mostafazadeh et al. (2016) also introduced SCT evaluation framework and built development set and test set to address the lack of evaluation framework and datasets on which story comprehension model can be trained and tested. Dev set and test set were crowd-sourced by producing two related endings for the plot. In other words, every plot has two endings, and label is the index of the more appropriate ending.

Recently, many works proposed a problem: SCT may be an easier task than identifying whether a given ending is coherent or not. Also, they (Cai et al. 2017; Srinivasan et al. 2018) got roughly the same accuracy by only using the endings to do a binary classification. To address this issue, Sharma et al. proposed SCTv1.5 which have the following new characters to shed human-authorship biases:

**The goal of SCTv1.5**
* The new endings ['right' or 'wrong'] should
    * contain a similar number of tokens;
    * have similar distributions of token n-grams and char-grams;
    * occur as standalone events with the same likelihood to occur, with topical, sentimental, or emotion consistencies when applicable.

*Method #1*
* write 'right' and 'wrong' ending for the first four sentences
    * each sentence should stay within the same subject area of the story;
    * The number of words in two endings should not differ by more than two words;
    * When possible, two endings should try to keep a similar tone/sentiment as one another.

*Method #2*
* modify the fifth sentence ('right' ending) to the 'wrong' ending
    * 'right ending' is from five sentences stories;
    * should make sense standalone;
    * can not differ in the number of words from original sentence by more than three words;
    * can not use 'not' in front of a description or a verb.

# Previous Approaches

**Feature-based approach**



**Neural network approach**