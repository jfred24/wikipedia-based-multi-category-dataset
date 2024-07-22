This repository contains the dataset created to aid in achieving the goals of the dissertation titled "Readability Assessment and Text Simplification through Open-Source Large Language Models”, as well as the model's responses for the tasks that were carried out. This dissertation aimed to understand how effective an open-source large language model (Llama3) is in assessing the readability of texts and simplifying text across multiple domains.

The dataset (categorized_dataset folder) contains 9 files in .csv format, each a collection of 10,000 lead section pairs sourced from Wikipedia (https://www.wikipedia.org/) and Simple Wikipedia (https://simple.wikipedia.org/) for a given category. Included categories are Culture, Education, Employment, Entertainment, Health, Leisure, Objects, Science and Time. The texts included in these files were used as the textual data that the large language model assessed and simplified in the context of this dissertation.

To extract the lead section text from the Wikipedia and Simple Wikipedia article pairs, a given category and its subcategories are traversed to collect page titles. The page title is the article's unique identifier across Wikipedia and Simple Wikipedia. No category is visited more than once, duplicate titles are discarded, and we check if the respective Wikipedia and Simple Wikipedia pages exist. If they do, the lead sections are collected and added to the dataset. Article pages that are disambiguation pages or article pairs with identical lead sections are not included. Disambiguation pages are pages created to resolve the confusion that might occur when a single term can be associated with more than one topic. These pages list articles associated with the same title or a similar term but are not proper article pages about a specific topic; instead, they serve as a navigational tool and, therefore, are not included. 10,000 pairs of lead sections were collected for each of the 9 selected categories.

To decide which categories the text samples were extracted from, we analyzed Simple Wikipedia's category tree and determined the number of article pages of each sub-category directly under the Everyday Life and Knowledge categories. Firstly, we chose Simple Wikipedia's category tree because Simple Wikipedia is less extensive than Wikipedia, reducing the risk of later encountering pages without corresponding Wikipedia articles and ensuring a higher success rate in finding matching lead sections. Second, we chose to focus on the subcategories under the Everyday Life and Knowledge categories because these categories encompass the core domains of the encyclopedia, capturing the main domains of human knowledge and everyday experiences. After analyzing the number of articles per category, we opted to include categories whose number of articles surpassed 100,000.

The folder model_responses contains 9 files in .csv format, each with the model's raw and processed responses for both tasks (readability assessment and text simplification).

The system prompt chosen for the readability assessment task was: "Your role is to rate the readability of texts that are provided to you.", and the text to assess was provided with the prompt: "Consider the following text: \{text\}" followed by two new lines and the instruction: "Based on your own assessment, rate its readability on a grade-level scale."

The system prompt chosen for the text simplification task was: "Your role is to simplify texts that are provided to you. Your reply should only consist of the simplified text.", and the text to simplify was provided with the prompt: "Consider the following text: \{text\}" followed by two new lines and the instruction: "Simplify the text into plain language, aiming to improve its readability and increase its comprehension by laypersons and people with lower information literacy."

Regarding the readability assessment task, in its response, the model attributes either a grade level to a text or a range spanning up to 3 levels, such as ``10th to 12th grade''. The grade level or range of levels is most often accompanied by a detailed justification of its rating. Only the grade level or interval of grade levels is needed for the analysis. During processing, we extract this information from the model's response. If the model assigns a single grade level, we process it as an integer. If the model assigns an interval of grade levels, we process it as the interval itself.

Regarding the text simplification task, most often, Llama's output is solely the simplified text; however, there are cases where Llama begins its response with an introductory phrase such as ``Here is the simplified text:'' or ends with a summary of the changes it has made to the original text. In such cases, these parts are removed from the response.

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
