---
layout: page
title: 'Movipendent: Online Movie Community'
description: a Javascript full-stack project with MongoDB
img: assets/img/3/3-homepage.png
importance: 47
category:
giscus_comments: true
---

Visit the [Website](https://movie-delivery-frontend.vercel.app/)

Code Link: [backend](https://github.com/ngcxy/MovieDelivery_backend), [frontend](https://github.com/ngcxy/MovieDelivery_frontend)

Short Demonstration Video on [YouTube](https://youtu.be/-SHo5A1ImtQ)


---

## Architecture

---

### Overall & communication
<div class="row">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.html path="assets/img/3/3-overall.png" title="example image" class="img-fluid rounded z-depth-1" %}
    </div>
</div>

### Backend
<div class="row">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.html path="assets/img/3/3-backend.png" title="example image" class="img-fluid rounded z-depth-1" %}
    </div>
</div>

### Frontend
<div class="row">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.html path="assets/img/3/3-frontend.png" title="example image" class="img-fluid rounded z-depth-1" %}
    </div>
</div>

### Database
<div class="row">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.html path="assets/img/3/3-database.png" title="example image" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
  
---
  
## Pages

---

### Homepage
<div class="row">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.html path="assets/img/3/3-homepage2.png" title="example image" class="img-fluid rounded z-depth-1" %}
    </div>
</div>

- Header function:
  - Title as the Homepage Router
  - Search Bar
  - Explore button to browse all movies
  - "+" button to recommend movie
  - Log in entry
- Homepage content:
  - Cover block with search bar
  - List of top movie
  - List of newest arrival
  - User's movie list (if logged in)

### Movie Detail Page
<div class="row">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.html path="assets/img/3/3-detailpage.png" title="example image" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="row">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.html path="assets/img/3/3-review.png" title="example image" class="img-fluid rounded z-depth-1" %}
    </div>
</div>

- Detail information:
  - Movie poster
  - Title, release year & description
  - Ratings & movie provider
  - Related video on YouTube
- Review section:
  - Input field for content & nickname
  - List of previous reviews
  - Multi-row supported

### Search & Explore & Recommend
<div class="row">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.html path="assets/img/3/3-search.png" title="example image" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="row">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.html path="assets/img/3/3-explore.png" title="example image" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="row">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.html path="assets/img/3/3-recommend.png" title="example image" class="img-fluid rounded z-depth-1" %}
    </div>
</div>

### Log in via Google

We implement Google OAuth platform for seamless login experience.