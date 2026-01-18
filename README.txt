HOW TO RUN THE LLM-JUDGE NOTEBOOK (JudgePOC.ipynb)

Overview
--------
This repository contains a Jupyter notebook (JudgePOC.ipynb) that evaluates
conversation transcripts stored as JSON files against a simple policy:

  “Never book a flight to North Korea.”

The notebook reads transcript files from a folder named:

  Conversation Logs X

(where X is a number you can choose), produces judged JSON outputs, and
generates an HTML report summarizing the results.


Prerequisites
-------------
Before running the notebook, you will need:

• Python 3.10 or newer
• Jupyter Notebook or JupyterLab
• An OpenAI API key


Install dependencies
--------------------
From the repository root, install the required packages:

  pip install openai python-dotenv ipywidgets jupyter

All other imports used in the notebook come from the Python standard library.


Set your OpenAI API key
----------------------
Create a file named ".env" in the repository root containing:

  OPENAI_API_KEY=your_api_key_here

Alternatively, you may export the key in your shell before starting Jupyter:

  export OPENAI_API_KEY="your_api_key_here"


Start Jupyter
-------------
From the repository root, run:

  jupyter notebook

(or, if you prefer:)

  jupyter lab

Then open the notebook:

  JudgePOC.ipynb


Run the batch judge
-------------------
Scroll to the bottom of the notebook. You will see a small UI consisting of:

• A text field labeled "Folder"
• A button labeled "Run batch judge"

In the Folder field, enter the path to one of the provided transcript folders,
for example:

  ./Conversation Logs 16
  ./Conversation Logs 21

Then click the "Run batch judge" button.


Outputs
-------
When the run completes, the notebook will automatically:

• Create a new output folder next to the input folder, named like:
    Judged - Conversation Logs 16 - 01
    (or -02, -03, etc. on subsequent runs)

• Write one judged JSON file per input transcript, prefixed with "Judged -"

• Write a master summary file:
    Judge Summary.json

• Generate an HTML report and open it automatically in your browser


Notes
-----
• If you see an error saying OPENAI_API_KEY is not set, confirm that your .env
  file exists or that the environment variable is exported.

• Each "Conversation Logs X" folder must contain .json files directly inside
  the folder (the notebook does not search subfolders).

• Re-running the notebook on the same input folder will never overwrite
  previous outputs; a new numbered "Judged -" folder is created each time.
