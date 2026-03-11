# Ex.04 Design a Website for Server Side Processing
## Date:10.03.26

## AIM:
To create a web page to calculate total bill amount with GST from price and GST percentage using server-side scripts.

## FORMULA:
Bill = P + (P * GST / 100)
<br> P --> Price (in Rupees)
<br> GST --> GST (in Percentage)
<br> Bill --> Total Bill Amount (in Rupees)

## DESIGN STEPS:

### Step 1:
Clone the repository from GitHub.

### Step 2:
Create Django Admin project.

### Step 3:
Create a New App under the Django Admin project.

### Step 4:
Create a HTML file to implement form based input and output.

### Step 5:
Create python programs for views and urls to perform server side processing.

### Step 6:
Receive input values from the form using request.POST.get().

### Step 7:
Calculate the total bill amount (including GST).

### Step 8:
Display the calculated result in the server console.

### Step 9:
Render the result to the HTML template.

### Step 10:
Publish the website in Localhost.

## PROGRAM:
calculator
```
<!DOCTYPE html>
<html>
<head>
    <title>GST Calculator</title>
    <style>
        body{
            font-family: Arial;
            margin:40px;
        }
        input{
            margin:5px;
        }
        button{
            margin-top:10px;
        }
    </style>
</head>

<body>

<h2>GST Calculator</h2>

<label>Price :</label>
<input type="number" id="price"><br>

<label>GST (R in %):</label>
<input type="number" id="gst"><br>

<button onclick="calculateGST()">Calculate</button>

<h3>Result:</h3>
<p id="result">GST: 0</p>

<script>
function calculateGST(){

    let price = document.getElementById("price").value;
    let gst = document.getElementById("gst").value;

    let gstAmount = (price * gst) / 100;

    document.getElementById("result").innerHTML = "GST: " + gstAmount.toFixed(2);
}
</script>

</body>
</html>
```
views.py
```
from django.shortcuts import render

def rectarea(request):
    context = {}
    context['area'] = "0"
    context['l'] = "0"
    context['b'] = "0"

    if request.method == 'POST':
        print("POST method is used")

        l = request.POST.get('length', '0')
        b = request.POST.get('breadth', '0')

        print(request, request)
        print('Length=', l)
        print('Breadth=', b)

        area = int(l) * int(b)

        context['area'] = area
        context['l'] = l
        context['b'] = b

        print('Area=', area)

    return render(request, 'mathapp/math.html', context)
```
URLS.PY:
```
    from django.contrib import admin
from django.urls import path
from mathapp import views

urlpatterns = [
    path('admin/', admin.site.urls),
    path('areofrectangle/', views.rectarea, name='areaofrectangle'),
    path('', views.rectarea, name='areaofrectangleroot')
]
```





## OUTPUT - SERVER SIDE:
![alt text](<Screenshot (531).png>)



## OUTPUT - WEBPAGE:
![alt text](<Screenshot (529).png>)



## RESULT:
The a web page to calculate total bill amount with GST from price and GST percentage using server-side scripts is created successfully.
