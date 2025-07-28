# AI/ML and Data Analytics [↑](AWS-Practitioner-Essentials-Notes.md)

### `Artificial Intelligence (AI) and Machine Learning (ML) on AWS` [↑](#aiml-and-data-analytics-)
**_Artificial Intelligence_** is a broad field focused on the development of intelligent computer systems capable of
performing human-like tasks.

**_Machine Learning_** is a type of AI for training machines to perform complex tasks without explicit instructions. ML
training finds the patterns hidden in vast amounts of historical data to produce an **ML model**. This ML model can
then be applied to new data to make predictions or decisions based on the patterns it's learned.


#### Common ML Business use cases
1. Predict trends, such as future stock prices.
2. Make decisions, like routing callers to the right department.
3. Detect anomalies, such as bank fraud.

### `AWS AI/ML Solutions` [↑](#aiml-and-data-analytics-)
The AWS AI/ML stack is composed of the following three (3) tiers of solutions:

#### Tier 1: AWS AI Services
Pre-built models that are already trained to perform specific functions. These ready-to-use, managed services can
help quickly solve for a variety of business use cases.

1. **Language Services**

AWS AI Language Services are great for when there is a need to interpret text or speech and transform it into something meaningful.

| Language Service      | Description                                                                                                                                                                                                                                                 |
|-----------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| **Amazon Comprehend** | Uses natural language processing to extract key insights from documents. It develop these insights by recognizing key phrases, language, sentiment, and other common elements in the document                                                               |
| **Amazon Polly**      | Converts text into life-like speech. Supports multiple languages, different genders, and variety of accents. <br/> **Use Cases:** Virtual assistants, e-learning applications, accessibility enhancements for visually impaired users.                      |
| **Amazon Transcribe** | Converts speech into text. Supports multiple language ans offers speaker identification, custom vocabulary, and real-time transcription. <br/> **Use cases:** Customer call transcription, automated subtitling, and metadata generation for media content. |
| **Amazon Translate**  | Text translation service. Ideal for global communication because it supports real-time and batch text translation across multiple language. <br/> **Use Cases:** Document translation and muti-language application integration.                            |


2. **Computer Vision and Search Services**

These services are ideal for answering questions and gathering insights from various types of content sources such as documents, images, videos, and more.

| Computer Vision and Search Services | Description                                                                                                                                                                                                                                                                                                                           |
|-------------------------------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| **Amazon Kendra**                   | Uses natural language processing to search for answers within large amounts of enterprise content. Understands the context of a query so it can return more precise and relevant answers than just a list of documents with matching keywords. <br/> **Use Cases:** Intelligent search, chatbots, and application search integration. |
| **Amazon Rekognition**              | Video analysis service. Identify objects, people, text, scenes, and activities within images and videos stored in Amazon S3. <br/> **Use cases:** Content moderation, identity verification, media analysis, and hone automation experiences.                                                                                         |
| **Amazon Textract**                 | Detects and extracts typed and handwritten text found in documents, forms, and even tables within documents. <br/> **Use cases:** Financial, healthcare, and government form text extraction for quick processing.                                                                                                                    |


3. **Conversational AI and personalization services**

Users can interact with applications through text and voice conversations. It is also possible to present customers with produce recommendations personalized just for them.

| Conversational AI Services | Description                                                                                                                                                                                       |
|----------------------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| **Amazon Lex**             | Add voice and text conversational interfaces to applications. This service use both Natural Language Understanding (NLU) and Automatic Speech Recognition (ASR) to create lifelike conversations. |
| **Amazon Personalize**     | Use historical data to build intelligent applications with personalized recommendations for customers.                                                                                            |


#### Tier 2: ML Services
[WORK IN PROGRESS]


1. **AI services** - pre-built models that are already trained to perform specific functions.
2. **ML services** - A more customized approach with `Amazon SageMaker AI` where you build, train, and deploy your
   own ML models with fully managed infrastructure.
3. **ML frameworks and infrastructure** - A completely custom approach to building models using purpose-build chips
   that integrate with popular ML frameworks.