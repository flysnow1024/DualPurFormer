# Recognition of Phonetically Related Words

This analysis supplements the overall classification results by comparing DualPurFormer with MDM-Tent on word classes with related phonetic structures, as shown in Fig. 2(a) of the paper.

## Word Selection

We select five representative word pairs based on similarities in Pinyin initials, finals, or tones:

| Word pair | English translation | Pinyin |
| --- | --- | --- |
| 心情–钢琴 | mood–piano | xin1 qing2–gang1 qin2 |
| 心情–香肠 | mood–sausage | xin1 qing2–xiang1 chang2 |
| 愿意–换药 | willing–change dressing | yuan4 yi4–huan4 yao4 |
| 手巾–手机 | towel–cell phone | shou3 jin1–shou3 ji1 |
| 玩–碗 | play–bowl | wan2–wan3 |

These pairs illustrate different forms of phonetic similarity rather than identical pronunciations. Because 心情 appears in two pairs, the selected pairs cover nine unique word classes. Each class is counted once when calculating the average accuracy.

## Evaluation Protocol

The analysis uses the subject-dependent evaluation setting described in the paper, covering 12 subjects and six random seeds.

For each subject and random seed, recognition accuracy is calculated separately for each of the nine selected classes. These class accuracies are averaged with equal weight, and the resulting accuracy is then averaged across the six seeds to obtain one score per subject and method.

Fig. 2(a) compares the distribution of these subject-level scores between MDM-Tent and DualPurFormer. The analysis concerns recognition accuracy on the selected classes, not the frequency of confusion between the two words in each pair.

## Interpretation

DualPurFormer shows a higher subject-level accuracy distribution than MDM-Tent on these phonetically related word classes. This observation is consistent with improved discrimination of words sharing phonetic components, although it does not directly establish which neural features account for the improvement.

## Available Materials

- `duin_word_pinyin.csv`: word-to-Pinyin mapping used to support phonetic analysis. Numerical suffixes indicate Mandarin tones; `5` denotes the neutral tone.
- `README.md`: selected word pairs and evaluation protocol for Fig. 2(a).

The mapping file alone is not sufficient to reproduce the figure. Full reproduction requires the evaluation code, trained checkpoints, and access to the DU-IN dataset. The complete evaluation code will be released with the model implementation upon acceptance of the paper. The dataset is not redistributed in this repository.
