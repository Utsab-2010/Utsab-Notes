---
tags:
  - Depth_Estimation
---
Link: https://zju3dv.github.io/InfiniDepth/#pointcloud
Paper: https://arxiv.org/pdf/2601.03252



### Depth as Neural Implicit Fields
They  have extended the concept of [[Neural Implicit Fields]] which maps any 2d coordinate to a depth value conditioned on the input RGB image of a fixed resolution.$$d_{I}(x,y) = N_{\mathbb{\theta}}(I,(x,y))$$
They implemented this NIF model using a **Local Implicit Decoder**.  It has two modules:
- Feature Query:  They use a VIT  encoder to capture Global information. 
	- This is followed by a **Reassemble Block** . They upsample shallow-layer features to higher resolutions.
	- They retain the deeper-layer features at their native(original resolution).
	- Constructed feature pyramid of form: $\{f^k\}^L_{k=1}$  where $f^k\in \mathbb{R}^{h_{k}*w_{k}*C^k}$
	- **Continuous Position Query**:
		- (x)