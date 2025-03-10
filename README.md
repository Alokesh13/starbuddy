import React, { useState, useEffect } from 'react';

const CertificateShowcase = () => {
  const [activeIndex, setActiveIndex] = useState(0);
  
  const certificates = [
    {
      id: 1,
      title: "FTMO Challenge Payout",
      amount: "$8,750",
      date: "February 2025",
      description: "Successfully completed the FTMO Challenge with 12% profit"
    },
    {
      id: 2,
      title: "MyForexFunds Payout",
      amount: "$5,320",
      date: "January 2025",
      description: "Consistent trading results with managed risk profile"
    },
    {
      id: 3,
      title: "TrueForex Evaluation",
      amount: "$3,940",
      date: "December 2024",
      description: "Passed the two-phase evaluation with impressive metrics"
    }
  ];

  useEffect(() => {
    const interval = setInterval(() => {
      setActiveIndex((prevIndex) => (prevIndex + 1) % certificates.length);
    }, 5000);
    
    return () => clearInterval(interval);
  }, [certificates.length]);

  return (
    <div className="min-h-screen bg-gradient-to-br from-gray-900 to-blue-900 text-white">
      {/* Header */}
      <header className="pt-8 pb-6 px-4">
        <div className="container mx-auto text-center">
          <h1 className="text-4xl font-bold mb-2">Trading Excellence</h1>
          <p className="text-xl text-blue-300">Verified Prop Firm Success</p>
        </div>
      </header>

      {/* 3D Certificate Showcase */}
      <section className="py-12">
        <div className="container mx-auto px-4">
          <div className="relative h-96 flex items-center justify-center perspective">
            {certificates.map((cert, index) => (
              <div
                key={cert.id}
                className={`absolute w-64 sm:w-80 md:w-96 bg-gradient-to-br from-blue-600 to-blue-800 
                           rounded-lg shadow-2xl p-6 transition-all duration-1000 ease-in-out
                           ${index === activeIndex ? 'z-10 scale-100 rotate-y-0 opacity-100' : 
                             index === (activeIndex + 1) % certificates.length ? 'z-0 scale-90 rotate-y-40 translate-x-20 opacity-70' : 
                             'z-0 scale-90 rotate-y-40 -translate-x-20 opacity-70'}`}
                style={{
                  transformStyle: 'preserve-3d',
                  boxShadow: '0 25px 50px -12px rgba(0, 0, 0, 0.5)',
                  border: '1px solid rgba(255, 255, 255, 0.2)'
                }}
              >
                <div className="border-b-2 border-blue-400 pb-4 mb-4">
                  <h2 className="text-2xl font-bold text-white">{cert.title}</h2>
                  <div className="flex justify-between items-center mt-2">
                    <span className="text-blue-200">{cert.date}</span>
                    <span className="text-green-400 font-bold text-xl">{cert.amount}</span>
                  </div>
                </div>
                <div className="mb-6">
                  <p className="text-blue-100">{cert.description}</p>
                </div>
                <div className="flex justify-center mt-4">
                  <div className="w-20 h-20 rounded-full bg-blue-900 flex items-center justify-center">
                    <svg className="w-12 h-12 text-green-400" fill="currentColor" viewBox="0 0 20 20">
                      <path fillRule="evenodd" d="M16.707 5.293a1 1 0 010 1.414l-8 8a1 1 0 01-1.414 0l-4-4a1 1 0 011.414-1.414L8 12.586l7.293-7.293a1 1 0 011.414 0z" clipRule="evenodd" />
                    </svg>
                  </div>
                </div>
              </div>
            ))}
          </div>
          
          {/* Certificate Navigation */}
          <div className="mt-8 flex justify-center gap-2">
            {certificates.map((_, index) => (
              <button
                key={index}
                onClick={() => setActiveIndex(index)}
                className={`w-3 h-3 rounded-full ${activeIndex === index ? 'bg-blue-400' : 'bg-gray-600'}`}
                aria-label={`View certificate ${index + 1}`}
              />
            ))}
          </div>
        </div>
      </section>

      {/* Achievements Section */}
      <section className="py-12 bg-black bg-opacity-30">
        <div className="container mx-auto px-4">
          <h2 className="text-3xl font-bold text-center mb-8">Trading Performance</h2>
          <div className="grid grid-cols-1 md:grid-cols-3 gap-6">
            <div className="bg-gray-800 bg-opacity-50 p-6 rounded-lg border border-blue-800">
              <div className="text-4xl font-bold text-green-400 mb-2">24%</div>
              <div className="text-xl mb-1">Average Monthly ROI</div>
              <p className="text-gray-400">Consistent returns across multiple accounts</p>
            </div>
            <div className="bg-gray-800 bg-opacity-50 p-6 rounded-lg border border-blue-800">
              <div className="text-4xl font-bold text-green-400 mb-2">5:1</div>
              <div className="text-xl mb-1">Risk-Reward Ratio</div>
              <p className="text-gray-400">Strategic position sizing with minimal drawdown</p>
            </div>
            <div className="bg-gray-800 bg-opacity-50 p-6 rounded-lg border border-blue-800">
              <div className="text-4xl font-bold text-green-400 mb-2">$18K+</div>
              <div className="text-xl mb-1">Total Payouts</div>
              <p className="text-gray-400">Verified withdrawals from prop trading firms</p>
            </div>
          </div>
        </div>
      </section>

      {/* Contact Section */}
      <section className="py-12">
        <div className="container mx-auto px-4 text-center">
          <h2 className="text-2xl font-bold mb-4">Interested in Trading Success?</h2>
          <p className="mb-6 max-w-lg mx-auto">Follow my trading journey or reach out for mentorship opportunities</p>
          <button className="bg-blue-600 hover:bg-blue-700 text-white px-6 py-3 rounded-lg font-bold transition-colors">
            Connect With Me
          </button>
        </div>
      </section>

      {/* Footer */}
      <footer className="py-6 bg-gray-900">
        <div className="container mx-auto px-4 text-center text-gray-400">
          <p>© 2025 Trading Excellence. All certificates verified and authentic.</p>
        </div>
      </footer>
    </div>
  );
};

export default CertificateShowcase;
