# Hidden Markov Model and Dynamic Programming  

## The application of Dynamic Programming : Parts-of-Speech Tagging (POS)
 
The process of assigning a part-of-speech tag (Noun, Verb, Adjective...) to each word in an input text.  Tagging is difficult because some words can repre

- The whole team played **well**. [adverb]
- You are doing **well** for yourself. [adjective]
- **Well**, this assignment took me forever to complete. [interjection]
- The **well** is dry. [noun]
- Tears were beginning to **well** in her eyes. [verb]

Distinguishing the parts-of-speech of a word in a sentence will help you better understand the meaning of a sentence. This would be critically important i

- Computing the transition matrix T in a Hidden Markov Model
- Computing the emission matrix E in a Hidden Markov Model
- Computing the Viterbi algorithm
- Computing the accuracy of POS tagging model

### Hidden Markov Models for POS  
Implementing a Hidden Markov Model (HMM) with a Viterbi decoder
- The HMM is one of the most commonly used algorithms in Natural Language Processing
- In addition to parts-of-speech tagging, HMM is used in speech recognition, speech synthesis, etc.

The Markov Model contains a number of states and the probability of transition between those states.
- In this case, the states are the parts-of-speech.
- A Markov Model utilizes a transition matrix, `T`.
- A Hidden Markov Model adds an observation or emission matrix `E` which describes the probability of a visible observation when we are in a particular st
- In this case, the emissions are the words in the corpus
- The state, which is hidden, is the POS tag of that word.  
  
The 'states' are the Parts-of-speech designations found in the training data. They will also be referred to as 'tags' or POS in this assignment.  
- "NN" is noun, singular, 
- 'NNS' is noun, plural. 
- In addition, there are helpful tags like '--s--' which indicate a start of a sentence.
- You can get a more complete description at [Penn Treebank II tag set](https://www.clips.uantwerpen.be/pages/mbsp-tags). 


### Creating the 'T' transition probabilities matrix

- `T` transition probabilities matrix.
- and the `E` emission probabilities matrix.

Here is an example of what the `T` transition matrix would look like:  

|**T** |...|         RBS  |          RP  |         SYM  |      TO  |          UH|  ...|
|---|---|---|---|---|---|---|---|   
|**RBS**  |...|2.217069e-06  |2.217069e-06  |2.217069e-06  |0.008870  |2.217069e-06|...|  
|**RP**   |...|3.756509e-07  |7.516775e-04  |3.756509e-07  |0.051089  |3.756509e-07|...|
|**SYM**  |...|1.722772e-05  |1.722772e-05  |1.722772e-05  |0.000017  |1.722772e-05|...|
|**TO**   |...|4.477336e-05  |4.472863e-08  |4.472863e-08  |0.000090  |4.477336e-05|...|
|**UH**  |...|1.030439e-05  |1.030439e-05  |1.030439e-05  |0.061837  |3.092348e-02|...|
| ... |...| ...          | ...          | ...          | ...      | ...        | ...|


Note that the matrix above was computed with smoothing.

Each cell gives you the probability to go from one part of speech to another.
- In other words, there is a 4.47e-8 chance of going from parts-of-speech `TO` to `RP`.
- The sum of each row has to equal 1, because we assume that the next POS tag must be one of the available columns in the table.




### References  
Bishop, C. M. (2006). *Pattern Recognition and Machine Learning*. Springer.