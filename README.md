# Knowledge Graphs with Contradictions

Collection of relevant datasets for building knowledge graphs (KGs) with contradicting information.

The PhD project sees the development of an approach able to detect contradicting statements within a KG to then produce conflict-aware KG representations for use in downstream tasks.
One of the major difficulties of evaluating a graph-based model on the task of contradiction detection over knowledge graphs is the near inexistence of benchmark datasets with contradictions.
Therefore, a first step to allow evaluation over this task is the construction of datasets for KGs with contradictions.   

As such, in "Section 2 - Datasets", I present several public datasets, the majority being of KGs, to potentially be used in my work.
Some, of the same domain but different data sources, may even be combined to generate logical contradictions.
The end goal of this process would be to enrich public KGs with the contradictions generated so that they can be used as benchmarks for a contradiction-aware learning task.

## Section 1 - Problem Definition

It is very common for large KGs, and in particular crowd-sourced KGs, to contain contradicting information due to the merging of information from different sources or collaborators with different world-views.
Yet, contradictions are often non-acknowledged, or simply "solved" by removal of one side.
This is due to the "majority-view" nature of most data collection and Machine Learning strategies, that solve contradictions by retaining the most relevant/popular one, in hopes that it is the most correct.
This perspective, however, is not necessarily the most realistic. Often, real world instances or concepts can in fact have multiple "real" facets that combined make up a complex "truth value".
E.g., "Marriage" is a real-world concept often characterized as being between two people. While this may be the majority view, at least in western countries, there are places and cultures where polygamy is in practice and marriage 
may be between one man and several women, or vice-versa. Therefore, a more realistic description of "Marriage" should include both properties, along with the context in which they are held true.


A major reason for the inexistence of actual contradiction learning benchmarks is the lack of consensus on what actual constitutes a contradiction within a domain knowledge graph.

Here contradictions are defined as two logically opposing statements for a common entity, as seen in the examples of the table below:

| Description Logic Formulae | Examples |
| ----------------------- | -----------------------------|
| (a ⊂ B) ⊓ (a ⊄ B) | Pizza  subClassOf  Food <br /> Pizza  NOT_subClassOf  Food |
| (B(a)) ⊓ (¬B(a)) |  Margherita hasTopping MozzarellaTopping <br /> Margherita NOT_hasIngredient Base <br /> hasBase subPropertyOf hasIngredient |
| (B(a)) ⊓ (¬C(a)) ⊓ (B ⊆ C) | Margherita nasBase PizzaBase <br /> Margherita NOT_hasIngredient Base <br /> hasBase subPropertyOf hasIngredient  |
| (B(a)) ⊓ (C(a)) ⊓ (B ⊥ C) | VegetarianPizza hasTopping onlyVegetables <br /> VegetarianPizza hasTopping Meat <br /> Meat disjoint onlyVegetables |
| (B(a,d)) ⊓ (B(a,e)) ⊓ Cards(a,d,B) = (0,1) | Portugal hasCapital Lisbon <br /> Portugal hasCapital Funchal <br /> hasCapital maxCardinality 1 |



These contradictions can be directly ( see example on row 1 of table above ) or indirectly logically detectable ( examples on rows 2 to 5 ). On the other hand, not all contradictions can be detected through logics alone.
For example, two statements may not contradict eachother within general knowledge but may be contradicting within a specific domain. On the other hand, there are "supposed" contradictions that, when given context (be it temporal, spatial, etc.) may not be contradicting. Therefore, the task of detecting contradictions is complex.

As seen in examples 1 to 3 of the Table above, the existence of both positive and negative statements can also result in contradictions as long as they are mutual negations (either direct or through logical inference).
Therefore, I also include datasets with negative statements in Section 2.
In cases where two datasets, one with exclusively positive statements and another with exclusively negative statements for common entities, contain data from the same domain, e.g. ConceptNet and Uncommonsense, it is possible to combine them into a single KG from which to derive the contradictions.
<br />

## Section 2 - Datasets

In the present section are listed a total of 9 datasets. Some contain directly negated statements/triples. Others do not include explicit negations but are known to contain contradicting statements.
The datasets will be used for a contradiction enrichment process where a neuro-symbolic method will detect the different types of existing contradictions, be it explicit or underlying,
and contextualize them with domain knowledge. Then, the enriched datasets will be used for a knowledge graph representation learning (KGRL) method to generate enriched contradiction-aware entity representations (a novel "contradiction learning" task).


| Dataset | Type | Domain | Language | Data Type | Year of Creation | Latest Update | # Entities | # Positive Triples * | # Negative Triples * | Download Link |
| ------------- | ------------- | ------------- |------------- | ------------- | ------------- | ------------- | ------------- | ------------- | ------------- | ------------- |
| wikidata  | structured KG  | Commonsense | Multilingual | Mixed (String/float/integer) | 29/10/2012 | 09/12/2024 | 114,682,266 | 15,019,727,427 | - | https://dumps.wikimedia.org/wikidatawiki/20241201/ |
| wikinegata  | structured KG  | Commonsense | English | Mixed (String/float/integer) | 2021 | 2021 | 600,000 | 100,000,000 | 681,000,000 | available per demand in https://d5demos.mpi-inf.mpg.de/negation/contact.html |
| ConceptNet 5.X  | unstructured KG  | Commonsense | Multilingual | Mixed (String/float/integer) | 03/11/2016 | 20/05/2020 | 300,000 | 1,600,000 | - | https://s3.amazonaws.com/conceptnet/downloads/2019/edges/conceptnet-assertions-5.7.0.csv.gz |
| Uncommonsense  | unstructured KG  | Commonsense | English | Mixed (String/float/integer) | 2022 | 2023 | 8,000 | - | 13,600,000 | https://uncommonsense.mpi-inf.mpg.de/download/#larger |
| NegatER  | unstructured KG  | Commonsense | English | String and Integer | 2022 | 2022 | 78,334 | 102,400 | 2,400 | see https://github.com/tsafavi/NegatER/tree/master/data/conceptnet/full |
| ATOMIC  | unstructured KG  | Commonsense | English | String and Integer | 2019 | 2022 | 309,515 | 877,108 | - | see https://huggingface.co/datasets/allenai/atomic |
| TrueWalks PPI  | structured KG  | Biomedical | English | String | 08/03/2023 | 08/03/2023 | 51,358 | 8,388 | 9,603 | https://zenodo.org/records/7709195/files/ppi-prediction.zip?download=1 |
| TrueWalks GDA  | structured KG  | Biomedical | English | String | 08/03/2023 | 08/03/2023 | 68,895 | 14,935 | 9,298 | https://zenodo.org/records/7709195/files/gda-prediction.zip?download=1 |
| TDC HuRI PPI  | PPI network data | Biomedical | N/A (STRING IDs) | String | 2020 | 2020 | 8,248 | 51,813 | 51,813 | see https://tdcommons.ai/multi_pred_tasks/ppi |

\* Does not include triples that pertain to links between ontology classes

<br />
<br />

### 2.1 - Commonsense KGs

This section covers the datasets of publicly-available commonsense Knowledge Graphs. Wikidata, ConceptNet and ATOMIC were collected via collaborative efforts, while the remainder were obtained from statistical inference methods over these KGs.

Large datasets obtained from collaborative efforts often have contradictions stemming from opposing views, beliefs and cultural habits.


### - wikidata [1]:

  The wikidata acts as the main storage for the structured data of Wikipedia.
  Each statement is composed of a **claim**, its **property-value** pair, its **references** and possible **qualifiers** (other property-value pairs that add context).
  Due to its crowd-sourced nature, it is known that Wikidata contains several contradicting statements that can be contextualized with qualifiers (e.g. see the examples <Jerusalem, CapitalOf, State of Palestine> and <Jerusalem, CapitalOf, Israel> with the qualifiers "statement disputed by" and "statement supported by" in https://www.wikidata.org/wiki/Q1218 ). The wikidata contains a total of 12,286 property types that serve as the predicate of a statement.

<br />

### -  wikinegata [2]:

  The wikinegata was obtained from a subset of wikidata along with a set of derived "useful" negative statements. Therefore, it also covers the majority of the property types in Wikidata, although the authors have not made the exact number available. To gain access to the dataset one must contact the authors through the corresponding weblink in the datasets' table.
  

<br />

### - ConceptNet 5.X [3]:

The Conceptnet is a KG that connects words and expressions of natural language through labeled edges to model general knowledge. It was constructed from expert-collected data, crowd-sourced data and through semi-automatic information retrieval methods. It contains a total of 34 relations with canonical English names but can apply to text in any language. The first version of the ConceptNet 5 was released in 2016. Since then it has periodically been update up to v5.8.

<br />
  
### - Uncommonsense [4]:

The Uncommonsense dataset was the first large dataset built with informative negative statements about everyday concepts through pruning and ranking of negatives by informativeness.

<br />

### - NegatER [5]:

The NegatER dataset was obtained from Language Model inference of negative statements over a subset of the ConceptNet KG. The dataset contains a total of 34 different types of relations and the authors provide data partitions of 100,000/2,400/2,400 train/validation/test triples (positives and negatives combined) for reproductibility of their experiments over the data.

<br />

### - ATOMIC [6]:

The ATOMIC dataset was created by the University of Washington using 877,000 textual descriptions of common concepts and events obtained from crowd sourced data. 
It contains inferential knowledge organized as "If-Then" premises with a total of nine different predicate/relation types.
  

<br />

<br />
   
### 2.2 - Biomedical KGs

This section covers biomedical datasets.


### - TrueWalks Protein-Protein Interaction (PPI)  [7]:
The PPI KG is composed of a PPI network with 440 proteins and its annotations to the Gene Ontology. The PPI network data contains 1,024 experimentally verified positive protein interactions and of 1,024 non-existent (negative) protein interactions, therefore it is a balanced dataset. By combining it with the ontology and with inferred positive (7,364 annotations) and negative statements (8,579 annotations) to it, the number of total entities is of 51,358 and 1,425,102 triples. The PPI network dataset does not contain entity features.


### - TrueWalks Gene-Disease Associations (GDA)  [7]:  
The GDA KG is composed of a Gene-Disease Association network with 755 genes and 162 diseases and of its annotations to the Human Phenotype Ontology (HP). The GDA network data contains 107 verified gene-disease relations and of 107 non-existent (negative) relations. By combining it with the ontology and with inferred positive (14,828 annotations) and negative statements (9,191 annotations) to it, the number of total entities is 68,895 and of 2,507,961 triples.
The GDA network dataset does not contain entity features.

<br />

### - TDC HuRI KG - on combining TDC's PPI dataset with Gene Ontology [8]:
The Protein-Protein Interaction dataset contains 8,248 proteins and 51,813 positive triples corresponding to experimentally tested physical interactions between proteins of the Human Interactome (HuRI data).
It also provides its own python package with an internal function for generating negative triples pertaining to experimentally-verified non-existent interactions between proteins.
To have a balanced dataset, I intend on generating 51,813 negative triples as well. The original dataset contains aminoacid sequence information as string-type protein features.

In previous experiments I have integrated the HuRI PPI data with the Gene Ontology (version 2020/06/01 - 44,266 active GO classes and 71,515 links) through data annotation to build a KG with a total number of 52,513 entities and 321,259 triples/statements.

The Gene Ontology and annotations files can be downloaded at https://release.geneontology.org/2020-06-01/ontology/go.owl and https://release.geneontology.org/2020-06-01/annotations/index.html, respectively.

<br />


## Section 3 - Limitations and Biases

In collaborative KGs the data is introduced and maintained by human collectors and editors who decide on the rules of content creation and management, which may not be the most appropriate. Some KGs are also updated through automated bots/web-scraping methods. There is therefore a possibility that some of the conflicting data may actually be due to one of the two statements being incorrect.

The combination of two different datasets, e.g. ConcepNet and Uncommonsense or Wikidata and Wikinegata, may introduce some difficulties in data integration if the data formats are not exactly the same. For example, the wikinegata does not provide references nor qualifiers. While qualifiers are not obligatory, the Wikidata KG's axiomatic schema requires that the each statement has at least one reference. Therefore, the introduction of wikinegata data with the wikidata as is could result in an assertion violation in wikidata.


<br />

## References
[1] Vrandečić, Denny, and Markus Krötzsch. "Wikidata: a free collaborative knowledgebase." Communications of the ACM 57.10 (2014): 78-85.

[2] Arnaout, Hiba, et al. "Wikinegata: a knowledge base with interesting negative statements." Proceedings of the VLDB Endowment 14.12 (2021): 2807-2810.

[3] Robyn Speer, Joshua Chin, and Catherine Havasi. 2017. "ConceptNet 5.5: An Open Multilingual Graph of General Knowledge." In proceedings of AAAI 31.

[4] Hiba Arnaout, Simon Razniewski, Gerhard Weikum, Jeff Z. Pan. UnCommonSense: Informative Negative Knowledge about Everyday Concepts. In CIKM, 2022.

[5] Safavi, Tara et al. “NegatER: Unsupervised Discovery of Negatives in Commonsense Knowledge Bases.” Conference on Empirical Methods in Natural Language Processing (2020).

[6] Sap, Maarten, et al. "Atomic: An atlas of machine commonsense for if-then reasoning." Proceedings of the AAAI conference on artificial intelligence. Vol. 33. No. 01. 2019.

[7] Sousa, Rita T., Sara Silva, and Catia Pesquita. "Benchmark datasets for biomedical knowledge graphs with negative statements." arXiv preprint arXiv:2307.11719 (2023).

[8] Luck, K., Kim, D., Lambourne, L. et al. A reference map of the human binary protein interactome. Nature 580, 402–408 (2020).
