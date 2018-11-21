# _MedMentions_: Full Dataset

This is the _ST21pv_ subset of the full _MedMentions_ dataset.
See also additional documentation [here](../README.md).

## Contents

* [data](data/): Data files ...
    * **corpus_pubtator.txt.gz:** The annotated data, in PubTator format, `gzip`-ed.
    * **corpus_pubtator_pmids_trng.txt, corpus_pubtator_pmids_dev.txt, corpus_pubtator_pmids_test.txt:**
      For the training / dev / validation splits, please refer to these files from the 
      [full MedMentions dataset](../full/data).
      
## Constructing the ST21pv subset

MedMentions ST21pv (MM-ST21pv) contains mentions of concepts from the ST21pv subset 
of UMLS 2017-AA Active. The ST21pv (21 Semantic Types and Preferred Vocabularies) subset of UMLS
was constructed to contain concepts that are linked in UMLS to one of the following 21 semantic types, 
or to one of their descendants in the semantic type hierarchy:

*   T005: Virus (level 4)
*   T007: Bacterium (level 4)
*   T017: Anatomical Structure (level 3)
*   T022: Body System (level 5)
*   T031: Body Substance (level 4)
*   T033: Finding (level 3)
*   T037: Injury or Poisoning (level 3)
*   T038: Biologic Function (level 4)
*   T058: Health Care Activity (level 4)
*   T062: Research Activity (level 4)
*   T074: Medical Device (level 4)
*   T082: Spatial Concept (level 4)
*   T091: Biomedical Occupation or Discipline (level 4)
*   T092: Organization (level 3)
*   T097: Professional or Occupational Group (level 4)
*   T098: Population Group (level 4)
*   T103: Chemical (level 4)
*   T168: Food (level 4)
*   T170: Intellectual Product (level 3)
*   T201: Clinical Attribute (level 4)
*   T204: Eukaryote (level 4)

Furthermore, only concepts that are mapped in UMLS to one of the following 18 source ontologies are 
included:

Ontology Abbrev. | Name
---------------- | ----
CPT	|  Current Procedural Terminology
FMA	|  Foundational Model of Anatomy 
GO	|   Gene Ontology
HGNC	|  HUGO Gene Nomenclature Committee
HPO	|  Human Phenotype Ontology
ICD10	|   International Classification of Diseases, Tenth Revision
ICD10CM	|  ICD10 Clinical Modification
ICD9CM	|  ICD9 Clinical Modification
MDR	|   Medical Dictionary for Regulatory Activities
MSH	|  Medical Subject Headings
MTH	|  UMLS Metathesaurus Names
NCBI	|  National Center for Biotechnology Information Taxonomy
NCI	|   National Cancer Institute Thesaurus
NDDF	|  First DataBank MedKnowledge
NDFRT	|  National Drug File -- Reference Terminology
OMIM	|  Online Mendelian Inheritance in Man
RXNORM	|  NLM's Nomenclature for Clinical Drugs for Humans
SNOMEDCT_US	|  US edn. of the Systematized Nomenclature of Medicine-Clinical Terms


## Some Corpus Statistics

Description | Stat  | avg
----------- | ----: | ---
Number of Annotated Docs in MM-ST21pv   |     4,392
Number of Concepts in UMLS ST21pv subset | ﻿2,327,250
Total number of Mentioned Concepts | 	       ﻿25,419   | (1.09% of UMLS ST21pv)
Total number of Mentions in MM-ST21pv |              ﻿203,282 | (46.3 / doc)
Total Number of of Tokens (PTB via StanfordNLP) |    1,176,058 | (267.8 / doc)
Number of Annotated Tokens | 			               366,742 | (83.5 / doc)
Proportion of tokens annotated | 	  	                 31.2% | (1.8 / mention)
