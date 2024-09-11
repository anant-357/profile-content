predicting the probability of a word in a document.

## Unigram Language Model

- **n-gram**: sequence of **n** words.<br/>
- "hello" is a *unigram* or *1-gram*. "hello world" is a *bigram* or *2-gram* and so on.

### Training 

Estimation of probability of a word in a sentence based on the words that have come before it.

<center> 
<b>Sentence: </b> "This is a bottle." <br/></center>
<b> Estimates:</b><ul> <li> P("This"), <li>P("is" | "This"), <li>P("a" | "This" "is"), <li>P("bottle" | "This" "is" "a"), <li>P("." | "This" "is" "a" "bottle")</ul>

#### Assumptions
- Probability of each word is **independent** of other words.
- Probability of a word is calculated as the fraction of times the word occurs among all words in the training text. Training is complete when probabilities of all words in the document is calculated.

<b><center> P<sub>train</sub>("bottle" | <strike>"This" "is" "a"</strike> ) = P<sub>train</sub>("bottle") = n<sub>train</sub>(dream)<b>/</b>N<sub>train</sub></center></b>  

### Prediction

Probability of each sentence: 
<b><center>
P<sub>eval</sub>("This is a bottle.")<br/> = P<sub>train</sub>("This") . P<sub>train</sub>("is" | "This") . P<sub>train</sub>("a" | "This" "is") . P<sub>train</sub>("bottle" | "This" "is" "a") . P<sub>train</sub>("." | "This" "is" "a" "bottle") <br/> = P<sub>train</sub>("This") . P<sub>train</sub>("is") . P<sub>train</sub>("a") . P<sub>train</sub>("bottle") . P<sub>train</sub>(".") 
</center></b>

We can see here that probabilities are assigned not only to words but also to sentences. The "." character is the ```[END]``` character which ensures that the probability of all possible sentences sum to 1.

### Evaluation Metric
#### Average Log Likelihood
<b><center> 
P<sub>eval</sub>(text) = &Pi; P<sub>train</sub>(word)<br/>
log(P<sub>eval</sub>(text)) = &Sigma; log(P<sub>train</sub>(word))<br/>
Average log likelihood<sub>eval</sub> = &Sigma; log(P<sub>train</sub>(word))<br/>/ N<sub>eval</sub>
</center></b>

### Unknown Unigrams

If our model gets a word which never occurred in the training data, we run into a problem.

<b><center>
n<sub>train</sub>(unigram) = 0<br/>
P<sub>train</sub>(unigram) = 0<br/>
log(P<sub>train</sub>(unigram)) = log(0) = -&infin;
</center></b>

### Laplace smoothing
- Introduce new **[UNK]** unigram. This unigram never occurs in the data so its counter always 0.
- Now a pseudo-count **k** is added to all unigrams in the data. Most commonly **k=1**. This is also called "add-one smoothing"

- The -&infin; problem is avoided now.
predicting the probability of a word in a document.

## Unigram Language Model

- **n-gram**: sequence of **n** words.<br/>
- "hello" is a *unigram* or *1-gram*. "hello world" is a *bigram* or *2-gram* and so on.

### Training 

Estimation of probability of a word in a sentence based on the words that have come before it.

<center> 
<b>Sentence: </b> "This is a bottle." <br/></center>
<b> Estimates:</b><ul> <li> P("This"), <li>P("is" | "This"), <li>P("a" | "This" "is"), <li>P("bottle" | "This" "is" "a"), <li>P("." | "This" "is" "a" "bottle")</ul>

#### Assumptions
- Probability of each word is **independent** of other words.
- Probability of a word is calculated as the fraction of times the word occurs among all words in the training text. Training is complete when probabilities of all words in the document is calculated.

<b><center> P<sub>train</sub>("bottle" | <strike>"This" "is" "a"</strike> ) = P<sub>train</sub>("bottle") = n<sub>train</sub>(dream)<b>/</b>N<sub>train</sub></center></b>  

### Prediction

Probability of each sentence: 
<b><center>
P<sub>eval</sub>("This is a bottle.")<br/> = P<sub>train</sub>("This") . P<sub>train</sub>("is" | "This") . P<sub>train</sub>("a" | "This" "is") . P<sub>train</sub>("bottle" | "This" "is" "a") . P<sub>train</sub>("." | "This" "is" "a" "bottle") <br/> = P<sub>train</sub>("This") . P<sub>train</sub>("is") . P<sub>train</sub>("a") . P<sub>train</sub>("bottle") . P<sub>train</sub>(".") 
</center></b>

We can see here that probabilities are assigned not only to words but also to sentences. The "." character is the ```[END]``` character which ensures that the probability of all possible sentences sum to 1.

### Evaluation Metric
#### Average Log Likelihood
<b><center> 
P<sub>eval</sub>(text) = &Pi; P<sub>train</sub>(word)<br/>
log(P<sub>eval</sub>(text)) = &Sigma; log(P<sub>train</sub>(word))<br/>
Average log likelihood<sub>eval</sub> = &Sigma; log(P<sub>train</sub>(word))<br/>/ N<sub>eval</sub>
</center></b>
