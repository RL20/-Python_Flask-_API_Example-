# Python Flask API example 
## Answer to your question Chananel 

Here's a simple example of how you can use Python Flask to retrieve data from an API and display it on a web page:
```python
from flask import Flask, render_template
import requests

app = Flask(__name__)

@app.route("/")
def index():
    # Make a request to the API
    response = requests.get("https://api.example.com/data")

    # Check if the API request was successful
    if response.status_code == 200:
        # Retrieve the data from the API
        data = response.json()

        # Render the data on a template
        return render_template("index.html", data=data)
    else:
        # Return an error message if the API request was not successful
        return "Could not retrieve data from API"

if __name__ == "__main__":
    app.run(debug=True)

```

The above code uses the requests library to make a GET request to the API at https://api.example.com/data. If the API returns a status code of 200 (indicating a successful response), the code retrieves the data from the API in JSON format and passes it to a template named index.html for display.

You would also need to create a template file templates/index.html that can display the data retrieved from the API. For example:
```css
<h1>Data from API</h1>
<ul>
{% for item in data %}
    <li>{{ item }}</li>
{% endfor %}
</ul>
```

This template uses the Jinja2 templating language to loop through the data and display each item as a list item in an unordered list.






