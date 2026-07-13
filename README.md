# FineMuSe

This repository is associated with the research paper titled *Beyond Binary Classification: Detecting Fine-Grained Sexism in Social Media Videos*, Laura De Grazia, Danae Sánchez Villegas, Desmond Elliott, Mireia Farrús, and Mariona Taulé.

To advance research on fine-grained sexism detection, we present FineMuSe, a new fine-grained multimodal dataset for sexism detection in Spanish (European and Peninsular). FineMuSe includes videos from the MuSeD dataset, which originally contained only binary annotations for TikTok and BitChute videos. In FineMuSe, these videos have been extended with fine-grained annotations. Additionally, the dataset includes a new data source, YouTube Shorts, which contains both binary and fine-grained annotations. For convenience, we refer to the TikTok and BitChute videos as Part 1 (P1) and the YouTube Shorts videos as Part 2 (P2).

The final dataset contains 828 videos, each labeled as sexist or non-sexist, and includes granular annotations for both sexist and non-sexist content. The annotations were developed using a three-level hierarchical taxonomy, with the first level comprising mutually exclusive categories and the second and third levels comprising sub-categories that may co-occur.

<img width="756" height="327" alt="final_taxonomy" src="https://github.com/user-attachments/assets/b2873bdb-3907-4240-816f-5bbf78cb9e9c" />

<h2>
  <img width="40" alt="analysing" src="https://github.com/user-attachments/assets/72d52d34-1889-447a-9928-71a698a710f9" />
  Dataset Statistics
</h2>

FineMuSe has a balanced distribution between sexist and non-sexist content, with 48.5% of the videos labeled as sexist in P1 and 54.2% in P2. The following figures illustrate the distribution of sexist and non-sexist sub-categories across P1 and P2:

<div>
  <img width="90%" alt="combined_sexism_figures" src="https://github.com/user-attachments/assets/60f0fe27-3fca-4edd-b032-7d6fa95ce0bf" />
</div>

<h2>
  <img width="40" alt="analysing" src="https://github.com/user-attachments/assets/1763a843-f6ee-4322-9918-55e9629dca34" />
  Annotation Process
</h2>

We relied on six expert annotators of diverse genders and ages to ensure demographic variety. The group was split into two teams, each assigned half of the dataset. The annotation process followed a three-step approach: first, annotating text transcripts; second, annotating audio; and finally, annotating videos. Each team annotated the text transcripts and videos for their assigned subset, while the other team handled the audio. To evaluate the reliability of the annotations, we computed Fleiss' Kappa. For the binary task, the Kappa values ranged from substantial (0.61–0.80) to almost perfect agreement (0.81–1.00). 
The fine-grained classification was more complex than the binary annotation, as evidenced by lower IAA scores, ranging from moderate (0.41–0.60) to substantial (0.61–0.80). 

---
<h2>
  <img width="40" alt="robot" src="https://github.com/user-attachments/assets/1a1a55e2-93f3-440b-a683-d5dcfe134b54" />
  Evaluation of LLMs and Multimodal LLMs 
</h2>

We evaluated a wide range of LLMs that process text-only inputs as well as multimodal LLMs that integrate both text and images. The task first requires determining whether a social media post is sexist and, if so, identifying its specific type(s) of sexism. All evaluations were conducted against labels assigned by annotators who had access to the full video. Our findings suggest that LLMs perform competitively with human annotators, particularly when they have access to multimodal information. The following figure illustrates the results for the fine-grained task across multimodal models, using per-class F1 as the evaluation metric:

<img width="1138" height="424" alt="macro_f1" src="https://github.com/user-attachments/files/29962132/per_class_f1_multimodal.pdf" />

## Dataset file structure

To respect privacy and platform terms, only video IDs are shared, and no video content is distributed. The dataset includes both binary and individual labels for each of the three levels of annotation (Text, Audio, and Video) for both Part 1 and Part 2. Each file contains the following columns:

* **Video_ID**: 
    * For P1, the video_id combines the platform name and the video identifier. Platforms include: TikTok (prefix tt), BitChute (prefix bt) 
    * For P2, the video_id For Part 2, the video_id includes only the video identifier, given that we sampled from a single platform.
      
* **Category_Majority_Voting**: The final label computed using a majority vote approach. 

* **Category_Label**: The individual label assigned by each annotator.

**Example**: 

| Video_ID | Sexism_Majority_Voting | Sexism_Label | Stereotypes_Majority_Voting| Stereotypes_Label |
| :--- | :---: | :---: | :---: | :---: |
| bt_1bQe-FLbb5k | 1 | [1, 0, 1] | 1 | [0, 1, 1] |


For research purposes, you can get access to the full dataset by filling out [this form](https://forms.gle/x2TwWhzBLqxYAv8E7). 
