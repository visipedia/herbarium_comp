# Herbarium Challenge 2020 - FGVC7

The Herbarium 2020 FGVC7 Challenge is to identify vascular plant species from a large, long-tailed collection herbarium specimens provided by the [New York Botanical Garden](https://www.nybg.org/plant-research-and-conservation/) (NYBG).

The Herbarium 2020 dataset contains over 1M images representing over 32,000 plant species. This is a dataset with a long tail; there are a minimum of 3 specimens per species, however, some species are represented by more than a hundred specimens. This dataset only contains vascular land plants which includes lycophytes, ferns, gymnosperms, and flowering plants. The extinct forms of lycophytes are the major component of coal deposits, ferns are indicators of ecosystem health, gymnosperms provide major habitats for animals, and flowering plants provide all of our crops, vegetables, and fruits.

<p float="left">
	<img src="./assets/specimen1.jpg" width=150>
	<img src="./assets/specimen2.jpg" width=150>
	<img src="./assets/specimen3.jpg" width=150>
	<img src="./assets/specimen4.jpg" width=150>
	<img src="./2020/assets/specimen5.jpg" width=150>
</p>

## Background
The New York Botanical Garden (NYBG) herbarium contains more than 7.8 million plant and fungal specimens. Herbaria are a massive repository of plant diversity data.  These collections not only represent a vast amount of plant diversity, but since herbarium collections include specimens dating back hundreds of years, they provide snapshots of plant diversity through time.  The integrity of the plant is maintained in herbaria as a pressed, dried specimen; a specimen collected nearly two hundred years ago by Darwin looks much the same as one collected a month ago by an NYBG botanist.  All specimens not only maintain their morphological features but also include collection dates and locations, and the name of the person who collected the specimen.  This information, multiplied by millions of plant collections, provides the framework for understanding plant diversity on a massive scale and learning how it has changed over time.

The teams with the most accurate models will be contacted, with the intention of using them on the un-named plant collections in the NYBG herbarium collection, and assessed by the NYBG plant specialists.

## About
This is an FGVC competition hosted as part of the [FGVC7](https://sites.google.com/corp/view/fgvc7/home) workshop at CVPR 2020 and sponsored by [NYBG](https://www.nybg.org/plant-research-and-conservation/).


## Kaggle
The leaderboard is being hosted on Kaggle ([challenge page](https://www.kaggle.com/c/herbarium-2020-fgvc7)).

## Dates
|||
|------|---------------|
Competition Starts|March 9, 2020|
Entry Deadline|May 4, 2020|
Team Merger Deadline|May 4, 2020|
Final Submission Deadline|May 11, 2020|

## Evaluation
Competition submissions are evaluated using the [macro F1 score](https://scikit-learn.org/stable/modules/generated/sklearn.metrics.f1_score.html).

F1 is calculated as follows:

<img src="https://render.githubusercontent.com/render/math?math=F_1 = 2 * \frac{precision * recall}{precision %2B recall}">

where:

<img src="https://render.githubusercontent.com/render/math?math=precision = \frac{TP}{TP %2B FP}">

<img src="https://render.githubusercontent.com/render/math?math=recall = \frac{TP}{TP %2B FN}">

In "macro" F1 a separate F1 score is calculated for each `species` value and then averaged.

### Submission File Format

For each image `Id`, you should predict the image label in the `Predicted` column. The submission file should have the following format:

    Id,Predicted
    0,0
    1,27
    2,42
    ...

## Data
### Terms of Use
* You will use the data only for non-commercial research and educational purposes.
* You will NOT distribute the images.

### Dataset Details
The dataset is hosted on [Kaggle](https://www.kaggle.com/c/herbarium-2020-fgvc7/data).

The training and test set contain images of herbarium specimens, from over 32,000 species of vascular plants. Each image contains exactly one specimen. The text and barcode labels on the specimen images have been blurred to remove category information in the image.

The data has been approximately split 80%/20% for training/test. Each category has at least 1 instance in both the training and test datasets. Note that the test set distribution is slightly different from the training set distribution. The training set contains species with hundreds of examples, but the test set has the number of examples per species capped at a maximum of 10.

Each image has different image dimensions, with a maximum of 1000 pixels in the larger dimension. These have been resized from the original image resolution. All images are in JPEG format.

### Dataset Format
This dataset uses the [COCO dataset format](http://cocodataset.org/#format-data) with additional annotation fields. In addition to the species category labels, we also provide region and supercategory information.

The training set metadata (`train/metadata.json`) and test set metadata (`test/metadata.json`) are JSON files in the format below. Naturally, the test set metadata file omits the "annotations", "categories" and "regions" elements.

	{
	  "annotations" : [annotation],
	  "categories" : [category],
	  "images" : [image],
	  "info" : info,
	  "licenses": [license],
	  "regions": [region]
	}

	info {
	  "year" : int,
	  "version" : str,
	  "url": str,
	  "description" : str,
	  "contributor" : str,
	  "date_created" : datetime
	}

	image {
	  "id" : int,
	  "width" : int,
	  "height" : int,
	  "file_name" : str,
	  "license" : int
	}

	annotation {
	  "id": int,
	  "image_id": int,
	  "category_id": int,
	  # Region where this specimen was collected.
	  "region_id": int
	}

	category {
	  "id" : int,
	  # Species name
	  "name" : str,
	  # We also provide the super-categories for each species.
	  "family": str,
	  "genus": str
	}

	region {
	  "id": int
	  "name": str
	}

	license {
	  "id": 1,
	  "name": str,
	  "url": str
	}

The training set images are organized in subfolders `train/<subfolder1>/<subfolder2>/<image id>.jpg`.

The test set images are organized in subfolders `test/<subfolder>/<image id>.jpg`.

## Guidelines
The general rule is that participants should only use the provided training and validation images for training models to classify the test images. We do not want participants crawling the web in search of additional data or using previous versions of this dataset. Pretrained models may be used to construct the algorithms from publicly available academic datasets (e.g. ImageNet, iNaturalist 2017-2018). Please specify any and all external data and/or models used for training when uploading results.

Participants are allowed to collect additional annotations on the provided training sets. Participants are not allowed to collect annotations on the test set. Teams should specify that they collected additional annotations when submitting results.

## About
This is an FGVCx competition hosted as part of the [FGVC7](https://sites.google.com/corp/view/fgvc7/home) workshop at CVPR 2020 and supported by the [New York Botanical Garden](https://www.nybg.org/plant-research-and-conservation/).

### Acknowledgements
Data is provided by Barbara Ambrose and Melissa Tulig (New York Botanical Garden).
