---
title: "Azure ML for Gender Coded Words in Google Image Searches"
excerpt: "Using Azure ML to assess the Gender coding of Google Image Searches"
collection: portfolio
---
## Project Background
One of my passions is being an advocate for women in STEM and I wanted to see how I could combine the two.
My idea was inspired from Invisible Women: Exposing Data Bias in a World Designed for Men by Caroline Criado-Perez and the notion that even “gender neutral” terms are in fact, gendered. One example she gave was the face that when people think of words such as “genius” it is more likely than not a male that is returned. I started to look into the issue, particularly as it deals with Google Image results and what gender is returned for search terms. I didn’t find very inspiring or trustworthy articles – a few old ones from the Sun or Huffington Post that were dated from 2012 or 2015. Surely things have changed since then! To test this hypothesis, I built a program that can digest a search term and return the first 100 Google images. Using Microsoft Azure Face program, it will determine the gender found in the photo and track if the term is male dominated, or female dominated.

This program was built using two key tech
1. [Microsoft Face API](Microsoft Face API (https://azure.microsoft.com/en-us/services/cognitive-services/face/): Detect and compare human faces through Azure
2. [Google Image Download Python Package](https://github.com/hardikvasa/google- images-download):This is a command line python program to search keyword/key-phrases on Google Images and optionally download images to your computer.


### Set Up Microsoft Azure Face APP
To use the Microsoft Azure Face API you need to create a sandbox through an azure account. Within the portal create a new Cognitive Services resource.

![resources](/images/gender/Picture1.png)

Within the portal, you will need to have access to the Keys to run the API
![keys](/images/gender/Picture2.png)

Now that we have access to the keys and have an appropriated resource, we can test the API connection in the correct region (West US 2 - westus2.api.cognitive.microsoft.com).
Creating a python file we can set up the following code, which will include the subscription key from the Azure Portal. The image that we will look at is:

![Example Image](/images/gender/Picture3.png)

This is done through the creation of a python file. We will run this program using the resource keys created above, accessing the image above hosted on Wikipedia. Within the Azure Face API there are many parameters that can be returned in the response, but for the purposes of this project we only need the gender parameter to be returned. We will print this response from the API.
```
import requests
import json
subscription_key = <your_key_here>
assert subscription_key

face_api_url = 'https://west2.api.cognitive.microsoft.com/face/v1.0/detect'
image_url = 'https://upload.wikimedia.org/wikipedia/commons/3/37/Dagestani_man_and_woman.jpg'

headers = {'Ocp-Apim-Subscription-Key': subscription_key}
params = {'returnFaceAttributes':'gender'}

response = requests.post(face_api_url,params=params,headers=headers,json=("url":image_url))
print(json.dumps(response.json()))
```
The API will return the following as a response for each of the faces detected in the image.
```
[{"faceId": "7418b025-8f8d-4faf-abf0-a0761f7eb4c5", "faceRectangle": {"width": 195, "top": 621, "height": 195, "left": 616}, "faceAttributes": {"gender": "male"}}, {"faceId": "50d887e7-6e59-4115-a97b-e16466e38377", "faceRectangle": {"width": 180, "top": 693, "height": 180, "left": 1503}, "faceAttributes": {"gender": "female"}}]
```

We can see that it returns an identification of both a male and a female in the photo. This photo was hosted online, but it can also be ran against local images (which will be important for the Google Image Download program). To do this we just need to update the headers to include Content-Type': 'application/octet-stream’.


## Install Google Image Download
The Google Image Download python package is a plug and play package, so I was able to install the python program and feed in a search term with ease. In the example below, we are creating a folder that will be labelled with the search term and include the first 20 photos from a google search of "genius".

```
search_term = "genius "
arguments = {"keywords":search_term,"limit":20}
absolute_image_paths = response.download(arguments)
```

![downloads folder](/images/gender/Picture4.png)
