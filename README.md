# SEER: Enhancing Multimodal Action Grounding with Semantic UI Parsing

## Overview

**SEER** (Semantic Extraction for Enhanced Reasoning) enhances GPT-4V's capability to interact with graphical user interfaces (GUIs) by extracting semantic meanings from UI elements and identifying interactable regions. This enables region-grounded actions, making multimodal environments more intuitive and interactive.

SEER pushes the boundaries of multimodal AI by combining vision-based UI parsing and advanced machine learning techniques to create structured, actionable insights from GUI screenshots.

---

## Features

- **Semantic Parsing**: Extracts UI elements' semantic meanings, categorizing buttons, icons, and text regions.  
- **Interactive Region Detection**: Accurately identifies clickable or interactable regions.  
- **Local Semantics Integration**: Enriches region data with descriptive functionality to improve context comprehension.  
- **Region-Grounded Actions**: Enables action generation contextualized to GUI regions.  
- **Gradio Demo**: Provides an interactive interface for testing SEER's capabilities.  

---

## Methodology Highlights

SEER is designed to decompose complex tasks into structured steps, leveraging multiple components to alleviate computational burdens on GPT-4V and enhance decision-making accuracy.

### 1. **Screen Parsing**

SEER integrates outputs from three key components to produce a structured, DOM-like representation of the UI, overlayed with bounding boxes for interactable elements:
- **Finetuned Interactable Icon Detection Model**
- **Finetuned Icon Description Model**
- **OCR Module**

This parsing process simplifies GPT-4V's tasks by focusing on semantic and functional information extraction.

### 2. **Interactable Region Detection**

Identifying interactable regions is a foundational step:
- A custom dataset of **67k UI screenshots** was curated, with bounding boxes derived from DOM trees of public web pages.  
- Bounding boxes from interactable region detection and OCR modules are merged while minimizing overlaps (overlap threshold > 90%).  
- Each region is assigned a unique ID to facilitate precise action mapping.  

### 3. **Local Semantics of Functionality**

To improve understanding of UI elements:
- A dataset of **7k icon-description pairs** was curated using GPT-4o and used to finetune a BLIP-v2 model.  
- This finetuned model generates accurate descriptions of icon functionality.  
- The descriptions and detected texts are integrated into prompts alongside the UI screenshot.  

By incorporating local semantics, SEER addresses limitations in GPT-4V's ability to simultaneously identify semantic information and predict actions. This integration significantly enhances its performance in multimodal tasks.

---

## Installation

1. **Create and activate the Python environment:**
   ```bash
   conda create -n "seer" python=3.12
   conda activate seer
   pip install -r requirements.txt
   ```

2. **Download pre-trained model checkpoints:**  
   Access models from [HuggingFace](https://huggingface.co/strikerhell/SEER-model) and place them in the appropriate directories:  
   - `weights/icon_detect/`  
   - `weights/icon_caption_florence/`  
   - `weights/icon_caption_blip2/`

3. **Convert safetensor files to PyTorch format:**  
   ```bash
   python weights/convert_safetensor_to_pt.py
   ```

---

## Usage

### Run Gradio Demo

Test SEER's capabilities with the Gradio-powered demo:
```bash
python gradio_demo.py
```

### Example Notebook

Explore SEER with sample use cases provided in `demo.ipynb`.

---

## Project Details

### Pipeline Components

- **UI Parsing Model**: Decomposes screenshots into actionable semantic data.
- **Interactive Region Detection**: Recognizes clickable and functional UI areas.
- **Action Grounding Framework**: Maps detected actions to the corresponding GUI elements.
- **Local Semantics Integration**: Enriches UI parsing with descriptive labels for improved task performance.

---

## Contributing

Feel free to fork the repository, make changes, and submit pull requests. Contributions are welcome!

## License

This project is licensed under the CC 4.0 License. See the [LICENSE](LICENSE) file for details.

## Author

**Pirate-Emperor**

[![Twitter](https://skillicons.dev/icons?i=twitter)](https://twitter.com/PirateKingRahul)
[![Discord](https://skillicons.dev/icons?i=discord)](https://discord.com/users/1200728704981143634)
[![LinkedIn](https://skillicons.dev/icons?i=linkedin)](https://www.linkedin.com/in/piratekingrahul)

[![Reddit](https://img.shields.io/badge/Reddit-FF5700?style=for-the-badge&logo=reddit&logoColor=white)](https://www.reddit.com/u/PirateKingRahul)
[![Medium](https://img.shields.io/badge/Medium-42404E?style=for-the-badge&logo=medium&logoColor=white)](https://medium.com/@piratekingrahul)

- GitHub: [Pirate-Emperor](https://github.com/Pirate-Emperor)
- Reddit: [PirateKingRahul](https://www.reddit.com/u/PirateKingRahul/)
- Twitter: [PirateKingRahul](https://twitter.com/PirateKingRahul)
- Discord: [PirateKingRahul](https://discord.com/users/1200728704981143634)
- LinkedIn: [PirateKingRahul](https://www.linkedin.com/in/piratekingrahul)
- Skype: [Join Skype](https://join.skype.com/invite/yfjOJG3wv9Ki)
- Medium: [PirateKingRahul](https://medium.com/@piratekingrahul)

Thank you for visiting the SEER project!

---
