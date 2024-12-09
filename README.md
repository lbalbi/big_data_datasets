# Knowledge Graphs with Contradictions

Collection of relevant datasets on public knowledge graphs with contradicting information.
Here contradictions are defined as two directly opposing statements for a common entity, e.g.:
- Entity a InstanceOf Class A, Entity b InstanceOf Class B,  < Entity a, has_child, Entity b >,  < Entity a, has_parent, Entity b > ;
- Entity a InstanceOf Class A, Entity b InstanceOf Class B, Entity c InstanceOf Class C,  < Entity a, has_child, Entity b >,  < Entity c, has_child, Entity b > , Class A IsDisjointWith Class B ;


## Datasets

- wikidata + wikinegata

- ConceptNet

- Negative BioKGs:
    PPI prediction;
    GDA prediction;
    disease prediction;
