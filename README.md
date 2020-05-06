# real-time-face-recognition-system

RGB camera was used to recognize face in this section. This recognition was developed using IMAQ Vision Development Toolkit. The system uses colour and pattern matching method to perform face recognition on a Kinect camera stream. Given right templates and adequate settings it does perform with respect to its simplicity. The whole approach can be split into two main parts; First, Face Detection. It was accomplished by matching Eye, Nose and Lips templates against the camera stream image. 

<img width="321" alt="1" src="https://user-images.githubusercontent.com/41656537/81127795-fbfd9d80-8f71-11ea-82b0-e095bdf5bf16.PNG">

Once these three are found, simple logical calculations are performed (e.g. is eye level higher than nose level) to determine whether it's really something resembling a face. After that a Boolean is used to flag this case. Secondly point following. Once a face is found, the X and Y of the last Lips match found (chosen arbitrarily) was extracted. This point (X, Y) is then tracked on the screen until another face is found.

<img width="332" alt="2" src="https://user-images.githubusercontent.com/41656537/81127811-0455d880-8f72-11ea-9281-87bd96be8fe3.PNG">

First, colour configured, and pattern recognition data initiated. This was adjusted to fit Kinect camera, templates and better lighting. Secondly, loaded template images. Then three IMAQ images created for the current and previous images (to do image tracking) and for preview image (The one shown in the Front Panel). After that, this array stored feature points in format of array of clusters, where each element of the array is a cluster of two items: point X and point Y which followed using IMAQ Optical Flow. Next, two images in parallel from the camera (doing this in series introduced a noticeable FPS drop) was acquired.
The Red (Default) colour plane extracted. Under different conditions other planes might be more suitable. Overlay data from previous frame cleared. First frame will not have any, so nothing will be cleared in the first run. Match Colour Pattern computed for a given template depending on the Setup Data configured initially. After that, a rectangle drawn around each face feature found in a different colour. Face is found depending on template matches found. Finally, Kinect camera session closed as the face recognized.

<img width="332" alt="3" src="https://user-images.githubusercontent.com/41656537/81127816-04ee6f00-8f72-11ea-878b-1ac47e140ee8.PNG">
