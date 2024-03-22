---
layout: page
title: 'Smart TA'
description: USC Graduate Directed Research
img: assets/img/7/structure.png
importance: 44
category:
giscus_comments: true
---

Working repositories:

Custom document embedding: [GitHub Link](https://github.com/ngcxy/Custom_Doc_Embedding)

Other Embedding models:  [GitHub Link](https://github.com/marioUSC/academyChatBot)

Piazza API: [GutHib Link](https://github.com/ngcxy/Piazza_API)

---

This is a ongoing USC directed research project supervised by Professor Young Cho at Viterbi School of Engineering. 
Our group of three is currently developing a smart TA application that can reply to students' answers immediately 
based on a model trained by previous posts.

<div class="row mt-3">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.html path="assets/img/7/structure.png" class="img-fluid rounded z-depth-1" %}
    </div>
</div>

### Language Model

The training process of the model is basically **document embedding**. 
We've already achieved high accuracy in two ways using pre-built techniques [**LlamaIndex**](https://www.llamaindex.ai/) and [**SBERT**](https://www.sbert.net/). 
Now, we're exploring a custom way in which we design the algorithms to process context by ourselves, aiming to reach a much lower processing cost.
The customized model will be introduced in the next section.

For the inference part, the input question will first get passed into the embedded model, 
which will provide us with questions that are most similar to the new question in our database.
After this, we can further retrieve the answers to these questions. 
Finally, we feed all the information to OpenAI API to let it deal with expression issues such as grammar, and summarize the answer.

<div class="row mt-3">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.html path="assets/img/7/nlp.png" class="img-fluid rounded z-depth-1" %}
    </div>
</div>

### Custom Embedding

Although pre-built libraries work well in embedding, there are still points in building our own embedding model.
First, the text of our post database are highly domain specific - it mainly concerns with course materials and concepts, 
so a customized model might be more flexible and efficient. 
Additionally, working on the algorithms by ourselves really helps me to significantly understand Natural Language Processing.

The processing includes these crucial procedure: Preprocessing, Word2Vec, Kmeans Clustering, and Histogram Construction.



### Piazza API

...

### Frontend

The frontend is a chat interface that serves mostly as a test tool. It is built by Next.js and hosted on Vercel.

<div class="row mt-3">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.html path="assets/img/7/frontend.png" class="img-fluid rounded z-depth-1" %}
    </div>
</div>

> My part in this project: Piazza API(completed) & Custom Embedding(On going)




