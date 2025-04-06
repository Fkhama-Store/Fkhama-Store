import { useState } from "react";
import { Card, CardContent } from "@/components/ui/card";
import { Button } from "@/components/ui/button";
import { FaDiscord, FaFacebookF, FaInstagram, FaTiktok } from "react-icons/fa";
import { useTranslation } from 'react-i18next';

export default function FkhamaStore() {
  const { t, i18n } = useTranslation(); // الترجمة
  const [selectedGame, setSelectedGame] = useState(null);

  const games = [
    {
      name: "Fortnite",
      image: "/fortnite.jpg",
      options: [
        { label: "1000 V-Bucks", price: "EGP 250" },
        { label: "2800 V-Bucks", price: "EGP 600" },
      ],
    },
    {
      name: "Valorant",
      image: "/valorant.jpg",
      options: [
        { label: "600 VP", price: "EGP 200" },
        { label: "1375 VP", price: "EGP 450" },
      ],
    },
  ];

  return (
    <div className="min-h-screen bg-gradient-to-b from-black to-gray-900 text-white p-6 flex flex-col justify-between">
      <header className="flex flex-col items-center mb-10">
        <h1 className="text-4xl font-bold text-center mb-4">{t('storeName')}</h1>
        
        {/* أزرار تغيير اللغة */}
        <div className="flex gap-4 mb-4">
          <Button onClick={() => i18n.changeLanguage('ar')} className="text-lg bg-gray-700 text-white px-4 py-2 rounded">عربي</Button>
          <Button onClick={() => i18n.changeLanguage('en')} className="text-lg bg-gray-700 text-white px-4 py-2 rounded">English</Button>
        </div>

        <div className="flex gap-4 text-2xl">
          <a href="https://discord.gg/kk8v74HaDq" target="_blank" rel="noopener noreferrer" className="hover:text-blue-400">
            <FaDiscord />
          </a>
          <a href="https://www.facebook.com/share/18RGqxKsai/?mibextid=wwXIfr" target="_blank" rel="noopener noreferrer" className="hover:text-blue-600">
            <FaFacebookF />
          </a>
          <a href="https://www.instagram.com/unkown.2025m?igsh=cWMzOXNmbWtwODhh&utm_source=qr" target="_blank" rel="noopener noreferrer" className="hover:text-pink-500">
            <FaInstagram />
          </a>
          <a href="https://www.tiktok.com/@tt_fakhama?_t=ZS-8vI3N3A3ria&_r=1" target="_blank" rel="noopener noreferrer" className="hover:text-gray-300">
            <FaTiktok />
          </a>
        </div>
      </header>

      <main>
        {!selectedGame ? (
          <div className="grid grid-cols-1 sm:grid-cols-2 gap-6">
            {games.map((game) => (
              <Card
                key={game.name}
                className="cursor-pointer hover:scale-105 transition"
                onClick={() => setSelectedGame(game)}
              >
                <CardContent className="flex flex-col items-center">
                  <img
                    src={game.image}
                    alt={game.name}
                    className="w-full h-48 object-cover rounded-lg mb-4"
                  />
                  <h2 className="text-2xl font-semibold">{game.name}</h2>
                </CardContent>
              </Card>
            ))}
          </div>
        ) : (
          <div>
            <Button className="mb-4" onClick={() => setSelectedGame(null)}>
              ⬅ {t('back')}
            </Button>
            <h2 className="text-3xl font-bold mb-6">{selectedGame.name} - {t('choosePackage')}</h2>
            <div className="grid grid-cols-1 sm:grid-cols-2 gap-6">
              {selectedGame.options.map((option, index) => (
                <Card key={index} className="bg-gray-800">
                  <CardContent className="p-4 flex flex-col items-start">
                    <span className="text-xl font-medium">{option.label}</span>
                    <span className="text-lg text-green-400">{option.price}</span>
                    <Button className="mt-4">{t('orderNow')}</Button>
                  </CardContent>
                </Card>
              ))}
            </div>
          </div>
        )}
      </main>

      <footer className="mt-16 text-center text-sm text-gray-400">
        <p>{t('followUs')}</p>
        <div className="flex justify-center gap-4 mt-2 text-xl">
          <a href="https://discord.gg/kk8v74HaDq" target="_blank" rel="noopener noreferrer" className="hover:text-blue-400">
            <FaDiscord />
          </a>
          <a href="https://www.facebook.com/share/18RGqxKsai/?mibextid=wwXIfr" target="_blank" rel="noopener noreferrer" className="hover:text-blue-600">
            <FaFacebookF />
          </a>
          <a href="https://www.instagram.com/unkown.2025m?igsh=cWMzOXNmbWtwODhh&utm_source=qr" target="_blank" rel="noopener noreferrer" className="hover:text-pink-500">
            <FaInstagram />
          </a>
          <a href="https://www.tiktok.com/@tt_fakhama?_t=ZS-8vI3N3A3ria&_r=1" target="_blank" rel="noopener noreferrer" className="hover:text-gray-300">
            <FaTiktok />
          </a>
        </div>

        <div className="mt-8">
          <h3 className="text-xl font-semibold text-white">{t('paymentMethods')}</h3>
          <p className="text-lg mt-2">{t('wallet')}</p>
          <p className="text-lg mt-1">{t('instapay')}</p>
        </div>
      </footer>
    </div>
  );
}
