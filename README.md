# Knowledge Graphs with Contradictions

Collection of relevant datasets for building knowledge graphs (KGs) with contradicting information.
Here contradictions are defined as two directly opposing statements for a common entity, e.g.:
- a) Entity a InstanceOf Class A, Entity b InstanceOf Class B,  < Entity a, has_child, Entity b >,  < Entity a, has_parent, Entity b > ;
- b) Entity a InstanceOf Class A, Entity b InstanceOf Class B, Entity c InstanceOf Class C,  < Entity a, has_child, Entity b >,  < Entity c, has_child, Entity b > , Class A IsDisjointWith Class B ;

These contradictions can be directly ( a) ) or indirectly logically detectable ( b) ).

## Section 1 - Tasks
The PhD project sees the development of an approach able to detect contradicting statements within a KG to then produce conflict-aware KG representations for use in downstream tasks.
One of the major difficulties of evaluating a graph-based model on the task of contradiction detection over knowledge graphs is the near inexistence of benchmark datasets with contradictions.
Therefore, a first step to allow evaluation over this task is the construction of datasets for KGs with contradictions.
As such, in "Section 2 - Datasets", I present several public datasets and propose the combination of those derived from the same data sources to generate logical contradictions.
The end goal of this process would be to enrich public KGs with the contradictions generated.


## Section 2 - Datasets

### 2.1 - Commonsense KGs
- wikidata [1] + wikinegata [2]:

- ConceptNet [3] + Uncommonsense [4]: non-structured knowledge graphs on commonsense
#negations: 6.2 millions
#subjects: 8k everyday concepts



### 2.2 - Biomedical KGs

- Negative BioKGs [5]:

    PPI prediction;
    GDA prediction;
    disease prediction;

- TDC's PPI dataset [6]

  

## References
[1] Vrandečić, Denny, and Markus Krötzsch. "Wikidata: a free collaborative knowledgebase." Communications of the ACM 57.10 (2014): 78-85.
[2] Arnaout, Hiba, et al. "Wikinegata: a knowledge base with interesting negative statements." Proceedings of the VLDB Endowment 14.12 (2021): 2807-2810.
[3] Robyn Speer, Joshua Chin, and Catherine Havasi. 2017. "ConceptNet 5.5: An Open Multilingual Graph of General Knowledge." In proceedings of AAAI 31.
[4] Hiba Arnaout, Simon Razniewski, Gerhard Weikum, Jeff Z. Pan. UnCommonSense: Informative Negative Knowledge about Everyday Concepts. In CIKM, 2022.
[5] Sousa, Rita T., Sara Silva, and Catia Pesquita. "Benchmark datasets for biomedical knowledge graphs with negative statements." arXiv preprint arXiv:2307.11719 (2023).
[6] Luck, K., Kim, D., Lambourne, L. et al. A reference map of the human binary protein interactome. Nature 580, 402–408 (2020).
