# Human rights in the news

A global heads-up dashboard of on-going and emerging human rights issues will rely at least in part on ingesting, classifying, and geolocating human rights related news stories from around the world. This code represents a Minimum Viable Product demonstration of such a pipeline. The model serves as a first step towards far more sophisticated approaches which have already been implemented for general news stories by projects such as GDELT (https://www.gdeltproject.org/).

For a full discussion on the use case, end user, and product development perspective of this project, please refer to: https://www.garethwalker.me/microsoft-ai-for-good

# A outline of the pipeline

Data pipeline is as follows:

1) RSS feeds relating to human rights news are ingested using feedparser (https://github.com/kurtmckee/feedparser). Note: In addition to sources such as Amnesty International, UNHRC, customer RSS feeds based on human rights related search terms used for both Google and Bing.

2) Title and body text are classified and evaluated using a Support Vector Machine text classifier (trained on US Justice Department reports)

3) Location entities are extracted using entity detection module of Spacy package. Stories for which locations cannot be identified are dropped.

4) Location entities are passed to Google Maps API to obtain latitude and longitude coordinates. Locations for which latitude and longitude cannot be found are dropped.

5)  News story title, date, human rights category, location, and coordinates are stored in a pandas dataframe and exported as CSV.

6) CSV ingested into Tableau visualization.

![Outline of approach](https://images.squarespace-cdn.com/content/v1/5b996a2bfcf7fda4e9eeb3a1/1559322844450-EZ8F05F1JZO802QJ6CRZ/ke17ZwdGBToddI8pDm48kD33KhhWEodMJvcytjXFyvFZw-zPPgdn4jUwVcJE1ZvWQUxwkmyExglNqGp0IvTJZamWLI2zvYWH8K3-s_4yszcp2ryTI0HqTOaaUohrI8PIQVUjsvMYGrjk5P5guv3Gb1aPQrnDLhtGUJ-UJkarKCw/Gareth+Walker+-+Data+for+Social+Good+%283%29.png?format=1500w)



SVM model trained on US State Department Country Reports on Human Rights
Model then applied to RSS News Feeds generated using human rights key words and/or feeds dedicated to human rights issues
Entity recognition and google API use to locate news stories


# Model evaluation

When applied to training data, model achieves an accuracy, precision, and recall of 76%. However, when applied to news stories, accuracy drops to 67%, recall to 60%, and precision to 62%. This is most likly due to the model over-fitting to the domain-specific language of the training corpus (official reports) and subsequently struggling to interpret the more generalized language of news stories. Some measures were taken to limit this over fitting, including limited the number of features held within the TFIDF vectorizor to the 400 most frequent terms (after stop words are removed).

![Model performance](https://github.com/InternetGareth/SVM_Human_Rights/blob/master/Data/performance.png)


# Using the model
Custom RSS feeds can be defined within the code. The output will be a CSV file containing the news story title, date, human rights category, location, and coordinates. This is then ready to be ingested by a data visualization or GIS platform. For an example of see the following:

https://public.tableau.com/profile/gareth.walker#!/vizhome/MappingHumanRightsNews-Updated/HumanRightsinthenews



# Training Data Requirement

Requires following file to be placed in 'Data/'

'us_state_dept_reports_1999_2018.csv'

Can be download here:
https://drive.google.com/file/d/1DhSlWI_2nKozM8Gcn7fy34kSBwzHjMSm/view?usp=sharing

# API requirements

Google maps API key required for geolocating news stories
