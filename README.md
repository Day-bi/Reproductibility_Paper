# Reproductibility_Paper
PatentSBERTa: A Deep NLP based Hybrid Model for Patent Distance and Classification using Augmented SBERTa
## PatentView API

````
```
import requests
from tqdm import tqdm

condition = '&f=["app_number","patent_id","cpc_section_id","cpc_group_id","cpc_subgroup_id","cpc_category"]'
url_post = 'https://api.patentsview.org/patents/query?q={"patent_number":"'


dict_list=[]

for i in tqdm(range(len(df))):
    num = df['appl_id'][i]
    api_url = url_post + str(num) + '"}' + condition
    api_data = requests.get(api_url)
    api_json = api_data.json()
    if api_json['patents'] != None:
        dict_list.extend(api_json['patents']) #된거
    
    if i % 100 == 0:
        final = pd.DataFrame.from_dict(dict_list)

final
```
````
