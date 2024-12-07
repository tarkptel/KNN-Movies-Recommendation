</head>
<body>

<h1>Movie Recommendation System Using KNN</h1>

<h2>Overview</h2>
<p>This project is a <strong>movie recommendation system</strong> designed using the <strong>K-Nearest Neighbors (KNN)</strong> algorithm. The goal is to recommend movies similar to a given movie based on their genres and average ratings, using the popular MovieLens dataset.</p>

<h2>Features</h2>
<ul>
    <li><strong>Dataset Merging:</strong> Combines movie metadata and user ratings for unified processing.</li>
    <li><strong>Genre Encoding:</strong> Encodes multi-genre data for better analysis.</li>
    <li><strong>Aggregated Ratings:</strong> Uses average movie ratings as a key feature.</li>
    <li><strong>KNN Implementation:</strong> Leverages cosine similarity to recommend similar movies.</li>
</ul>

<h2>Project Workflow</h2>

<h3>1. Data Loading</h3>
<p>The project utilizes two datasets:</p>
<ul>
    <li><strong>Movies Metadata:</strong> Contains details like <em>movieId</em>, <em>title</em>, and <em>genres</em>.</li>
    <li><strong>User Ratings:</strong> Includes user preferences in the form of <em>ratings</em>.</li>
</ul>

<h3>2. Data Merging</h3>
<p>The datasets are merged on the <strong>movieId</strong> column to align movie details with their respective ratings.</p>

<h3>3. Feature Engineering</h3>
<p>Multi-genre information is encoded using <strong>MultiLabelBinarizer</strong>, creating binary features for each genre. This allows the model to compare movies based on their genres effectively.</p>

<h3>4. Aggregation</h3>
<p>For each movie, the following features are calculated:</p>
<ul>
    <li><strong>Average Rating:</strong> Summarizes user feedback.</li>
    <li><strong>Genre Binary Features:</strong> Indicates the presence of specific genres.</li>
</ul>

<h3>5. Recommendation Model</h3>
<p>The KNN algorithm is employed to find movies similar to a selected one. Cosine similarity is used as the metric to measure similarity between movies based on their features.</p>

<h2>Technologies Used</h2>
<ul>
    <li><strong>Python</strong></li>
    <li><strong>Pandas:</strong> Data processing and aggregation.</li>
    <li><strong>Scikit-learn:</strong> Encoding genres and implementing the KNN model.</li>
</ul>

<h2>Why KNN?</h2>
<p>KNN is a simple yet effective algorithm for finding similar items in a dataset. It works well for this project because:</p>
<ul>
    <li>It is intuitive and interpretable.</li>
    <li>It does not assume a specific distribution of the data.</li>
    <li>Cosine similarity helps in comparing multi-dimensional data effectively.</li>
</ul>

<h2>How to Use the System</h2>
<ol>
    <li>Download and prepare the datasets (<em>movies.csv</em> and <em>ratings.csv</em>).</li>
    <li>Install required libraries:
        <ul>
            <li><strong>Pandas:</strong> For data handling.</li>
            <li><strong>Scikit-learn:</strong> For the KNN implementation.</li>
        </ul>
    </li>
    <li>Run the project script to generate recommendations.</li>
</ol>

<h2>Future Enhancements</h2>
<p>Potential improvements to the system include:</p>
<ul>
    <li><strong>User-based Filtering:</strong> Recommend movies based on individual user preferences.</li>
    <li><strong>Dimensionality Reduction:</strong> Use techniques like PCA to handle high-dimensional genre data efficiently.</li>
    <li><strong>Interactive Interface:</strong> Develop a user-friendly web or desktop application for the recommendation system.</li>
</ul>

</body>
</html>
