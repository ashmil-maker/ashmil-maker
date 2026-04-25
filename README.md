<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Alex Neon | Electric Developer</title>
    <link href="https://fonts.googleapis.com/css2?family=Orbitron:wght@400;700;900&family=Inter:wght@300;400;600&display=swap" rel="stylesheet">
    <style>
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
        }

        body {
            background: linear-gradient(135deg, #0a0a0a 0%, #0d1117 50%, #000 100%);
            color: #e0e0e0;
            font-family: 'Inter', sans-serif;
            overflow-x: hidden;
            position: relative;
            min-height: 100vh;
        }

        /* Particle Background */
        .particles {
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            pointer-events: none;
            z-index: 1;
        }

        .particle {
            position: absolute;
            background: radial-gradient(circle, #00f7ff20, transparent);
            border-radius: 50%;
            animation: float 20s infinite linear;
        }

        @keyframes float {
            0% { transform: translateY(100vh) rotate(0deg); opacity: 0; }
            10% { opacity: 1; }
            90% { opacity: 1; }
            100% { transform: translateY(-100px) rotate(360deg); opacity: 0; }
        }

        /* Lightning Effect */
        .lightning {
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            pointer-events: none;
            z-index: 2;
            opacity: 0;
        }

        .lightning::before {
            content: '';
            position: absolute;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            background: radial-gradient(circle, rgba(0,247,255,0.1) 0%, transparent 70%);
            animation: lightningFlash 8s infinite;
        }

        @keyframes lightningFlash {
            0%, 90%, 100% { opacity: 0; transform: scale(1); }
            91% { opacity: 0.3; transform: scale(1.1); }
            92% { opacity: 0; }
        }

        /* Cursor Trail */
        .cursor-trail {
            position: fixed;
            width: 20px;
            height: 20px;
            background: radial-gradient(circle, #00f7ff40, transparent);
            border-radius: 50%;
            pointer-events: none;
            z-index: 1000;
            transition: transform 0.1s ease;
        }

        /* Main Container */
        .container {
            position: relative;
            z-index: 10;
            max-width: 1400px;
            margin: 0 auto;
            padding: 0 20px;
        }

        /* Hero Section */
        .hero {
            height: 100vh;
            display: flex;
            flex-direction: column;
            justify-content: center;
            align-items: center;
            text-align: center;
            position: relative;
        }

        .hero h1 {
            font-family: 'Orbitron', monospace;
            font-size: clamp(3rem, 8vw, 8rem);
            font-weight: 900;
            background: linear-gradient(45deg, #00f7ff, #ff00ff, #00ff88, #00f7ff);
            background-size: 300% 300%;
            -webkit-background-clip: text;
            -webkit-text-fill-color: transparent;
            background-clip: text;
            animation: gradientShift 3s ease infinite, glowPulse 2s ease-in-out infinite alternate;
            text-shadow: 0 0 20px rgba(0,247,255,0.5);
            position: relative;
        }

        .hero h1::before {
            content: '';
            position: absolute;
            top: -10px;
            left: 50%;
            transform: translateX(-50%);
            width: 100%;
            height: 4px;
            background: linear-gradient(90deg, transparent, #00f7ff, #ff00ff, transparent);
            border-radius: 2px;
            animation: electricFlow 2s linear infinite;
        }

        @keyframes gradientShift {
            0%, 100% { background-position: 0% 50%; }
            50% { background-position: 100% 50%; }
        }

        @keyframes glowPulse {
            0% { filter: drop-shadow(0 0 20px #00f7ff40); }
            100% { filter: drop-shadow(0 0 40px #00f7ff80); }
        }

        @keyframes electricFlow {
            0% { transform: translateX(-50%) scaleX(0); }
            50%, 100% { transform: translateX(-50%) scaleX(1); }
        }

        .typing-text {
            font-size: clamp(1.2rem, 3vw, 2rem);
            font-weight: 300;
            margin: 20px 0 40px;
            min-height: 2.5rem;
            color: #b0b0b0;
        }

        .typing-text::after {
            content: '|';
            animation: blink 1s infinite;
            color: #00f7ff;
        }

        @keyframes blink {
            0%, 50% { opacity: 1; }
            51%, 100% { opacity: 0; }
        }

        /* Section Headers */
        .section-header {
            font-family: 'Orbitron', monospace;
            font-size: clamp(2rem, 5vw, 4rem);
            font-weight: 700;
            text-align: center;
            margin: 100px 0 60px;
            background: linear-gradient(45deg, #00f7ff, #ff00ff);
            -webkit-background-clip: text;
            -webkit-text-fill-color: transparent;
            background-clip: text;
            position: relative;
            filter: drop-shadow(0 0 20px rgba(0,247,255,0.3));
        }

        .section-header::after {
            content: '';
            position: absolute;
            bottom: -10px;
            left: 50%;
            transform: translateX(-50%);
            width: 80px;
            height: 2px;
            background: linear-gradient(90deg, #00f7ff, #ff00ff);
            border-radius: 1px;
        }

        /* Quote Section */
        .quote {
            background: rgba(0,247,255,0.05);
            backdrop-filter: blur(20px);
            border: 1px solid rgba(0,247,255,0.2);
            border-radius: 20px;
            padding: 40px;
            margin: 60px 0;
            text-align: center;
            font-size: 1.3rem;
            font-style: italic;
            position: relative;
            overflow: hidden;
        }

        .quote::before {
            content: '"';
            font-size: 6rem;
            color: #00f7ff40;
            position: absolute;
            top: -20px;
            left: 20px;
            font-family: serif;
        }

        .quote::after {
            content: '"';
            font-size: 6rem;
            color: #00f7ff40;
            position: absolute;
            bottom: -40px;
            right: 20px;
            font-family: serif;
        }

        /* Skills Section */
        .skills-grid {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(200px, 1fr));
            gap: 20px;
            margin: 40px 0;
        }

        .skill-badge {
            background: rgba(13,17,23,0.8);
            backdrop-filter: blur(10px);
            border: 1px solid rgba(0,247,255,0.3);
            border-radius: 15px;
            padding: 25px;
            text-align: center;
            transition: all 0.3s ease;
            position: relative;
            overflow: hidden;
        }

        .skill-badge:hover {
            transform: translateY(-10px) scale(1.05);
            border-color: #00f7ff;
            box-shadow: 0 20px 40px rgba(0,247,255,0.3);
            background: rgba(0,247,255,0.1);
        }

        .skill-badge::before {
            content: '';
            position: absolute;
            top: 0;
            left: -100%;
            width: 100%;
            height: 100%;
            background: linear-gradient(90deg, transparent, rgba(0,247,255,0.2), transparent);
            transition: left 0.5s;
        }

        .skill-badge:hover::before {
            left: 100%;
        }

        .skill-icon {
            font-size: 2.5rem;
            margin-bottom: 10px;
            background: linear-gradient(45deg, #00f7ff, #ff00ff);
            -webkit-background-clip: text;
            -webkit-text-fill-color: transparent;
            background-clip: text;
            display: block;
        }

        /* Projects Section */
        .projects-grid {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(350px, 1fr));
            gap: 30px;
            margin: 40px 0;
        }

        .project-card {
            background: rgba(13,17,23,0.6);
            backdrop-filter: blur(20px);
            border: 1px solid rgba(0,247,255,0.2);
            border-radius: 20px;
            padding: 30px;
            transition: all 0.4s cubic-bezier(0.25, 0.46, 0.45, 0.94);
            position: relative;
            overflow: hidden;
        }

        .project-card::before {
            content: '';
            position: absolute;
            top: 0;
            left: 0;
            right: 0;
            height: 4px;
            background: linear-gradient(90deg, #00f7ff, #ff00ff, #00f7ff);
            background-size: 200% 100%;
            animation: shimmer 2s infinite;
        }

        @keyframes shimmer {
            0% { background-position: 200% 0; }
            100% { background-position: -200% 0; }
        }

        .project-card:hover {
            transform: translateY(-15px);
            box-shadow: 0 30px 60px rgba(0,247,255,0.4);
            border-color: #00f7ff;
        }

        .project-title {
            font-family: 'Orbitron', monospace;
            font-size: 1.5rem;
            margin-bottom: 15px;
            color: #00f7ff;
        }

        .project-tech {
            display: flex;
            flex-wrap: wrap;
            gap: 8px;
            margin-bottom: 20px;
        }

        .tech-tag {
            background: rgba(0,247,255,0.1);
            color: #00f7ff;
            padding: 5px 12px;
            border-radius: 20px;
            font-size: 0.8rem;
            border: 1px solid rgba(0,247,255,0.3);
        }

        /* Stats Section */
        .stats-container {
            background: rgba(13,17,23,0.4);
            backdrop-filter: blur(20px);
            border: 1px solid rgba(0,247,255,0.2);
            border-radius: 20px;
            padding: 40px;
            text-align: center;
            margin: 40px 0;
        }

        .stats-grid {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(150px, 1fr));
            gap: 30px;
            margin-top: 30px;
        }

        .stat-item {
            position: relative;
        }

        .stat-number {
            font-family: 'Orbitron', monospace;
            font-size: 2.5rem;
            font-weight: 900;
            background: linear-gradient(45deg, #00f7ff, #ff00ff);
            -webkit-background-clip: text;
            -webkit-text-fill-color: transparent;
            background-clip: text;
            display: block;
        }

        .stat-label {
            color: #888;
            font-size: 0.9rem;
            margin-top: 5px;
            letter-spacing: 1px;
        }

        /* Contact Section */
        .contact {
            text-align: center;
            padding: 80px 0 40px;
            border-top: 1px solid rgba(0,247,255,0.2);
            margin-top: 80px;
        }

        .contact-links {
            display: flex;
            justify-content: center;
            gap: 30px;
            margin-top: 30px;
            flex-wrap: wrap;
        }

        .contact-link {
            color: #b0b0b0;
            text-decoration: none;
            font-size: 1.1rem;
            padding: 12px 24px;
            border: 1px solid rgba(0,247,255,0.3);
            border-radius: 50px;
            transition: all 0.3s ease;
            position: relative;
            overflow: hidden;
        }

        .contact-link:hover {
            color: #00f7ff;
            border-color: #00f7ff;
            box-shadow: 0 10px 30px rgba(0,247,255,0.3);
            transform: translateY(-3px);
        }

        /* Scroll Progress */
        .scroll-progress {
            position: fixed;
            top: 0;
            left: 0;
            height: 4px;
            background: linear-gradient(90deg, #00f7ff, #ff00ff);
            z-index: 1001;
            transform-origin: left;
        }

        /* Responsive */
        @media (max-width: 768px) {
            .container { padding: 0 15px; }
            .skills-grid, .projects-grid { grid-template-columns: 1fr; }
            .stats-grid { grid-template-columns: repeat(2, 1fr); }
            .contact-links { flex-direction: column; align-items: center; }
        }

        /* Smooth Scroll */
        html {
            scroll-behavior: smooth;
        }
    </style>
</head>
<body>
    <!-- Particle Background -->
    <div class="particles" id="particles"></div>
    
    <!-- Lightning Effect -->
    <div class="lightning"></div>
    
    <!-- Cursor Trail -->
    <div class="cursor-trail" id="cursorTrail"></div>
    
    <!-- Scroll Progress -->
    <div class="scroll-progress" id="scrollProgress"></div>

    <div class="container">
        <!-- Hero Section -->
        <section class="hero" id="hero">
            <h1>Alex Neon</h1>
            <div class="typing-text" id="typingText"></div>
        </section>

        <!-- Quote Section -->
        <div class="quote">
            "Code doesn't just run. It pulses with electric potential, waiting to strike."
        </div>

        <!-- About Section -->
        <h2 class="section-header">About</h2>
        <p style="text-align: center; max-width: 800px; margin: 0 auto 80px; line-height: 1.8; opacity: 0.9;">
            Full-stack developer crafting futuristic experiences with React, Node.js, and bleeding-edge WebGL. 
            I build interfaces that feel alive—electric, responsive, and impossibly smooth. 
            When not coding, I'm chasing the perfect synthwave playlist or reverse-engineering neural networks.
        </p>

        <!-- Skills Section -->
        <h2 class="section-header">Skills</h2>
        <div class="skills-grid">
            <div class="skill-badge">
                <span class="skill-icon">⚛️</span>
                <strong>React</strong>
                <div style="font-size: 0.9rem; color: #888; margin-top: 8px;">Next.js • TypeScript</div>
            </div>
            <div class="skill-badge">
                <span class="skill-icon">⚡</span>
                <strong>Node.js</strong>
                <div style="font-size: 0.9rem; color: #888; margin-top: 8px;">Express • Fastify</div>
            </div>
            <div class="skill-badge">
                <span class="skill-icon">🌐</span>
                <strong>WebGL</strong>
                <div style="font-size: 0.9rem; color: #888; margin-top: 8px;">Three.js • Shader GLSL</div>
            </div>
            <div class="skill-badge">
                <span class="skill-icon">📱</span>
                <strong>Mobile</strong>
                <div style="font-size: 0.9rem; color: #888; margin-top: 8px;">React Native • Swift</div>
            </div>
            <div class="skill-badge">
                <span class="skill-icon">🐳</span>
                <strong>DevOps</strong>
                <div style="font-size: 0.9rem; color: #888; margin-top: 8px;">Docker • Kubernetes</div>
            </div>
            <div class="skill-badge">
                <span class="skill-icon">🎨</span>
                <strong>Design</strong>
                <div style="font-size: 0.9rem; color: #888; margin-top: 8px;">Figma • Framer Motion</div>
            </div>
        </div>

        <!-- Projects Section -->
        <h2 class="section-header">Projects</h2>
        <div class="projects-grid">
            <div class="project-card">
                <h3 class="project-title">NeonForge</h3>
                <div class="project-tech">
                    <span class="tech-tag">React</span>
                    <span class="tech-tag">Three.js</span>
                    <span class="tech-tag">WebGL</span>
                </div>
                <p style="color: #b0b0b0; line-height: 1.6;">
                    Real-time 3D shader editor with live collaboration. Built collaborative WebGL playground with node-based shader composition.
                </p>
                <div style="margin-top: 20px;">
                    <a href="#" class="contact-link" style="font-size: 0.9rem; padding: 8px 20px; display: inline-block;">Live Demo</a>
                    <a href="#" class="contact-link" style="font-size: 0.9rem; padding: 8px 20px; display: inline-block; margin-left: 10px;">Code</a>
                </div>
            </div>
            <div class="project-card">
                <h3 class="project-title">Pulse API</h3>
                <div class="project-tech">
                    <span class="tech-tag">Node.js</span>
                    <span class="tech-tag">GraphQL</span>
                    <span class="tech-tag">Kafka</span>
                </div>
                <p style="color: #b0b0b0; line-height: 1.6;">
                    High-throughput streaming API handling 10M+ req/min. Distributed event streaming platform with zero-downtime deployments.
                </p>
                <div style="margin-top: 20px;">
                    <a href="#" class="contact-link" style="font-size: 0.9rem; padding: 8px 20px; display: inline-block;">Docs</a>
                </div>
            </div>
            <div class="project-card">
                <h3 class="project-title">SynthWave UI</h3>
                <div class="project-tech">
                    <span class="tech-tag">Tailwind</span>
                    <span class="tech-tag">Framer Motion</span>
                    <span class="tech-tag">React</span>
                </div>
                <p style="color: #b0b0b0; line-height: 1.6;">
                    100+ component library with electric animations. Production-ready UI kit with glassmorphism and particle systems.
                </p>
                <div style="margin-top: 20px;">
                    <a href="#" class="contact-link" style="font-size: 0.9rem; padding: 8px 20px; display: inline-block;">View Library</a>
                </div>
            </div>
        </div>

        <!-- GitHub Stats -->
        <h2 class="section-header">Stats</h2>
        <div class="stats-container">
            <div class="stats-grid">
                <div class="stat-item">
                    <span class="stat-number" data-target="127">0</span>
                    <div class="stat-label">Repositories</div>
                </div>
                <div class="stat-item">
                    <span class="stat-number" data-target="48">0</span>
                    <div class="stat-label">Stars</div>
                </div>
                <div class="stat-item">
                    <span class="stat-number" data-target="23">0</span>
                    <div class="stat-label">Forks</div>
                </div>
                <div class="stat-item">
                    <span class="stat-number" data-target="12.5k">0</span>
                    <div class="stat-label">Commits</div>
                </div>
            </div>
        </div>

        <!-- Contact Section -->
        <section class="contact">
            <h2 class="section-header">Connect</h2>
            <p style="font-size: 1.2rem; opacity: 0.9; margin-bottom: 30px;">
                Let's build something electric ⚡️
            </p>
            <div class="contact-links">
                <a href="#" class="contact-link">✉️ hello@alexneon.dev</a>
                <a href="#" class="contact-link">🐙 github.com/alexneon</a>
                <a href="#" class="contact-link">💼 linkedin.com/in/alexneon</a>
                <a href="#" class="contact-link">🐦 x.com/alexneon_dev</a>
            </div>
        </section>
    </div>

    <script>
        // Typing Effect
        const phrases = [
            "Full-Stack Developer",
            "WebGL Sorcerer",
            "Neon Architect", 
            "Electric Coder",
            "Future Builder"
        ];
        let phraseIndex = 0;
        let charIndex = 0;
        let isDeleting = false;

        function typeWriter() {
            const typingElement = document.getElementById('typingText');
            const currentPhrase = phrases[phraseIndex];
            
            if (isDeleting) {
                typingElement.textContent = currentPhrase.substring(0, charIndex - 1);
                charIndex--;
            } else {
                typingElement.textContent = currentPhrase.substring(0, charIndex + 1);
                charIndex++;
            }
            
            let typeSpeed = isDeleting ? 50 : 100;
            if (charIndex === currentPhrase.length) {
                isDeleting = true;
                typeSpeed = 2000;
            } else if (charIndex === 0) {
                isDeleting = false;
                phraseIndex = (phraseIndex + 1) % phrases.length;
            }
            
            setTimeout(typeWriter, typeSpeed);
        }
        typeWriter();

        // Particle System
        function createParticle() {
            const particle = document.createElement('div');
            particle.className = 'particle';
            particle.style.left = Math.random() * 100 + '%';
            particle.style.width = (Math.random() * 4 + 2) + 'px';
            particle.style.height = particle.style.width;
            particle.style.animationDuration = (Math.random() * 10 + 10) + 's';
            particle.style.animationDelay = Math.random() * 5 + 's';
            document.getElementById('particles').appendChild(particle);

            setTimeout(() => {
                particle.remove();
            }, 30000);
        }

        setInterval(createParticle, 300);

        // Cursor Trail
        const cursorTrail = document.getElementById('cursorTrail');
        document.addEventListener('mousemove', (e) => {
            cursorTrail.style.left = e.clientX + 'px';
            cursorTrail.style.top = e.clientY + 'px';
        });

        // Scroll Progress
        window.addEventListener('scroll', () => {
            const scrollTop = document.documentElement.scrollTop;
            const scrollHeight = document.documentElement.scrollHeight - document.documentElement.clientHeight;
            const progress = (scrollTop / scrollHeight) * 100;
            document.getElementById('scrollProgress').style.transform = `scaleX(${progress / 100})`;
        });

        // Animate Stats on Scroll
        const observerOptions = {
            threshold: 0.5,
            rootMargin: '0px 0px -100px 0px'
        };

        const observer = new IntersectionObserver((entries) => {
            entries.forEach(entry => {
                if (entry.isIntersecting) {
                    const statNumbers = entry.target.querySelectorAll('.stat-number');
                    statNumbers.forEach(stat => animateNumber(stat));
                }
            });
        }, observerOptions);

        function animateNumber(element) {
            const target = parseFloat(element.dataset.target);
            let current = 0;
            const increment = target / 100;
            const timer = setInterval(() => {
                current += increment;
                if (current >= target) {
                    current = target;
                    clearInterval(timer);
                }
                element.textContent = Math.floor(current).toLocaleString();
            }, 20);
        }

        observer.observe(document.querySelector('.stats-container'));

        // Lightning flashes
        setInterval(() => {
            document.querySelector('.lightning').style.opacity = Math.random() > 0.95 ? '0.8' : '0';
        }, 8000);
    </script>
</body>
</html>
