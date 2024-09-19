# Commit Message Dataset

This repository contains a human-labeled dataset of commit messages, issue text, and code content, distributed in `jsonl` (JSON Lines) format and compressed using gzip. The dataset has been carefully annotated to support research and validation in the context of topic modeling and other natural language processing (NLP) tasks.

## Dataset Overview

The dataset consists of 40,000 unique items, each representing a commit message or issue text, along with indexed code content. The key features of the dataset are:

- **Problem/solution classification**: Each item has two boolean labels:
  - `problem`: Set to `True` if the text describes a problem.
  - `solution`: Set to `True` if the text describes a solution.

- **Semantic similarity**: For each commit message, up to 5 other semantically similar commit messages are paired and labeled as `similar` or `not similar`. This approach mirrors a labeling methodology commonly used in the research community.

## Files in the Repository

Each file in this repository is in `jsonl.gz` format, where:
- **jsonl**: The dataset is stored in JSON Lines format, where each line represents a single JSON object.
- **gz**: Files are compressed using gzip to save space and ease distribution.

## Dataset Use

This dataset was used to validate the results of topic modeling performed in this project. It is designed to assist with the following tasks:
- Evaluating problem/solution detection in commit messages.
- Measuring semantic similarity between commit messages.
- Supporting research in topic modeling and natural language processing for code-related data.

## File Structure

Each item in the dataset is structured as follows:

```json
{
  "id": "unique_identifier",
  "commit_message": "The commit message text",
  "issue_text": "Associated issue text, if available",
  "code_content": "Relevant code content, if applicable",
  "labels": {
    "problem": true,
    "solution": false
  },
  "similar_commits": [
    {
      "commit_id": "another_commit_id",
      "similar": true
    },
    ...
  ]
}
```

- **`id`**: A unique identifier for the commit message.
- **`commit_message`**: The text of the commit message.
- **`issue_text`**: Text from any associated issue (if available).
- **`code_content`**: Relevant code snippet related to the commit (if applicable).
- **`labels`**: Boolean flags indicating whether the text describes a problem and/or solution.
- **`similar_commits`**: A list of up to 5 other commit messages and their similarity labels.

## How to Access

To download and decompress a dataset file:

```bash
gzip -d <file_name>.jsonl.gz
```

To read the dataset, simply load it line-by-line as a JSON object:

```python
import json

with open('<file_name>.jsonl', 'r') as file:
    for line in file:
        data = json.loads(line)
        print(data)
```

## Citation

If you use this dataset in your research, please cite it as follows:

```
[Author(s)], "Commit Message Dataset for Problem/Solution Detection and Semantic Similarity", [Year].
```

## Acknowledgements

We would like to thank the human reviewers for their effort in labeling the dataset and supporting this research.



## Mirror  

The dataset and associated files can also be downloaded via the links below:
- https://storage.googleapis.com/temp-public-share/sagemaker.tar
