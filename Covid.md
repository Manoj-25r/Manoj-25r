{'User-Agent': 'Mozilla/5.0 (Macintosh; Intel Mac OS X 10_10_1) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/39.0.2171.95 Safari/537.36'}

from fake_useragent import UserAgent
user_agent = UserAgent()
    
from typing import Union
import requests
from requests.exceptions import HTTPError
import json

url="https://cdn-api.co-vin.in/api/v2/appointment/sessions/public/findByPin?pincode=831001&date=31-03-2021"

def call_api(url) -> Union[HTTPError, dict]:
        # user_agent = UserAgent()
        # headers = headers={'User-Agent': user_agent  }
        headers = headers={'User-Agent': 'Mozilla/5.0 (Macintosh; Intel Mac OS X 10_10_1) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/39.0.2171.95 Safari/537.36'}
        response = requests.get(url, headers=headers)
        try:
            response.raise_for_status()
        except requests.exceptions.HTTPError as e:
            return e

        return response.json()

response= call_api(url)
print(json.dumps(response,indent = 4))
Response from server

{
    "sessions": [
        {
            "center_id": 627226,
            "name": "ASG Hospital Covishield",
            "address": "",
            "state_name": "Jharkhand",
            "district_name": "East Singhbhum",
            "block_name": "Jugalsalai Sah Golmu",
            "pincode": 831001,
            "from": "19:30:00",
            "to": "14:30:00",
            "lat": 22,
            "long": 86,
            "fee_type": "Paid",
            "session_id": "735811ed-f841-49e4-b129-62ac7e9fef37",
            "date": "31-03-2021",
            "available_capacity_dose1": 0,
            "available_capacity_dose2": 0,
            "available_capacity": 100,
            "fee": "0",
            "min_age_limit": 45,
            "vaccine": "COVISHIELD",
            "slots": []
        }
    ]
}
Without passing header data
    
from typing import Union
import requests
from requests.exceptions import HTTPError
import json

url="https://cdn-api.co-vin.in/api/v2/appointment/sessions/public/findByPin?pincode=831001&date=31-03-2021"

def call_api(url) -> Union[HTTPError, dict]:

        response = requests.get(url)
        try:
            response.raise_for_status()
        except requests.exceptions.HTTPError as e:
            return e

        return response.json()

response= call_api(url)
print(response))
Response from server

403 Client Error: Forbidden for url: https://cdn-api.co-vin.in/api/v2/appointment/sessions/public/findByPin?pincode=831001&date=31-03-2021
