---
language:
- en
tags:
- Manga
- Object Detection
- OCR
- Character Grounding
- Panel Captioning
- Image-Text-to-Text
---
<style>
  .title-container {
    display: flex;
    flex-direction: column; /* Stack elements vertically */
    justify-content: center;
    align-items: center;
  }
  
  .title {
    font-size: 2em;
    text-align: center;
    color: #333;
    font-family: 'Comic Sans MS', cursive; /* Use Comic Sans MS font */
    text-transform: uppercase;
    letter-spacing: 0.1em;
    padding: 0.5em 0 0.2em;
    background: transparent;
  }
  
  .title span {
    background: -webkit-linear-gradient(45deg, #6495ED, #4169E1); /* Blue gradient */
    -webkit-background-clip: text;
    -webkit-text-fill-color: transparent;
  }

  .subheading {
    font-size: 1.5em; /* Adjust the size as needed */
    text-align: center;
    color: #555; /* Adjust the color as needed */
    font-family: 'Comic Sans MS', cursive; /* Use Comic Sans MS font */
  }

  .authors {
    font-size: 1em; /* Adjust the size as needed */
    text-align: center;
    color: #777; /* Adjust the color as needed */
    font-family: 'Comic Sans MS', cursive; /* Use Comic Sans MS font */
    padding-top: 1em;
  }

  .affil {
    font-size: 1em; /* Adjust the size as needed */
    text-align: center;
    color: #777; /* Adjust the color as needed */
    font-family: 'Comic Sans MS', cursive; /* Use Comic Sans MS font */
  }

</style>

<div class="title-container">
  <div class="title">
    From <span>Panels</span> to <span>Prose</span>
  </div>
  <div class="subheading">
    Generating Literary Narratives from Comics
  </div>
  <div class="authors">
    Ragav Sachdeva and Andrew Zisserman
  </div>
  <div class="affil">
    University of Oxford
  </div>
  <div style="display: flex;">
    <a href="https://arxiv.org/abs/2503.23344"><img alt="Static Badge" src="https://img.shields.io/badge/arXiv-2503.23344-blue"></a>
    &emsp;
    <img alt="Dynamic JSON Badge" src="https://img.shields.io/badge/dynamic/json?url=https%3A%2F%2Fhuggingface.co%2Fapi%2Fmodels%2Fragavsachdeva%2Fmagiv3%3Fexpand%255B%255D%3Ddownloads%26expand%255B%255D%3DdownloadsAllTime&query=%24.downloadsAllTime&label=%F0%9F%A4%97%20Downloads">
  </div>
</div>

<!-- Optional: add a teaser image for v3 here, e.g.
![image/png](https://cdn-uploads.huggingface.co/.../your_magiv3_teaser.png)
-->

Magiv3 is a unified vision-language model for comic understanding. Given an image and a task prompt, it autoregressively produces text-only outputs for a range of tasks: localising panels, characters, texts and speech-bubble tails, performing OCR, and grounding characters referenced in a caption to their locations in the panel.

# Usage
```python
model = AutoModelForCausalLM.from_pretrained("ragavsachdeva/magiv3", torch_dtype=torch.float16, trust_remote_code=True).cuda().eval()
processor = AutoProcessor.from_pretrained("ragavsachdeva/magiv3", trust_remote_code=True)

model.predict_detections_and_associations(images, processor)
model.predict_ocr(images, processor)
model.predict_character_grounding(images, captions, processor)
```

# License and Citation
The provided model and datasets are available for unrestricted use in personal, research, non-commercial, and not-for-profit endeavors. For any other usage scenarios, kindly contact me via email, providing a detailed description of your requirements, to establish a tailored licensing arrangement. My contact information can be found on my website: ragavsachdeva [dot] github [dot] io

```
@InProceedings{Sachdeva25,
      title={From Panels to Prose: Generating Literary Narratives from Comics},
      author={Ragav Sachdeva and Andrew Zisserman},
      booktitle={IEEE International Conference on Computer Vision (ICCV)},
      year={2025},
      eprint={2503.23344},
      archivePrefix={arXiv},
      primaryClass={cs.CV},
      url={https://arxiv.org/abs/2503.23344}
}
```