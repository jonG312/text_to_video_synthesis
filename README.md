# text_to_video_synthesis
This model is based on a multi-stage text-to-video generation diffusion model, which inputs a description text and returns a video that matches the text description. Only English input is supported.
## Model Description
The text-to-video generation diffusion model consists of three sub-networks: text feature extraction, text feature-to-video latent space diffusion model, and video latent space to video visual space. The overall model parameters are about 1.7 billion. Support English input. The diffusion model adopts the Unet3D structure, and realizes the function of video generation through the iterative denoising process from the pure Gaussian noise video.
## How to expect the model to be used and where it is applicable
This model has a wide range of applications and can reason and generate videos based on arbitrary English text descriptions. 
## How to use
This model currently only supports inference on the GPU. This demo requires about 16GB CPU RAM and 16GB GPU RAM. Under the ModelScope framework, the current model can be used by calling a simple Pipeline, where the input must be in dictionary format, the legal key value is 'text', and the content is a short text. 
## Operating environment
pip install modelscope==1.4.2
pip install open_clip_torch
pip install pytorch-lightning
## Code example
from modelscope.pipelines import pipeline
from modelscope.outputs import OutputKeys

p = pipeline('text-to-video-synthesis', 'damo/text-to-video-synthesis')
test_text = {
        'text': 'A panda eating bamboo on a rock.',
    }
output_video_path = p(test_text, output_video='./output.mp4')[OutputKeys.OUTPUT_VIDEO]
print('output_video_path:', output_video_path)
## View Results
The above code will display the save path of the output mp4 video, and the current encoding format can be played normally with VLC player. Some other media players may not view it normally.
## Model limitations and biases
- The model is trained based on public data sets such as Webvid, and the generated results may have deviations related to the distribution of training data.
- This model cannot achieve perfect film and television quality generation.
- The model cannot generate clear text.
- The model is mainly trained with English corpus and does not support other languages ​​at the moment**.
- The performance of this model needs to be improved on complex compositional generation tasks.
## isuse, Malicious Use and Excessive Use
- The model can only be used for non-commercial purposes. The model is meant for research purposes.
- The model was not trained to realistically represent people or events, so using it to generate such content is beyond the model's capabilities.
- It is prohibited to generate content that is demeaning or harmful to people or their environment, culture, religion, etc.
- Prohibited for pornographic, violent and bloody content generation.
- Prohibited for error and false information generation.
## Training data
The training data includes LAION5B, ImageNet, Webvid and other public datasets. Image and video filtering is performed after pre-training such as aesthetic score, watermark score, and deduplication.
