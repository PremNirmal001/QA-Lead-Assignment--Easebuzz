1\. **Project Structure**



project/

\-test\_api.py

\-requirements.txt





2\. **Install Dependency**

pip install pytest requests jsonschema





3\. **Pytest Test Suite**



import requests

import pytest

from jsonschema import validate



BASE\_URL = "https://jsonplaceholder.typicode.com"



\# Simple schemas

post\_schema = {

&#x20;   "type": "object",

&#x20;   "required": \["userId", "id", "title", "body"]

}



comment\_schema = {

&#x20;   "type": "object",

&#x20;   "required": \["postId", "id", "name", "email", "body"]

}



user\_schema = {

&#x20;   "type": "object",

&#x20;   "required": \["id", "name", "username", "email"]

}



\# Parameterized test

@pytest.mark.parametrize("endpoint, schema", \[

&#x20;   ("/posts", post\_schema),

&#x20;   ("/comments", comment\_schema),

&#x20;   ("/users", user\_schema)

])

def test\_api(endpoint, schema):

&#x20;   response = requests.get(BASE\_URL + endpoint)



&#x20;   # Status code check

&#x20;   assert response.status\_code == 200



&#x20;   # Response time check

&#x20;   assert response.elapsed.total\_seconds() < 2



&#x20;   # Schema validation (only required keys)

&#x20;   data = response.json()

&#x20;   for item in data:

&#x20;       validate(instance=item, schema=schema)



4\. **Run Command**

pytest -v





