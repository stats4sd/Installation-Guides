---
layout: default
section: e.g. Tools
title: My Title
permalink: /abc/xyz
---

# Content Header

If you want to link this page correctly the page title here should match the page
title in `data/pagesMeta`

# Linking headers {#linkID}

You can build links to parts of the same page (# link) by adding and id to the
heading element and adding corresponding link to the `pagesMeta` subsection.
It builds the link in the usual way, e.g.  
<a href="#linkID">Link</a>

# Images

Images should be stored in assets folder and can be put inline as:
![image](/assets/images/Stats4SD_red.png)

By default they will fill the page width, so to display either upload a smaller image or use one of the following classes (will cap max width):

.size--large - 600px
.size--medium-large - 500px
.size--medium - 400px
.size--medium-small - 300px
.size--small - 200px

e.g.
![image](/assets/images/Stats4SD_red.png){:class="size--small"}
