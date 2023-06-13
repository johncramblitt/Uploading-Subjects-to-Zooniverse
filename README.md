## Best Practices for Uploading Images to a Zooniverse Subject Set
It is easy to upload small batches of images through the Zooniverse website, but when uploading large numbers of images, the Panoptes command line interface is 
more effective. Read more on how to utilize the Panoptes Client here. 

#### Setup
To start, install the panoptes client. Installing python-magic and python-magic-bin may also be required. 
Set the working directory to the filepath where the images to be uploaded are installed. Create an empty subject-set on the Zooniverse website and take note of the numerical subject ID. 

#### Create a Manifest
A manifest is a csv file that allows the inclusion metadata with image uploads. This will be essential later on for data processing. The manifest file should be a csv 
with two columns, one titled "metadata" with the image datetimes, and one titled "filepath" with the image filepath. This will allow Zooniverse to grab the required files 
as well as any information included in the metadata column. For the Snow Spotter Project, it is best practice for the metadata to be only the datetime as this allows for simpler processing later on.
However, as long as the datetime is included somewhere within the metadata, it can be extracted from the data export. 

#### Upload Images
Run the following command in the command line, where subjectid is the unique subject-set ID assigned by Zooniverse and filename.csv is the name of the manifest file. 
```python
panoptes subject-set upload-subjects subjectid filename.csv
```
If the upload fails, follow the instructions provided to save the yaml file. Resume the upload with the following code, where subjectid is the same subject-set ID assigned by Zooniverse and filename.yaml is the name of the file 
just saved following the failed upload.  
```python
panoptes subject-set upload-subjects subjectod filename.yaml
```
