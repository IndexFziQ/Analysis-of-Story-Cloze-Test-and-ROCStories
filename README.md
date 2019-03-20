# ROC Stories Cloze-Task(SCT) Analysis

Analysis on ROCStories and related cloze-task. History, developments and future works.

# Introduction

Firstly, Mostafazadeh et al. (2016) proposed ROCStories dataset, which is a collection of crowd-sourced complete five sentence stories through Amazon MTurk. With a theme, each Story follows a character through a fairly simple series of events to a conclusion. We usually call the first four sentences 'plot', and the last one 'ending'. The prompt to the crowd-sourcing is the following points:

**The prompt of ROCStories**
Imagine that you want to tell a five-sentence story to your friend. It can be about something that happened, something you or someone else has experienced in the past, or simply any life story about someone or something. Your task is to write this five-sentence story. Your should have all of the following five properties:
* Your story should be entirely realistic;
* Your story should read like a coherent story, with a specific beginning and end, where something happens in between. This constraint resulted in many casual and temporal links between the events.
* Each sentence in your story should be logically related to the next sentence and be about the characters of the story.

There are two main tasks about ROCStories: *1, story cloze test (SCT); 2, story generation; 3, knowledge extraction and narrative structure learning.* We focus on the first one and will research on the next two.

Based on ROCStories, Mostafazadeh et al. (2016) also introduced **SCT** evaluation framework and built development set and test set to address the lack of evaluation framework and datasets on which story comprehension model can be trained and tested. Dev set and test set were crowd-sourced by producing two related endings for the plot. In other words, every plot has two endings, and label is the index of the more appropriate ending.

**The prompt of SCTv1.0**
You are given a sequence of four sentences, which together form a coherent four-sentence story. Your task is to write the fifth sentence which is an ending to the story in two ways:
* 'right ending': that naturally ends the story in a coherent and meaningful way.
* 'wrong ending': that is entirely **impossible** to be a correct/natural ending to the story. That is, if you add this fifth sentence to the four sentences it would not make sense as a meaningful story.
*Besides:*
* All endings should follow up the story by sharing at least one of the characters of the story.
* All endings should be meaningful and realistic when you read it on its own.

Recently, many works proposed a problem: SCTv1.0 may be an easier task than identifying whether a given ending is coherent or not. Also, they (Cai et al. 2017; Srinivasan et al. 2018) got roughly the same accuracy by only using the endings to do a binary classification. Maybe, the prompt of SCTv1.0 has some problems. To address this issue, Sharma et al. proposed SCTv1.5 which have the following new characters to shed human-authorship biases:

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

ROCNLP (baseline) Two feed-forward neural networks trained jointly on ROCStories to project the four-sentences context and the right fifth sen- tence into the same vector space. This model is called Deep Structured Semantic Model (DSSM) (Huang et al., 2013) and had outperformed all the other baselines reported in Mostafazadeh et al. (2016).

msap (University of Washington) Linear clas- sifier based on language modeling probabilities of the entire story, and linguistic features of only the ending sentences. These ending “style” features include sentence length as well as word and character n-gram in each candi- date ending (independent of story).

cogcomp (University of Illinois). Linear classi- fication system that measures a story’s coherence based on the sequence of events, emotional trajec- tory, and plot consistency. This model takes into account frame-based and sentiment-based lan- guage modeling probabilities as well as a topical consistency score.

EndingReg 
Tackling the Story Ending Biases in The Story Cloze Test
Rishi Sharma, James F. Allen, Omid Bakhshandeh, Nasrin Mostafazadeh

**Neural network approach**

A Simple and Effective Approach to the Story Cloze Test
Siddarth Srinivasan, Richa Arora, Mark Riedl
Georgia Institute of Technology

Improving Language Understanding by Generative Pre-Training

Improving Machine Reading Comprehension with General Reading Strategies

Incorporating Structured Commonsense Knowledge in Story Completion