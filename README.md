# Predicting-Video-Memorability-Scores
Predicting Video Memorability Scores Using Machine Learning Models.
This project is an attempt on "Predicting Media Memorability Task at MediaEval 2018" challege. I have used the dataset provideed by the organisers to train and build the model. The code for this challege was written using python.

Repository organization:

  1. Dataset : Contains two files namely :
        dev-set_ground-truth.csv :  This file contains the ground truth of memorability scores given to each video.
        dev-set_video-captions.txt: Contains the captions assigned to each video.
        
  2. Models_Exploration.ipynb
        In this file, various features have been extracted and explored from the videos dataset. I have extensively used Natural Language Processing techniques for retrieving the text features from captions. After evaluting all models, the final model was built.
        
  3. Memorability_Predictor.ipynb
        This is the final predictor, that can predict the short-term and long-term memorability scores of any video with captions. The best result for this predictor for predicting the short-term memorability scores is 𝟬.𝟰𝟬𝟰 (which is promising, as the highest scores achieved in this challange is 0.49)
        
    
