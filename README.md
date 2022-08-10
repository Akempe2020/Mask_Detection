# Mask_Detection
This project takes an image of someone who is or isn't wearing a mask and detects whether they are or aren't. 
For those who aren't wearing a mask, it will tell them to put it on, and it will say good job to those who are.

It works by using a model trained with a dataset consisting of people with and without masks. Then, the code will detect whether the person is wearing their mask or not. 
If they are, it will print out good job, if not, it'll tell them to put it on.

## Steps to run the project:
1. Push this github to your jetson nano.
2. Either use the test file or download your own image of someone wearing or not wearing a mask into the test folder, which is in data/mask/test/. 
There will be two folders, WithMask and WithoutMask. Upload the image accordingly.
3. In the mask_detection_project directory, paste these two commands:
 NET=models/mask and
 DATASET=data/mask 
This will set the values to these directories and will allow the final command to work.
4. Once that's done, to run the program, paste this:
python3 mask_detection.py --model=$NET/resnet18.onnx --input_blob=input_0 --output_blob=output_0 --labels=$DATASET/labels.txt $DATASET/test/WithMask/blank.png output.png
 Some changes may need to be made to classify difference images. If your image is in the WithoutMask folder, change the value WithMask to WithoutMask.
Change the blank.png to any png in the test folders. And if you classify multiple images, you need to change output to a different number, like output_1.png.
If you download your own image, it may be a different kind, like a jpg. If this is the case, you would need to change blank.png to whatever the filename is.
It would be blank.jpg. You would also need to change output.png to output.jpg.
5. Wait for it to run, then near the bottom you should see the percentage for WithMask and WithoutMask. Underneath, you will see the statement congratulating someone
on wearing their mask or telling them to put it on. Some images may work better than others.
6. If you want to see the image with the percentage on the image, scp it onto your desktop or into your downloads.
