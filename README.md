# EX01 Developing a Simple Webserver

# Date:
02/12/2024
# AIM:
To develop a simple webserver to serve html pages and display the configuration details of laptop.

# DESIGN STEPS:
## Step 1:
HTML content creation.

## Step 2:
Design of webserver workflow.

## Step 3:
Implementation using Python code.

## Step 4:
Serving the HTML pages.

## Step 5:
Testing the webserver.

# PROGRAM:
from django.shortcuts import render,HttpResponse


# Create your views here.
def trial(request):
    return HttpResponse('<p>Hello</p>')
def htm(request):
    return render(request,"home.html")

~
content = '''
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Laptop Specifications</title>
  <link rel="stylesheet" href="styles.css">
</head>
<body>
  <div class="laptop-specs">
    <h1>Laptop Specifications</h1>
    <div class="spec">
      <h2>Processor</h2>
      <p>Intel Core i5 13th Gen</p>
    </div>
    <div class="spec">
      <h2>RAM</h2>
      <p>16GB DDR4</p>
    </div>
    <div class="spec">
      <h2>Storage</h2>
      <p>512GB SSD</p>
    </div>
    <div class="spec">
      <h2>Graphics</h2>
      <p>NVIDIA GTX 4050</p>
    </div>
    <div class="spec">
      <h2>Operating System</h2>
      <p>Windows 11</p>
    </div>
  </div>
  <style>
  /* General Reset */
body {
  margin: 0;
  font-family: Arial, sans-serif;
  background-color: #f4f4f9;
  color: #333;
}

/* Laptop Specs Container */
.laptop-specs {
  max-width: 600px;
  margin: 50px auto;
  padding: 20px;
  background: #ffffff;
  border-radius: 8px;
  box-shadow: 0 4px 6px rgba(0, 0, 0, 0.1);
}

/* Header Styles */
.laptop-specs h1 {
  text-align: center;
  font-size: 2rem;
  margin-bottom: 20px;
  color: #4CAF50;
}

/* Individual Specification Styles */
.spec {
  border-bottom: 1px solid #ddd;
  padding: 15px 0;
}

.spec:last-child {
  border-bottom: none;
}

.spec h2 {
  font-size: 1.2rem;
  color: #555;
}

.spec p {
  font-size: 1rem;
  margin: 5px 0 0;
  color: #333;
}
</style>
</body>
</html>


'''

from http.server import HTTPServer,BaseHTTPRequestHandler
class Myserver(BaseHTTPRequestHandler):
    def do_GET(self):
        print("Get request received...")
        self.send_response(200)
        self.send_header("content-type","text/html")
        self.end_headers()
        self.wfile.write(content.encode())

print("This is my webserver")
server_address = ('',8000)
httpd = HTTPServer(server_address,Myserver)
httpd.serve_forever()

~
# OUTPUT:

![Screenshot 2024-11-15 193920](https://github.com/user-attachments/assets/9d6dda27-c2bb-4486-b156-6899c6397dd4)
![Screenshot 2024-11-15 195523](https://github.com/user-attachments/assets/63683749-c9f3-4605-8d3d-2a0f76bd2a75)



# RESULT:
The program for implementing simple webserver is executed successfully.
