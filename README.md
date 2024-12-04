# Conversation-Data-Processor

The goal of this code is to extract acoustic features from conversational data. While the original project focuses on understanding the interaction between children conversing with three partners, the code has broader applications. It can be used in analyzing human-to-human interactions, human-to-AI interactions, or group conversations, and it can further be applied to studies in linguistics, sociolinguistics, speech therapy, communication training, and more. These use cases make the code highly versatile and relevant to both academic and practical, everyday scenarios.

## How to Use This Code
The input required is preprocessed audio files segmented by conversational partner and turn. For instance, if participants A and B are conversing, the code expects a folder of audio files named and segmented as follows: “A_1,” “B_1,” “A_2,” and so forth.

To make this code work for your conversation specifically, you’ll need to make some revisions to the conversation partner lists to specify your partners, as well as adjust the if conditions in the code, which are clearly commented alongside the relevant lines of code.

The code prints progress at each stage, allowing for quick troubleshooting by pinpointing specific functions or files where the process might stop.

## Processing Steps
Step 1: Segment extraction:
The code processes the input audio files, extracts each segment, and saves them as individual files in a folder.

Step 2: Feature analysis:
The code analyzes acoustic features, including pitch, intensity, speech rate, and articulation rate, using two methods:
* Using the librosa library: Detects syllable nuclei based on intensity peaks to identify syllable boundaries, and then calculates syllable count for each segment and divides it by the duration of the segment (or the voiced duration). Liborosa is primarily designed for music and audio analysis, and it has limited accuracy for speech styles, such as pitch shifts in child speech, rapid speech where syllables overlap, noise interference, so be cautious to use it when you have these interferences.
* Using the parselmouth and scipy libraries: Follows a similar process but detects intensity peaks using parselmouth’s tools. Parselmouth is often used for phonetic analyses and is always paired with Praat’s comprehensive suite of speech processing algorithms. may provide greater precision in certain speech contexts, especially those involving tonal languages or nuanced pitch variations.

Step 3: Data compilation:
The code organizes the extracted features for each segment into a csv file. This file has metrics like pitch, intensity, speech rate, and articulation rate for every turn, named in snake case connecting conversation condition, conversation ID, partner identity, and turn number. This structure provides ample information for downstream analysis.

Step 4: Post-Processing 
The code sorts, filters, and calculates data in the csv file using pandas. For instance, you can select specific types of information for targeted analysis, combine data fields to compute aggregate metrics, and draw statistical insights based on feature comparisons.

The code also includes an example of data visualization, but the rich csv data allows for endless possibilities. You can explore:
* Correlations between features like pitch and emotional intensity
* Cluster analyses or heatmaps
* Cross-variable explorations commonly used in scientific research, such as principal component analysis (PCA) or scatterplots for feature comparisons

If you have any questions or suggestions for improvement, feel free to email me! I’m open to feedback to make this code more robust and versatile.
