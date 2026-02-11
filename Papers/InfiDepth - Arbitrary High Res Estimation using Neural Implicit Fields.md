---
tags:
  - Depth_Estimation
---
Link: https://zju3dv.github.io/InfiniDepth/#pointcloud
Paper: https://arxiv.org/pdf/2601.03252



### Depth as Neural Implicit Fields
They  have extended the concept of [[Neural Implicit Fields]] which maps any 2d coordinate to a depth value conditioned on the input RGB image of a fixed resolution.$$d_{I}(x,y) = N_{\mathbb{\theta}}(I,(x,y))$$
They implemented this NIF model using a **Local Implicit Decoder**.  It has two modules:
- Feature Query: 