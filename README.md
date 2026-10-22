<details>
<summary>🎨 <strong>Click to view the 3D VIC Model Code</strong></summary>

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0, maximum-scale=1.0, user-scalable=no">
    <title>3D VIC Model</title>
    <style>
        body {
            margin: 0;
            padding: 0;
            background-color: #050510;
            display: flex;
            justify-content: center;
            align-items: center;
            min-height: 100vh;
            overflow: hidden;
        }
        #canvas-container {
            width: 100%;
            height: 100vh;
            display: flex;
            justify-content: center;
            align-items: center;
        }
    </style>
    <!-- Load Three.js from a reliable CDN -->
    <script src="https://cdnjs.cloudflare.com/ajax/libs/three.js/r128/three.min.js"></script>
</head>
<body>

    <div id="canvas-container"></div>

    <script>
        const container = document.getElementById('canvas-container');
        
        // 1. Scene setup
        const scene = new THREE.Scene();
        
        // 2. Camera setup
        const camera = new THREE.PerspectiveCamera(45, container.clientWidth / container.clientHeight, 0.1, 1000);
        camera.position.z = 12;

        // 3. Renderer setup
        const renderer = new THREE.WebGLRenderer({ alpha: true, antialias: true });
        renderer.setSize(container.clientWidth, container.clientHeight);
        renderer.setPixelRatio(window.devicePixelRatio);
        container.appendChild(renderer.domElement);

        // 4. Lighting
        const ambientLight = new THREE.AmbientLight(0xffffff, 0.8);
        scene.add(ambientLight);

        const pointLight1 = new THREE.PointLight(0x22d3ee, 2, 50); // Cyan glow
        pointLight1.position.set(10, 10, 10);
        scene.add(pointLight1);

        const pointLight2 = new THREE.PointLight(0xe879f9, 2, 50); // Pink/Magenta glow
        pointLight2.position.set(-10, -10, 10);
        scene.add(pointLight2);

        // 5. Create the Text using TubeGeometry (No external font files required)
        const group = new THREE.Group();

        // Material for the neon glass tube
        const material = new THREE.MeshPhysicalMaterial({
            color: 0x22d3ee,           
            emissive: 0x22d3ee,        
            emissiveIntensity: 1.5,    
            metalness: 0.2,            
            roughness: 0.1,            
            transmission: 0.9,         // Makes it glassy
            thickness: 0.5,            
            ior: 1.5,                  
            clearcoat: 1.0             
        });

        // Helper function to draw a straight line
        function drawLine(x1, y1, x2, y2) {
            const path = new THREE.LineCurve3(new THREE.Vector3(x1, y1, 0), new THREE.Vector3(x2, y2, 0));
            const geometry = new THREE.TubeGeometry(path, 1, 0.4, 16, false);
            group.add(new THREE.Mesh(geometry, material));
        }

        // Helper function to draw an arc (for the 'C')
        function drawArc(x, y, radius, startAngle, endAngle) {
            const path = new THREE.ArcCurve(x, y, radius, startAngle, endAngle, false);
            const points = path.getPoints(32);
            const curve = new THREE.CatmullRomCurve3(points.map(p => new THREE.Vector3(p.x, p.y, 0)));
            const geometry = new THREE.TubeGeometry(curve, 32, 0.4, 16, false);
            group.add(new THREE.Mesh(geometry, material));
        }

        // --- Draw 'V' ---
        drawLine(-4, 2, -3, -2);
        drawLine(-3, -2, -2, 2);

        // --- Draw 'I' ---
        drawLine(0, 2, 0, -2);

        // --- Draw 'C' ---
        drawArc(3, 0, 2, Math.PI * 0.25, Math.PI * 1.75);

        // Center the whole group
        group.position.x = -0.5; 
        scene.add(group);

        // 6. Animation Loop
        const clock = new THREE.Clock();

        function animate() {
            requestAnimationFrame(animate);
            
            const time = clock.getElapsedTime();

            // Rotate 360 degrees
            group.rotation.y = time * 1.2;
            // Float up and down
            group.position.y = Math.sin(time * 2) * 0.5;

            renderer.render(scene, camera);
        }

        animate();

        // 7. Handle window resize (e.g., when you tilt your phone)
        window.addEventListener('resize', () => {
            if (container.clientWidth > 0 && container.clientHeight > 0) {
                camera.aspect = container.clientWidth / container.clientHeight;
                camera.updateProjectionMatrix();
                renderer.setSize(container.clientWidth, container.clientHeight);
            }
        });
    </script>
</body>
</html>
```
</details>

# Fixseo — SEO Audit & Digital Growth Agency

![Fixseo Logo](https://fixseo.uk/IMG_9720.jpeg)

**Automated SEO audits in 5 seconds. Get a score, issues list, and fix guide delivered to your inbox.**

[![Website](https://img.shields.io/badge/Website-fixseo.uk-blue?style=flat-square)](https://fixseo.uk)
[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg?style=flat-square)](https://opensource.org/licenses/MIT)

---

## 🚀 Live Site

Visit Fixseo → **[https://fixseo.uk](https://fixseo.uk)**

---

## ✨ Features

### 🔍 Automated SEO Audits
- Get a full SEO score in 5 seconds
- Identify technical issues holding your site back
- Receive a step-by-step fix guide
- No calls. No meetings. No subscriptions.

### 🤖 AI Visibility Check
- See if AI search engines (Gemini, ChatGPT, Perplexity) can find your site
- Check for AI crawler blocking
- Free visibility report

---

## 🧠 What's Included

| Feature | Description |
| :--- | :--- |
| **SEO Score** | 0-100 rating of your site's health |
| **Title Tag Check** | Missing or too long/short |
| **Meta Description** | Missing or poorly written |
| **H1 Heading** | Missing or multiple H1s |
| **Mobile Friendliness** | Viewport and responsive checks |
| **AI Crawlability** | Check if AI bots are blocked |
| **Fix Guide** | Step-by-step instructions |
| **Full Audit Report** | Complete breakdown of issues |

---

## 💰 Pricing

| Product | Price | What You Get |
| :--- | :--- | :--- |
| **AI Visibility Check** | Free | Check if AI can see your site |
| **Quick Fix Guide** | £9.99 | Step-by-step fix guide only |
| **Full SEO Audit + Guide** | £19.99 | Complete audit + fix guide |

---

## 📊 How It Works

| Step | Action |
| :--- | :--- |
| **1** | Enter your website URL and email |
| **2** | Vic scans your site for SEO issues |
| **3** | You receive a score and issues list |
| **4** | Apply the fixes and improve your ranking |

---

## 🛠️ Tech Stack

| Frontend | Backend | Deployment |
| :--- | :--- | :--- |
| HTML/CSS | Python Flask | Vercel |
| JavaScript | Node.js | Cloud Run |
| Tailwind CSS | Brevo SMTP | GitHub |
| - | CashClaw | - |

---

## 📦 Installation

Clone the repository:

```bash
git clone https://github.com/djp1122222-alt/fixseo.git
cd fixseo
```

