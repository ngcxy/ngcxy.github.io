---
layout: page
title: 'BlogStract: a blogging platform'
description: a full-stack blog application, with Django for the backend, React for the frontend, PostgreSQL for the database
img: assets/img/2/2-homepage.png
importance: 49
category: 
giscus_comments: true
---

Visit the [Website](my-blog-app-silk.vercel.app)

Code Link on [GitHub](https://github.com/ngcxy/Blog-app)

This Full-Stack Blog Website project is a dynamic and user-friendly application providing seamless experience for both blog creators and readers.

### Features
- Homepage displaying all blogs in thumbnail cards
- Detail page for every single blog showing the content
- User dashboard allowing users to browse and edit blogs
- A built-in authentication system based on JSON Web Tokens

<div class="row">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.html path="assets/img/2/2-homepage.png" title="example image" class="img-fluid rounded z-depth-1" %}
    </div>
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.html path="assets/img/2/2-detailPage.png" title="example image" class="img-fluid rounded z-depth-1" %}
    </div>
</div>

<div class="row">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.html path="assets/img/2/2-signup.png" title="example image" class="img-fluid rounded z-depth-1" %}
    </div>
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.html path="assets/img/2/2-signin.png" title="example image" class="img-fluid rounded z-depth-1" %}
    </div>
</div>


<div class="row">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.html path="assets/img/2/2-dashboard.png" title="example image" class="img-fluid rounded z-depth-1" %}
    </div>
</div>

---

### Tools

- **Frontend**: Built with React, **Backend server**: Powered by Django REST Framework
- Database: Postgresql (with [supabase](https://supabase.com/))
- Media storage for image: AWS S3
- User authentication: JWT token
- React ui library: [Material UI](https://mui.com/)