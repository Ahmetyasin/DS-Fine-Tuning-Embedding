# **Fine-Tuning Embedding Model with Domain Knowledge**

This repository provides a comprehensive guide for fine-tuning an embedding model to specialize and incorporate domain knowledge, specifically using data science academic textbooks. The **Fine_Tuning.ipynb** file walks through the step-by-step process of creating a fine-tuning dataset by utilizing Grobid for data extraction and semantic splitting techniques to enhance the relevance and quality of the data.

## **Textbooks Used for Fine-Tuning Dataset**

The fine-tuning dataset is built using academic textbooks that cover various aspects of data science, including machine learning, deep learning, time series analysis, reinforcement learning, and more. These textbooks are:

1. Aßenmacher, Matthias. *Multimodal Deep Learning* (2023).
2. Bertsekas, Dimitri P. *A Course in Reinforcement Learning*.
3. Boykis, Vicki. *What are Embeddings* (2023).
4. Bruce, Peter & Andrew Bruce. *Practical Statistics for Data Scientists* (2017).
5. Daumé III, Hal. *A Course in Machine Learning*.
6. Deisenroth, Marc Peter et al. *Mathematics for Machine Learning* (2020).
7. Devlin, Hannah et al. *Seeing Theory*.
8. Gutmann, Michael U. *Pen & Paper: Exercises in Machine Learning*.
9. Jung, Alexander. *Machine Learning: The Basics* (2022).
10. Langr, Jakub & Vladimir Bok. *Deep Learning with Generative Adversarial Networks* (2019).
11. MacKay, David J.C. *Information Theory, Inference, and Learning Algorithms* (2003).
12. Montgomery, Douglas C. et al. *Introduction to Time Series Analysis and Forecasting* (2015).
13. Nilsson, Nils J. *Introduction to Machine Learning* (1996).
14. Prince, Simon J.D. *Understanding Deep Learning* (2024).
15. Shashua, Amnon. *Introduction to Machine Learning* (2008).
16. Sutton, Richard S. & Andrew G. Barto. *Reinforcement Learning: An Introduction* (2018).
17. Alpaydin, Ethem. *Introduction to Machine Learning* (2014).

These books serve as the foundation for creating the fine-tuning dataset stored in `train_dataset_17_book_grobid_semantic.json`.

## **Fine-Tuning Process**

1. **Data Cleaning & Preprocessing**:
   - Grobid was used to clean and extract text from the textbooks.
   - A **Semantic Node Parser** was applied to split the content into meaningful nodes, improving data relevancy by grouping semantically similar text blocks.

2. **Creating Fine-Tuning Dataset**:
   - Each node represents a segment of the textbook based on semantic similarity.
   - For each node, a query, corpus, and relevant documents are created.
   - The OpenAI embedding model was utilized to design queries where the relevant corpus would answer the question posed by the query.
   - The final dataset was stored as a JSON file, containing the necessary data for fine-tuning the embedding model.

3. **Fine-Tuning an Embedding Model**:
   - The model `sentence-transformers/all-mpnet-base-v2` was fine-tuned using this dataset to specialize in data science concepts.
   - Fine-tuning allows the model to improve its ability to understand and generate embeddings tailored to the domain-specific knowledge from the textbooks.
   - IMPORTANT: Make sure Grobid is running. 
To do this, ensure Docker Desktop is open and then run the following command in your terminal:
docker run -t --rm --init -p 8070:8070 -p 8071:8071 grobid/grobid:0.7.0
This will start Grobid on ports 8070 and 8071, which is needed for the parsing to work.


## **How to Use This Repository**

By following the steps in **Fine_Tuning.ipynb**, you can create a fine-tuning dataset using any set of domain-specific documents, preprocess the data using Grobid, and fine-tune an open-source embedding model.

## **Conclusion**

This repository demonstrates how to fine-tune an embedding model using domain-specific academic content. By leveraging Grobid, semantic parsing, and open-source models, you can specialize a model to your domain of interest and improve its understanding of relevant queries and responses.

---

Anyone can replicate this process to fine-tune any open-source embedding model with their own domain-specific data.
