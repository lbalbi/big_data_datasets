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




These contradictions can be directly ( see example on row 1 of table above ) or indirectly logically detectable ( examples on rows 2 to 5 ).

As seen in examples 1 to 3 of the Table above, the existence of both positive and negative statements can also result in contradictions as long as they are mutual negations (either direct or through logical inference).
Therefore, I also include datasets with negative statements in Section 2.
In cases where two datasets, one with exclusively positive statements and another with exclusively negative statements for common entities, contain data from the same domain, e.g. ConceptNet and Uncommonsense, it is possible to combine them into a single KG from which to derive the contradictions.
<br />

## Section 2 - Datasets

I present a total of 10 datasets with either opposing or directly negated statements/triples.


| Dataset | Type | Domain | # Entities | # Positive Triples | # Negative Triples | Download Link |
| ------------- | ------------- | ------------- | ------------- | ------------- | ------------- | ------------- |
| wikidata  | structured KG  | Commonsense | 114,682,266 |  | | https://dumps.wikimedia.org/wikidatawiki/20241201/ |
| wikinegata  | structured KG  | Commonsense | | 100 million | 681 million | available per demand in https://d5demos.mpi-inf.mpg.de/negation/contact.html |
| ConceptNet  | unstructured KG  | Commonsense | | | | https://s3.amazonaws.com/conceptnet/downloads/2019/edges/conceptnet-assertions-5.7.0.csv.gz |
| Uncommonsense  | unstructured KG  | Commonsense | 8,000 | - | 13.6 million | https://uncommonsense.mpi-inf.mpg.de/download/#larger |
| NegatER  | unstructured KG  | Commonsense | | | | see https://github.com/tsafavi/NegatER/tree/master/data/conceptnet/full |
| ATOMIC  | unstructured KG  | Commonsense | | | | see https://huggingface.co/datasets/allenai/atomic |
| TrueWalks PPI  | structured KG  | Biomedical | | | | https://zenodo.org/records/7709195/files/ppi-prediction.zip?download=1 |
| TrueWalks GDA  | structured KG  | Biomedical | | | | https://zenodo.org/records/7709195/files/gda-prediction.zip?download=1 |
| TrueWalks PDA  | structured KG  | Biomedical | | | | https://zenodo.org/records/7709195/files/disease-prediction.zip?download=1 |
| TDC PPI  | PPI network data | Biomedical | 8,248 | 51,813 | 51,813 | see https://tdcommons.ai/multi_pred_tasks/ppi |
<br />
<br />

### 2.1 - Commonsense KGs

This section covers the datasets of publicly-available commonsense Knowledge Graphs. Wikidata, ConceptNet and ATOMIC were collected via collaborative efforts, while the remainder were obtained from statistical inference methods over these KGs.
Large datasets obtained from collaborative 


### - wikidata [1]:
  The wikidata acts as the main storage for the structured data of Wikipedia.
  

### -  wikinegata [2]:
  The wikinegata was obtained from a subset of wikidata along with a set of derived "useful" negative statements.


### - ConceptNet [3]:
negative statements make up only 3% of examples in the ConceptNet knowledge graph

  
### - ConceptNet + Uncommonsense [4]:

  Uncommonsense covers 8,000 entities and 6.2 millions of negative statements.


### - NegatER [5]:



### - ATOMIC [6]:

  The dataset was created by the University of Washington using crowd sourced data.
  

<br />

<br />
   
### 2.2 - Biomedical KGs

This section covers biomedical datasets.


### - TrueWalks Protein-Protein Interaction (PPI)  [7]:


### - TrueWalks Gene-Disease Associations (GDA)  [7]:  


### - TrueWalks Patient-Disease Association (PDA)  [7]:  




### - HuRI KG - on combining TDC's PPI dataset with Gene Ontology [8]:
The Protein-Protein Interaction dataset contains 8,248 proteins and 51,813 positive triples corresponding to experimentally tested physical interactions between proteins of the Human Interactome (HuRI data).
It also provides its own python package with an internal function for generating negative triples pertaining to experimentally-verified non-existent interactions between proteins.
To have a balanced dataset, I intend on generating 51,813 negative triples as well.

Furthermore, by integrating the HuRI PPI data with the Gene Ontology (current version - 2024/11/03 - 62,046 GO classes) through data annotation, we build a KG with a total number of entities of 70,294 and XXXX triples/statements. 

51,813 + 51,813 + 

The Gene Ontology and annotations files can be downloaded at https://geneontology.org/docs/download-ontology/ and https://current.geneontology.org/products/pages/downloads.html, respectively.

<br />


## Section 3 - Limitations and Biases

Collaborative KGs - The data is introduced and maintained by human collectors and editors who decide on the rules of content creation and management, which may not be the most appropriate. Some KGs are also updated through automated bots/web-scraping methods. There is therefore a possibility that some of the conflicting data may actually be due to one of the two statements being incorrect.


<br />

## References
[1] Vrandečić, Denny, and Markus Krötzsch. "Wikidata: a free collaborative knowledgebase." Communications of the ACM 57.10 (2014): 78-85.

[2] Arnaout, Hiba, et al. "Wikinegata: a knowledge base with interesting negative statements." Proceedings of the VLDB Endowment 14.12 (2021): 2807-2810.

[3] Robyn Speer, Joshua Chin, and Catherine Havasi. 2017. "ConceptNet 5.5: An Open Multilingual Graph of General Knowledge." In proceedings of AAAI 31.

[4] Hiba Arnaout, Simon Razniewski, Gerhard Weikum, Jeff Z. Pan. UnCommonSense: Informative Negative Knowledge about Everyday Concepts. In CIKM, 2022.

[5] Safavi, Tara et al. “NegatER: Unsupervised Discovery of Negatives in Commonsense Knowledge Bases.” Conference on Empirical Methods in Natural Language Processing (2020).

[6] Jiang, Liwei, et al. "" I'm Not Mad": Commonsense Implications of Negation and Contradiction." arXiv preprint arXiv:2104.06511 (2021).

[7] Sousa, Rita T., Sara Silva, and Catia Pesquita. "Benchmark datasets for biomedical knowledge graphs with negative statements." arXiv preprint arXiv:2307.11719 (2023).

[8] Luck, K., Kim, D., Lambourne, L. et al. A reference map of the human binary protein interactome. Nature 580, 402–408 (2020).
