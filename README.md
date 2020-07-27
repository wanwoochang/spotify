# spotify
Yet another data engineering and machine learning exercise using Python and Spotify's Web API.

This project was inspired by other Spotify machine learning projects such as <a href="https://medium.com/analytics-vidhya/clustering-most-listened-songs-of-the-2010s-using-spotify-data-8e25e8b082ce">Clustering the Most Listened to Songs of the 2010s Using Spotify Data</a> and <a href="https://towardsdatascience.com/profiling-my-favorite-songs-on-spotify-through-clustering-33fee591783d">Profiling my Favourite Songs on Spotify through Clustering</a>. While these projects focused on tracks from curated track playlists, this project focused on recommended tracks through Spotify's Web API as detailed on <a href="https://developer.spotify.com/documentation/web-api/reference/browse/get-recommendations/">this page</a>. I wanted to get an understanding of Spotify's genres at the track level instead of the readily available genre data for artists and albums, which was at times sparse and inconsistent. As a result, I opted to collect a sample of approximately 500 unique tracks per seed genre. I did, however, limit the 'liveness' feature of recordings to be at 0.85, which allowed for the collection of a wide range of tracks while excluding tracks which Spotify deems as live recordings. With every seed genre sampling, I created a folder and stored each track ID as a small .JSON file to keep a track of which track is associated to which genre(s) as one track can be associated to multiple genres. While this is a good approach to associate tracks to genres during the collection process, there is a theoretical downside to this process. Track collection was done in alphabetical order according to genre. Tracks from genres such as 'acoustic', 'ambient', or 'chill' may potentially be associated to more genres than tracks collected from 'rock', 'sertanejo', or 'world-music'. This could be rectified by simply collecting recommendations in reverse order to ensure that all tracks receive equal opportunity to be associated to their seed genres.

# Seed genres
Available through the <a href="https://developer.spotify.com/console/get-available-genre-seeds/">'available-seed-genres'</a> endpoint in Spotify's Web API, this is a list of genres available to be used to get recommendations for tracks. At the time of conducting this project, there were 126 genres available.

# Cluster analysis
Without any real predetermined labels/outcomes for the data, an unsupervised machine learning algorithm such as clustering seemed to be the best approach. By the time data had been collected, I had just over 48,000 tracks with <a href="https://developer.spotify.com/documentation/web-api/reference/tracks/get-audio-features/">features</a>. K-means is a highly popular algorithm and was applied as shown in the 'cluster.ipynb' notebook. Other algorithms such as t-SNE or DBSCAN are options I'd like to explore in the future.

# Results of cluster analysis
Cluster 0: Loud tracks with high energy and fast tempo. Punk rock, emo, punk, J-rock, and anime tracks comprise the majority of this category. Artists include Nirvana, Pearl Jam, Green Day, and blink-182.

Cluster 1: On average the quietest and slowest of the clusters, these tracks are heavy on acoustics and instrumentals with a somber tone. Tracks of this cluster fall under soundtracks, piano, classical, movies, and ambient genres, composed by trained artists such as Yiruma, Ludovico Einaudi, and Hans Zimmer.

Cluster 2: For techno and house enthusiasts, this cluster is dominated by songs falling under minimal and detroit techno, progressive and deep house, trance, and the like. Frequent artists include Aphex Twin, Napalm Death, and Armin van Buuren.

Cluster 3: A unique cluster in that there isn't a cohesive theme among the most frequent genres (gospel, dubstep, house, techno), but rather tracks which sound like live performances. Reel Big Fish, Nirvana, Nine Inch Nails, and blink-182 have tracks frequently appearing in this group.

Cluster 4: The cluster featuring disco, spanish, salsa, and happy genres. This is the group of songs to listen to if you want to dance to a beat or if you want a good work out. Top recurring artists include Daddy Yankee, Reel Big Fish, Wisin & Yandel, and Shakira.

Cluster 5: Songs with a Jamaican flair fall under this group, such as dancehall, hip hop, and reggae; this group has tracks with high energy and danceability with an upbeat tempo and sound. Artists include Vybz Kartel, Drake, Popcaan, 2 Chainz, and Lil Wayne.

Cluster 6: Similar to cluster 0, this cluster has songs to for headbanging, but with a heavier melody. Top occurring genres are heavy metal, dubstep, and metalcore, with top occurring bands being Alice in Chains, Pearl Jam, and Death.

Cluster 7: Similar to cluster 1 but with a slightly more upbeat tune and tempo and singing. Some genres to describe this group include singer songwriter, folk, acoustic, and rainy day. Artists include Googoosh, Luciano Pavarotti, and Carlos Gardel.

# Tools used
<ul>
  <li>Python</li>
    <ul>
      <li>JupyterLab</li>
      <li>Requests</li>
      <li>Pandas</li>
      <li>Matplotlib</li>
      <li>Seaborn</li>
      <li>Scikit-Learn</li>
    </ul>
  <li>PostgreSQL</li>
  <li>Tableau (<a href="https://public.tableau.com/profile/wan.woo.chang#!/vizhome/SpotifyTrackFeaturesAnalysis/SpotifyTrackFeaturesAnalysis">dashboard</a>)</li>
</li>
