APP:
General info:
Flask app 
Written in python 3.

Flow:
app fetch Covid-19 data from https://corona.lmao.ninja API.
app serves 4 endpoints - every endpoint has its own app.route.
every endpoint trigger a function (get) with 2 parameters - endpoint and country:
“get” function is located under app.context_processor, the app gets 2 parameters and executes the API call to the data source. 
 In order to get the wanted data, the JSON response file from the data source is being sorted and the first pair of “key-value” are printed. 

Jenkinsfile:
Declarative pipeline that creates a parametrized job with 3 stages:
Job params are endpoint and country.
Stage 1 - “clone”: 
Clone the repo from github.
Stage 2- “build_app”:
Run the flask app script and enable requests to localhost. (use flask default port - 5000)
Note - the script command is “python3.6” (I have also python 2.7 on my jenkins server), please change it to “python” if needed. 
Stage 3 - “tests”:
Executing the command “curl localhost:5000/status” to access check the “status” endpoint.
Executing curl command with the chosen parameters. 


