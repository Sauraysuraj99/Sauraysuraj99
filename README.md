<!DOCTYPE html>
<html lang="en">

<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0, user-scalable=no">
    <title>Suraj Kumar | Java Full Stack Developer | Animated Portfolio</title>
    <!-- Google Fonts & Font Awesome -->
    <link
        href="https://fonts.googleapis.com/css2?family=Inter:opsz,wght@14..32,300;14..32,400;14..32,600;14..32,700;14..32,800&family=JetBrains+Mono:wght@400;500&display=swap"
        rel="stylesheet">
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.0.0-beta3/css/all.min.css">
    <style>
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
        }

        body {
            background: #0a0c10;
            font-family: 'Inter', sans-serif;
            color: #edeff2;
            overflow-x: hidden;
            line-height: 1.5;
        }

        /* animated gradient mesh background */
        .animated-bg {
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            z-index: -2;
            background: radial-gradient(circle at 20% 30%, rgba(25, 30, 45, 0.9), #07090e);
        }

        .animated-bg::before {
            content: "";
            position: absolute;
            width: 200%;
            height: 200%;
            top: -50%;
            left: -50%;
            background: radial-gradient(circle at 40% 50%, rgba(100, 80, 200, 0.18), transparent 70%);
            animation: slowDrift 28s infinite alternate ease-in-out;
            pointer-events: none;
        }

        .animated-bg::after {
            content: "";
            position: absolute;
            width: 150%;
            height: 150%;
            top: -30%;
            left: -30%;
            background: radial-gradient(ellipse at 80% 70%, rgba(0, 200, 180, 0.08), transparent 60%);
            animation: slowDriftReverse 32s infinite alternate;
            pointer-events: none;
        }

        @keyframes slowDrift {
            0% {
                transform: translate(0%, 0%) rotate(0deg);
                opacity: 0.4;
            }

            100% {
                transform: translate(4%, 6%) rotate(4deg);
                opacity: 0.8;
            }
        }

        @keyframes slowDriftReverse {
            0% {
                transform: translate(0%, 0%) rotate(0deg);
            }

            100% {
                transform: translate(-5%, 3%) rotate(-3deg);
            }
        }

        /* floating particles (code-like) */
        .code-particles {
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            z-index: -1;
            pointer-events: none;
            overflow: hidden;
        }

        .particle {
            position: absolute;
            font-family: 'JetBrains Mono', monospace;
            font-size: 0.9rem;
            opacity: 0.2;
            color: #5f7f9e;
            white-space: nowrap;
            user-select: none;
            animation: floatParticle linear infinite;
        }

        @keyframes floatParticle {
            0% {
                transform: translateY(100vh) translateX(0) rotate(0deg);
                opacity: 0;
            }

            20% {
                opacity: 0.3;
            }

            80% {
                opacity: 0.3;
            }

            100% {
                transform: translateY(-20vh) translateX(40px) rotate(8deg);
                opacity: 0;
            }
        }

        /* layout */
        .container {
            max-width: 1300px;
            margin: 0 auto;
            padding: 2rem 2rem 4rem;
        }

        /* hero section */
        .hero {
            min-height: 90vh;
            display: flex;
            flex-direction: column;
            justify-content: center;
            align-items: center;
            text-align: center;
            gap: 1.2rem;
            padding: 2rem 1rem;
        }

        .avatar-wrapper {
            margin-bottom: 1rem;
            position: relative;
        }

        .avatar {
            width: 140px;
            height: 140px;
            border-radius: 50%;
            border: 3px solid rgba(0, 210, 200, 0.6);
            box-shadow: 0 20px 35px -10px rgba(0, 0, 0, 0.5), 0 0 0 6px rgba(0, 210, 200, 0.1);
            transition: transform 0.3s ease;
            object-fit: cover;
        }

        .avatar:hover {
            transform: scale(1.02);
        }

        .glow-text {
            background: linear-gradient(135deg, #C0F2FF, #A5D8FF, #7B9EFF);
            background-clip: text;
            -webkit-background-clip: text;
            color: transparent;
            font-weight: 800;
        }

        h1 {
            font-size: 3.2rem;
            font-weight: 800;
            letter-spacing: -0.02em;
        }

        .typed-container {
            font-size: 1.6rem;
            font-weight: 500;
            min-height: 4rem;
            color: #bfd9ff;
        }

        .highlight {
            color: #6fe5ff;
            border-bottom: 2px solid #3aa8ff;
            display: inline-block;
        }

        .tagline {
            max-width: 650px;
            color: #b0bbd4;
            font-size: 1.1rem;
            margin: 1rem 0;
        }

        .btn-group {
            display: flex;
            gap: 1.2rem;
            flex-wrap: wrap;
            justify-content: center;
            margin-top: 1.2rem;
        }

        .btn {
            padding: 0.8rem 2rem;
            border-radius: 60px;
            font-weight: 600;
            text-decoration: none;
            transition: all 0.25s ease;
            display: inline-flex;
            align-items: center;
            gap: 0.6rem;
            background: rgba(20, 30, 45, 0.7);
            backdrop-filter: blur(4px);
            border: 0.5px solid rgba(100, 150, 250, 0.3);
            color: #eef4ff;
        }

        .btn-primary {
            background: linear-gradient(95deg, #2a6fdb, #3b82f6);
            border: none;
            box-shadow: 0 8px 18px rgba(59, 130, 246, 0.25);
        }

        .btn-primary:hover {
            transform: translateY(-3px);
            background: linear-gradient(95deg, #3b7beb, #4f93ff);
            box-shadow: 0 15px 25px -8px rgba(59, 130, 246, 0.4);
        }

        .btn-outline:hover {
            background: rgba(59, 130, 246, 0.2);
            border-color: #3b82f6;
            transform: translateY(-2px);
        }

        /* section styles */
        section {
            margin: 5rem 0;
        }

        .section-title {
            font-size: 2rem;
            font-weight: 700;
            margin-bottom: 2rem;
            display: flex;
            align-items: center;
            gap: 12px;
        }

        .section-title i {
            font-size: 1.8rem;
            background: linear-gradient(145deg, #6ee7ff, #3b82f6);
            background-clip: text;
            -webkit-background-clip: text;
            color: transparent;
        }

        .tech-grid {
            display: flex;
            flex-wrap: wrap;
            gap: 1rem;
            margin-top: 1.5rem;
        }

        .tech-badge {
            background: #11161f;
            padding: 0.6rem 1.3rem;
            border-radius: 40px;
            font-size: 0.9rem;
            font-weight: 500;
            backdrop-filter: blur(4px);
            border: 1px solid #2a3342;
            transition: all 0.2s;
            display: inline-flex;
            align-items: center;
            gap: 8px;
        }

        .tech-badge i {
            font-size: 1rem;
            color: #3b82f6;
        }

        .tech-badge:hover {
            border-color: #3b82f6;
            transform: translateY(-3px);
            background: #0f1825;
        }

        /* repo cards animation */
        .repo-grid {
            display: grid;
            grid-template-columns: repeat(auto-fill, minmax(300px, 1fr));
            gap: 1.6rem;
            margin-top: 2rem;
        }

        .repo-card {
            background: rgba(15, 22, 33, 0.65);
            backdrop-filter: blur(6px);
            border-radius: 24px;
            padding: 1.5rem;
            border: 1px solid rgba(70, 130, 200, 0.2);
            transition: all 0.3s cubic-bezier(0.2, 0.9, 0.4, 1.1);
            animation: fadeUp 0.6s ease backwards;
        }

        .repo-card:hover {
            transform: translateY(-5px) scale(1.01);
            border-color: rgba(59, 130, 246, 0.5);
            background: rgba(20, 30, 48, 0.8);
            box-shadow: 0 25px 35px -12px rgba(0, 0, 0, 0.4);
        }

        .repo-name {
            font-weight: 700;
            font-size: 1.25rem;
            display: flex;
            align-items: center;
            gap: 8px;
        }

        .repo-desc {
            font-size: 0.85rem;
            color: #9cb0d0;
            margin: 0.6rem 0 1rem;
            line-height: 1.4;
        }

        .lang-color {
            display: inline-block;
            width: 12px;
            height: 12px;
            border-radius: 50%;
            background: #e34c26;
            margin-right: 6px;
        }

        /* timeline stats */
        .stats-wrap {
            display: flex;
            justify-content: space-between;
            flex-wrap: wrap;
            gap: 2rem;
            background: rgba(12, 18, 28, 0.6);
            border-radius: 2rem;
            padding: 2rem;
            backdrop-filter: blur(8px);
            border: 1px solid #2a3342;
        }

        .stat-item {
            flex: 1;
            text-align: center;
        }

        .stat-number {
            font-size: 2.5rem;
            font-weight: 800;
            background: linear-gradient(135deg, #fff, #8bb5ff);
            background-clip: text;
            -webkit-background-clip: text;
            color: transparent;
        }

        .footer-social {
            display: flex;
            justify-content: center;
            gap: 2rem;
            margin-top: 3rem;
            flex-wrap: wrap;
        }

        .social-link {
            font-size: 1.6rem;
            color: #9aaec9;
            transition: 0.2s;
        }

        .social-link:hover {
            color: #3b82f6;
            transform: translateY(-3px);
        }

        /* animations */
        @keyframes fadeUp {
            from {
                opacity: 0;
                transform: translateY(20px);
            }

            to {
                opacity: 1;
                transform: translateY(0);
            }
        }

        .animate-once {
            animation: fadeUp 0.6s ease forwards;
        }

        /* responsive */
        @media (max-width: 700px) {
            h1 {
                font-size: 2.2rem;
            }

            .typed-container {
                font-size: 1.2rem;
            }

            .container {
                padding: 1.5rem;
            }

            .stats-wrap {
                flex-direction: column;
                align-items: center;
                gap: 1rem;
            }
        }
    </style>
</head>

<body>

    <div class="animated-bg"></div>
    <div class="code-particles" id="particlesContainer"></div>

    <main class="container">
        <!-- Hero Animation Section -->
        <div class="hero">
            <div class="avatar-wrapper">
                <img class="avatar" src="https://avatars.githubusercontent.com/u/176518497?v=4" alt="Suraj Kumar">
            </div>
            <h1>
                <span class="glow-text">Suraj Kumar</span>
            </h1>
            <div class="typed-container">
                <span id="dynamicRole" class="highlight"></span>
            </div>
            <p class="tagline">
                Java Full Stack Developer · Spring Boot · React · Generative AI Enthusiast <br>
                Building scalable systems & mindful code.
            </p>
            <div class="btn-group">
                <a href="https://github.com/Sauraysuraj99" target="_blank" class="btn btn-primary"><i
                        class="fab fa-github"></i> GitHub</a>
                <a href="https://www.linkedin.com/in/suraj-kumar-168230250/" target="_blank" class="btn btn-outline"><i
                        class="fab fa-linkedin-in"></i> LinkedIn</a>
                <a href="https://radiant-bunny-949c03.netlify.app/" target="_blank" class="btn btn-outline"><i
                        class="fas fa-globe"></i> Portfolio</a>
            </div>
        </div>

        <!-- Tech Stack Section with animation on scroll -->
        <section>
            <div class="section-title">
                <i class="fas fa-code"></i>
                <span>Tech Toolbox</span>
            </div>
            <div class="tech-grid" id="techStack"></div>
        </section>

        <!-- Pinned Repositories (inspired from profile) -->
        <section>
            <div class="section-title">
                <i class="fas fa-star"></i>
                <span>Popular Repositories</span>
            </div>
            <div class="repo-grid" id="repoList"></div>
        </section>

        <!-- GitHub Stats Insight with animated counters -->
        <section>
            <div class="section-title">
                <i class="fas fa-chart-line"></i>
                <span>Dev Pulse</span>
            </div>
            <div class="stats-wrap">
                <div class="stat-item">
                    <div class="stat-number" id="repoCount">56</div>
                    <div>Public Repos</div>
                </div>
                <div class="stat-item">
                    <div class="stat-number" id="followersCount">4</div>
                    <div>Followers</div>
                </div>
                <div class="stat-item">
                    <div class="stat-number" id="followingCount">10</div>
                    <div>Following</div>
                </div>
                <div class="stat-item">
                    <div class="stat-number" id="contributionYear">2026</div>
                    <div>Active Year</div>
                </div>
            </div>
        </section>

        <!-- Connect Footer -->
        <div class="footer-social">
            <a href="https://github.com/Sauraysuraj99" class="social-link" target="_blank"><i
                    class="fab fa-github"></i></a>
            <a href="https://www.linkedin.com/in/suraj-kumar-168230250/" class="social-link" target="_blank"><i
                    class="fab fa-linkedin-in"></i></a>
            <a href="https://www.instagram.com/suraj.sauray_raj99" class="social-link" target="_blank"><i
                    class="fab fa-instagram"></i></a>
            <a href="https://www.facebook.com/share/19X62owCHf/" class="social-link" target="_blank"><i
                    class="fab fa-facebook-f"></i></a>
            <a href="mailto:sauraysuraj@gmail.com" class="social-link" target="_blank"><i
                    class="fas fa-envelope"></i></a>
        </div>
        <p style="text-align: center; margin-top: 3rem; font-size: 0.75rem; opacity: 0.6;">
            ⚡ Debugging code logically & life mindfully — Suraj Kumar
        </p>
    </main>

    <script>
        // ----- dynamic typing animation (leading role)
        const roles = [
            "Java Full Stack Developer",
            "Spring Boot & React Architect",
            "Backend Systems Designer",
            "Generative AI Explorer",
            "Open Source Contributor"
        ];
        let roleIndex = 0;
        let charIndex = 0;
        let isDeleting = false;
        const dynamicSpan = document.getElementById("dynamicRole");

        function typeEffect() {
            const currentRole = roles[roleIndex];
            if (isDeleting) {
                dynamicSpan.innerText = currentRole.substring(0, charIndex - 1);
                charIndex--;
                if (charIndex === 0) {
                    isDeleting = false;
                    roleIndex = (roleIndex + 1) % roles.length;
                    setTimeout(typeEffect, 300);
                } else {
                    setTimeout(typeEffect, 60);
                }
            } else {
                dynamicSpan.innerText = currentRole.substring(0, charIndex + 1);
                charIndex++;
                if (charIndex === currentRole.length) {
                    isDeleting = true;
                    setTimeout(typeEffect, 1800);
                } else {
                    setTimeout(typeEffect, 90);
                }
            }
        }
        typeEffect();

        // ----- floating code particles (JavaScript, Java, etc)
        const particles = ["{ code; }", "() => {}", "<React />", "SpringBoot", "JDBC", "MySQL", "✨ DevOps", "💻 fullstack", "🚀 deploy", "⚡ microservices", "public static void", "npm start"];
        const particleContainer = document.getElementById("particlesContainer");
        for (let i = 0; i < 38; i++) {
            const particle = document.createElement("div");
            particle.className = "particle";
            const randomText = particles[Math.floor(Math.random() * particles.length)];
            particle.innerText = randomText;
            const size = 0.7 + Math.random() * 0.7;
            particle.style.fontSize = `${size}rem`;
            particle.style.left = `${Math.random() * 100}%`;
            particle.style.animationDuration = `${8 + Math.random() * 15}s`;
            particle.style.animationDelay = `${Math.random() * 15}s`;
            particle.style.opacity = `${0.1 + Math.random() * 0.25}`;
            particleContainer.appendChild(particle);
        }

        // Tech stack data fully aligned with your profile (Java, spring, react, sql, git)
        const techStackList = [
            { name: "Java", icon: "fab fa-java" },
            { name: "Spring Boot", icon: "fas fa-leaf" },
            { name: "Hibernate", icon: "fas fa-database" },
            { name: "JavaScript", icon: "fab fa-js" },
            { name: "React", icon: "fab fa-react" },
            { name: "HTML5/CSS3", icon: "fab fa-html5" },
            { name: "MySQL", icon: "fas fa-database" },
            { name: "MongoDB", icon: "fas fa-leaf" },
            { name: "Git/GitHub", icon: "fab fa-git-alt" },
            { name: "Docker", icon: "fab fa-docker" },
            { name: "REST APIs", icon: "fas fa-plug" },
            { name: "Tailwind CSS", icon: "fas fa-paintbrush" }
        ];

        const techContainer = document.getElementById("techStack");
        techStackList.forEach(tech => {
            const badge = document.createElement("div");
            badge.className = "tech-badge";
            badge.innerHTML = `<i class="${tech.icon}"></i> ${tech.name}`;
            techContainer.appendChild(badge);
        });

        // Repositories data based on your pinned repos from profile
        const repositories = [
            { name: "Sauraysuraj99", description: "✨ GitHub profile README — config & bio.", language: "Markdown", color: "#563d7c", url: "https://github.com/Sauraysuraj99/Sauraysuraj99" },
            { name: "PORTFOLIOFILE", description: "Personal portfolio frontend showcase.", language: "HTML", color: "#e34c26", url: "https://github.com/Sauraysuraj99/PORTFOLIOFILE" },
            { name: "portfollio-demo", description: "First repository demo — learning journey.", language: "CSS", color: "#563d7c", url: "https://github.com/Sauraysuraj99/portfollio-demo" },
            { name: "Profile-demo", description: "Interactive profile page demo.", language: "HTML", color: "#e34c26", url: "https://github.com/Sauraysuraj99/Profile-demo" },
            { name: "PROFILE--Portfolio", description: "PROFILE modern portfolio design.", language: "HTML", color: "#e34c26", url: "https://github.com/Sauraysuraj99/PROFILE--Portfolio" },
            { name: "PORTFOLLIOPROFILE-Suraj", description: "Advanced dev portfolio concept.", language: "JavaScript", color: "#f1e05a", url: "https://github.com/Sauraysuraj99/PORTFOLLIOPROFILE-Suraj" }
        ];

        const repoGrid = document.getElementById("repoList");
        repositories.forEach((repo, idx) => {
            const card = document.createElement("div");
            card.className = "repo-card";
            card.style.animationDelay = `${idx * 0.05}s`;
            card.innerHTML = `
      <div class="repo-name">
        <i class="fas fa-book-open"></i>
        <a href="${repo.url}" target="_blank" style="text-decoration: none; color: #cde1ff;">${repo.name}</a>
      </div>
      <div class="repo-desc">${repo.description}</div>
      <div style="font-size: 0.75rem; display: flex; align-items: center; gap: 12px;">
        <span><span class="lang-color" style="background: ${repo.color};"></span> ${repo.language}</span>
        <span><i class="far fa-star"></i> ★</span>
      </div>
    `;
            repoGrid.appendChild(card);
        });

        // Animated counters (from actual stats: 4 followers, 10 following, 56 repos)
        function animateCounter(elementId, targetValue, duration = 1500) {
            const element = document.getElementById(elementId);
            if (!element) return;
            let start = 0;
            const increment = targetValue / (duration / 16);
            let current = 0;
            const updateCounter = () => {
                current += increment;
                if (current < targetValue) {
                    element.innerText = Math.floor(current);
                    requestAnimationFrame(updateCounter);
                } else {
                    element.innerText = targetValue;
                }
            };
            requestAnimationFrame(updateCounter);
        }

        // trigger counters when visible (lazy using intersection observer) 
        const statSection = document.querySelector(".stats-wrap");
        const observer = new IntersectionObserver((entries) => {
            entries.forEach(entry => {
                if (entry.isIntersecting) {
                    animateCounter("repoCount", 56);
                    animateCounter("followersCount", 4);
                    animateCounter("followingCount", 10);
                    document.getElementById("contributionYear").innerText = "2026";
                    observer.disconnect();
                }
            });
        }, { threshold: 0.4 });
        if (statSection) observer.observe(statSection);

        // Additional small animated stats using random motion for "pulse" feel
        const extraEffect = () => {
            const statNumbers = document.querySelectorAll(".stat-number");
            statNumbers.forEach(el => {
                el.style.transition = "text-shadow 0.2s";
                setInterval(() => {
                    if (Math.random() > 0.85) {
                        el.style.textShadow = "0 0 6px #3b82f6";
                        setTimeout(() => el.style.textShadow = "none", 300);
                    }
                }, 1800);
            });
        };
        setTimeout(extraEffect, 1000);

        // Add smooth reveal for all sections on scroll
        const revealElements = document.querySelectorAll("section, .hero, .footer-social");
        const revealObserver = new IntersectionObserver((entries) => {
            entries.forEach(entry => {
                if (entry.isIntersecting) {
                    entry.target.style.opacity = "1";
                    entry.target.style.transform = "translateY(0)";
                    revealObserver.unobserve(entry.target);
                }
            });
        }, { threshold: 0.05 });
        revealElements.forEach(el => {
            el.style.opacity = "0";
            el.style.transform = "translateY(20px)";
            el.style.transition = "all 0.5s cubic-bezier(0.2, 0.9, 0.4, 1.1)";
            revealObserver.observe(el);
        });
        // hero already visible, force reveal
        document.querySelector(".hero").style.opacity = "1";
        document.querySelector(".hero").style.transform = "translateY(0)";

        // Also generate small glow circle moving based on mouse movement (extra polish)
        document.addEventListener("mousemove", (e) => {
            const glow = document.createElement("div");
            // not heavy — just temporary effect
            const x = e.clientX, y = e.clientY;
            const element = document.elementFromPoint(x, y);
            if (element && element.classList && element.classList.contains("repo-card")) {
                element.style.transition = "box-shadow 0.1s";
                element.style.boxShadow = "0 0 0 2px rgba(59,130,246,0.3)";
                setTimeout(() => {
                    if (element) element.style.boxShadow = "";
                }, 150);
            }
        });

        // generate dynamic year in footer
        const yearSpan = document.createElement("span");
        // optional extra: current year display inside footer (already there but dynamic)
        console.log("🔥 Animation Portfolio Loaded — Java Full Stack Momentum");
    </script>
</body>

</html>
- 👋 Hi, I’m @Sauraysuraj99
- 👀 I’m software developer 
- 🌱 I’m currently working...
- 💞️ I’m looking to collaborate on ...
- 📫 How to reach me ...
- 😄 Pronouns: ...
- ⚡ Fun fact: ...
- 👋 Hi, I’m @Sauraysuraj99  

👨‍💻 Software Engineer by profession  
🌿 Explorer & spiritual learner by mindset  

💡 I build scalable backend systems using Java, JDBC, and MySQL.  

🌱 Currently growing in Full Stack Development and life wisdom simultaneously.  

🤝 Open to meaningful collaborations in tech and purpose-driven projects.  

📫 Let’s connect and grow together.  

⚡ I debug code logically and life mindfully.


<!---
Sauraysuraj99/Sauraysuraj99 is a ✨ special ✨ repository because its `README.md` (this file) appears on your GitHub profile.
You can click the Preview link to take a look at your changes.
--->
<h1 align="center">Hi 👋, I'm Suraj Kumar</h1>
<h3 align="center">Java Full Stack Developer 🚀</h3>

---

### 👨‍💻 About Me
- 🔭 I’m currently working on Full Stack Projects  
- 🌱 Currently learning Backend & System Design  
- 💬 Ask me about Java, Spring Boot, React  
- 📍 Bangalore, India  

---

### 🌐 Connect With Me

<p align="left">
<a href="https://radiant-bunny-949c03.netlify.app/" target="blank">🌐 Portfolio</a> |
<a href="https://linkedin.com/in/your-link" target="blank">💼 LinkedIn</a> |
<a href="https://instagram.com/your-link" target="blank">📸 Instagram</a> |
<a href="https://facebook.com/your-link" target="blank">📘 Facebook</a> |
<a href="https://snapchat.com/add/your-link" target="blank">👻 Snapchat</a>
</p>

---

### 🛠️ Tech Stack
- 💻 Java | Spring Boot | Hibernate  
- 🌐 HTML | CSS | JavaScript | React  
- 🗄️ MySQL | MongoDB  
- ⚙️ Git | GitHub | VS Code  

---

### 📊 GitHub Stats

<p align="center">
<img src="https://github-readme-stats.vercel.app/api?username=Sauraysuraj99&show_icons=true&theme=radical" alt="stats" />
</p>

---

### 🔥 Streak Stats



# suraj-
# 💫 About Me:
Hi 👋 I'm Suraj<br>💻 Java Full Stack Developer | Generative AI Enthusiast<br>I am a passionate Software Engineer who enjoys building scalable applications and solving real-world problems using code.<br>I specialize in Java backend development, databases, and modern web technologies, and I am currently exploring Generative AI and intelligent applications.<br>🚀 About Me<br>🔭 I'm currently working on<br>Building scalable web applications using Java, Spring Boot, SQL, and modern web technologies.<br>🤝 I'm looking to collaborate on<br>Open-source Java Full Stack projects, AI-powered applications, and innovative software solutions.<br>🧠 I'm looking for help with<br>Advanced system design, microservices architecture, and Generative AI integration.<br>🌱 I'm currently learning<br>Spring Boot, Microservices, Docker, Cloud, REST APIs, and Generative AI technologies.<br>💬 Ask me about<br>Java, JDBC, SQL, Backend Development, APIs, and Full Stack Development.<br>⚡ Fun fact<br>I enjoy turning ideas into real software applications and constantly learning new technologies.<br>🛠 Tech Stack<br>💻 Programming Languages<br>Java<br>JavaScript<br>SQL<br>⚙ Backend Technologies<br>Spring Boot<br>JDBC<br>REST APIs<br>Microservices<br>🌐 Frontend<br>HTML<br>CSS<br>JavaScript<br>🗄 Database<br>MySQL<br>PostgreSQL<br>🤖 AI / Modern Technologies<br>Generative AI<br>OpenAI APIs<br>AI integrations in web apps<br>☁ Tools & Platforms<br>Git & GitHub<br>Docker<br>VS Code<br>Eclipse<br>📈 GitHub Goals<br>✔ Build real-world Full Stack Projects<br>✔ Contribute to Open Source Projects<br>✔ Integrate Generative AI with Web Applications<br>✔ Improve System Design and Cloud Skills<br>📫 Connect With Me<br>💼 LinkedIn: (Add your LinkedIn link)<br>📧 Email: (Add your email)<br>🌐 Portfolio: (Add portfolio if you create one)


## 🌐 Socials:
[![Facebook](https://img.shields.io/badge/Facebook-%231877F2.svg?logo=Facebook&logoColor=white)](https://facebook.com/https://www.facebook.com/share/17izrBD24N/) [![Instagram](https://img.shields.io/badge/Instagram-%23E4405F.svg?logo=Instagram&logoColor=white)](https://instagram.com/https://www.instagram.com/soul.of.suraj.sauray_raj99?igsh=ZGZ6YWh3Y2JnbTZj) [![LinkedIn](https://img.shields.io/badge/LinkedIn-%230077B5.svg?logo=linkedin&logoColor=white)](https://linkedin.com/in/https://www.linkedin.com/in/suraj-kumar-168230250/) [![Pinterest](https://img.shields.io/badge/Pinterest-%23E60023.svg?logo=Pinterest&logoColor=white)](https://pinterest.com/https://pin.it/44ZRYP7Gl) [![YouTube](https://img.shields.io/badge/YouTube-%23FF0000.svg?logo=YouTube&logoColor=white)](https://youtube.com/@https://youtube.com/@sourceofsurjsurytechnology8793?si=hH65UizHPpFhy6Wn) [![email](https://img.shields.io/badge/Email-D14836?logo=gmail&logoColor=white)](mailto:sauraysuraj@gmail.com) 

# 💻 Tech Stack:
![Apache Groovy](https://img.shields.io/badge/Apache%20Groovy-4298B8.svg?style=for-the-badge&logo=Apache+Groovy&logoColor=white) ![AssemblyScript](https://img.shields.io/badge/assembly%20script-%23000000.svg?style=for-the-badge&logo=assemblyscript&logoColor=white) ![C](https://img.shields.io/badge/c-%2300599C.svg?style=for-the-badge&logo=c&logoColor=white) ![C#](https://img.shields.io/badge/c%23-%23239120.svg?style=for-the-badge&logo=csharp&logoColor=white) ![C++](https://img.shields.io/badge/c++-%2300599C.svg?style=for-the-badge&logo=c%2B%2B&logoColor=white) ![Elixir](https://img.shields.io/badge/elixir-%234B275F.svg?style=for-the-badge&logo=elixir&logoColor=white) ![Dgraph](https://img.shields.io/badge/dgraph-%23E50695.svg?style=for-the-badge&logo=dgraph&logoColor=white) ![Dart](https://img.shields.io/badge/dart-%230175C2.svg?style=for-the-badge&logo=dart&logoColor=white) ![CSS3](https://img.shields.io/badge/css3-%231572B6.svg?style=for-the-badge&logo=css3&logoColor=white) ![Crystal](https://img.shields.io/badge/crystal-%23000000.svg?style=for-the-badge&logo=crystal&logoColor=white) ![Clojure](https://img.shields.io/badge/Clojure-%23Clojure.svg?style=for-the-badge&logo=Clojure&logoColor=Clojure) ![Elm](https://img.shields.io/badge/Elm-60B5CC?style=for-the-badge&logo=elm&logoColor=white) ![Haskell](https://img.shields.io/badge/Haskell-5e5086?style=for-the-badge&logo=haskell&logoColor=white) ![Erlang](https://img.shields.io/badge/Erlang-white.svg?style=for-the-badge&logo=erlang&logoColor=a90533) ![Fortran](https://img.shields.io/badge/Fortran-%23734F96.svg?style=for-the-badge&logo=fortran&logoColor=white) ![Go](https://img.shields.io/badge/go-%2300ADD8.svg?style=for-the-badge&logo=go&logoColor=white) ![GraphQL](https://img.shields.io/badge/-GraphQL-E10098?style=for-the-badge&logo=graphql&logoColor=white) ![Kotlin](https://img.shields.io/badge/kotlin-%237F52FF.svg?style=for-the-badge&logo=kotlin&logoColor=white) ![Julia](https://img.shields.io/badge/-Julia-9558B2?style=for-the-badge&logo=julia&logoColor=white) ![JavaScript](https://img.shields.io/badge/javascript-%23323330.svg?style=for-the-badge&logo=javascript&logoColor=%23F7DF1E) ![HTML5](https://img.shields.io/badge/html5-%23E34F26.svg?style=for-the-badge&logo=html5&logoColor=white) ![Java](https://img.shields.io/badge/java-%23ED8B00.svg?style=for-the-badge&logo=openjdk&logoColor=white) ![LaTeX](https://img.shields.io/badge/latex-%23008080.svg?style=for-the-badge&logo=latex&logoColor=white) ![Lua](https://img.shields.io/badge/lua-%232C2D72.svg?style=for-the-badge&logo=lua&logoColor=white) ![Markdown](https://img.shields.io/badge/markdown-%23000000.svg?style=for-the-badge&logo=markdown&logoColor=white) ![Nim](https://img.shields.io/badge/nim-%23FFE953.svg?style=for-the-badge&logo=nim&logoColor=white) ![Nix](https://img.shields.io/badge/NIX-5277C3.svg?style=for-the-badge&logo=NixOS&logoColor=white) ![Objective-C](https://img.shields.io/badge/OBJECTIVE--C-%233A95E3.svg?style=for-the-badge&logo=apple&logoColor=white) ![PHP](https://img.shields.io/badge/php-%23777BB4.svg?style=for-the-badge&logo=php&logoColor=white) ![Perl](https://img.shields.io/badge/perl-%2339457E.svg?style=for-the-badge&logo=perl&logoColor=white) ![Org Mode](https://img.shields.io/badge/orgmode-%2377AA99.svg?style=for-the-badge&logo=org&logoColor=white) ![Octave](https://img.shields.io/badge/OCTAVE-darkblue?style=for-the-badge&logo=octave&logoColor=fcd683) ![OCaml](https://img.shields.io/badge/OCaml-%23E98407.svg?style=for-the-badge&logo=ocaml&logoColor=white) ![PowerShell](https://img.shields.io/badge/PowerShell-%235391FE.svg?style=for-the-badge&logo=powershell&logoColor=white) ![Scala](https://img.shields.io/badge/scala-%23DC322F.svg?style=for-the-badge&logo=scala&logoColor=white) ![Python](https://img.shields.io/badge/python-3670A0?style=for-the-badge&logo=python&logoColor=ffdd54) ![Bash Script](https://img.shields.io/badge/bash_script-%23121011.svg?style=for-the-badge&logo=gnu-bash&logoColor=white) ![R](https://img.shields.io/badge/r-%23276DC3.svg?style=for-the-badge&logo=r&logoColor=white) ![ReScript](https://img.shields.io/badge/rescript-%2314162c?style=for-the-badge&logo=rescript&logoColor=e34c4c) ![Ruby](https://img.shields.io/badge/ruby-%23CC342D.svg?style=for-the-badge&logo=ruby&logoColor=white) ![Rust](https://img.shields.io/badge/rust-%23000000.svg?style=for-the-badge&logo=rust&logoColor=white) ![TypeScript](https://img.shields.io/badge/typescript-%23007ACC.svg?style=for-the-badge&logo=typescript&logoColor=white) ![Swift](https://img.shields.io/badge/swift-F54A2A?style=for-the-badge&logo=swift&logoColor=white) ![Solidity](https://img.shields.io/badge/Solidity-%23363636.svg?style=for-the-badge&logo=solidity&logoColor=white) ![Windows Terminal](https://img.shields.io/badge/Windows%20Terminal-%234D4D4D.svg?style=for-the-badge&logo=windows-terminal&logoColor=white) ![Zig](https://img.shields.io/badge/Zig-%23F7A41D.svg?style=for-the-badge&logo=zig&logoColor=white) ![Firebase](https://img.shields.io/badge/firebase-%23039BE5.svg?style=for-the-badge&logo=firebase) ![DigitalOcean](https://img.shields.io/badge/DigitalOcean-%230167ff.svg?style=for-the-badge&logo=digitalOcean&logoColor=white) ![Datadog](https://img.shields.io/badge/datadog-%23632CA6.svg?style=for-the-badge&logo=datadog&logoColor=white) ![Codeberg](https://img.shields.io/badge/Codeberg-2185D0?style=for-the-badge&logo=Codeberg&logoColor=white) ![Cloudflare](https://img.shields.io/badge/Cloudflare-F38020?style=for-the-badge&logo=Cloudflare&logoColor=white) ![Azure](https://img.shields.io/badge/azure-%230072C6.svg?style=for-the-badge&logo=microsoftazure&logoColor=white) ![AWS](https://img.shields.io/badge/AWS-%23FF9900.svg?style=for-the-badge&logo=amazon-aws&logoColor=white) ![Alibaba Cloud](https://img.shields.io/badge/AlibabaCloud-%23FF6701.svg?style=for-the-badge&logo=alibabacloud&logoColor=white) ![Glitch](https://img.shields.io/badge/glitch-%233333FF.svg?style=for-the-badge&logo=glitch&logoColor=white) ![Google Cloud](https://img.shields.io/badge/GoogleCloud-%234285F4.svg?style=for-the-badge&logo=google-cloud&logoColor=white) ![Heroku](https://img.shields.io/badge/heroku-%23430098.svg?style=for-the-badge&logo=heroku&logoColor=white) ![Linode](https://img.shields.io/badge/linode-00A95C?style=for-the-badge&logo=linode&logoColor=white) ![Netlify](https://img.shields.io/badge/netlify-%23000000.svg?style=for-the-badge&logo=netlify&logoColor=#00C7B7) ![Oracle](https://img.shields.io/badge/Oracle-F80000?style=for-the-badge&logo=oracle&logoColor=white) ![OpenStack](https://img.shields.io/badge/Openstack-%23f01742.svg?style=for-the-badge&logo=openstack&logoColor=white) ![OVH](https://img.shields.io/badge/ovh-%23123F6D.svg?style=for-the-badge&logo=ovh&logoColor=#123F6D) ![Render](https://img.shields.io/badge/Render-%46E3B7.svg?style=for-the-badge&logo=render&logoColor=white) ![Scaleway](https://img.shields.io/badge/SCALEWAY-%234f0599.svg?style=for-the-badge&logo=scaleway&logoColor=white) ![Vercel](https://img.shields.io/badge/vercel-%23000000.svg?style=for-the-badge&logo=vercel&logoColor=white) ![Vultr](https://img.shields.io/badge/Vultr-007BFC.svg?style=for-the-badge&logo=vultr) ![.Net](https://img.shields.io/badge/.NET-5C2D91?style=for-the-badge&logo=.net&logoColor=white) ![AdonisJS](https://img.shields.io/badge/adonisjs-%23220052.svg?style=for-the-badge&logo=adonisjs&logoColor=white) ![Alpine.js](https://img.shields.io/badge/alpinejs-white.svg?style=for-the-badge&logo=alpinedotjs&logoColor=%238BC0D0) ![Anaconda](https://img.shields.io/badge/Anaconda-%2344A833.svg?style=for-the-badge&logo=anaconda&logoColor=white) ![Angular](https://img.shields.io/badge/angular-%23DD0031.svg?style=for-the-badge&logo=angular&logoColor=white) ![Angular.js](https://img.shields.io/badge/angular.js-%23E23237.svg?style=for-the-badge&logo=angularjs&logoColor=white) ![Ant-Design](https://img.shields.io/badge/-AntDesign-%230170FE?style=for-the-badge&logo=ant-design&logoColor=white) ![Apache Spark](https://img.shields.io/badge/Apache%20Spark-FDEE21?style=for-the-badge&logo=apachespark&logoColor=black) ![Blazor](https://img.shields.io/badge/blazor-%235C2D91.svg?style=for-the-badge&logo=blazor&logoColor=white) ![Aurelia](https://img.shields.io/badge/aurelia-%23ED2B88.svg?style=for-the-badge&logo=aurelia&logoColor=fff) ![Astro](https://img.shields.io/badge/astro-%232C2052.svg?style=for-the-badge&logo=astro&logoColor=white) ![Apollo-GraphQL](https://img.shields.io/badge/-ApolloGraphQL-311C87?style=for-the-badge&logo=apollo-graphql) ![Apache Hive](https://img.shields.io/badge/Apache%20Hive-FDEE21?style=for-the-badge&logo=apachehive&logoColor=black) ![Apache Hadoop](https://img.shields.io/badge/Apache%20Hadoop-66CCFF?style=for-the-badge&logo=apachehadoop&logoColor=black) ![Apache Kafka](https://img.shields.io/badge/Apache%20Kafka-000?style=for-the-badge&logo=apachekafka) ![Bootstrap](https://img.shields.io/badge/bootstrap-%238511FA.svg?style=for-the-badge&logo=bootstrap&logoColor=white) ![Buefy](https://img.shields.io/badge/Buefy-7957D5?style=for-the-badge&logo=buefy&logoColor=48289E) ![Bulma](https://img.shields.io/badge/bulma-00D0B1?style=for-the-badge&logo=bulma&logoColor=white) ![Bun](https://img.shields.io/badge/Bun-%23000000.svg?style=for-the-badge&logo=bun&logoColor=white) ![Chakra](https://img.shields.io/badge/chakra-%234ED1C5.svg?style=for-the-badge&logo=chakraui&logoColor=white) ![Chart.js](https://img.shields.io/badge/chart.js-F5788D.svg?style=for-the-badge&logo=chart.js&logoColor=white) ![Code-Igniter](https://img.shields.io/badge/CodeIgniter-%23EF4223.svg?style=for-the-badge&logo=codeIgniter&logoColor=white) ![Context-API](https://img.shields.io/badge/Context--Api-000000?style=for-the-badge&logo=react) ![nVIDIA](https://img.shields.io/badge/cuda-000000.svg?style=for-the-badge&logo=nVIDIA&logoColor=green) ![Elasticsearch](https://img.shields.io/badge/elasticsearch-%230377CC.svg?style=for-the-badge&logo=elasticsearch&logoColor=white) ![EJS](https://img.shields.io/badge/ejs-%23B4CA65.svg?style=for-the-badge&logo=ejs&logoColor=black) ![Drupal](https://img.shields.io/badge/drupal-%230678BE.svg?style=for-the-badge&logo=drupal&logoColor=white) ![DjangoREST](https://img.shields.io/badge/DJANGO-REST-ff1709?style=for-the-badge&logo=django&logoColor=white&color=ff1709&labelColor=gray) ![Django](https://img.shields.io/badge/django-%23092E20.svg?style=for-the-badge&logo=django&logoColor=white) ![Directus](https://img.shields.io/badge/directus-%2364f.svg?style=for-the-badge&logo=directus&logoColor=white) ![Deno JS](https://img.shields.io/badge/deno%20js-000000?style=for-the-badge&logo=deno&logoColor=white) ![DaisyUI](https://img.shields.io/badge/daisyui-5A0EF8?style=for-the-badge&logo=daisyui&logoColor=white) ![Electron.js](https://img.shields.io/badge/Electron-191970?style=for-the-badge&logo=Electron&logoColor=white) ![Ember](https://img.shields.io/badge/ember-1C1E24?style=for-the-badge&logo=ember.js&logoColor=#D04A37) ![Esbuild](https://img.shields.io/badge/esbuild-%23FFCF00.svg?style=for-the-badge&logo=esbuild&logoColor=black) ![Expo](https://img.shields.io/badge/expo-1C1E24?style=for-the-badge&logo=expo&logoColor=#D04A37) ![Express.js](https://img.shields.io/badge/express.js-%23404d59.svg?style=for-the-badge&logo=express&logoColor=%2361DAFB) ![FastAPI](https://img.shields.io/badge/FastAPI-005571?style=for-the-badge&logo=fastapi) ![Fastify](https://img.shields.io/badge/fastify-%23000000.svg?style=for-the-badge&logo=fastify&logoColor=white) ![Filament](https://img.shields.io/badge/Filament-FFAA00?style=for-the-badge&logoColor=%23000000) ![Flask](https://img.shields.io/badge/flask-%23000.svg?style=for-the-badge&logo=flask&logoColor=white) ![Insomnia](https://img.shields.io/badge/Insomnia-black?style=for-the-badge&logo=insomnia&logoColor=5849BE) ![Gutenberg](https://img.shields.io/badge/gutenberg-%23077CB2.svg?style=for-the-badge&logo=gutenberg&logoColor=white) ![Gulp](https://img.shields.io/badge/GULP-%23CF4647.svg?style=for-the-badge&logo=gulp&logoColor=white) ![Green Sock](https://img.shields.io/badge/green%20sock-88CE02?style=for-the-badge&logo=greensock&logoColor=white) ![Grav](https://img.shields.io/badge/grav-%23FFFFFF.svg?style=for-the-badge&logo=grav&logoColor=221E1F) ![Gatsby](https://img.shields.io/badge/Gatsby-%23663399.svg?style=for-the-badge&logo=gatsby&logoColor=white) ![Framework7](https://img.shields.io/badge/framework7-%23EE350F.svg?style=for-the-badge&logo=framework7&logoColor=white) ![Flutter](https://img.shields.io/badge/Flutter-%2302569B.svg?style=for-the-badge&logo=Flutter&logoColor=white) ![Handlebars](https://img.shields.io/badge/Handlebars-%23000000?style=for-the-badge&logo=Handlebars.js&logoColor=white) ![Laravel](https://img.shields.io/badge/laravel-%23FF2D20.svg?style=for-the-badge&logo=laravel&logoColor=white) ![Next JS](https://img.shields.io/badge/Next-black?style=for-the-badge&logo=next.js&logoColor=white) ![NodeJS](https://img.shields.io/badge/node.js-6DA55F?style=for-the-badge&logo=node.js&logoColor=white) ![Livewire](https://img.shields.io/badge/livewire-%234e56a6.svg?style=for-the-badge&logo=livewire&logoColor=white) ![Ionic](https://img.shields.io/badge/Ionic-%233880FF.svg?style=for-the-badge&logo=Ionic&logoColor=white) ![Jasmine](https://img.shields.io/badge/jasmine-%238A4182.svg?style=for-the-badge&logo=jasmine&logoColor=white) ![Less](https://img.shields.io/badge/less-2B4C80?style=for-the-badge&logo=less&logoColor=white) ![Nodemon](https://img.shields.io/badge/NODEMON-%23323330.svg?style=for-the-badge&logo=nodemon&logoColor=%BBDEAD) ![MUI](https://img.shields.io/badge/MUI-%230081CB.svg?style=for-the-badge&logo=mui&logoColor=white) ![JavaFX](https://img.shields.io/badge/javafx-%23FF0000.svg?style=for-the-badge&logo=javafx&logoColor=white) ![Jinja](https://img.shields.io/badge/jinja-white.svg?style=for-the-badge&logo=jinja&logoColor=black) ![Metero JS](https://img.shields.io/badge/meteorjs-%23d74c4c.svg?style=for-the-badge&logo=meteor&logoColor=white) ![Node-RED](https://img.shields.io/badge/Node--RED-%238F0000.svg?style=for-the-badge&logo=node-red&logoColor=white) ![Nuxt JS](https://img.shields.io/badge/Nuxt-002E3B?style=for-the-badge&logo=nuxt.js&logoColor=#00DC82) ![Mantine](https://img.shields.io/badge/Mantine-ffffff?style=for-the-badge&logo=Mantine&logoColor=339af0) ![Joomla](https://img.shields.io/badge/joomla-%235091CD.svg?style=for-the-badge&logo=joomla&logoColor=white) ![jQuery](https://img.shields.io/badge/jquery-%230769AD.svg?style=for-the-badge&logo=jquery&logoColor=white) ![MaxCompute](https://img.shields.io/badge/MaxCompute-%23FF6701?style=for-the-badge&logo=alibabacloud&logoColor=white) ![Nx](https://img.shields.io/badge/nx-143055?style=for-the-badge&logo=nx&logoColor=white) ![OpenCV](https://img.shields.io/badge/opencv-%23white.svg?style=for-the-badge&logo=opencv&logoColor=white) ![OpenGL](https://img.shields.io/badge/OpenGL-%23FFFFFF.svg?style=for-the-badge&logo=opengl) ![NPM](https://img.shields.io/badge/NPM-%23CB3837.svg?style=for-the-badge&logo=npm&logoColor=white) ![JWT](https://img.shields.io/badge/JWT-black?style=for-the-badge&logo=JSON%20web%20tokens) ![P5js](https://img.shields.io/badge/p5.js-ED225D?style=for-the-badge&logo=p5.js&logoColor=FFFFFF) ![NestJS](https://img.shields.io/badge/nestjs-%23E0234E.svg?style=for-the-badge&logo=nestjs&logoColor=white) ![Radix UI](https://img.shields.io/badge/radix%20ui-161618.svg?style=for-the-badge&logo=radix-ui&logoColor=white) ![Redux](https://img.shields.io/badge/redux-%23593d88.svg?style=for-the-badge&logo=redux&logoColor=white) ![SolidJS](https://img.shields.io/badge/SolidJS-2c4f7c?style=for-the-badge&logo=solid&logoColor=c8c9cb) ![Socket.io](https://img.shields.io/badge/Socket.io-black?style=for-the-badge&logo=socket.io&badgeColor=010101) ![React Hook Form](https://img.shields.io/badge/React%20Hook%20Form-%23EC5990.svg?style=for-the-badge&logo=reacthookform&logoColor=white) ![RabbitMQ](https://img.shields.io/badge/rabbitmq-FF6600?style=for-the-badge&logo=rabbitmq&logoColor=white) ![ROS](https://img.shields.io/badge/ros-%230A0FF9.svg?style=for-the-badge&logo=ros&logoColor=white) ![Quasar](https://img.shields.io/badge/Quasar-16B7FB?style=for-the-badge&logo=quasar&logoColor=black) ![Quarkus](https://img.shields.io/badge/quarkus-%234794EB.svg?style=for-the-badge&logo=quarkus&logoColor=white) ![Qt](https://img.shields.io/badge/Qt-%23217346.svg?style=for-the-badge&logo=Qt&logoColor=white) ![Pug](https://img.shields.io/badge/Pug-FFF?style=for-the-badge&logo=pug&logoColor=A86454) ![PNPM](https://img.shields.io/badge/pnpm-%234a4a4a.svg?style=for-the-badge&logo=pnpm&logoColor=f69220) ![Phoenix Framework](https://img.shields.io/badge/phoenixframework-%23FD4F00.svg?style=for-the-badge&logo=phoenixframework&logoColor=black) ![Rails](https://img.shields.io/badge/rails-%23CC0000.svg?style=for-the-badge&logo=ruby-on-rails&logoColor=white) ![RayLib](https://img.shields.io/badge/RAYLIB-FFFFFF?style=for-the-badge&logo=raylib&logoColor=black) ![Remix](https://img.shields.io/badge/remix-%23000.svg?style=for-the-badge&logo=remix&logoColor=white) ![Spring](https://img.shields.io/badge/spring-%236DB33F.svg?style=for-the-badge&logo=spring&logoColor=white) ![TailwindCSS](https://img.shields.io/badge/tailwindcss-%2338B2AC.svg?style=for-the-badge&logo=tailwind-css&logoColor=white) ![Tauri](https://img.shields.io/badge/tauri-%2324C8DB.svg?style=for-the-badge&logo=tauri&logoColor=%23FFFFFF) ![Strapi](https://img.shields.io/badge/strapi-%232E7EEA.svg?style=for-the-badge&logo=strapi&logoColor=white) ![RollupJS](https://img.shields.io/badge/RollupJS-ef3335?style=for-the-badge&logo=rollup.js&logoColor=white) ![React](https://img.shields.io/badge/react-%2320232a.svg?style=for-the-badge&logo=react&logoColor=%2361DAFB) ![RxDB](https://img.shields.io/badge/rxdb-%238D1F89.svg?style=for-the-badge&logo=rxdb&logoColor=white) ![React Native](https://img.shields.io/badge/react_native-%2320232a.svg?style=for-the-badge&logo=react&logoColor=%2361DAFB) ![SASS](https://img.shields.io/badge/SASS-hotpink.svg?style=for-the-badge&logo=SASS&logoColor=white) ![RxJS](https://img.shields.io/badge/rxjs-%23B7178C.svg?style=for-the-badge&logo=reactivex&logoColor=white) ![React Query](https://img.shields.io/badge/-React%20Query-FF4154?style=for-the-badge&logo=react%20query&logoColor=white) ![React Router](https://img.shields.io/badge/React_Router-CA4245?style=for-the-badge&logo=react-router&logoColor=white) ![Snowflake](https://img.shields.io/badge/snowflake-%2329B5E8.svg?style=for-the-badge&logo=snowflake&logoColor=white) ![Semantic UI React](https://img.shields.io/badge/Semantic%20UI%20React-%2335BDB2.svg?style=for-the-badge&logo=SemanticUIReact&logoColor=white) ![Symfony](https://img.shields.io/badge/symfony-%23000000.svg?style=for-the-badge&logo=symfony&logoColor=white) ![SvelteKit](https://img.shields.io/badge/sveltekit-%23ff3e00.svg?style=for-the-badge&logo=svelte&logoColor=white) ![Svelte](https://img.shields.io/badge/svelte-%23f1413d.svg?style=for-the-badge&logo=svelte&logoColor=white) ![Streamlit](https://img.shields.io/badge/Streamlit-%23FE4B4B.svg?style=for-the-badge&logo=streamlit&logoColor=white) ![Styled Components](https://img.shields.io/badge/styled--components-DB7093?style=for-the-badge&logo=styled-components&logoColor=white) ![Stylus](https://img.shields.io/badge/stylus-%23ff6347.svg?style=for-the-badge&logo=stylus&logoColor=white) ![UnoCSS](https://img.shields.io/badge/unocss-333333.svg?style=for-the-badge&logo=unocss&logoColor=white) ![Three js](https://img.shields.io/badge/threejs-black?style=for-the-badge&logo=three.js&logoColor=white) ![Vuetify](https://img.shields.io/badge/Vuetify-1867C0?style=for-the-badge&logo=vuetify&logoColor=AEDDFF) ![WebGL](https://img.shields.io/badge/WebGL-990000?logo=webgl&logoColor=white&style=for-the-badge) ![Webpack](https://img.shields.io/badge/webpack-%238DD6F9.svg?style=for-the-badge&logo=webpack&logoColor=black) ![Thymeleaf](https://img.shields.io/badge/Thymeleaf-%23005C0F.svg?style=for-the-badge&logo=Thymeleaf&logoColor=white) ![Badge Name](https://img.shields.io/badge/tRPC-%232596BE.svg?style=for-the-badge&logo=tRPC&logoColor=white) ![Type-graphql](https://img.shields.io/badge/-TypeGraphQL-%23C04392?style=for-the-badge) ![Vite](https://img.shields.io/badge/vite-%23646CFF.svg?style=for-the-badge&logo=vite&logoColor=white) ![Vue.js](https://img.shields.io/badge/vue.js-%2335495e.svg?style=for-the-badge&logo=vuedotjs&logoColor=%234FC08D) ![Yarn](https://img.shields.io/badge/yarn-%232C8EBB.svg?style=for-the-badge&logo=yarn&logoColor=white) ![Xamarin](https://img.shields.io/badge/Xamarin-3199DC?style=for-the-badge&logo=xamarin&logoColor=white) ![WordPress](https://img.shields.io/badge/WordPress-%23117AC9.svg?style=for-the-badge&logo=WordPress&logoColor=white) ![Windicss](https://img.shields.io/badge/windicss-48B0F1.svg?style=for-the-badge&logo=windi-css&logoColor=white) ![Web3.js](https://img.shields.io/badge/web3.js-F16822?style=for-the-badge&logo=web3.js&logoColor=white) ![Apache](https://img.shields.io/badge/apache-%23D42029.svg?style=for-the-badge&logo=apache&logoColor=white) ![Apache Airflow](https://img.shields.io/badge/Apache%20Airflow-017CEE?style=for-the-badge&logo=Apache%20Airflow&logoColor=white) ![Apache Ant](https://img.shields.io/badge/Apache%20Ant-A81C7D?style=for-the-badge&logo=Apache%20Ant&logoColor=white) ![Apache Flink](https://img.shields.io/badge/Apache%20Flink-E6526F?style=for-the-badge&logo=Apache%20Flink&logoColor=white) ![Apache Maven](https://img.shields.io/badge/Apache%20Maven-C71A36?style=for-the-badge&logo=Apache%20Maven&logoColor=white) ![Apache Tomcat](https://img.shields.io/badge/apache%20tomcat-%23F8DC75.svg?style=for-the-badge&logo=apache-tomcat&logoColor=black) ![Gunicorn](https://img.shields.io/badge/gunicorn-%298729.svg?style=for-the-badge&logo=gunicorn&logoColor=white) ![Jenkins](https://img.shields.io/badge/jenkins-%232C5263.svg?style=for-the-badge&logo=jenkins&logoColor=white) ![Nginx](https://img.shields.io/badge/nginx-%23009639.svg?style=for-the-badge&logo=nginx&logoColor=white) ![AmazonDynamoDB](https://img.shields.io/badge/Amazon%20DynamoDB-4053D6?style=for-the-badge&logo=Amazon%20DynamoDB&logoColor=white) ![Firebase](https://img.shields.io/badge/firebase-a08021?style=for-the-badge&logo=firebase&logoColor=ffcd34) ![Appwrite](https://img.shields.io/badge/Appwrite-%23FD366E.svg?style=for-the-badge&logo=appwrite&logoColor=white) ![Arango DB](https://img.shields.io/badge/ArangoDB-DDE072?style=for-the-badge&logo=arangodb&logoColor=white) ![ApacheCassandra](https://img.shields.io/badge/cassandra-%231287B1.svg?style=for-the-badge&logo=apache-cassandra&logoColor=white) ![CockroachLabs](https://img.shields.io/badge/Cockroach%20Labs-6933FF?style=for-the-badge&logo=Cockroach%20Labs&logoColor=white) ![Couchbase](https://img.shields.io/badge/Couchbase-EA2328?style=for-the-badge&logo=couchbase&logoColor=white) ![CrateDB](https://img.shields.io/badge/CrateDB-009DC7?style=for-the-badge&logo=CrateDB&logoColor=white) ![Neo4J](https://img.shields.io/badge/Neo4j-008CC1?style=for-the-badge&logo=neo4j&logoColor=white) ![MySQL](https://img.shields.io/badge/mysql-4479A1.svg?style=for-the-badge&logo=mysql&logoColor=white) ![MongoDB](https://img.shields.io/badge/MongoDB-%234ea94b.svg?style=for-the-badge&logo=mongodb&logoColor=white) ![MicrosoftSQLServer](https://img.shields.io/badge/Microsoft%20SQL%20Server-CC2927?style=for-the-badge&logo=microsoft%20sql%20server&logoColor=white) ![MusicBrainz](https://img.shields.io/badge/Musicbrainz-EB743B?style=for-the-badge&logo=musicbrainz&logoColor=BA478F) ![MariaDB](https://img.shields.io/badge/MariaDB-003545?style=for-the-badge&logo=mariadb&logoColor=white) ![InfluxDB](https://img.shields.io/badge/InfluxDB-22ADF6?style=for-the-badge&logo=InfluxDB&logoColor=white) ![PlanetScale](https://img.shields.io/badge/planetscale-%23000000.svg?style=for-the-badge&logo=planetscale&logoColor=white) ![PocketBase](https://img.shields.io/badge/pocketbase-%23b8dbe4.svg?style=for-the-badge&logo=Pocketbase&logoColor=black) ![Postgres](https://img.shields.io/badge/postgres-%23316192.svg?style=for-the-badge&logo=postgresql&logoColor=white) ![SurrealDB](https://img.shields.io/badge/SurrealDB-FF00A0?style=for-the-badge&logo=surrealdb&logoColor=white) ![Teradata](https://img.shields.io/badge/Teradata-F37440?style=for-the-badge&logo=teradata&logoColor=white) ![Realm](https://img.shields.io/badge/Realm-39477F?style=for-the-badge&logo=realm&logoColor=white) ![Hibernate](https://img.shields.io/badge/Hibernate-59666C?style=for-the-badge&logo=Hibernate&logoColor=white) ![Prisma](https://img.shields.io/badge/Prisma-3982CE?style=for-the-badge&logo=Prisma&logoColor=white) ![Redis](https://img.shields.io/badge/redis-%23DD0031.svg?style=for-the-badge&logo=redis&logoColor=white) ![Single Store](https://img.shields.io/badge/Single%20Store-AA00FF?style=for-the-badge&logo=singlestore&logoColor=white) ![SQLite](https://img.shields.io/badge/sqlite-%2307405e.svg?style=for-the-badge&logo=sqlite&logoColor=white) ![Supabase](https://img.shields.io/badge/Supabase-3ECF8E?style=for-the-badge&logo=supabase&logoColor=white) ![Quill](https://img.shields.io/badge/Quill-52B0E7?style=for-the-badge&logo=apache&logoColor=white) ![Sequelize](https://img.shields.io/badge/Sequelize-52B0E7?style=for-the-badge&logo=Sequelize&logoColor=white) ![Adobe](https://img.shields.io/badge/adobe-%23FF0000.svg?style=for-the-badge&logo=adobe&logoColor=white) ![Adobe Acrobat Reader](https://img.shields.io/badge/Adobe%20Acrobat%20Reader-EC1C24.svg?style=for-the-badge&logo=Adobe%20Acrobat%20Reader&logoColor=white) ![Adobe After Effects](https://img.shields.io/badge/Adobe%20After%20Effects-9999FF.svg?style=for-the-badge&logo=Adobe%20After%20Effects&logoColor=white) ![Adobe Audition](https://img.shields.io/badge/Adobe%20Audition-9999FF.svg?style=for-the-badge&logo=Adobe%20Audition&logoColor=white) ![Adobe Creative Cloud](https://img.shields.io/badge/Adobe%20Creative%20Cloud-DA1F26.svg?style=for-the-badge&logo=Adobe%20Creative%20Cloud&logoColor=white) ![Adobe Lightroom](https://img.shields.io/badge/Adobe%20Lightroom-31A8FF.svg?style=for-the-badge&logo=Adobe%20Lightroom&logoColor=white) ![Adobe InDesign](https://img.shields.io/badge/Adobe%20InDesign-49021F?style=for-the-badge&logo=adobeindesign&logoColor=FF3366) ![Adobe Illustrator](https://img.shields.io/badge/adobe%20illustrator-%23FF9A00.svg?style=for-the-badge&logo=adobe%20illustrator&logoColor=white) ![Adobe Fonts](https://img.shields.io/badge/Adobe%20Fonts-000B1D.svg?style=for-the-badge&logo=Adobe%20Fonts&logoColor=white) ![Adobe Dreamweaver](https://img.shields.io/badge/Adobe%20Dreamweaver-FF61F6.svg?style=for-the-badge&logo=Adobe%20Dreamweaver&logoColor=white) ![Adobe Lightroom Classic](https://img.shields.io/badge/Adobe%20Lightroom%20Classic-31A8FF.svg?style=for-the-badge&logo=Adobe%20Lightroom%20Classic&logoColor=white) ![Affinity Photo](https://img.shields.io/badge/affinityphoto-%237E4DD2.svg?style=for-the-badge&logo=affinity-photo&logoColor=white) ![Affinity Designer](https://img.shields.io/badge/affinity%20desginer-%231B72BE.svg?style=for-the-badge&logo=affinity-designer&logoColor=white) ![Aseprite](https://img.shields.io/badge/Aseprite-FFFFFF?style=for-the-badge&logo=Aseprite&logoColor=#7D929E) ![Adobe XD](https://img.shields.io/badge/Adobe%20XD-470137?style=for-the-badge&logo=Adobe%20XD&logoColor=#FF61F6) ![Adobe Premiere Pro](https://img.shields.io/badge/Adobe%20Premiere%20Pro-9999FF.svg?style=for-the-badge&logo=Adobe%20Premiere%20Pro&logoColor=white) ![Adobe Photoshop](https://img.shields.io/badge/adobe%20photoshop-%2331A8FF.svg?style=for-the-badge&logo=adobe%20photoshop&logoColor=white) ![Blender](https://img.shields.io/badge/blender-%23F5792A.svg?style=for-the-badge&logo=blender&logoColor=white) ![Inkscape](https://img.shields.io/badge/Inkscape-e0e0e0?style=for-the-badge&logo=inkscape&logoColor=080A13) ![Invision](https://img.shields.io/badge/invision-FF3366?style=for-the-badge&logo=invision&logoColor=white) ![Krita](https://img.shields.io/badge/Krita-203759?style=for-the-badge&logo=krita&logoColor=EEF37B) ![Canva](https://img.shields.io/badge/Canva-%2300C4CC.svg?style=for-the-badge&logo=Canva&logoColor=white) ![Clip Studio Paint](https://img.shields.io/badge/ClipStudioPaint-%23CFD3D3.svg?style=for-the-badge&logo=ClipStudioPaint&logoColor=white) ![Proto.io](https://img.shields.io/badge/Proto.io-161637?style=for-the-badge&logo=proto.io&logoColor=00e5ff) ![Rhinoceros](https://img.shields.io/badge/Rhinoceros-801010?style=for-the-badge&logo=rhinoceros&logoColor=white) ![Dribbble](https://img.shields.io/badge/Dribbble-EA4C89?style=for-the-badge&logo=dribbble&logoColor=white) ![Sketch](https://img.shields.io/badge/Sketch-FFB387?style=for-the-badge&logo=sketch&logoColor=black) ![Figma](https://img.shields.io/badge/figma-%23F24E1E.svg?style=for-the-badge&logo=figma&logoColor=white) ![Sketch Up](https://img.shields.io/badge/SketchUp-005F9E?style=for-the-badge&logo=sketchup&logoColor=white) ![Framer](https://img.shields.io/badge/Framer-black?style=for-the-badge&logo=framer&logoColor=blue) ![Gimp](https://img.shields.io/badge/Gimp-657D8B?style=for-the-badge&logo=gimp&logoColor=FFFFFF) ![Storybook](https://img.shields.io/badge/-Storybook-FF4785?style=for-the-badge&logo=storybook&logoColor=white) ![Keras](https://img.shields.io/badge/Keras-%23D00000.svg?style=for-the-badge&logo=Keras&logoColor=white) ![Matplotlib](https://img.shields.io/badge/Matplotlib-%23ffffff.svg?style=for-the-badge&logo=Matplotlib&logoColor=black) ![mlflow](https://img.shields.io/badge/mlflow-%23d9ead3.svg?style=for-the-badge&logo=numpy&logoColor=blue) ![NumPy](https://img.shields.io/badge/numpy-%23013243.svg?style=for-the-badge&logo=numpy&logoColor=white) ![Pandas](https://img.shields.io/badge/pandas-%23150458.svg?style=for-the-badge&logo=pandas&logoColor=white) ![Plotly](https://img.shields.io/badge/Plotly-%233F4F75.svg?style=for-the-badge&logo=plotly&logoColor=white) ![PyTorch](https://img.shields.io/badge/PyTorch-%23EE4C2C.svg?style=for-the-badge&logo=PyTorch&logoColor=white) ![scikit-learn](https://img.shields.io/badge/scikit--learn-%23F7931E.svg?style=for-the-badge&logo=scikit-learn&logoColor=white) ![Scipy](https://img.shields.io/badge/SciPy-%230C55A5.svg?style=for-the-badge&logo=scipy&logoColor=%white) ![TensorFlow](https://img.shields.io/badge/TensorFlow-%23FF6F00.svg?style=for-the-badge&logo=TensorFlow&logoColor=white) ![CircleCI](https://img.shields.io/badge/circleci-%23161616.svg?style=for-the-badge&logo=circleci&logoColor=white) ![Octopus Deploy](https://img.shields.io/badge/octopus%20deploy-0D80D8?style=for-the-badge&logo=octopusdeploy&logoColor=white) ![ChipperCI](https://img.shields.io/badge/chipperci-1e394e.svg?style=for-the-badge&logo=chipperci&logoColor=white) ![CloudBees](https://img.shields.io/badge/CloudBees-1997B5&?logo=cloudbees&logoColor=white&style=for-the-badge) ![Apache Subversion](https://img.shields.io/badge/subversion-%23809CC9.svg?style=for-the-badge&logo=subversion&logoColor=white) ![GitLab](https://img.shields.io/badge/gitlab-%23181717.svg?style=for-the-badge&logo=gitlab&logoColor=white) ![Fastlane](https://img.shields.io/badge/fastlane-%2382bd4e.svg?style=for-the-badge&logo=fastlane&logoColor=black) ![GitLab CI](https://img.shields.io/badge/gitlab%20CI-%23181717.svg?style=for-the-badge&logo=gitlab&logoColor=white) ![GitHub Actions](https://img.shields.io/badge/github%20actions-%232671E5.svg?style=for-the-badge&logo=githubactions&logoColor=white) ![TeamCity](https://img.shields.io/badge/teamcity-000000.svg?style=for-the-badge&logo=teamcity&logoColor=white) ![TravisCI](https://img.shields.io/badge/travis%20ci-%232B2F33.svg?style=for-the-badge&logo=travis&logoColor=white) ![GitHub](https://img.shields.io/badge/github-%23121011.svg?style=for-the-badge&logo=github&logoColor=white) ![Gitee](https://img.shields.io/badge/Gitee-C71D23?style=for-the-badge&logo=gitee&logoColor=white) ![Gitea](https://img.shields.io/badge/Gitea-34495E?style=for-the-badge&logo=gitea&logoColor=5D9425) ![Git](https://img.shields.io/badge/git-%23F05033.svg?style=for-the-badge&logo=git&logoColor=white) ![Forgejo](https://img.shields.io/badge/forgejo-%23FB923C.svg?style=for-the-badge&logo=forgejo&logoColor=white) ![Bitbucket](https://img.shields.io/badge/bitbucket-%230047B3.svg?style=for-the-badge&logo=bitbucket&logoColor=white) ![Gitpod](https://img.shields.io/badge/gitpod-f06611.svg?style=for-the-badge&logo=gitpod&logoColor=white) ![Mercurial](https://img.shields.io/badge/mercurial-999999.svg?style=for-the-badge&logo=mercurial&logoColor=white) ![Perforce Helix](https://img.shields.io/badge/-PERFORCE%20HELIX-404040?style=for-the-badge&logo=Perforce&logoColor=white) ![Cypress](https://img.shields.io/badge/-cypress-%23E5E5E5?style=for-the-badge&logo=cypress&logoColor=058a5e) ![Jasmine](https://img.shields.io/badge/-Jasmine-%238A4182?style=for-the-badge&logo=Jasmine&logoColor=white) ![Jest](https://img.shields.io/badge/-jest-%23C21325?style=for-the-badge&logo=jest&logoColor=white) ![Mocha](https://img.shields.io/badge/-mocha-%238D6748?style=for-the-badge&logo=mocha&logoColor=white) ![Playwright](https://img.shields.io/badge/-playwright-%232EAD33?style=for-the-badge&logo=playwright&logoColor=white) ![Puppeteer](https://img.shields.io/badge/Puppeteer-%2340B5A4.svg?style=for-the-badge&logo=Puppeteer&logoSize=auto&logoColor=black) ![Selenium](https://img.shields.io/badge/-selenium-%43B02A?style=for-the-badge&logo=selenium&logoColor=white) ![Sentry](https://img.shields.io/badge/sentry-%23362D59.svg?style=for-the-badge&logo=sentry&logoColor=white) ![Testing-Library](https://img.shields.io/badge/-TestingLibrary-%23E33332?style=for-the-badge&logo=testing-library&logoColor=white) ![Vitest](https://img.shields.io/badge/-Vitest-252529?style=for-the-badge&logo=vitest&logoColor=FCC72B) ![Airbnb](https://img.shields.io/badge/Airbnb-%23ff5a5f.svg?style=for-the-badge&logo=Airbnb&logoColor=white) ![Alfred](https://img.shields.io/badge/alfred-%235C1F87.svg?style=for-the-badge&logo=alfred) ![Ansible](https://img.shields.io/badge/ansible-%231A1918.svg?style=for-the-badge&logo=ansible&logoColor=white) ![AquaSec](https://img.shields.io/badge/aqua-%231904DA.svg?style=for-the-badge&logo=aqua&logoColor=#0018A8) ![Arduino](https://img.shields.io/badge/-Arduino-00979D?style=for-the-badge&logo=Arduino&logoColor=white) ![Babel](https://img.shields.io/badge/Babel-F9DC3e?style=for-the-badge&logo=babel&logoColor=black) ![Bitwarden](https://img.shields.io/badge/bitwarden-%23175DDC.svg?style=for-the-badge&logo=bitwarden&logoColor=white) ![Cisco](https://img.shields.io/badge/cisco-%23049fd9.svg?style=for-the-badge&logo=cisco&logoColor=black) ![CMake](https://img.shields.io/badge/CMake-%23008FBA.svg?style=for-the-badge&logo=cmake&logoColor=white) ![Gradle](https://img.shields.io/badge/Gradle-02303A.svg?style=for-the-badge&logo=Gradle&logoColor=white) ![FFmpeg](https://shields.io/badge/FFmpeg-%23171717.svg?logo=ffmpeg&style=for-the-badge&labelColor=171717&logoColor=5cb85c) ![ElasticSearch](https://img.shields.io/badge/-ElasticSearch-005571?style=for-the-badge&logo=elasticsearch) ![ESLint](https://img.shields.io/badge/ESLint-4B3263?style=for-the-badge&logo=eslint&logoColor=white) ![Docker](https://img.shields.io/badge/docker-%230db7ed.svg?style=for-the-badge&logo=docker&logoColor=white) ![Crowdin](https://img.shields.io/badge/Crowdin-2E3340.svg?style=for-the-badge&logo=Crowdin&logoColor=white) ![Confluence](https://img.shields.io/badge/confluence-%23172BF4.svg?style=for-the-badge&logo=confluence&logoColor=white) ![CodeCov](https://img.shields.io/badge/codecov-%23ff0077.svg?style=for-the-badge&logo=codecov&logoColor=white) ![Grafana](https://img.shields.io/badge/grafana-%23F46800.svg?style=for-the-badge&logo=grafana&logoColor=white) ![Notion](https://img.shields.io/badge/Notion-%23000000.svg?style=for-the-badge&logo=notion&logoColor=white) ![OpenAPI Specification](https://img.shields.io/badge/openapiinitiative-%23000000.svg?style=for-the-badge&logo=openapiinitiative&logoColor=white) ![Home Assistant](https://img.shields.io/badge/home%20assistant-%2341BDF5.svg?style=for-the-badge&logo=home-assistant&logoColor=white) ![Homebridge](https://img.shields.io/badge/homebridge-%23491F59.svg?style=for-the-badge&logo=homebridge&logoColor=white) ![Jellyfin](https://img.shields.io/badge/jellyfin-%23000B25.svg?style=for-the-badge&logo=Jellyfin&logoColor=00A4DC) ![Jira](https://img.shields.io/badge/jira-%230A0FFF.svg?style=for-the-badge&logo=jira&logoColor=white) ![Kubernetes](https://img.shields.io/badge/kubernetes-%23326ce5.svg?style=for-the-badge&logo=kubernetes&logoColor=white) ![Meta](https://img.shields.io/badge/Meta-%230467DF.svg?style=for-the-badge&logo=Meta&logoColor=white) ![Mosquitto](https://img.shields.io/badge/mosquitto-%233C5280.svg?style=for-the-badge&logo=eclipsemosquitto&logoColor=white) ![Plex](https://img.shields.io/badge/plex-%23E5A00D.svg?style=for-the-badge&logo=plex&logoColor=white) ![PlatformIO](https://img.shields.io/badge/PlatformIO-%23222.svg?style=for-the-badge&logo=platformio&logoColor=%23f5822a) ![Pi-Hole](https://img.shields.io/badge/pihole-%2396060C.svg?style=for-the-badge&logo=pi-hole&logoColor=white) ![Packer](https://img.shields.io/badge/packer-%23E7EEF0.svg?style=for-the-badge&logo=packer&logoColor=%2302A8EF) ![OpenTelemetry](https://img.shields.io/badge/OpenTelemetry-FFFFFF?&style=for-the-badge&logo=opentelemetry&logoColor=black) ![OpenSea](https://img.shields.io/badge/OpenSea-%232081E2.svg?style=for-the-badge&logo=opensea&logoColor=white) ![Portfolio](https://img.shields.io/badge/Portfolio-%23000000.svg?style=for-the-badge&logo=firefox&logoColor=#FF7139) ![SonarLint](https://img.shields.io/badge/SonarLint-CB2029?style=for-the-badge&logo=SONARLINT&logoColor=white) ![Twilio](https://img.shields.io/badge/Twilio-F22F46?style=for-the-badge&logo=Twilio&logoColor=white) ![Postman](https://img.shields.io/badge/Postman-FF6C37?style=for-the-badge&logo=postman&logoColor=white) ![SonarQube](https://img.shields.io/badge/SonarQube-black?style=for-the-badge&logo=sonarqube&logoColor=4E9BCD) ![Power Bi](https://img.shields.io/badge/power_bi-F2C811?style=for-the-badge&logo=powerbi&logoColor=black) ![Prettier](https://img.shields.io/badge/prettier-%23F7B93E.svg?style=for-the-badge&logo=prettier&logoColor=black) ![Prezi](https://img.shields.io/badge/Prezi-%23000000.svg?style=for-the-badge&logo=Prezi&logoColor=white) ![Prometheus](https://img.shields.io/badge/Prometheus-E6522C?style=for-the-badge&logo=Prometheus&logoColor=white) ![Rancher](https://img.shields.io/badge/rancher-%230075A8.svg?style=for-the-badge&logo=rancher&logoColor=white) ![Raspberry Pi](https://img.shields.io/badge/-Raspberry_Pi-C51A4A?style=for-the-badge&logo=Raspberry-Pi) ![Trello](https://img.shields.io/badge/Trello-%23026AA7.svg?style=for-the-badge&logo=Trello&logoColor=white) ![Terraform](https://img.shields.io/badge/terraform-%235835CC.svg?style=for-the-badge&logo=terraform&logoColor=white) ![TOR](https://img.shields.io/badge/tor-%237E4798.svg?style=for-the-badge&logo=tor-project&logoColor=white) ![Tampermonkey](https://img.shields.io/badge/tampermonkey-%2300485B.svg?style=for-the-badge&logo=tampermonkey&logoColor=white) ![Swagger](https://img.shields.io/badge/-Swagger-%23Clojure?style=for-the-badge&logo=swagger&logoColor=white) ![Splunk](https://img.shields.io/badge/splunk-%23000000.svg?style=for-the-badge&logo=splunk&logoColor=white) ![Ubiquiti](https://img.shields.io/badge/ubiquiti-%230559C9.svg?style=for-the-badge&logo=ubiquiti&logoColor=white) ![Battle.net](https://img.shields.io/badge/battle.net-%2300AEFF.svg?style=for-the-badge&logo=battle.net&logoColor=white) ![Uber](https://img.shields.io/badge/Uber-%23000000.svg?style=for-the-badge&logo=Uber&logoColor=white) ![Bevy](https://img.shields.io/badge/bevy-%23232326.svg?style=for-the-badge&logo=bevy&logoColor=white) ![EA](https://img.shields.io/badge/ea-%23000000.svg?style=for-the-badge&logo=ea&logoColor=white) ![Epic Games](https://img.shields.io/badge/epicgames-%23313131.svg?style=for-the-badge&logo=epicgames&logoColor=white) ![Vagrant](https://img.shields.io/badge/vagrant-%231563FF.svg?style=for-the-badge&logo=vagrant&logoColor=white) ![Wireguard](https://img.shields.io/badge/wireguard-%2388171A.svg?style=for-the-badge&logo=wireguard&logoColor=white) ![XFCE](https://img.shields.io/badge/XFCE-%232284F2.svg?style=for-the-badge&logo=xfce&logoColor=white) ![Zigbee](https://img.shields.io/badge/zigbee-%23EB0443.svg?style=for-the-badge&logo=zigbee&logoColor=white) ![Analogue](https://img.shields.io/badge/Analogue-1A1A1A?style=for-the-badge&logo=Analogue&logoColor=white) ![OpenGL](https://img.shields.io/badge/OpenGL-white?logo=OpenGL&style=for-the-badge) ![AMD](https://img.shields.io/badge/AMD-%23000000.svg?style=for-the-badge&logo=amd&logoColor=white) ![nVIDIA](https://img.shields.io/badge/nVIDIA-%2376B900.svg?style=for-the-badge&logo=nVIDIA&logoColor=white) ![Unity](https://img.shields.io/badge/unity-%23000000.svg?style=for-the-badge&logo=unity&logoColor=white) ![Ubisoft](https://img.shields.io/badge/Ubisoft-%23F5F5F5.svg?style=for-the-badge&logo=Ubisoft&logoColor=black) ![Itch.io](https://img.shields.io/badge/Itch-%23FF0B34.svg?style=for-the-badge&logo=Itch.io&logoColor=white) ![Humble Bundle](https://img.shields.io/badge/HumbleBundle-%23494F5C.svg?style=for-the-badge&logo=HumbleBundle&logoColor=white) ![Godot Engine](https://img.shields.io/badge/GODOT-%23FFFFFF.svg?style=for-the-badge&logo=godot-engine) ![Riot Games](https://img.shields.io/badge/riotgames-D32936.svg?style=for-the-badge&logo=riotgames&logoColor=white) ![PlayStation Network](https://img.shields.io/badge/PSN-%230070D1.svg?style=for-the-badge&logo=Playstation&logoColor=white) ![Sidequest](https://img.shields.io/badge/sidequest-%23101227.svg?style=for-the-badge&logo=sidequest&logoColor=white) ![Square Enix](https://img.shields.io/badge/SquareEnix-%23ED1C24.svg?style=for-the-badge&logo=SquareEnix&logoColor=white) ![Steam](https://img.shields.io/badge/steam-%23000000.svg?style=for-the-badge&logo=steam&logoColor=white) ![Unreal Engine](https://img.shields.io/badge/unrealengine-%23313131.svg?style=for-the-badge&logo=unrealengine&logoColor=white) ![Xbox](https://img.shields.io/badge/xbox-%23107C10.svg?style=for-the-badge&logo=xbox&logoColor=white)
# 📊 GitHub Stats:
![](https://github-readme-stats.vercel.app/api?username=Sauraysuraj99&theme=dark&hide_border=false&include_all_commits=false&count_private=false)<br/>
![](https://nirzak-streak-stats.vercel.app/?user=Sauraysuraj99&theme=dark&hide_border=false)<br/>
![](https://github-readme-stats.vercel.app/api/top-langs/?username=Sauraysuraj99&theme=dark&hide_border=false&include_all_commits=false&count_private=false&layout=compact)

---
[![](https://visitcount.itsvg.in/api?id=Sauraysuraj99&icon=0&color=0)](https://visitcount.itsvg.in)

<!-- Proudly created with GPRM ( https://gprm.itsvg.in ) -->


<p align="center">
<img src="https://streak-stats.demolab.com?user=Sauraysuraj99&theme=radical" alt="streak" />
</p>


### 🌐 Connect With Me

<p align="left">
<a href="https://joyful-pixie-ffdc6f.netlify.app/" target="blank">🌐 Portfolio</a> |
<a href="https://linkedin.com/in/your-link" target="blank">💼 LinkedIn</a> |
<a href="https://instagram.com/your-link" target="blank">📸 Instagram</a> |
<a href="https://facebook.com/your-link" target="blank">📘 Facebook</a> |
<a href="https://snapchat.com/add/your-link" target="blank">👻 Snapchat</a>
</p>
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0, user-scalable=no">
  <title>Suraj Kumar | Java Full Stack Developer | Animated Portfolio</title>
  <!-- Google Fonts & Font Awesome -->
  <link href="https://fonts.googleapis.com/css2?family=Inter:opsz,wght@14..32,300;14..32,400;14..32,600;14..32,700;14..32,800&family=JetBrains+Mono:wght@400;500&display=swap" rel="stylesheet">
  <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.0.0-beta3/css/all.min.css">
  <style>
    * {
      margin: 0;
      padding: 0;
      box-sizing: border-box;
    }

    body {
      background: #0a0c10;
      font-family: 'Inter', sans-serif;
      color: #edeff2;
      overflow-x: hidden;
      line-height: 1.5;
    }

    /* animated gradient mesh background */
    .animated-bg {
      position: fixed;
      top: 0;
      left: 0;
      width: 100%;
      height: 100%;
      z-index: -2;
      background: radial-gradient(circle at 20% 30%, rgba(25, 30, 45, 0.9), #07090e);
    }

    .animated-bg::before {
      content: "";
      position: absolute;
      width: 200%;
      height: 200%;
      top: -50%;
      left: -50%;
      background: radial-gradient(circle at 40% 50%, rgba(100, 80, 200, 0.18), transparent 70%);
      animation: slowDrift 28s infinite alternate ease-in-out;
      pointer-events: none;
    }

    .animated-bg::after {
      content: "";
      position: absolute;
      width: 150%;
      height: 150%;
      top: -30%;
      left: -30%;
      background: radial-gradient(ellipse at 80% 70%, rgba(0, 200, 180, 0.08), transparent 60%);
      animation: slowDriftReverse 32s infinite alternate;
      pointer-events: none;
    }

    @keyframes slowDrift {
      0% { transform: translate(0%, 0%) rotate(0deg); opacity: 0.4; }
      100% { transform: translate(4%, 6%) rotate(4deg); opacity: 0.8; }
    }

    @keyframes slowDriftReverse {
      0% { transform: translate(0%, 0%) rotate(0deg); }
      100% { transform: translate(-5%, 3%) rotate(-3deg); }
    }

    /* floating particles (code-like) */
    .code-particles {
      position: fixed;
      top: 0;
      left: 0;
      width: 100%;
      height: 100%;
      z-index: -1;
      pointer-events: none;
      overflow: hidden;
    }

    .particle {
      position: absolute;
      font-family: 'JetBrains Mono', monospace;
      font-size: 0.9rem;
      opacity: 0.2;
      color: #5f7f9e;
      white-space: nowrap;
      user-select: none;
      animation: floatParticle linear infinite;
    }

    @keyframes floatParticle {
      0% {
        transform: translateY(100vh) translateX(0) rotate(0deg);
        opacity: 0;
      }
      20% { opacity: 0.3; }
      80% { opacity: 0.3; }
      100% {
        transform: translateY(-20vh) translateX(40px) rotate(8deg);
        opacity: 0;
      }
    }

    /* layout */
    .container {
      max-width: 1300px;
      margin: 0 auto;
      padding: 2rem 2rem 4rem;
    }

    /* hero section */
    .hero {
      min-height: 90vh;
      display: flex;
      flex-direction: column;
      justify-content: center;
      align-items: center;
      text-align: center;
      gap: 1.2rem;
      padding: 2rem 1rem;
    }

    .avatar-wrapper {
      margin-bottom: 1rem;
      position: relative;
    }

    .avatar {
      width: 140px;
      height: 140px;
      border-radius: 50%;
      border: 3px solid rgba(0, 210, 200, 0.6);
      box-shadow: 0 20px 35px -10px rgba(0,0,0,0.5), 0 0 0 6px rgba(0, 210, 200, 0.1);
      transition: transform 0.3s ease;
      object-fit: cover;
    }

    .avatar:hover {
      transform: scale(1.02);
    }

    .glow-text {
      background: linear-gradient(135deg, #C0F2FF, #A5D8FF, #7B9EFF);
      background-clip: text;
      -webkit-background-clip: text;
      color: transparent;
      font-weight: 800;
    }

    h1 {
      font-size: 3.2rem;
      font-weight: 800;
      letter-spacing: -0.02em;
    }

    .typed-container {
      font-size: 1.6rem;
      font-weight: 500;
      min-height: 4rem;
      color: #bfd9ff;
    }

    .highlight {
      color: #6fe5ff;
      border-bottom: 2px solid #3aa8ff;
      display: inline-block;
    }

    .tagline {
      max-width: 650px;
      color: #b0bbd4;
      font-size: 1.1rem;
      margin: 1rem 0;
    }

    .btn-group {
      display: flex;
      gap: 1.2rem;
      flex-wrap: wrap;
      justify-content: center;
      margin-top: 1.2rem;
    }

    .btn {
      padding: 0.8rem 2rem;
      border-radius: 60px;
      font-weight: 600;
      text-decoration: none;
      transition: all 0.25s ease;
      display: inline-flex;
      align-items: center;
      gap: 0.6rem;
      background: rgba(20, 30, 45, 0.7);
      backdrop-filter: blur(4px);
      border: 0.5px solid rgba(100, 150, 250, 0.3);
      color: #eef4ff;
    }

    .btn-primary {
      background: linear-gradient(95deg, #2a6fdb, #3b82f6);
      border: none;
      box-shadow: 0 8px 18px rgba(59,130,246,0.25);
    }

    .btn-primary:hover {
      transform: translateY(-3px);
      background: linear-gradient(95deg, #3b7beb, #4f93ff);
      box-shadow: 0 15px 25px -8px rgba(59,130,246,0.4);
    }

    .btn-outline:hover {
      background: rgba(59,130,246,0.2);
      border-color: #3b82f6;
      transform: translateY(-2px);
    }

    /* section styles */
    section {
      margin: 5rem 0;
    }

    .section-title {
      font-size: 2rem;
      font-weight: 700;
      margin-bottom: 2rem;
      display: flex;
      align-items: center;
      gap: 12px;
    }

    .section-title i {
      font-size: 1.8rem;
      background: linear-gradient(145deg, #6ee7ff, #3b82f6);
      background-clip: text;
      -webkit-background-clip: text;
      color: transparent;
    }

    .tech-grid {
      display: flex;
      flex-wrap: wrap;
      gap: 1rem;
      margin-top: 1.5rem;
    }

    .tech-badge {
      background: #11161f;
      padding: 0.6rem 1.3rem;
      border-radius: 40px;
      font-size: 0.9rem;
      font-weight: 500;
      backdrop-filter: blur(4px);
      border: 1px solid #2a3342;
      transition: all 0.2s;
      display: inline-flex;
      align-items: center;
      gap: 8px;
    }

    .tech-badge i {
      font-size: 1rem;
      color: #3b82f6;
    }

    .tech-badge:hover {
      border-color: #3b82f6;
      transform: translateY(-3px);
      background: #0f1825;
    }

    /* repo cards animation */
    .repo-grid {
      display: grid;
      grid-template-columns: repeat(auto-fill, minmax(300px, 1fr));
      gap: 1.6rem;
      margin-top: 2rem;
    }

    .repo-card {
      background: rgba(15, 22, 33, 0.65);
      backdrop-filter: blur(6px);
      border-radius: 24px;
      padding: 1.5rem;
      border: 1px solid rgba(70, 130, 200, 0.2);
      transition: all 0.3s cubic-bezier(0.2, 0.9, 0.4, 1.1);
      animation: fadeUp 0.6s ease backwards;
    }

    .repo-card:hover {
      transform: translateY(-5px) scale(1.01);
      border-color: rgba(59,130,246,0.5);
      background: rgba(20, 30, 48, 0.8);
      box-shadow: 0 25px 35px -12px rgba(0,0,0,0.4);
    }

    .repo-name {
      font-weight: 700;
      font-size: 1.25rem;
      display: flex;
      align-items: center;
      gap: 8px;
    }

    .repo-desc {
      font-size: 0.85rem;
      color: #9cb0d0;
      margin: 0.6rem 0 1rem;
      line-height: 1.4;
    }

    .lang-color {
      display: inline-block;
      width: 12px;
      height: 12px;
      border-radius: 50%;
      background: #e34c26;
      margin-right: 6px;
    }

    /* timeline stats */
    .stats-wrap {
      display: flex;
      justify-content: space-between;
      flex-wrap: wrap;
      gap: 2rem;
      background: rgba(12, 18, 28, 0.6);
      border-radius: 2rem;
      padding: 2rem;
      backdrop-filter: blur(8px);
      border: 1px solid #2a3342;
    }

    .stat-item {
      flex: 1;
      text-align: center;
    }

    .stat-number {
      font-size: 2.5rem;
      font-weight: 800;
      background: linear-gradient(135deg, #fff, #8bb5ff);
      background-clip: text;
      -webkit-background-clip: text;
      color: transparent;
    }

    .footer-social {
      display: flex;
      justify-content: center;
      gap: 2rem;
      margin-top: 3rem;
      flex-wrap: wrap;
    }

    .social-link {
      font-size: 1.6rem;
      color: #9aaec9;
      transition: 0.2s;
    }

    .social-link:hover {
      color: #3b82f6;
      transform: translateY(-3px);
    }

    /* animations */
    @keyframes fadeUp {
      from {
        opacity: 0;
        transform: translateY(20px);
      }
      to {
        opacity: 1;
        transform: translateY(0);
      }
    }

    .animate-once {
      animation: fadeUp 0.6s ease forwards;
    }

    /* responsive */
    @media (max-width: 700px) {
      h1 { font-size: 2.2rem; }
      .typed-container { font-size: 1.2rem; }
      .container { padding: 1.5rem; }
      .stats-wrap { flex-direction: column; align-items: center; gap: 1rem; }
    }
  </style>
</head>
<body>

<div class="animated-bg"></div>
<div class="code-particles" id="particlesContainer"></div>

<main class="container">
  <!-- Hero Animation Section -->
  <div class="hero">
    <div class="avatar-wrapper">
      <img class="avatar" src="https://avatars.githubusercontent.com/u/176518497?v=4" alt="Suraj Kumar">
    </div>
    <h1>
      <span class="glow-text">Suraj Kumar</span>
    </h1>
    <div class="typed-container">
      <span id="dynamicRole" class="highlight"></span>
    </div>
    <p class="tagline">
      Java Full Stack Developer · Spring Boot · React · Generative AI Enthusiast <br>
      Building scalable systems & mindful code.
    </p>
    <div class="btn-group">
      <a href="https://github.com/Sauraysuraj99" target="_blank" class="btn btn-primary"><i class="fab fa-github"></i> GitHub</a>
      <a href="https://www.linkedin.com/in/suraj-kumar-168230250/" target="_blank" class="btn btn-outline"><i class="fab fa-linkedin-in"></i> LinkedIn</a>
      <a href="https://radiant-bunny-949c03.netlify.app/" target="_blank" class="btn btn-outline"><i class="fas fa-globe"></i> Portfolio</a>
    </div>
  </div>

  <!-- Tech Stack Section with animation on scroll -->
  <section>
    <div class="section-title">
      <i class="fas fa-code"></i>
      <span>Tech Toolbox</span>
    </div>
    <div class="tech-grid" id="techStack"></div>
  </section>

  <!-- Pinned Repositories (inspired from profile) -->
  <section>
    <div class="section-title">
      <i class="fas fa-star"></i>
      <span>Popular Repositories</span>
    </div>
    <div class="repo-grid" id="repoList"></div>
  </section>

  <!-- GitHub Stats Insight with animated counters -->
  <section>
    <div class="section-title">
      <i class="fas fa-chart-line"></i>
      <span>Dev Pulse</span>
    </div>
    <div class="stats-wrap">
      <div class="stat-item">
        <div class="stat-number" id="repoCount">56</div>
        <div>Public Repos</div>
      </div>
      <div class="stat-item">
        <div class="stat-number" id="followersCount">4</div>
        <div>Followers</div>
      </div>
      <div class="stat-item">
        <div class="stat-number" id="followingCount">10</div>
        <div>Following</div>
      </div>
      <div class="stat-item">
        <div class="stat-number" id="contributionYear">2026</div>
        <div>Active Year</div>
      </div>
    </div>
  </section>

  <!-- Connect Footer -->
  <div class="footer-social">
    <a href="https://github.com/Sauraysuraj99" class="social-link" target="_blank"><i class="fab fa-github"></i></a>
    <a href="https://www.linkedin.com/in/suraj-kumar-168230250/" class="social-link" target="_blank"><i class="fab fa-linkedin-in"></i></a>
    <a href="https://www.instagram.com/suraj.sauray_raj99" class="social-link" target="_blank"><i class="fab fa-instagram"></i></a>
    <a href="https://www.facebook.com/share/19X62owCHf/" class="social-link" target="_blank"><i class="fab fa-facebook-f"></i></a>
    <a href="mailto:sauraysuraj@gmail.com" class="social-link" target="_blank"><i class="fas fa-envelope"></i></a>
  </div>
  <p style="text-align: center; margin-top: 3rem; font-size: 0.75rem; opacity: 0.6;">
    ⚡ Debugging code logically & life mindfully — Suraj Kumar
  </p>
</main>

<script>
  // ----- dynamic typing animation (leading role)
  const roles = [
    "Java Full Stack Developer",
    "Spring Boot & React Architect",
    "Backend Systems Designer",
    "Generative AI Explorer",
    "Open Source Contributor"
  ];
  let roleIndex = 0;
  let charIndex = 0;
  let isDeleting = false;
  const dynamicSpan = document.getElementById("dynamicRole");

  function typeEffect() {
    const currentRole = roles[roleIndex];
    if (isDeleting) {
      dynamicSpan.innerText = currentRole.substring(0, charIndex - 1);
      charIndex--;
      if (charIndex === 0) {
        isDeleting = false;
        roleIndex = (roleIndex + 1) % roles.length;
        setTimeout(typeEffect, 300);
      } else {
        setTimeout(typeEffect, 60);
      }
    } else {
      dynamicSpan.innerText = currentRole.substring(0, charIndex + 1);
      charIndex++;
      if (charIndex === currentRole.length) {
        isDeleting = true;
        setTimeout(typeEffect, 1800);
      } else {
        setTimeout(typeEffect, 90);
      }
    }
  }
  typeEffect();

  // ----- floating code particles (JavaScript, Java, etc)
  const particles = ["{ code; }", "() => {}", "<React />", "SpringBoot", "JDBC", "MySQL", "✨ DevOps", "💻 fullstack", "🚀 deploy", "⚡ microservices", "public static void", "npm start"];
  const particleContainer = document.getElementById("particlesContainer");
  for (let i = 0; i < 38; i++) {
    const particle = document.createElement("div");
    particle.className = "particle";
    const randomText = particles[Math.floor(Math.random() * particles.length)];
    particle.innerText = randomText;
    const size = 0.7 + Math.random() * 0.7;
    particle.style.fontSize = `${size}rem`;
    particle.style.left = `${Math.random() * 100}%`;
    particle.style.animationDuration = `${8 + Math.random() * 15}s`;
    particle.style.animationDelay = `${Math.random() * 15}s`;
    particle.style.opacity = `${0.1 + Math.random() * 0.25}`;
    particleContainer.appendChild(particle);
  }

  // Tech stack data fully aligned with your profile (Java, spring, react, sql, git)
  const techStackList = [
    { name: "Java", icon: "fab fa-java" },
    { name: "Spring Boot", icon: "fas fa-leaf" },
    { name: "Hibernate", icon: "fas fa-database" },
    { name: "JavaScript", icon: "fab fa-js" },
    { name: "React", icon: "fab fa-react" },
    { name: "HTML5/CSS3", icon: "fab fa-html5" },
    { name: "MySQL", icon: "fas fa-database" },
    { name: "MongoDB", icon: "fas fa-leaf" },
    { name: "Git/GitHub", icon: "fab fa-git-alt" },
    { name: "Docker", icon: "fab fa-docker" },
    { name: "REST APIs", icon: "fas fa-plug" },
    { name: "Tailwind CSS", icon: "fas fa-paintbrush" }
  ];

  const techContainer = document.getElementById("techStack");
  techStackList.forEach(tech => {
    const badge = document.createElement("div");
    badge.className = "tech-badge";
    badge.innerHTML = `<i class="${tech.icon}"></i> ${tech.name}`;
    techContainer.appendChild(badge);
  });

  // Repositories data based on your pinned repos from profile
  const repositories = [
    { name: "Sauraysuraj99", description: "✨ GitHub profile README — config & bio.", language: "Markdown", color: "#563d7c", url: "https://github.com/Sauraysuraj99/Sauraysuraj99" },
    { name: "PORTFOLIOFILE", description: "Personal portfolio frontend showcase.", language: "HTML", color: "#e34c26", url: "https://github.com/Sauraysuraj99/PORTFOLIOFILE" },
    { name: "portfollio-demo", description: "First repository demo — learning journey.", language: "CSS", color: "#563d7c", url: "https://github.com/Sauraysuraj99/portfollio-demo" },
    { name: "Profile-demo", description: "Interactive profile page demo.", language: "HTML", color: "#e34c26", url: "https://github.com/Sauraysuraj99/Profile-demo" },
    { name: "PROFILE--Portfolio", description: "PROFILE modern portfolio design.", language: "HTML", color: "#e34c26", url: "https://github.com/Sauraysuraj99/PROFILE--Portfolio" },
    { name: "PORTFOLLIOPROFILE-Suraj", description: "Advanced dev portfolio concept.", language: "JavaScript", color: "#f1e05a", url: "https://github.com/Sauraysuraj99/PORTFOLLIOPROFILE-Suraj" }
  ];

  const repoGrid = document.getElementById("repoList");
  repositories.forEach((repo, idx) => {
    const card = document.createElement("div");
    card.className = "repo-card";
    card.style.animationDelay = `${idx * 0.05}s`;
    card.innerHTML = `
      <div class="repo-name">
        <i class="fas fa-book-open"></i>
        <a href="${repo.url}" target="_blank" style="text-decoration: none; color: #cde1ff;">${repo.name}</a>
      </div>
      <div class="repo-desc">${repo.description}</div>
      <div style="font-size: 0.75rem; display: flex; align-items: center; gap: 12px;">
        <span><span class="lang-color" style="background: ${repo.color};"></span> ${repo.language}</span>
        <span><i class="far fa-star"></i> ★</span>
      </div>
    `;
    repoGrid.appendChild(card);
  });

  // Animated counters (from actual stats: 4 followers, 10 following, 56 repos)
  function animateCounter(elementId, targetValue, duration = 1500) {
    const element = document.getElementById(elementId);
    if (!element) return;
    let start = 0;
    const increment = targetValue / (duration / 16);
    let current = 0;
    const updateCounter = () => {
      current += increment;
      if (current < targetValue) {
        element.innerText = Math.floor(current);
        requestAnimationFrame(updateCounter);
      } else {
        element.innerText = targetValue;
      }
    };
    requestAnimationFrame(updateCounter);
  }

  // trigger counters when visible (lazy using intersection observer) 
  const statSection = document.querySelector(".stats-wrap");
  const observer = new IntersectionObserver((entries) => {
    entries.forEach(entry => {
      if (entry.isIntersecting) {
        animateCounter("repoCount", 56);
        animateCounter("followersCount", 4);
        animateCounter("followingCount", 10);
        document.getElementById("contributionYear").innerText = "2026";
        observer.disconnect();
      }
    });
  }, { threshold: 0.4 });
  if (statSection) observer.observe(statSection);

  // Additional small animated stats using random motion for "pulse" feel
  const extraEffect = () => {
    const statNumbers = document.querySelectorAll(".stat-number");
    statNumbers.forEach(el => {
      el.style.transition = "text-shadow 0.2s";
      setInterval(() => {
        if (Math.random() > 0.85) {
          el.style.textShadow = "0 0 6px #3b82f6";
          setTimeout(() => el.style.textShadow = "none", 300);
        }
      }, 1800);
    });
  };
  setTimeout(extraEffect, 1000);

  // Add smooth reveal for all sections on scroll
  const revealElements = document.querySelectorAll("section, .hero, .footer-social");
  const revealObserver = new IntersectionObserver((entries) => {
    entries.forEach(entry => {
      if (entry.isIntersecting) {
        entry.target.style.opacity = "1";
        entry.target.style.transform = "translateY(0)";
        revealObserver.unobserve(entry.target);
      }
    });
  }, { threshold: 0.05 });
  revealElements.forEach(el => {
    el.style.opacity = "0";
    el.style.transform = "translateY(20px)";
    el.style.transition = "all 0.5s cubic-bezier(0.2, 0.9, 0.4, 1.1)";
    revealObserver.observe(el);
  });
  // hero already visible, force reveal
  document.querySelector(".hero").style.opacity = "1";
  document.querySelector(".hero").style.transform = "translateY(0)";

  // Also generate small glow circle moving based on mouse movement (extra polish)
  document.addEventListener("mousemove", (e) => {
    const glow = document.createElement("div");
    // not heavy — just temporary effect
    const x = e.clientX, y = e.clientY;
    const element = document.elementFromPoint(x, y);
    if (element && element.classList && element.classList.contains("repo-card")) {
      element.style.transition = "box-shadow 0.1s";
      element.style.boxShadow = "0 0 0 2px rgba(59,130,246,0.3)";
      setTimeout(() => {
        if (element) element.style.boxShadow = "";
      }, 150);
    }
  });

  // generate dynamic year in footer
  const yearSpan = document.createElement("span");
  // optional extra: current year display inside footer (already there but dynamic)
  console.log("🔥 Animation Portfolio Loaded — Java Full Stack Momentum");
</script>
</body>
</html>
