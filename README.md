import React, { useState, useEffect } from 'react';
import { motion, AnimatePresence } from 'framer-motion';
import { 
  Instagram, 
  Mail, 
  ArrowRight, 
  Camera, 
  Video, 
  Star, 
  TrendingUp, 
  Users, 
  Smartphone, 
  ShoppingBag,
  ChevronRight,
  Menu,
  X,
  Heart
} from 'lucide-react';

// --- Global Styles & Brand Identity ---
const brand = {
  colors: {
    wine: "#6D2E46",
    dustyRose: "#9B5C73",
    mauvePink: "#B97A8D",
    blush: "#D9A7B3",
    nude: "#E8C9D0",
    cream: "#FAF5F7",
    plumBrown: "#4A2C36",
    femBrown: "#70505A",
    roseGold: "#C88A9B",
  },
  fonts: {
    script: "'Parisienne', cursive",
    serif: "'Cormorant Garamond', serif",
    sans: "'Manrope', sans-serif"
  }
};

// --- Components ---

const GrainOverlay = () => (
  <div className="fixed inset-0 pointer-events-none z-[9999] opacity-[0.03]" 
       style={{ backgroundImage: `url('https://grainy-gradients.vercel.app/noise.svg')` }} />
);

const WatercolorBlob = ({ className, color = brand.colors.blush }) => (
  <div className={`absolute rounded-full blur-[100px] opacity-20 pointer-events-none -z-10 ${className}`}
       style={{ backgroundColor: color }} />
);

const Navbar = () => {
  const [isOpen, setIsOpen] = useState(false);
  const [scrolled, setScrolled] = useState(false);

  useEffect(() => {
    const handleScroll = () => setScrolled(window.scrollY > 50);
    window.addEventListener('scroll', handleScroll);
    return () => window.removeEventListener('scroll', handleScroll);
  }, []);

  const navLinks = [
    { name: 'Story', href: '#about' },
    { name: 'Offerings', href: '#services' },
    { name: 'Gallery', href: '#work' },
    { name: 'Results', href: '#stats' },
    { name: 'Contact', href: '#contact' }
  ];

  return (
    <nav className={`fixed top-0 w-full z-50 transition-all duration-700 ${scrolled ? 'py-4' : 'py-8'}`}>
      <div className="container mx-auto px-6">
        <div className={`flex items-center justify-between px-8 py-3 rounded-full transition-all duration-700 ${scrolled ? 'bg-white/40 backdrop-blur-xl shadow-sm border border-white/40' : 'bg-transparent'}`}>
          <div className="text-2xl md:text-3xl font-script tracking-tight text-[#4A2C36] flex items-center gap-1">
            Punjaban<span className="text-[#9B5C73] text-lg mt-2">.ugc</span>
          </div>
          
          <div className="hidden md:flex items-center space-x-10">
            {navLinks.map((link) => (
              <a key={link.name} href={link.href} className="text-[10px] font-bold uppercase tracking-[0.3em] text-[#70505A] hover:text-[#6D2E46] transition-colors">
                {link.name}
              </a>
            ))}
            <button 
              onClick={() => document.getElementById('contact').scrollIntoView({ behavior: 'smooth' })}
              className="px-7 py-2.5 rounded-full bg-[#6D2E46] text-white text-xs font-bold uppercase tracking-widest hover:shadow-lg hover:shadow-[#6D2E46]/20 transition-all duration-500"
            >
              Collab
            </button>
          </div>

          <button className="md:hidden text-[#4A2C36]" onClick={() => setIsOpen(!isOpen)}>
            {isOpen ? <X size={24} /> : <Menu size={24} />}
          </button>
        </div>
      </div>

      <AnimatePresence>
        {isOpen && (
          <motion.div
            initial={{ opacity: 0, scale: 0.95 }}
            animate={{ opacity: 1, scale: 1 }}
            exit={{ opacity: 0, scale: 0.95 }}
            className="absolute top-full left-0 w-full bg-white/95 backdrop-blur-2xl md:hidden py-12 px-6 shadow-2xl border-b border-pink-50"
          >
            <div className="flex flex-col items-center space-y-8">
              {navLinks.map((link) => (
                <a 
                  key={link.name} 
                  href={link.href} 
                  onClick={() => setIsOpen(false)}
                  className="text-2xl font-serif text-[#4A2C36]"
                >
                  {link.name}
                </a>
              ))}
              <button 
                onClick={() => { setIsOpen(false); document.getElementById('contact').scrollIntoView({ behavior: 'smooth' }); }}
                className="w-full py-4 rounded-full bg-[#6D2E46] text-white font-bold tracking-widest uppercase text-xs"
              >
                Inquire Now
              </button>
            </div>
          </motion.div>
        )}
      </AnimatePresence>
    </nav>
  );
};

const SectionHeading = ({ subtitle, title, centered = true }) => (
  <div className={`mb-20 ${centered ? 'text-center' : 'text-left'}`}>
    <motion.span 
      initial={{ opacity: 0, y: 15 }}
      whileInView={{ opacity: 1, y: 0 }}
      viewport={{ once: true }}
      className="font-script text-3xl text-[#9B5C73] mb-2 block"
    >
      {subtitle}
    </motion.span>
    <motion.h2 
      initial={{ opacity: 0, y: 20 }}
      whileInView={{ opacity: 1, y: 0 }}
      viewport={{ once: true }}
      transition={{ delay: 0.2, duration: 1 }}
      className="text-4xl md:text-6xl font-serif text-[#4A2C36] leading-tight"
    >
      {title}
    </motion.h2>
    {centered && <div className="h-px w-20 bg-pink-200 mx-auto mt-8" />}
  </div>
);

const Hero = () => {
  return (
    <section className="relative min-h-screen flex items-center pt-28 pb-12 overflow-hidden bg-[#FAF5F7]">
      <WatercolorBlob className="top-[-10%] right-[-5%] w-[60%] h-[60%] opacity-30" color="#EFD5DB" />
      <WatercolorBlob className="bottom-[10%] left-[-10%] w-[50%] h-[50%]" color="#E6B7C1" />

      <div className="container mx-auto px-6 grid grid-cols-1 lg:grid-cols-2 gap-12 items-center relative z-10">
        <motion.div
          initial={{ opacity: 0, y: 30 }}
          animate={{ opacity: 1, y: 0 }}
          transition={{ duration: 1.5, ease: [0.16, 1, 0.3, 1] }}
          className="max-w-full overflow-hidden"
        >
          <div className="flex items-center space-x-4 mb-8">
            <span className="h-[1px] w-12 bg-[#9B5C73]" />
            <span className="text-[#9B5C73] font-bold tracking-[0.4em] uppercase text-[10px]">UGC & Brand Storytelling</span>
          </div>
          
          <h1 className="text-6xl md:text-7xl lg:text-8xl font-script text-[#4A2C36] leading-[1.1] mb-6 pr-4">
            punjaban<span className="text-[#9B5C73]">.</span>ugc
          </h1>
          
          <h2 className="text-2xl md:text-3xl font-serif italic text-[#70505A] mb-10 max-w-md">
            Soft luxury visuals for romantic & fashion-forward brands.
          </h2>
          
          <div className="flex flex-wrap gap-4 md:gap-6">
            <button 
              onClick={() => document.getElementById('work').scrollIntoView({ behavior: 'smooth' })}
              className="px-8 md:px-12 py-4 md:py-5 rounded-full bg-gradient-to-r from-[#6D2E46] to-[#9B5C73] text-white text-[10px] md:text-xs font-bold tracking-widest uppercase hover:shadow-xl hover:shadow-[#6D2E46]/20 transition-all duration-700 flex items-center space-x-3 group"
            >
              <span>View Portfolio</span>
              <ArrowRight size={16} className="group-hover:translate-x-1 transition-transform" />
            </button>
            <button 
              onClick={() => document.getElementById('contact').scrollIntoView({ behavior: 'smooth' })}
              className="px-8 md:px-12 py-4 md:py-5 rounded-full bg-white text-[#6D2E46] text-[10px] md:text-xs font-bold tracking-widest uppercase border border-pink-100 hover:bg-pink-50/50 transition-all duration-700 shadow-sm"
            >
              Work With Me
            </button>
          </div>

          <div className="mt-16 md:mt-20 flex items-center space-x-8 md:space-x-12 opacity-80">
            <div className="flex flex-col">
              <span className="text-3xl md:text-4xl font-serif text-[#4A2C36]">150+</span>
              <span className="text-[10px] text-[#70505A] uppercase tracking-widest font-bold">Campaigns</span>
            </div>
            <div className="h-10 w-px bg-pink-100" />
            <div className="flex flex-col">
              <span className="text-3xl md:text-4xl font-serif text-[#4A2C36]">4.8M</span>
              <span className="text-[10px] text-[#70505A] uppercase tracking-widest font-bold">Impressions</span>
            </div>
          </div>
        </motion.div>

        <motion.div
          initial={{ opacity: 0, scale: 0.98 }}
          animate={{ opacity: 1, scale: 1 }}
          transition={{ duration: 2, ease: "easeOut" }}
          className="relative mt-8 lg:mt-0"
        >
          {/* Magazine Layout Visual */}
          <div className="relative z-10 w-full aspect-[4/5] rounded-[20px] overflow-hidden shadow-2xl p-4 bg-white">
             <div className="w-full h-full rounded-[10px] overflow-hidden relative">
                <div className="absolute inset-0 bg-gradient-to-t from-[#6D2E46]/20 to-transparent mix-blend-multiply" />
                <img 
                  src="https://images.unsplash.com/photo-1512436991641-6745cdb1723f?auto=format&fit=crop&q=80&w=800" 
                  alt="Portfolio" 
                  className="w-full h-full object-cover grayscale-[20%]"
                />
             </div>
          </div>
          
          <motion.div 
            animate={{ y: [0, -10, 0] }}
            transition={{ duration: 6, repeat: Infinity, ease: "easeInOut" }}
            className="absolute -bottom-6 md:-bottom-10 -right-4 md:-right-6 z-20 p-6 md:p-8 rounded-[30px] bg-white/60 backdrop-blur-xl border border-white shadow-2xl max-w-[200px] md:max-w-[240px]"
          >
            <Heart className="text-[#9B5C73] mb-4" size={20} fill="#9B5C73" />
            <p className="text-base md:text-lg font-serif italic text-[#4A2C36] leading-snug">"Bringing soul back to digital marketing through artistic expression."</p>
          </motion.div>
        </motion.div>
      </div>
    </section>
  );
};

const About = () => {
  return (
    <section id="about" className="py-24 md:py-40 bg-white relative">
      <div className="container mx-auto px-6">
        <div className="grid grid-cols-1 lg:grid-cols-12 gap-16 md:gap-24 items-center">
          <div className="lg:col-span-6 relative">
            <div className="absolute inset-0 bg-pink-100 rounded-[50px] -rotate-3 -z-10 scale-105 opacity-30" />
            <motion.div
              initial={{ opacity: 0 }}
              whileInView={{ opacity: 1 }}
              viewport={{ once: true }}
              transition={{ duration: 1.5 }}
              className="rounded-[40px] overflow-hidden shadow-xl aspect-[3/4]"
            >
              <img src="https://images.unsplash.com/photo-1594744803329-e58b31de8bf5?auto=format&fit=crop&q=80&w=800" alt="Identity" className="w-full h-full object-cover" />
            </motion.div>
          </div>

          <div className="lg:col-span-6">
            <SectionHeading subtitle="The Artist" title="Feminine, Artistic, Soulful" centered={false} />
            <p className="text-xl md:text-2xl font-serif text-[#70505A] mb-8 md:10 leading-relaxed italic">
              "I believe content shouldn't just be consumed; it should be felt."
            </p>
            <p className="text-base md:text-lg text-[#70505A]/80 mb-12 leading-relaxed font-light">
              I am Kamaljeet Kour, known as <strong>punjaban.ugc</strong>. My journey is about blending my cultural heritage with a high-fashion romantic aesthetic. I help global brands move away from sterile marketing and toward emotional connections.
            </p>

            <div className="grid grid-cols-2 gap-6 md:gap-8">
              {[
                { label: 'Creative Direction', icon: <Camera size={18}/> },
                { label: 'Romantic Styling', icon: <Heart size={18}/> },
                { label: 'Luxury Editing', icon: <Video size={18}/> },
                { label: 'Brand Strategy', icon: <TrendingUp size={18}/> },
              ].map((item, idx) => (
                <div key={idx} className="flex items-center space-x-4">
                  <div className="w-10 h-10 rounded-full bg-[#FAF5F7] flex items-center justify-center text-[#9B5C73]">
                    {item.icon}
                  </div>
                  <span className="text-[10px] font-bold uppercase tracking-widest text-[#4A2C36]">{item.label}</span>
                </div>
              ))}
            </div>
          </div>
        </div>
      </div>
    </section>
  );
};

const Services = () => {
  const services = [
    {
      title: "Atmospheric Reels",
      desc: "Short-form video content that captures the 'mood' of your products through cinematic transitions and soft lighting.",
      icon: <Video className="w-8 h-8" />,
      tag: "Video"
    },
    {
      title: "Artistic Photography",
      desc: "Editorial lifestyle shots with a grainy, film-like aesthetic that tells a romantic brand story.",
      icon: <Camera className="w-8 h-8" />,
      tag: "Visuals"
    },
    {
      title: "Bespoke Media Kits",
      desc: "Custom-designed influencer presentations that mirror your brand's luxury identity and values.",
      icon: <Star className="w-8 h-8" />,
      tag: "Strategic"
    },
    {
      title: "Emotional Reviews",
      desc: "Authentic, soft-spoken testimonial content that resonates with heart-led consumers.",
      icon: <Users className="w-8 h-8" />,
      tag: "Authentic"
    }
  ];

  return (
    <section id="services" className="py-24 md:py-40 bg-[#FAF5F7]">
      <div className="container mx-auto px-6">
        <SectionHeading subtitle="Curated Services" title="Elevate Your Visual Identity" />
        
        <div className="grid grid-cols-1 md:grid-cols-2 gap-12 max-w-5xl mx-auto">
          {services.map((s, idx) => (
            <motion.div
              key={idx}
              whileHover={{ y: -8 }}
              className="p-10 md:p-12 rounded-[50px] bg-white border border-pink-50 shadow-sm hover:shadow-2xl transition-all duration-700 group flex flex-col items-center text-center"
            >
              <div className="mb-8 p-6 rounded-full bg-[#FAF5F7] text-[#9B5C73] transition-colors group-hover:bg-[#6D2E46] group-hover:text-white">
                {s.icon}
              </div>
              <span className="text-[10px] font-bold text-[#D9A7B3] uppercase tracking-[0.4em] mb-4">{s.tag}</span>
              <h3 className="text-2xl md:text-3xl font-serif text-[#4A2C36] mb-6">{s.title}</h3>
              <p className="text-[#70505A]/70 leading-relaxed text-sm md:base font-light mb-8 max-w-xs">{s.desc}</p>
              <button 
                onClick={() => document.getElementById('contact').scrollIntoView({ behavior: 'smooth' })}
                className="flex items-center space-x-2 text-[#9B5C73] font-bold text-xs uppercase tracking-widest group"
              >
                <span>Request Pricing</span>
                <ChevronRight size={14} className="group-hover:translate-x-1 transition-transform" />
              </button>
            </motion.div>
          ))}
        </div>
      </div>
    </section>
  );
};

const Portfolio = () => {
  const images = [
    { url: "https://images.unsplash.com/photo-1490481651871-ab68de25d43d?auto=format&fit=crop&q=80&w=800", title: "Midnight Silk" },
    { url: "https://images.unsplash.com/photo-1537905569824-f89f14cceb68?auto=format&fit=crop&q=80&w=800", title: "Morning Glow" },
    { url: "https://images.unsplash.com/photo-1524250502761-1ac6f2e30d43?auto=format&fit=crop&q=80&w=800", title: "Soft Linens" },
    { url: "https://images.unsplash.com/photo-1515886657613-9f3515b0c78f?auto=format&fit=crop&q=80&w=800", title: "Mauve Moments" },
    { url: "https://images.unsplash.com/photo-1509631179647-0177331693ae?auto=format&fit=crop&q=80&w=800", title: "Parisian Chic" },
    { url: "https://images.unsplash.com/photo-1539109136881-3be0616acf4b?auto=format&fit=crop&q=80&w=800", title: "Luxury Skin" },
  ];

  return (
    <section id="work" className="py-24 md:py-40 bg-white">
      <div className="container mx-auto px-6">
        <SectionHeading subtitle="Art Gallery" title="Bespoke Visual Stories" />

        <div className="columns-1 md:columns-2 lg:columns-3 gap-8 md:gap-10">
          {images.map((img, i) => (
            <motion.div 
              key={i}
              initial={{ opacity: 0 }}
              whileInView={{ opacity: 1 }}
              viewport={{ once: true }}
              className="relative group mb-10 overflow-hidden rounded-[30px] cursor-pointer shadow-lg"
            >
              <div className="absolute inset-0 bg-[#6D2E46]/10 opacity-0 group-hover:opacity-100 transition-opacity duration-700 z-10" />
              <img src={img.url} alt={img.title} className="w-full h-auto transform group-hover:scale-105 transition-all duration-[1.5s]" />
              <div className="absolute inset-0 bg-gradient-to-t from-[#4A2C36]/80 via-transparent to-transparent opacity-0 group-hover:opacity-100 transition-all duration-700 z-20 flex flex-col justify-end p-8 md:p-10">
                <span className="font-script text-2xl text-white mb-2">{img.title}</span>
                <p className="text-white/70 text-[10px] uppercase tracking-widest font-bold">Campaign 2024</p>
              </div>
            </motion.div>
          ))}
        </div>
      </div>
    </section>
  );
};

const Contact = () => {
  return (
    <section id="contact" className="py-24 md:py-40 bg-[#F4E4E8] relative overflow-hidden">
      <WatercolorBlob className="top-[-20%] left-[-10%] w-[60%] h-[60%] opacity-40" color="#B97A8D" />
      
      <div className="container mx-auto px-6 relative z-10">
        <div className="max-w-6xl mx-auto grid grid-cols-1 lg:grid-cols-2 gap-16 md:gap-20 bg-white/40 backdrop-blur-3xl rounded-[40px] md:rounded-[60px] p-8 md:p-24 border border-white shadow-2xl">
          <div>
            <span className="font-script text-3xl md:text-4xl text-[#9B5C73] block mb-4">Let's Create...</span>
            <h2 className="text-4xl md:text-6xl font-serif text-[#4A2C36] mb-8 md:10 leading-tight">Something truly <br /><span className="italic">beautiful.</span></h2>
            <p className="text-base md:text-lg text-[#70505A] mb-12 font-light leading-relaxed">
              Accepting inquiries for fashion, beauty, and luxury lifestyle brands looking for an artistic, feminine touch.
            </p>
            
            <div className="space-y-6 md:space-y-8">
              <div className="flex items-center space-x-6">
                <div className="w-12 h-12 md:w-14 md:h-14 rounded-full bg-white flex items-center justify-center text-[#9B5C73] shadow-sm">
                  <Mail size={24} />
                </div>
                <div>
                  <p className="text-[10px] text-[#D9A7B3] uppercase font-bold tracking-[0.2em]">Email Me</p>
                  <p className="text-lg md:text-xl font-serif text-[#4A2C36]">punjabanugc06@gmail.com</p>
                </div>
              </div>
              <div className="flex items-center space-x-6">
                <div className="w-12 h-12 md:w-14 md:h-14 rounded-full bg-white flex items-center justify-center text-[#9B5C73] shadow-sm">
                  <Instagram size={24} />
                </div>
                <div>
                  <p className="text-[10px] text-[#D9A7B3] uppercase font-bold tracking-[0.2em]">Connect</p>
                  <p className="text-lg md:text-xl font-serif text-[#4A2C36]">@punjaban.ugc</p>
                </div>
              </div>
            </div>
          </div>

          {/* Connected to punjabanugc06@gmail.com using FormSubmit */}
          <form action="https://formsubmit.co/punjabanugc06@gmail.com" method="POST" className="space-y-6 md:space-y-8 mt-12 lg:mt-0">
            {/* FormSubmit Configuration */}
            <input type="hidden" name="_subject" value="New Collaboration Inquiry - Punjaban.ugc" />
            <input type="hidden" name="_template" value="box" />
            <input type="hidden" name="_autoresponse" value="Thank you for reaching out to Punjaban.ugc. I have received your message and will get back to you shortly." />

            <div className="space-y-2">
              <label className="text-[10px] uppercase tracking-[0.3em] font-bold text-[#9B5C73]">Who are you?</label>
              <input 
                type="text" 
                name="name" 
                required 
                placeholder="Name or Brand Name" 
                className="w-full bg-white/50 border-b border-pink-200 py-4 focus:border-[#6D2E46] outline-none transition-all placeholder:text-[#D9A7B3]/50 font-serif text-lg" 
              />
            </div>
            <div className="space-y-2">
              <label className="text-[10px] uppercase tracking-[0.3em] font-bold text-[#9B5C73]">Reach you at</label>
              <input 
                type="email" 
                name="email" 
                required 
                placeholder="Email Address" 
                className="w-full bg-white/50 border-b border-pink-200 py-4 focus:border-[#6D2E46] outline-none transition-all placeholder:text-[#D9A7B3]/50 font-serif text-lg" 
              />
            </div>
            <div className="space-y-2">
              <label className="text-[10px] uppercase tracking-[0.3em] font-bold text-[#9B5C73]">The Vision</label>
              <textarea 
                name="message" 
                required 
                placeholder="Tell me your story..." 
                rows="4" 
                className="w-full bg-white/50 border-b border-pink-200 py-4 focus:border-[#6D2E46] outline-none transition-all placeholder:text-[#D9A7B3]/50 font-serif text-lg resize-none"
              ></textarea>
            </div>
            <button type="submit" className="w-full py-5 md:py-6 rounded-full bg-[#6D2E46] text-white font-bold tracking-[0.3em] uppercase text-xs hover:shadow-2xl hover:shadow-[#6D2E46]/30 transition-all duration-700">
              Send Love Note
            </button>
          </form>
        </div>
      </div>
    </section>
  );
};

const Footer = () => (
  <footer className="py-16 bg-[#FAF5F7] border-t border-pink-50 text-center">
    <div className="container mx-auto px-6">
      <div className="text-3xl md:text-4xl font-script text-[#4A2C36] mb-6">
        Punjaban<span className="text-[#9B5C73] text-xl">.ugc</span>
      </div>
      <div className="w-12 h-px bg-pink-200 mx-auto mb-8" />
      <div className="text-[#B97A8D] text-[10px] font-bold uppercase tracking-[0.4em] mb-8">
        Designed for Soft Luxury Brands
      </div>
      <div className="flex justify-center space-x-10 text-[#70505A]">
        <a href="https://instagram.com/punjaban.ugc" target="_blank" rel="noreferrer" className="hover:text-[#6D2E46] transition-colors"><Instagram size={20} /></a>
        <a href="mailto:punjabanugc06@gmail.com" className="hover:text-[#6D2E46] transition-colors"><Mail size={20} /></a>
        <a href="#contact" className="hover:text-[#6D2E46] transition-colors"><Heart size={20} /></a>
      </div>
      <p className="mt-12 text-[10px] text-[#D9A7B3] uppercase tracking-[0.2em]">© 2024 Punjaban.ugc - All Rights Reserved</p>
    </div>
  </footer>
);

export default function App() {
  return (
    <div className="font-sans text-[#4A2C36] selection:bg-[#6D2E46]/10 selection:text-[#6D2E46] bg-[#FAF5F7]">
      <style>{`
        @import url('https://fonts.googleapis.com/css2?family=Parisienne&family=Cormorant+Garamond:ital,wght@0,300;0,400;0,500;0,600;0,700;1,400&family=Manrope:wght@300;400;500;600;700&display=swap');
        
        .font-script { font-family: 'Parisienne', cursive; }
        .font-serif { font-family: 'Cormorant Garamond', serif; }
        .font-sans { font-family: 'Manrope', sans-serif; }
        
        html { scroll-behavior: smooth; }
        
        ::-webkit-scrollbar {
          width: 5px;
        }
        ::-webkit-scrollbar-track {
          background: #FAF5F7;
        }
        ::-webkit-scrollbar-thumb {
          background: #D9A7B3;
          border-radius: 10px;
        }

        /* Watercolor animation */
        @keyframes drift {
          0% { transform: translate(0, 0) scale(1); }
          50% { transform: translate(20px, 20px) scale(1.1); }
          100% { transform: translate(0, 0) scale(1); }
        }
      `}</style>
      
      <GrainOverlay />
      <Navbar />
      <main>
        <Hero />
        <section className="py-12 md:py-20 bg-white/30 backdrop-blur-md overflow-hidden flex justify-center">
            <div className="flex space-x-12 md:space-x-20 opacity-30 grayscale contrast-125">
                 {['CHANEL', 'DIOR', 'VOGUE', 'GUCCI', 'HERMÈS', 'PRADA'].map(l => (
                     <span key={l} className="text-xl md:text-3xl font-serif tracking-[0.4em]">{l}</span>
                 ))}
            </div>
        </section>
        <About />
        <Services />
        <Portfolio />
        <Contact />
      </main>
      <Footer />
    </div>
  );
}
