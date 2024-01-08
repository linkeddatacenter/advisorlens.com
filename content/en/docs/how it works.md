---
title: How it works
description: Learn how How do AdvisorLens work?
weight: 15
---

AdvisorLens is a innovative implementation of neuro-symbolic AI platform that operates in two phases: Semantic information retrieval and neural content generation.

In the semantic search phase:

Algorithms actively search for and retrieve relevant information based on the user’s prompt by traversing a knowledge graph. This retrieved information is the basis for generating coherent and contextually relevant responses according with new LLM models and algorithms.

AdvisorLens works both in open and close domain enterprise settings, a more restricted set of trusted sources is typically used to enhance the security and reliability of internal knowledge. For example, AdvisorLens system can look for:
- Current contextual factors, such as real-time weather updates and the user’s precise location
- User-centric details, their previous orders on the website, their interactions with the website, and their current account status
- Relevant factual data in private documents that are  private  

In the content generation phase:

After retrieving the relevant information, a generative language model, such as a transformer-based model, takes over. It uses the retrieved context to generate natural language responses. The generated text can be further conditioned or fine-tuned based on the retrieved content to ensure that it aligns with the context and is contextually accurate. The system  includes references to the sources it consulted for transparency and verification purposes.

```plantuml
database "Proprietary data" as data
actor "User Question" as questions
node "AdvisorLens Model" as model
database "Knowlege graph db" as kb #line.dashed
file "Semantic Context" as prompt #line.dashed
agent LLM
file "answers"

data --> model
questions --> model
model -> kb : Store
model -> kb : Search

questions --> prompt
kb --> prompt : relevant data

prompt -> LLM
LLM -> answers
```

The image shows how AdvisorLens works: the AdvisorLens model parses proprietary data, detect semantics and store it in a knowledge graph. Then the model receives the user question and search it in the semanti knowledge base. It retrieves the top relevant documents and prompt the original question and information to LLM which leads LLM to generate an accurate answer.


AdvisorLens use two systems to obtain external data:

- **Knowledge graph**: Knowledge graph help find relevant documents using semantic searches. They can also work independently.
- **Feature stores**: These are systems or platforms to manage and store structured data features used in machine learning and AI applications. They provide organized and accessible data for training and inference processes in machine learning models like LLMs.
