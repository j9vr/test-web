<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Test Web</title>

    <style>
        /* RESET */
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
            scroll-behavior: smooth;
        }

        body {
            font-family: Arial, sans-serif;
            background: #0d0d0d;
            color: #e6e6e6;
        }

        /* HEADER */
        header {
            background: #111;
            padding: 25px;
            text-align: center;
            box-shadow: 0 0 15px #00ffee;
        }

        header h1 {
            color: #00ffee;
            text-shadow: 0 0 12px #00ffee;
            font-size: 42px;
        }

        /* NAVIGATION */
        nav {
            background: #141414;
            padding: 15px 0;
            text-align: center;
        }

        nav a {
            color: #00ffee;
            font-weight: bold;
            text-decoration: none;
            margin: 0 15px;
            padding: 8px 15px;
            border-radius: 6px;
            transition: 0.3s;
        }

        nav a:hover {
            background: #00ffee;
            color: #000;
            box-shadow: 0 0 10px #00ffee;
        }

        /* SECTIONS */
        section {
            padding: 60px 20px;
            text-align: center;
        }

        h2 {
            font-size: 32px;
            margin-bottom: 15px;
            color: #00ffee;
            text-shadow: 0 0 10px #00ffee;
        }

        p {
            font-size: 18px;
            max-width: 700px;
            margin: 0 auto;
            color: #ccc;
        }

        /* BUTTON */
        .btn {
            display: inline-block;
            margin-top: 25px;
            padding: 12px 25px;
            background: #00ffee;
            color: #000;
            border-radius: 8px;
            text-decoration: none;
            font-weight: bold;
            box-shadow: 0 0 10px #00ffee;
            transition: 0.3s;
        }

        .btn:hover {
            background: #00c4b8;
            transform: scale(1.06);
            box-shadow: 0 0 20px #00ffee;
        }

        /* FOOTER */
        footer {
            background: #111;
            text-align: center;
            padding: 20px;
            color: #777;
            margin-top: 30px;
            font-size: 14px;
        }
    </style>
</head>

<body>

    <!-- HEADER -->
    <header>
        <h1>Welcome to Test Web</h1>
        <p>A simple website hosted on GitHub Pages</p>
    </header>

    <!-- NAVIGATION -->
    <nav>
        <a href="#home">Home</a>
        <a href="#about">About</a>
        <a href="#contact">Contact</a>
    </nav>

    <!-- HOME SECTION -->
    <section id="home">
        <h2>Home</h2>
        <p>This is a clean, modern website created using HTML and hosted for free on GitHub Pages.</p>
        <a class="btn" href="#about">Learn More</a>
    </section>

    <!-- ABOUT SECTION -->
    <section id="about">
        <h2>About</h2>
        <p>You can fully customize this website.  
           Change colors, add pages, insert images, or build anything you want.</p>
        <p>GitHub Pages makes publishing websites super easy — just update your code and push.</p>
    </section>

    <!-- CONTACT SECTION -->
    <section id="contact">
        <h2>Contact</h2>
        <p>If you want more pages or advanced features, I can generate more code for you.</p>
        <a class="btn" href="#home">Back to Top</a>
    </section>

    <!-- FOOTER -->
    <footer>
        © 2026 • Test Web • GitHub Pages
    </footer>

</body>
</html>
