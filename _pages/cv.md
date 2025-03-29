---
layout: archive
title: "CV"
permalink: /cv/
author_profile: true
redirect_from:
  - /resume
---

{% include base_path %}

General Information
======
* **Full Name:** José Manuel de Frutos  
* **Languages:** Spanish, French, English  

Education
======
* **2023-2027(expected):** Ph.D. in Pure and Applied Mathematics, University Carlos III de Madrid, Spain. Leveraged rank statistics to develop novel loss functions for generative machine learning models.
* **2020:** Master’s degree, University Autónoma of Madrid, Madrid, Spain
  * Stochastic processes and advanced statistics.
  * Numerical methods and advanced PDEs.
  * [Master's thesis](/files/TFM2020_07_07jmdefrutos.pdf) on the mathematical foundations of image segmentation.
* **2018:** Double Bachelor in Mathematics and Computer Science, University Autónoma of Madrid, Madrid, Spain
  * Foundations of mathematics and computer science.
  * PDEs, numerical methods, statistics, AI/ML, algorithm analysis.
  * C/C++, Java, Python.
  * [Bachelor thesis](/files/TFG_MAT.pdf) on geometric measure theory.
* **2016:** Internacional exchange program at École Polytechnique, Paris, France
  * Focused on Mathematics, Computer Science, and Economy.


Work experience
======
* **2023 - Present:** Ph.D. Student in Machine Learning and Bayesian Filtering  
  * **Institution:** University Carlos III of Madrid, Madrid, Spain  
  * **Research Focus:** Deep Learning models applied to filtering methods  
  * **Project:** Development of Bayesian filtering methods using Deep Learning  
    * **Technologies:** ParticleFilter, Bayesian filtering, deep learning, generative models  
    * **Tools:** Python (pyTorch, Jax), Julia (Flux)  
    * **Publications:** AIStats2024 (published), Pattern Recognition (submitted), NeurIPS (in preparation)

* **2020 - 2023**: Full Stack Software Engineer at *Devo inc*
  * R&D Software Engineer. Interactive searches team for logs management.
  * Performed and improved handling of queries.
  * **Implemented new mathematical operations for logs management:**
    * JavaScript, Java8, Nodejs, Jest, Mocha, SQL, ANTLR4.
* **Summer 2019:** Graduate Research on Soft Computing at *University of Cádiz, Cádiz, Spain*
  * Reduced SQL databases using soft computing algorithms and concept lattices.
* **Summer 2018:** CERN Openlab Internship at *CERN, Geneva, Switzerland*
  * Designed and implemented a new configuration management tool for the IT-CM-LCS group.
  * Ruby, Python, Puppet, Ansible, Grafana.
* **Summer 2018:** Severo Ochoa aid program – Introduction to Research at *Instituto de Ciencias Matemáticas (ICMAT)*
  * Developed fluid dynamics algorithms using Dedalus and PyMPI.
* **2017 - 2018:** Software Engineer at *European Southern Observatory, Antofagasta, Chile*
  * Installed Datalab for Observatory Logs, storing 1 petabyte per day (Elasticsearch, Cassandra, KairosDB, Puppet).
  * Installed and managed Data Analytic tools (ELK, Jupyter, Grafana, Kibana).
  * Set up a Reverse-Proxy security architecture using Nginx.
  * Coded anomaly detection algorithms for instrumental failures (Pandas, TensorFlow).
  * Performed data ingestion, extraction, and load (ETL) boosted by 1000x (Python3, Bash).
  * Data visualization using Matplotlib, Bokeh, Plotly.
  * Provided advice on new hardware acquisition with a budget of 40K Euros.
  
Publications
======
  <ul>{% for post in site.publications reversed %}
    {% include archive-single-cv.html %}
  {% endfor %}</ul>
  
Talks
======
  <ul>{% for post in site.talks reversed %}
    {% include archive-single-talk-cv.html  %}
  {% endfor %}</ul>
  
Teaching
======
  <ul>{% for post in site.teaching reversed %}
    {% include archive-single-cv.html %}
  {% endfor %}</ul>
  
Other Interests
======
* **Hobbies:** Basketball, travel, reading good books!
