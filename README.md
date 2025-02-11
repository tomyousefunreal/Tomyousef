<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Portfolio - Yousef</title>
    <link rel="stylesheet" href="styles.css">
    <style>
        body {
            margin: 0;
            font-family: Arial, sans-serif;
            background: linear-gradient(135deg, #1e1e2f, #2a2a3c);
            color: white;
            text-align: center;
            scroll-behavior: smooth;
        }
        header {
            padding: 20px;
            background: rgba(0, 0, 0, 0.5);
            position: fixed;
            width: 100%;
            top: 0;
            left: 0;
            z-index: 100;
        }
        nav {
            display: flex;
            justify-content: space-between;
            align-items: center;
            padding: 0 50px;
        }
        .logo {
            font-size: 24px;
            font-weight: bold;
            color: #4CAF50;
        }
        nav ul {
            list-style: none;
            display: flex;
            gap: 20px;
        }
        nav ul li a {
            color: white;
            text-decoration: none;
            font-size: 18px;
            transition: 0.3s;
        }
        nav ul li a:hover {
            color: #4CAF50;
        }
        .hero {
            display: flex;
            flex-direction: column;
            align-items: center;
            justify-content: center;
            height: 100vh;
            text-align: center;
            padding: 50px;
            gap: 20px;
        }
        .hero-content {
            max-width: 500px;
            animation: fadeIn 1.5s ease-in-out;
        }
        .hero h1 {
            font-size: 48px;
            background: linear-gradient(90deg, #ff00ff, #00ffff);
            -webkit-background-clip: text;
            -webkit-text-fill-color: transparent;
            animation: colorChange 3s infinite alternate;
        }
        .hero h2 {
            font-size: 24px;
            animation: fadeIn 2s ease-in-out;
        }
        .btn {
            display: inline-block;
            padding: 10px 20px;
            background: #4CAF50;
            color: white;
            text-decoration: none;
            font-size: 18px;
            border-radius: 5px;
            transition: 0.3s;
        }
        .btn:hover {
            background: #388E3C;
        }
        .animated-section {
            font-size: 36px;
            font-weight: bold;
            animation: fadeIn 1.5s ease-in-out, moveUp 2s ease-in-out infinite alternate;
        }
        @keyframes fadeIn {
            from { opacity: 0; transform: translateY(20px); }
            to { opacity: 1; transform: translateY(0); }
        }
        @keyframes moveUp {
            0% { transform: translateY(0); }
            100% { transform: translateY(-10px); }
        }
        img {
            width: 250px;
            border-radius: 50%;
        }
        .project-images img {
            width: 150px;
            margin: 10px;
            border-radius: 10px;
        }
    </style>
</head>
<body>
    <header>
        <nav>
            <div class="logo">Yousef</div>
            <ul>
                <li><a href="#about">About</a></li>
                <li><a href="#services">Services</a></li>
                <li><a href="#projects">Projects</a></li>
                <li><a href="#whyme">Why Me</a></li>
                <li><a href="#contact">Contact</a></li>
            </ul>
        </nav>
    </header>
    
    <section class="hero">
        <img src="me.jpg" alt="Yousef" style="width: 300px;">
        <div class="hero-content">
            <h1>Hello, I'm Yousef</h1>
            <h2>Game Developer & AI Enthusiast</h2>
            <p>Creating immersive experiences with Unreal Engine & AI.</p>
            <a href="#projects" class="btn">View My Work</a>
        </div>
    </section>
    
    <section id="about" class="animated-section">
        <h2>About Me</h2>
        <p>Passionate about game development and AI, delivering high-quality experiences with expertise in Unreal Engine.</p>
    </section>
    
    <section id="services" class="animated-section">
        <h2>Services</h2>
        <p>Offering Unreal Engine development, AI integration, and game design services.</p>
    </section>
    
    <section id="projects" class="animated-section">
        <h2>Projects</h2>
        <div class="project-images">
            <img src="image1 (3).png" alt="Project 3">
            <img src="image1 (4).png" alt="Project 4">
            <img src="image1 (5).png" alt="Project 5">
            <img src="image1 (6).png" alt="Project 6">
            <img src="image1 (7).png" alt="Project 7">
            <img src="image1 (8).png" alt="Project 8">
            <img src="image1 (9).png" alt="Project 9">
            <img src="image1 (10).png" alt="Project 10">
            <img src="image1 (11).png" alt="Project 11">
            <img src="image1 (12).png" alt="Project 12">
        </div>
    </section>

    <section id="whyme" class="animated-section">
        <h2>Why Me?</h2>
        <p>With years of experience and passion for innovation, I ensure top-tier game and AI solutions.</p>
    </section>

    <section id="contact" class="animated-section">
        <h2>Contact Me</h2>
        <p>Email: yousefunreal@gmail.com</p>
        <p>Phone: 01019646537</p>
    </section>
</body>
</html>
