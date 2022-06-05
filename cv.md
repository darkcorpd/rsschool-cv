# **Albert Tuykin**

Junior Data Scientist

![Photo](https://github.com/darkcorpd/darkcorpd.github.io/blob/main/avatar400.jpg)
---

## Contacts

**Location:** Kazan, Russia

**Phone:** +7 917 2202320

**E-mail:** darkcorpd@gmail.com

**Telegram:** @darkcorp

**GitHub:** [darkcorpd](https://github.com/darkcorpd/)

---

## Briefly About Myself:

*I have an extensive experience in the financial sector as an analyst, risk manager and trader. 
Daily work with a lot of data, processing with Excel, VBA, Python. Operating experience with information systems Bloomberg, Cbonds, RuData etc.
Used to provide maintenance of financial companies in different jurisdictions (Russia, Cyprus, Switzerland, Cayman Islands, USA, Estonia). 
My goal is to become a full stack data scientist.*

---

## Skills and Proficiency:

* Excel, VBA, PowerQuery
* Python, R, SQL
* JavaScript Basics
* HTML, CSS Basics
* Git, GitHub
* VS Code


## Code example:
```
# Load historical prices and volumes from MOEX for liquidity report

import requests
import apimoex
import pandas as pd
import urllib.request, json 

def load_prices(securities, 
                start, 
                end):
    result = []
    for security in securities:
            with urllib.request.urlopen(f'https://iss.moex.com/iss/securities.json?q={security}') as url:
                data = json.loads(url.read().decode())
                ticker = data['securities']['data'][0][1]
    
            with requests.Session() as session:
                data = apimoex.find_securities(session, 
                                               security, 
                                               columns = None)
                df = pd.DataFrame(data)
                board = df.at[0, 'primary_boardid']
                engine = 'futures' if board == 'RFUD' else 'stock'
                market = 'forts' if board == 'RFUD' else 'shares'
                start_date = start
                end_date = end
                data = apimoex.get_board_history(session, 
                                                 security = ticker, 
                                                 start = start_date, 
                                                 end = end_date, 
                                                 columns = ['SECID', 
                                                            'TRADEDATE', 
                                                            'HIGH', 
                                                            'LOW', 
                                                            'CLOSE', 
                                                            'VOLUME'], 
                                                 board = board, 
                                                 market = market, 
                                                 engine = engine)
                result.extend(data[-10:])
  
    df = pd.DataFrame(result)
    df.set_index('SECID', inplace=True)
    # To save to .csv uncomment
    # df.to_csv(f'{security}_{start_date}-{end_date}.txt',sep='\t', index=False)
    # To print as a plain text uncomment
    # print(df.to_string())
    return df


# ============================================================================== #
# Set initial data:
securities  = ['CHMF', 
               'TATNP', 
               'PHOR', 
               'BRM2', 
               'RU0007661625']
start       = '2022-04-01'  #YYYY-MM-DD
end         = '2022-04-30'  #YYYY-MM-DD

load_prices(securities, start, end)

```

---

## Education:
2021 - **Creating and Applying Big Data Technologies** - NTI Educational Competence Center, Kazan

2009 - **Engineer in Aircraft and Helicopter Engineering** - 
Kazan National Research Technical University, Kazan

2005 - **Finance and Credit, Banking** - 
Kazan State Institute of Finance and Economics, Kazan

## Additional education:

* Coursera courses:
  - Foundations: Data, Data, Everywhere by Google
  - Ask Questions to Make Data-Driven Decisions by Google
  - Data Analysis with Python by IBM
  - Databases and SQL for Data Science with Python by IBM
  - Inferential Statistics by Duke University
  - SQL for Data Science by University of California, Davis
  - Mathematics and Python for Data Science

* Basic Statistics on Stepik
* Basic SQL, Python, R, HTML, Statistics courses on Sololearn, DataCamp, w3schools, Stepik and other resources.
* JavaScript Manual on learnjavascript.ru (*in progress*)
* RS Schools Course «JavaScript/Front-end. Stage 0» (*in progress*)

## Languages:
* English - Intermediate/Upper-intermediate
* Russian - Native
* German - Basic/Intermediate
* Turkish - Basic/Intermediate
