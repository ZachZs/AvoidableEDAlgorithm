# Avoidable ED Algorithm

This repository contains the final presentation of the practicum work that my team did for Benevera Health during my M.S. program. The actual code and data sets are unavailable as they are property of Benevera Health, but they have allowed the use of the presentation slides that the team created to be used.

### <i>Background</i>

Benevera Health is a Population Health Management Company that works as a joint venture between several hospitals and an insurance provider (Harvard Pilgrim). Their analytics team finds at-risk patients, and their health care team provides support to those patients.

Our team was tasked with creating a model to predict if a patient would have an avoidable emergency department visit in the near future. A visit would be considered avoidable if it was preventable through seeking earlier care (our basis was the NYU ED Algorithm -> more information can be found <a href="https://wagner.nyu.edu/faculty/billings/nyued-background">here</a>).

Benevera supplied the team with access to Electronic Health Records (EHR) records from the hospitals, as well as insurance information for their members. This provided a large amount of data for the team to work with. The data was aggregated into individual claims, which were the basis of the predictive models.

### <i>Results</i>

The final result has two components; an exploration of the data, and the creation of predictive models. The exploration of the data was used as an investigation to find insights into what information from the EHR would be useful to Benevera. They could take these results and use them to increase the productivity of their analytics team in finding at-risk patients.

The creation of the predictive model utilized both traditional machine learning methods, as well as deep learning methods. Due to limitations in computing power/tool access, only two traditional methods were used (Random Forest and Logistic Regression). The outcome of these attempts were unsuccessful, and the models proved unusable.

The attempts at creating a neural network proved much more successful. After creating numerous types and builds of networks, the final one was an ensemble of multiple inputs. The basic structure was four inputs, one for each data type (categorical, continuous, ICD codes, and Procedure codes). These inputs were run through their own formatting and combined within a dense vanilla neural network, which was then used to predict the claim as avoidable or not. For each member, the claim predictions were compiled together and used to create a risk score for that patient. See slides for more in-depth description.

### <i>Tools Used</i>

<b>Word2Vec</b>: A tool used to create vector representations of words. The team treated the ICD and Procedure codes as words, and the amount of them in a claim as a sentence. Word2Vec was then run on the 'corpus' of the codes for each claim to create a vector for each code that was then used in place of the code in the model. <a href="https://papers.nips.cc/paper/5021-distributed-representations-of-words-and-phrases-and-their-compositionality.pdf">Here</a> is the original paper about the method.

<b>Embedding Layers</b>: Another method of turning categories into vectors. This method was used on the categorical data (besides the ICD and Procedure codes) to create numerical representations of their values for the model.

<b>Major Python Packages</b>: <a href="https://radimrehurek.com/gensim/index.html">Gensim</a>, <a href="https://scikit-learn.org/stable/">Sci-Kit Learn</a>, <a href="https://keras.io/">Keras</a>, <a href="https://pandas.pydata.org/">Pandas</a>, <a href="https://seaborn.pydata.org/">Seaborn</a>
