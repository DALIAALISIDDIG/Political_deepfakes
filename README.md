# Political Audio Deepfakes, Warning Timing, and Media Trust

Data, analysis notebooks, and survey materials for **“Warnings about AI-generated political audio can undermine media trust.”**

Can people distinguish authentic political speech from AI-generated audio? Does believing a clip is real affect willingness to share it? And does the timing of a warning help people identify synthetic speech while preserving trust in media?

This project examines these questions across **three studies with 3,305 US participants**. The central finding is that timing matters: a warning provided before an authenticity judgment improved identification of synthetic audio, while a disclosure provided after judgment reduced trust in political audio content and online political media.

**Authors:** Dalia Ali, Jan Zilinsky, Cheng Yu, Naira Paola Arnez Jordan, Urs Gasser, Yannis Theocharis, and Orestis Papakyriakopoulos.

**Affiliations:** Technical University of Munich, Germany; University of Gothenburg, Sweden.

## Start here

- **Understand the research:** read the [study overview](#study-overview) and [main findings](#main-findings).
- **Explore the data:** open the workbooks in [Data/](Data/).
- **Follow the analyses:** use the [notebook guide](#analysis-notebooks) and [setup instructions](#running-the-analyses).
- **Inspect the stimuli and survey:** see [Audios with Links.xlsx](Audios%20with%20Links.xlsx) and the [survey source code](Survey/deepfake-main/).

## Study overview

Participants were recruited through Prolific in the United States. Data collection took place between May 2025 and April 2026. The final samples reported in the manuscript are:

| Study | Participants | Experimental design | Main measures | Data |
| --- | ---: | --- | --- | --- |
| Study 1 | 600 | Authentic audio with authentic content; synthetic audio with authentic content; synthetic audio with fabricated content | Authenticity judgments, policy agreement, and reported likelihood of voting for the speaker | [Phase_1.xlsx](Data/Phase_1.xlsx) |
| Study 2 | 603 | The same three audio-content conditions, with additional measures before and after exposure | Authenticity judgments, political evaluations, issue salience, emotional responses, and sharing intentions | [Phase_2.xlsx](Data/Phase_2.xlsx) |
| Study 3 | 2,102 | No warning; warning before authenticity judgment; disclosure after authenticity judgment | Identification of synthetic audio, trust in political audio content, and trust in online political media | [Phase_3.xlsx](Data/Phase_3.xlsx) |

### Studies 1 and 2: audio authenticity and political responses

The stimulus collection contains **210 clips** featuring Donald Trump and Kamala Harris across seven topics: immigration, national security, the economy, racism, climate, education, and gender. Each participant heard one clip, approximately 10–15 seconds long.

The three conditions distinguish the authenticity of the **voice recording** from the authenticity of the **statement**:

| `group_no` | Audio | Content |
| --- | --- | --- |
| 1 | Authentic recording | A statement the politician actually made |
| 2 | AI-generated voice | A statement the politician actually made |
| 3 | AI-generated voice | A fabricated statement the politician had not made |

Synthetic audio was generated using Meta's AudioBox research system. The [audio workbook](Audios%20with%20Links.xlsx) lists clip identifiers, recording URLs, text, descriptions, topics, speakers, and condition information.

### Study 3: when the warning appears

All participants heard the same AI-generated clip of Donald Trump discussing Greenland, with fabricated political content. Holding the clip constant allowed the study to compare warning timing across conditions.

| `group_no` | Condition | Procedure |
| --- | --- | --- |
| 1 | No warning | Listen, judge authenticity, then report trust |
| 2 | Pre-judgment warning | Receive information that the audio is AI-generated before listening and judging it, then report trust |
| 3 | Post-judgment disclosure | Listen and judge authenticity, receive information that the audio is AI-generated, then report trust |

**The meaning of `group_no` changes between Studies 1–2 and Study 3.** In the post-judgment condition, the authenticity response records the participant's initial judgment, before the disclosure.

## Main findings

The following results summarize the associated manuscript:

- **Synthetic political audio was often mistaken for authentic speech.** In Studies 1 and 2, 78.5% of authentic recordings were correctly identified. Correct identification of synthetic clips ranged from 35.5% to 61.4%, depending on the study and whether the statement was authentic or fabricated.
- **Political evaluations did not differ detectably across the three audio conditions.** Studies 1 and 2 found no detectable differences in policy agreement or reported voting intentions across conditions.
- **Issue salience increased after exposure in Study 2.** The proportion naming the clip's topic among the country's most important problems rose from 30.3% to 36.2%. This change did not differ significantly across audio conditions.
- **Perceived authenticity was associated with greater sharing intentions.** Among Study 2 participants exposed to synthetic audio, those who judged the clip as real reported greater willingness to share it privately and publicly. This is an association, rather than a randomized effect of perceived authenticity.
- **A warning before judgment improved identification in Study 3.** Correct identification increased from 68.9% without a warning to 82.5% with a pre-judgment warning, with no detectable reduction in the measured trust outcomes.
- **Disclosure after judgment reduced trust.** Compared with no warning, post-judgment disclosure lowered trust in political audio content and online political media. The decline was concentrated among participants who had initially judged the synthetic clip as real.

Study 3 was preregistered on **AsPredicted (#274189)**. Trust outcomes were preregistered; the correct-identification analyses were exploratory.

These findings concern responses in the study settings. Sharing measures capture intentions, and the Study 3 timing comparison uses one clip. Because data collection followed the 2024 US presidential election, reported likelihood of voting for Harris was a hypothetical measure of candidate support.

## Repository contents

```text
Political_deepfakes/
├── README.md
├── Audios with Links.xlsx
├── Data/
│   ├── Phase_1.xlsx
│   ├── Phase_2.xlsx
│   └── Phase_3.xlsx
├── Data Analysis/
│   ├── Deepfakes_authenticity_judgment.ipynb
│   ├── Deepfakes__issue_saliance_ipynb.ipynb
│   └── Deepfakes_trust.ipynb
├── Survey/
│   └── deepfake-main/
│       ├── app.py
│       ├── pages/
│       ├── UNSD_Methodology_ancestry.csv
│       └── requirements.txt
└── requirements.txt
```

The `Phase_*.xlsx` workbooks correspond to Studies 1–3. The audio workbook contains links to recordings; audio files are hosted externally.

### Analysis notebooks

| Notebook | Focus | Main figure outputs named in the code |
| --- | --- | --- |
| [Deepfakes_authenticity_judgment.ipynb](Data%20Analysis/Deepfakes_authenticity_judgment.ipynb) | Correct authenticity judgments across the three audio-content conditions in Studies 1 and 2 | `Figure_1A_authenticity_discernment` |
| [Deepfakes__issue_saliance_ipynb.ipynb](Data%20Analysis/Deepfakes__issue_saliance_ipynb.ipynb) | Issue salience and sharing intentions in Study 2, plus additional exploratory analyses | `Figure_2_salience_sharing` |
| [Deepfakes_trust.ipynb](Data%20Analysis/Deepfakes_trust.ipynb) | Warning timing, identification, and trust in Study 3; trust differences by initial authenticity judgment | `Figure_3_warning_timing`; `Figure_4_initial_judgment_trust` |

Figure cells save PNG and PDF files in the notebook's working directory. Some notebooks contain alternative figure versions or additional analyses. Filenames above retain the repository's original spelling.

### Selected variables

| Variable | Meaning |
| --- | --- |
| `group_no` | Experimental condition, using the study-specific mappings above |
| `realness_perception` | Binary authenticity judgment: `1` = judged real, `0` = judged fake |
| `audio_clip_id` | Audio-stimulus identifier |
| `speaker`, `topic` | Speaker and topic labels in Studies 1 and 2 |
| `policy_agreement`, `likelihood_to_vote` | Policy agreement and reported likelihood of voting for the speaker in Studies 1 and 2 |
| `mip_topics_before`, `mip_topics` | Most-important-problem responses before and after exposure in Study 2 |
| `salience_before`, `salience_after` | Issue-salience ratings before and after exposure in Study 2 |
| `share_likely_private`, `share_likely_public` | Private and public sharing intentions in Study 2 |
| `trust_content`, `trust_media` | Trust in political audio content and online political media in Study 3 |

This table is a guide to key analysis variables. Consult the survey questions and notebook recoding steps for item wording, scales, and analysis-specific transformations. A judgment of “fake” is correct for a synthetic clip; a judgment of “real” is correct for an authentic clip.

## Running the analyses

### 1. Download the repository and prepare an environment

```bash
git clone https://github.com/DALIAALISIDDIG/Political_deepfakes.git
cd Political_deepfakes
python3 -m venv .venv
source .venv/bin/activate
python -m pip install --upgrade pip
python -m pip install jupyterlab pandas numpy scipy matplotlib statsmodels openpyxl gdown
jupyter lab
```

On Windows, activate the environment with `.venv\Scripts\activate` instead. The packages above cover the notebook imports and Excel loading. They are not pinned to the original analysis environment. The existing `requirements.txt` files primarily describe the survey application's dependencies and do not include all notebook requirements.

### 2. Open a notebook and review its loading cells

Open a notebook from `Data Analysis/` and run its cells in order. The notebooks currently use `gdown` to download Excel workbooks from Google Drive. These download cells require internet access and accessible source links.

To use the workbooks checked into this repository, replace the download/path assignments in each data-loading block with local paths. For a notebook running from the repository root or `Data Analysis/`, use:

```python
from pathlib import Path
import pandas as pd

repo_root = Path.cwd()
if not (repo_root / "Data").is_dir():
    repo_root = repo_root.parent

P1_PATH = str(repo_root / "Data" / "Phase_1.xlsx")
P2_PATH = str(repo_root / "Data" / "Phase_2.xlsx")
P3_PATH = str(repo_root / "Data" / "Phase_3.xlsx")

df1 = pd.read_excel(P1_PATH)
df2 = pd.read_excel(P2_PATH)
df3 = pd.read_excel(P3_PATH)
```

**Check later cells too:** several notebooks download data again or reset `P3_PATH` to `"Phase_3.xlsx"`. Update those assignments as well, preserving any subsequent `pd.read_excel` calls and variable names such as `p1` and `p2`.

### 3. Inspect the results

The notebooks print descriptive statistics and model summaries and create the figures listed above. Use the study-specific condition definitions when interpreting results. The supplied notebooks cover the analyses described in the notebook guide; they should not be assumed to reproduce every result in the manuscript.

## Survey implementation

The [survey source](Survey/deepfake-main/) uses Streamlit and includes consent, audio presentation, authenticity and evaluation questions, demographic questions, and completion pages. Separate Study 3 pages implement the control, pre-judgment warning, and post-judgment disclosure conditions.

The current `app.py` routes participants to `pages/Rate_responses_phase3.py`, the control-condition page. The other variants are `Rate_responses_phase3_T1.py` and `Rate_responses_phase3_T2.py`. Review the routing and condition assignment before adapting the survey.

The application requires an SSH connection, a MySQL database with the expected tables and audio records, and these Streamlit secrets: `ssh_host`, `ssh_port`, `ssh_user`, `ssh_password`, `db_host`, `db_port`, `db_user`, `db_password`, and `db_name`. Credentials and database setup scripts are not included. The source documents the collection implementation and needs that infrastructure to run.

Once the database and secrets are configured, launch it from its application directory:

```bash
cd Survey/deepfake-main
python -m pip install -r requirements.txt
python -m streamlit run app.py
```

The audio collection contains both authentic and synthetic speech. Preserve the condition labels and explain which recordings are AI-generated when presenting study materials.

## Ethics and funding

The research was approved by the Non-Medical Division of the Ethics Committee of the Technical University of Munich, reference **2024-92-NM-BA**. All participants provided informed consent.

The research received funding from Meta, which also provided access to AudioBox for generating the synthetic stimuli. As stated in the manuscript, Meta had no role in study design, data collection, analysis, interpretation, or manuscript preparation. The voice-generation system itself is not included in this repository.

## Reference and contact

When using these materials, please acknowledge the associated manuscript and link to this repository:

> Ali, D., Zilinsky, J., Yu, C., Arnez Jordan, N. P., Gasser, U., Theocharis, Y., & Papakyriakopoulos, O. *Warnings about AI-generated political audio can undermine media trust.*

For questions about the research or reuse of the materials, contact **Dalia Ali** at [dalia.ali@tum.de](mailto:dalia.ali@tum.de). For repository issues, use [GitHub Issues](https://github.com/DALIAALISIDDIG/Political_deepfakes/issues).

No license file is currently included in the repository. Contact the authors for clarification about reuse permissions.
