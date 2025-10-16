# SunShine-Game-Shop
import { useState } from 'react'
import { Card, CardContent } from '@/components/ui/card'
import { Button } from '@/components/ui/button'
import { motion } from 'framer-motion'
import { ShoppingBag, Sun, Gamepad2 } from 'lucide-react'

export default function SunShineGameShop() {
  const [page, setPage] = useState('home')
  const [selected, setSelected] = useState(null)

  const accounts = [
    { id: 1, name: 'Lv. 2450 | Leopard', price: '$25', fruit: 'Leopard', img: 'https://via.placeholder.com/400x200' },
    { id: 2, name: 'Lv. 2300 | Dough', price: '$20', fruit: 'Dough', img: 'https://via.placeholder.com/400x200' },
    { id: 3, name: 'Lv. 2100 | Dragon', price: '$30', fruit: 'Dragon', img: 'https://via.placeholder.com/400x200' },
  ]

  return (
    <div className="min-h-screen bg-[#0a0a0a] text-white">
      {/* Navbar */}
      <header className="flex items-center justify-between px-6 py-4 border-b border-gray-800 bg-black/40 backdrop-blur">
        <div className="flex items-center gap-2 text-yellow-400 text-xl font-bold">
          <Sun className="text-yellow-400" /> SunShine Game Shop
        </div>
        <nav className="flex gap-6 text-gray-300">
          <button onClick={() => setPage('home')} className={page==='home'?'text-yellow-400':''}>Home</button>
          <button onClick={() => setPage('accounts')} className={page==='accounts'?'text-yellow-400':''}>Accounts</button>
          <button onClick={() => setPage('how')} className={page==='how'?'text-yellow-400':''}>How to Buy</button>
          <button onClick={() => setPage('contact')} className={page==='contact'?'text-yellow-400':''}>Contact</button>
        </nav>
      </header>

      {/* Page Content */}
      <main className="p-8">
        {page === 'home' && (
          <motion.div initial={{ opacity: 0, y: 30 }} animate={{ opacity: 1, y: 0 }} className="text-center space-y-6">
            <Gamepad2 className="mx-auto text-yellow-400" size={60} />
            <h1 className="text-4xl font-bold text-yellow-400">Buy Trusted Blox Fruits Accounts Instantly</h1>
            <p className="text-gray-400">Fast, safe, and verified accounts — powered by SunShine Game Shop ☀️</p>
            <Button onClick={() => setPage('accounts')} className="bg-yellow-500 hover:bg-yellow-400 text-black font-semibold px-6 py-3 rounded-xl">
              View Accounts
            </Button>
          </motion.div>
        )}

        {page === 'accounts' && (
          <motion.div initial={{ opacity: 0 }} animate={{ opacity: 1 }} className="grid md:grid-cols-3 gap-6">
            {accounts.map((acc) => (
              <Card key={acc.id} className="bg-gray-900 border border-gray-800 hover:border-yellow-500 transition">
                <CardContent className="p-0">
                  <img src={acc.img} alt={acc.name} className="rounded-t-xl w-full h-40 object-cover" />
                  <div className="p-4 space-y-2">
                    <h2 className="font-bold text-lg">{acc.name}</h2>
                    <p className="text-gray-400">Fruit: {acc.fruit}</p>
                    <div className="flex justify-between items-center">
                      <span className="text-yellow-400 font-bold">{acc.price}</span>
                      <Button onClick={() => { setSelected(acc); setPage('checkout') }} className="bg-yellow-500 text-black font-semibold">Buy Now</Button>
                    </div>
                  </div>
                </CardContent>
              </Card>
            ))}
          </motion.div>
        )}

        {page === 'checkout' && selected && (
          <motion.div initial={{ opacity: 0 }} animate={{ opacity: 1 }} className="max-w-lg mx-auto bg-gray-900 p-8 rounded-2xl border border-gray-800 space-y-4">
            <h2 className="text-2xl font-bold text-yellow-400">Checkout</h2>
            <p className="text-gray-300">You're buying: <strong>{selected.name}</strong></p>
            <p className="text-yellow-400 font-bold">Total: {selected.price}</p>
            <div className="space-y-2">
              <p className="text-gray-400">Please pay via <span className="text-yellow-400">GCash</span> and send your payment screenshot below.</p>
              <input type="file" className="w-full bg-black border border-gray-700 p-2 rounded" />
              <Button className="bg-yellow-500 hover:bg-yellow-400 text-black font-semibold w-full">Confirm Purchase</Button>
            </div>
          </motion.div>
        )}

        {page === 'how' && (
          <motion.div initial={{ opacity: 0 }} animate={{ opacity: 1 }} className="max-w-2xl mx-auto text-gray-300 space-y-4">
            <h2 className="text-3xl font-bold text-yellow-400">How to Buy</h2>
            <ol className="list-decimal pl-6 space-y-2">
              <li>Choose an account from the Accounts page.</li>
              <li>Pay using GCash to the number shown.</li>
              <li>Upload your payment proof.</li>
              <li>Receive your login info via Discord or Email instantly.</li>
            </ol>
          </motion.div>
        )}

        {page === 'contact' && (
          <motion.div initial={{ opacity: 0 }} animate={{ opacity: 1 }} className="max-w-md mx-auto text-gray-300 space-y-4">
            <h2 className="text-3xl font-bold text-yellow-400">Contact Us</h2>
            <input placeholder="Your Name" className="w-full p-2 bg-black border border-gray-700 rounded" />
            <input placeholder="Your Email" className="w-full p-2 bg-black border border-gray-700 rounded" />
            <textarea placeholder="Your Message" className="w-full p-2 bg-black border border-gray-700 rounded h-32" />
            <Button className="bg-yellow-500 hover:bg-yellow-400 text-black font-semibold w-full">Send Message</Button>
            <p className="text-sm text-gray-500 text-center">Discord / Facebook links can be added here later.</p>
          </motion.div>
        )}
      </main>

      <footer className="text-center text-gray-500 text-sm py-4 border-t border-gray-800">© 2025 SunShine Game Shop. All rights reserved.</footer>
    </div>
  )
}
