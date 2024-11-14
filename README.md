import React, { useState } from 'react';
import { ChevronLeft, ChevronRight, Shield, Key, Lock, AlertTriangle } from 'lucide-react';

const Presentation = () => {
  const [currentSlide, setCurrentSlide] = useState(0);

  const slides = [
    {
      title: "Why Cybersecurity Matters",
      icon: Shield,
      points: [
        "60% of small companies go out of business within 6 months of a cyber attack",
        "Most breaches exploit simple security mistakes",
        "We're all targets - but we can make ourselves harder targets",
        "Think of security like mining safety - small daily habits prevent major incidents"
      ]
    },
    {
      title: "The 'High-Hanging Fruit' Strategy",
      icon: Key,
      points: [
        "Criminals look for easy targets - don't be one",
        "Basic security measures deter most attackers",
        "They'll move on to easier targets if you're too much work",
        "It's about making the effort not worth their time"
      ]
    },
    {
      title: "Simple But Effective Measures",
      icon: Lock,
      points: [
        "Use different passwords for different accounts",
        "Enable Two-Factor Authentication (2FA)",
        "Use a password manager (like LastPass or 1Password)",
        "Keep software and systems updated"
      ]
    },
    {
      title: "Warning Signs & Response",
      icon: AlertTriangle,
      points: [
        "Unexpected password reset emails",
        "Unfamiliar account activity",
        "Strange device login notifications",
        "If in doubt, report to IT immediately"
      ]
    }
  ];

  const nextSlide = () => {
    setCurrentSlide((prev) => (prev + 1) % slides.length);
  };

  const prevSlide = () => {
    setCurrentSlide((prev) => (prev - 1 + slides.length) % slides.length);
  };

  const CurrentIcon = slides[currentSlide].icon;

  return (
    <div className="flex flex-col h-screen bg-gray-100">
      {/* Header */}
      <div className="bg-blue-600 text-white p-4">
        <h1 className="text-xl font-bold">Online Security Safety Share</h1>
        <p className="text-sm">Making Yourself a Hard Target Online</p>
      </div>

      {/* Main Content */}
      <div className="flex-1 flex flex-col items-center justify-center p-8 relative">
        <div className="absolute top-0 right-0 p-4 text-gray-500">
          Slide {currentSlide + 1} of {slides.length}
        </div>

        <div className="max-w-2xl w-full bg-white rounded-lg shadow-lg p-8">
          <div className="flex items-center mb-6">
            <CurrentIcon className="w-8 h-8 text-blue-600 mr-4" />
            <h2 className="text-2xl font-bold text-gray-800">{slides[currentSlide].title}</h2>
          </div>

          <ul className="space-y-4">
            {slides[currentSlide].points.map((point, index) => (
              <li key={index} className="flex items-start">
                <span className="inline-block w-6 h-6 bg-blue-100 text-blue-600 rounded-full flex items-center justify-center mr-3 mt-0.5">
                  {index + 1}
                </span>
                <span className="text-gray-700">{point}</span>
              </li>
            ))}
          </ul>
        </div>
      </div>

      {/* Navigation */}
      <div className="flex justify-center items-center gap-4 p-4">
        <button
          onClick={prevSlide}
          className="p-2 bg-blue-600 text-white rounded-full hover:bg-blue-700 transition-colors"
        >
          <ChevronLeft className="w-6 h-6" />
        </button>
        <button
          onClick={nextSlide}
          className="p-2 bg-blue-600 text-white rounded-full hover:bg-blue-700 transition-colors"
        >
          <ChevronRight className="w-6 h-6" />
        </button>
      </div>
    </div>
  );
};

export default Presentation;
