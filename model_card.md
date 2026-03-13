# 🎧 Model Card: Music Recommender Simulation

## 1. Model Name  

VibeFinder 1.0

---

## 2. Intended Use  

This recommender suggests songs from a small catalog based on a user's preferred genre, mood, and energy level.

The system assumes that a user's musical taste can be approximated by a few simple features such as genre, emotional mood, and intensity (energy).

This project is designed for classroom exploration and learning about recommendation systems. It is not intended for real users or production environments.

---

## 3. How the Model Works  

The recommender evaluates each song in the dataset and calculates a score based on how well the song matches the user’s preferences.

Each song has several attributes such as genre, mood, energy, tempo, and other musical features. The user profile specifies target preferences such as favorite genre, preferred mood, and desired energy level.

The scoring system awards points when a song matches the user's preferred genre or mood. It also calculates a similarity score based on how close the song’s energy level is to the user’s target energy. Songs that match more of these preferences receive higher scores.

After scoring every song, the system sorts the results from highest to lowest score and returns the top recommendations along with explanations describing why each song was selected.

---

## 4. Data  

The dataset used in this project contains 18 songs stored in a CSV file. Each song includes attributes such as title, artist, genre, mood, energy level, tempo, valence, danceability, and acousticness.

The songs represent a small range of genres including pop, lofi, rock, electronic, jazz, ambient, and hip hop. Additional songs were added during development to create a slightly more diverse catalog.

Because the dataset is small and synthetic, it does not capture the full diversity of real music tastes. Many genres and musical styles are missing, and the distribution of songs may not represent real listening behavior.

---

## 5. Strengths  

The recommender works well for clear and consistent user profiles. For example, the Chill Lofi profile produced recommendations that strongly matched the expected vibe, with low-energy lofi tracks appearing at the top.

The scoring logic is also transparent. Because the system explains each recommendation with reasons such as “genre match” or “energy similarity,” it is easy to understand why a song was ranked highly.

The system also demonstrates how a simple rule-based scoring approach can produce intuitive recommendations even without complex machine learning. 

A simple diversity penalty was added to reduce repeated artists or genres in the top recommendations. This helps prevent repetitive suggestions and encourages more variety in the results.

---

## 6. Limitations and Bias 

The recommender system has several limitations related to the dataset and the scoring logic. First, the dataset is very small, with only a limited number of songs and genres. Because of this, the system cannot represent the full diversity of musical taste, which may cause certain genres or moods to appear more frequently in the recommendations.

Another limitation is that the scoring logic relies heavily on numerical similarity for energy. When the energy weight is increased, high-energy songs tend to dominate the recommendations even if the genre does not match the user’s preference. This can create a bias toward intense or energetic tracks.

The system also assumes that users have clear and consistent preferences. When a profile contains conflicting preferences (for example, requesting ambient music with very high energy and an intense mood), the recommender may produce results that only partially match the request. This shows that the model struggles when user preferences are contradictory. 

---

## 7. Evaluation  

To evaluate the recommender system, I tested several different user profiles representing distinct listening preferences. These included profiles such as High-Energy Pop, Chill Lofi, Deep Intense Rock, and a conflicting profile that requested ambient music with high energy and an intense mood.

For each profile, I ran the recommender and examined the top five suggested songs. I looked at whether the recommended songs matched the intended musical vibe of the user profile, such as relaxed low-energy tracks for the Chill Lofi profile or aggressive high-energy songs for the Deep Intense Rock profile.

One surprising result appeared in the High-Energy Pop test. The song "Sunrise City" consistently ranked first because it matched both the genre and mood while also having a high energy similarity score. This showed that the scoring logic strongly rewards combined matches across multiple features.

I also performed a small experiment by changing the scoring weights. I reduced the genre weight and increased the energy weight to see how the rankings changed. After this change, songs with energy values closer to the user's target became more dominant in the recommendations. This experiment demonstrated how sensitive the system is to weight adjustments and how small scoring changes can significantly influence the final rankings.

---

## 8. Future Work  

Several improvements could make the recommender more realistic.

First, the dataset could be expanded with hundreds or thousands of songs to better represent different musical tastes. A larger catalog would also allow the recommender to provide more diverse suggestions.

Second, additional user preferences could be added, such as tempo range, danceability, or acousticness. These features could help capture more subtle musical preferences.

Finally, the system could include diversity rules to prevent recommending too many songs from the same artist or genre in the top results.

---

## 9. Personal Reflection  

One of the biggest learning moments in this project was seeing how simple scoring rules can produce recommendations that feel surprisingly realistic. Even without machine learning, combining a few features such as genre, mood, and energy can create results that resemble real music recommendation systems.

Using AI tools helped speed up the development process, especially for generating code structure and experimenting with scoring logic. However, it was important to carefully review the generated code to make sure the logic actually matched the intended design.

This project also showed how sensitive recommendation systems are to weight tuning. Small changes to scoring weights can significantly change which songs appear in the top results.

If I continued developing this project, I would explore adding more song features and introducing diversity rules to avoid recommending songs that are too similar to each other.