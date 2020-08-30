# VRU21k Dataset and Augmentation
Contains the jupyter notebook for augmentating VRU datas and selecting combining training data from nuScenes and BDD100k

## Data Augmentation
The algorithm:
1. Randomly selects a scene (background image with no existing VRUs)
2. Performs random augmentations on scene:
  * horizontal flip
  * contrast enhancement
3. Randomly selects 5 objects (.png file with background removed preferrably)
4. Performs random augmentation on objects individually:
  * scaling
  * aspect ratio (reduce max(w,h) by 10%)
  * colour switch
  * add noise (speckles)
  * horizontal flip
  * contrast enhancement
5. Place the 5 objects into a column at a random vertical position (a scene is divided into 5 colours)
6. Image frame is saved, and labels automatically generated
  
## VRU21k Dataset
Consists of iamges from nuScenes (after 3d -> 2D conversion), BDD100k and NUS-ST

* Frame selection criteria (BDD100k and nuScenes)
  1. if there's 4 or more objects in the scene
  2. if there's 2 or more objects in the scene AND at least 1 bicycle or motorbike
* Shortlisted frames
  * 11291 frames from nuScenes
  * 11477 frames from BDD100k
  * 4000 frames from augmented VRU data
* Total split into 21000 train, 5768 val
