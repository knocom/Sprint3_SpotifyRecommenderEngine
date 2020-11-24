# Sprint3_SpotifyRecommenderEngine
A few of the notebooks we used to come up with a Spotify Song Recommender Engine for a fictional Philippine band, Bean & Bean, who wishes to get a big break in the music industry!

Essentially, our team (myself, Jelly, Franz, William) utilized Spotify's API and extracted the Top 200 songs in Spotify from September 2019 - September 2020 along with their [audio features](https://developer.spotify.com/documentation/web-api/reference/tracks/get-audio-features/). We also classified popular Spotify tracks into different genres such as Folk, Rock, Country, Hiphop/Rap, Jazz, Electronic, etc. The audio features of each genre would be used in a training set to build a classification algorithm to predict the genres of songs that did not pass through the training model via K-Nearest Neighbors (kNN).

## 1_Sprint3_presentation_Mainstay&Viral_Nox

This notebook shows how we were able to classify a song as a 'Mainstay' or a 'Viral' song. Mainstay songs are those that never left the Top 200 chart for a whole year. Viral songs are songs which appeared in the Top 100 at least once and registered a rapid increase in chart position growth at least once in the past year. (The exact parameter we used to measure this was 7 Day Rolling Standard Deviation in Chart Position. If the song was in the 4th Quartile (Top 25%), then it would be eligible to be called a viral song.) 

Out of 1032 unique tracks in the Spotify Top 200 Charts, we were able to identify 38 Mainstay and 120 Viral songs.

## 2_Create_Recommender_Engine_Pool_noxv2bsampledsets

We were able to get sample track data for each genre by searching each genre as a keyword in Spotify Search and selecting the top playlists with the keyword in its name. A portion of the songs here were then used as a training pool for the kNN Algorithm. Normalization/Scaling of data was also done due to some audio features like loudness and tempo being much larger than the rest (which were usually within the 0 to 1 range). We next built the kNN Algorith using the different audio features as the feature columns with genre as the target. We were able to get 59% Accuracy after cross-validation and tweaking the number of genres to be used. It is worth noting that getting a very high accuracy score for a genre classification model such as this is extremely difficult given the fact that most songs do not have an official genre classification and would often have features which overlap between two or more genres. After the model was created, we used it to classify the predicted genres of all the other songs which were in our dataset.


For our group's presentation on the Spotify Recommender Engine project, please refer to this [link](https://docs.google.com/presentation/d/1IhwqKKCQs-BBfx8iKkVikn6-JZHX8VzT5PewdHS091o/).

Special thanks to [Eskwelabs](https://www.eskwelabs.com/)  and our instructor JC Peralta!
