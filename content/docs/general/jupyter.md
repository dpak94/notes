---
layout: post
title: Jupyter
permalink: /jupyter/
draft: true
---

# Jupyter

![Jupyter](https://miro.medium.com/v2/resize:fit:720/format:webp/1*wOHyKy6fl3ltcBMNpCvC6Q.png)

## Displaying HTML Content in Notebook

```python
from IPython.display import HTML

html_data = """
<img src = 'http://python.org/images/python-logo.gif'/><br/><button>Click Me</button>
"""

html = HTML(data = html_data)
html # Displays the HTML object in Jupyter Notebook
```

## Displaying Local File Link in Notebook

```python
from IPython.display import FileLink

file_link = FileLink(path='./hello_jupyter.ipynb') # FileLink Object
file_link # Prints the FileLink Objects
```

## Displaying Local Directory Files in Notebook

```python
from IPython.display import FileLinks

file_links = FileLinks('.') # FileLinks Object created
display(file_links)
```

## Playing Local Audio File in Notebook

```python
from IPython.display import Audio

Audio(data=None, filename=None, url=None, embed=None, rate=None, autoplay=False)
# filename is the local audio filepath
url is the audio stream link
```

## Playing YouTube Video in Notebook

```python
from IPython.display import YouTube as YT
yt_video = YT('gsjijkrngr')
display(yt_video)
```
