Vertebra Keypoint association and filtering pipeline Dataset
============================================================

[Spine Image](img/spines.png)

This is the accompanying dataset for the paper: 
Robust vertebra identification using simultaneous node and edge predicting Graph Neural Networks
Authors: Vincent Bürgin, Raphael Prevost, Marijn F. Stollenga

Structure
=========
The dataset consist of 4 folders with json files, each with keypoint detections corresponding to a spine CT scan.
- KeypointPredictionsNoSacrum: consists of a Training and Validation folder with keypoint detections from a neural network, trained as described in the paper.
These serve as training data for the Graph Neural Network, adding realistic mistakes (missing and superfluous detections) to train the GNN.
- KeypointGroundTruthNoSacrum: consists of a Training and Validation folder with ground truth keypoint predictions that serve as the testing grounds of the GNN. These were created in a bootstrap and validation process by the authors.
- mapping-export-Training.txt and mapping-export-Validation.txt contains file associations of the dataset identifiers to their original data scans. These come from 3 different datasets as described in the paper:
  - The VerSe dataset: _Sekuboyina, Anjany, et al. "VerSe: a vertebrae labelling and segmentation benchmark for multi-detector CT images." Medical image analysis 73 (2021): 102166._
  - The CT Colonography dataset: _Smith, K., Clark, K., Bennett, W., Nolan, T., Kirby, J., Wolfsberger, M., Moulton, J., Vendt, B., Freymann, J.: Data from ct-colonography. The cancer imaging archive (2015)_
  - The CT Pancreas dataset: _Roth, H.R., Farag, A., Turkbey, E., Lu, L., Liu, J., Summers, R.M.: Data from pancreas-ct. the cancer imaging archive. IEEE Transactions on Image Processing (2016)_

Keypoint Prediction files
=========================
The Keypoint Prediction files are structured as json as follows:
- A list of keypoints is stored, with each having a:
  - 'coordinates' entry, with a 'world_space' entry of the keypoint position in DICOM world coordinates.
  - 'type' entry, with: 
    - 'spine_segment' entry denoting the prediced spine segment (C = cervical, T = thoracic, L = Lumbar), only present for body detections
    - the 'spine_segment_propabilities' the unnormalized segment probabilities (C,T,L), only present for body detections,
    - the 'keypoint_type' denoting the keypoint type (body = vertebra body, left = left pedicle, right = right pedicle,

Keypoint Groundtruth files
==========================
The Keypoint Groundtruth files are structures as json as follows:
- A list of keypoints is stored, with each having a:
  - 'coordinates' entry, with a 'world_space' entry of the keypoint position in DICOM world coordinates.
  - 'type' entry, with:
    - 'spine_level' denoting the spine level (C2 = second Cervical, T3 = third thoracic, L4 = fourth Lumbar etc.)
    - the 'keypoint_type' denoting the keypoint type (body = vertebra body, left = left pedicle, right = right pedicle.
