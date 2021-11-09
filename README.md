# MedMentions: A UMLS Annotated Dataset

This is a preliminary release of the _MedMentions_ dataset, a corpus of Biomedical papers
annotated with mentions of UMLS entities. [CZI Meta](https://www.chanzuckerberg.com/science/projects-meta) 
is releasing this data to promote NLP research on Biomedical text.

This data is being released under the [CC0 license](https://creativecommons.org/publicdomain/zero/1.0/).
The papers in the corpus were selected from those available from [PubMed&reg; / Medline&reg;](https://www.nlm.nih.gov/databases/download/pubmed_medline.html).
Users are referred to that source for the most current and accurate version of the text for the corresponding papers.


## Introduction

**Corpus:** The _MedMentions_ corpus consists of 4,392 papers (Titles and Abstracts) randomly selected
from among papers released on [PubMed](https://www.ncbi.nlm.nih.gov/pubmed/) in 2016, that 
were in the biomedical field, published in the English language, and had both a Title and 
an Abstract.

**Annotators:** We recruited a team of professional annotators with rich experience in biomedical content 
curation to exhaustively annotate all [UMLS&reg;](https://uts.nlm.nih.gov/home.html) 
(2017AA full version) entity mentions in these papers.

**Annotation quality:** We did not collect stringent IAA (Inter-annotator agreement) data. 
To gain insight on the annotation quality of *MedMentions*, we randomly selected eight 
papers from the annotated corpus, containing a total of 469 concepts. Two biologists 
('Reviewer') who did not participate in the annotation task then each reviewed four papers. 
The agreement between Reviewers and Annotators, an estimate of the *Precision* of the 
annotations, was 97.3%.


## The Full Dataset, and Subsets

* [full](full/): This is the full dataset
* [ST21pv](st21pv/): This is the ST21pv subset, containing a subset of the full annotations, 
    targeting information retrieval.


## The PubTator format

The annotated data is published in [PubTator](http://bioportal.bioontology.org/ontologies/EDAM?p=classes&conceptid=format_3783)
format:

Each paper or document ends with a blank line, and is represented as (without the spaces):
```
PMID | t | Title text
PMID | a | Abstract text
PMID TAB StartIndex TAB EndIndex TAB MentionTextSegment TAB SemanticTypeID TAB EntityID
...
```

The first two lines present the Title and Abstract texts (no line-breaks or tabs in the _text_). 
Subsequent lines present the mentions, one per line.
The _StartIndex_ and _EndIndex_ are 0-based character indices into the document text, constructed
by concatenating the Title and Abstract, separated by a SPACE character. The _MentionTextSegment_
is the actual mention between those character positions. The _EntityID_ is the UMLS entity 
(concept) id, and the _SemanticTypeID_ is the id for the Semantic Type that entity is linked 
to in UMLS. If the UMLS entity is linked to more than one semantic type, then this field 
contains a comma-separated list of all these type IDs. All UMLS concepts that are not in the 2017-AA Active release are linked to the
special semantic type _UnknownType_.

Here is an example:
```
25763772|t|DCTN4 as a modifier of chronic Pseudomonas aeruginosa infection in cystic fibrosis
25763772|a|Pseudomonas aeruginosa (Pa) infection in cystic fibrosis (CF) patients is associated with worse long-term pulmonary disease and shorter survival, and chronic Pa infection (CPA) is associated with reduced lung function, faster rate of lung decline, increased rates of exacerbations and shorter survival. By using exome sequencing and extreme phenotype design, it was recently shown that isoforms of dynactin 4 (DCTN4) may influence Pa infection in CF, leading to worse respiratory disease. The purpose of this study was to investigate the role of DCTN4 missense variants on Pa infection incidence, age at first Pa infection and chronic Pa infection incidence in a cohort of adult CF patients from a single centre. Polymerase chain reaction and direct sequencing were used to screen DNA samples for DCTN4 variants. A total of 121 adult CF patients from the Cochin Hospital CF centre have been included, all of them carrying two CFTR defects: 103 developed at least 1 pulmonary infection with Pa, and 68 patients of them had CPA. DCTN4 variants were identified in 24% (29/121) CF patients with Pa infection and in only 17% (3/18) CF patients with no Pa infection. Of the patients with CPA, 29% (20/68) had DCTN4 missense variants vs 23% (8/35) in patients without CPA. Interestingly, p.Tyr263Cys tend to be more frequently observed in CF patients with CPA than in patients without CPA (4/68 vs 0/35), and DCTN4 missense variants tend to be more frequent in male CF patients with CPA bearing two class II mutations than in male CF patients without CPA bearing two class II mutations (P = 0.06). Our observations reinforce that DCTN4 missense variants, especially p.Tyr263Cys, may be involved in the pathogenesis of CPA in male CF.
25763772        0       5       DCTN4   T116,T123    C4308010
25763772        23      63      chronic Pseudomonas aeruginosa infection        T047    C0854135
25763772        67      82      cystic fibrosis T047    C0010674
25763772        83      120     Pseudomonas aeruginosa (Pa) infection   T047    C0854135
...
```
In this example, the Title is 82 characters long. The first mention is for the UMLS concept
"DCTN4 protein, human" whose UMLS id is _C4308010_. This entity is linked to two semantic 
types: "Amino Acid, Peptide, or Protein" (T116) and "Biologically Active Substance" (T123). 


## How to cite

If you use MedMentions, please cite the following paper:

Sunil Mohan and Donghui Li. 2019.
*MedMentions: A Large Biomedical Corpus Annotated with UMLS Concepts*.
In Proceedings of the 2019 Conference on Automated Knowledge Base Construction (AKBC 2019).
Amherst, Massachusetts, USA. May 2019.
[[Preprint](https://arxiv.org/abs/1902.09476)]

### Our Latest Model

Our model achieves SOTA results (2021) on UMLS recognition (ST21pv subset): a lower bound F1 score of **0.570** for *mention level* entity recognition (detection and linking), and an F1 score of **0.657** for recognizing UMLS concepts at the *document level*. For details, please see the following paper:

Sunil Mohan, Rico Angell, Nicholas Monath, Andrew McCallum. 2021.
*Low Resource Recognition and Linking of Biomedical Concepts from a Large Ontology*. In Proceedings of the ACM Conference on Bioinformatics, Computational Biology, and Health Informatics (ACM-BCB), 2021. [[doi](https://doi.org/10.1145/3459930.3469524)] [[Preprint](https://arxiv.org/abs/2101.10587)]

### Other papers on MedMentions

Shikhar Murty, Patrick Verga, Luke Vilnis, Irena Radovanovic and Andrew McCallum. 2018.
*Hierarchical Losses and New Resources for Fine-grained Entity Typing and Linking*.
The 56th Annual Meeting of the Association for Computational Linguistics (ACL). 
Melbourne, Australia. July 2018.


## Feedback, Questions

If you have any comments, questions or issues, please post a note in 
[GitHub issues](https://github.com/chanzuckerberg/MedMentions/issues).
