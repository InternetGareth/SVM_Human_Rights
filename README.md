# SVM_Human_Rights
A text classification tool for mapping human rights abuses in news articles

# Approach
SVM model trained on US State Department Country Reports on Human Rights
Model then applied to RSS News Feeds generated using human rights key words and/or feeds dedicated to human rights issues
Entity recognition and google API use to locate news stories
![Outline of approach](https://images.squarespace-cdn.com/content/v1/5b996a2bfcf7fda4e9eeb3a1/1559322844450-EZ8F05F1JZO802QJ6CRZ/ke17ZwdGBToddI8pDm48kD33KhhWEodMJvcytjXFyvFZw-zPPgdn4jUwVcJE1ZvWQUxwkmyExglNqGp0IvTJZamWLI2zvYWH8K3-s_4yszcp2ryTI0HqTOaaUohrI8PIQVUjsvMYGrjk5P5guv3Gb1aPQrnDLhtGUJ-UJkarKCw/Gareth+Walker+-+Data+for+Social+Good+%283%29.png?format=1500w)

# Training Data Requirement

Requires following file to be placed in 'Data/'

'us_state_dept_reports_1999_2018.csv'

Can be download here:
https://drive.google.com/file/d/1DhSlWI_2nKozM8Gcn7fy34kSBwzHjMSm/view?usp=sharing

# API requirements

Google maps API key required for geolocating news stories

