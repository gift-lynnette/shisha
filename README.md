
<!DOCTYPE HTML>
<html>
<head>
    <title>Responsive Menu Cards with Header and Footer</title>
    <meta name="viewport" content="width=device-width, initial-scale=1">
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.4.0/css/all.min.css">
    <style>
        /* Reset and Global Styles */
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
        }

        body {
            font-family: 'Arial', sans-serif;
            line-height: 1.6;
            color: #333;
            background-color: #000000; /* Changed body color to match card background */
            /* Added padding-top to account for the fixed header height */
            padding-top: 65px; 
        }
        body {
            opacity: 0;
            transform: translateY(100px);
            transition: all 0.8s ease;
        }

        body.loaded {
            opacity: 1;
            transform: translateY(0);
        }
        header {
            position: fixed;
            top: 0;
            left: 0;
            right: 0;
            background: rgba(0, 0, 0, 0.95);
            backdrop-filter: blur(10px);
            z-index: 1000;
            padding: 0.5rem 0;
            transition: all 0.3s ease;
        }

        .header-container {
            max-width: 1200px;
            margin: 0 auto;
            display: flex;
            justify-content: space-between;
            align-items: center;
            padding: 0 2rem;
        }

        .logo img {
            height: 50px;
            width: auto;
        }

        .nav ul {
            display: flex;
            list-style: none;
            gap: 2rem;
        }

        .nav a {
            color: white;
            text-decoration: none;
            font-weight: 500;
            transition: color 0.3s ease;
            position: relative;
        }

        .nav a:hover {
            color: #f89a20;
        }

        .nav a::after {
            content: '';
            position: absolute;
            bottom: -5px;
            left: 0;
            width: 0;
            height: 2px;
            background: #f89a20;
            transition: width 0.3s ease;
        }

        .nav a:hover::after {
            width: 100%;
        }

        .book-now a {
            background: linear-gradient(45deg, #f89a20, #ff6b35);
            color: white;
            padding: 0.8rem 1.5rem;
            border-radius: 25px;
            text-decoration: none;
            font-weight: 600;
            transition: all 0.3s ease;
            box-shadow: 0 4px 15px rgba(248, 154, 32, 0.3);
        }

        .book-now a:hover {
            transform: translateY(-2px);
            box-shadow: 0 6px 20px rgba(248, 154, 32, 0.5);
        }

        .bar {
            display: none; /* Hidden by default on desktop */
            color: white;
            font-size: 1.5rem;
            cursor: pointer;
        }
        /* /* ----------- MENU HEADER IMAGE STYLES --------  */
        .menu-hero {
            width: 100%;
            height: 350px; /* Reduced height to fit better above the cards */
            background-image: url('images/1.jpg'); /* Use a nice food/menu image */
            background-size: cover;
            background-position: center;
            display: flex;
            justify-content: center;
            align-items: center;
            text-align: center;
            position: relative;
            margin-bottom: 40px; /* Space between hero and cards */
            box-shadow: 0 5px 15px rgba(0, 0, 0, 0.1);
        }

        .menu-hero::before {
            content: '';
            position: absolute;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            background: rgba(0, 0, 0, 0.4); /* Dark overlay */
        }

        .menu-caption {
            z-index: 10;
            color: white;
            font-size: 3.5rem;
            font-weight: bold;
            text-shadow: 0 3px 6px rgba(0, 0, 0, 0.7);
        }
        
        @media (max-width: 768px) {
            .menu-hero {
                height: 250px;
            }
            .menu-caption {
                font-size: 2.5rem;
            }
        }
        
            
        .first {
            text-align: center;
            margin-bottom: 0px;
            color:  #f89a20;
        }
        
        .first h1 {
            font-size: 2.8rem;
            margin-bottom: 10px;
            font-weight: 700;
        }
        
        .first p {
            font-size: 1.2rem;
            max-width: 600px;
            margin: 0 auto;
            color:  #f89a20;
        }
        
        /* ----------- CARD STYLES -------- */
        .main-content {
            padding: 20px 0; /* Add vertical padding around the cards */
            margin-bottom: 150px; 
            
        }
        
        .container {
            display: flex;
            flex-wrap: wrap;
            gap: 20px; 
            justify-content: center;
            align-items: center;
            max-width: 1200px;
            width: 100%;
            margin: 0 auto;
            padding: 0 20px;
        }

        .container .card {
            position: relative;
            cursor: pointer;
            width: 90%; 
            max-width: 300px; 
            height: 200px;
        }
        
        .container .card .slide.slide1 {
            position: relative;
            display: flex;
            justify-content: center;
            align-items: center;
            z-index: 1;
            transition: 0.7s cubic-bezier(0.25, 0.46, 0.45, 0.94);
            transform: translateY(100px);
            
            /* Background Image Setup */
            background-size: cover;
            background-position: center;
            background-repeat: no-repeat;
            border-radius:15px;
            overflow: hidden; 
            box-shadow: inset 0 0 0 1000px rgba(0, 0, 0, 0.3); 
        }
        
        /* Individual Background Image URLs */
        .card.breakfast .slide.slide1 {
            background-image: url('images/food.png');
            width: 300px;
            /* height: 50px; */
        }
        .card.dinner .slide.slide1 {
            background-image: url('images/dinner.png');
            width: 300px;
        }
        .card.drinks .slide.slide1 {
            background-image: url('images/drinks.png');
        }
        .card.shisha .slide.slide1 {
            background-image: url('images/food.png');
            width: 300px;
        }
        
        .container .card:hover .slide.slide1 {
            transform: translateY(0px);
            box-shadow: none; 
            
        }
        .slide1 .card-title {
            color: #fff;
            font-size: 1.5rem;
            font-weight: bold;
            text-transform: uppercase;
            letter-spacing: 1px;
            text-shadow: 0 2px 4px rgba(0, 0, 0, 0.8); 
        }

        .container .card .icon, 
        .container .card .icon img {
            display: none; 
        }
        
        .container .card .slide {
            width: 100%;
            height: 100%;
            transition: 0.5s cubic-bezier(0.25, 0.46, 0.45, 0.94);
            border-radius: 15px;
            overflow: hidden;
        }
      
        
        .container .card .slide.slide2 {
            position: relative;
            display: flex;
            flex-direction: column; 
            justify-content: space-between; 
            align-items: center;
            padding: 20px;
            box-sizing: border-box;
            transition: 0.8s cubic-bezier(0.25, 0.46, 0.45, 0.94);
            transform: translateY(-100px);
            box-shadow: 0 20px 40px rgba(0, 0, 0, 0.1);
            /* background: white; */
            border-radius: 0px 0px 15px 15px;
        }

        .container .card:hover .slide.slide2 {
            transform: translateY(0);
            margin-bottom: 200px;
            z-index: 3;
        }
        
        .slide2 .content-text {
            display: flex;
            flex-direction: column;
            align-items: center;
            text-align: center;
            margin-bottom: 10px; 
        }
        
        .container .card .slide.slide2 .content p {
            margin: 0;
            padding: 0;
            color:#fff ;
            font-size: 16px;
            line-height: 1.5;
        }

        .container .card .slide.slide2 .content h3 {
            margin: 0 0 5px 0; 
            padding: 0;
            font-size: 24px;
            color: #f89a20;
            font-weight: bold;
        }

        .btn {
            background:linear-gradient(45deg,#f89a20,#ff6b35);
            color:#fff;
            border:none;
            padding:8px 18px; 
            border-radius:25px;
            font-size:0.8rem; 
            font-weight:bold;
            cursor:pointer;
            text-transform:uppercase;
            transition:all 0.3s;
            display:block; 
            margin-top: auto; 
            width:fit-content;
            text-decoration: none; 
            transition: all 0.3s ease;

            
        }

        .read-more-btn:hover{
            transform:scale(1.05);
            box-shadow:0 5px 15px rgba(248,154,32,0.4);
        }
        
        /* --- 2 Up / 2 Down Responsiveness --- */
        @media (min-width: 600px) {
            .container {
                gap: 40px; 
            }
            .container .card {
                flex-basis: calc(50% - 20px); 
                max-width: 400px; 
            }
        }
        
       
        .footer {
            background: linear-gradient(135deg, #1a1a1a, #000);
            padding: 3rem 0 1rem;
            margin-top: 40px; /* Space above footer */
        }

        .footer-container {
            max-width: 1200px;
            margin: 0 auto;
            padding: 0 2rem;
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(250px, 1fr));
            gap: 2rem;
        }

        .footer-left h3,
        .footer-links h3,
        .footer-social h3 {
            color: #f89a20;
            margin-bottom: 1rem;
        }

        .footer-left p,
        .footer-links a {
            color: #ccc;
            text-decoration: none;
            transition: color 0.3s ease;
        }

        .footer-links a:hover {
            color: #f89a20;
        }

        .footer-links ul {
            list-style: none;
        }

        .footer-links li {
            margin-bottom: 0.5rem;
        }

        .footer-logo {
            height: 40px;
            margin-bottom: 1rem;
        }

        .social-icons {
            display: flex;
            gap: 1rem;
        }

        .social-icons a {
            color: #ccc;
            font-size: 1.5rem;
            transition: all 0.3s ease;
        }

        .social-icons a:hover {
            color: #f89a20;
            transform: translateY(-3px);
        }

        .footer-bottom {
            text-align: center;
            padding-top: 2rem;
            margin-top: 2rem;
            border-top: 1px solid #333;
            color: #ccc;
        }

    
        /* ----------- RESPONSIVE MEDIA QUERIES -------- */
        @media (max-width: 768px) {
            /* Header Responsive Styles */
            .bar {
                display: block; /* Show hamburger icon */
            }
            
            .nav {
                display: none; /* Hide nav by default on mobile */
                position: absolute;
                top: 100%;
                left: 0;
                right: 0;
                background: rgba(0, 0, 0, 0.98);
                padding: 1rem 0;
                backdrop-filter: blur(10px);
                animation: slideDown 0.3s ease;
            }
            
            .nav.active {
                display: block; /* Show nav when 'active' class is added by JS */
            }
            
            .nav ul {
                flex-direction: column;
                gap: 1.5rem;
                padding: 0 2rem;
            }
            
            .nav li {
                text-align: center;
            }

            /* Footer Responsive Styles */
            .footer-container {
                grid-template-columns: 1fr;
                text-align: center;
                gap: 2rem;
            }
            
            .social-icons {
                justify-content: center;
            }
        }

        @media (max-width: 480px) {
            .header-container {
                padding: 0 1rem;
            }
            .footer-container {
                padding: 0 1rem;
            }
            /* Adjustments for card text on smaller screens */
            .container .card .slide.slide2 .content h3 {
                font-size: 20px;
            }
            .container .card .slide.slide2 .content p {
                font-size: 14px;
            }
        }

        /* Navigation slide animation for mobile menu */
        @keyframes slideDown {
            from {
                opacity: 0;
                transform: translateY(-10px);
            }
            to {
                opacity: 1;
                transform: translateY(0);
            }
        }
    </style>
</head>
<body>

<header>
    <div class="header-container">
        <div class="logo">
            <img src="images/Logo orange.png" alt="Logo">
        </div>

        <nav class="nav" id="navMenu">
            <ul>
                <li><a href="home.html">Home</a></li>
                <li><a href="menu.html">Menu</a></li>
                <li><a href="about.html">About Us</a></li>
                <li><a href="gallery.html">Gallery</a></li>
                <li><a href="contact.html">Contacts</a></li>
            </ul>
        </nav>

        <div class="book-now">
            <a href="https://www.opentable.co.uk/r/berwick-manor-lounge-reservations-rainham?restref=444399&lang=en-GB&ot_source=Restaurant%20website">Book Now</a>
        </div>

        <i class="fa-solid fa-bars bar" id="hamburger"></i>
    </div>
</header>
<div class="menu-hero">
    <h1 class="menu-caption">Our Menu</h1>
</div>
<div class="main-content">
    <div class="first">
        <h1>Our Dining and Shisha Menu</h1>
        <p>Discover our delicious offerings prepared with the freshest ingredients</p>
    </div>
    <div class="container">
        <div class="card breakfast">
            <div class="slide slide1">
                <div class="content">
                    <span class="card-title">Breakfast Menu</span>
                </div>
            </div>
            <div class="slide slide2">
                <div class="content">
                    <div class="content-text">
                        <h3>Breakfast Menu</h3>
                        <p>Start your day with our delicious breakfast options, from fluffy pancakes to savory omelets.</p>
                    </div>
                  <div class="more">
                      <a href="breakfast.html" class="btn">Read More</a>
                  </div>
                </div>
            </div>
        </div>

        <div class="card dinner">
            <div class="slide slide1">
                <div class="content">
                    <span class="card-title">Dinner Special</span>
                </div>
            </div>
            <div class="slide slide2">
                <div class="content">
                    <div class="content-text">
                        <h3>Dinner Special</h3>
                        <p>Experience fine dining with our premium menu featuring seasonal ingredients and chef specialties.</p>
                    </div>
                     <div class="more">
                      <a href="dinner.html" class="btn">Read More</a>
                  </div>
                </div>
            </div>
        </div>

        <div class="card drinks">
            <div class="slide slide1">
                <div class="content">
                    <span class="card-title">Premium Drinks</span>
                </div>
            </div>
            <div class="slide slide2">
                <div class="content">
                    <div class="content-text">
                        <h3>Premium Drinks</h3>
                        <p>Handcrafted beverages, specialty cocktails, and a curated selection of fine wines and spirits.</p>
                    </div>
                     <div class="more">
                      <a href="drinks.html" class="btn">Read More</a>
                  </div>
                </div>
            </div>
        </div>

        <div class="card shisha">
            <div class="slide slide1">
                <div class="content">
                    <span class="card-title">Shisha Lounge</span>
                </div>
            </div>
            <div class="slide slide2">
                <div class="content">
                    <div class="content-text">
                        <h3>Shisha Lounge</h3>
                        <p>Relax in our premium shisha lounge experience with a variety of classic and exotic flavors.</p>
                    </div>
                     <div class="more">
                      <a href="shisha.html" class="btn">Read More</a>
                  </div>
                </div>
            </div>
        </div>
    </div>
</div>
<footer class="footer">
    <div class="footer-container">
        <div class="footer-left">
            <img src="images/Logo orange.png" alt="Footer Logo" class="footer-logo">
            <h3>Berwick Manor</h3>
            <p>
                Experience dining and shisha in a luxurious and unforgettable setting.
            </p>
        </div>

        <div class="footer-links">
            <h3>Quick Links</h3>
            <ul>
                <li><a href="#">Home</a></li>
                <li><a href="#">Menu</a></li>
                <li><a href="#">About</a></li>
                <li><a href="#">Contact</a></li>
            </ul>
        </div>

        <div class="footer-social">
            <h3>Follow Us</h3>
            <div class="social-icons">
                <a href="#"><i class="fab fa-facebook-f"></i></a>
                <a href="#"><i class="fab fa-instagram"></i></a>
                <a href="#"><i class="fab fa-twitter"></i></a>
            </div>
        </div>
    </div>

    <div class="footer-bottom">
        &copy; 2025 Berwick Manor. All Rights Reserved.
    </div>
</footer>
<script>
    // Mobile menu toggle functionality
    const hamburger = document.getElementById('hamburger');
    const navMenu = document.getElementById('navMenu');

    hamburger.addEventListener('click', () => {
        navMenu.classList.toggle('active');
    });
        // Trigger animation when page loads
    window.addEventListener('load', function() {
        document.body.classList.add('loaded');
    });

    // Header background change on scroll functionality
    window.addEventListener('scroll', () => {
        const header = document.querySelector('header');
        if (window.scrollY > 100) {
            header.style.background = 'rgba(0, 0, 0, 0.98)';
        } else {
            header.style.background = 'rgba(0, 0, 0, 0.95)';
        }
    });

    // Dummy modal function for buttons
    function openModal(item) {
        console.log("Opening modal for: " + item);
        alert("Open modal for: " + item);
    }
</script>
</body>
</html>
