<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Punjaban.ugc | Luxury Portfolio</title>
    
    <!-- Fonts -->
    <link rel="preconnect" href="https://fonts.googleapis.com">
    <link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
    <link href="https://fonts.googleapis.com/css2?family=Parisienne&family=Cormorant+Garamond:ital,wght@0,300;0,400;0,500;0,600;0,700;1,400&family=Manrope:wght@300;400;500;600;700&display=swap" rel="stylesheet">
    
    <!-- Tailwind CSS -->
    <script src="https://cdn.tailwindcss.com"></script>
    
    <!-- Lucide Icons -->
    <script src="https://unpkg.com/lucide@latest"></script>

    <style>
        :root {
            --wine: #6D2E46;
            --dusty-rose: #9B5C73;
            --mauve-pink: #B97A8D;
            --blush: #D9A7B3;
            --nude: #E8C9D0;
            --cream: #FAF5F7;
            --plum-brown: #4A2C36;
            --fem-brown: #70505A;
        }

        .font-script { font-family: 'Parisienne', cursive; }
        .font-serif { font-family: 'Cormorant Garamond', serif; }
        .font-sans { font-family: 'Manrope', sans-serif; }

        html { scroll-behavior: smooth; }
        body { background-color: var(--cream); overflow-x: hidden; }

        .grain-overlay {
            position: fixed;
            inset: 0;
            pointer-events: none;
            z-index: 9999;
            opacity: 0.03;
            background-image: url('https://grainy-gradients.vercel.app/noise.svg');
        }

        .watercolor-blob {
            position: absolute;
            border-radius: 50%;
            filter: blur(100px);
            opacity: 0.2;
            pointer-events: none;
            z-index: -10;
        }

        .nav-scrolled {
            background: rgba(255, 255, 255, 0.4);
            backdrop-filter: blur(16px);
            box-shadow: 0 4px 30px rgba(0, 0, 0, 0.05);
            padding: 0.75rem 1.5rem !important;
        }

        .btn-primary {
            background: linear-gradient(to right, var(--wine), var(--dusty-rose));
            transition: all 0.5s ease;
        }
        .btn-primary:hover {
            box-shadow: 0 10px 25px -5px rgba(109, 46, 70, 0.3);
            transform: translateY(-2px);
        }

        .portfolio-card img {
            transition: transform 1.5s ease;
        }
        .portfolio-card:hover img {
            transform: scale(1.05);
        }

        @keyframes drift {
            0%, 100% { transform: translate(0, 0) scale(1); }
            50% { transform: translate(20px, 20px) scale(1.1); }
        }
        .animate-drift {
            animation: drift 10s infinite ease-in-out;
        }

        /* Prevent text overflow for the script font */
        .hero-title {
            line-height: 1.2;
            padding-bottom: 0.1em;
        }
    </style>
</head>
<body class="font-sans text-[#4A2C36]">

    <div class="grain-overlay"></div>

    <!-- Navigation -->
    <nav id="navbar" class="fixed top-0 w-full z-50 transition-all duration-700 py-6 md:py-8">
        <div class="container mx-auto px-6">
            <div class="flex items-center justify-between px-6 md:px-8 py-3 rounded-full transition-all duration-700 border border-transparent">
                <div class="text-2xl md:text-3xl font-script tracking-tight text-[#4A2C36] flex items-center gap-1">
                    Punjaban<span class="text-[#9B5C73] text-lg mt-2">.ugc</span>
                </div>
                
                <div class="hidden md:flex items-center space-x-8 lg:space-x-10">
                    <a href="#about" class="text-[10px] font-bold uppercase tracking-[0.3em] text-[#70505A] hover:text-[#6D2E46] transition-colors">Story</a>
                    <a href="#services" class="text-[10px] font-bold uppercase tracking-[0.3em] text-[#70505A] hover:text-[#6D2E46] transition-colors">Offerings</a>
                    <a href="#work" class="text-[10px] font-bold uppercase tracking-[0.3em] text-[#70505A] hover:text-[#6D2E46] transition-colors">Gallery</a>
                    <a href="#contact" class="text-[10px] font-bold uppercase tracking-[0.3em] text-[#70505A] hover:text-[#6D2E46] transition-colors">Contact</a>
                    <button onclick="document.getElementById('contact').scrollIntoView({behavior: 'smooth'})" class="px-7 py-2.5 rounded-full bg-[#6D2E46] text-white text-xs font-bold uppercase tracking-widest hover:shadow-lg hover:shadow-[#6D2E46]/20 transition-all duration-500">
                        Collab
                    </button>
                </div>

                <button class="md:hidden text-[#4A2C36]" id="menu-btn">
                    <i data-lucide="menu"></i>
                </button>
            </div>
        </div>
        
        <!-- Mobile Menu -->
        <div id="mobile-menu" class="hidden absolute top-full left-0 w-full bg-white/95 backdrop-blur-2xl py-12 px-6 shadow-2xl border-b border-pink-50 text-center">
            <div class="flex flex-col items-center space-y-8">
                <a href="#about" class="text-2xl font-serif text-[#4A2C36]">Story</a>
                <a href="#services" class="text-2xl font-serif text-[#4A2C36]">Offerings</a>
                <a href="#work" class="text-2xl font-serif text-[#4A2C36]">Gallery</a>
                <a href="#contact" class="text-2xl font-serif text-[#4A2C36]">Contact</a>
                <button onclick="document.getElementById('contact').scrollIntoView({behavior: 'smooth'}); document.getElementById('mobile-menu').classList.add('hidden');" class="w-full py-4 rounded-full bg-[#6D2E46] text-white font-bold tracking-widest uppercase text-xs">
                    Inquire Now
                </button>
            </div>
        </div>
    </nav>

    <!-- Hero Section -->
    <section class="relative min-h-screen flex items-center pt-32 pb-16 overflow-hidden">
        <div class="watercolor-blob top-[-10%] right-[-5%] w-[60%] h-[60%] opacity-30" style="background-color: #EFD5DB;"></div>
        <div class="watercolor-blob bottom-[10%] left-[-10%] w-[50%] h-[50%]" style="background-color: #E6B7C1;"></div>

        <div class="container mx-auto px-6 relative z-10">
            <div class="grid grid-cols-1 lg:grid-cols-2 gap-12 lg:gap-20 items-center">
                <div class="max-w-xl">
                    <div class="flex items-center space-x-4 mb-6 md:mb-8">
                        <span class="h-[1px] w-12 bg-[#9B5C73]"></span>
                        <span class="text-[#9B5C73] font-bold tracking-[0.4em] uppercase text-[10px]">UGC & Brand Storytelling</span>
                    </div>
                    
                    <h1 class="hero-title text-6xl md:text-7xl lg:text-8xl font-script text-[#4A2C36] mb-6">
                        punjaban<span class="text-[#9B5C73]">.</span>ugc
                    </h1>
                    
                    <h2 class="text-2xl md:text-3xl font-serif italic text-[#70505A] mb-10 leading-relaxed">
                        Soft luxury visuals for romantic & fashion-forward brands.
                    </h2>
                    
                    <div class="flex flex-wrap gap-4 md:gap-6">
                        <button onclick="document.getElementById('work').scrollIntoView({behavior: 'smooth'})" class="btn-primary px-8 md:px-10 py-4 md:py-5 rounded-full text-white text-[10px] md:text-xs font-bold tracking-widest uppercase flex items-center space-x-3 group">
                            <span>View Portfolio</span>
                            <i data-lucide="arrow-right" class="w-4 h-4 group-hover:translate-x-1 transition-transform"></i>
                        </button>
                        <button onclick="document.getElementById('contact').scrollIntoView({behavior: 'smooth'})" class="px-8 md:px-10 py-4 md:py-5 rounded-full bg-white text-[#6D2E46] text-[10px] md:text-xs font-bold tracking-widest uppercase border border-pink-100 hover:bg-pink-50/50 transition-all duration-700 shadow-sm">
                            Work With Me
                        </button>
                    </div>

                    <div class="mt-16 md:mt-24 flex items-center space-x-10 md:space-x-16 opacity-80 border-l border-pink-100 pl-8">
                        <div class="flex flex-col">
                            <span class="text-3xl md:text-4xl font-serif text-[#4A2C36]">150+</span>
                            <span class="text-[10px] text-[#70505A] uppercase tracking-widest font-bold mt-1">Campaigns</span>
                        </div>
                        <div class="flex flex-col">
                            <span class="text-3xl md:text-4xl font-serif text-[#4A2C36]">4.8M</span>
                            <span class="text-[10px] text-[#70505A] uppercase tracking-widest font-bold mt-1">Impressions</span>
                        </div>
                    </div>
                </div>

                <div class="relative mt-12 lg:mt-0 lg:pl-10">
                    <!-- Main Frame -->
                    <div class="relative z-10 w-full max-w-md mx-auto aspect-[4/5] rounded-[30px] overflow-hidden shadow-2xl p-4 bg-white transform -rotate-2">
                        <div class="w-full h-full rounded-[20px] overflow-hidden relative">
                            <div class="absolute inset-0 bg-gradient-to-t from-[#6D2E46]/10 to-transparent mix-blend-multiply"></div>
                            <img src="https://images.unsplash.com/photo-1512436991641-6745cdb1723f?auto=format&fit=crop&q=80&w=800" alt="Creative Showcase" class="w-full h-full object-cover grayscale-[10%]">
                        </div>
                    </div>
                    
                    <!-- Floating Quote -->
                    <div class="absolute -bottom-8 md:-bottom-12 -left-4 md:left-0 z-20 p-6 md:p-8 rounded-[30px] bg-white/70 backdrop-blur-xl border border-white shadow-2xl max-w-[200px] md:max-w-[260px] animate-drift transform rotate-3">
                        <i data-lucide="heart" class="text-[#9B5C73] mb-4 fill-[#9B5C73] w-5 h-5"></i>
                        <p class="text-base md:text-lg font-serif italic text-[#4A2C36] leading-snug">"Bringing soul back to digital marketing through artistic expression."</p>
                    </div>
                </div>
            </div>
        </div>
    </section>

    <!-- Logo Bar -->
    <section class="py-16 bg-white/40 backdrop-blur-md overflow-hidden border-y border-pink-50">
        <div class="container mx-auto px-6">
            <div class="flex flex-wrap justify-center items-center gap-10 md:gap-20 opacity-30 grayscale contrast-125">
                <span class="text-xl md:text-2xl font-serif tracking-[0.4em] uppercase">CHANEL</span>
                <span class="text-xl md:text-2xl font-serif tracking-[0.4em] uppercase">DIOR</span>
                <span class="text-xl md:text-2xl font-serif tracking-[0.4em] uppercase text-center">VOGUE</span>
                <span class="text-xl md:text-2xl font-serif tracking-[0.4em] uppercase">GUCCI</span>
                <span class="text-xl md:text-2xl font-serif tracking-[0.4em] uppercase">PRADA</span>
            </div>
        </div>
    </section>

    <!-- About Section -->
    <section id="about" class="py-24 md:py-40 bg-white relative">
        <div class="container mx-auto px-6">
            <div class="grid grid-cols-1 lg:grid-cols-12 gap-16 md:gap-24 items-center">
                <div class="lg:col-span-6 relative">
                    <div class="absolute inset-0 bg-pink-100 rounded-[50px] rotate-3 -z-10 scale-105 opacity-30"></div>
                    <div class="rounded-[40px] overflow-hidden shadow-xl aspect-[3/4] border-8 border-white">
                        <img src="https://images.unsplash.com/photo-1594744803329-e58b31de8bf5?auto=format&fit=crop&q=80&w=800" alt="Identity" class="w-full h-full object-cover">
                    </div>
                </div>

                <div class="lg:col-span-6">
                    <div class="mb-10 md:mb-12">
                        <span class="font-script text-4xl text-[#9B5C73] mb-4 block">The Artist</span>
                        <h2 class="text-4xl md:text-6xl font-serif text-[#4A2C36] leading-tight">Feminine, Artistic, Soulful</h2>
                    </div>
                    <p class="text-xl md:text-2xl font-serif text-[#70505A] mb-8 leading-relaxed italic">
                        "I believe content shouldn't just be consumed; it should be felt."
                    </p>
                    <p class="text-base md:text-lg text-[#70505A]/80 mb-12 leading-relaxed font-light">
                        I am Kamaljeet Kour, known as <strong>punjaban.ugc</strong>. My journey is about blending my cultural heritage with a high-fashion romantic aesthetic. I help global brands move away from sterile marketing and toward emotional connections.
                    </p>

                    <div class="grid grid-cols-2 gap-8">
                        <div class="flex items-center space-x-4">
                            <div class="w-10 h-10 rounded-full bg-[#FAF5F7] flex items-center justify-center text-[#9B5C73] flex-shrink-0">
                                <i data-lucide="camera" class="w-4 h-4"></i>
                            </div>
                            <span class="text-[10px] font-bold uppercase tracking-widest text-[#4A2C36]">Creative Direction</span>
                        </div>
                        <div class="flex items-center space-x-4">
                            <div class="w-10 h-10 rounded-full bg-[#FAF5F7] flex items-center justify-center text-[#9B5C73] flex-shrink-0">
                                <i data-lucide="heart" class="w-4 h-4"></i>
                            </div>
                            <span class="text-[10px] font-bold uppercase tracking-widest text-[#4A2C36]">Romantic Styling</span>
                        </div>
                        <div class="flex items-center space-x-4">
                            <div class="w-10 h-10 rounded-full bg-[#FAF5F7] flex items-center justify-center text-[#9B5C73] flex-shrink-0">
                                <i data-lucide="video" class="w-4 h-4"></i>
                            </div>
                            <span class="text-[10px] font-bold uppercase tracking-widest text-[#4A2C36]">Luxury Editing</span>
                        </div>
                        <div class="flex items-center space-x-4">
                            <div class="w-10 h-10 rounded-full bg-[#FAF5F7] flex items-center justify-center text-[#9B5C73] flex-shrink-0">
                                <i data-lucide="trending-up" class="w-4 h-4"></i>
                            </div>
                            <span class="text-[10px] font-bold uppercase tracking-widest text-[#4A2C36]">Brand Strategy</span>
                        </div>
                    </div>
                </div>
            </div>
        </div>
    </section>

    <!-- Services Section -->
    <section id="services" class="py-24 md:py-40 bg-[#FAF5F7]">
        <div class="container mx-auto px-6">
            <div class="text-center mb-20">
                <span class="font-script text-4xl text-[#9B5C73] mb-4 block">Curated Services</span>
                <h2 class="text-4xl md:text-6xl font-serif text-[#4A2C36] leading-tight">Elevate Your Visual Identity</h2>
                <div class="h-px w-20 bg-pink-200 mx-auto mt-8"></div>
            </div>
            
            <div class="grid grid-cols-1 md:grid-cols-2 gap-10 md:gap-12 max-w-5xl mx-auto">
                <!-- Service Item -->
                <div class="p-10 md:p-12 rounded-[50px] bg-white border border-pink-50 shadow-sm transition-all duration-700 group flex flex-col items-center text-center hover:shadow-2xl hover:-translate-y-2">
                    <div class="mb-8 p-6 rounded-full bg-[#FAF5F7] text-[#9B5C73] transition-colors group-hover:bg-[#6D2E46] group-hover:text-white">
                        <i data-lucide="video" class="w-8 h-8"></i>
                    </div>
                    <span class="text-[10px] font-bold text-[#D9A7B3] uppercase tracking-[0.4em] mb-4">Video</span>
                    <h3 class="text-2xl md:text-3xl font-serif text-[#4A2C36] mb-6">Atmospheric Reels</h3>
                    <p class="text-[#70505A]/70 leading-relaxed text-sm md:base font-light mb-8 max-w-xs">Short-form video content that captures the 'mood' of your products through cinematic transitions and soft lighting.</p>
                    <button onclick="document.getElementById('contact').scrollIntoView({behavior: 'smooth'})" class="flex items-center space-x-2 text-[#9B5C73] font-bold text-xs uppercase tracking-widest">
                        <span>Request Pricing</span>
                        <i data-lucide="chevron-right" class="w-4 h-4"></i>
                    </button>
                </div>

                <!-- Service Item -->
                <div class="p-10 md:p-12 rounded-[50px] bg-white border border-pink-50 shadow-sm transition-all duration-700 group flex flex-col items-center text-center hover:shadow-2xl hover:-translate-y-2">
                    <div class="mb-8 p-6 rounded-full bg-[#FAF5F7] text-[#9B5C73] transition-colors group-hover:bg-[#6D2E46] group-hover:text-white">
                        <i data-lucide="camera" class="w-8 h-8"></i>
                    </div>
                    <span class="text-[10px] font-bold text-[#D9A7B3] uppercase tracking-[0.4em] mb-4">Visuals</span>
                    <h3 class="text-2xl md:text-3xl font-serif text-[#4A2C36] mb-6">Artistic Photography</h3>
                    <p class="text-[#70505A]/70 leading-relaxed text-sm md:base font-light mb-8 max-w-xs">Editorial lifestyle shots with a grainy, film-like aesthetic that tells a romantic brand story.</p>
                    <button onclick="document.getElementById('contact').scrollIntoView({behavior: 'smooth'})" class="flex items-center space-x-2 text-[#9B5C73] font-bold text-xs uppercase tracking-widest">
                        <span>Request Pricing</span>
                        <i data-lucide="chevron-right" class="w-4 h-4"></i>
                    </button>
                </div>
            </div>
        </div>
    </section>

    <!-- Portfolio Section -->
    <section id="work" class="py-24 md:py-40 bg-white">
        <div class="container mx-auto px-6">
            <div class="text-center mb-20">
                <span class="font-script text-4xl text-[#9B5C73] mb-4 block">Art Gallery</span>
                <h2 class="text-4xl md:text-6xl font-serif text-[#4A2C36] leading-tight">Bespoke Visual Stories</h2>
                <div class="h-px w-20 bg-pink-200 mx-auto mt-8"></div>
            </div>

            <div class="grid grid-cols-1 md:grid-cols-2 lg:grid-cols-3 gap-8 md:gap-10">
                <!-- Portfolio Card -->
                <div class="portfolio-card relative group overflow-hidden rounded-[40px] cursor-pointer shadow-lg aspect-[4/5] border-8 border-white">
                    <img src="https://images.unsplash.com/photo-1490481651871-ab68de25d43d?auto=format&fit=crop&q=80&w=800" class="w-full h-full object-cover grayscale-[20%]" alt="Work">
                    <div class="absolute inset-0 bg-gradient-to-t from-[#4A2C36]/80 via-transparent to-transparent opacity-0 group-hover:opacity-100 transition-all duration-700 flex flex-col justify-end p-8 md:p-10">
                        <span class="font-script text-2xl text-white mb-2">Midnight Silk</span>
                        <p class="text-white/70 text-[10px] uppercase tracking-widest font-bold">Campaign 2024</p>
                    </div>
                </div>
                <!-- Portfolio Card -->
                <div class="portfolio-card relative group overflow-hidden rounded-[40px] cursor-pointer shadow-lg aspect-[4/5] border-8 border-white">
                    <img src="https://images.unsplash.com/photo-1537905569824-f89f14cceb68?auto=format&fit=crop&q=80&w=800" class="w-full h-full object-cover grayscale-[20%]" alt="Work">
                    <div class="absolute inset-0 bg-gradient-to-t from-[#4A2C36]/80 via-transparent to-transparent opacity-0 group-hover:opacity-100 transition-all duration-700 flex flex-col justify-end p-8 md:p-10">
                        <span class="font-script text-2xl text-white mb-2">Morning Glow</span>
                        <p class="text-white/70 text-[10px] uppercase tracking-widest font-bold">Campaign 2024</p>
                    </div>
                </div>
                <!-- Portfolio Card -->
                <div class="portfolio-card relative group overflow-hidden rounded-[40px] cursor-pointer shadow-lg aspect-[4/5] border-8 border-white">
                    <img src="https://images.unsplash.com/photo-1515886657613-9f3515b0c78f?auto=format&fit=crop&q=80&w=800" class="w-full h-full object-cover grayscale-[20%]" alt="Work">
                    <div class="absolute inset-0 bg-gradient-to-t from-[#4A2C36]/80 via-transparent to-transparent opacity-0 group-hover:opacity-100 transition-all duration-700 flex flex-col justify-end p-8 md:p-10">
                        <span class="font-script text-2xl text-white mb-2">Mauve Moments</span>
                        <p class="text-white/70 text-[10px] uppercase tracking-widest font-bold">Campaign 2024</p>
                    </div>
                </div>
            </div>
        </div>
    </section>

    <!-- Contact Section -->
    <section id="contact" class="py-24 md:py-40 bg-[#F4E4E8] relative overflow-hidden">
        <div class="watercolor-blob top-[-20%] left-[-10%] w-[60%] h-[60%] opacity-40" style="background-color: #B97A8D;"></div>
        
        <div class="container mx-auto px-6 relative z-10">
            <div class="max-w-6xl mx-auto grid grid-cols-1 lg:grid-cols-2 gap-16 md:gap-20 bg-white/40 backdrop-blur-3xl rounded-[40px] md:rounded-[60px] p-8 md:p-16 lg:p-24 border border-white shadow-2xl">
                <div>
                    <span class="font-script text-4xl text-[#9B5C73] block mb-6">Let's Create...</span>
                    <h2 class="text-4xl md:text-6xl font-serif text-[#4A2C36] mb-8 leading-tight">Something truly <br /><span class="italic">beautiful.</span></h2>
                    <p class="text-base md:text-lg text-[#70505A] mb-12 font-light leading-relaxed">
                        Accepting inquiries for fashion, beauty, and luxury lifestyle brands looking for an artistic, feminine touch.
                    </p>
                    
                    <div class="space-y-8">
                        <div class="flex items-center space-x-6">
                            <div class="w-12 h-12 md:w-14 md:h-14 rounded-full bg-white flex items-center justify-center text-[#9B5C73] shadow-sm flex-shrink-0">
                                <i data-lucide="mail" class="w-6 h-6"></i>
                            </div>
                            <div>
                                <p class="text-[10px] text-[#D9A7B3] uppercase font-bold tracking-[0.2em]">Email Me</p>
                                <p class="text-lg md:text-xl font-serif text-[#4A2C36]">punjabanugc06@gmail.com</p>
                            </div>
                        </div>
                        <div class="flex items-center space-x-6">
                            <div class="w-12 h-12 md:w-14 md:h-14 rounded-full bg-white flex items-center justify-center text-[#9B5C73] shadow-sm flex-shrink-0">
                                <i data-lucide="instagram" class="w-6 h-6"></i>
                            </div>
                            <div>
                                <p class="text-[10px] text-[#D9A7B3] uppercase font-bold tracking-[0.2em]">Connect</p>
                                <p class="text-lg md:text-xl font-serif text-[#4A2C36]">@punjaban.ugc</p>
                            </div>
                        </div>
                    </div>
                </div>

                <form action="https://formsubmit.co/punjabanugc06@gmail.com" method="POST" class="space-y-8 mt-12 lg:mt-0">
                    <input type="hidden" name="_subject" value="New Collaboration Inquiry - Punjaban.ugc">
                    <input type="hidden" name="_template" value="box">
                    <input type="hidden" name="_autoresponse" value="Thank you for reaching out to Punjaban.ugc. I have received your message and will get back to you shortly.">

                    <div class="space-y-2">
                        <label class="text-[10px] uppercase tracking-[0.3em] font-bold text-[#9B5C73]">Who are you?</label>
                        <input type="text" name="name" required placeholder="Name or Brand Name" class="w-full bg-white/50 border-b border-pink-200 py-4 focus:border-[#6D2E46] outline-none transition-all placeholder:text-[#D9A7B3]/50 font-serif text-lg">
                    </div>
                    <div class="space-y-2">
                        <label class="text-[10px] uppercase tracking-[0.3em] font-bold text-[#9B5C73]">Reach you at</label>
                        <input type="email" name="email" required placeholder="Email Address" class="w-full bg-white/50 border-b border-pink-200 py-4 focus:border-[#6D2E46] outline-none transition-all placeholder:text-[#D9A7B3]/50 font-serif text-lg">
                    </div>
                    <div class="space-y-2">
                        <label class="text-[10px] uppercase tracking-[0.3em] font-bold text-[#9B5C73]">The Vision</label>
                        <textarea name="message" required placeholder="Tell me your story..." rows="4" class="w-full bg-white/50 border-b border-pink-200 py-4 focus:border-[#6D2E46] outline-none transition-all placeholder:text-[#D9A7B3]/50 font-serif text-lg resize-none"></textarea>
                    </div>
                    <button type="submit" class="w-full py-5 md:py-6 rounded-full bg-[#6D2E46] text-white font-bold tracking-[0.3em] uppercase text-xs hover:shadow-2xl hover:shadow-[#6D2E46]/30 transition-all duration-700">
                        Send Love Note
                    </button>
                </form>
            </div>
        </div>
    </section>

    <!-- Footer -->
    <footer class="py-16 bg-[#FAF5F7] border-t border-pink-50 text-center">
        <div class="container mx-auto px-6">
            <div class="text-4xl md:text-5xl font-script text-[#4A2C36] mb-6">
                Punjaban<span class="text-[#9B5C73] text-xl">.ugc</span>
            </div>
            <div class="w-12 h-px bg-pink-200 mx-auto mb-8"></div>
            <div class="text-[#B97A8D] text-[10px] font-bold uppercase tracking-[0.4em] mb-8">
                Designed for Soft Luxury Brands
            </div>
            <div class="flex justify-center space-x-10 text-[#70505A]">
                <a href="https://instagram.com/punjaban.ugc" target="_blank" class="hover:text-[#6D2E46] transition-colors"><i data-lucide="instagram" class="w-5 h-5"></i></a>
                <a href="mailto:punjabanugc06@gmail.com" class="hover:text-[#6D2E46] transition-colors"><i data-lucide="mail" class="w-5 h-5"></i></a>
                <a href="#contact" class="hover:text-[#6D2E46] transition-colors"><i data-lucide="heart" class="w-5 h-5"></i></a>
            </div>
            <p class="mt-12 text-[10px] text-[#D9A7B3] uppercase tracking-[0.2em]">© 2024 Punjaban.ugc - All Rights Reserved</p>
        </div>
    </footer>

    <script>
        // Initialize Icons
        lucide.createIcons();

        // Navbar Scroll Effect
        const navbar = document.getElementById('navbar');
        window.addEventListener('scroll', () => {
            if (window.scrollY > 50) {
                navbar.classList.add('nav-scrolled');
                navbar.querySelector('.container > div').classList.add('bg-white/40', 'backdrop-blur-xl', 'shadow-sm', 'border-white/40');
            } else {
                navbar.classList.remove('nav-scrolled');
                navbar.querySelector('.container > div').classList.remove('bg-white/40', 'backdrop-blur-xl', 'shadow-sm', 'border-white/40');
            }
        });

        // Mobile Menu Toggle
        const menuBtn = document.getElementById('menu-btn');
        const mobileMenu = document.getElementById('mobile-menu');
        menuBtn.addEventListener('click', () => {
            mobileMenu.classList.toggle('hidden');
        });

        // Close menu on link click
        document.querySelectorAll('#mobile-menu a').forEach(link => {
            link.addEventListener('click', () => {
                mobileMenu.classList.add('hidden');
            });
        });
    </script>
</body>
</html>
