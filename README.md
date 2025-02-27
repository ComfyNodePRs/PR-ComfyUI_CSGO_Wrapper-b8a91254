# ComfyUI_CSGO_Wrapper
You can using InstantX's CSGO in comfyUI

**CSGO From: [link](https://github.com/instantX-research/CSGO)**

**Notice**
* runway is runway，When using the SDXL monolithic model, errors may occur because the “runway” has deleted their model library. The solution is to upgrade to the latest version of diffusers or modify the diffuser code content. The modification method can be found in the link: [link](https://github.com/huggingface/diffusers/commit/d8a16635f47ac455abd61879bcc6be32dfeaa561)

1.Installation
-----
  In the ./ComfyUI /custom_node directory, run the following:   
```
git clone https://github.com/smthemex/ComfyUI_CSGO_Wrapper.git
```  
  
2.requirements  
----
For ComfyUI users, all libraries in the requirements file should be available. If not, please uncomment the # and reinstall
```
pip install -r requirements.txt
```
3 Need  model 
----
3.1 base SDXl ckpt      
```
├── ComfyUI/models/checkpoints/
|      ├──any SDXL weights #for example: Jumpernaut XL_v9-RunDiffusionPhoto_v2.safetensors
```
3.2 main ckpt      
CSGO models [link](https://huggingface.co/InstantX/CSGO/tree/main)
```
├── ComfyUI/models/checkpoints/
|      ├──acsgo_4_32.bin  #need token 4/32
|      ├──acsgo.bin   #need token 4/16
```
3.3 base vae   
```
├── ComfyUI/models/vae/
|      ├──any SDXL vae weights  #sdxl.vae.safetensors 
```
3.4 image encoder   
h94/IP-Adapter/sdxl_models [link](https://huggingface.co/h94/IP-Adapter/tree/main/sdxl_models/image_encoder)
```
├── any path dir/
|             ├── model.safetensors
|             ├── config.json
```
3.5 controlnet   
TTPlanet/TTPLanet_SDXL_Controlnet_Tile_Realistic [link](https://huggingface.co/TTPlanet/TTPLanet_SDXL_Controlnet_Tile_Realistic)
```
├── any path dir/
|             ├── diffusion_pytorch_model.safetensors  #rename from "TTPLANET_Controlnet_Tile_realistic_v2_fp16.safetensors"
|             ├── config.json
```
3.6 if using LLM  
Salesforce/blip-image-captioning-large  [link](https://huggingface.co/Salesforce/blip-image-captioning-large/tree/main)
```
├── any path dir/
|             ├── model.safetensors
|             ├── config.json
|             ├── preprocessor_config.json
|             ├── special_tokens_map.json
|             ├── tokenizer.json
|             ├── tokenizer_config.json
|             ├── vocab.txt
```
4 Example
----
![](https://github.com/smthemex/ComfyUI_CSGO_Wrapper/blob/main/example/exampleA.png)  
![](https://github.com/smthemex/ComfyUI_CSGO_Wrapper/blob/main/example/example.png)


5 Function Description of Nodes  
---
* content_tokens:  keep in 4;   
* style_tokens:   if using csgo.bin keep num "16",if using csgo_4_32.bin keep num  "32" ;  
* text_only: if not using content img ;    
* Blip is not necessary;  


6 Citation
------
CSGO
``` python  
@article{xing2024csgo,
       title={CSGO: Content-Style Composition in Text-to-Image Generation}, 
       author={Peng Xing and Haofan Wang and Yanpeng Sun and Qixun Wang and Xu Bai and Hao Ai and Renyuan Huang and Zechao Li},
       year={2024},
       journal = {arXiv 2408.16766},
}
}
```

