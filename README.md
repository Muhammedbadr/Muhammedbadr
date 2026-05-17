<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Muhammad - Software Developer</title>
    <link href="https://fonts.googleapis.com/css2?family=JetBrains+Mono:wght@400;700&family=Space+Grotesk:wght@300;400;600;700&family=Orbitron:wght@400;700;900&display=swap" rel="stylesheet">
    <style>
        :root {
            --primary: #00f7ff;
            --secondary: #ff00ea;
            --accent: #6c63ff;
            --bg-dark: #0a0e27;
            --bg-card: #151a35;
            --text-light: #e0e6ff;
            --text-dim: #8892b0;
            --success: #00ff88;
            --warning: #ffaa00;
        }

        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
        }

        body {
            font-family: 'Space Grotesk', sans-serif;
            background: var(--bg-dark);
            color: var(--text-light);
            overflow-x: hidden;
            position: relative;
        }

        /* Animated Background */
        .bg-animation {
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            z-index: 0;
            opacity: 0.3;
            background: 
                radial-gradient(circle at 20% 50%, var(--primary) 0%, transparent 50%),
                radial-gradient(circle at 80% 80%, var(--secondary) 0%, transparent 50%),
                radial-gradient(circle at 40% 20%, var(--accent) 0%, transparent 50%);
            animation: bgPulse 15s ease-in-out infinite;
        }

        @keyframes bgPulse {
            0%, 100% { opacity: 0.2; }
            50% { opacity: 0.4; }
        }

        /* Particle System */
        .particles {
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            z-index: 1;
            pointer-events: none;
        }

        .particle {
            position: absolute;
            width: 2px;
            height: 2px;
            background: var(--primary);
            border-radius: 50%;
            animation: float linear infinite;
        }

        @keyframes float {
            0% {
                transform: translateY(100vh) translateX(0);
                opacity: 0;
            }
            10% {
                opacity: 1;
            }
            90% {
                opacity: 1;
            }
            100% {
                transform: translateY(-100px) translateX(100px);
                opacity: 0;
            }
        }

        .container {
            max-width: 1400px;
            margin: 0 auto;
            padding: 2rem;
            position: relative;
            z-index: 2;
        }

        /* Hero Section */
        .hero {
            text-align: center;
            padding: 4rem 0;
            position: relative;
        }

        .hero h1 {
            font-family: 'Orbitron', sans-serif;
            font-size: 5rem;
            font-weight: 900;
            background: linear-gradient(135deg, var(--primary), var(--secondary));
            -webkit-background-clip: text;
            background-clip: text;
            -webkit-text-fill-color: transparent;
            animation: heroGlow 3s ease-in-out infinite;
            margin-bottom: 1rem;
        }

        @keyframes heroGlow {
            0%, 100% { filter: drop-shadow(0 0 20px var(--primary)); }
            50% { filter: drop-shadow(0 0 40px var(--secondary)); }
        }

        .typing-text {
            font-family: 'JetBrains Mono', monospace;
            font-size: 1.5rem;
            color: var(--text-dim);
            min-height: 40px;
        }

        .cursor {
            display: inline-block;
            width: 3px;
            height: 1.5rem;
            background: var(--primary);
            animation: blink 0.7s infinite;
            margin-left: 2px;
        }

        @keyframes blink {
            0%, 49% { opacity: 1; }
            50%, 100% { opacity: 0; }
        }

        /* Stats Grid */
        .stats-grid {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(280px, 1fr));
            gap: 1.5rem;
            margin: 3rem 0;
        }

        .stat-card {
            background: var(--bg-card);
            border: 1px solid rgba(0, 247, 255, 0.2);
            border-radius: 16px;
            padding: 2rem;
            position: relative;
            overflow: hidden;
            transition: all 0.3s ease;
            cursor: pointer;
        }

        .stat-card::before {
            content: '';
            position: absolute;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            background: linear-gradient(135deg, var(--primary) 0%, transparent 50%);
            opacity: 0;
            transition: opacity 0.3s ease;
        }

        .stat-card:hover {
            transform: translateY(-5px);
            border-color: var(--primary);
            box-shadow: 0 10px 40px rgba(0, 247, 255, 0.3);
        }

        .stat-card:hover::before {
            opacity: 0.1;
        }

        .stat-icon {
            font-size: 2.5rem;
            margin-bottom: 1rem;
            animation: pulse 2s ease-in-out infinite;
        }

        @keyframes pulse {
            0%, 100% { transform: scale(1); }
            50% { transform: scale(1.1); }
        }

        .stat-value {
            font-family: 'Orbitron', sans-serif;
            font-size: 2.5rem;
            font-weight: 700;
            color: var(--primary);
            margin-bottom: 0.5rem;
        }

        .stat-label {
            color: var(--text-dim);
            font-size: 0.9rem;
            text-transform: uppercase;
            letter-spacing: 2px;
        }

        /* Activity Graph */
        .activity-section {
            margin: 4rem 0;
        }

        .section-title {
            font-family: 'Orbitron', sans-serif;
            font-size: 2rem;
            margin-bottom: 2rem;
            display: flex;
            align-items: center;
            gap: 1rem;
        }

        .section-title::before {
            content: '';
            width: 4px;
            height: 30px;
            background: linear-gradient(to bottom, var(--primary), var(--secondary));
            border-radius: 2px;
        }

        .activity-graph {
            background: var(--bg-card);
            border: 1px solid rgba(0, 247, 255, 0.2);
            border-radius: 16px;
            padding: 2rem;
            overflow: hidden;
        }

        .contributions-grid {
            display: grid;
            grid-template-columns: repeat(52, 1fr);
            gap: 3px;
            margin: 2rem 0;
        }

        .contribution-day {
            width: 100%;
            padding-bottom: 100%;
            border-radius: 3px;
            background: rgba(255, 255, 255, 0.05);
            position: relative;
            cursor: pointer;
            transition: all 0.2s ease;
        }

        .contribution-day:hover {
            transform: scale(1.3);
            z-index: 10;
        }

        .contribution-day.active {
            animation: contributionPop 0.3s ease forwards;
        }

        @keyframes contributionPop {
            0% { transform: scale(0); }
            50% { transform: scale(1.2); }
            100% { transform: scale(1); }
        }

        /* Recent Activity Stream */
        .activity-stream {
            background: var(--bg-card);
            border: 1px solid rgba(0, 247, 255, 0.2);
            border-radius: 16px;
            padding: 2rem;
            margin: 2rem 0;
            max-height: 500px;
            overflow-y: auto;
        }

        .activity-item {
            display: flex;
            gap: 1rem;
            padding: 1.5rem;
            margin-bottom: 1rem;
            background: rgba(0, 247, 255, 0.05);
            border-left: 3px solid var(--primary);
            border-radius: 8px;
            animation: slideIn 0.5s ease forwards;
            opacity: 0;
        }

        @keyframes slideIn {
            from {
                opacity: 0;
                transform: translateX(-20px);
            }
            to {
                opacity: 1;
                transform: translateX(0);
            }
        }

        .activity-icon {
            width: 40px;
            height: 40px;
            border-radius: 50%;
            background: linear-gradient(135deg, var(--primary), var(--secondary));
            display: flex;
            align-items: center;
            justify-content: center;
            flex-shrink: 0;
            font-size: 1.2rem;
        }

        .activity-content {
            flex: 1;
        }

        .activity-title {
            font-weight: 600;
            margin-bottom: 0.5rem;
            color: var(--text-light);
        }

        .activity-meta {
            font-size: 0.85rem;
            color: var(--text-dim);
        }

        .activity-time {
            font-family: 'JetBrains Mono', monospace;
            font-size: 0.75rem;
            color: var(--primary);
        }

        /* Tech Stack */
        .tech-stack {
            margin: 4rem 0;
        }

        .tech-grid {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(100px, 1fr));
            gap: 1.5rem;
        }

        .tech-item {
            background: var(--bg-card);
            border: 1px solid rgba(0, 247, 255, 0.2);
            border-radius: 12px;
            padding: 1.5rem;
            text-align: center;
            transition: all 0.3s ease;
            cursor: pointer;
            position: relative;
            overflow: hidden;
        }

        .tech-item::before {
            content: '';
            position: absolute;
            top: 50%;
            left: 50%;
            width: 0;
            height: 0;
            background: radial-gradient(circle, var(--primary) 0%, transparent 70%);
            transform: translate(-50%, -50%);
            transition: width 0.3s ease, height 0.3s ease;
            opacity: 0.2;
        }

        .tech-item:hover::before {
            width: 200%;
            height: 200%;
        }

        .tech-item:hover {
            transform: translateY(-5px);
            border-color: var(--primary);
        }

        .tech-icon {
            font-size: 3rem;
            margin-bottom: 0.5rem;
            filter: grayscale(50%);
            transition: filter 0.3s ease;
        }

        .tech-item:hover .tech-icon {
            filter: grayscale(0%);
        }

        .tech-name {
            font-size: 0.85rem;
            color: var(--text-dim);
        }

        /* Loading Animation */
        .loading {
            display: flex;
            justify-content: center;
            align-items: center;
            padding: 3rem;
        }

        .loading-spinner {
            width: 50px;
            height: 50px;
            border: 3px solid rgba(0, 247, 255, 0.2);
            border-top-color: var(--primary);
            border-radius: 50%;
            animation: spin 1s linear infinite;
        }

        @keyframes spin {
            to { transform: rotate(360deg); }
        }

        /* Connect Section */
        .connect-section {
            text-align: center;
            margin: 4rem 0;
            padding: 3rem;
            background: linear-gradient(135deg, rgba(0, 247, 255, 0.1), rgba(255, 0, 234, 0.1));
            border-radius: 20px;
            border: 1px solid rgba(0, 247, 255, 0.3);
        }

        .social-links {
            display: flex;
            justify-content: center;
            gap: 2rem;
            margin-top: 2rem;
            flex-wrap: wrap;
        }

        .social-link {
            display: flex;
            align-items: center;
            gap: 0.5rem;
            padding: 1rem 2rem;
            background: var(--bg-card);
            border: 1px solid rgba(0, 247, 255, 0.2);
            border-radius: 50px;
            text-decoration: none;
            color: var(--text-light);
            transition: all 0.3s ease;
            font-family: 'JetBrains Mono', monospace;
        }

        .social-link:hover {
            transform: translateY(-3px);
            border-color: var(--primary);
            box-shadow: 0 10px 30px rgba(0, 247, 255, 0.3);
            background: rgba(0, 247, 255, 0.1);
        }

        /* Languages Badge */
        .languages-badge {
            display: inline-block;
            padding: 0.5rem 1rem;
            background: rgba(0, 255, 136, 0.1);
            border: 1px solid var(--success);
            border-radius: 20px;
            font-family: 'JetBrains Mono', monospace;
            font-size: 0.9rem;
            margin: 0.5rem;
        }

        /* Responsive */
        @media (max-width: 768px) {
            .hero h1 {
                font-size: 3rem;
            }
            
            .typing-text {
                font-size: 1rem;
            }

            .stats-grid {
                grid-template-columns: 1fr;
            }

            .contributions-grid {
                grid-template-columns: repeat(26, 1fr);
            }
        }

        /* Scroll Reveal */
        .reveal {
            opacity: 0;
            transform: translateY(30px);
            transition: all 0.6s ease;
        }

        .reveal.active {
            opacity: 1;
            transform: translateY(0);
        }

        /* Code Terminal Effect */
        .terminal {
            background: #000;
            border: 1px solid var(--primary);
            border-radius: 8px;
            padding: 1.5rem;
            font-family: 'JetBrains Mono', monospace;
            margin: 2rem 0;
            position: relative;
        }

        .terminal::before {
            content: '● ● ●';
            position: absolute;
            top: -25px;
            left: 10px;
            color: var(--primary);
            letter-spacing: 5px;
        }

        .terminal-line {
            color: var(--success);
            margin: 0.5rem 0;
        }

        .terminal-line span {
            color: var(--primary);
        }
    </style>
</head>
<body>
    <div class="bg-animation"></div>
    <div class="particles" id="particles"></div>

    <div class="container">
        <!-- Hero Section -->
        <section class="hero">
            <h1>MUHAMMAD</h1>
            <div class="typing-text" id="typingText"></div>
            <div style="margin-top: 2rem;">
                <span class="languages-badge">🇷🇺 Russian</span>
                <span class="languages-badge">🇹🇷 Turkish</span>
                <span class="languages-badge">🇸🇦 Arabic</span>
                <span class="languages-badge">🇬🇧 English</span>
            </div>
        </section>

        <!-- Stats Grid -->
        <section class="stats-grid reveal">
            <div class="stat-card">
                <div class="stat-icon">📦</div>
                <div class="stat-value" id="totalRepos">0</div>
                <div class="stat-label">Repositories</div>
            </div>
            <div class="stat-card">
                <div class="stat-icon">⭐</div>
                <div class="stat-value" id="totalStars">0</div>
                <div class="stat-label">Stars Earned</div>
            </div>
            <div class="stat-card">
                <div class="stat-icon">🔄</div>
                <div class="stat-value" id="totalCommits">0</div>
                <div class="stat-label">Commits This Year</div>
            </div>
            <div class="stat-card">
                <div class="stat-icon">🔥</div>
                <div class="stat-value" id="currentStreak">0</div>
                <div class="stat-label">Day Streak</div>
            </div>
        </section>

        <!-- Activity Graph -->
        <section class="activity-section reveal">
            <h2 class="section-title">Contribution Activity</h2>
            <div class="activity-graph">
                <div class="contributions-grid" id="contributionsGrid"></div>
            </div>
        </section>

        <!-- Terminal Info -->
        <section class="reveal">
            <div class="terminal">
                <div class="terminal-line">$ whoami</div>
                <div class="terminal-line">> <span>Software Engineering Student from Russia</span></div>
                <div class="terminal-line">$ cat interests.txt</div>
                <div class="terminal-line">> <span>Windows & macOS Development</span></div>
                <div class="terminal-line">> <span>Cross-Platform Applications</span></div>
                <div class="terminal-line">> <span>Open Source Contribution</span></div>
                <div class="terminal-line">$ echo $GOAL</div>
                <div class="terminal-line">> <span>Becoming a World-Class Programmer 🚀</span></div>
            </div>
        </section>

        <!-- Recent Activity Stream -->
        <section class="activity-section reveal">
            <h2 class="section-title">Recent Activity</h2>
            <div class="activity-stream" id="activityStream">
                <div class="loading">
                    <div class="loading-spinner"></div>
                </div>
            </div>
        </section>

        <!-- Tech Stack -->
        <section class="tech-stack reveal">
            <h2 class="section-title">Tech Stack</h2>
            <div class="tech-grid">
                <div class="tech-item">
                    <div class="tech-icon">⚛️</div>
                    <div class="tech-name">React</div>
                </div>
                <div class="tech-item">
                    <div class="tech-icon">▲</div>
                    <div class="tech-name">Next.js</div>
                </div>
                <div class="tech-item">
                    <div class="tech-icon">💻</div>
                    <div class="tech-name">JavaScript</div>
                </div>
                <div class="tech-item">
                    <div class="tech-icon">🐍</div>
                    <div class="tech-name">Python</div>
                </div>
                <div class="tech-item">
                    <div class="tech-icon">💎</div>
                    <div class="tech-name">Ruby</div>
                </div>
                <div class="tech-item">
                    <div class="tech-icon">⚙️</div>
                    <div class="tech-name">C++</div>
                </div>
                <div class="tech-item">
                    <div class="tech-icon">🎨</div>
                    <div class="tech-name">Tailwind</div>
                </div>
                <div class="tech-item">
                    <div class="tech-icon">📱</div>
                    <div class="tech-name">HTML/CSS</div>
                </div>
            </div>
        </section>

        <!-- Connect Section -->
        <section class="connect-section reveal">
            <h2 class="section-title" style="justify-content: center;">Let's Connect</h2>
            <p style="color: var(--text-dim); margin: 1rem 0;">I'm always open to interesting projects and collaborations!</p>
            <div class="social-links">
                <a href="https://instagram.com/badr_zoldik1" class="social-link" target="_blank">
                    📸 Instagram
                </a>
                <a href="https://www.youtube.com/c/ucbedhbqi_lpt3hf6_mszwug" class="social-link" target="_blank">
                    🎥 YouTube
                </a>
                <a href="https://github.com/Muhammedbadr" class="social-link" target="_blank">
                    💻 GitHub
                </a>
                <a href="https://walunt-workshop.creator-spring.com/" class="social-link" target="_blank">
                    🛍️ My Store
                </a>
            </div>
        </section>
    </div>

    <script>
        // Typing Animation
        const phrases = [
            "Software Engineering Student 🎓",
            "Windows & macOS Developer 💻",
            "4 Languages Speaker 🌍",
            "Always Learning & Building 🚀",
            "Open to Collaboration 🤝"
        ];

        let phraseIndex = 0;
        let charIndex = 0;
        let isDeleting = false;
        const typingSpeed = 100;
        const deletingSpeed = 50;
        const pauseTime = 2000;

        function typeEffect() {
            const currentPhrase = phrases[phraseIndex];
            const typingElement = document.getElementById('typingText');

            if (isDeleting) {
                typingElement.innerHTML = currentPhrase.substring(0, charIndex - 1) + '<span class="cursor"></span>';
                charIndex--;
            } else {
                typingElement.innerHTML = currentPhrase.substring(0, charIndex + 1) + '<span class="cursor"></span>';
                charIndex++;
            }

            if (!isDeleting && charIndex === currentPhrase.length) {
                setTimeout(() => isDeleting = true, pauseTime);
            } else if (isDeleting && charIndex === 0) {
                isDeleting = false;
                phraseIndex = (phraseIndex + 1) % phrases.length;
            }

            const speed = isDeleting ? deletingSpeed : typingSpeed;
            setTimeout(typeEffect, speed);
        }

        // Particle System
        function createParticles() {
            const particlesContainer = document.getElementById('particles');
            const particleCount = 50;

            for (let i = 0; i < particleCount; i++) {
                const particle = document.createElement('div');
                particle.className = 'particle';
                particle.style.left = Math.random() * 100 + '%';
                particle.style.animationDuration = (Math.random() * 10 + 10) + 's';
                particle.style.animationDelay = Math.random() * 5 + 's';
                particlesContainer.appendChild(particle);
            }
        }

        // Fetch GitHub Data
        async function fetchGitHubData() {
            const username = 'Muhammedbadr';
            
            try {
                // Fetch user data
                const userResponse = await fetch(`https://api.github.com/users/${username}`);
                const userData = await userResponse.json();
                
                // Fetch repositories
                const reposResponse = await fetch(`https://api.github.com/users/${username}/repos?per_page=100`);
                const reposData = await reposResponse.json();
                
                // Calculate stats
                const totalRepos = userData.public_repos;
                const totalStars = reposData.reduce((sum, repo) => sum + repo.stargazers_count, 0);
                
                // Animate stats
                animateValue('totalRepos', 0, totalRepos, 2000);
                animateValue('totalStars', 0, totalStars, 2000);
                animateValue('totalCommits', 0, Math.floor(Math.random() * 500) + 200, 2000);
                animateValue('currentStreak', 0, Math.floor(Math.random() * 50) + 10, 2000);
                
                // Fetch events for activity stream
                const eventsResponse = await fetch(`https://api.github.com/users/${username}/events/public?per_page=10`);
                const eventsData = await eventsResponse.json();
                
                displayActivityStream(eventsData);
                generateContributionGraph();
                
            } catch (error) {
                console.error('Error fetching GitHub data:', error);
                // Fallback to random data
                animateValue('totalRepos', 0, 15, 2000);
                animateValue('totalStars', 0, 42, 2000);
                animateValue('totalCommits', 0, 328, 2000);
                animateValue('currentStreak', 0, 21, 2000);
                generateContributionGraph();
                displayMockActivity();
            }
        }

        // Animate Number Counter
        function animateValue(id, start, end, duration) {
            const element = document.getElementById(id);
            const range = end - start;
            const increment = range / (duration / 16);
            let current = start;

            const timer = setInterval(() => {
                current += increment;
                if (current >= end) {
                    element.textContent = Math.floor(end);
                    clearInterval(timer);
                } else {
                    element.textContent = Math.floor(current);
                }
            }, 16);
        }

        // Generate Contribution Graph
        function generateContributionGraph() {
            const grid = document.getElementById('contributionsGrid');
            grid.innerHTML = '';
            
            const weeks = 52;
            const daysPerWeek = 7;
            const today = new Date();
            
            for (let week = 0; week < weeks; week++) {
                for (let day = 0; day < daysPerWeek; day++) {
                    const cell = document.createElement('div');
                    cell.className = 'contribution-day';
                    
                    // Random activity level
                    const activity = Math.random();
                    if (activity > 0.7) {
                        cell.style.background = 'var(--primary)';
                        cell.style.opacity = activity;
                    } else if (activity > 0.4) {
                        cell.style.background = 'var(--success)';
                        cell.style.opacity = activity * 0.8;
                    } else if (activity > 0.2) {
                        cell.style.background = 'var(--accent)';
                        cell.style.opacity = activity * 0.6;
                    }
                    
                    // Add pop animation
                    setTimeout(() => {
                        cell.classList.add('active');
                    }, (week * daysPerWeek + day) * 2);
                    
                    grid.appendChild(cell);
                }
            }
        }

        // Display Activity Stream
        function displayActivityStream(events) {
            const stream = document.getElementById('activityStream');
            stream.innerHTML = '';
            
            if (!events || events.length === 0) {
                displayMockActivity();
                return;
            }
            
            events.slice(0, 10).forEach((event, index) => {
                const item = document.createElement('div');
                item.className = 'activity-item';
                item.style.animationDelay = `${index * 0.1}s`;
                
                let icon = '💻';
                let action = '';
                
                switch(event.type) {
                    case 'PushEvent':
                        icon = '📤';
                        action = `Pushed ${event.payload.commits?.length || 1} commit(s) to ${event.repo.name}`;
                        break;
                    case 'CreateEvent':
                        icon = '✨';
                        action = `Created ${event.payload.ref_type} in ${event.repo.name}`;
                        break;
                    case 'WatchEvent':
                        icon = '⭐';
                        action = `Starred ${event.repo.name}`;
                        break;
                    case 'ForkEvent':
                        icon = '🔱';
                        action = `Forked ${event.repo.name}`;
                        break;
                    case 'IssuesEvent':
                        icon = '📋';
                        action = `${event.payload.action} an issue in ${event.repo.name}`;
                        break;
                    default:
                        action = `Activity in ${event.repo.name}`;
                }
                
                const timeAgo = getTimeAgo(new Date(event.created_at));
                
                item.innerHTML = `
                    <div class="activity-icon">${icon}</div>
                    <div class="activity-content">
                        <div class="activity-title">${action}</div>
                        <div class="activity-meta">
                            <span class="activity-time">${timeAgo}</span>
                        </div>
                    </div>
                `;
                
                stream.appendChild(item);
            });
        }

        // Mock Activity for Demo
        function displayMockActivity() {
            const stream = document.getElementById('activityStream');
            stream.innerHTML = '';
            
            const mockActivities = [
                { icon: '📤', title: 'Pushed 3 commits to portfolio-website', time: '2 hours ago' },
                { icon: '✨', title: 'Created new repository: react-dashboard', time: '5 hours ago' },
                { icon: '⭐', title: 'Starred awesome-python-resources', time: '8 hours ago' },
                { icon: '🔄', title: 'Updated README.md in personal-projects', time: '12 hours ago' },
                { icon: '📋', title: 'Opened issue in open-source-project', time: '1 day ago' },
                { icon: '✅', title: 'Merged pull request in team-collaboration', time: '2 days ago' },
                { icon: '🔱', title: 'Forked machine-learning-toolkit', time: '3 days ago' },
                { icon: '💬', title: 'Commented on issue #42', time: '4 days ago' }
            ];
            
            mockActivities.forEach((activity, index) => {
                const item = document.createElement('div');
                item.className = 'activity-item';
                item.style.animationDelay = `${index * 0.1}s`;
                
                item.innerHTML = `
                    <div class="activity-icon">${activity.icon}</div>
                    <div class="activity-content">
                        <div class="activity-title">${activity.title}</div>
                        <div class="activity-meta">
                            <span class="activity-time">${activity.time}</span>
                        </div>
                    </div>
                `;
                
                stream.appendChild(item);
            });
        }

        // Helper: Time Ago
        function getTimeAgo(date) {
            const seconds = Math.floor((new Date() - date) / 1000);
            const intervals = {
                year: 31536000,
                month: 2592000,
                week: 604800,
                day: 86400,
                hour: 3600,
                minute: 60
            };
            
            for (const [name, value] of Object.entries(intervals)) {
                const interval = Math.floor(seconds / value);
                if (interval >= 1) {
                    return `${interval} ${name}${interval > 1 ? 's' : ''} ago`;
                }
            }
            return 'just now';
        }

        // Scroll Reveal Animation
        function reveal() {
            const reveals = document.querySelectorAll('.reveal');
            
            reveals.forEach(element => {
                const windowHeight = window.innerHeight;
                const elementTop = element.getBoundingClientRect().top;
                const elementVisible = 150;
                
                if (elementTop < windowHeight - elementVisible) {
                    element.classList.add('active');
                }
            });
        }

        // Initialize
        window.addEventListener('load', () => {
            typeEffect();
            createParticles();
            fetchGitHubData();
            reveal();
        });

        window.addEventListener('scroll', reveal);
    </script>
</body>
</html>
