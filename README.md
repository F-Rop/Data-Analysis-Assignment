Data-Analysis-Assignment - Netflix shows - MySQL

Dataset Name: Netflix Shows

Task one Data Dive

Findings 
1.Inconsistent Data Formats: For example, dates are in different formats.
2.Missing Values: Some columns are missing critical data.
3.USeof Special Characters: This may cause issues during import.
4.Data Type Mismatch: Some columns supposed to be numeric are text. 

Observation 
1.The data set contains and shows multiple countries use Netflix indicating it's global reach.
2.Wide rage of genres indicating diverese content offserings.
3.Multiple age brackets and ratings indicating shows of diffrenet age groups. 

Task two Data fun
Find's out which year had the most releases.
SELECT release_year, COUNT(*) AS count
FROM netflix_titles
GROUP BY release_year
ORDER BY count DESC
LIMIT 1;
Result: Realse year - 2021 count - 53 

calculate the average duration of shows for each genre(listed_in)to see if some genres tend to have longer or shorter shows.
SELECT listed_in, AVG(duration) AS average_duration
FROM netflix_titles
GROUP BY listed_in
ORDER BY average_duration DESC;
![data fun](https://github.com/F-Rop/Data-Analysis-Assignment/assets/160117048/af74978f-79b1-48ff-a854-8098d76a376c)

This query will show the distribution of show ratings.
SELECT rating, COUNT(*) AS count
FROM netflix_titles
GROUP BY rating
ORDER BY count DESC;
![data fun2](https://github.com/F-Rop/Data-Analysis-Assignment/assets/160117048/9c2c4cd8-11b2-46c4-ba1a-1f56f2fdd44d)

Combining genre with average duration, let’s find out which genres have the longest shows on average.
SELECT listed_in, AVG(duration) AS average_duration
FROM netflix_titles
GROUP BY listed_in
ORDER BY average_duration DESC
LIMIT 5;
![data fun3](https://github.com/F-Rop/Data-Analysis-Assignment/assets/160117048/0102cb26-52e3-4be1-bef8-4542b13da0ab)

This query will show the number of shows produced by each country.
SELECT country, COUNT(*) AS count
FROM netflix_titles
GROUP BY country
ORDER BY count DESC;
![data fun4](https://github.com/F-Rop/Data-Analysis-Assignment/assets/160117048/a2300dcc-b54b-4392-9bf9-68f2dc97fb7a)


This query categorizes shows into different duration ranges, showing the distribution of show lengths.
SELECT
  CASE
    WHEN duration < 30 THEN '< 30 minutes'
    WHEN duration BETWEEN 30 AND 59 THEN '30-59 minutes'
    WHEN duration BETWEEN 60 AND 89 THEN '60-89 minutes'
    ELSE '90+ minutes'
  END AS duration_range,
  COUNT(*) AS count
FROM netflix_titles
GROUP BY duration_range
ORDER BY count DESC;
![data fun 5](https://github.com/F-Rop/Data-Analysis-Assignment/assets/160117048/4f124072-7b0d-4ebc-8968-9d725fbc1c0e)

Task 3 - Ask Away 

This query helps us understand the most popular genres in the United States.
SELECT listed_in, COUNT(*) AS count
FROM netflix_titles
WHERE country = 'United States'
GROUP BY listed_in
ORDER BY count DESC
LIMIT 5;
![ask 1](https://github.com/F-Rop/Data-Analysis-Assignment/assets/160117048/a327818f-c2de-4761-b706-505c1f5dc05e)
Result Analysis:

Documentaries: The high count of documentaries might indicate a strong interest in factual content and educational material among U.S. viewers.
Dramas: The prevalence of dramas suggests a preference for narrative-driven content that explores emotional and relational themes.
Comedies: Comedies are also popular, highlighting a demand for light-hearted and humorous content.
Action & Adventure: The popularity of action and adventure shows points to a taste for thrilling and dynamic storytelling.
Thrillers: The interest in thrillers suggests viewers enjoy suspenseful and gripping content.

This query identifies which rating category has the longest average show duration
SELECT rating, AVG(duration) AS average_duration
FROM netflix_titles
GROUP BY rating
ORDER BY average_duration DESC
LIMIT 1;
![ask2](https://github.com/F-Rop/Data-Analysis-Assignment/assets/160117048/2c9c8328-8c16-465d-a058-121c4fb0c5ce)
TV-MA (Mature Audience): Shows with this rating tend to have the longest average duration. This could be because mature content often includes complex storylines, deeper character development, and themes that require more time to explore.

Conclusion
These queries provided insightful findings:

Popular Genres in the U.S.: Understanding the top genres helps in tailoring content strategies to cater to the U.S. audience's preferences.
Longest Average Show Duration by Rating: Knowing that TV-MA shows have longer durations can inform decisions about content production and scheduling, ensuring that the platform meets the needs of viewers seeking more extensive and in-depth viewing experiences.
By formulating these questions and analyzing the data, we gain valuable insights into viewer preferences and content characteristics, aiding in more informed decision-making for content curation and strategy.

