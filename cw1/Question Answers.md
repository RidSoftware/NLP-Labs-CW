# Results:

| index | Dataset | Vector size | Window | Min count | Epochs | Vocab size | Spearman rho          | p-value                 | OOV pairs | Train time \(s\) | p-value \(decimal\)     |
| ----- | ------- | ----------- | ------ | --------- | ------ | ---------- | --------------------- | ----------------------- | --------- | ---------------- | ----------------------- |
| 7     | large   | 50          | 10     | 5         | 5      | 162898     | 0\.6539066110731484   | 3\.0263652213558535e-42 | 18        | 681\.11          | 0\.00000000000000000000 |
| 6     | large   | 100         | 5      | 5         | 5      | 162898     | 0\.650294100150042    | 1\.1913446245283676e-41 | 18        | 555\.76          | 0\.00000000000000000000 |
| 5     | large   | 50          | 5      | 5         | 5      | 162898     | 0\.6362302847074028   | 2\.077818557932442e-39  | 18        | 613\.96          | 0\.00000000000000000000 |
| 8     | large   | 50          | 5      | 2         | 5      | 290287     | 0\.6357040886166813   | 2\.5074098198668358e-39 | 18        | 633\.58          | 0\.00000000000000000000 |
| 9     | large   | 50          | 5      | 5         | 10     | 162898     | 0\.6334754558563429   | 5\.53552533092025e-39   | 18        | 1154\.1          | 0\.00000000000000000000 |
| 4     | small   | 50          | 5      | 5         | 10     | 13838      | 0\.18788640385045638  | 0\.0027490474051209326  | 101       | 11\.12           | 0\.00274904740512093258 |
| 2     | small   | 50          | 10     | 5         | 5      | 13838      | 0\.12147209984712935  | 0\.05412181908011854    | 101       | 7\.08            | 0\.05412181908011853837 |
| 0     | small   | 50          | 5      | 5         | 5      | 13838      | 0\.09265386133610805  | 0\.14246348964573674    | 101       | 6\.52            | 0\.14246348964573674056 |
| 1     | small   | 100         | 5      | 5         | 5      | 13838      | 0\.0778064318955937   | 0\.21837340265671623    | 101       | 4\.72            | 0\.21837340265671623118 |
| 3     | small   | 50          | 5      | 2         | 5      | 26508      | 0\.061705343034525906 | 0\.2859219159502587     | 52        | 5\.98            | 0\.28592191595025867601 |

# Questions
**a. What are the cosine similarity scores for the following pairs:**
- plane / car
- planet / sun
- cup / article
- sugar / approach

*ANSWER:*
- plane / car
	- 0.6031457
- planet / sun
	- 0.59318095
- cup / article
	- 0.050892476
- sugar / approach
	- -0.17874575

---
**b. What is the value of the Spearman correlation coefficients computed in Step 4?**

*ANSWER:*
wikitext_small: Spearman ρ = 0.11157656314685778
wikitext_large: Spearman ρ = 0.6283015932937069

---
**c. How do you interpret each coefficient value with respect to the word similarity task?**

**Are the coefficient values for the two vector space models you created different, and if so, why?**

*ANSWER:*
The spearman correlation for wikitext_small (approx. 0.11) shows a weak relationship between the models similarity scores and human judgements. It is at least a positive value which shows that it did learn in the right direction, just not very well.

The spearman correlation for wikitext_large (approx. 0.63) shows a much stronger relationship which indicates that training on a larger corpus generally aligns better with human perception of the relatedness of the words.

The difference (large > small) occurs because the larger dataset gives more examples of the words in various context, thus the model can learn a more nuanced understanding of the words semantic relationships to others. The smaller corpus will have a more limited vocabulary and less data to train on, meaning the models semantic understanding less informed.

---
**d. What is the value of the Spearman correlation coefficient and how do you interpret it?**

*ANSWER:*
0.6941224810339758

The pretrained google news model had a rho value of approx. 0.69, showing a strong positive relationship between the model and the benchmark.

This is better than even our word2vec trained on the wikitext_large model, strengthening the idea that a larger corpus increases the alignment with human perception, as this model is trained on a much larger (and likely more diverse) corpus than the wikitext models.

Note that there seems to be diminishing returns as we train on larger and larger corpus, approaching rho of ~0.7, perhaps this is indicative of a limitation of using wordsim353 as a benchmark.

---
**e. Create a table of results that summarises your experiments.** 
Tips: In case you have run several experiments with different hyperparameters choose to present the most significant. It might be worth presenting more than one experiment with only a single hyperparameter change if you want to emphasise a striking difference worth discussing. Finally, apart from the Spearman correlation coefficients, make sure you also include the most significant hyperparameters as separate columns (for example, see Table 2 from [Merity et al., 2016](https://arxiv.org/pdf/1609.07843.pdf)).

*ANSWER:*

| Dataset | Vector size | Window | Min count | Epochs | Vocab size | Spearman rho          | p-value                 | OOV pairs | Train time \(s\) | p-value \(decimal\)     |
| ------- | ----------- | ------ | --------- | ------ | ---------- | --------------------- | ----------------------- | --------- | ---------------- | ----------------------- |
| small   | 50          | 5      | 5         | 5      | 13838      | 0\.09265386133610805  | 0\.14246348964573674    | 101       | 6\.52            | 0\.14246348964573674056 |
| small   | 100         | 5      | 5         | 5      | 13838      | 0\.0778064318955937   | 0\.21837340265671623    | 101       | 4\.72            | 0\.21837340265671623118 |
| small   | 50          | 10     | 5         | 5      | 13838      | 0\.12147209984712935  | 0\.05412181908011854    | 101       | 7\.08            | 0\.05412181908011853837 |
| small   | 50          | 5      | 2         | 5      | 26508      | 0\.061705343034525906 | 0\.2859219159502587     | 52        | 5\.98            | 0\.28592191595025867601 |
| small   | 50          | 5      | 5         | 10     | 13838      | 0\.18788640385045638  | 0\.0027490474051209326  | 101       | 11\.12           | 0\.00274904740512093258 |
| large   | 50          | 5      | 5         | 5      | 162898     | 0\.6362302847074028   | 2\.077818557932442e-39  | 18        | 613\.96          | 0\.00000000000000000000 |
| large   | 100         | 5      | 5         | 5      | 162898     | 0\.650294100150042    | 1\.1913446245283676e-41 | 18        | 555\.76          | 0\.00000000000000000000 |
| large   | 50          | 10     | 5         | 5      | 162898     | 0\.6539066110731484   | 3\.0263652213558535e-42 | 18        | 681\.11          | 0\.00000000000000000000 |
| large   | 50          | 5      | 2         | 5      | 290287     | 0\.6357040886166813   | 2\.5074098198668358e-39 | 18        | 633\.58          | 0\.00000000000000000000 |
| large   | 50          | 5      | 5         | 10     | 162898     | 0\.6334754558563429   | 5\.53552533092025e-39   | 18        | 1154\.1          | 0\.00000000000000000000 |

---
**f. Using the table of results from your answer to question g., write a short discussion section that answers the following questions:**
	i. Does a bigger corpus yield better representations?
	ii. Does a bigger vocabulary yield better representations?
	iii. Do bigger word vectors yield better representations?
	iv. Does a bigger context window yield better representations?
	v. Step 6 requires you to look for the best combination of hyperparameters using
	the same two datasets for evaluation. Is this a good practice?

*ANSWER:*
	i. Does a bigger corpus yield better representations?
		Yes, the models trained on wikitext_large (rho = ~0.06-0.19) consistently outperformed those trained on wikitext_small (rho = ~0.63-0.65) regards the Spearman correlations. This strongly indicates that larger corpus teaches richer context to the model's semantic understanding of words. The google news model continues this trend.
	ii. Does a bigger vocabulary yield better representations?
		Our results have not shown this, with both large and small datasets, when we reduced min_count from 5 to 2 (which increases vocabulary).
			wikitext_small, min_count = 5, rho = 0.09265386133610805
			wikitext_small, min_count = 2, rho = 0.061705343034525906
			wikitext_large, min_count = 5, rho = 0.6362302847074028
			wikitext_large, min_count = 2, rho = 0.6357040886166813
		This in fact suggests the opposite, I suspect that this is because we add relatively unimportant/rarer words provides more noise than useful semantic context.
	iii. Do bigger word vectors yield better representations?
		Our results show that with a small dataset, increasing word vector size reduces the spearman correlation, where as with a large dataset it does improve the spearman correlation.
			wikitext_small, vector_size = 50, rho = 0.09265386133610805
			wikitext_small, vector_size = 100, rho = 0.0778064318955937
			wikitext_large, vector_size = 50, rho = 0.6362302847074028
			wikitext_large, vector_size = 100, rho = 0.650294100150042
		This suggests that bigger vectors only produce better trained word2vec models if there is sufficiently large datasets.
	iv. Does a bigger context window yield better representations?
		Yes, our results show that an increase in context window size yields the best results. Our highest rho values correlated with an increase in the window size from 5-10, for both small and large datasets.
			wikitext_small, window = 5, rho = 0.09265386133610805
			wikitext_small, window = 10, rho = 0.12147209984712935
			wikitext_large, window = 5, rho = 0.6362302847074028
			wikitext_large, window = 10, rho = 0.6539066110731484
		This suggests that context window size is the most important hyperparameter to tune when we seek to improve our model. (at least in the context of improving spearman correlation with wordsim353 as our evaluation metric)
	v. Step 6 requires you to look for the best combination of hyperparameters using the same two datasets for evaluation. Is this a good practice?
		Not necessarily as we risk overfitting to the WordSim353 instead of improving our model generally. Though we use the wordsim dataset as a gold standard in this example, it is not the universal source of truth regarding the semantic meaning of words.


---
**g. What are the top-5 analogies for the following configurations:**
- man is to woman as king is to ___ ?
- Athens is to Greece as Rome is to ___ ?
- reading is to read as playing is to ___ ?
- Greece is to souvlaki as Italy is to ___ ?
- airplane is to propeller as car is to ___ ?
Is the top-1 answer always the “correct”? What about the rest of the results?

*ANSWER:*

 man  is to  woman  as  king  is to ?
1. queen (0.7118)
2. monarch (0.6190)
3. princess (0.5902)
4. crown_prince (0.5499)
5. prince (0.5377)

 Athens  is to  Greece  as  Rome  is to ?
1. Italy (0.6826)
2. Sicily (0.5808)
3. Portugal (0.5467)
4. Italian (0.5194)
5. ANSA (0.5114)

 reading  is to  read  as  playing  is to ?
1. played (0.7010)
2. play (0.6676)
3. Playing (0.5651)
4. playin (0.5131)
5. toplay (0.4870)

 Greece  is to  souvlaki  as  Italy  is to ?
1. quiche_Lorraine (0.5962)
2. gelati (0.5909)
3. pesce (0.5880)
4. pizza_margherita (0.5872)
5. porchetta (0.5866)

 airplane  is to  propeller  as  car  is to ?
1. steering_wheel (0.5703)
2. front_fender (0.5417)
3. fender (0.5393)
4. Ford_Festiva (0.5320)
5. Nissan_###ZX (0.5274)

The top-1 answer is not necessarily 'perfect', for example a car-steering_wheel is not necessarily an exact analogous match to airplane-propeller, perhaps a perfect analogy doesn't exist. But the highest valued results are generally of approximate semantic meaning. At least within the context of the data that the models learn from.

---
**h. What are the top-5 analogies for the following configurations?

**Can you identify any gender-based stereotypes? **

**Briefly discuss your findings:**
- man is to woman as computer programmer is to ___ ?
- man is to woman as superstar is to ___ ?
- man is to woman as guitarist is to ___ ?
- man is to woman as boss is to ___ ?

*ANSWER:*

 man  is to  woman  as  computer_programmer  is to ?
1. homemaker (0.5627)
2. housewife (0.5105)
3. graphic_designer (0.5052)
4. schoolteacher (0.4979)
5. businesswoman (0.4935)

 man  is to  woman  as  superstar  is to ?
1. megastar (0.6585)
2. diva (0.6237)
3. pop_diva (0.5787)
4. star (0.5745)
5. songstress (0.5550)

 man  is to  woman  as  guitarist  is to ?
1. vocalist (0.7626)
2. drummer (0.6976)
3. bassist (0.6961)
4. singer_guitarist (0.6777)
5. guitarist_vocalist (0.6640)

 man  is to  woman  as  boss  is to ?
1. bosses (0.5523)
2. manageress (0.4915)
3. exec (0.4594)
4. Manageress (0.4560)
5. receptionist (0.4474)

The gender bias arises quite evidently, in the example man-woman as computer_programmer-homemaker/housewife/etc., which is clear as it applies gendered stereotypes to occupations. This is due to the bias within the data that it is trained upon, thus directly replicating biases from the data.

---