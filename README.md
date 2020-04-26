#detecting shapes using python and opencv along with numpy..
import cv2 #opencv
import numpy as npy
path= "   " #image path in system
img=cv2.imread(path)
def empty(a):#just take an empty function 
    pass
cv2.namedWindow("trackbar")  #creating a tracbar window with a name "trackbar"
cv2.resizeWindow("trackbar",400,300)
cv2.createTrackbar("hue min","trackbar",0,179,empty)
cv2.createTrackbar("hue max","trackbar",255,255,empty)
cv2.createTrackbar("sat min","trackbar",0,255,empty)
cv2.createTrackbar("sat max","trackbar",255,255,empty)
cv2.createTrackbar("val min","trackbar",0,255,empty)
cv2.createTrackbar("val max","trackbar",255,255,empty)
while True:
     hue_min=cv2.getTrackbarPos("hue min","trackbar")
     hue_max=cv2.getTrackbarPos("hue max","trackbar")
     sat_min=cv2.getTrackbarPos("sat min","trackbar")
     sat_max=cv2.getTrackbarPos("sat max","trackbar")
     val_min=cv2.getTrackbarPos("val min","trackbar")
     val_max=cv2.getTrackbarPos("val max","trackbar")
     lower = np.array([hue_min,sat_min,val_min])  
     upper = np.array([hue_max,sat_max,val_max])
     mask = cv2.inRange(img, lower, upper)
     cv2.imshow("mask",mask)#mask in the quotations is window name in which out output gets displayed we can give any window name for it..
     contours,hie=cv2.findContours(img,cv2.RETR_EXTERNAL,cv2.CHAIN_APPROX_NONE)
     for cnt in contours:
        cv2.drawContours(img,[cnt],-1,(0,255,0),2)
        cv2.imshow("image",img)

cv2.waitKey(0)
