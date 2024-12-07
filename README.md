</head>
<body>

<h1>Movie Recommendation System Using KNN</h1>

<h2>Overview</h2>
<p>This project implements a <strong>movie recommendation system</strong> using the <strong>K-Nearest Neighbors (KNN)</strong> algorithm. It is built on the <strong>MovieLens dataset</strong> and focuses on recommending movies similar to a given movie based on their genres and average ratings.</p>

<h2>Key Features</h2>
<ul>
    <li><strong>Dataset Integration:</strong> Merges metadata and ratings for unified analysis.</li>
    <li><strong>Feature Engineering:</strong> Encodes genres and aggregates ratings.</li>
    <li><strong>Recommendation Algorithm:</strong> Implements KNN to suggest similar movies.</li>
</ul>

<h2>Steps in the Project</h2>
<h3>1. Data Loading</h3>
<p>The project uses the following datasets:</p>
<ul>
    <li><code>movies.csv</code>: Metadata about movies, such as <code>movieId</code>, <code>title</code>, and <code>genres</code>.</li>
    <li><code>ratings.csv</code>: User ratings, including <code>userId</code>, <code>movieId</code>, <code>rating</code>, and <code>timestamp</code>.</li>
</ul>
<pre>
movies = pd.read_csv("movies.csv")
ratings = pd.read_csv("ratings.csv")
</pre>

<h3>2. Data Merging</h3>
<p>Merges <code>movies.csv</code> and <code>ratings.csv</code> using the <code>movieId</code> column:</p>
<pre>
data = pd.merge(ratings, movies, on='movieId')
</pre>

<h3>3. Feature Engineering</h3>
<p>Encodes the <code>genres</code> column using <code>MultiLabelBinarizer</code>:</p>
<pre>
mlb = MultiLabelBinarizer()
genres_encoded = mlb.fit_transform(data['genres'])
</pre>
<p>Appends the encoded genres back to the dataset.</p>

<h3>4. Data Aggregation</h3>
<p>Groups data by <code>movieId</code> and calculates:</p>
<ul>
    <li>Average ratings for each movie.</li>
    <li>Presence of each genre as binary features.</li>
</ul>
<pre>
movie_features = data.groupby('movieId').agg({
    'rating': 'mean',
    **{genre: 'max' for genre in mlb.classes_}
}).reset_index()
</pre>

<h3>5. KNN Model</h3>
<p>Uses KNN to find similar movies based on cosine similarity:</p>
<pre>
knn = NearestNeighbors(n_neighbors=5, metric='cosine')
knn.fit(X)
</pre>

<h3>6. Recommendations</h3>
<p>Generates recommendations for a given movie:</p>
<pre>
distances, indices = knn.kneighbors([X.iloc[movie_index]])
for i in indices[0]:
    print(movies[movies['movieId'] == movie_ids.iloc[i]]['title'].values[0])
</pre>

<h2>Technologies Used</h2>
<ul>
    <li><strong>Python</strong></li>
    <li><strong>Pandas:</strong> Data manipulation and aggregation.</li>
    <li><strong>Scikit-learn:</strong> KNN model and MultiLabelBinarizer.</li>
</ul>

<h2>Why These Techniques Were Used?</h2>
<ul>
    <li><strong>MultiLabelBinarizer:</strong> Handles multi-valued genres effectively.</li>
    <li><strong>Aggregating Ratings:</strong> Summarizes user preferences efficiently.</li>
    <li><strong>KNN:</strong> Identifies similar movies with cosine similarity.</li>
</ul>

<h2>How to Use</h2>
<ol>
    <li>Clone the repository:
        <pre>git clone https://github.com/yourusername/movie-recommendation-knn.git</pre>
    </li>
    <li>Install the required libraries:
        <pre>pip install pandas scikit-learn</pre>
    </li>
    <li>Run the script:
        <pre>python movie_recommendation.py</pre>
    </li>
</ol>

<h2>Possible Improvements</h2>
<ul>
    <li>Integrate user-based filtering for personalized recommendations.</li>
    <li>Use dimensionality reduction (e.g., PCA) to optimize for large datasets.</li>
    <li>Develop a user interface for better interaction.</li>
</ul>

</body>
</html>
