# text_to_video_synthesis
This model is based on a multi-stage text-to-video generation diffusion model, which inputs a description text and returns a video that matches the text description. Only English input is supported.
## Model Description
The text-to-video generation diffusion model consists of three sub-networks: text feature extraction, text feature-to-video latent space diffusion model, and video latent space to video visual space. The overall model parameters are about 1.7 billion. Support English input. The diffusion model adopts the Unet3D structure, and realizes the function of video generation through the iterative denoising process from the pure Gaussian noise video.
## How to expect the model to be used and where it is applicable
This model has a wide range of applications and can reason and generate videos based on arbitrary English text descriptions. 
## How to use
This model currently only supports inference on the GPU. This demo requires about 16GB CPU RAM and 16GB GPU RAM. Under the ModelScope framework, the current model can be used by calling a simple Pipeline, where the input must be in dictionary format, the legal key value is 'text', and the content is a short text. 
