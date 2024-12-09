# Knowledge Graphs with Contradictions

Collection of relevant datasets on public knowledge graphs with contradicting information.
Here contradictions are defined as two directly opposing statements for a common entity, e.g.:
- Entity a InstanceOf Class A, Entity b InstanceOf Class B,  < Entity a, has_child, Entity b >,  < Entity a, has_parent, Entity b > ;
- Entity a InstanceOf Class A, Entity b InstanceOf Class B, Entity c InstanceOf Class C,  < Entity a, has_child, Entity b >,  < Entity c, has_child, Entity b > , Class A IsDisjointWith Class B ;


## Datasets

- wikidata [1] + wikinegata [2]:

- ConceptNet [3]:
#negations: 6.2 millions
#subjects: 8k everyday concepts

- Negative BioKGs [4]:

    PPI prediction;
    GDA prediction;
    disease prediction;

- TDC's PPI dataset [5]

## References
[1] Vrandečić, Denny, and Markus Krötzsch. "Wikidata: a free collaborative knowledgebase." Communications of the ACM 57.10 (2014): 78-85.
[2] Arnaout, Hiba, et al. "Wikinegata: a knowledge base with interesting negative statements." Proceedings of the VLDB Endowment 14.12 (2021): 2807-2810.
[3] Hiba Arnaout, Simon Razniewski, Gerhard Weikum, Jeff Z. Pan. UnCommonSense: Informative Negative Knowledge about Everyday Concepts. In CIKM, 2022.
[4] Sousa, Rita T., Sara Silva, and Catia Pesquita. "Benchmark datasets for biomedical knowledge graphs with negative statements." arXiv preprint arXiv:2307.11719 (2023).
[5] Luck, K., Kim, D., Lambourne, L. et al. A reference map of the human binary protein interactome. Nature 580, 402–408 (2020).
