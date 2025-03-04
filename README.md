# Usage

```python
model = AutoModelForCausalLM.from_pretrained("ragavsachdeva/magiv3", torch_dtype=torch.float16, trust_remote_code=True).cuda().eval()
processor = AutoProcessor.from_pretrained("ragavsachdeva/magiv3", trust_remote_code=True)

model.predict_detections_and_associations(images, processor)
model.predict_ocr(images, processor)
model.predict_character_grounding(images, captions, processor)

```
