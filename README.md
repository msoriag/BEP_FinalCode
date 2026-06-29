# Generative AI vs Human-Written Descriptions: Informational Alignment

## Project Overview
With the rapid integration of generative artificial intelligence in e-commerce, product descriptions are increasingly automated. This project evaluates the extent to which these AI-generated descriptions actually align with consumer information needs, comparing them against a human-written baseline. 

By utilizing user-generated Questions and Answers (Q&A) as a proxy for unresolved consumer information needs, this study measures whether AI models successfully cover the practical attributes consumers actively seek out.

## Key Findings
Based on mixed-effects logistic regression models and coverage measurements:
* **The Information Gap:** AI-generated descriptions achieved a moderate coverage rate of 42.4%, leaving a substantial 57.6% information gap. Human-written text consistently outperformed AI in covering these critical consumer terms.
* **Technical vs. Physical Attributes:** AI successfully captured standardized technical specifications (e.g., storage capacity, screen resolution) but exhibited a notable gap in covering spatial and physical factors (e.g., equipment padding, dimensions).
* **Prompt Engineering is Ineffective Here:** Manipulating the AI's tone (Neutral/Informative) and persona (Quality-Focused) did not produce statistically significant variations in information coverage ($p>0.05$).
* **No "Over-claims":** Detected zero instances of over-coverage within the Q&A-derived dictionary, suggesting that omission—rather than text fabrication—is the dominant measurable issue in this low-context e-commerce setting.
* **Conclusion:** Businesses cannot rely solely on generic automated text generation; manual intervention remains necessary to capture critical human-centric usability details.

## Methodology
1. **Demand Structure Creation:** Applied Natural Language Processing (NLP) and **BERTopic** to Amazon's "Electronics" Q&A dataset to map consumer inquiries, creating a unique dictionary of 108 frequently asked attributes.
2. **AI Text Generation:** Generated alternative product descriptions using GPT-5.5 across four experimental conditions manipulating tone and persona. 
3. **Coverage Measurement:** Informational coverage was calculated using a strict string-matching algorithm combined with a hybrid semantic similarity framework (SentenceTransformers) using a threshold of 0.45.
4. **Statistical Modeling:** Results were analyzed using mixed-effects logistic regression models to account for baseline differences between products and isolate the true effects of the tested variables.

## Data Acquisition (Important)
Due to GitHub's file size limits (100MB), the raw datasets are **not** included in this repository. You must download them manually before running the project.

Please download the following two files and place them in the root directory of this project:

1. **Product Metadata**:  
   [Download `meta_Electronics.json.gz`](https://mcauleylab.ucsd.edu/public_datasets/data/amazon_v2/metaFiles2/meta_Electronics.json.gz)
2. **Q&A Data**:  
   [Download `qa_Electronics.json.gz`](https://mcauleylab.ucsd.edu/public_datasets/data/amazon/qa/qa_Electronics.json.gz)

*Note: Do not unzip these files. The code is designed to parse them directly in their compressed `.gz` format.*

## Installation & Setup
This project is built using Python. It is recommended to use a virtual environment to manage dependencies.

1. **Clone the repository:**
   ```bash
   git clone <your-repo-url>
   cd <your-repo-folder>
