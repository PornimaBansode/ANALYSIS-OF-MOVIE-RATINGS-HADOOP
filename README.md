# ANALYSIS-OF-MOVIE-RATINGS-HADOOP

Implementation Details- 
 
While working on a Hadoop project, we need to look at few prior requirements which shall be met, these are as follows:- 1. Operating System: Using a 64-bit operating system helps to avoid constraining the amount of memory that can be used on worker nodes. 2. Computation V/S Data: Computational (or processing) capacity is determined by the aggregate number of Map/Reduce slots available across all nodes in a cluster. Map/Reduce slots are configured on a perserver basis. 3. Memory: Depending on the application, system’s memory requirements will vary. 4. Storage: A Hadoop platform that’s designed to achieve performance and scalability by moving the activity to the data is preferable.  5.  Capacity: The number of disks and their corresponding storage capacity determines the total amount of the FileServer storage capacity for your cluster. The more disks we have, the less likely it is that we will have multiple tasks accessing a given disk at the same time.  6. Network:  Hadoop is very bandwidth-intensive, Use dedicated switches use rack awareness.  
 
Once these things are appropriate, we can move further to the next step Data Life Cycle in Hadoop. 1. Data collection: - The data that is collected is the Raw Data which needs to be filtered using different tools. 2. Data transferring- Apache Sqoop is used to transfer the data between Apache Hadoop and structured datastores such as relation database. 3. Data Storage: - As I have used Red Hat Linux BigInsights by IBM, the storage is done in HDFS and Hive. But, before storing ETL was performed. 4. Data Processing: - Since MapReduce is a tedious job, the preference in this project was given to HIVE and PIG for processing the data efficiently.  
 
 
 
The Movie data is collected from the GroupLens Research Project where the data can answer the following questions: - • List the unique user id of female users whose age is between 20 - 30 and who has rated the highest rated Action AND War movies. 
 
• Find top 10 average rated “Action" movies in descending order of rating. 
 
 
• List all the movies with its genre where the movie genre is Action or Drama and the average movie rating is in between 4.4 - 4.7 and only the male users rate the movie. 
 
• Analysis of top 20 movies. 
 
 
• Analysis of different genres of movies. 
 
• Analysis of a number of females and males who rated the movies. 
 
 
• Find movies rated based on the occupation of the user. 
 
• Age analysis of the user who has rated the movies. 
 
Analysis of Movie Data using Pig- I used Movie dataset for analysis with Pig. Three datasets of varying sizes are available from the site. The data was download and unzipped. It contains three text files: ratings.dat, users.dat, and movies.dat. We can view them in Notepad+ on Windows since for this project Linux is been used, we preferred vi editor. Contents of these files are described in README that accompanies the dataset. For the sake of completeness, data in the three files is briefly described here- 
 
# Ratings Data 
ratings.dat–>userid::movieid:rating::timestamp 
 
userid ranges from 1 to 6040,  
movieid ranges from 1 to 3952,  rating is made on a five-star discrete scale (whole-star rating only) and timestamp is in seconds. 
 

# Users data 
 
users.dat–>userid::gender::age::occupation::zipcode 
 
gender is M or F;  age is categorized as 1, 18, 25, 35,45, 50, 56.  The meanings are:  1: <18;  18: 18-24;  25: 25-34;  35: 35-44;  45: 45-49;  50: 50-55;  56 is 56+. 
 
Occupation is one of these:  0: other,  1: academic/educator ;  2: artist ;  3: clerical/admin ;  4: college/grad student ;  5: customer service ;  6: doctor/health care ;  7: executive/managerial ;  8: farmer ;  
9: homemaker ;  10: K-12 student ;  11: lawyer ;  12: programmer ;  13: retired ;  14: sales/marketing ;  15: scientist ;  16: self-employed ;  17: technician/engineer ;  18: tradesman/craftsman ;  19: unemployed ;  20: writer 
 
# Movies Data 
movies.dat–>movieID::title::genres 
 
Titles are movie titles and genres are pipe-separated and are selected from the following genres: Action, Adventure, Animation, Children’s, Comedy, Crime, Documentary, Drama, Fantasy, Film-Noir, Horror, Musical, Mystery, Romance, Sci-Fi, Thriller, War, Western 
 
Field separators are a double colon. Since working with double colon becomes tedious, these are substituted with a comma. Further, the whole directory is copied to the Hadoop folder. The following shell script does the preparatory work of inserting a comma as field separator and copying the whole movie folder to Hadoop. The machine has BigInsights installed.      The data is loaded in the hdfs at path        “/user/biadmin/pornima/processed_data” 
 
The three data files are located at  • Movies data- /user/biadmin/pornima/processed_data/moviesnew.dat • Ratings data- /user/biadmin/pornima/processed_data/ratingsnew.dat • Users data- /user/biadmin/pornima/processed_data/usersnew.dat Similarly, the pig queries are stored in the above given path. 

 
 
# Analysis of Movie Data using Hive: 
 
The Hive output is also stored in the HDFS. The storage path is “/biginsights/hive/warehouse/imdb.db”. Here, ‘imdb.db’ is the database where all the hive queries are stored.  
 
# Experimental setup and results: 
 
Operating System: Red Hat Linux. Software used: VMware Workstation, IBM Biginsights. Visualization tools: BigSheets and Tableau Public 10.2. 
 
Following are the details of data which has been used for the analysis-

![Movie Genres](testImages/Capture1.jpg)
 
