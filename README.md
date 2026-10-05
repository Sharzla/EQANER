# EQANER: Quran English Named Entity Recognition Dataset

EQANER is a named entity recognition (NER) dataset built on English translations of the Quran. It contains two English translations of the Quran, each annotated at the token level with eight named entity types. Each translation was produced by a different translator and is provided as a separate CSV file. The annotations follow the BIO tagging scheme.

## Contents

| File | Translator | Description |
|------|------------|-------------|
| `hilalikhan-revised.csv` | *Hilali-Khan* | Annotated English translation by Muhammad Muhsin Khan and Muhammad Taqi-ud-Din al-Hilali |
| `yusufali-revised.csv` | *Yusuf Ali* | Annotated English translation by Yusuf Ali |

## File format

Each CSV file has three columns:

| Column | Description |
|--------|-------------|
| `Sentence #` | Number identifying the verse/sentence the token belongs to |
| `token` | A single word or punctuation token |
| `Tag` | The entity label for the token, in BIO format |

Example:

| Sentence # | token | Tag |
|------------|-------|-----|
| 1 | And | O |
| 1 | We | O |
| 1 | sent | O |
| 1 | Moses | B-Prophet |
| 1 | to | O |
| 1 | Pharaoh | B-PERSON |

## Entity tags

Tags use the BIO scheme: `B-` marks the first token of an entity, `I-` marks a continuation token, and `O` marks a token outside any entity.

| Entity | Description | Tags |
|--------|-------------|------|
| Prophet | Names of prophets | `B-Prophet`, `I-Prophet` |
| PERSON | Names of individuals (excluding prophets) | `B-PERSON`, `I-PERSON` |
| NameOfGod | Names referring to God in Islam | `B-NameOfGod`, `I-NameOfGod` |
| NameOfGroup | Names of groups of people mentioned in the Quran | `B-NameOfGroup`, `I-NameOfGroup` |
| SpecialTime | Names related to the Day of Qiyamah (Judgement) | `B-SpecialTime`, `I-SpecialTime` |
| Angel | Names of angels | `B-Angel`, `I-Angel` |
| Jinn | Names of jinn or devil entities | `B-Jinn`, `I-Jinn` |
| LOC | Names of places mentioned in the Quran | `B-LOC`, `I-LOC` |


### Load directly from GitHub

```python
url = "https://raw.githubusercontent.com/<username>/<repo>/main/yusufali-revised.csv"
df1 = pd.read_csv(url)
```

### Combine both datasets

The two files share the same three columns (`Sentence #`, `token`, `Tag`), so they can be combined into a single dataset by appending the second file below the first. After the last row of the first CSV, the next row is the first row of the second CSV. This can be done with any table tool, such as Pandas (`pd.concat`).

### Check the entity distribution

```python
print(combined["Tag"].value_counts())
```

## Annotation notes

The annotation process, guidelines, and quality evaluation for this dataset are described in our paper:

> *Tarmizi, S. A., & Saad, S.* (2025, November). EQANER: Annotated Corpus for English Quranic Studies. In 2025 International Conference on Electrical Engineering and Informatics (ICEEI) (pp. 1-6). IEEE.
> doi: 10.1109/ICEEI68459.2025.11331085.

Please refer to the paper for full details on the annotation scheme, annotator guidelines, and dataset construction.


## Citation

If you use EQANER, please cite our paper:

```bibtex
@article{eqaner,
    author={Tarmizi, Shasha Arzila and Saad, Saidah},
    booktitle={2025 International Conference on Electrical Engineering and Informatics (ICEEI)}, 
    title={EQANER: Annotated Corpus for English Quranic Studies}, 
    year={2025},
    volume={},
    number={},
    pages={1-6},
    keywords={Training;Translation;Annotations;Reviews;Named entity recognition;Bidirectional control;Information retrieval;Transformers;Conditional random fields;Encoding;named entity recognition;annotated corpus;Quranic texts},
    doi={10.1109/ICEEI68459.2025.11331085}}
}
```

## Contact

*Shasha Arzila*
shasha.arzila@gmail.com
