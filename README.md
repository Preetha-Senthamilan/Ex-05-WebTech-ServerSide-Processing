# Design a Website for Server Side Processing

# AIM:

To design a website to perform mathematical calculations in server side.

# DESIGN STEPS:

### STEP 1:
Clone the repository from github

### STEP 2:
Create Django Admin Project

### STEP 3:
Create new app

### STEP 4:
Create python programs for views and urls

### STEP 5:
Create HTML file of forms

### STEP 6:
Publish the websute in the given url

# PROGRAM:
'''
math.html

<!DOCTYPE html>
<html>
<head>
    <meta charset='utf-8'>
    <meta http-equiv='X-UA-Compatible' content='IE=edge'>
    <title>Volume Calculator</title>
    <meta name='viewport' content='width=device-width, initial-scale=1'>
    
</head>
<style>
    *{
        box-sizing: border-box;
        font-family: Arial, Helvetica, sans-serif;
    }

    body{
    background-color: lightpink;
    color:blue;
    }

    .container{
    width: 1080px;
    height: 350px;
    margin-top: 100px;
    margin-left: auto;
    margin-right: auto;
    border-radius: 25px;
    border: 10px solid lightgreen;
    box-shadow: inset 0 0 15px rgb(231, 217, 160);
    background-color:cornsilk;
    }
    h1{
        color: rgb(0, 0, 0);
        text-align: center;
    }
    .calculate{
        padding-top: 10px;
        padding-bottom: 10px;
        padding-left: 10px;
        padding-right:10px;
        text-align: center;
        font-size: 20px;
        padding-top: 7px;
        font-family: Cambria, Cochin, Georgia, Times, 'Times New Roman', serif;
    }
</style>
<body>
    <div class="container">
        <h1>VOLUME OF OF A CUBOID</h1>
        <h3 align="center">Preetha-Senthamilan(22008734)</h3>
        <form method="POST">
            {% csrf_token %}
            <div class="calculate"> 
                Enter Height:<input type="text" name="height" value={{h}}></input><br/>
            </div>
            <div class="calculate">
                Enter Length:<input type="text" name="length" value={{l}}></input><br/>
            </div>
            <div class="calculate">
                Enter Width:<input type="text" name="width" value={{w}}></input><br/>
            </div>
            <div class="calculate">
                <input type="submit" value="Calculate Volume"></input><br/>
            </div>
            <div class="calculate">
                Volume:<input type="text" name="volume" value={{volume}}></input>
            </div>
        </form>
    </div>
</body>
</html>

views.py


from django.shortcuts import render

def volumecalculation(request):
    context ={}
    context["volume"]='0'
    context["h"]='0'
    context["l"]='0'
    context["w"]='0'
    if request.method == 'POST':
        
        h=request.POST.get('height','0')
        l=request.POST.get('length','0')
        w=request.POST.get('width','0')
        volume=int(h)*int(l)*int(w)
        context['volume'] = volume
        context['l']=l
        context['h']=h
        context['w']=w
    return render(request,"myapp/math.html",context)


urls.py

from django.contrib import admin
from django.urls import path
from myapp import views

urlpatterns = [
    path('admin/', admin.site.urls),
    path('volofrectangulartank/',views.volumecalculation,name="volofrectangulartank"),
    path('',views.volumecalculation,name="volofrectangulartankroot")
]
'''

## OUTPUT:
![OUTpUT](./home.png)

# RESULT:

The program for implemtimg server side processing is completed successfully
