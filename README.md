Project details:
Driver Drowsiness Detection System with OpenCV &amp; Machine Learning
This driver drowsiness detection project is created to prevent accidents. Drowsiness means
sleepiness, so it prevents accidents that are caused by drivers who are feeling drowsy or we can
say who fell asleep while driving. So we are creating a Drowsiness detection system that will
detect that the person’s eyes are closed or open. And if a person’s eyes are closed for a few
seconds, the system will alert the person by ringing an alert sound.
Our approach to Create Drowsiness detection system:
In this project, for collecting images from webcam we will be using OpenCV and feed these
images to our Deep learning model which will classify that the person’s eyes is ‘Open’ or ‘Closed’.
So we will follow these steps:

 We will take image input from the camera
 Detect face and eyes in the image.
 Create a Region of Interest(ROI), for both detected face and eyes.
 Feed this to our classifier(model), which will categorize whether eyes are open or closed.
 At last, we will calculate the time to check if the person is drowsy or not.

Driver Drowsiness Detection 

haar cascade files: This folder has files that are used to detect the face and eyes of a person,
these files are xml files. The haar cascade files have many xml files that are required to detect
objects in an image. You can download this also just by searching on Google.
Beep-07.wav: This file is used to play the alert sound when a person closes its eyes for a few
seconds.
drowsiness_system.py: This file consists of full implementation of our project in which we have
loaded the model and used it to alert the person whenever he/she will feel drowsy. So this is the
main file, you have to run this file for detection procedure.
Let’s go step by step:
1. Importing all the needed libraries:
2. Setting an alarm sound file, and we will set a path of haar cascade files to detect face, detect left
eye, and detect right eye.
3. After this we will load our model, and using OpenCV we will access a webcam that will capture
each frame.
4. This is the main logic of code. In this code we are checking that, if the person’s left eye and
right eye are closed, time will increase and if time increases more than 10 the alert sound will
start, and if both eyes are open the time decreases and sound stops after some time.

if(right_eye_pred[0] == 0 and left_eye_pred == 0):
time += 1
cv2. putText(frame,&quot;Inactive&quot;,(10,height-20), font, 1,(255,255,255),1,cv2.LINE_AA)
# if(right_eye_pred[0]==1 or left_eye_pred[0]==1):
else:
time -= 1
cv2.putText(frame,&quot;Active&quot;,(10,height-20), font, 1,(255,255,255),1,cv2.LINE_AA)
if(time&lt;0):
time=0
cv2.putText(frame,&#39;Wake up Time !!:&#39;+str(time),(300,height-20), font, 1,(0,0,255),1,cv2.LINE_AA)
if (time&gt;10):
#person is feeling dazzi we will alert :
cv2.imwrite(os.path.join(path,&#39;image.jpg&#39;),frame)
try:
alarm_sound.play()
except:
pass
if(thick &lt; 16):
thick = thick+2
else:
thick=thick-2
if(thick&lt;2):
thick=2
cv2.rectangle(frame,(0,0),(width,height),(0,0,255),thick)
cv2.imshow(&#39;frame&#39;,frame)
if cv2.waitKey(1) &amp; 0xFF == ord(&#39;q&#39;):
break
capture.release()
cv2.destroyAllWindows()
So this is the full explanation of the “drowsiness_system.py” file.
Summary
In this project, we learn OpenCV and use a haar cascade classifier to detect faces and eyes of a
person. With the help of this, we are successfully able to create a drowsy driver alert system.
