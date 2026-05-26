# Ex.04 Design a Website for Server Side Processing


## AIM:
To create a web page to calculate vehicle mileage and fuel efficiency using server-side scripts.

## FORMULA:
M = D / F
<br> M --> Mileage (in km/l)
<br> D --> Distance Travelled (in km)
<br> F --> Fuel Consumed (in l)

## DESIGN STEPS:

### Step 1:
Clone the repository from GitHub.

### Step 2:
Create Django Admin project.

### Step 3:
Create a New App under the Django Admin project.

### Step 4:
Create python programs for views and urls to perform server side processing.

### Step 5:
Create a HTML file to implement form based input and output.

### Step 6:
Publish the website in the given URL.

## PROGRAM:
```
mathexp_5.html [ HTML code]
<html>
    <head>
        <style>
            body 
            {
            font-family:Arial,sans-serif;
            background-color:rgb(109, 242, 73);
            color:white;
            display:flex;
            justify-content: center;
            align-items: center;
            height:100vh;
            border-radius: 5%;
            background: rgb(215, 40, 221);
            }
            .table  
            {

                width: 550px;
                height: 400px;
                background-color: crimson;
                border: 5px solid cyan;
                padding: 40px;
                margin: 100px auto;
                text-align: center;
            }
        </style>
    </head>

    
<body>
    <div class="table">
        <h1>Mileage Calculator</h1>
        <h3>R NITHISH AADITIYAA [25011876]</h3>

        <form method="POST">
            {% csrf_token %}

            <label>Distance:</label>
            <input type="number" name="distance" value="{{ km }}">
            <br><br>

            <label>Fuel:</label>
            <input type="number" name="fuel" value="{{ lt }}">
            <br><br>

            <button type="submit">Calculate</button>
            <br><br>

            <label>Mileage (KM/Litre):</label>
            <input type="number" value="{{ mileage }}" readonly> km/l
        </form>
    </div>
</body>
</html>

views.py

from django.shortcuts import render
def mileage(request):
    km = int(request.POST.get('distance', 0))
    lt = int(request.POST.get('fuel', 0))
    mileage = km * lt if request.method == 'POST' else 0
    print("Distance=",km)
    print("Fuel=",lt)
    print("Mileage=",mileage)
    return render(request, 'mathserverapp/mathexp_5.html', {'km': km, 'lt': lt, 'mileage': mileage})

urls.py

from django.contrib import admin

from django.urls import path
from mathserverapp import views
urlpatterns = [
    path('', views.mileage, name='mileage'),
]

```

## OUTPUT - SERVER SIDE:

![alt text](<Screenshot (156).png>)

## OUTPUT - WEBPAGE:

![alt text](<Screenshot (157).png>)

## RESULT:
The a web page to calculate vehicle mileage and fuel efficiency using server-side scripts is created successfully.
