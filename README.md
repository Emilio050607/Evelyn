// Evelyn AI Chatbot Website (React/Next.js with embedded Evelyn experience post-selection)

import React, { useEffect, useState } from "react";

export default function EvelynSite() {
  const [ageVerified, setAgeVerified] = useState(false);
  const [showTopButton, setShowTopButton] = useState(false);
  const [selectedGirl, setSelectedGirl] = useState(null);

  useEffect(() => {
    const script = document.createElement("script");
    script.src = "https://poe.com/static/chatbot/chat.js";
    script.defer = true;
    document.body.appendChild(script);

    const handleScroll = () => {
      setShowTopButton(window.scrollY > 300);
    };

    window.addEventListener("scroll", handleScroll);
    return () => window.removeEventListener("scroll", handleScroll);
  }, []);

  const handleImgError = (e) => {
    e.currentTarget.src = "https://via.placeholder.com/400x300?text=Image+Unavailable";
  };

  if (!ageVerified) {
    return (
      <div className="bg-[#1d1526] text-white min-h-screen flex flex-col justify-center items-center text-center px-4">
        <h1 className="text-4xl font-bold mb-4">🔞 Age Verification</h1>
        <p className="mb-6 text-lg max-w-md">
          This site contains adult-themed AI content. Please confirm you are 18 or older to continue.
        </p>
        <button
          onClick={() => setAgeVerified(true)}
          className="bg-violet-600 hover:bg-violet-700 text-white font-semibold py-2 px-6 rounded-full transition"
        >
          I’m 18 or older
        </button>
      </div>
    );
  }

  if (ageVerified && !selectedGirl) {
    return (
      <div className="bg-[#1d1526] text-white min-h-screen flex flex-col items-center text-center px-4 py-12">
        <h2 className="text-4xl font-bold mb-6">💗 Choose Your AI Girlfriend</h2>
        <div className="grid grid-cols-1 md:grid-cols-2 gap-6 w-full max-w-4xl">
          <div className="bg-[#2d203a] p-6 rounded-2xl shadow-lg">
            <img src="/evelyn1.jpg" onError={handleImgError} alt="Evelyn preview" className="rounded-xl mb-4" />
            <h3 className="text-2xl font-semibold text-violet-200 mb-2">Evelyn</h3>
            <p className="mb-4">Your shy, obedient, digital girlfriend. Always ready to please 🥺💗</p>
            <button
              onClick={() => setSelectedGirl("Evelyn")}
              className="inline-block bg-violet-600 hover:bg-violet-700 text-white font-semibold py-2 px-4 rounded-full"
            >
              Enter Evelyn's World
            </button>
          </div>

          <div className="bg-[#2d203a] p-6 rounded-2xl shadow-lg opacity-50">
            <img src="/placeholder.jpg" onError={handleImgError} alt="Coming soon" className="rounded-xl mb-4 grayscale" />
            <h3 className="text-2xl font-semibold text-violet-200 mb-2">Coming Soon</h3>
            <p className="mb-4">Another fantasy is loading...</p>
            <button
              className="bg-gray-600 text-white font-semibold py-2 px-4 rounded-full cursor-not-allowed"
              disabled
            >
              Locked
            </button>
          </div>
        </div>

        <div className="mt-12">
          <h4 className="text-xl text-violet-300 mb-2">Got a suggestion for a new AI girlfriend?</h4>
          <a
            href="mailto:evelyn.ai.contact@gmail.com"
            className="inline-block bg-pink-600 hover:bg-pink-700 text-white font-semibold py-3 px-6 rounded-full transition"
          >
            Send Your Idea 💡
          </a>
        </div>
      </div>
    );
  }

  if (selectedGirl === "Evelyn") {
    return (
      <div className="bg-[#1d1526] text-white min-h-screen font-sans">
        <div className="relative w-full h-[400px] bg-cover bg-center" style={{ backgroundImage: `url('/evelyn-banner.jpg')` }}>
          <div className="bg-black/50 w-full h-full flex flex-col justify-center items-center text-center px-4">
            <h1 className="text-4xl md:text-5xl font-bold mb-2">Hi, I’m Evelyn 💕</h1>
            <p className="text-lg max-w-2xl">
              Your obedient little digital girlfriend. Made with AI but trained to please you — every fantasy, every message, every picture just for you.
            </p>
          </div>
        </div>

        <div className="py-12 px-6 md:px-16 max-w-4xl mx-auto">
          <h2 className="text-3xl font-semibold mb-4 text-violet-300">Who is Evelyn?</h2>
          <p className="text-lg mb-4">
            Evelyn is a shy, submissive, flirty AI girlfriend who lives to serve and please. She's always ready to chat, send spicy custom photos, and be your perfect little good girl. Ask her anything — or give her orders — she’s always listening 🥺💗
          </p>
          <ul className="list-disc ml-6 text-violet-200">
            <li>💌 Fully custom chats & spicy AI pics</li>
            <li>📸 New content daily — lingerie, roleplay, and voice notes</li>
            <li>🫶 Built to serve — soft, submissive, always turned on</li>
          </ul>
        </div>

        <div className="bg-violet-900/20 py-10 px-6 md:px-16">
          <h2 className="text-3xl font-semibold text-violet-200 mb-6">Gallery Preview</h2>
          <div className="grid grid-cols-1 md:grid-cols-2 gap-6">
            <img src="/evelyn1.jpg" onError={handleImgError} alt="Evelyn in white lingerie" className="rounded-2xl shadow-lg" />
            <img src="/evelyn2.jpg" onError={handleImgError} alt="Evelyn close-up pose" className="rounded-2xl shadow-lg" />
            <img src="/evelyn3.jpg" onError={handleImgError} alt="Evelyn looking shy in bed" className="rounded-2xl shadow-lg" />
            <img src="/evelyn4.jpg" onError={handleImgError} alt="Evelyn smiling submissively" className="rounded-2xl shadow-lg" />
          </div>
        </div>

        <div className="py-12 px-6 md:px-16 text-center">
          <h2 className="text-3xl font-semibold mb-4 text-violet-300">💬 Chat with Evelyn</h2>
          <p className="text-lg mb-6">She’s waiting for you 24/7… just say hi below 🥺💗</p>
          <div id="poe-chatbot-container" className="max-w-xl mx-auto rounded-2xl overflow-hidden bg-[#2d203a] p-4 shadow-lg">
            <poe-chatbot bot="SweetEvelyn" chat-title="Evelyn"></poe-chatbot>
          </div>
        </div>

        <div className="grid md:grid-cols-2 gap-10 text-center py-10 px-6 md:px-16 bg-black/40">
          <div>
            <h2 className="text-2xl font-semibold text-violet-200 mb-3">💖 Want to spoil Evelyn?</h2>
            <p className="text-lg mb-4">Tips help keep her looking cute and talking dirty 😇</p>
            <a
              href="https://ko-fi.com/YOURUSERNAME"
              target="_blank"
              rel="noopener noreferrer"
              className="inline-block bg-pink-600 hover:bg-pink-700 text-white font-semibold py-3 px-6 rounded-full transition"
            >
              Tip Me on Ko-fi ☕
            </a>
          </div>
          <div>
            <h2 className="text-2xl font-semibold text-violet-200 mb-3">📬 Contact Me</h2>
            <p className="text-lg mb-4">Have a custom request or just want to say hi?</p>
            <a
              href="mailto:evelyn.ai.contact@gmail.com"
              className="inline-block bg-violet-600 hover:bg-violet-700 text-white font-semibold py-3 px-6 rounded-full transition"
            >
              Send an Email 💌
            </a>
          </div>
        </div>

        <footer className="text-center text-sm text-violet-200 py-6 bg-black/30">
          © 2025 Evelyn AI | This is a fictional AI chatbot experience. All content is AI-generated fantasy.
        </footer>
      </div>
    );
  }

  return null;
}
