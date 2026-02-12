---
tags:
  - Depth_Estimation
---
Link: https://zju3dv.github.io/InfiniDepth/#pointcloud
Paper: https://arxiv.org/pdf/2601.03252



### Depth as Neural Implicit Fields
They  have extended the concept of [[Neural Implicit Fields]] which maps any 2d coordinate to a depth value conditioned on the input RGB image of a fixed resolution.$$d_{I}(x,y) = N_{\mathbb{\theta}}(I,(x,y))$$
They implemented this NIF model using a **Local Implicit Decoder**.  It has two modules:
- #### Feature Query:  
	- They use a VIT  encoder to capture Global information. 
	- This is followed by a **Reassemble Block** . They upsample shallow-layer features to higher resolutions.
	- They retain the deeper-layer features at their native(original resolution).
	- Constructed feature pyramid of form: $\{f^k\}^L_{k=1}$  where $f^k\in \mathbb{R}^{h_{k}*w_{k}*C^k}$
		- Output of each $f^k$ is a **feature map** of the original image.
		
	- ##### **Continuous Position Query**:
		-  $(x, y)$ in an image of size $W \times H$, the model first scales that coordinate to match the specific dimensions of each layer in the feature pyramid $(h_k, w_k)$:$$(x_k, y_k) = \left( x \cdot \frac{w_k}{W}, y \cdot \frac{h_k}{H} \right)$$
		- Because $(x_k, y_k)$ will almost never be a perfect integer (e.g., it might be $112.4$), the model looks at the **four nearest pixels** in that feature map. This is defined as the neighborhood $\mathcal{N}_k$: $$\mathcal{N}_k(x_k, y_k) = \{ (i, j) \mid i \in \{\lfloor x_k \rfloor, \lfloor x_k \rfloor + 1 \}, j \in \{\lfloor y_k \rfloor, \lfloor y_k \rfloor + 1 \} \}$$
	- **Bilinear Interpolation**: Now instead of taking closer of the 4 pixels, we take the bilinear interpolation between them. This gives us a single value per feature map at scale k per query (x,y). $$f^k_{(x,y)} \in \mathbb{R}^{1 \times C^k}$$
- #### Depth Decoding: 
	- 