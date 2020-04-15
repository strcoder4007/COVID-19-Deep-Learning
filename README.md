# Detecting covid-19 using Xray images

##Collecting data

###Positive Covid-19 X-rays

[This](https://github.com/ieee8023/covid-chestxray-dataset) repository currently contains 68 covid-positive xrays as well as of MERS, SARS, and ARDS.

```python
python build_dataset.py -m <dataset folder path> -o <output path>
```

###Negative Covid-19 X-rays

[Kaggle chest xray dataset](https://www.kaggle.com/paultimothymooney/chest-xray-pneumonia).

We select 68 random images from the above dataset to keep balance.


##Training the model

I use VGGNet which is pre-trained on the imagenet dataset.

```python
python trainModel.py -d <dataset path>
```

![plot](https://user-images.githubusercontent.com/41234408/77198206-88f8ae80-6b0c-11ea-8f46-7dd74b4c5a78.png)

##Detection


```python
python detectCovid.py -i <input image path> -m <trained model path>
```

This will give an output with image labeled as covid-positive or covid-negetive.

##Output

For exmaple, for the image [covid1.jpeg], which is covid-positive.

```python
python detectCovid.py -i test-data/covid1.jpeg -m model.h5
```

![Screenshot from 2020-03-21 00-48-17](https://user-images.githubusercontent.com/41234408/77198931-f0632e00-6b0d-11ea-8233-1c52cad25b30.png)


For the image [normal1.jpeg], which is covid-negetive, I got the following output:

```python
python3 detectCovid.py -i test-data/normal1.jpeg -m model.h5
```

![Screenshot from 2020-03-21 00-51-53](https://user-images.githubusercontent.com/41234408/77199111-4fc13e00-6b0e-11ea-95a5-224b0e78d2fa.png)
