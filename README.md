# Welcome to BIODICA website

### Add a new post to the news section   

* Go to the **_posts/** folder and create a new markdown file (.md) which will contain your new post. It shoud be entitled **year-month-day-name.md** (e.g 2022-01-04-welcome-to-biodica.md).

* Add the following header in your file:   

	```
	---
	layout: post
	title:  "your_title"
	author: your name
	---
	```

* Following this header you can write any content that you like.

### Add a new tutorial

* Go to **_docs/tutorials/** and create a new markdown file (.md) which will contain your new tutorial. It should be entitled **file_name.md** (e.g tuto_rbh.md).  

* Add the following header in your file:

	```
	---
	layout: page
	title: your title
	permalink: /docs/tutorials/file_name/
	author: your name (optional)
	---

	<div class = "container">
    	    <h2>{{ page.title }}</h2>
    	    <p>{% if page.author %}{{ page.author }}{% endif %}</p>
	</div>
	<br>
	```

* Following this header you can write any content that you like.   

* Choose and image which illustrates this tutorial well and save it to **assets/img/your_image.png**

* Open **_docs/tutorials.html** and go to the `<div class="row">` section and add:   

	```
	<div class="responsive">
    	  <div class="gallery">
      	    <div class="image">
              <a href="{{ "/docs/tutorials/file_name/" | relative_url }}">
              <img src="../../assets/img/your_image.png" class="img-responsive" alt="Cerulean"></a>
            </div>
            <div class="desc">
              Brief description/brief title for your tutorial
            </div>
          </div>
        </div>
	```

### Add a new page to the docs section
