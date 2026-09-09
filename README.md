# Projects

This is an overview of past and current major projects. 

## SIMULTAN

This project was developed over the course of 11 years by an interdisciplinary team of software and civil engineers at the [TU Wien](https://www.tuwien.at/cee/mbb/bph) under the lead of [Prof. Thomas Bednar](https://tiss.tuwien.ac.at/person/37331.html).

<picture>
  <source media="(prefers-color-scheme: dark)" srcset="/assets/images/Simultan_dark.png">
  <source media="(prefers-color-scheme: light)" srcset="/assets/images/Simultan_light.png">
  <img alt="SIMULTAN" src="default-image.png">
</picture>

[Data model repository on GitLab](https://gitlab.tuwien.ac.at/simultangroup/SIMULTAN)

[Data model repository on GitHub](https://github.com/bph-tuwien/SIMULTAN)

[Data model documentation](https://github.com/bph-tuwien/SIMULTAN.Documentation/wiki)

It was initially funded by the [Austrian Research Promotion Agency (FFG)](https://www.ffg.at/en); later it was further developed in close cooperation with multiple partners from the Architecture, Engineering and Construction (AEC) industry.

## Procedural Shape Contraction

![Overview of PSC](./assets/images/PSC_Overview.png)

This project demonstrates a method for integrating 2d construction documentation-level architectural details into a 3d conceptual model of a building, which transforms it into a detailed surface model.  The goal is to generate geometry that can be built in the designated material using the appropriate standardized techniques. The workflow consists of the following steps:

1. Each 2d detail is subjected to manual 1d feature extraction to determine those shapes that have an influence on the final 3d model.
2. The sharp features of the 3d model are extracted to obtain the building’s 3d skeleton, consisting of edge curves and corners.
3. We align the feature collection obtained from each detail with the 3d skeleton, in accordance with the architectural design. The goal is to build a 2-manifold with a boundary at each corner of the 3d skeleton.
4. Spanning ruled surfaces between neighbouring corner manifolds completes the final surface model.

This project focuses on the algorithm for constructing the corner manifolds: After the alignment of the feature collections with the 3d skeleton is performed, we calculate a rich descriptor, based on geometric relationship functions, for each feature. In addition, we construct its adjacency graph, containing all other features whose descriptor will change in case this feature is discarded. We then apply simultaneous procedural contraction to all feature collections affecting the same corner of the 3d model. In each step a preservation score is calculated for all features, based on their descriptors. The feature with the lowest score is discarded and the descriptors and adjacency graphs for all others recalculated. This contraction produces ruled surface segments that are eventually stitched together into a 2-manifold with a boundary. The algorithm evaluation was performed by building a prototype in MatLab and testing it on 170 detail combinations.

[The work was published as a master thesis at TU Wien](https://repositum.tuwien.at/handle/20.500.12708/158223)
