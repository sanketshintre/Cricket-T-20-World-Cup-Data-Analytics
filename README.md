# Cricket-T-20-World-Cup-Data-Analytics

# Cricket-T-20-World-Cup-Data-Analytics-

# Cricket Analysis [Python | Web scrapping | Pandas | Power BI]
• Created a Power BI report to identify top 11 players for a T20 cricket team by scraping data from espncricinfo
with a Brightdata website tool, cleaning and transforming the data with pandas, and evaluating various player
performance metrics.
• Used the resulting Power BI dashboard to select players for various categories (openers, middle order/anchors,
finishers, all-rounders, specialist fast bowlers) and ultimately choose the top 11 players to play in the match.
• Selected team using the Power BI dashboard

# Data Processing using Pandas
#import necessary libraries
import pandas as pd
import json
with open('t20_json_files/t20_wc_match_results.json') as f:
data = json.load(f)
df_match = pd.DataFrame(data[0]['matchSummary'])
df_match.head()
team1 team2 winner margin ground

matchDate \
0 Namibia Sri Lanka Namibia 55 runs Geelong Oct 16,
2022
1 Netherlands U.A.E. Netherlands 3 wickets Geelong Oct 16,
2022
2 Scotland West Indies Scotland 42 runs Hobart Oct 17,
2022
3 Ireland Zimbabwe Zimbabwe 31 runs Hobart Oct 17,
2022
4 Namibia Netherlands Netherlands 5 wickets Geelong Oct 18,
2022
scorecard
0 T20I # 1823
1 T20I # 1825
2 T20I # 1826
3 T20I # 1828
4 T20I # 1830
df_match.shape
(45, 7)
Use scorecard as a match id to link with other tables
df_match.rename({'scorecard': 'match_id'}, axis = 1, inplace = True)
df_match.head()

team1 team2 winner margin ground
matchDate \
0 Namibia Sri Lanka Namibia 55 runs Geelong Oct 16,
2022
1 Netherlands U.A.E. Netherlands 3 wickets Geelong Oct 16,
2022
2 Scotland West Indies Scotland 42 runs Hobart Oct 17,
2022
3 Ireland Zimbabwe Zimbabwe 31 runs Hobart Oct 17,
2022
4 Namibia Netherlands Netherlands 5 wickets Geelong Oct 18,
2022

match_id
0 T20I # 1823
1 T20I # 1825
2 T20I # 1826
3 T20I # 1828
4 T20I # 1830

Create a match ids dictionary that maps team names to a unique match id. This will
be useful later on to link with other tables
match_ids_dict = {}
for index, row in df_match.iterrows():
key1 = row['team1'] + ' Vs ' + row['team2']
key2 = row['team2'] + ' Vs ' + row['team1']
match_ids_dict[key1] = row['match_id']
match_ids_dict[key2] = row['match_id']
df_match.to_csv('t20_csv_files/dim_match_summary.csv', index = False)
with open('t20_json_files/t20_wc_batting_summary.json') as f:
data = json.load(f)
all_records = []
for rec in data:
all_records.extend(rec['battingSummary'])
df_batting = pd.DataFrame(all_records)
df_batting.head(11)
match teamInnings battingPos
batsmanName \
0 Namibia Vs Sri Lanka Namibia 1 Michael van
Lingen
1 Namibia Vs Sri Lanka Namibia 2 Divan la
Cock
2 Namibia Vs Sri Lanka Namibia 3 Jan Nicol Loftie-
Eaton
3 Namibia Vs Sri Lanka Namibia 4 Stephan
Baard
4 Namibia Vs Sri Lanka Namibia 5 Gerhard
Erasmus(c)
5 Namibia Vs Sri Lanka Namibia 6 Jan
Frylinck
6 Namibia Vs Sri Lanka Namibia 7 David
Wiese
7 Namibia Vs Sri Lanka Namibia 8 JJ
Smit
8 Namibia Vs Sri Lanka Sri Lanka 1 Pathum
Nissanka
9 Namibia Vs Sri Lanka Sri Lanka 2 Kusal


# Player Selection Based On criteria:


<img width="960" alt="2023-02-22 (4) - Copy" src="https://user-images.githubusercontent.com/123626990/229266406-c9592427-94bd-4719-a1dd-44e0421c1ded.png">
<img width="960" alt="2023-02-22 (5)" src="https://user-images.githubusercontent.com/123626990/229266408-3494fe28-0a1c-4117-bcf2-6f278909eb38.png">
<img width="960" alt="2023-02-22 (6)" src="https://user-images.githubusercontent.com/123626990/229266410-aa8e551e-5d78-4e24-8ea1-0d8f513b2419.png">
<img width="960" alt="2023-02-22 (7)" src="https://user-images.githubusercontent.com/123626990/229266411-8f17d3af-825f-4a17-a30f-50cad5e8fef0.png">
<img width="960" alt="2023-02-22 (8)" src="https://user-images.githubusercontent.com/123626990/229266402-23f2d03a-e21b-4d32-909f-6c445db9a1dc.png">

# Player Selection Based On criteria in Power BI:

<img width="960" alt="2023-04-01" src="https://user-images.githubusercontent.com/123626990/229270135-048c0975-28cd-4a59-bf4d-d4ebf5e50cd4.png">
<img width="960" alt="2023-04-01 (1)" src="https://user-images.githubusercontent.com/123626990/229270144-415ee727-c17c-4217-a6da-f8f08b5089ae.png">
<img width="960" alt="2023-04-01 (2)" src="https://user-images.githubusercontent.com/123626990/229270157-0601e7ab-b637-4074-8206-fa16126e6112.png">
<img width="960" alt="2023-04-01 (3)" src="https://user-images.githubusercontent.com/123626990/229270167-28393f77-b32a-4c82-9bfe-6f63ff5032fe.png">
<img width="960" alt="2023-04-01 (4)" src="https://user-images.githubusercontent.com/123626990/229270203-e1dfe1ae-8836-4592-9d36-2ebda5ec218c.png">


# Cricket T-20 World-Cup Best 11 in Power BI

<img width="960" alt="2023-02-22 (9)" src="https://user-images.githubusercontent.com/123626990/229266574-5d09b9dc-d7d5-470c-bf26-6cd16642e9e0.png">
<img width="960" alt="2023-02-22 (10)" src="https://user-images.githubusercontent.com/123626990/229266582-e26f6423-5003-4e39-83bd-2f9ab88e9048.png">
<img width="960" alt="2023-02-22 (11)" src="https://user-images.githubusercontent.com/123626990/229266589-9302ef98-46bf-402f-9366-f8ed156def2a.png">
