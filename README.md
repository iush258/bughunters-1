<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>ScholarSphere - Scholarship Matcher</title>
    <link href="https://fonts.googleapis.com/css2?family=Poppins:wght@400;600;800&display=swap" rel="stylesheet">
    <style>
        body {
            font-family: 'Poppins', sans-serif;
            background-color: #001220;
            margin: 0;
            padding: 0;
            color: white;
        }
        
        .container {
            background: linear-gradient(to right, #164e63, #115e59, #1e3a8a);
            min-height: 100vh;
            display: flex;
            align-items: center;
            justify-content: center;
            padding: 1.5rem;
            overflow-x: hidden;
            position: relative;
        }
        
        .hidden {
            display: none !important;
        }
        
        /* Animations */
        .animate-pulse-slow {
            animation: pulse 3s infinite;
        }
        
        .fade-in {
            animation: fadeIn 1.5s ease-out;
        }
        
        .slide-in {
            animation: slideIn 1.2s ease-out;
        }
        
        .float {
            animation: floating 3s ease-in-out infinite;
        }
        
        .bounce {
            animation: bounce 2s ease-in-out infinite;
        }
        
        .spin-slow {
            animation: spin 8s linear infinite;
        }
        
        .sparkle {
            animation: sparkle 2s linear infinite;
        }
        
        .scale-on-hover {
            transition: transform 0.3s ease;
        }
        
        .scale-on-hover:hover {
            transform: translateY(-10px) scale(1.02);
        }
        
        @keyframes pulse {
            0%, 100% { transform: scale(1); opacity: 1; }
            50% { transform: scale(1.05); opacity: 0.8; }
        }
        
        @keyframes fadeIn {
            0% { opacity: 0; transform: translateY(20px); }
            100% { opacity: 1; transform: translateY(0); }
        }
        
        @keyframes slideIn {
            0% { opacity: 0; transform: translateX(-100%); }
            100% { opacity: 1; transform: translateX(0); }
        }
        
        @keyframes floating {
            0%, 100% { transform: translateY(0); }
            50% { transform: translateY(-15px); }
        }
        
        @keyframes bounce {
            0%, 100% { transform: translateY(0); }
            50% { transform: translateY(-20px); }
        }
        
        @keyframes spin {
            0% { transform: rotate(0deg); }
            100% { transform: rotate(360deg); }
        }
        
        @keyframes sparkle {
            0%, 100% { opacity: 1; }
            50% { opacity: 0.5; }
        }
        
        @keyframes shake {
            0%, 100% { transform: rotate(0deg); }
            25% { transform: rotate(5deg); }
            50% { transform: rotate(0deg); }
            75% { transform: rotate(-5deg); }
        }
        
        /* Particles */
        .particles {
            position: absolute;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            overflow: hidden;
            z-index: 0;
        }
        
        .particle {
            position: absolute;
            display: block;
            pointer-events: none;
            animation: fall linear infinite;
        }
        
        @keyframes fall {
            0% {
                transform: translateY(-100px) rotate(0deg);
                opacity: 0;
            }
            10% {
                opacity: 1;
            }
            100% {
                transform: translateY(100vh) rotate(360deg);
                opacity: 0;
            }
        }
        
        /* Styling */
        .gradient-text {
            background: linear-gradient(to right, #00FFFF, #00BFFF, #1E90FF);
            -webkit-background-clip: text;
            background-clip: text;
            color: transparent;
        }
        
        .glass {
            background: rgba(255, 255, 255, 0.1);
            backdrop-filter: blur(10px);
            -webkit-backdrop-filter: blur(10px);
            border: 1px solid rgba(255, 255, 255, 0.2);
            border-radius: 1rem;
        }
        
        .glow {
            box-shadow: 0 0 15px 5px rgba(0, 255, 255, 0.5);
        }
        
        /* Layout */
        .page {
            text-align: center;
            max-width: 64rem;
            z-index: 10;
            position: relative;
        }
        
        .icon-container {
            position: absolute;
        }
        
        .top-icon {
            top: -5rem;
            left: 50%;
            transform: translateX(-50%);
        }
        
        .top-left-icon {
            top: 2.5rem;
            left: 2.5rem;
        }
        
        .bottom-right-icon {
            bottom: 0;
            right: 0;
        }
        
        .top-right-icon {
            top: -1.25rem;
            right: -1.25rem;
        }
        
        /* Typography */
        h1 {
            font-size: 3.75rem;
            font-weight: 800;
            margin-bottom: 1.5rem;
            text-shadow: 0 4px 6px rgba(0, 0, 0, 0.1);
        }
        
        h2 {
            font-size: 2.5rem;
            font-weight: 700;
            margin-bottom: 1rem;
        }
        
        h3 {
            font-size: 1.5rem;
            font-weight: 700;
            margin-bottom: 0.5rem;
            color: #67e8f9;
        }
        
        p {
            margin-bottom: 1rem;
        }
        
        .text-lg {
            font-size: 1.125rem;
        }
        
        .text-xl {
            font-size: 1.25rem;
        }
        
        .text-2xl {
            font-size: 1.5rem;
        }
        
        .text-cyan {
            color: #67e8f9;
        }
        
        /* Forms */
        input, textarea {
            width: 100%;
            max-width: 28rem;
            padding: 0.75rem 1rem;
            border-radius: 0.75rem;
            text-align: center;
            font-size: 1.25rem;
            margin-bottom: 1rem;
            background: rgba(255, 255, 255, 0.2);
            border: 1px solid #67e8f9;
            color: white;
        }
        
        input::placeholder, textarea::placeholder {
            color: rgba(255, 255, 255, 0.7);
        }
        
        textarea {
            min-height: 150px;
            text-align: left;
        }
        
        /* Buttons */
        button {
            cursor: pointer;
            transition: all 0.3s ease;
        }
        
        button:hover {
            transform: scale(1.05);
        }
        
        button:active {
            transform: scale(0.95);
        }
        
        .btn-primary {
            padding: 1rem 2rem;
            background: linear-gradient(to right, #06b6d4, #3b82f6);
            border: none;
            border-radius: 0.75rem;
            font-size: 1.5rem;
            font-weight: 600;
            color: white;
            box-shadow: 0 10px 15px -3px rgba(0, 0, 0, 0.1), 0 4px 6px -2px rgba(0, 0, 0, 0.05);
        }
        
        .btn-primary:hover {
            background: linear-gradient(to right, #0891b2, #2563eb);
        }
        
        .btn-secondary {
            padding: 0.75rem 1.5rem;
            background: transparent;
            border: 1px solid #06b6d4;
            border-radius: 0.5rem;
            font-size: 1.125rem;
            font-weight: 600;
            color: white;
            margin-left: 1rem;
        }
        
        .btn-secondary:hover {
            background: rgba(6, 182, 212, 0.2);
        }
        
        .btn-link {
            background: none;
            border: none;
            color: #67e8f9;
            font-weight: 700;
            padding: 0;
        }
        
        .btn-link:hover {
            text-decoration: underline;
            color: #a5f3fc;
        }
        
        /* Layout components */
        .form-container {
            padding: 2rem;
            margin-bottom: 2rem;
        }
        
        .card-grid {
            display: grid;
            grid-template-columns: 1fr;
            gap: 2rem;
            width: 100%;
            max-width: 80rem;
        }
        
        .card {
            padding: 1.5rem;
            border-radius: 0.5rem;
            box-shadow: 0 10px 15px -3px rgba(0, 0, 0, 0.1), 0 4px 6px -2px rgba(0, 0, 0, 0.05);
            position: relative;
        }
        
        .mb-2 {
            margin-bottom: 0.5rem;
        }
        
        .mb-4 {
            margin-bottom: 1rem;
        }
        
        .mb-8 {
            margin-bottom: 2rem;
        }
        
        .mb-10 {
            margin-bottom: 2.5rem;
        }
        
        .mt-8 {
            margin-top: 2rem;
        }
        
        .mt-32 {
            margin-top: 8rem;
        }
        
        .ml-4 {
            margin-left: 1rem;
        }
        
        .mx-auto {
            margin-left: auto;
            margin-right: auto;
        }
        
        .space-y-4 > * + * {
            margin-top: 1rem;
        }
        
        .flex {
            display: flex;
        }
        
        .justify-center {
            justify-content: center;
        }
        
        .items-center {
            align-items: center;
        }
        
        .flex-col {
            flex-direction: column;
        }
        
        .relative {
            position: relative;
        }
        
        .w-full {
            width: 100%;
        }
        
        .max-w-3xl {
            max-width: 48rem;
        }
        
        .max-w-4xl {
            max-width: 56rem;
        }
        
        .max-w-5xl {
            max-width: 64rem;
        }
        
        .max-w-md {
            max-width: 28rem;
        }
        
        .text-left {
            text-align: left;
        }
        
        .text-center {
            text-align: center;
        }
        
        .z-10 {
            z-index: 10;
        }
        
        /* Icons */
        .icon {
            fill: none;
            stroke: currentColor;
            stroke-width: 2;
            stroke-linecap: round;
            stroke-linejoin: round;
        }
        
        .icon-cyan {
            color: #67e8f9;
        }
        
        .icon-yellow {
            color: #fde047;
        }
        
        .icon-pink {
            color: #f9a8d4;
        }
        
        .icon-lg {
            width: 6rem;
            height: 6rem;
        }
        
        .icon-md {
            width: 5rem;
            height: 5rem;
        }
        
        .icon-sm {
            width: 4rem;
            height: 4rem;
        }
        
        .icon-xs {
            width: 1.5rem;
            height: 1.5rem;
        }
        
        /* Media Queries */
        @media (min-width: 768px) {
            .card-grid {
                grid-template-columns: 1fr 1fr;
            }
        }
    </style>
</head>
<body>
    <div class="container">
        <div class="particles"></div>

        <!-- Homepage -->
        <div id="homepage" class="page">
            <div class="icon-container top-icon float">
                <!-- Graduation Cap Icon -->
                <svg class="icon icon-lg icon-cyan" viewBox="0 0 24 24">
                    <path d="M22 10v6M2 10l10-5 10 5-10 5z"></path>
                    <path d="M6 12v5c0 2 2 3 6 3s6-1 6-3v-5"></path>
                </svg>
            </div>
            
            <h1 class="animate-pulse-slow">
                Welcome to <span class="gradient-text">ScholarSphere</span>
            </h1>
            
            <div class="float mb-8">
                <!-- Book Open Icon -->
                <svg class="icon icon-lg icon-cyan" viewBox="0 0 24 24">
                    <path d="M2 3h6a4 4 0 0 1 4 4v14a3 3 0 0 0-3-3H2z"></path>
                    <path d="M22 3h-6a4 4 0 0 0-4 4v14a3 3 0 0 1 3-3h7z"></path>
                </svg>
            </div>
            
            <p class="text-2xl mb-8">
                Discover the best scholarships tailored to your academic profile.
            </p>
            
            <div class="glass form-container glow">
                <input type="number" id="gpa" placeholder="Enter your GPA" class="mx-auto">
                <br>
                <button id="find-scholarships" class="btn-primary">
                    Find Scholarships Now
                </button>
            </div>
            
            <div class="icon-container bottom-right-icon bounce">
                <!-- Book Icon -->
                <svg class="icon icon-sm icon-cyan" viewBox="0 0 24 24">
                    <path d="M2 3h6a4 4 0 0 1 4 4v14a3 3 0 0 0-3-3H2z"></path>
                    <path d="M22 3h-6a4 4 0 0 0-4 4v14a3 3 0 0 1 3-3h7z"></path>
                </svg>
            </div>
        </div>

        <!-- Results Page -->
        <div id="results-page" class="page hidden">
            <div class="icon-container top-left-icon spin-slow">
                <!-- Lightbulb Icon -->
                <svg class="icon icon-sm icon-yellow" viewBox="0 0 24 24">
                    <path d="M9 18h6M10 22h4M15.09 14c.18-.98.65-1.74 1.41-2.5A4.65 4.65 0 0 0 18 8 6 6 0 0 0 6 8c0 1 .23 2.23 1.5 3.5A4.61 4.61 0 0 1 8.91 14"></path>
                </svg>
            </div>
            
            <div class="text-center mb-10 z-10">
                <h1 class="fade-in gradient-text">ScholarSphere - Scholarship Results</h1>
                <p class="text-xl mb-8 fade-in">Here are the scholarships that match your academic profile.</p>
                <button id="back-to-home" class="btn-primary fade-in">
                    Back to Home
                </button>
            </div>

            <div class="card-grid slide-in z-10">
                <div class="glass card scale-on-hover">
                    <div class="icon-container top-right-icon sparkle">
                        <!-- Lightbulb Icon -->
                        <svg class="icon icon-xs icon-yellow" viewBox="0 0 24 24">
                            <path d="M9 18h6M10 22h4M15.09 14c.18-.98.65-1.74 1.41-2.5A4.65 4.65 0 0 0 18 8A6 6 0 0 0 6 8c0 1 .23 2.23 1.5 3.5A4.61 4.61 0 0 1 8.91 14"></path>
                        </svg>
                    </div>
                    <h3>Science Excellence Scholarship</h3>
                    <p class="mb-4">Available for students pursuing Science degrees with a minimum GPA of 3.5.</p>
                    <button class="btn-link" data-details="science">Learn More</button>
                </div>

                <div class="glass card scale-on-hover">
                    <div class="icon-container top-right-icon sparkle">
                        <!-- Pen Tool Icon -->
                        <svg class="icon icon-xs icon-pink" viewBox="0 0 24 24">
                            <path d="m12 19 7-7 3 3-7 7-3-3z"></path>
                            <path d="m18 13-1.5-7.5L2 2l3.5 14.5L13 18l5-5z"></path>
                            <path d="m2 2 7.586 7.586"></path>
                            <circle cx="11" cy="11" r="2"></circle>
                        </svg>
                    </div>
                    <h3>Arts and Humanities Grant</h3>
                    <p class="mb-4">Ideal for students in History, Literature, and related fields. No GPA requirement.</p>
                    <button class="btn-link" data-details="arts">Learn More</button>
                </div>
            </div>
            
            <div class="icon-container bottom-right-icon bounce">
                <!-- Book Icon -->
                <svg class="icon icon-sm icon-cyan" viewBox="0 0 24 24">
                    <path d="M2 3h6a4 4 0 0 1 4 4v14a3 3 0 0 0-3-3H2z"></path>
                    <path d="M22 3h-6a4 4 0 0 0-4 4v14a3 3 0 0 1 3-3h7z"></path>
                </svg>
            </div>
        </div>

        <!-- Scholarship Details Pages -->
        <div id="science-details" class="page glass max-w-3xl mx-auto z-10 hidden">
            <div class="icon-container top-icon float">
                <!-- Lightbulb Icon -->
                <svg class="icon icon-sm icon-yellow" viewBox="0 0 24 24">
                    <path d="M9 18h6M10 22h4M15.09 14c.18-.98.65-1.74 1.41-2.5A4.65 4.65 0 0 0 18 8A6 6 0 0 0 6 8c0 1 .23 2.23 1.5 3.5A4.61 4.61 0 0 1 8.91 14"></path>
                </svg>
            </div>
            <h2 class="gradient-text">Science Excellence Scholarship</h2>
            <p class="mb-4">Eligibility: Students with a GPA of 3.5+ pursuing Science degrees.</p>
            <p class="mb-4">Application Deadline: June 30, 2025</p>
            <button class="btn-primary apply-now">Apply Now</button>
            <button class="btn-secondary back-to-results">Back to Results</button>
        </div>

        <div id="arts-details" class="page glass max-w-3xl mx-auto z-10 hidden">
            <div class="icon-container top-icon float">
                <!-- Pen Tool Icon -->
                <svg class="icon icon-sm icon-pink" viewBox="0 0 24 24">
                    <path d="m12 19 7-7 3 3-7 7-3-3z"></path>
                    <path d="m18 13-1.5-7.5L2 2l3.5 14.5L13 18l5-5z"></path>
                    <path d="m2 2 7.586 7.586"></path>
                    <circle cx="11" cy="11" r="2"></circle>
                </svg>
            </div>
            <h2 class="gradient-text">Arts and Humanities Grant</h2>
            <p class="mb-4">Eligibility: Students in History, Literature, and related fields.</p>
            <p class="mb-4">No minimum GPA requirement.</p>
            <button class="btn-primary apply-now">Apply Now</button>
            <button class="btn-secondary back-to-results">Back to Results</button>
        </div>

        <!-- Application Form -->
        <div id="application-form" class="page glass max-w-3xl mx-auto z-10 hidden">
            <div class="icon-container top-icon">
                <!-- Search Icon with animation -->
                <svg class="icon icon-sm icon-cyan" viewBox="0 0 24 24" style="animation: shake 5s infinite;">
                    <circle cx="11" cy="11" r="8"></circle>
                    <line x1="21" y1="21" x2="16.65" y2="16.65"></line>
                </svg>
            </div>
            <h2 class="gradient-text">ScholarSphere - Scholarship Application Form</h2>
            <form id="scholarship-form" class="space-y-4">
                <div class="relative">
                    <input type="text" name="name" placeholder="Full Name" required>
                </div>
                <div class="relative">
                    <input type="email" name="email" placeholder="Email" required>
                </div>
                <div class="relative">
                    <textarea name="reason" placeholder="Why do you deserve this scholarship?" required></textarea>
                </div>
                <button type="submit" class="btn-primary">
                    Submit Application
                </button>
                <button type="button" class="btn-secondary cancel-application">Cancel</button>
            </form>
        </div>

        <!-- Ending Page -->
        <div id="ending-page" class="page text-center max-w-4xl z-10 hidden">
            <div class="icon-container top-icon">
                <!-- Award Icon with animation -->
                <svg class="icon icon-lg icon-yellow" viewBox="0 0 24 24" style="animation: floating 5s ease-in-out infinite, shake 5s infinite;">
                    <circle cx="12" cy="8" r="7"></circle>
                    <polyline points="8.21 13.89 7 23 12 20 17 23 15.79 13.88"></polyline>
                </svg>
            </div>
            
            <h2 class="gradient-text mt-32">Thank You!</h2>
            <p class="text-2xl mb-8">Your application has been successfully submitted. Here's a summary of your application:</p>
            
            <div class="glass text-left mb-8 form-container">
                <p class="text-xl"><strong class="text-cyan">Name:</strong> <span id="summary-name"></span></p>
                <p class="text-xl"><strong class="text-cyan">Email:</strong> <span id="summary-email"></span></p>
                <p class="text-xl"><strong class="text-cyan">Reason:</strong> <span id="summary-reason"></span></p>
            </div>
            
            <div class="flex justify-center">
                <button id="restart" class="btn-primary mt-8">
                    Back to Home
                </button>
            </div>
            
            <div class="icon-container bottom-right-icon bounce">
                <!-- Star Icon -->
                <svg class="icon icon-md icon-yellow" viewBox="0 0 24 24">
                    <polygon points="12 2 15.09 8.26 22 9.27 17 14.14 18.18 21.02 12 17.77 5.82 21.02 7 14.14 2 9.27 8.91 8.26 12 2"></polygon>
                </svg>
            </div>
        </div>
    </div>

    <script>
        // Store application data
        let applicationData = {
            name: "",
            email: "",
            reason: ""
        };
        
        // DOM Elements
        const pages = {
            homepage: document.getElementById('homepage'),
            results: document.getElementById('results-page'),
            scienceDetails: document.getElementById('science-details'),
            artsDetails: document.getElementById('arts-details'),
            applicationForm: document.getElementById('application-form'),
            ending: document.getElementById('ending-page')
        };
        
        // Helper function to show a specific page and hide others
        function showPage(pageId) {
            // Hide all pages
            Object.values(pages).forEach(page => {
                page.classList.add('hidden');
            });
            
            // Show the requested page
            pages[pageId].classList.remove('hidden');
            
            // Create appropriate particles
            if (pageId === 'homepage' || pageId === 'results') {
                createParticles();
            } else if (pageId === 'ending') {
                createConfetti();
            }
        }
        
        // Event Listeners
        document.getElementById('find-scholarships').addEventListener('click', function() {
            const gpa = document.getElementById('gpa').value;
            if (gpa) {
                showPage('results');
            }
        });
        
        document.getElementById('back-to-home').addEventListener('click', function() {
            showPage('homepage');
        });
        
        document.querySelectorAll('[data-details]').forEach(button => {
            button.addEventListener('click', function() {
                const detailsType = this.getAttribute('data-details');
                if (detailsType === 'science') {
                    showPage('scienceDetails');
                } else if (detailsType === 'arts') {
                    showPage('artsDetails');
                }
            });
        });
        
        document.querySelectorAll('.apply-now').forEach(button => {
            button.addEventListener('click', function() {
                showPage('applicationForm');
            });
        });
        
        document.querySelectorAll('.back-to-results').forEach(button => {
            button.addEventListener('click', function() {
                showPage('results');
            });
        });
        
        document.querySelector('.cancel-application').addEventListener('click', function() {
            showPage('results');
        });
        
        document.getElementById('scholarship-form').addEventListener('submit', function(event) {
            event.preventDefault();
            
            // Get form data
            const formData = new FormData(event.target);
            applicationData = {
                name: formData.get('name'),
                email: formData.get('email'),
                reason: formData.get('reason')
            };
            
            // Display the data in the summary
            document.getElementById('summary-name').textContent = applicationData.name;
            document.getElementById('summary-email').textContent = applicationData.email;
            document.getElementById('summary-reason').textContent = applicationData.reason;
            
            // Show ending page
            showPage('ending');
        });
        
        document.getElementById('restart').addEventListener('click', function() {
            // Reset form
            document.getElementById('scholarship-form').reset();
            
            // Go back to homepage
            showPage('homepage');
        });
        
        // Particle animations
        function createParticles() {
            const particlesContainer = document.querySelector('.particles');
            particlesContainer.innerHTML = '';
            
            const particleCount = 30;
            const emojis = ['🎓', '📚', '🔍', '✨', '💡', '🌟', '📝', '🎯'];
            
            for (let i = 0; i < particleCount; i++) {
                const particle = document.createElement('span');
                particle.className = 'particle';
                particle.textContent = emojis[Math.floor(Math.random() * emojis.length)];
                particle.style.left = Math.random() * 100 + 'vw';
                particle.style.fontSize = Math.random() * 20 + 10 + 'px';
                particle.style.animationDuration = Math.random() * 15 + 5 + 's';
                particle.style.animationDelay = Math.random() * 5 + 's';
                particlesContainer.appendChild(particle);
            }
        }
        
        function createConfetti() {
            const particlesContainer = document.querySelector('.particles');
            particlesContainer.innerHTML = '';
            
            const particleCount = 100;
            const colors = ['#FF0000', '#00FF00', '#0000FF', '#FFFF00', '#FF00FF', '#00FFFF'];
            
            for (let i = 0; i < particleCount; i++) {
                const particle = document.createElement('div');
                particle.className = 'particle';
                particle.style.width = '10px';
                particle.style.height = '10px';
                particle.style.borderRadius = Math.random() > 0.5 ? '50%' : '0';
                particle.style.backgroundColor = colors[Math.floor(Math.random() * colors.length)];
                particle.style.left = Math.random() * 100 + 'vw';
                particle.style.animationDuration = Math.random() * 3 + 2 + 's';
                particle.style.animationDelay = Math.random() * 0.5 + 's';
                particlesContainer.appendChild(particle);
            }
        }
        
        // Initialize particles on page load
        window.addEventListener('load', function() {
            createParticles();
        });
    </script>
</body>
</html>
