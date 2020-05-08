# Machine learning models based on sleep_classifiers
Building improved ML classifiers for sleep data from Olivia Walch's (@ojwalch) <a href="https://github.com/ojwalch/sleep_classifiers">sleep_classifiers</a>. 

If you're looking for Jupyter Notebooks containing the ML models, check out the <code>notebooks</code> folder; more detailed descriptions can be found in that folder's <code>README</code>. If you're interested in ETL/feature extraction and engineering, look at <code>source/etl.py</code>. These generally assume you have already extracted the data from Dr. Walch's study into the <code>data</code> folder of the project root directory (directory where this <code>README</code> lives). 

In this project, I analyze accelerometer timeseries from the aforementioned <code>sleep_classifiers</code> with the goal of predicting sleep stages (awake/NREM/REM) based on Apple Watch accelerometer data. The current focus is accurate prediction of Awake/Asleep. For supervised ML, I build two TensorFlow neural networks, one feedforward and one convolutional, and two logistic regression models. The first NN has only densely connected layers, the second has two convolutional layers, separated by a max pool layer, that feed into two densely connected layers. Additionally, I also explore _k_-means and OPTICS for unsupervised clustering.  

Our most successful improvements to Dr. Walch's earlier work have come from using a CNN on the <a href="https://musiclab.chromeexperiments.com/Spectrogram/">spectrogram</a> of acceleration derivatives. When plotted with time on the horizontal axis and frequency on the vertical axis, we can visualize these STFTs as spectrograms. These spectrograms are input as black-and-white images to the neural networks. To give some idea for the information contained in these, here is a spectrogram (top) generated using the Librosa library along with the derivative of acceleration (in blue)and PSG labels (in maize) on the bottom. The highest PSG label of 5 corresonds to REM sleep; awake is class 0; NREM stages are classes 1, 2, 3, 4. 
<img src="images/8173033_spectrogram_PSG.png">  