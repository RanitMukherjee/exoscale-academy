---
docType: "Course"
title: "Using Object Storage"
description: "Store application assets in Object Storage"
courseTitle: "Using Object Storage"
weight: 8
banner: "98e16360-a366-4b78-8e0a-031da07fdacb/images/exoscale-icon.svg"
tags: [kubernetes, helm, exoscale]
level: [introductory]
categories: [exoscale]
---

In this section, you’ll use Simple Object Storage (SOS), an Exoscale AWS S3-compatible storage service, to store images used by the VotingApp.

## Using images instead of labels

The VotingApp allows dynamic configuration of labels and images. The default configuration is below; it uses string labels for cats and dogs.

```bash
# Dynamic configuration
items:
  labels:
    a: "cats"
    b: "dogs"
  images:
    enabled: false
    a: https://sos-ch-gva-2.exo.io/votingapp/items/a.png
    b: https://sos-ch-gva-2.exo.io/votingapp/items/b.png
```

Modify your current *values.yaml* file, so it allows using images instead of labels.

```yaml {filename="values.yaml"}
items:
  images:
    enabled: true
```

> [!WARNING]
> By default, it uses images available at the following URLs:
> - https://sos-ch-gva-2.exo.io/votingapp/items/a.png
> - https://sos-ch-gva-2.exo.io/votingapp/items/b.png

Next, upgrade the application.

```bash
helm upgrade --install vote oci://registry-1.docker.io/voting/app --version v1.0.36 --namespace vote --create-namespace -f values.yaml
```

The *vote-ui* and *result-ui* web interfaces should now display images as follows:

![vote-ui-sos](vote-ui-sos)

![result-ui-sos](result-ui-sos)

In the next part, you’ll use your images.

## Create a bucket

First, go to the Storage section.

![buckets-sos](buckets-sos)

Next, create a bucket.

![create-buckets-sos](create-buckets-sos)

> [!WARNING]
> Since bucket names are global, do not use generic names, as somebody may already use them.

![display-buckets-sos](display-buckets-sos)

Next, explore the bucket’s detailed page and select the “Upload Object” action.

![upload-object](upload-object)

Select two images from your local machine.

> [!INFO]
> Please use square PNG images

![votingapp-bucket-tom](votingapp-bucket-tom)

Change the “content-type” header into “image/png” for each image.

![content-type-sos](content-type-sos)

Next, add the PUBLIC_READ ACL to make the images public.

![public-read-sos](public-read-sos)

From the image’s detail page, get the public URL and use it in the *values.yaml* file as follows:

```yaml {filename="values.yaml"}
items:
  images:
    enabled: true
    a: https://sos-ch-gva-2.exo.io/votingapp-bucket-tom/argocd.png  # Use the URL of your image
    b: https://sos-ch-gva-2.exo.io/votingapp-bucket-tom/flux.png    # Use the URL of your image
```

```bash
helm upgrade --install vote oci://registry-1.docker.io/voting/app --version v1.0.36 --namespace vote --create-namespace -f values.yaml
```

![vote-sos](vote-sos)

![result-sos](result-sos)

> [!INFO]
> Want to know more about Exoscale Object Storage offering? Visit the [documentation](https://community.exoscale.com/product/storage/) to get the entire feature set.

