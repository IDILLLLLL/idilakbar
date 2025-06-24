# idilakbar
My Github Profile
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Visual Code Study Dashboard</title>
    <style>
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
        }

        body {
            font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
            background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
            min-height: 100vh;
            overflow-x: hidden;
        }

        .container {
            max-width: 1400px;
            margin: 0 auto;
            padding: 20px;
        }

        .header {
            text-align: center;
            margin-bottom: 40px;
            color: white;
        }

        .header h1 {
            font-size: 3rem;
            margin-bottom: 10px;
            text-shadow: 2px 2px 4px rgba(0,0,0,0.3);
            animation: slideInDown 1s ease-out;
        }

        .header p {
            font-size: 1.2rem;
            opacity: 0.9;
            animation: fadeInUp 1s ease-out 0.3s both;
        }

        .dashboard {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(300px, 1fr));
            gap: 25px;
            margin-bottom: 40px;
        }

        .card {
            background: rgba(255, 255, 255, 0.95);
            backdrop-filter: blur(10px);
            border-radius: 20px;
            padding: 30px;
            box-shadow: 0 15px 35px rgba(0,0,0,0.1);
            transition: all 0.3s ease;
            animation: fadeInUp 0.8s ease-out;
            position: relative;
            overflow: hidden;
        }

        .card::before {
            content: '';
            position: absolute;
            top: 0;
            left: 0;
            right: 0;
            height: 4px;
            background: linear-gradient(90deg, #ff6b6b, #4ecdc4, #45b7d1, #96ceb4);
            animation: shimmer 2s infinite;
        }

        .card:hover {
            transform: translateY(-10px);
            box-shadow: 0 25px 50px rgba(0,0,0,0.15);
        }

        .card-header {
            display: flex;
            align-items: center;
            margin-bottom: 20px;
        }

        .card-icon {
            width: 50px;
            height: 50px;
            border-radius: 12px;
            display: flex;
            align-items: center;
            justify-content: center;
            font-size: 24px;
            margin-right: 15px;
            color: white;
        }

        .progress-card .card-icon { background: linear-gradient(135deg, #ff6b6b, #ee5a24); }
        .skills-card .card-icon { background: linear-gradient(135deg, #4ecdc4, #44a08d); }
        .projects-card .card-icon { background: linear-gradient(135deg, #45b7d1, #2d98da); }
        .schedule-card .card-icon { background: linear-gradient(135deg, #96ceb4, #85c1a0); }

        .card-title {
            font-size: 1.5rem;
            font-weight: 700;
            color: #2c3e50;
        }

        .progress-bar {
            width: 100%;
            height: 12px;
            background: #ecf0f1;
            border-radius: 10px;
            overflow: hidden;
            margin: 15px 0;
            position: relative;
        }

        .progress-fill {
            height: 100%;
            border-radius: 10px;
            transition: width 2s ease-out;
            position: relative;
            overflow: hidden;
        }

        .progress-fill::after {
            content: '';
            position: absolute;
            top: 0;
            left: 0;
            right: 0;
            bottom: 0;
            background: linear-gradient(90deg, transparent, rgba(255,255,255,0.3), transparent);
            animation: progressShine 2s infinite;
        }

        .progress-item {
            margin-bottom: 20px;
        }

        .progress-label {
            display: flex;
            justify-content: space-between;
            margin-bottom: 8px;
            font-weight: 600;
            color: #34495e;
        }

        .skill-tag {
            display: inline-block;
            background: linear-gradient(135deg, #667eea, #764ba2);
            color: white;
            padding: 8px 16px;
            border-radius: 20px;
            margin: 5px;
            font-size: 0.9rem;
            font-weight: 500;
            transition: all 0.3s ease;
            cursor: pointer;
        }

        .skill-tag:hover {
            transform: scale(1.05);
            box-shadow: 0 5px 15px rgba(102, 126, 234, 0.4);
        }

        .project-item {
            background: #f8f9fa;
            border-radius: 12px;
            padding: 20px;
            margin-bottom: 15px;
            border-left: 4px solid #45b7d1;
            transition: all 0.3s ease;
        }

        .project-item:hover {
            background: #e9ecef;
            transform: translateX(5px);
        }

        .project-title {
            font-weight: 700;
            color: #2c3e50;
            margin-bottom: 8px;
        }

        .project-desc {
            color: #7f8c8d;
            font-size: 0.9rem;
            line-height: 1.5;
        }

        .schedule-item {
            display: flex;
            align-items: center;
            padding: 15px;
            border-radius: 12px;
            margin-bottom: 12px;
            background: linear-gradient(135deg, #f8f9fa, #e9ecef);
            transition: all 0.3s ease;
        }

        .schedule-item:hover {
            background: linear-gradient(135deg, #e9ecef, #dee2e6);
            transform: scale(1.02);
        }

        .schedule-time {
            background: linear-gradient(135deg, #96ceb4, #85c1a0);
            color: white;
            padding: 8px 12px;
            border-radius: 8px;
            font-weight: 600;
            margin-right: 15px;
            min-width: 80px;
            text-align: center;
        }

        .schedule-task {
            font-weight: 600;
            color: #2c3e50;
        }

        .stats-grid {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(200px, 1fr));
            gap: 20px;
            margin-top: 30px;
        }

        .stat-card {
            background: rgba(255, 255, 255, 0.9);
            border-radius: 15px;
            padding: 25px;
            text-align: center;
            transition: all 0.3s ease;
            animation: fadeInUp 1s ease-out;
        }

        .stat-card:hover {
            transform: translateY(-5px);
            box-shadow: 0 15px 30px rgba(0,0,0,0.1);
        }

        .stat-number {
            font-size: 2.5rem;
            font-weight: 800;
            background: linear-gradient(135deg, #667eea, #764ba2);
            -webkit-background-clip: text;
            -webkit-text-fill-color: transparent;
            background-clip: text;
        }

        .stat-label {
            color: #7f8c8d;
            font-weight: 600;
            margin-top: 8px;
        }

        .floating-elements {
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            pointer-events: none;
            z-index: -1;
        }

        .floating-element {
            position: absolute;
            background: rgba(255, 255, 255, 0.1);
            border-radius: 50%;
            animation: float 6s ease-in-out infinite;
        }

        .floating-element:nth-child(1) {
            width: 80px;
            height: 80px;
            top: 20%;
            left: 10%;
            animation-delay: 0s;
        }

        .floating-element:nth-child(2) {
            width: 120px;
            height: 120px;
            top: 60%;
            right: 15%;
            animation-delay: -2s;
        }

        .floating-element:nth-child(3) {
            width: 60px;
            height: 60px;
            bottom: 30%;
            left: 20%;
            animation-delay: -4s;
        }

        @keyframes slideInDown {
            from {
                opacity: 0;
                transform: translateY(-50px);
            }
            to {
                opacity: 1;
                transform: translateY(0);
            }
        }

        @keyframes fadeInUp {
            from {
                opacity: 0;
                transform: translateY(30px);
            }
            to {
                opacity: 1;
                transform: translateY(0);
            }
        }

        @keyframes shimmer {
            0% { transform: translateX(-100%); }
            100% { transform: translateX(100%); }
        }

        @keyframes progressShine {
            0% { transform: translateX(-100%); }
            100% { transform: translateX(100%); }
        }

        @keyframes float {
            0%, 100% { transform: translateY(0px) rotate(0deg); }
            50% { transform: translateY(-20px) rotate(180deg); }
        }

        @media (max-width: 768px) {
            .header h1 {
                font-size: 2rem;
            }
            
            .dashboard {
                grid-template-columns: 1fr;
            }
            
            .container {
                padding: 15px;
            }
        }
    </style>
</head>
<body>
    <div class="floating-elements">
        <div class="floating-element"></div>
        <div class="floating-element"></div>
        <div class="floating-element"></div>
    </div>

    <div class="container">
        <div class="header">
            <h1>🚀 Visual Code Study</h1>
            <p>Dashboard pembelajaran coding yang interaktif dan visual</p>
        </div>

        <div class="dashboard">
            <div class="card progress-card">
                <div class="card-header">
                    <div class="card-icon">📊</div>
                    <div class="card-title">Progress Belajar</div>
                </div>
                <div class="progress-item">
                    <div class="progress-label">
                        <span>JavaScript</span>
                        <span>85%</span>
                    </div>
                    <div class="progress-bar">
                        <div class="progress-fill" style="width: 85%; background: linear-gradient(90deg, #ff6b6b, #ee5a24);"></div>
                    </div>
                </div>
                <div class="progress-item">
                    <div class="progress-label">
                        <span>React</span>
                        <span>70%</span>
                    </div>
                    <div class="progress-bar">
                        <div class="progress-fill" style="width: 70%; background: linear-gradient(90deg, #4ecdc4, #44a08d);"></div>
                    </div>
                </div>
                <div class="progress-item">
                    <div class="progress-label">
                        <span>Node.js</span>
                        <span>60%</span>
                    </div>
                    <div class="progress-bar">
                        <div class="progress-fill" style="width: 60%; background: linear-gradient(90deg, #45b7d1, #2d98da);"></div>
                    </div>
                </div>
            </div>

            <div class="card skills-card">
                <div class="card-header">
                    <div class="card-icon">🛠️</div>
                    <div class="card-title">Skills & Technologies</div>
                </div>
                <div class="skills-container">
                    <div class="skill-tag">HTML5</div>
                    <div class="skill-tag">CSS3</div>
                    <div class="skill-tag">JavaScript</div>
                    <div class="skill-tag">React</div>
                    <div class="skill-tag">Node.js</div>
                    <div class="skill-tag">MongoDB</div>
                    <div class="skill-tag">Git</div>
                    <div class="skill-tag">VS Code</div>
                    <div class="skill-tag">Responsive Design</div>
                    <div class="skill-tag">API Development</div>
                </div>
            </div>

            <div class="card projects-card">
                <div class="card-header">
                    <div class="card-icon">💻</div>
                    <div class="card-title">Current Projects</div>
                </div>
                <div class="project-item">
                    <div class="project-title">E-Commerce Website</div>
                    <div class="project-desc">Membangun toko online dengan React dan Node.js, fitur keranjang belanja dan payment gateway</div>
                </div>
                <div class="project-item">
                    <div class="project-title">Weather App</div>
                    <div class="project-desc">Aplikasi cuaca real-time menggunakan API, responsive design dengan animasi</div>
                </div>
                <div class="project-item">
                    <div class="project-title">Task Manager</div>
                    <div class="project-desc">CRUD application untuk manajemen tugas dengan local storage</div>
                </div>
            </div>

            <div class="card schedule-card">
                <div class="card-header">
                    <div class="card-icon">📅</div>
                    <div class="card-title">Jadwal Belajar Hari ini</div>
                </div>
                <div class="schedule-item">
                    <div class="schedule-time">09:00</div>
                    <div class="schedule-task">Review JavaScript Fundamentals</div>
                </div>
                <div class="schedule-item">
                    <div class="schedule-time">11:00</div>
                    <div class="schedule-task">Practice React Components</div>
                </div>
                <div class="schedule-item">
                    <div class="schedule-time">14:00</div>
                    <div class="schedule-task">Build Portfolio Website</div>
                </div>
                <div class="schedule-item">
                    <div class="schedule-time">16:00</div>
                    <div class="schedule-task">Algorithm & Data Structures</div>
                </div>
                <div class="schedule-item">
                    <div class="schedule-time">19:00</div>
                    <div class="schedule-task">Code Review & Documentation</div>
                </div>
            </div>
        </div>

        <div class="stats-grid">
            <div class="stat-card">
                <div class="stat-number">127</div>
                <div class="stat-label">Jam Belajar</div>
            </div>
            <div class="stat-card">
                <div class="stat-number">23</div>
                <div class="stat-label">Proyek Selesai</div>
            </div>
            <div class="stat-card">
                <div class="stat-number">8.5</div>
                <div class="stat-label">Rating Rata-rata</div>
            </div>
            <div class="stat-card">
                <div class="stat-number">45</div>
                <div class="stat-label">Hari Streak</div>
            </div>
        </div>
    </div>

    <script>
        // Animate progress bars on load
        document.addEventListener('DOMContentLoaded', function() {
            const progressBars = document.querySelectorAll('.progress-fill');
            progressBars.forEach(bar => {
                const width = bar.style.width;
                bar.style.width = '0%';
                setTimeout(() => {
                    bar.style.width = width;
                }, 500);
            });
        });

        // Add interactive hover effects
        document.querySelectorAll('.skill-tag').forEach(tag => {
            tag.addEventListener('click', function() {
                this.style.animation = 'none';
                setTimeout(() => {
                    this.style.animation = '';
                }, 10);
            });
        });

        // Add click animations to cards
        document.querySelectorAll('.card').forEach(card => {
            card.addEventListener('click', function() {
                this.style.transform = 'scale(0.98)';
                setTimeout(() => {
                    this.style.transform = '';
                }, 150);
            });
        });

        // Dynamic time update for schedule
        function updateCurrentTime() {
            const now = new Date();
            const currentHour = now.getHours();
            const currentMinute = now.getMinutes();
            const currentTime = `${currentHour.toString().padStart(2, '0')}:${currentMinute.toString().padStart(2, '0')}`;
            
            document.querySelectorAll('.schedule-time').forEach(timeElement => {
                const scheduleTime = timeElement.textContent;
                if (scheduleTime === currentTime) {
                    timeElement.parentElement.style.background = 'linear-gradient(135deg, #ff6b6b, #ee5a24)';
                    timeElement.parentElement.style.color = 'white';
                    timeElement.parentElement.style.transform = 'scale(1.05)';
                }
            });
        }

        // Update time every minute
        setInterval(updateCurrentTime, 60000);
        updateCurrentTime();

        // Add particle animation
        function createParticle() {
            const particle = document.createElement('div');
            particle.style.position = 'fixed';
            particle.style.width = '4px';
            particle.style.height = '4px';
            particle.style.background = 'rgba(255, 255, 255, 0.6)';
            particle.style.borderRadius = '50%';
            particle.style.pointerEvents = 'none';
            particle.style.left = Math.random() * window.innerWidth + 'px';
            particle.style.top = window.innerHeight + 'px';
            particle.style.zIndex = '-1';
            
            document.body.appendChild(particle);
            
            const animation = particle.animate([
                { transform: 'translateY(0px)', opacity: 1 },
                { transform: `translateY(-${window.innerHeight + 100}px)`, opacity: 0 }
            ], {
                duration: 3000 + Math.random() * 2000,
                easing: 'linear'
            });
            
            animation.onfinish = () => particle.remove();
        }

        // Create particles periodically
        setInterval(createParticle, 2000);
    </script>
</body>
</html>
