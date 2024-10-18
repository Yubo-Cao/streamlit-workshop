---
# You can also start simply with 'default'
theme: seriph
# random image from a curated Unsplash collection by Anthony
# like them? see https://unsplash.com/collections/94734566/slidev
background: #ffffff
# some information about your slides (markdown enabled)
title: StreamLit Workshop
# apply unocss classes to the current slide
class: text-center
# https://sli.dev/features/drawing
drawings:
  persist: false
# slide transition: https://sli.dev/guide/animations.html#slide-transitions
transition: slide-left
# enable MDC Syntax: https://sli.dev/features/mdc
mdc: true
# take snapshot for each slide in the overview
overviewSnapshots: true

addons:
    - slidev-addon-qrcode
---


<h1 class="mx-auto !text-primary">
StreamLit Workshop
</h1>

<div class="flex items-center justify-center">
<QRCode
    :width="128"
    :height="128"
    type="svg"
    data="https://forms.gle/oEg292Cv9Hp1ivke6"
    :margin="10"
    :imageOptions="{ margin: 10 }"
/>
</div>

<div class="max-w-xl mx-auto text-slate-600">
  Sharing StreamLit, a Python library that makes it easy to create and share machine learning and data science application
</div>

<div class="pt-12">
  <span @click="$slidev.nav.next" class="px-2 py-1 rounded cursor-pointer" hover="bg-white bg-opacity-10">
    Yubo Cao
    <carbon:chevron-right class="animate-pulse"/>
  </span>
</div>

<!--
The last comment block of each slide will be treated as slide notes. It will be visible and editable in Presenter Mode along with the slide. [Read more in the docs](https://sli.dev/guide/syntax.html#notes)
-->

---
transition: slide-left
---

# Attendance

<div class="flex items-center justify-center h-full">
<QRCode
    :width="256"
    :height="256"
    type="svg"
    data="https://forms.gle/oEg292Cv9Hp1ivke6"
    :margin="10"
    :imageOptions="{ margin: 10 }"
/>
</div>

---
transition: slide-left
---


# Table of contents

<Toc minDepth="1" maxDepth="2" columns="2"></Toc>

---
transition: slide-left
---

# Scenario

- You have built an algorithm, but it's only accessible through the Jupyter Notebook.

```py
result = []

for group in tqdm(hg38_annot.groupby("transcript_id")):
    x, y = construct_entry(group)
    if x is not None:
        y_hat = model(x.unsqueeze(0)).argmax(2).squeeze(0)
        result.append( { "x": x, "y": y, "y_hat": y_hat, } )
```

- You don't know web development (or don't have time to build a full-fledged web app).
- Yet, you need to share the algorithm with your team or the world.
  - Science fair
  - Journal publication
  - HackGwinnett, TSA, FBLA, etc.


---
transition: slide-left
level: 2
---

# StreamLit

StreamLit is a Python library that makes it easy to create and share web apps for your machine learning and data science projects.

<div class="flex flex-row gap-4 items-center mx-auto w-fit">
  <img v-click src="https://streamlit.io/images/brand/streamlit-mark-color.png" alt="StreamLit Logo" class="w-24">
  <div class="p-12 max-w-lg">
    <img v-click src="/images/streamlit-example-1.png" alt="StreamLit Example">
  </div>
</div>

---
transition: slide-left
level: 2
---

# StreamLit Cont'd

- Only minimal efforts is needed to convert the Jupyter Notebook to a web app.

<!-- spacer -->
<div class="h-8"></div> 

```py
    import streamlit as st
    import pandas as pd

    st.title("AP Micro Analysis Example")

    col1, col2 = st.columns([0.3, 0.7])
    with col1:
        q_min = st.slider("Minimum quantity", 10, 3000, 10)
        q_max = st.slider("Maximum quantity", 10, 3000, 3000)
    with col2:
        st.line_chart(
            pd.read_csv("costs.csv").set_index("Quantity").loc[q_min:q_max]
        )
```


---
transiton: slide-left
layout: image-right
image: /images/streamlit-side.png
level: 1
---

# Project

In this workshop, we will build a StreamLit app that:

- Takes a image from user.
- Identify the text in the image.
- Display the text in the image.

---
layout: iframe-right
url: https://embed.deepnote.com/700ca279-f03d-44b5-8ee9-c6f4c054c1fe/76ba62bfc9794342b64ef523b7c87aa4/81ac8fcb483146639ff543dd4639c95b?height=693.6666870117188
level: 2
---

# Installation

Create an account in [Deepnote](https://deepnote.com) and create a new project.

<div class="w-20 my-4 fill-blue-400">
<svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 695 120" class="text-blue-400"><path d="M160.2 19.96h32.4c27.48 0 40.1 13.96 40.1 39.23s-15.14 40.56-40.1 40.56h-32.4V19.96zm15.13 12.63v54.65h16.07c18.72 0 26.15-10.11 26.15-28.06 0-18.75-7.83-26.6-26.95-26.6h-15.27zm64.92 36.7c0-21.14 11.95-33.64 31.47-33.64 18.85 0 28.01 11.44 28.01 28.59 0 2.39 0 5.19-.26 8.38h-45.01c1.06 11.3 6.77 17.02 17.39 17.02 9.96 0 13.41-4.79 15.13-10.77l12.22 3.46c-2.92 11.3-10.75 19.02-27.48 19.02-19.12-.01-31.47-11.18-31.47-32.06zm14.34-6.25h32c-.53-10.77-5.31-16.36-15.27-16.36-9.69.01-15.4 5.19-16.73 16.36zm53.11 6.25c0-21.14 11.95-33.64 31.47-33.64 18.85 0 28.01 11.44 28.01 28.59 0 2.39 0 5.19-.26 8.38h-45.01c1.06 11.3 6.77 17.02 17.39 17.02 9.96 0 13.41-4.79 15.13-10.77l12.22 3.46c-2.92 11.3-10.75 19.02-27.48 19.02-19.12-.01-31.47-11.18-31.47-32.06zm14.34-6.25h32c-.53-10.77-5.31-16.36-15.27-16.36-9.69.01-15.4 5.19-16.73 16.36zm93.6 38.43c-11.42 0-18.72-7.45-21.77-18.35h-.93v36.83h-14.21v-82.7h14.21v16.22h.93c3.32-10.77 10.22-17.82 21.51-17.82 14.74 0 22.97 11.7 22.97 32.98s-8.63 32.84-22.71 32.84zm8.63-32.84c0-13.56-4.78-20.08-15.27-20.08-9.82 0-16.06 6.92-16.06 17.82v4.79c0 10.51 6.37 17.69 15.93 17.69 10.49-.01 15.4-6.79 15.4-20.22zm39.57 31.11h-14.21v-62.5h13.94v16.49h1.2c3.45-11.57 11.42-18.09 21.91-18.09 13.01 0 19.25 8.78 19.25 22.34v41.76h-14.21V61.71c0-7.58-3.32-13.17-11.95-13.17-9.56 0-15.93 6.38-15.93 15.82v35.38zm52.71-31.38c0-20.61 12.35-32.71 31.73-32.71 19.12 0 31.47 12.1 31.47 32.71 0 20.48-11.68 33.11-31.47 33.11-20.05 0-31.73-12.63-31.73-33.11zm14.34-.13c0 12.9 5.31 20.88 17.26 20.88 11.82 0 17.39-7.98 17.39-20.88s-5.84-20.48-17.39-20.48-17.26 7.58-17.26 20.48zm63.73-19.42h-8.76V37.25h8.76V20.36h14.34v16.89h18.32v11.57h-18.32v29.92c0 6.12 2.26 9.31 8.5 9.31 3.19 0 5.97-.66 9.03-1.6l1.73 12.77c-4.65 1.46-7.83 2.26-14.07 2.26-13.67 0-19.52-9.04-19.52-20.74V48.81zm40.1 20.48c0-21.14 11.95-33.64 31.47-33.64 18.85 0 28.01 11.44 28.01 28.59 0 2.39 0 5.19-.26 8.38h-45.01c1.06 11.3 6.77 17.02 17.39 17.02 9.96 0 13.41-4.79 15.13-10.77l12.22 3.46c-2.92 11.3-10.75 19.02-27.48 19.02-19.13-.01-31.47-11.18-31.47-32.06zm14.34-6.25h32c-.53-10.77-5.31-16.36-15.27-16.36-9.7.01-15.41 5.19-16.73 16.36z" class="fill-blue-600"></path><path fill-rule="evenodd" clip-rule="evenodd" d="M42.35 0c-2.18.01-3.14 0-3.14 0C23.9 22.23 15.31 34.69 0 56.92h36.08c3.07 0 6.44.11 9.91.45l-10.7 14.94L0 120h50.2s.03-.01.05-.01c-.02 0-.05.01-.05.01s69.8-2.14 69.8-63.4C120 2.93 57.73-.06 42.35 0z" class="fill-blue-500"></path><path d="M50.2 120s29.15-5.48 29.15-32.64c0-22.25-17.66-28.47-33.36-29.99l-10.7 14.94L0 120h50.2m15.23-14.01c.03-.05.06-.09.09-.13-.03.04-.06.09-.09.13z" fill-rule="evenodd" clip-rule="evenodd" class="fill-blue-400"></path><path d="M35.29 72.31c22.15 0 36.64 10.38 33.71 24.93C66.06 111.79 50.2 120 50.2 120s29.15-5.48 29.15-32.64c0-22.25-17.66-28.47-33.36-29.99l-10.7 14.94zM50.2 120z" class="css-746bdy"></path><path fill-rule="evenodd" clip-rule="evenodd" d="M0 56.92C15.31 34.69 23.9 22.23 39.22 0c0 0 .96.01 3.14 0C57.73-.06 120 2.93 120 56.6c0 61.27-69.8 63.4-69.8 63.4s29.15-5.47 29.15-32.64-26.33-30.44-43.27-30.44H0z" class="fill-blue-500"></path></svg>
</div>

<v-click>
Create a new cell and type the following to install StreamLit using pip:

```sh
%pip install streamlit
```
</v-click>

<v-click>
Install necessary libraries for this project:

```sh
!apt-get update && apt-get install ffmpeg libsm6 libxext6 -y
%pip install paddlepaddle paddleocr
```
</v-click>


---
level: 2
layout: image-right
image: /images/widget_gallery.png
---

# StreamLit Widgets

- StreamLit provides a set of building blocks, called **widgets**, to build the web app.
- We will use the following widgets in this project:
  - `st.file_uploader`: Upload an image file.
  - `st.image`: Display the image.
  - `st.write/st.markdown`: Display text.

---
level: 2
layout-class: gap-4
---

# Mental Model

```py {all|1|3|4|5|all}
import streamlit as st

st.file_uploader("Upload a file", type=["png", "jpg", "jpeg"])
st.image("hg-logo.png", caption="HackGwinnett Logo", use_column_width=True, clamp=True)
st.write('**Hello,** *world!* :sunglasses:')
```

<v-clicks at="1">

- Imports the StreamLit library.
- Places a file uploader widget on the page.
- Places a image widget on the page.
- Places a text widget on the page.
- Whenever the source code is changed, or the user interacts with the widgets (*e.g.,* uploading a file), StreamLit will remove all the widgets and run the script from the beginning.

</v-clicks>

---
level: 2
layout: image-right
image: /images/write_example.png
---

# `st.write`

Write text, images, dataframe (table), *etc.* to the web app.

```py
st.write("Hello, *Ms. R!*")

st.write(pd.DataFrame(
    {
        "A": [1, 2, 3],
        "B": [4, 5, 6],
    }
))

st.write("![HackGwinnett Logo](hg-logo.png)")
```

---
level: 2
layout: image-right
image: /images/fu_example.png
---

# `FileUploader`

Display a file uploader widget.

```py
st.file_uploader("Upload a file", type=["png", "jpg", "jpeg"])

st.file_uploader("Upload a pdf file", type="pdf")
```

- `label`: The label of the widget.
- `type`: Default to `None`, allowing all file types. Otherwise, a list of file extensions/a single file extension to be accepted.

---
level: 2
layout: image-right
image: /images/image_example.png
---

# `st.image`

Display an image.

```py
st.image("hg-logo.png", caption="HackGwinnett Logo", use_column_width=True, clamp=True)
```

- `image`: The image to be displayed.
- `caption`: The caption of the image.
- `use_column_width`: Default to `False`. If `True`, the image will be displayed in the full width of the column, *i.e.,* the parent container.
- `clamp`: Default to `False`. If `Treu`, clamp of the pixel to the range [0, 255]; otherwise, error will be thrown for invalid pixel values.


---
level: 2
---

# OCR

- Optical Character Recognition (OCR) is the process of converting images of text into machine-encoded text.
- This seminar is **not** about OCR, AI, or ML. Hence, PaddleOCR will be used to identify the text in the image.

```py
# ocr = PaddleOCR()

def extract_text(ocr, image_path: str):
  result = ocr.ocr(image_path)

  text = ""
  for line in result:
      for word in line:
          text += word[1][0] + " "
      text += "\n"
  
  return text
```

---
layout: two-cols-header
layout-class: gap-4
level: 1
---


# Our First StreamLit App

::left::

```py {1|all}
%%writefile app.py
import streamlit as st
from paddleocr import PaddleOCR
from PIL import Image
from tempfile import NamedTemporaryFile

ocr = PaddleOCR()

st.title("Accessble OCR")

img = st.file_uploader("Upload an image", type=["jpg", "png", "jpeg"])

if img:
    img = Image.open(img)

    st.image(img, caption="Uploaded Image", use_column_width=True)

    with NamedTemporaryFile(delete=False, suffix=".jpg") as temp:
        img.save(temp.name, format="JPEG")
        st.write(extract_text(ocr, temp.name))
```

```
!streamlit run app.py --server.port 8080
```

::right::

<img src="/images/notebook_settings.png" alt="Notebook Settings" class="w-40 mb-8 mx-auto">

<ul>
<li>
Click <carbon:overflow-menu-horizontal class="inline-block w-6 h-6"/> near the "Stop machine" on the lower left project pane.
</li>
<li>
Set the incoming connections to "on."
</li>
</ul>



---
level: 2
---

# Issues

- The favicon is not set.
- Application froze when the image is uploaded.
- When refresh, application will take a long-time to load (due to the OCR process).

---
level: 2
---

````md magic-move

```py
import streamlit as st
from paddleocr import PaddleOCR
from PIL import Image
from tempfile import NamedTemporaryFile

ocr = PaddleOCR()

st.title("Accessble OCR")

img = st.file_uploader("Upload an image", type=["jpg", "png", "jpeg"])

if img:
    img = Image.open(img)

    st.image(img, caption="Uploaded Image", use_column_width=True)

    with NamedTemporaryFile(delete=False, suffix=".jpg") as temp:
        img.save(temp.name, format="JPEG")
        st.write(extract_text(ocr, temp.name))
```

```py
import streamlit as st
from paddleocr import PaddleOCR
from PIL import Image
from tempfile import NamedTemporaryFile

ocr = PaddleOCR()

# Set favicon to🔍
st.set_page_config(page_title="Accessible OCR", page_icon="🔍")

img = st.file_uploader("Upload an image", type=["jpg", "png", "jpeg"])

if img:
    img = Image.open(img)

    st.image(img, caption="Uploaded Image", use_column_width=True)

    with NamedTemporaryFile(delete=False, suffix=".jpg") as temp:
        img.save(temp.name, format="JPEG")
        st.write(extract_text(ocr, temp.name))
```

```py
import streamlit as st
from paddleocr import PaddleOCR
from PIL import Image
from tempfile import NamedTemporaryFile

# Set favicon to🔍
st.set_page_config(page_title="Accessible OCR", page_icon="🔍")

ocr = PaddleOCR()

img = st.file_uploader("Upload an image", type=["jpg", "png", "jpeg"])

if img:
    img = Image.open(img)

    st.image(img, caption="Uploaded Image", use_column_width=True)

    with NamedTemporaryFile(delete=False, suffix=".jpg") as temp:
        img.save(temp.name, format="JPEG")
        st.write(extract_text(ocr, temp.name))
```

```py
import streamlit as st
from paddleocr import PaddleOCR
from PIL import Image
from tempfile import NamedTemporaryFile

# Set favicon to🔍
st.set_page_config(page_title="Accessible OCR", page_icon="🔍")

# Cache the OCR model to reduce time between reload
@st.cache_resource
def initliaze_ocr():
    return PaddleOCR()
  
ocr = initliaze_ocr()

img = st.file_uploader("Upload an image", type=["jpg", "png", "jpeg"])

if img:
    img = Image.open(img)

    st.image(img, caption="Uploaded Image", use_column_width=True)

    with NamedTemporaryFile(delete=False, suffix=".jpg") as temp:
        img.save(temp.name, format="JPEG")
        st.write(extract_text(ocr, temp.name))
```

```py
import streamlit as st
from paddleocr import PaddleOCR
from PIL import Image
from tempfile import NamedTemporaryFile

# Set favicon to🔍
st.set_page_config(page_title="Accessible OCR", page_icon="🔍")

# Cache the OCR model to reduce time between reload
@st.cache_resource
def initliaze_ocr():
    return PaddleOCR()
  
ocr = initliaze_ocr()

img = st.file_uploader("Upload an image", type=["jpg", "png", "jpeg"])

if img:
    img = Image.open(img)

    st.image(img, caption="Uploaded Image", use_column_width=True)

    with NamedTemporaryFile(delete=False, suffix=".jpg") as temp:
        img.save(temp.name, format="JPEG")
        with st.spinner("Processing..."): # Add a spinner
            st.write(extract_text(ocr, temp.name))
```

````

---
level: 1
---

# Publish the App

- StreamLit provide a community cloud service to host the app for free.
- Push the code to GitHub, with `requirements.txt` specifying the dependencies.
- Register for an account in StreamLit Sharing, then upload the repository.

```sh
your_repository/
├── requirements.txt
└── your_app.py
```

---
level: 1
---

# When StreamLit is not enough

- Now, we want to show the image the bbox of the text.
- StreamLit doesn't provide a widget to draw on the image.
- We can use `cv2` to draw the bbox on the image.

```py
import cv2

def draw_bbox(image, result):
    for line in result:
        for word in line:
            cv2.rectangle(image, word[0][0], word[0][2], (0, 255, 0), 2)
    return image
```

---
level: 1
layout: two-cols
layout-class: gap-8
---

# When StreamLit is not enough Cont'd

```py
img_empty = st.empty()
img_empty.image(img, caption="Uploaded Image", use_column_width=True)

# after many lines

img = draw_bbox(img, result)
img_empty.image(img, caption="Labelled Image", use_column_width=True)
```

- `empty` will only have one widget, hence, when `image` is called, the previous image will be replaced by the new image.

::right::

## Limitations

- StreamLit is not completely reactive. As seen, the `.empty` and `.spinner` leave side effects that might be troublesome in large applications.
- Custom widget might be needed for more complex applications. In our use case, we either abuse `bokeh`, `plotly`, or we would hand-roll our own widget with Node.js.



---
layout: cover
background: #ffffff
---

# Thank you!

[GitHub](https://github.com/hackgwinnett), [Website](https://hackgwinnett.org)