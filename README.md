# Static Website Hosting with Apache
# By VANSH BAGRA from National Institute of Technology Silchar for GCGC Scholar ID: 2412139

## Part 1: Local Development Setup

### Step 1: Creating a Project Directory
Open up the terminal and create a new directory for my static website:
```bash
mkdir myStaticWebsite
cd myStaticWebsite
```

### Step 2: Created Website Files
Created the HTML and CSS files for my static website:
```bash
touch interesting-facts.html
touch interesting-facts.css
```

### Step 3: Add Content to my Files
Edited the HTML file with webstorm:

Add the following content:
```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>The Aurora Borealis</title>
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <link rel="stylesheet" href="interesting-facts.css">
</head>
<body>
<div class="container">
    <h1>Aurora Borealis</h1>
    <img class="fact-image" src="https://images.unsplash.com/photo-1506744038136-46273834b3fb?auto=format&fit=crop&w=800&q=80" alt="Aurora Borealis">
    <p>
        The <strong>Aurora Borealis</strong>, also known as the Northern Lights, is a natural light display predominantly seen in high-latitude regions around the Arctic. This mesmerizing phenomenon occurs when charged particles from the sun collide with gases in Earth's atmosphere, producing vibrant colors that dance across the night sky.
    </p>
    <p>
        The colors of the aurora depend on the type of gas involved and the altitude of the collisions. Green is the most common color, caused by oxygen molecules about 60 miles above the earth. Red, blue, and purple hues can also appear, creating a breathtaking spectacle.
    </p>
    <div class="source">
        Source: <a href="https://www.northernlightscentre.ca/northernlights.html" target="_blank">northernlightscentre.ca</a>
    </div>
</div>
</body>
</html>
```

Edited the CSS file:

Add styling:
```css
:root {
    --primary-bg: #1b2b34;
    --secondary-bg: #343d46;
    --accent: #6699cc;
    --text-main: #c0c5ce;
    --text-light: #d8dee9;
    --card-bg: #232f34;
    --shadow: 0 8px 32px 0 rgba(31, 38, 135, 0.25);
}
body {
    background: linear-gradient(135deg, var(--primary-bg) 60%, var(--accent) 100%);
    color: var(--text-main);
    font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
    margin: 0;
    padding: 0;
    min-height: 100vh;
}
.container {
    max-width: 600px;
    margin: 40px auto;
    background: var(--card-bg);
    border-radius: 18px;
    box-shadow: var(--shadow);
    padding: 32px 28px;
    transition: box-shadow 0.2s;
}
h1 {
    text-align: center;
    font-size: 2.3em;
    margin-bottom: 0.6em;
    letter-spacing: 2px;
    color: var(--accent);
    font-weight: 600;
}
.fact-image {
    display: block;
    margin: 0 auto 24px auto;
    border-radius: 14px;
    width: 100%;
    max-width: 400px;
    box-shadow: 0 4px 16px rgba(0,0,0,0.5);
}
p {
    font-size: 1.13em;
    line-height: 1.7;
    color: var(--text-light);
}
.source {
    margin-top: 24px;
    font-size: 0.97em;
    color: var(--accent);
    text-align: center;
}
a {
    color: var(--accent);
    text-decoration: underline;
}
@media (max-width: 700px) {
    .container {
        max-width: 100vw;
        padding: 1rem;
    }
    h1 {
        font-size: 2em;
    }
}
@media (max-width: 480px) {
    .container {
        padding: 1rem;
    }
    h1 {
        font-size: 1.4em;
    }
    .fact-image {
        max-width: 100%;
    }
}   
```

## Part 2: Version Control Setup

### Step 4: Initialize Git Repository
```bash
git init
git add .
git commit -m "Initial commit: Add HTML and CSS files"
```

### Step 5: Push to GitHub
Created a new repository on GitHub, then:
```bash
git remote add origin https://github.com/bagraVansh/interesting-facts.git
git branch -M main
git push -u origin main
```

## Part 3: Cloud Server Setup

### Step 6: Created and Configured Azure VM
1. Log into Microsoft Azure Portal
2. Created a new Virtual Machine (Ubuntu 20.04 LTS)
3. Configure networking to allow HTTP (port 80) and SSH (port 22) traffic

### Step 7: Connect to Your Server
Connected via SSH using my VM's public IP:
```bash
ssh username@your-server-ip
```

### Step 8: Update System and Install Apache
Update the package list and install Apache:
```bash
sudo apt update
sudo apt upgrade -y
sudo apt install apache2 -y
```

### Step 9: Start and Enable Apache
```bash
sudo systemctl start apache2
sudo systemctl enable apache2
```

Verify Apache is running:
```bash
sudo systemctl status apache2
```

## Part 4: Deployed my Website

### Step 10: Cloned my Repository
```bash
git clone https://github.com/bagraVansh/interesting-facts.git ~/myWebsite
```

### Step 11: Move Files to Web Directory
```bash
sudo mv ~/myWebsite /var/www/
```

### Step 12: Set Proper Permissions
```bash
sudo chown -R user:user /var/www/myWebsite
sudo chmod -R 755 /var/www/myWebsite
```

### Step 13: Configured Apache Virtual Host
Edited the default Apache configuration:
```bash
sudo nano /etc/apache2/sites-available/000-default.conf
```

Modified the DocumentRoot line:
```apache
DocumentRoot /var/www/myWebsite
```

### Step 14: Test Configuration and Reload Apache
Tested the configuration for syntax errors:
```bash
sudo apache2ctl configtest
```

The test passed, reloaded Apache:
```bash
sudo systemctl reload apache2
```

## Part 5: Verification and Testing

### Step 15: Testing My Website
1. Open up a web browser
2. Navigate to the URL address: `http://135.235.136.8`


### Step 16: Checking Apache Status
```bash
sudo systemctl status apache2
```

## Conclusion
The website is now live and accessible via the URL address: http://135.235.136.8
