# Knowledge Graphs with Contradictions

Collection of relevant datasets for building knowledge graphs (KGs) with contradicting information.

The PhD project sees the development of an approach able to detect contradicting statements within a KG to then produce conflict-aware KG representations for use in downstream tasks.
One of the major difficulties of evaluating a graph-based model on the task of contradiction detection over knowledge graphs is the near inexistence of benchmark datasets with contradictions.
Therefore, a first step to allow evaluation over this task is the construction of datasets for KGs with contradictions.   

As such, in "Section 2 - Datasets", I present several public datasets, the majority being of KGs, to potentially be used in my work.
Some, of the same domain and data sources, may even be combined to generate logical contradictions.
The end goal of this process would be to enrich public KGs with the contradictions generated so that they can be used as benchmarks for a contradiction-aware learning task.

## Section 1 - Problem Definition

It is very common for large KGs, and in particular crowd-sourced KGs, to contain contradicting information due to the merging of information from different sources or collaborators with different world-views.
Yet, contradictions are often non-acknowledged, or simply "solved" by removal of one side.
This is due to the "majority-view" nature of most data collection and Machine Learning strategies, that solve contradictions by retaining the most relevant/popular one, in hopes that it is the most correct.
This perspective, however, is not necessarily the most realistic. Often, real world instances or concepts can in fact have multiple "real" facets that combined make up a complex "truth value".
E.g., "Marriage" is a real-world concept often characterized as being between two people. While this may be the majority view, at least in western countries, there are places and cultures where polygamy is in practice and marriage 
may be between one man and several women, or vice-versa. Therefore, a more realistic description of "Marriage" should include both properties, along with the context they are held true in.


A major reason for the inexistence of actual contradiction learning benchmarks is the lack of consensus on what actual constitutes a contradiction within a domain knowledge graph.

Here contradictions are defined as two directly opposing statements for a common entity, e.g.:

| Description Logic Formulae | Examples |
| ----------------------- | -----------------------------|
| (a ⊂ B) ⊓ (a ⊄ B) | Pizza  subClassOf  Food;
Pizza  NOT_subClassOf  Food |
| (B(a)) ⊓ (¬B(a)) |  |
|  |  |
|  |  |
|  |  |




These contradictions can be directly ( a) ) or indirectly logically detectable ( b) ).

Negative statements can also contribute to the existence of contradictions as long as they are a negation (through logical inferrence) of any other positive statement.
Therefore, I also include datasets with negative statements in Section 2.
     

## Section 2 - Datasets

I present a total of 10 datasets with either opposing or directly negated statements.
The datasets of wikidata, ConceptNet and ATOMIC were collected via collaborative efforts.



| Dataset | Type | Domain | # Entities | # Positive Triples | # Negative Triples | Download Link |
| ------------- | ------------- | ------------- | ------------- | ------------- | ------------- | ------------- |
| wikidata  | structured KG  | Commonsense | 114,682,266 |  | | https://dumps.wikimedia.org/wikidatawiki/20241201/ |
| wikinegata  | structured KG  | Commonsense | | 100 million | 681 million | |
| ConceptNet  | unstructured KG  | Commonsense | | | | |
| Uncommonsense  | unstructured KG  | Commonsense | 8,000 | - | 13.6 million | https://uncommonsense.mpi-inf.mpg.de/download/#larger |
| NegatER  | unstructured KG  | Commonsense | | | | |
| ATOMIC  | unstructured KG  | Commonsense | | | | see https://huggingface.co/datasets/allenai/atomic |
| TrueWalks PPI  | structured KG  | Biomedical | | | | https://zenodo.org/records/7709195/files/ppi-prediction.zip?download=1 |
| TrueWalks GDA  | structured KG  | Biomedical | | | | https://zenodo.org/records/7709195/files/gda-prediction.zip?download=1 |
| TrueWalks PDA  | structured KG  | Biomedical | | | | https://zenodo.org/records/7709195/files/disease-prediction.zip?download=1 |
| TDC PPI  | PPI network data | Biomedical | 8,248 | 51,813 | 51,813 | see https://tdcommons.ai/multi_pred_tasks/ppi |


### 2.1 - Commonsense KGs

### - wikidata [1]:
  The wikidata acts as the main storage for the structured data of Wikipedia.
  The latest version (as of 11/12/2024) of the KG contains 114,682,266 entities and over 1.5B triples/ statements.

### -  wikinegata [2]:
  The wikinegata was obtained from a subset of wikidata along with a set of derived "useful" negative statements. It contains 681 million negative and 100 million positive statements


### - ConceptNet [3]:


  
### - ConceptNet + Uncommonsense [4]:

  Uncommonsense covers 8,000 entities and 6.2 millions of negative statements.


### - NegatER [5]:



### - ATOMIC [6]:

  The dataset was created by the University of Washington using crowd sourced data.
  


   
### 2.2 - Biomedical KGs

### - Negative BioKGs from TrueWalks [7]:

  Protein-Protein Interaction (PPI) dataset;
       - 
  
  Gene-Disease Associations (GDA) dataset;
       -
  
  Patient-Disease Association (PDA) dataset;
       -

### - KG on combining TDC's PPI dataset with Gene Ontology [8]:
The PPI dataset contains 8,248 proteins and 51,813 positive and negative triples. When integrated with the Gene Ontology, the total number of entities is YYYY and the number of facts is XXXX.

   
### Limitations and Biases
Collaborative KGs - Data is entered and maintained by editors who decide on the rules of content creation and management. Automated bots/web-scraping methods also enter data.
 negative statements make up only 3% of examples in the ConceptNet knowledge graph



## References
[1] Vrandečić, Denny, and Markus Krötzsch. "Wikidata: a free collaborative knowledgebase." Communications of the ACM 57.10 (2014): 78-85.

[2] Arnaout, Hiba, et al. "Wikinegata: a knowledge base with interesting negative statements." Proceedings of the VLDB Endowment 14.12 (2021): 2807-2810.

[3] Robyn Speer, Joshua Chin, and Catherine Havasi. 2017. "ConceptNet 5.5: An Open Multilingual Graph of General Knowledge." In proceedings of AAAI 31.

[4] Hiba Arnaout, Simon Razniewski, Gerhard Weikum, Jeff Z. Pan. UnCommonSense: Informative Negative Knowledge about Everyday Concepts. In CIKM, 2022.

[5] Safavi, Tara et al. “NegatER: Unsupervised Discovery of Negatives in Commonsense Knowledge Bases.” Conference on Empirical Methods in Natural Language Processing (2020).

[6] Jiang, Liwei, et al. "" I'm Not Mad": Commonsense Implications of Negation and Contradiction." arXiv preprint arXiv:2104.06511 (2021).

[7] Sousa, Rita T., Sara Silva, and Catia Pesquita. "Benchmark datasets for biomedical knowledge graphs with negative statements." arXiv preprint arXiv:2307.11719 (2023).

[8] Luck, K., Kim, D., Lambourne, L. et al. A reference map of the human binary protein interactome. Nature 580, 402–408 (2020).
