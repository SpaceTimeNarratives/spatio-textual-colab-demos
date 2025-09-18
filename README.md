# spatio-textual - Colab Demos 📓✨

End-to-end, Colab-friendly tutorials for the [**spatio-textual**](https://github.com/SpaceTimeNarratives/spatio-textual) package, tailored to Digital/Spatial Humanities use cases (Holocaust survivors' testimonies and the Corpus of Lake District Writing).

---

## Table of Contents
1. [Prerequisites](#prerequisites)
2. [Quick Start (Colab)](#quick-start-colab)
3. [Notebooks](#notebooks)
4. [Sample Data](#sample-data)
5. [FAQ / Troubleshooting](#faq)
6. [License](#license)

---

## Prerequisites
- Python 3.9+
- A modern browser for Google Colab (Chrome/Edge/Firefox)
- *(Optional)* A GitHub account if you want to fork/clone this tutorial repo

---

## Quick Start (Colab)

1. Open any notebook below (once this repo is on GitHub) by replacing `SpaceTimeNarratives/spatio-textual-colab-demos` with your correct repo path:
   - demo_1_entity_annotation.ipynb](https://colab.research.google.com/github/SpaceTimeNarratives/spatio-textual-colab-demos/blob/main/demo_1_entity_annotation.ipynb)
      - Entity & verb annotation, sentence-safe chunking, and Q↔A-aware testimony segmentation.
   - [demo_2_sentiment_emotions.ipynb](https://colab.research.google.com/github/SpaceTimeNarratives/spatio-textual-colab-demos/blob/main/demo_2_sentiment_emotions.ipynb)
      - Sentiment and emotion classification (rule backend) + hooks for HF/LLM.
   - [Interpretation: demo_4_interpretation.ipynb](https://colab.research.google.com/github/SpaceTimeNarratives/spatio-textual-colab-demos/blob/main/demo_4_interpretation.ipynb)
      - Record-level summaries, affect explanations, simple themes (LLM-friendly).
   - [Visualisation: demo_5_visualisation.ipynb](https://colab.research.google.com/github/SpaceTimeNarratives/spatio-textual-colab-demos/blob/main/demo_5_visualisation.ipynb)
      - GeoJSON export, Folium maps, and co-occurrence graphs.

2. In the first cell of each notebook, run the **Setup** cell to install dependencies.

3. Execute cells sequentially.

> Tip: If you are maintaining your own Python package repo for `spatio_textual`, add an install cell like `pip install git+https://github.com/<OWNER>/<PKG_REPO>.git@main` at the top of each notebook.

> 🧩 These notebooks assume you have access to the `spatio_textual` package (installed locally or available in your Colab environment).

---

## Notebooks

- `demo_1_entity_annotation.ipynb`  
  **Focus:** Entities, verbs, sentence-safe chunking, Q↔A testimony segmentation (`qa.py`).  
  **Input sample:** `data/testimonies/testimony_001.txt`, `data/testimonies/snippet_002.txt`.

- `demo_2_sentiment.ipynb`  
  **Focus:** Rule-based sentiment + hooks for HF/LLM; attach labels/scores to segments.

- `demo_3_emotion.ipynb`  
  **Focus:** Ekman-style emotions; rule backend + hooks; optional distributions.

- `demo_4_interpretation.ipynb`  
  **Focus:** Summaries, affect explanations, theme tags; optional LLM hook.

- `demo_5_visualisation.ipynb`  
  **Focus:** GeoJSON export, Folium maps, co-occurrence graphs.

---

## Sample Data

Small testimony snippets are provided under `data/testimonies/` for quick runs. You can replace these with your own transcripts.

- `data/testimonies/testimony_001.txt`
- `data/testimonies/testimony_002.txt`

Each file uses a simple Q↔A prefixed format (e.g., `Q:` and `A:` lines), which the notebooks parse with `segment_testimony(...)`.

---

## FAQ

**Q: Colab says a spaCy model is missing.**  
A: Run `python -m spacy download en_core_web_sm` in the Setup cell.

**Q: I want faster execution.**  
A: Use `en_core_web_sm` for demos; switch to `en_core_web_trf` for higher quality (slower) runs.

**Q: I want to try Hugging Face models.**  
A: Uncomment the HF installs in the Setup cell and wire a `transformers` pipeline as shown in the sentiment notebook.

**Q: How do I keep pandas schema consistent?**  
A: Use `load_annotations(..., ensure_columns=True)` to add any missing columns.

---

## 📄 License

GNU GENERAL PUBLIC LICENSE. See [LICENSE](./LICENSE.txt).

---

## `requirements_colab.txt`

```text
spacy>=3.6,<4.0
geonamescache>=2.0.0
pandas>=2.0.0

# Optional (progress bar, maps)
tqdm>=4.66.0
folium>=0.15.0

# (Optional) Transformers/LLM backends for richer sentiment/emotion
# transformers>=4.41.0
# torch>=2.0.0
# openai>=1.0.0
```

> In Colab, you can also inline these as `%pip install -q -r requirements_colab.txt`.

---

## `data/testimonies/testimony_001.txt`

```text
Q: Where were you living before the deportations?
A: We lived in Amsterdam with my parents and sister.
Q: Do you remember what happened when the transports began?
A: Anne Frank was taken from Amsterdam to Auschwitz. Many families were separated.
```

---

## `data/testimonies/testimony_002.txt`

```text
Q: How did you feel during the journey?
A: We were afraid, hungry, and cold during the march.
Q: Did anyone help you when you arrived?
A: A farmer welcomed us and offered warm soup; I felt a small relief.
```

---

## Suggested repo layout

```text
spatio-textual-colab-demos/
├─ README.md
├─ requirements_colab.txt
├─ demo_1_entity_annotation.ipynb
├─ demo_2_sentiment.ipynb
├─ demo_3_emotion.ipynb
├─ demo_4_interpretation.ipynb
├─ demo_5_visualisation.ipynb
└─ data/
   └─ testimonies/
      ├─ testimony_001.txt
      └─ testimony_002.txt
```

> After creating the repo with these files and notebooks, you can open each notebook directly in Colab via the GitHub link format shown above.
