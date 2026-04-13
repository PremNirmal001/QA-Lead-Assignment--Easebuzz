import requests

import json



1 **API URL**

url = "https://jsonplaceholder.typicode.com/posts"



2 **Fetch data**

response = requests.get(url)



3 **Check status code**

if response.status\_code == 200:

&#x20;   print("Status Code is 200 - Success")

else:

&#x20;   print("Failed with status code:", response.status\_code)



4 **Convert response to JSON**

posts = response.json()



5 **Validate keys in each post**

for post in posts:

&#x20;   if "userId" in post and "id" in post and "title" in post and "body" in post:

&#x20;       continue

&#x20;   else:

&#x20;       print("Missing keys in post:", post)



print("Key validation completed")



6 **Save first 5 posts to file**

first\_5 = posts\[:5]



with open("first\_5\_posts.json", "w") as file:

&#x20;   json.dump(first\_5, file, indent=4)



print("First 5 posts saved successfully")

