# Reproductibility_Paper
PatentSBERTa: A Deep NLP based Hybrid Model for Patent Distance and Classification using Augmented SBERTa
## PatentView API

````
```
import requests
from tqdm import tqdm

condition = '&f=["patent_abstract","patent_id"]' # abstract, id
url_post = 'https://api.patentsview.org/patents/query?q={"patent_number":"' # input : patent_number


dict_list=[]

for i in tqdm(range(len(df))):
    num = df['patent_number'][i] # input columns == patent_number
    api_url = url_post + str(num) + '"}' + condition  # host
    api_data = requests.get(api_url)
    api_json = api_data.json()

    if api_json['patents'] != None:
        dict_list.extend(api_json['patents']) # update if not-none
    
    if i % 100 == 0:
        final = pd.DataFrame.from_dict(dict_list) # dictionary to dataframe

final
```
````
