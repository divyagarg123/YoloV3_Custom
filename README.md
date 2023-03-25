# YoloV3_Custom

Clone the repo: https://github.com/divyagarg123/YoloV3_Copy
Create a folder called weights in the root (YoloV3) folder
Download from: https://drive.google.com/file/d/1vRDkpAiNdqHORTUImkrpD7kK_DkCcMus/view?usp=share_link
Place 'yolov3-spp-ultralytics.pt' file in the weights folder.

For custom dataset:

Clone this repo: https://github.com/miki998/YoloV3_Annotation_Tool
Follow the installation steps as mentioned in the repo.
For the assignment, download 25 images of each class.
Annotate the images using the Annotation tool.

Save the images in  data/customdata/images folder and labels in data/customdata/labels after annotating the images.

Image :

![image](https://user-images.githubusercontent.com/109232157/227699824-f27bb043-6b73-4764-a4fc-7787b3f3c111.png)
Label:

0 0.49333333333333335 0.4866666666666667 0.9688888888888889 0.41333333333333333

Change classes to 4 in custom.data

Change custom.names to have following classes:
pan
rollingpin
pestle
strainer

Change custom.txt to have locations of all the custom images.

For COCO's 80 classes, VOLOv3's output vector has 255 dimensions ( (4+1+80)*3). Now we have 4 class, so we would need to change it's architecture.
Copy the contents of 'yolov3-spp.cfg' file to a new file called 'yolov3-custom.cfg' file in the data/cfg folder.
Search for 'filters=255' (you should get entries entries). Change 255 to 27 = (4+1+4)*3
Search for 'classes=80' and change all three entries to 'classes=4'
As we are working with very few samples. In such a case it is a good idea to change:
burn_in to 100
max_batches to 5000
steps to 4000,4500

Run this command python train.py --data data/customdata/custom.data --batch 10 --cache --cfg cfg/yolov3-custom.cfg --epochs 3 --nosave

Run command !python detect.py --conf-thres 0.1 --output data/custom_data/out_out to infer the results.

Below are the images for each class after annotation.

PAN

![image](https://user-images.githubusercontent.com/109232157/227700032-57ff45ff-7921-4117-8869-fed2c9773bfc.png)
![image](https://user-images.githubusercontent.com/109232157/227700058-ac275e0c-97a3-4354-afbd-320415dec6fe.png)

RollingPin

![image](https://user-images.githubusercontent.com/109232157/227700105-359392ec-f213-4d84-80a7-e1765265754a.png)
![image](https://user-images.githubusercontent.com/109232157/227700124-d462e64a-4349-4052-a33d-ca5bb1cf9fee.png)

Strainer:

![image](https://user-images.githubusercontent.com/109232157/227700147-8933e945-57d5-4428-a17d-3d9f2bcfcca7.png)
![image](https://user-images.githubusercontent.com/109232157/227700166-1919aa4e-933d-43cb-95d5-b8588e691e0c.png)

Pestle:

![image](https://user-images.githubusercontent.com/109232157/227700184-16c35ac4-e4ad-4ff5-83ac-de1fa8e223ce.png)
![image](https://user-images.githubusercontent.com/109232157/227700203-ffd2ea17-0996-4e59-88b6-2a3bf9ce5cb0.png)







