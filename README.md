## <!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Photography Portfolio | [Your Name]</title>
    <!-- Load Tailwind CSS -->
    <script src="https://cdn.tailwindcss.com"></script>
    <style>
        /* Custom font import and configuration */
        @import url('https://fonts.googleapis.com/css2?family=Inter:wght@100..900&display=swap');
        
        :root {
            --primary-color: #fca311; /* Gold/Orange Accent */
            --bg-color: #121212;     /* Dark Charcoal Background */
            --text-color: #e5e5e5;   /* Light Gray Text */
        }
        
        body {
            font-family: 'Inter', sans-serif;
            background-color: var(--bg-color);
            color: var(--text-color);
            scroll-behavior: smooth;
        }

        /* Set a high contrast for the gallery items on hover */
        .gallery-item:hover .overlay {
            opacity: 1;
        }

        /* Simple animation for section reveal */
        .fade-in {
            animation: fadeIn 1s ease-in-out forwards;
            opacity: 0;
        }
        @keyframes fadeIn {
            from { opacity: 0; transform: translateY(20px); }
            to { opacity: 1; transform: translateY(0); }
        }

        /* Responsive image aspect ratio for the gallery */
        .aspect-square {
            aspect-ratio: 1 / 1;
        }
    </style>
    <script>
        tailwind.config = {
            theme: {
                extend: {
                    colors: {
                        'accent': 'var(--primary-color)',
                        'dark-bg': 'var(--bg-color)',
                        'light-text': 'var(--text-color)',
                    }
                }
            }
        }

        // JavaScript for smooth scrolling and simple navigation functionality
        function setupNavigation() {
            const navLinks = document.querySelectorAll('nav a');
            navLinks.forEach(link => {
                link.addEventListener('click', (e) => {
                    e.preventDefault();
                    const targetId = link.getAttribute('href').substring(1);
                    const targetElement = document.getElementById(targetId);
                    if (targetElement) {
                        targetElement.scrollIntoView({ behavior: 'smooth' });
                    }
                    // Close mobile menu if open
                    const menu = document.getElementById('mobile-menu');
                    const menuButton = document.getElementById('menu-button');
                    if (menu.classList.contains('flex')) {
                        menu.classList.remove('flex');
                        menu.classList.add('hidden');
                        menuButton.textContent = '☰'; // Reset button text
                    }
                });
            });

            // Mobile menu toggle
            const menuButton = document.getElementById('menu-button');
            const mobileMenu = document.getElementById('mobile-menu');
            menuButton.addEventListener('click', () => {
                mobileMenu.classList.toggle('hidden');
                mobileMenu.classList.toggle('flex');
                menuButton.textContent = mobileMenu.classList.contains('flex') ? '✕' : '☰';
            });
        }

        // Function to trigger fade-in animations when scrolled into view
        function setupScrollAnimations() {
            const observer = new IntersectionObserver((entries, obs) => {
                entries.forEach(entry => {
                    if (entry.isIntersecting) {
                        entry.target.classList.add('opacity-100');
                        entry.target.style.animationDelay = `${Math.random() * 0.2}s`; // Stagger effect
                        obs.unobserve(entry.target);
                    }
                });
            }, { threshold: 0.1 });

            document.querySelectorAll('.fade-in').forEach(el => {
                observer.observe(el);
            });
        }

        window.onload = () => {
            setupNavigation();
            setupScrollAnimations();
        };
    </script>
</head>
<body class="min-h-screen">

    <!-- Header & Navigation -->
    <header class="sticky top-0 z-50 bg-dark-bg/90 backdrop-blur-sm shadow-md">
        <div class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8">
            <div class="flex justify-between items-center h-20">
                <div class="flex-shrink-0">
                    <a href="#home" class="text-3xl font-extrabold text-accent tracking-wider hover:text-white transition duration-300">
                        LENS <span class="text-white">MAESTRO</span>
                    </a>
                </div>
                
                <!-- Desktop Navigation -->
                <nav class="hidden md:flex space-x-8">
                    <a href="#home" class="text-light-text hover:text-accent font-medium transition duration-300 rounded-full px-3 py-2">Home</a>
                    <a href="#portfolio" class="text-light-text hover:text-accent font-medium transition duration-300 rounded-full px-3 py-2">Portfolio</a>
                    <a href="#about" class="text-light-text hover:text-accent font-medium transition duration-300 rounded-full px-3 py-2">About</a>
                    <a href="#contact" class="text-light-text hover:text-accent font-medium transition duration-300 rounded-full px-3 py-2">Contact</a>
                </nav>

                <!-- Mobile Menu Button -->
                <button id="menu-button" class="md:hidden text-2xl text-light-text p-2 rounded-lg hover:bg-gray-800 transition duration-300" aria-label="Toggle navigation menu">
                    ☰
                </button>
            </div>
        </div>

        <!-- Mobile Menu (Hidden by default) -->
        <div id="mobile-menu" class="hidden md:hidden absolute w-full bg-dark-bg shadow-lg flex-col items-center py-4 space-y-4">
            <a href="#home" class="block text-light-text hover:text-accent font-medium w-full text-center py-2">Home</a>
            <a href="#portfolio" class="block text-light-text hover:text-accent font-medium w-full text-center py-2">Portfolio</a>
            <a href="#about" class="block text-light-text hover:text-accent font-medium w-full text-center py-2">About</a>
            <a href="#contact" class="block text-light-text hover:text-accent font-medium w-full text-center py-2">Contact</a>
        </div>
    </header>

    <main>
        <!-- Hero Section -->
        <section id="home" class="relative h-screen flex items-center justify-center text-center overflow-hidden">
            <!-- Background Image (Use a high-quality placeholder) -->
            <img 
                src="https://placehold.co/1920x1080/1a1a1a/e5e5e5?text=Dramatic+Landscape+Shot" 
                alt="Dramatic photography backdrop" 
                class="absolute inset-0 w-full h-full object-cover blur-sm opacity-50"
            />
            <!-- *** REPLACE THE 'src' ATTRIBUTE ABOVE WITH A LARGE, DRAMATIC PHOTO URL *** -->
            
            <!-- Hero Content -->
            <div class="relative z-10 p-6 bg-dark-bg/50 rounded-xl max-w-4xl mx-4 fade-in">
                <h1 class="text-5xl sm:text-7xl font-extrabold mb-4 leading-tight">
                    Capturing <span class="text-accent">Moments</span>, <br class="sm:hidden"/> Defining <span class="text-accent">Stories</span>
                </h1>
                <p class="text-xl sm:text-2xl font-light mb-8 text-light-text/80">
                    Fine Art and Documentary Photography by [Your Name].
                </p>
                <a href="#portfolio" class="inline-block bg-accent text-dark-bg font-bold py-3 px-8 rounded-full shadow-lg transform hover:scale-105 transition duration-300 ease-in-out hover:bg-white hover:text-accent">
                    View My Work
                </a>
            </div>
        </section>

        <!-- Portfolio Gallery Section -->
        <section id="portfolio" class="py-16 sm:py-24">
            <div class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8">
                <h2 class="text-4xl sm:text-5xl font-extrabold text-center mb-12 text-white fade-in">
                    Latest <span class="text-accent">Works</span>
                </h2>
                
                <!-- Responsive Photo Grid -->
                <div class="grid grid-cols-2 md:grid-cols-3 lg:grid-cols-4 gap-4 sm:gap-6">
                    <!-- Gallery Item 1 -->
                    <div class="group relative rounded-lg overflow-hidden shadow-xl gallery-item fade-in">
                        <img 
                            src="https://placehold.co/800x600/292b2c/ffffff?text=Street+Portrait" 
                            alt="Street Portrait" 
                            class="w-full h-full object-cover aspect-square transition duration-500 group-hover:scale-105"
                            onerror="this.onerror=null;this.src='https://placehold.co/800x600/444/999?text=Error';"
                        >
                        <!-- *** REPLACE THE 'src' ATTRIBUTE ABOVE WITH PHOTO 1 URL *** -->
                        <!-- Overlay for Hover Effect -->
                        <div class="overlay absolute inset-0 bg-dark-bg/60 flex items-center justify-center opacity-0 transition duration-500">
                            <span class="text-white text-lg font-semibold border-2 border-accent p-2 rounded-lg">Street</span>
                        </div>
                    </div>

                    <!-- Gallery Item 2 -->
                    <div class="group relative rounded-lg overflow-hidden shadow-xl gallery-item fade-in">
                        <img 
                            src="https://placehold.co/800x1200/5e503f/ffffff?text=Abstract+Architecture" 
                            alt="Abstract Architecture" 
                            class="w-full h-full object-cover aspect-square transition duration-500 group-hover:scale-105"
                            onerror="this.onerror=null;this.src='https://placehold.co/800x1200/444/999?text=Error';"
                        >
                        <!-- *** REPLACE THE 'src' ATTRIBUTE ABOVE WITH PHOTO 2 URL *** -->
                        <div class="overlay absolute inset-0 bg-dark-bg/60 flex items-center justify-center opacity-0 transition duration-500">
                            <span class="text-white text-lg font-semibold border-2 border-accent p-2 rounded-lg">Architecture</span>
                        </div>
                    </div>

                    <!-- Gallery Item 3 -->
                    <div class="group relative rounded-lg overflow-hidden shadow-xl gallery-item fade-in">
                        <img 
                            src="https://placehold.co/800x800/22333b/ffffff?text=Nature+Close-up" 
                            alt="Nature Close-up" 
                            class="w-full h-full object-cover aspect-square transition duration-500 group-hover:scale-105"
                            onerror="this.onerror=null;this.src='https://placehold.co/800x800/444/999?text=Error';"
                        >
                        <!-- *** REPLACE THE 'src' ATTRIBUTE ABOVE WITH PHOTO 3 URL *** -->
                        <div class="overlay absolute inset-0 bg-dark-bg/60 flex items-center justify-center opacity-0 transition duration-500">
                            <span class="text-white text-lg font-semibold border-2 border-accent p-2 rounded-lg">Nature</span>
                        </div>
                    </div>

                    <!-- Gallery Item 4 -->
                    <div class="group relative rounded-lg overflow-hidden shadow-xl gallery-item fade-in">
                        <img 
                            src="https://placehold.co/800x600/4f5d75/ffffff?text=Black+and+White+Scene" 
                            alt="Black and White Scene" 
                            class="w-full h-full object-cover aspect-square transition duration-500 group-hover:scale-105"
                            onerror="this.onerror=null;this.src='https://placehold.co/800x600/444/999?text=Error';"
                        >
                        <!-- *** REPLACE THE 'src' ATTRIBUTE ABOVE WITH PHOTO 4 URL *** -->
                        <div class="overlay absolute inset-0 bg-dark-bg/60 flex items-center justify-center opacity-0 transition duration-500">
                            <span class="text-white text-lg font-semibold border-2 border-accent p-2 rounded-lg">B&W</span>
                        </div>
                    </div>

                    <!-- Gallery Item 5 -->
                    <div class="group relative rounded-lg overflow-hidden shadow-xl gallery-item fade-in">
                        <img 
                            src="https://placehold.co/800x600/7a7a7a/ffffff?text=Vibrant+Food+Shot" 
                            alt="Vibrant Food Shot" 
                            class="w-full h-full object-cover aspect-square transition duration-500 group-hover:scale-105"
                            onerror="this.onerror=null;this.src='https://placehold.co/800x600/444/999?text=Error';"
                        >
                        <!-- *** REPLACE THE 'src' ATTRIBUTE ABOVE WITH PHOTO 5 URL *** -->
                        <div class="overlay absolute inset-0 bg-dark-bg/60 flex items-center justify-center opacity-0 transition duration-500">
                            <span class="text-white text-lg font-semibold border-2 border-accent p-2 rounded-lg">Food</span>
                        </div>
                    </div>

                    <!-- Gallery Item 6 -->
                    <div class="group relative rounded-lg overflow-hidden shadow-xl gallery-item fade-in">
                        <img 
                            src="https://placehold.co/800x600/3d405b/ffffff?text=Concert+Photography" 
                            alt="Concert Photography" 
                            class="w-full h-full object-cover aspect-square transition duration-500 group-hover:scale-105"
                            onerror="this.onerror=null;this.src='https://placehold.co/800x600/444/999?text=Error';"
                        >
                        <!-- *** REPLACE THE 'src' ATTRIBUTE ABOVE WITH PHOTO 6 URL *** -->
                        <div class="overlay absolute inset-0 bg-dark-bg/60 flex items-center justify-center opacity-0 transition duration-500">
                            <span class="text-white text-lg font-semibold border-2 border-accent p-2 rounded-lg">Events</span>
                        </div>
                    </div>
                    
                    <!-- Gallery Item 7 (Only visible on larger screens for better grid balance) -->
                    <div class="group relative rounded-lg overflow-hidden shadow-xl gallery-item hidden md:block fade-in">
                        <img 
                            src="https://placehold.co/800x1000/8d8a8a/ffffff?text=Fashion+Editorial" 
                            alt="Fashion Editorial" 
                            class="w-full h-full object-cover aspect-square transition duration-500 group-hover:scale-105"
                            onerror="this.onerror=null;this.src='https://placehold.co/800x1000/444/999?text=Error';"
                        >
                        <!-- *** REPLACE THE 'src' ATTRIBUTE ABOVE WITH PHOTO 7 URL *** -->
                        <div class="overlay absolute inset-0 bg-dark-bg/60 flex items-center justify-center opacity-0 transition duration-500">
                            <span class="text-white text-lg font-semibold border-2 border-accent p-2 rounded-lg">Fashion</span>
                        </div>
                    </div>

                    <!-- Gallery Item 8 (Only visible on larger screens for better grid balance) -->
                    <div class="group relative rounded-lg overflow-hidden shadow-xl gallery-item hidden lg:block fade-in">
                        <img 
                            src="https://placehold.co/800x600/c1c1c1/333333?text=Macro+Detail" 
                            alt="Macro Detail" 
                            class="w-full h-full object-cover aspect-square transition duration-500 group-hover:scale-105"
                            onerror="this.onerror=null;this.src='https://placehold.co/800x600/444/999?text=Error';"
                        >
                        <!-- *** REPLACE THE 'src' ATTRIBUTE ABOVE WITH PHOTO 8 URL *** -->
                        <div class="overlay absolute inset-0 bg-dark-bg/60 flex items-center justify-center opacity-0 transition duration-500">
                            <span class="text-white text-lg font-semibold border-2 border-accent p-2 rounded-lg">Macro</span>
                        </div>
                    </div>
                    
                </div>
            </div>
        </section>

        <!-- About Section -->
        <section id="about" class="py-16 sm:py-24 bg-gray-900">
            <div class="max-w-4xl mx-auto px-4 sm:px-6 lg:px-8 text-center">
                <h2 class="text-4xl sm:text-5xl font-extrabold mb-8 text-white fade-in">
                    The <span class="text-accent">Photographer</span>
                </h2>
                <div class="flex flex-col md:flex-row items-center gap-8">
                    <!-- Profile Picture -->
                    <div class="flex-shrink-0 fade-in">
                        <img 
                            src="https://placehold.co/300x300/fca311/121212?text=Your+Photo" 
                            alt="Profile Photo of Photographer" 
                            class="w-48 h-48 rounded-full object-cover border-4 border-accent shadow-2xl mx-auto"
                            onerror="this.onerror=null;this.src='https://placehold.co/300x300/444/999?text=Photo';"
                        >
                        <!-- *** REPLACE THE 'src' ATTRIBUTE ABOVE WITH YOUR HEADSHOT/PROFILE PHOTO URL *** -->
                    </div>
                    <!-- Bio Text -->
                    <div class="text-left space-y-4 fade-in">
                        <p class="text-lg text-light-text/90">
                            Hello! I'm **[Your Name]**, a professional photographer specializing in striking street photography and detailed architectural studies. I believe every scene holds a hidden narrative, and my mission is to reveal that story through light and composition.
                        </p>
                        <p class="text-lg text-light-text/90">
                            Based in [Your City], I've been documenting the world for over ten years, shifting focus from commercial work to passion projects that explore human connection and the geometry of urban spaces. When I'm not behind the lens, you can find me hiking the nearest trail or drinking too much coffee.
                        </p>
                        <a href="#contact" class="mt-4 inline-block text-accent font-semibold hover:underline transition duration-300">
                            Let's Connect &rarr;
                        </a>
                    </div>
                </div>
            </div>
        </section>

        <!-- Contact Section -->
        <section id="contact" class="py-16 sm:py-24">
            <div class="max-w-xl mx-auto px-4 sm:px-6 lg:px-8 text-center">
                <h2 class="text-4xl sm:text-5xl font-extrabold mb-4 text-white fade-in">
                    Hire or Collaborate
                </h2>
                <p class="text-xl text-light-text/80 mb-10 fade-in">
                    Have a project in mind or want to license an image? Let's talk.
                </p>
                
                <div class="fade-in">
                    <!-- Mock Contact Form (can be wired to a service later) -->
                    <form action="#" method="POST" class="space-y-6 bg-gray-800 p-8 rounded-xl shadow-2xl">
                        <input type="text" placeholder="Your Name" required class="w-full p-3 rounded-lg bg-gray-700 border border-gray-600 text-white focus:ring-accent focus:border-accent transition duration-300">
                        <input type="email" placeholder="Your Email" required class="w-full p-3 rounded-lg bg-gray-700 border border-gray-600 text-white focus:ring-accent focus:border-accent transition duration-300">
                        <textarea placeholder="Tell me about your project..." rows="4" required class="w-full p-3 rounded-lg bg-gray-700 border border-gray-600 text-white focus:ring-accent focus:border-accent transition duration-300"></textarea>
                        <button type="submit" class="w-full bg-accent text-dark-bg font-bold py-3 rounded-lg transform hover:scale-[1.01] transition duration-300 ease-in-out shadow-lg hover:bg-white hover:text-accent">
                            Send Message
                        </button>
                    </form>
                </div>
                
                <div class="mt-10 text-lg fade-in">
                    <p class="mb-2">Email: <a href="mailto:contact@[yourdomain].com" class="text-accent hover:underline">contact@[yourdomain].com</a></p>
                    <p class="mb-6">Phone: <a href="tel:+15551234567" class="text-accent hover:underline">(555) 123-4567</a></p>
                    
                    <!-- Social Icons (Using simple text/emojis as placeholders) -->
                    <div class="flex justify-center space-x-6">
                        <a href="#" target="_blank" class="text-light-text hover:text-accent text-3xl transition duration-300" aria-label="Instagram">📸</a>
                        <a href="#" target="_blank" class="text-light-text hover:text-accent text-3xl transition duration-300" aria-label="LinkedIn">💼</a>
                        <a href="#" target="_blank" class="text-light-text hover:text-accent text-3xl transition duration-300" aria-label="Twitter/X">🐦</a>
                    </div>
                </div>
            </div>
        </section>

    </main>

    <!-- Footer -->
    <footer class="bg-gray-900 py-8 mt-12">
        <div class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8 text-center text-sm text-gray-500">
            <p>&copy; 2024 LENS MAESTRO. All rights reserved. Photography by [Your Name].</p>
        </div>
    </footer>

</body>
</html>

