# Ex.05 Design a Website for Server Side Processing
# Date:15-11-2024
# AIM:
To design a website to calculate the power of a lamp filament in an incandescent bulb in the server side.

# FORMULA:
P = I2R
P --> Power (in watts)
 I --> Intensity
 R --> Resistance

# DESIGN STEPS:
## Step 1:
Clone the repository from GitHub.

## Step 2:
Create Django Admin project.

## Step 3:
Create a New App under the Django Admin project.

## Step 4:
Create python programs for views and urls to perform server side processing.

## Step 5:
Create a HTML file to implement form based input and output.

## Step 6:
Publish the website in the given URL.

# PROGRAM :
math.html
~~~
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Mathserver</title>
    <style>
        
.container {
    width: 300px;
    margin: 0 auto;
    padding: 20px;
    text-align: center;
    margin-top: 10%;
    background-color: #f9f9f9;
    border: 1px solid #ccc;
    border-radius: 8px;
}

h1 {
    font-size: 1.5rem;
    color: #333;
    margin-bottom: 20px;
}

.formelt {
    margin-bottom: 15px;
}

input[type="text"] {
    width: 90%;
    padding: 8px;
    border: 1px solid #ccc;
    border-radius: 4px;
    font-size: 1rem;
}

input[type="submit"] {
    padding: 10px 20px;
    background-color: #007BFF;
    color: white;
    border: none;
    border-radius: 4px;
    font-size: 1rem;
    cursor: pointer;
}

input[type="submit"]:hover {
    background-color: #0056b3;
}

    </style>
</head>
<body>
        <div class="container" style="text-align: center;">
            <h1>Volume of the cube</h1>
            <form method="POST">
                {% csrf_token %}
                <div class="formelt">
                    Radius: <input type="text" name="radius" value="{{r}}">m<br/>
                </div>
                <div class="formelt">
                    Height: <input type="text" name="height" value="{{h}}">m<br/>
                </div>
                <div class="formelt">
                    <input type="submit" value="Calculate"><br/>
                </div>
                <div class="formelt">
                    Volume: <input type="text" name="Volume" value="{{vol}}">m<sup>3</sup><br/>
                </div>
            </form>
        </div>
  
</body>
</html>
~~~
views.py
~~~
from django.shortcuts import render

def volume(request):
    context = {}
    context['vol'] = "0"
    context['r'] = "0"
    context['h'] = "0"
    
    if request.method == 'POST':
        print("POST method is used")
        
        print('request.POST:', request.POST)
        
        r = request.POST.get('radius', '0') 
        h = request.POST.get('height', '0') 
        print('radius =', r)
        print('height =', h)
        
        vol = 1/3 * 3.14 * int(r) *int(r) *int(h)
        context['vol'] = vol
        context['r'] = r
        context['h'] = h
        print('Volume of Cube =', vol)
    
    return render(request, 'mathapp/math.html', context)
~~~
urls.py
~~~

from django.contrib import admin
from django.urls import path
from mathapp import views
urlpatterns = [
    path('admin/', admin.site.urls),
    path('volume/',views.volume,name="volumeofcube"),
    path('',views.volume,name="volumeofcube")
]
~~~
# SERVER SIDE PROCESSING:
![terminal](https://github.com/user-attachments/assets/544063d4-3536-4f27-8ec6-0b734c352935)


# HOMEPAGE:
![Ir2](https://github.com/user-attachments/assets/570c6868-7b51-45e7-8b20-a4cc98cc5a7f)


# RESULT:
The program for performing server side processing is completed successfully.
