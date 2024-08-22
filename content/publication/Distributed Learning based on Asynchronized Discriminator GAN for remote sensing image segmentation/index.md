---
title: 'Distributed Learning based on Asynchronized Discriminator GAN for remote sensing image segmentation'

# Authors
# If you created a profile for a user (e.g. the default `admin` user), write the username (folder name) here
# and it will be replaced with their full name and linked to their profile.
authors:
  - Mingkang Yuan
  - Ye Li


date: '2022-11-03T00:00:00Z'
doi: ''

# Schedule page publish date (NOT publication's date).
publishDate: '2023-01-03T00:00:00Z'

# Publication type.
# Accepts a single type but formatted as a YAML list (for Hugo requirements).
# Enter a publication type from the CSL standard.
publication_types: ['paper-conference']

# Publication name and optional abbreviated publication name.
publication: In *Proceedings of the 8th International Conference on Communication and Information Processing*
publication_short: In *ICCIP'22*

abstract: Remote sensing images are usually distributed in different departments and contain private information, so they normally cannot be available publicly. However, it is a trend to jointly use remote sensing images from different departments, because it normally enables the model to capture more information and remote sensing image analysis based on deep learning generally requires lots of training data. To address the above problem, in this paper, we apply a distributed asynchronized discriminator GAN framework (DGAN) to jointly learn remote sensing images from different client nodes. The DGAN is composed of multiple distributed discriminators and a central generator, and only the synthetic remote sensing images generated by the DGAN are used to train a semantic segmentation model. Based on DGAN, we establish an experimental platform composed of multiple different hosts, which adopts socket and multi-process technology to realize asynchronous communication between hosts, and visualize the training and testing process. During DGAN training, instead of original remote sensing images or convolutional network model information, only synthetic images, losses and labeled images are exchanged between nodes. Therefore, the DGAN well protects the privacy and security of the original remote sensing images. We verify the performance of the DGAN on three remote sensing image datasets (City-OSM, WHU and Kaggle Ship). In the experiments, we take different distributions of remote sensing images in client nodes into consideration. The experiments show that the DGAN has a great capacity for distributed remote sensing image learning without sharing the original remote sensing images or the convolutional network model. Moreover, compared with a centralized GAN trained on all remote sensing images collected from all client nodes, the DGAN can achieve almost the same performance in semantic segmentation tasks for remote sensing images.


tags:
  - DGAN, Remote sensing images, Privacy

# Display this page in the Featured widget?
featured: true

# Custom links (uncomment lines below)
# links:
# - name: Custom Link
#   url: http://example.org

url_pdf: ''

# Featured image
# To use, add an image named `featured.jpg/png` to your page's folder.
image:
  caption: 'Image credit: [**Unsplash**](https://unsplash.com/photos/pLCdAaMFLTE)'
  focal_point: ''
  preview_only: false

# Associated Projects (optional).
#   Associate this publication with one or more of your projects.
#   Simply enter your project's folder or file name without extension.
#   E.g. `internal-project` references `content/project/internal-project/index.md`.
#   Otherwise, set `projects: []`.
projects:
  - example

# Slides (optional).
#   Associate this publication with Markdown slides.
#   Simply enter your slide deck's filename without extension.
#   E.g. `slides: "example"` references `content/slides/example/index.md`.
#   Otherwise, set `slides: ""`.
slides: example
---

{{% callout note %}}
Click the _Cite_ button above to demo the feature to enable visitors to import publication metadata into their reference management software.
{{% /callout %}}

{{% callout note %}}
Create your slides in Markdown - click the _Slides_ button to check out the example.
{{% /callout %}}

Add the publication's **full text** or **supplementary notes** here. You can use rich formatting such as including [code, math, and images](https://docs.hugoblox.com/content/writing-markdown-latex/).