# Design a Website for Server Side Processing

## AIM:
To design a website to perform mathematical calculations in server side.

## DESIGN STEPS:

### Step 1:
Desing your website for calculation using wireframe work.

### Step 2:
Then to execute the wireframe work desing use html,css

### Step 3:
Use views.py to execute the coding in serverside.

### Step 4:
Mention the path of the website in urls.py.

### Step 5:
Publish the website in the given URL



## PROGRAM :
view.py
```
from django.shortcuts import render

def areacalculation(request):
    context ={}
    context['area']="0"
    context['l']="0"
    context['b']="0"
    if request.method == 'POST':
        l= request.POST.get('length','0')
        b=request.POST.get('breadth','0')
        area=int(l)*int(b)
        context['area']=area
        context['l']=l
        context['b']=b
    return render(request,'mathapp/area.html',context)
```
Area.html
```
<!DOCTYPE html>
<html>
<head>
    <meta charset='utf-8'>
    <meta http-equiv='X-UA-Compatible' content='IE=edge'>
    <title>Page Title</title>
    <meta name='viewport' content='width=device-width, initial-scale=1'>
    
</head>
<style>
    body {
  background-color: lightskyblue;
}
    .container{
    width: 1080px;
    height: 440px;
    margin-top: 100px;
    margin-left: auto;
    margin-right: auto;
    border-width: 2px 2px 2px 2px;
    border-style: solid;
    box-shadow: 15px 15px 8px lightsteelblue;
    
}
    .heading{
        text-align: center;
    }
    .element{
        padding-top: 20px;
        padding-bottom: 20px;
        padding-left: 20px;
        padding-right:20px;
        text-align: center;
        font-size: 20px;
        background-color:lightpink;
        
    }
    .footer{
        display: block;
        width: 100%;
        height: 35px;
        background-color: violet;
        color: black;
        text-align: center;
        padding-top: 7px;
        font-size: large;
        
        }
</style>

<body>
     
    <div class="container">
        <div class="element", backgroung color="white">
        <h1  class="heading">AREA OF A RECTANGLE</h1>
        </div>
        <form method="POST">
            {% csrf_token %}
            <div class="element"> 
                Length=<input type="text" name="length" value={{length}}></input><br/>
            </div>
            <div class="element">
                Breadth=<input type="text" name="breadth" value={{breath}}></input><br/>
            </div>
            <div class="element">
                <input type="submit" value="AREA OF RECTANGLE"></input><br/>
            </div>
            <div class="element">
                Area=<input type="text" name="area" value={{area}}></input>
            </div>
            <div class="footer">
                    Developed by PAVIZHI.B
            </div>
        </form>
    </div>
    
</body>
</html>
```
url.py
```
"""calculations URL Configuration

The `urlpatterns` list routes URLs to views. For more information please see:
    https://docs.djangoproject.com/en/3.1/topics/http/urls/
Examples:
Function views

    1. Add an import:  from my_app import views
    2. Add a URL to urlpatterns:  path('', views.home, name='home')

Class-based views

    1. Add an import:  from other_app.views import Home
    2. Add a URL to urlpatterns:  path('', Home.as_view(), name='home')

Including another URLconf

    1. Import the include() function: from django.urls import include, path
    2. Add a URL to urlpatterns:  path('blog/', include('blog.urls'))
"""
from django.contrib import admin
from django.urls import path
from mathapp import views

urlpatterns = [
    path('admin/', admin.site.urls),
    path('areaofrectaanglr/',views.areacalculation,name="areaofrectangle"),
    path('',views.areacalculation,name="areaofrectangleroot")
]
```

## OUTPUT:
![output](./output.png)



## Result:
A website to perform mathematical calculations in server side is created.

