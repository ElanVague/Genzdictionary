import { useState } from 'react';
import { Sun, Moon, Search } from 'lucide-react';
import { Switch } from '@/components/ui/switch';
import { Input } from '@/components/ui/input';

const words = [
  { word: 'rizz', real: 'charisma', meaning: 'The ability to charm or seduce someone effortlessly.' },
  { word: 'bet', real: 'okay/sure', meaning: 'Used to express agreement or confirmation.' },
  { word: 'slay', real: 'do really well', meaning: 'To succeed in something in an impressive way.' },
  { word: 'cap', real: 'lie', meaning: 'Used to call out someone who’s lying or exaggerating.' },
  { word: 'no cap', real: 'no lie', meaning: 'Used to emphasize that one is telling the truth.' },
  { word: 'sus', real: 'suspicious', meaning: 'Used when someone or something seems off or shady.' },
  { word: 'vibe check', real: 'atmosphere test', meaning: 'A spontaneous assessment of someone’s energy or behavior.' },
  { word: 'simp', real: 'overly affectionate', meaning: 'Someone who does too much for a person they like.' },
  { word: 'ghosted', real: 'suddenly ignored', meaning: 'When someone cuts off communication with no explanation.' },
  { word: 'cheugy', real: 'outdated', meaning: 'Used to describe someone or something that’s out of style or trying too hard.' },
  { word: 'drip', real: 'style/fashion', meaning: 'Refers to someone’s cool or stylish outfit.' },
  { word: 'flex', real: 'show off', meaning: 'Bragging or showing off something.' },
  { word: 'snatched', real: 'perfectly styled', meaning: 'Looking great, usually referring to makeup or fashion.' },
  { word: 'fire', real: 'amazing', meaning: 'Used to describe something really cool or awesome.' },
  { word: 'salty', real: 'bitter/jealous', meaning: 'Being upset or bitter about something.' },
  { word: 'lowkey', real: 'kind of', meaning: 'Something done subtly or secretly.' },
  { word: 'highkey', real: 'definitely', meaning: 'Something done openly or with emphasis.' }
];

const taglines = [
  "Where Slang Meets Sense.",
  "Translate the Trend.",
  "The Ultimate Gen Z Lexicon.",
  "From Rizz to Rizal – Know It All.",
  "Talk Gen Z Like a Pro.",
  "Slang It, Understand It.",
  "The Culture. The Words. The Meaning.",
  "Your Guide to the New Lingo.",
  "Understand Gen Z, One Word at a Time."
];

export default function GenZDictionary() {
  const [darkMode, setDarkMode] = useState(false);
  const [query, setQuery] = useState('');

  const filteredWords = words.filter(w =>
    w.word.toLowerCase().includes(query.toLowerCase()) ||
    w.real.toLowerCase().includes(query.toLowerCase()) ||
    w.meaning.toLowerCase().includes(query.toLowerCase())
  );

  return (
    <div className={darkMode ? 'bg-[#1a1a1a] text-white min-h-screen' : 'bg-gradient-to-tr from-[#fdfbfb] to-[#ebedee] text-black min-h-screen'}>
      {/* Header */}
      <header className="flex items-center justify-between p-4 border-b shadow-md bg-white/30 backdrop-blur-md rounded-b-xl">
        <div>
          <h1 className="text-3xl font-extrabold tracking-tight bg-gradient-to-r from-[#ff4ecd] via-[#7f5af0] to-[#00c2cb] bg-clip-text text-transparent">
            GenZ Dictionary
          </h1>
          <p className="text-sm italic text-[#7f5af0] mt-1">Decode the Lingo. Speak the Vibe.</p>
        </div>
        <div className="flex items-center gap-4">
          <div className="flex items-center gap-1">
            <Sun size={18} />
            <Switch checked={darkMode} onCheckedChange={setDarkMode} />
            <Moon size={18} />
          </div>
        </div>
      </header>

      {/* Tagline Banners */}
      <div className="flex flex-wrap gap-2 justify-center p-2 px-6">
        {taglines.map((tag, i) => (
          <span
            key={i}
            className="text-xs font-semibold text-white bg-gradient-to-r from-[#ff4ecd] via-[#7f5af0] to-[#00c2cb] rounded-full px-3 py-1 shadow-md hover:scale-105 transition"
          >
            {tag}
          </span>
        ))}
      </div>

      {/* Search */}
      <div className="flex justify-center p-6">
        <div className="relative w-full max-w-lg">
          <Input
            type="text"
            placeholder="Search Gen Z words..."
            value={query}
            onChange={e => setQuery(e.target.value)}
            className="pl-10 rounded-xl shadow-lg"
          />
          <Search className="absolute left-3 top-2.5 text-gray-500" size={18} />
        </div>
      </div>

      {/* Words List */}
      <main className="grid gap-4 p-4 max-w-5xl mx-auto">
        {filteredWords.length > 0 ? (
          filteredWords.map((item, index) => (
            <div
              key={index}
              className={
                darkMode
                  ? 'bg-[#2c2c2e] border border-[#3a3a3c] p-5 rounded-2xl shadow-xl transition hover:scale-[1.01] duration-300 ease-in-out'
                  : 'bg-white/80 p-5 rounded-2xl shadow-xl transition hover:scale-[1.01] duration-300 ease-in-out backdrop-blur-md'
              }
            >
              <h2 className="text-xl font-bold text-[#7f5af0]">{item.word}</h2>
              <p className="text-sm text-gray-500">Real Word: {item.real}</p>
              <p className="text-md mt-1">{item.meaning}</p>
            </div>
          ))
        ) : (
          <p className="text-center text-gray-500">No results found.</p>
        )}
      </main>

      {/* Footer */}
      <footer className="text-center text-sm p-6 text-gray-600 mt-8">
        &copy; 2025 <span className="text-[#7f5af0] font-semibold">GenZ Dictionary</span> — Decode the Lingo. Speak the Vibe.
      </footer>
    </div>
  );
}
