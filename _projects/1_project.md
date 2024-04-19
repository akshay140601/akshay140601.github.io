---
layout: page
title: RAG-based chatbot for answering questions related to CMU
description:
img: assets/img/proj_1_1.png
importance: 1
category: work
related_publications: true
---

In the field of Natural Language Processing, developing systems that can answer domain-specific questions from diverse and complex sources presents a challenging task. We develop and implement a Retrieval Augmented Generation (RAG) system tailored specifically for answering questions within the domains of CMU and LTI. Leveraging the framework proposed by Lewis et al. (2020), our RAG system comprises three key components: a document embedder, a document retriever, and a question-answering system. Our endeavor involved extensive experimentation with diverse models and techniques aimed at optimizing each component's performance.

We first scraped all the data from different formats of documents such as HTML, PDF, and Semantic Scholar API. Cleaning of the data was performed and data annotation was done to create a high quality test dataset to effectively assess the performance of our system. We created three different RAG system, each built on top of the previous system. The first system was a vanilla RAG system, that uses a basic retriever to get the top-100 relevant documents and then passes the top-3 documents as context to the LLM (Llama2-70B-chat). We then observed that in most of the questions, the retriever got the right document, but it was not in top-3. Hence, we implemented a reranker system, which is much more powerful but computationally expensive. With the reranker built on top of the vanilla RAG system, we compared the input query with all 100 retrieved documents and ranked them again. This improved our performance but our system was very sensitive to the way the questions were framed. We then built a multiquery retriever system that paraphrases the question in 3 different ways, retrieves documents separately for all the questions, and passes the unique documents to the reranker system. The reranked top-3 documents are then passed to the reader model as a context to get the answer to the query. This turned out to be the best system, and its architecture is shown in Figure 1.

<div class="row">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="assets/img/proj_1_1.png" title="example image" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="caption">
    This image can also have a caption. It's like magic.
</div>

We evaluated our system on 3 metrics viz., exact match (if the generated answer matches exactly with the reference answer), F1 score, and recall. Our best system had an F1 score of 0.41, and the closed book usage of our system had an F1 score of only 0.1352. We also made sure that our results are statistically significant. We see a tremendous improvement in performance with using our RAG architecture.

In conclusion, we developed a RAG system to answer questions related to CMU and the LTI department. We created a complex yet fast architecture for accurately answering the questions. Our system results in a 1.57x increase in performance compared to a vanilla RAG system and 3x improvement when compared to the closed book model usage.
