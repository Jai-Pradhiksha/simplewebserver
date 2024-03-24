# EX01 Developing a Simple Webserver
## Date: 24.03.2024

## AIM:
To develop a simple webserver to serve html pages.

## DESIGN STEPS:
### Step 1: 
HTML content creation.

### Step 2:
Design of webserver workflow.

### Step 3:
Implementation using Python code.

### Step 4:
Serving the HTML pages.

### Step 5:
Testing the webserver.

## PROGRAM:
'''
from http.server import HTTPServer, BaseHTTPRequestHandler
content = """
<!DOCTYPE html>
<html lang="en">

<head>
    {% load static %}
    <meta charset="UTF-8">
    <meta http-equiv="X-UA-Compatible" content="IE=edge">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">

    <link rel="stylesheet" href="https://cdn.jsdelivr.net/npm/bootstrap-icons@1.11.3/font/bootstrap-icons.min.css">
    <link href="https://cdn.jsdelivr.net/npm/bootstrap@5.3.3/dist/css/bootstrap.min.css" rel="stylesheet"
        integrity="sha384-QWTKZyjpPEjISv5WaRU9OFeRpok6YctnYmDr5pNlyT2bRjXh0JMhjY6hW+ALEwIH" crossorigin="anonymous">
    <link rel="icon"
        href="https://in.images.search.yahoo.com/images/view;_ylt=Awrx_fBXs_5lyoYMdja9HAx.;_ylu=c2VjA3NyBHNsawNpbWcEb2lkAzc5ZWJkMDIzYjc1YTVjZjA3YTY0Y2VhYTE0M2I4YmVkBGdwb3MDMTUEaXQDYmluZw--?back=https%3A%2F%2Fin.images.search.yahoo.com%2Fsearch%2Fimages%3Fp%3Dwonderla%2Blogo%26type%3DE211IN714G0%26fr%3Dmcafee%26fr2%3Dpiv-web%26tab%3Dorganic%26ri%3D15&w=770&h=433&imgurl=static-news.moneycontrol.com%2Fstatic-mcnews%2F2017%2F05%2Fwonderla-new-1280-720-770x433.jpg&rurl=http%3A%2F%2Fwww.moneycontrol.com%2Fnews%2Fbusiness%2Fearnings-business%2Fwonderla-holidays-happy-with-revenue-growth-2288983.html&size=35.2KB&p=wonderla+logo&oid=79ebd023b75a5cf07a64ceaa143b8bed&fr2=piv-web&fr=mcafee&tt=Wonderla+Holidays+happy+with+revenue+growth+-+Moneycontrol.com&b=0&ni=21&no=15&ts=&tab=organic&sigr=OIsg_eIa1pPO&sigb=7mEOZMlfPH5N&sigi=XF8flOzAN3NY&sigt=e2e5xmUlrXwq&.crumb=TZPNgIuenwF&fr=mcafee&fr2=piv-web&type=E211IN714G0"
        type="image/icon type">

    <title>Wonderla Homepage</title>
    <style>
        i {
            color: #f5b301;
            font-size: 20px;
            padding: 10px;
        }

        i:hover {
            color: white;
        }

        a {
            text-decoration: none;
            color: #f5b301;
            font-size: 15px;
            font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
            padding: 5px;
        }

        .px-wide {
            width: 300px;
        }
    </style>
</head>

<body>
    <div>
        <div class="row " style="background-color: #1E2328; margin:auto">
            <div class="col-1 ">
                <img src="{% static 'images/wonderlalogo.png' %}" alt="logo" style="width: 130px; margin:auto">
            </div>
            <div class="col-5 " style="margin: auto; text-align:center;">
                <a href="">Parks</a><i class="bi bi-three-dots-vertical"></i>
                <a href="">Resort</a><i class="bi bi-three-dots-vertical"></i>
                <a href="">Tickets</a><i class="bi bi-three-dots-vertical"></i>
                <a href="">Offers</a><i class="bi bi-three-dots-vertical"></i>
                <a href="">Quick Links</a><i class="bi bi-three-dots-vertical"></i>
                <a href="">Contact us</a>
            </div>

            <div class="col-3" style="margin: auto;">
                <a href=""><i class="bi bi-instagram"></i></a>
                <a href=""><i class="bi bi-twitter"></i></a>
                <a href=""><i class="bi bi-youtube"></i></a>
                <a href=""><i class="bi bi-facebook"></i></a>
                <a href=""><i class="bi bi-pinterest"></i></a>
                <a href=""><i class="bi bi-whatsapp"></i></a>

            </div>

            <div class="col-3">
                <div style="border: 2px solid; border-radius: 15px; margin:auto">
                    <i class="bi bi-search"></i>
                    <input type="text" placeholder="Search"
                        style="background-color: #f5b301; border: opx; outline: none;">
                </div>
            </div>
        </div>
    </div>
    <div id="carouselExampleIndicators" class="carousel slide" style="max-height: 562px;">
        <div class="carousel-indicators">
            <button type="button" data-bs-target="#carouselExampleIndicators" data-bs-slide-to="0" class="active"
                aria-current="true" aria-label="Slide 1"></button>
            <button type="button" data-bs-target="#carouselExampleIndicators" data-bs-slide-to="1"
                aria-label="Slide 2"></button>
            <button type="button" data-bs-target="#carouselExampleIndicators" data-bs-slide-to="2"
                aria-label="Slide 3"></button>
        </div>
        <div class="carousel-inner">
            <div class="carousel-item active">
                <img src="{% static 'images/image1.png'  %}" class="d-block w-100" alt="carousel1">
            </div>
            <div class="carousel-item">
                <img src="{% static 'images/image2.png' %}" class="d-block w-100" alt="carousel2">
            </div>
            <div class="carousel-item">
                <img src="{% static 'images/image3.png' %}" class="d-block w-100" alt="carousel3">
            </div>
        </div>
        <button class="carousel-control-prev" type="button" data-bs-target="#carouselExampleIndicators"
            data-bs-slide="prev">
            <span class="carousel-control-prev-icon" aria-hidden="true"></span>
            <span class="visually-hidden">Previous</span>
        </button>
        <button class="carousel-control-next" type="button" data-bs-target="#carouselExampleIndicators"
            data-bs-slide="next">
            <span class="carousel-control-next-icon" aria-hidden="true"></span>
            <span class="visually-hidden">Next</span>
        </button>
    </div>

    <div class="container-fluid">
        <div class="row justify-content-around" style="background-color: #f5b301;">
            <div class="row" style="margin-top: 50px;"></div>
            <div class="col-md-4">
                <div class="card mx-auto" style="width: 18rem;">
                    <img src="{% static 'images/image1.png' %}" class="card-img-top" alt="...">
                    <div class="card-body">
                        <p class="card-text">
                        <h4 style="text-align: center;">Wonderla <br>Kochi</h4>
                        </p>
                    </div>
                </div>
            </div>
            <div class="col-md-4">
                <div class="card mx-auto" style="width: 18rem;">
                    <img src="{% static 'images/image2.png' %}" class="card-img-top" alt="...">
                    <div class="card-body">
                        <p class="card-text">
                        <h4 style="text-align: center;">Wonderla <br> Bengaluru</h4>
                        </p>
                    </div>
                </div>
            </div>
            <div class="col-md-4">
                <div class="card mx-auto" style="width: 18rem;">
                    <img src="{% static 'images/image3.png' %}" class="card-img-top" alt="...">
                    <div class="card-body">
                        <p class="card-text">
                        <h4 style="text-align: center;">Wonderla <br> Hyderabad</h4>
                        </p>
                    </div>
                </div>
            </div>
        </div>
    </div>

    </div>

</body>

</html>
"""

class myhandler(BaseHTTPRequestHandler):
    def do_GET(self):
        print("request received")
        self.send_response(200)
        self.send_header('content-type', 'text/html; charset-utf-8' )
        self.end_headers()
        self.wfile.write(content.encode())
        
server_address = ('', 8000)
httpd = HTTPServer(server_address,myhandler)
print("my webserver is running...")
httpd.serve_forever()
'''
## OUTPUT:
![alt text](<Screenshot 2024-03-24 175605.png>)
![alt text](<Screenshot 2024-03-24 175658.png>)
![alt text](<Screenshot 2024-03-24 175711.png>)

## RESULT:
The program for implementing simple webserver is executed successfully.
