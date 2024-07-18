This repository contains the dataset created to aid in achieving the goals of the dissertation titled "Readability Assessment and Text Simplification through Open-Source Large Language Models," as well as the model's responses for the tasks that were carried out. This dissertation aimed to understand how effective an open-source large language model is in assessing
the readability of texts and simplifying text across multiple domains.

- categorized_dataset: contains 9 files, each a collection of 10,000 lead section pairs sourced from Wikipedia and Simple Wikipedia for a given category. Included categories are Culture, Education, Employment, Entertainment, Health, Leisure, Objects, Science and Time.
- model_responses: contains 9 files, each with the model's raw and processed responses for both tasks (readability assessment and text simplification).

## categorized_dataset
- Title: Title of the article
- Original: Lead section from Wikipedia
- Simple: Lead section from Simple Wikipedia

## model_responses
- Title: Title of the article
- Response_original: Model's assessment of the readability of the lead section from Wikipedia
- Response_simple: Model's assessment of the readability of the lead section from Simple Wikipedia
- Response_simplified: Model's simplification of the lead section from Wikipedia
- Processed_response_original: The attributed grade-level extracted from Response_original
- Processed_response_simple: The attributed grade-level extracted from Response_simple
- Processed_response_simplified: Processed model's simplification of the lead section from Wikipedia
