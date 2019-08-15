%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%
%%%%%	CA684 - MEDIAEVAL 2018 PREDICTING MEDIA MEMORABILITY TASK: DEVELOPMENT SET
%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%

-----------------------------------------------------------------------------------------------------------------------------------
# BRIEF DESCRIPTION
-----------------------------------------------------------------------------------------------------------------------------------

The current package corresponds to the development set released in the context of the MediaEval 2018 Predicting Media Memorability
 Task.

It contains the development set's video sources and ground truth.

It is accompanied with pre-extracted visual features to help participants to the task develop their systems, together with additional
and optional data.

The license attached to the dataset is described in file MemorabilityDataset2018_license.txt.

Please note that the files provided contains all the needed information to understand and use the development set.

-----------------------------------------------------------------------------------------------------------------------------------
# GROUND TRUTH
-----------------------------------------------------------------------------------------------------------------------------------

Ground truth is provided in file dev-set_ground-truth.csv.

For each video of the development set, it consists of:
	•	the video's name given as videoX.webm 
	•	its short-term memorability score.
	•	the number of annotations which was used to calculate its short-term memorability score.
	•	its long-term memorability score.
	•	the number of annotations which was used to calculate its long-term memorability score.

-----------------------------------------------------------------------------------------------------------------------------------
# SOURCES (folder "sources")
-----------------------------------------------------------------------------------------------------------------------------------
The development set contains 6,000 short videos.

The videos are proposed in .webm format (3000k). Please note that this format was also used during the collection of the annotations.

-----------------------------------------------------------------------------------------------------------------------------------
# FEATURES (folder "features")
-----------------------------------------------------------------------------------------------------------------------------------
A set of pre-extracted visual features are provided to the participants to the task.

* Video features:
  - C3D features [1]
  - HMP (Histogram of Motion Patterns) [2]

* Image features:
  - HoG (Histogram of Oriented Gradients) [3]
  - LBP (Local Binary Pattern) [4]
  - Fc7layer from InceptionV3 [5]
  - ORB (Oriented FAST and Rotated BRIEF) [6] (An efficient alternative to SIFT or SURF)
  - Color Histogram

We would like to thank Ricardo Manhaes Savii (https://github.com/ricoms) and Mihai Gabriel Constantin
 (https://scholar.google.com/citations?user=A1oerNkAAAAJ&hl=en) for extracting the features.

The feature files' formats are described at the end of this README.

-----------------------------------------------------------------------------------------------------------------------------------
# ADDITIONAL DATA (folder additional-data)
-----------------------------------------------------------------------------------------------------------------------------------

LaMem dataset from MIT [7] is also provided as optional external data to the task. LaMem contains approx. 60,000 images together
 with their memorability scores. We additionally provide the Image features cited in the previous section for the LaMem images.


Please note that the Movie Memorability Dataset from Technicolor, presented in [8] and not included in this package, may also considered
as external data. It is downlodable at the following address:
 https://www.technicolor.com/dream/research-innovation/movie-memorability-dataset

Participants are free to use additional data or not. 

-----------------------------------------------------------------------------------------------------------------------------------
# FEATURES FORMAT
-----------------------------------------------------------------------------------------------------------------------------------
Precomputed features are organized in different folders, one per feature. Most of the time the chosen file format was plain text.
We specify the internal feature format for each feature file below.

#Video specialized features

For the following two features, participants will find one file per video.

    C3D features [1]
        outputs: the final classification layer of the C3D model
        file format: text file
        feature: a single list of numbers on one line (dimension = 101)

    HMP [2]
        outputs: the histogram of motion patterns for each video
        file format: text file
        feature: a single list of pairs of numbers with format: bin:number (dimension = 6075) on one line


#Image features on video

The following features were extracted on three key-frames (first (0), middle (56) and last (112)) on each video. So there are three 
files for each video, with names videoNb-0.txt, videoNb-56.txt, videoNb-112.txt.

    HoG [3]
        outputs: histograms of oriented gradients. Gradients are calculated on 32x32 windows on a grey scale image.
        file format: text file
        feature: a single list of numbers on one line (dimension = depends on the image size)

    LBP [4]
        outputs: Local Binary Patterns. These features represent some local texture information. LBP values are calculated for patches 
	of 8x15 pixels.
        file format: text file
        feature: a single list of numbers on one line (dimension = depends on the image size)

    InceptionV3 [5]
        outputs: output of the fc7layer of the InceptionV3 deep network.
        file format: text file
        feature: a single list of pairs of numbers with format imagenet_class:activation (max dimension = 1,000)

    ORB [6] (An efficient alternative to SIFT or SURF)
        outputs: Oriented FAST and Rotated BRIEF. ORB is basically a fusion of FAST keypoint detector and BRIEF descriptor with many 
	modifications to enhance the performance.
        file format: pickle (extension of file ".p").
        feature: a list of keypoints and descriptors (see [9] and the official wiki of the task for a detailed explanation. Keypoints
	and their descriptors were stored using function pickle_keypoints [10])

    Color Histogram
        outputs: classic color histogram (three channels)
        file format: text file
        feature: 3 lists (Red, Green, Blue in that order) of 255 pairs with format bin:number, e.g., 254:1008. One list per line.


We would like to thank Ricardo Manhaes Savii (Universidade Federal de São Paulo) for extracting the features. His code to extract
 the features is available here: https://github.com/ricoms/video_image_features

-----------------------------------------------------------------------------------------------------------------------------------
# REFERENCES
-----------------------------------------------------------------------------------------------------------------------------------
[1] D. Tran, L. Bourdev, R. Fergus, L. Torresani, and M. Paluri, **Learning Spatiotemporal Features with 3D Convolutional Networks**, ICCV 2015, PDF.
[2] ALMEIDA, Jurandy; LEITE, Neucimar J.; TORRES, Ricardo da S. Comparison of video sequences with histograms of motion patterns. In: **Image Processing (ICIP), 2011 18th IEEE International Conference on**. IEEE, 2011. p. 3673-3676.
[3] Dalal, N. and B. Triggs. **Histograms of Oriented Gradients for Human Detection**, IEEE Computer Society Conference on Computer Vision and Pattern Recognition, Vol. 1 (June 2005), pp. 886–893.
[4] DC. He and L. Wang (1990), **Texture Unit, Texture Spectrum, And Texture Analysis**, Geoscience and Remote Sensing, IEEE Transactions on, vol. 28, pp. 509 - 512.
[5] SZEGEDY, Christian et al. **Rethinking the inception architecture for computer vision**. In: Proceedings of the IEEE Conference on Computer Vision and Pattern Recognition. 2016. p. 2818-2826.
[6] Ethan Rublee, Vincent Rabaud, Kurt Konolige, and Gary Bradski. **Orb: an efficient alternative to sift or surf**. In Computer Vision (ICCV), 2011 IEEE International Conference on, pages 2564–2571. IEEE, 2011.
[7] Khosla, A., Raju, A. S., Torralba, A., & Oliva, A. (2015, December). Understanding and predicting image memorability at a large scale. In Computer Vision (ICCV), 2015 IEEE International Conference on (pp. 2390-2398). IEEE.
[8] R.Cohendet, K. Yadati, N. Q. Duong and C.-H. Demarty. Annotating, understanding, and predicting long-term video memorability. In Proceedings of the ICMR 2018 Conference, Yokohama, Japan, June 11-14, 2018.
[9] http://opencv-python-tutroals.readthedocs.io/en/latest/py_tutorials/py_feature2d/py_orb/py_orb.html
[10] https://github.com/ricoms/video_image_features/blob/master/utils.py
