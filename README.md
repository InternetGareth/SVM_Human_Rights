# Human Rights in the News

A global heads-up dashboard of on-going and emerging humnan rights issues will rely at least in part on injesting, classifying, and geolocating human rights related news stories from around the world. This code represents a Minimum Viable Product demonstration of just such a pipeline. The model serves as a first step towards far more sophisticated approaches which have allready been implmeneted for general news stories by projects such as GDELT (https://www.gdeltproject.org/).

For a full discussion on the use case, end user, and product development perspective of this project, please refer to: https://www.garethwalker.me/microsoft-ai-for-good

# A outline of the pipeline

Data pipeline is as follows:

1) RSS feeds relating to human rights news are injested using feedparser (https://github.com/kurtmckee/feedparser). Note: In addition to sources such as Amnesty International, UNHRC, customer RSS feeds based on human rights related search terms used for both Google and Bing.

2) Title and body text are classified and evaluated using a Support Vector Machine text classifier (trained on US Justice Department reports)

3) Location entities are extracted using entity detection module of Spacy package. Stories for which locations cannot be identified are dropped.

4) Location entities are passed to Google Maps API to obtain latitude and longitude coordinates. Locations for which latitude and longitude cannot be found are dropped.

5)  New story title, date, human rights catagory, location, and coordinates are stored in a pandas dataframe and exported as CSV.

6) CSV injested into Tableau visualisation.

![Outline of approach](https://images.squarespace-cdn.com/content/v1/5b996a2bfcf7fda4e9eeb3a1/1559322844450-EZ8F05F1JZO802QJ6CRZ/ke17ZwdGBToddI8pDm48kD33KhhWEodMJvcytjXFyvFZw-zPPgdn4jUwVcJE1ZvWQUxwkmyExglNqGp0IvTJZamWLI2zvYWH8K3-s_4yszcp2ryTI0HqTOaaUohrI8PIQVUjsvMYGrjk5P5guv3Gb1aPQrnDLhtGUJ-UJkarKCw/Gareth+Walker+-+Data+for+Social+Good+%283%29.png?format=1500w)



SVM model trained on US State Department Country Reports on Human Rights
Model then applied to RSS News Feeds generated using human rights key words and/or feeds dedicated to human rights issues
Entity recognition and google API use to locate news stories


# Model evaluation



![Model performance](https://github.com/InternetGareth/SVM_Human_Rights/blob/master/Data/performance.png)

# Training Data Requirement

Requires following file to be placed in 'Data/'

'us_state_dept_reports_1999_2018.csv'

Can be download here:
https://drive.google.com/file/d/1DhSlWI_2nKozM8Gcn7fy34kSBwzHjMSm/view?usp=sharing

# API requirements

Google maps API key required for geolocating news stories

