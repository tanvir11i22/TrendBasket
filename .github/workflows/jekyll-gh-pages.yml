<!DOCTYPE html>
<html lang="bn">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>DarazDropship | ডেমো পেমেন্ট সিস্টেম</title>
    <script src="https://cdn.tailwindcss.com"></script>
    <link href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.0.0/css/all.min.css" rel="stylesheet">
    <link href="https://fonts.googleapis.com/css2?family=Inter:wght@300;400;500;600;700&family=Noto+Sans+Bengali:wght@400;500;600;700&display=swap" rel="stylesheet">
    <style>
        body { 
            font-family: 'Inter', 'Noto Sans Bengali', sans-serif; 
            background: #f5f7fa; 
        }
        .daraz-orange { color: #f57224; }
        .bg-daraz-orange { background-color: #f57224; }
        .bkash-pink { color: #e2136e; }
        .bg-bkash-pink { background-color: #e2136e; }
        
        .product-card { transition: all 0.3s ease; background: white; }
        .product-card:hover { transform: translateY(-8px); box-shadow: 0 20px 40px rgba(0,0,0,0.1); }
        
        .payment-modal { animation: slideUp 0.3s ease-out; }
        @keyframes slideUp { from { transform: translateY(100%); opacity: 0; } to { transform: translateY(0); opacity: 1; } }
        
        .toast { animation: slideIn 0.3s ease-out; }
        @keyframes slideIn { from { transform: translateX(100%); opacity: 0; } to { transform: translateX(0); opacity: 1; } }
        
        .loading-spinner { border: 3px solid #f3f3f3; border-top: 3px solid #e2136e; border-radius: 50%; width: 40px; height: 40px; animation: spin 1s linear infinite; }
        @keyframes spin { 0% { transform: rotate(0deg); } 100% { transform: rotate(360deg); } }
        
        .bkash-ui { background: linear-gradient(135deg, #e2136e 0%, #b91c5c 100%); }
    </style>
</head>
<body class="text-gray-800">

    <!-- DEMO DISCLAIMER -->
    <div class="bg-red-600 text-white text-center py-2 px-4 text-sm font-semibold">
        <i class="fa-solid fa-triangle-exclamation mr-2"></i>
        ডেমো সিস্টেম: এটি শিক্ষার উদ্দেশ্যে তৈরি। কোনো আসল পেমেন্ট প্রক্রিয়া হয় না।
    </div>

    <!-- Navigation -->
    <nav class="bg-white shadow-md sticky top-0 z-40">
        <div class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8">
            <div class="flex justify-between items-center h-16">
                <div class="flex items-center cursor-pointer" onclick="app.navigate('home')">
                    <div class="bg-daraz-orange text-white p-2 rounded-lg mr-2">
                        <i class="fa-solid fa-bag-shopping text-xl"></i>
                    </div>
                    <div>
                        <span class="text-2xl font-bold text-gray-900">Daraz</span>
                        <span class="text-sm text-gray-500 block -mt-1">ড্রপশিপ হাব</span>
                    </div>
                </div>

                <div class="hidden md:flex items-center space-x-6">
                    <button onclick="app.navigate('home')" class="text-gray-600 hover:text-daraz-orange font-medium">হোম</button>
                    <button onclick="app.navigate('products')" class="text-gray-600 hover:text-daraz-orange font-medium">প্রোডাক্টস</button>
                    <button onclick="app.navigate('orders')" class="text-gray-600 hover:text-daraz-orange font-medium">আমার অর্ডার</button>
                    <button onclick="app.navigate('admin')" class="text-gray-600 hover:text-daraz-orange font-medium">এডমিন</button>
                </div>

                <div class="flex items-center space-x-4">
                    <button onclick="app.toggleCart()" class="relative p-2 text-gray-600 hover:text-daraz-orange transition-colors">
                        <i class="fa-solid fa-cart-shopping text-2xl"></i>
                        <span id="cart-badge" class="absolute -top-1 -right-1 bg-daraz-orange text-white text-xs font-bold w-5 h-5 rounded-full flex items-center justify-center opacity-0 transform scale-0 transition-all">0</span>
                    </button>
                </div>
            </div>
        </div>
    </nav>

    <main class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8 py-8">

        <!-- HOME SECTION -->
        <section id="home-section">
            <div class="bg-gradient-to-r from-orange-500 to-pink-500 rounded-2xl p-8 md:p-12 mb-8 text-white relative overflow-hidden shadow-xl">
                <div class="relative z-10 max-w-2xl">
                    <div class="inline-block bg-white/20 backdrop-blur-sm px-4 py-1 rounded-full text-sm font-semibold mb-4">
                        <i class="fa-solid fa-bolt mr-2"></i>লাইভ ডেমো সিস্টেম
                    </div>
                    <h1 class="text-4xl md:text-5xl font-bold mb-4">বিকাশ পেমেন্ট ইন্টিগ্রেশন</h1>
                    <p class="text-lg mb-6 opacity-90">এটি একটি ডেমো ড্রপশিপিং সিস্টেম। আসল টাকা লেনদেন হয় না।</p>
                    <button onclick="app.navigate('products')" class="bg-white text-orange-600 px-8 py-3 rounded-full font-bold hover:shadow-lg transform hover:scale-105 transition-all">
                        শপিং করুন
                    </button>
                </div>
            </div>

            <!-- Categories -->
            <div class="grid grid-cols-2 md:grid-cols-4 gap-4 mb-12">
                <div onclick="app.filterCategory('Electronics')" class="bg-white p-6 rounded-xl shadow-sm hover:shadow-md cursor-pointer transition-all text-center">
                    <i class="fa-solid fa-mobile-screen text-4xl text-blue-500 mb-3"></i>
                    <span class="font-semibold block">ইলেকট্রনিক্স</span>
                </div>
                <div onclick="app.filterCategory('Fashion')" class="bg-white p-6 rounded-xl shadow-sm hover:shadow-md cursor-pointer transition-all text-center">
                    <i class="fa-solid fa-shirt text-4xl text-purple-500 mb-3"></i>
                    <span class="font-semibold block">ফ্যাশন</span>
                </div>
                <div onclick="app.filterCategory('Home')" class="bg-white p-6 rounded-xl shadow-sm hover:shadow-md cursor-pointer transition-all text-center">
                    <i class="fa-solid fa-couch text-4xl text-orange-500 mb-3"></i>
                    <span class="font-semibold block">হোম অ্যান্ড লিভিং</span>
                </div>
                <div onclick="app.filterCategory('Beauty')" class="bg-white p-6 rounded-xl shadow-sm hover:shadow-md cursor-pointer transition-all text-center">
                    <i class="fa-solid fa-spray-can-sparkles text-4xl text-pink-500 mb-3"></i>
                    <span class="font-semibold block">বিউটি</span>
                </div>
            </div>
        </section>

        <!-- PRODUCTS SECTION -->
        <section id="products-section" class="hidden">
            <div class="flex justify-between items-center mb-8">
                <div>
                    <h2 class="text-3xl font-bold">সব প্রোডাক্ট</h2>
                    <p class="text-gray-500 mt-1">সব প্রাইসে ৪% সার্ভিস চার্জ যোগ করা আছে • ডেমো</p>
                </div>
                <div class="flex gap-2 flex-wrap">
                    <button onclick="app.filterCategory('All')" class="category-btn active px-4 py-2 rounded-full bg-daraz-orange text-white text-sm">সব</button>
                    <button onclick="app.filterCategory('Electronics')" class="category-btn px-4 py-2 rounded-full bg-gray-200 text-gray-700 text-sm">ইলেকট্রনিক্স</button>
                    <button onclick="app.filterCategory('Fashion')" class="category-btn px-4 py-2 rounded-full bg-gray-200 text-gray-700 text-sm">ফ্যাশন</button>
                    <button onclick="app.filterCategory('Home')" class="category-btn px-4 py-2 rounded-full bg-gray-200 text-gray-700 text-sm">হোম</button>
                    <button onclick="app.filterCategory('Beauty')" class="category-btn px-4 py-2 rounded-full bg-gray-200 text-gray-700 text-sm">বিউটি</button>
                    <button onclick="app.filterCategory('Gaming')" class="category-btn px-4 py-2 rounded-full bg-gray-200 text-gray-700 text-sm">গেমিং</button>
                    <button onclick="app.filterCategory('Photography')" class="category-btn px-4 py-2 rounded-full bg-gray-200 text-gray-700 text-sm">ফটোগ্রাফি</button>
                </div>
            </div>

            <!-- Price Info -->
            <div class="bg-blue-50 border border-blue-200 rounded-lg p-4 mb-6">
                <div class="flex items-center text-blue-800">
                    <i class="fa-solid fa-circle-info mr-3 text-xl"></i>
                    <div>
                        <p class="font-semibold">স্বচ্ছ মূল্য নীতি</p>
                        <p class="text-sm">দেখানো প্রাইস = Daraz প্রাইস + ৪% সার্ভিস ফি। কোনো গোপন চার্জ নেই।</p>
                    </div>
                </div>
            </div>

            <div id="product-grid" class="grid grid-cols-1 sm:grid-cols-2 lg:grid-cols-3 xl:grid-cols-4 gap-6"></div>
        </section>

        <!-- ORDERS SECTION -->
        <section id="orders-section" class="hidden max-w-4xl mx-auto">
            <h2 class="text-3xl font-bold mb-8">আমার অর্ডার</h2>
            <div id="orders-list" class="space-y-4">
                <div class="text-center py-12 text-gray-400">
                    <i class="fa-solid fa-box-open text-6xl mb-4 opacity-30"></i>
                    <p>কোনো অর্ডার নেই। শপিং শুরু করুন!</p>
                </div>
            </div>
        </section>

        <!-- ADMIN SECTION -->
        <section id="admin-section" class="hidden">
            <div class="flex justify-between items-center mb-8">
                <h2 class="text-3xl font-bold">এডমিন ড্যাশবোর্ড</h2>
                <div class="flex gap-4">
                    <div class="bg-white px-4 py-2 rounded-lg shadow-sm">
                        <span class="text-gray-500 text-sm">মোট অর্ডার</span>
                        <div class="text-2xl font-bold" id="admin-total-orders">0</div>
                    </div>
                    <div class="bg-white px-4 py-2 rounded-lg shadow-sm">
                        <span class="text-gray-500 text-sm">রেভিনিউ (ডেমো)</span>
                        <div class="text-2xl font-bold text-green-600" id="admin-revenue">৳ 0</div>
                    </div>
                </div>
            </div>

            <div class="bg-white rounded-xl shadow-sm overflow-hidden">
                <div class="overflow-x-auto">
                    <table class="w-full">
                        <thead class="bg-gray-50">
                            <tr>
                                <th class="px-6 py-3 text-left text-xs font-medium text-gray-500 uppercase">অর্ডার আইডি</th>
                                <th class="px-6 py-3 text-left text-xs font-medium text-gray-500 uppercase">কাস্টমার</th>
                                <th class="px-6 py-3 text-left text-xs font-medium text-gray-500 uppercase">আইটেম</th>
                                <th class="px-6 py-3 text-left text-xs font-medium text-gray-500 uppercase">মোট</th>
                                <th class="px-6 py-3 text-left text-xs font-medium text-gray-500 uppercase">পেমেন্ট</th>
                                <th class="px-6 py-3 text-left text-xs font-medium text-gray-500 uppercase">স্ট্যাটাস</th>
                                <th class="px-6 py-3 text-left text-xs font-medium text-gray-500 uppercase">অ্যাকশন</th>
                            </tr>
                        </thead>
                        <tbody id="admin-orders-table" class="divide-y divide-gray-200"></tbody>
                    </table>
                </div>
            </div>
        </section>

    </main>

    <!-- CART SIDEBAR -->
    <div id="cart-overlay" onclick="app.toggleCart()" class="fixed inset-0 bg-black/50 z-40 hidden transition-opacity opacity-0"></div>
    <div id="cart-sidebar" class="fixed top-0 right-0 h-full w-full max-w-md bg-white shadow-2xl z-50 transform translate-x-full transition-transform duration-300 flex flex-col">
        <div class="p-6 border-b flex justify-between items-center bg-gray-50">
            <h2 class="text-xl font-bold">শপিং কার্ট</h2>
            <button onclick="app.toggleCart()" class="text-gray-500 hover:text-gray-700"><i class="fa-solid fa-xmark text-2xl"></i></button>
        </div>
        <div id="cart-items" class="flex-1 overflow-y-auto p-6"></div>
        <div class="border-t p-6 bg-gray-50">
            <div class="flex justify-between mb-4">
                <span class="text-gray-600">সাবটোটাল</span>
                <span id="cart-total" class="font-bold text-xl text-daraz-orange">৳ 0</span>
            </div>
            <button onclick="app.showCheckout()" class="w-full bg-daraz-orange text-white py-3 rounded-lg font-bold hover:bg-orange-600 transition-colors">
                চেকআউট করুন
            </button>
        </div>
    </div>

    <!-- CHECKOUT MODAL -->
    <div id="checkout-modal" class="fixed inset-0 bg-black/60 z-50 hidden flex items-center justify-center p-4">
        <div class="bg-white rounded-2xl max-w-2xl w-full max-h-[90vh] overflow-y-auto payment-modal">
            <div class="p-6 border-b flex justify-between items-center">
                <h2 class="text-2xl font-bold">চেকআউট</h2>
                <button onclick="app.closeCheckout()" class="text-gray-500 hover:text-gray-700"><i class="fa-solid fa-xmark text-2xl"></i></button>
            </div>
            
            <div class="p-6">
                <div class="bg-gray-50 rounded-xl p-4 mb-6">
                    <h3 class="font-bold mb-3">অর্ডার সারাংশ</h3>
                    <div id="checkout-items" class="space-y-2 mb-3"></div>
                    <div class="border-t pt-3 flex justify-between font-bold text-lg">
                        <span>মোট</span>
                        <span id="checkout-total" class="text-daraz-orange">৳ 0</span>
                    </div>
                </div>

                <div class="mb-6">
                    <h3 class="font-bold mb-3">ডেলিভারি তথ্য</h3>
                    <div class="grid grid-cols-2 gap-4">
                        <input type="text" id="customer-name" placeholder="পুরো নাম" class="border rounded-lg px-4 py-2 focus:outline-none focus:border-daraz-orange">
                        <input type="tel" id="customer-phone" placeholder="ফোন নম্বর" class="border rounded-lg px-4 py-2 focus:outline-none focus:border-daraz-orange">
                        <textarea id="customer-address" placeholder="ডেলিভারি ঠিকানা" class="border rounded-lg px-4 py-2 col-span-2 h-20 resize-none focus:outline-none focus:border-daraz-orange"></textarea>
                    </div>
                </div>

                <div class="mb-6">
                    <h3 class="font-bold mb-3">পেমেন্ট মেথড</h3>
                    <div class="space-y-3">
                        <label class="flex items-center p-4 border-2 rounded-xl cursor-pointer hover:border-bkash-pink transition-colors" onclick="app.selectPayment('bkash')">
                            <input type="radio" name="payment" value="bkash" class="mr-3">
                            <div class="flex items-center flex-1">
                                <div class="w-12 h-12 bg-bkash-pink rounded-lg flex items-center justify-center text-white mr-3">
                                    <i class="fa-solid fa-mobile-screen-button text-xl"></i>
                                </div>
                                <div>
                                    <div class="font-bold">বিকাশ</div>
                                    <div class="text-sm text-gray-500">বিকাশে পেমেন্ট করুন (ডেমো)</div>
                                </div>
                            </div>
                        </label>
                        
                        <label class="flex items-center p-4 border-2 rounded-xl cursor-pointer hover:border-green-500 transition-colors" onclick="app.selectPayment('cod')">
                            <input type="radio" name="payment" value="cod" class="mr-3">
                            <div class="flex items-center flex-1">
                                <div class="w-12 h-12 bg-green-500 rounded-lg flex items-center justify-center text-white mr-3">
                                    <i class="fa-solid fa-money-bill-wave text-xl"></i>
                                </div>
                                <div>
                                    <div class="font-bold">ক্যাশ অন ডেলিভারি</div>
                                    <div class="text-sm text-gray-500">পণ্য হাতে পেয়ে টাকা দিন</div>
                                </div>
                            </div>
                        </label>
                    </div>
                </div>

                <button onclick="app.processPayment()" id="pay-button" class="w-full bg-bkash-pink text-white py-4 rounded-xl font-bold text-lg hover:bg-pink-700 transition-colors flex items-center justify-center gap-2">
                    <span>অর্ডার করুন (ডেমো)</span>
                    <i class="fa-solid fa-arrow-right"></i>
                </button>
                
                <p class="text-center text-xs text-gray-400 mt-4">
                    <i class="fa-solid fa-lock mr-1"></i> এটি একটি ডেমো। কোনো আসল পেমেন্ট হবে না।
                </p>
            </div>
        </div>
    </div>

    <!-- bKASH MODAL -->
    <div id="bkash-modal" class="fixed inset-0 bg-black/80 z-[60] hidden flex items-center justify-center p-4">
        <div class="bkash-ui rounded-2xl max-w-md w-full p-6 text-white payment-modal relative overflow-hidden">
            <div class="absolute -top-20 -right-20 w-40 h-40 bg-white/10 rounded-full"></div>
            <div class="absolute -bottom-20 -left-20 w-40 h-40 bg-white/10 rounded-full"></div>
            
            <div class="relative z-10">
                <div class="text-center mb-6">
                    <div class="w-16 h-16 bg-white rounded-full flex items-center justify-center mx-auto mb-3">
                        <i class="fa-solid fa-mobile-screen-button text-3xl text-bkash-pink"></i>
                    </div>
                    <h3 class="text-2xl font-bold">বিকাশ পেমেন্ট</h3>
                    <p class="text-white/80">ডেমো ট্রানজাকশন</p>
                </div>

                <div class="bg-white/20 backdrop-blur-sm rounded-xl p-4 mb-6">
                    <div class="flex justify-between mb-2">
                        <span class="text-white/80">মার্চেন্ট</span>
                        <span class="font-semibold">DarazDropship</span>
                    </div>
                    <div class="flex justify-between mb-2">
                        <span class="text-white/80">পরিমাণ</span>
                        <span class="font-bold text-xl" id="bkash-amount">৳ 0</span>
                    </div>
                </div>

                <div class="space-y-4 mb-6">
                    <div>
                        <label class="block text-sm mb-2 text-white/90">বিকাশ নম্বর</label>
                        <input type="tel" value="01XXXXXXXXX" readonly class="w-full bg-white/20 border border-white/30 rounded-lg px-4 py-3 text-white">
                    </div>
                    <div>
                        <label class="block text-sm mb-2 text-white/90">বিকাশ পিন (ডেমো)</label>
                        <input type="password" value="1234" readonly class="w-full bg-white/20 border border-white/30 rounded-lg px-4 py-3 text-white">
                    </div>
                </div>

                <div class="flex gap-3">
                    <button onclick="app.closeBkashModal()" class="flex-1 bg-white/20 hover:bg-white/30 text-white py-3 rounded-lg font-semibold">বাতিল</button>
                    <button onclick="app.confirmBkashPayment()" id="bkash-confirm-btn" class="flex-1 bg-white text-bkash-pink py-3 rounded-lg font-bold flex items-center justify-center gap-2">
                        <span>কনফার্ম</span>
                        <i class="fa-solid fa-check"></i>
                    </button>
                </div>
            </div>
        </div>
    </div>

    <!-- SUCCESS MODAL -->
    <div id="success-modal" class="fixed inset-0 bg-black/60 z-[70] hidden flex items-center justify-center p-4">
        <div class="bg-white rounded-2xl max-w-md w-full p-8 text-center payment-modal">
            <div class="w-20 h-20 bg-green-100 rounded-full flex items-center justify-center mx-auto mb-4">
                <i class="fa-solid fa-check text-4xl text-green-600"></i>
            </div>
            <h3 class="text-2xl font-bold mb-2">অর্ডার সফল!</h3>
            <p class="text-gray-600 mb-6">আপনার ডেমো অর্ডার রেকর্ড করা হয়েছে। কোনো আসল পেমেন্ট হয়নি।</p>
            
            <div class="bg-gray-50 rounded-lg p-4 mb-6 text-left">
                <div class="flex justify-between mb-2">
                    <span class="text-gray-500">অর্ডার আইডি:</span>
                    <span class="font-mono font-bold" id="success-order-id">#ORD-000</span>
                </div>
            </div>

            <button onclick="app.closeSuccessModal(); app.navigate('orders')" class="w-full bg-daraz-orange text-white py-3 rounded-lg font-bold">
                আমার অর্ডার দেখুন
            </button>
        </div>
    </div>

    <!-- TOAST -->
    <div id="toast-container" class="fixed bottom-4 right-4 z-[80] space-y-2"></div>

    <script>
        const app = {
            cart: [],
            orders: [],
            
            // সম্পূর্ণ ৩৬টি প্রোডাক্ট
            products: [
                // ইলেকট্রনিক্স (১২টি)
                {
                    id: 1,
                    name: "realme C53 - 6GB RAM 128GB ROM - 33W চার্জ",
                    darazPrice: 28999,
                    category: "Electronics",
                    image: "https://static-01.daraz.pk/p/39e2c00b9ce95c84c70b8d9c84f3c396.jpg",
                    rating: 4.8,
                    reviews: 1250,
                    sold: 3420,
                    badge: "১২.১২ ডিল"
                },
                {
                    id: 2,
                    name: "Samsung Galaxy A14 - 6GB RAM 128GB ROM",
                    darazPrice: 42999,
                    category: "Electronics",
                    image: "https://static-01.daraz.pk/p/2f8c8ad4c0b0c5b6a3e8d9f1c2b4a6e8.jpg",
                    rating: 4.6,
                    reviews: 890,
                    sold: 2100,
                    badge: "বেস্ট সেলার"
                },
                {
                    id: 3,
                    name: "Xiaomi Redmi 12 - 8GB RAM 128GB ROM - 50MP ক্যামেরা",
                    darazPrice: 34999,
                    category: "Electronics",
                    image: "https://static-01.daraz.pk/p/1a3b5c7d9e1f3a5b7c9d1e3f5a7b9c1d.jpg",
                    rating: 4.7,
                    reviews: 2100,
                    sold: 5600,
                    badge: "ট্রেন্ডিং"
                },
                {
                    id: 4,
                    name: "Apple iPhone 15 Pro Max - 256GB - ন্যাচারাল টাইটানিয়াম",
                    darazPrice: 434999,
                    category: "Electronics",
                    image: "https://static-01.daraz.pk/p/9f8e7d6c5b4a3928170654433221100f.jpg",
                    rating: 4.9,
                    reviews: 320,
                    sold: 450,
                    badge: "প্রিমিয়াম"
                },
                {
                    id: 5,
                    name: "Anker PowerCore 20000mAh পাওয়ার ব্যাংক - ফাস্ট চার্জিং",
                    darazPrice: 4999,
                    category: "Electronics",
                    image: "https://static-01.daraz.pk/p/abc123def45678901234567890123456.jpg",
                    rating: 4.8,
                    reviews: 3400,
                    sold: 8900,
                    badge: "১২.১২ ডিল"
                },
                {
                    id: 6,
                    name: "Lenovo IdeaPad Slim 3 - Intel Core i3 - 8GB RAM - 256GB SSD",
                    darazPrice: 84999,
                    category: "Electronics",
                    image: "https://static-01.daraz.pk/p/def789abc01234567890123456789012.jpg",
                    rating: 4.5,
                    reviews: 560,
                    sold: 1200,
                    badge: "ফ্ল্যাশ সেল"
                },
                {
                    id: 7,
                    name: "Sony WH-CH520 ওয়্যারলেস হেডফোন - ৫০ঘণ্টা ব্যাটারি",
                    darazPrice: 8999,
                    category: "Electronics",
                    image: "https://static-01.daraz.pk/p/45678901234567890123456789012345.jpg",
                    rating: 4.6,
                    reviews: 780,
                    sold: 2300,
                    badge: null
                },
                {
                    id: 8,
                    name: "Samsung 43\" Crystal UHD 4K স্মার্ট টিভি",
                    darazPrice: 89999,
                    category: "Electronics",
                    image: "https://static-01.daraz.pk/p/78901234567890123456789012345678.jpg",
                    rating: 4.7,
                    reviews: 430,
                    sold: 890,
                    badge: "বিগ স্ক্রিন"
                },
                {
                    id: 9,
                    name: "Dell ওয়্যারলেস মাউস WM126 - ব্ল্যাক",
                    darazPrice: 1299,
                    category: "Electronics",
                    image: "https://static-01.daraz.pk/p/01234567890123456789012345678901.jpg",
                    rating: 4.4,
                    reviews: 1200,
                    sold: 4500,
                    badge: null
                },
                {
                    id: 10,
                    name: "TP-Link Archer C6 AC1200 ওয়্যারলেস রাউটার",
                    darazPrice: 4499,
                    category: "Electronics",
                    image: "https://static-01.daraz.pk/p/34567890123456789012345678901234.jpg",
                    rating: 4.8,
                    reviews: 2100,
                    sold: 5600,
                    badge: "১২.১২ ডিল"
                },
                {
                    id: 11,
                    name: "Canon EOS 2000D DSLR ক্যামেরা ১৮-৫৫মিমি লেন্স",
                    darazPrice: 94999,
                    category: "Electronics",
                    image: "https://static-01.daraz.pk/p/67890123456789012345678901234567.jpg",
                    rating: 4.9,
                    reviews: 180,
                    sold: 320,
                    badge: "ফটোগ্রাফি"
                },
                {
                    id: 12,
                    name: "JBL Tune 760NC ওয়্যারলেস ANC হেডফোন",
                    darazPrice: 14999,
                    category: "Electronics",
                    image: "https://static-01.daraz.pk/p/90123456789012345678901234567890.jpg",
                    rating: 4.7,
                    reviews: 650,
                    sold: 1400,
                    badge: "টপ রেটেড"
                },

                // ফ্যাশন (৮টি)
                {
                    id: 13,
                    name: "মেন্স ক্যাজুয়াল কটন টি-শার্ট - ৩ পিস - মাল্টি কালার",
                    darazPrice: 1299,
                    category: "Fashion",
                    image: "https://static-01.daraz.pk/p/fashion1234567890123456789012345.jpg",
                    rating: 4.3,
                    reviews: 3400,
                    sold: 12000,
                    badge: "১২.১২ ডিল"
                },
                {
                    id: 14,
                    name: "উইমেন্স এমব্রয়ডার্ড লন সুট - আনস্টিচড ৩ পিস",
                    darazPrice: 2499,
                    category: "Fashion",
                    image: "https://static-01.daraz.pk/p/fashion2345678901234567890123456.jpg",
                    rating: 4.5,
                    reviews: 1200,
                    sold: 4500,
                    badge: "ঈদ কালেকশন"
                },
                {
                    id: 15,
                    name: "Nike রানিং শুজ - এয়ার জুম স্ট্রাকচার - ব্ল্যাক",
                    darazPrice: 18999,
                    category: "Fashion",
                    image: "https://static-01.daraz.pk/p/fashion3456789012345678901234567.jpg",
                    rating: 4.8,
                    reviews: 890,
                    sold: 2300,
                    badge: "স্পোর্টস"
                },
                {
                    id: 16,
                    name: "Adidas ওরিজিনালস স্নিকার্স - হোয়াইট/গ্রিন",
                    darazPrice: 15999,
                    category: "Fashion",
                    image: "https://static-01.daraz.pk/p/fashion4567890123456789012345678.jpg",
                    rating: 4.7,
                    reviews: 650,
                    sold: 1800,
                    badge: "ক্লাসিক"
                },
                {
                    id: 17,
                    name: "লেদার ওয়ালেট ফর মেন - জেনুইন কাউহাইড - ব্রাউন",
                    darazPrice: 1299,
                    category: "Fashion",
                    image: "https://static-01.daraz.pk/p/fashion5678901234567890123456789.jpg",
                    rating: 4.4,
                    reviews: 2100,
                    sold: 6700,
                    badge: null
                },
                {
                    id: 18,
                    name: "উইমেন্স ক্রসবডি ব্যাগ - PU লেদার - ব্ল্যাক",
                    darazPrice: 1999,
                    category: "Fashion",
                    image: "https://static-01.daraz.pk/p/fashion6789012345678901234567890.jpg",
                    rating: 4.6,
                    reviews: 1500,
                    sold: 4200,
                    badge: "ট্রেন্ডিং"
                },
                {
                    id: 19,
                    name: "Ray-Ban এভিয়েটর সানগ্লাস - গোল্ড ফ্রেম",
                    darazPrice: 12999,
                    category: "Fashion",
                    image: "https://static-01.daraz.pk/p/fashion7890123456789012345678901.jpg",
                    rating: 4.9,
                    reviews: 320,
                    sold: 780,
                    badge: "প্রিমিয়াম"
                },
                {
                    id: 20,
                    name: "উইন্টার হুডি - ফ্লিস লাইনড - ইউনিসেক্স - গ্রে",
                    darazPrice: 2499,
                    category: "Fashion",
                    image: "https://static-01.daraz.pk/p/fashion8901234567890123456789012.jpg",
                    rating: 4.5,
                    reviews: 2800,
                    sold: 8900,
                    badge: "উইন্টার সেল"
                },

                // হোম অ্যান্ড লিভিং (৮টি)
                {
                    id: 21,
                    name: "Philips এয়ার ফ্রায়ার HD9200/90 - ৪.১লি - র‍্যাপিড এয়ার",
                    darazPrice: 24999,
                    category: "Home",
                    image: "https://static-01.daraz.pk/p/home123456789012345678901234567.jpg",
                    rating: 4.8,
                    reviews: 2100,
                    sold: 5600,
                    badge: "কিচেন এসেনশিয়াল"
                },
                {
                    id: 22,
                    name: "Haier 12KG টুইন টব ওয়াশিং মেশিন - HWM120-35FF",
                    darazPrice: 38999,
                    category: "Home",
                    image: "https://static-01.daraz.pk/p/home234567890123456789012345678.jpg",
                    rating: 4.7,
                    reviews: 1200,
                    sold: 3400,
                    badge: "১২.১২ ডিল"
                },
                {
                    id: 23,
                    name: "Gree 1.5 টন ইনভার্টার এসি - GS-18XLMV - হিট অ্যান্ড কুল",
                    darazPrice: 134999,
                    category: "Home",
                    image: "https://static-01.daraz.pk/p/home345678901234567890123456789.jpg",
                    rating: 4.6,
                    reviews: 890,
                    sold: 2100,
                    badge: "সামার রেডি"
                },
                {
                    id: 24,
                    name: "নন-স্টিক কুকওয়্যার সেট - ১২ পিস - গ্র্যানাইট কোটেড",
                    darazPrice: 4999,
                    category: "Home",
                    image: "https://static-01.daraz.pk/p/home456789012345678901234567890.jpg",
                    rating: 4.5,
                    reviews: 3400,
                    sold: 8900,
                    badge: "বেস্ট ভ্যালু"
                },
                {
                    id: 25,
                    name: "রোবট ভ্যাকুয়াম ক্লিনার - স্মার্ট নেভিগেশন - ওয়াইফাই",
                    darazPrice: 24999,
                    category: "Home",
                    image: "https://static-01.daraz.pk/p/home567890123456789012345678901.jpg",
                    rating: 4.4,
                    reviews: 560,
                    sold: 1200,
                    badge: "স্মার্ট হোম"
                },
                {
                    id: 26,
                    name: "মেমোরি ফোম পিলো - অর্থোপেডিক সাপোর্ট - ২ পিস",
                    darazPrice: 1999,
                    category: "Home",
                    image: "https://static-01.daraz.pk/p/home678901234567890123456789012.jpg",
                    rating: 4.7,
                    reviews: 4500,
                    sold: 12000,
                    badge: null
                },
                {
                    id: 27,
                    name: "ইলেকট্রিক কেটলি - ১.৮লি - স্টেইনলেস স্টিল - অটো শাট-অফ",
                    darazPrice: 1999,
                    category: "Home",
                    image: "https://static-01.daraz.pk/p/home789012345678901234567890123.jpg",
                    rating: 4.6,
                    reviews: 2800,
                    sold: 7800,
                    badge: "ডেইলি এসেনশিয়াল"
                },
                {
                    id: 28,
                    name: "LED সিলিং লাইট - 24W - রিমোট কন্ট্রোল - ডিমেবল",
                    darazPrice: 2499,
                    category: "Home",
                    image: "https://static-01.daraz.pk/p/home890123456789012345678901234.jpg",
                    rating: 4.5,
                    reviews: 1200,
                    sold: 3400,
                    badge: null
                },

                // বিউটি (৮টি)
                {
                    id: 29,
                    name: "The Ordinary Niacinamide 10% + Zinc 1% - 30ml",
                    darazPrice: 2499,
                    category: "Beauty",
                    image: "https://static-01.daraz.pk/p/beauty12345678901234567890123456.jpg",
                    rating: 4.9,
                    reviews: 5600,
                    sold: 15000,
                    badge: "হলি গ্রেইল"
                },
                {
                    id: 30,
                    name: "Maybelline New York Lash Sensational মাসকারা - ব্ল্যাক",
                    darazPrice: 1299,
                    category: "Beauty",
                    image: "https://static-01.daraz.pk/p/beauty23456789012345678901234567.jpg",
                    rating: 4.7,
                    reviews: 3400,
                    sold: 8900,
                    badge: "বেস্ট সেলার"
                },
                {
                    id: 31,
                    name: "Dyson Supersonic হেয়ার ড্রায়ার - আয়রন/ফিউশিয়া",
                    darazPrice: 149999,
                    category: "Beauty",
                    image: "https://static-01.daraz.pk/p/beauty34567890123456789012345678.jpg",
                    rating: 4.9,
                    reviews: 450,
                    sold: 890,
                    badge: "লাক্সারি"
                },
                {
                    id: 32,
                    name: "L'Oreal Paris Revitalift অ্যান্টি-এজিং ডে ক্রিম - 50ml",
                    darazPrice: 1899,
                    category: "Beauty",
                    image: "https://static-01.daraz.pk/p/beauty45678901234567890123456789.jpg",
                    rating: 4.6,
                    reviews: 2100,
                    sold: 5600,
                    badge: "অ্যান্টি-এজিং"
                },
                {
                    id: 33,
                    name: "MAC Matte লিপস্টিক - রুবি উ - 3g",
                    darazPrice: 3999,
                    category: "Beauty",
                    image: "https://static-01.daraz.pk/p/beauty56789012345678901234567890.jpg",
                    rating: 4.8,
                    reviews: 1800,
                    sold: 4200,
                    badge: "ক্লাসিক রেড"
                },
                {
                    id: 34,
                    name: "Neutrogena Hydro Boost ওয়াটার জেল - 50ml",
                    darazPrice: 2499,
                    category: "Beauty",
                    image: "https://static-01.daraz.pk/p/beauty67890123456789012345678901.jpg",
                    rating: 4.7,
                    reviews: 1200,
                    sold: 3400,
                    badge: "হাইড্রেশন"
                },
                {
                    id: 35,
                    name: "Philips হেয়ার স্ট্রেইটনার - কেরাটিন প্রোটেক্ট - BHS378",
                    darazPrice: 8999,
                    category: "Beauty",
                    image: "https://static-01.daraz.pk/p/beauty78901234567890123456789012.jpg",
                    rating: 4.6,
                    reviews: 890,
                    sold: 2300,
                    badge: "হেয়ার কেয়ার"
                },
                {
                    id: 36,
                    name: "Olay Total Effects 7-in-1 অ্যান্টি-এজিং সিরাম - 50ml",
                    darazPrice: 3499,
                    category: "Beauty",
                    image: "https://static-01.daraz.pk/p/beauty89012345678901234567890123.jpg",
                    rating: 4.5,
                    reviews: 1500,
                    sold: 4500,
                    badge: "১২.১২ ডিল"
                }
            ],

            selectedPayment: null,
            currentOrder: null,

            init() {
                this.processPrices();
                this.renderProducts(this.products);
                this.loadSampleOrders();
            },

            processPrices() {
                this.products.forEach(p => {
                    p.originalPrice = p.darazPrice;
                    p.price = Math.round(p.darazPrice * 1.04);
                    p.commission = p.price - p.darazPrice;
                });
            },

            formatPrice(price) {
                return '৳ ' + price.toLocaleString('bn-BD');
            },

            renderProducts(products) {
                const grid = document.getElementById('product-grid');
                
                if (products.length === 0) {
                    grid.innerHTML = `
                        <div class="col-span-full text-center py-20">
                            <i class="fa-solid fa-box-open text-6xl text-gray-300 mb-4"></i>
                            <p class="text-gray-500 text-lg">কোনো প্রোডাক্ট পাওয়া যায়নি।</p>
                        </div>
                    `;
                    return;
                }

                grid.innerHTML = products.map(p => `
                    <div class="product-card rounded-xl overflow-hidden shadow-sm border border-gray-100 group">
                        ${p.badge ? `<div class="absolute top-3 left-3 z-10 bg-daraz-orange text-white text-xs font-bold px-3 py-1 rounded-full shadow-md">${p.badge}</div>` : ''}
                        
                        <div class="relative h-56 overflow-hidden bg-gray-100">
                            <img src="${p.image}" alt="${p.name}" class="w-full h-full object-cover group-hover:scale-110 transition-transform duration-500" onerror="this.src='https://via.placeholder.com/300x300?text=No+Image'">
                            <div class="absolute inset-0 bg-black/40 opacity-0 group-hover:opacity-100 transition-opacity duration-300 flex items-center justify-center">
                                <button onclick="app.addToCart(${p.id})" class="bg-white text-gray-900 px-6 py-3 rounded-full font-bold hover:bg-daraz-orange hover:text-white transition-colors transform translate-y-4 group-hover:translate-y-0 duration-300">
                                    কার্টে যোগ করুন
                                </button>
                            </div>
                        </div>
                        
                        <div class="p-4">
                            <div class="flex items-center gap-1 mb-2 text-yellow-400 text-xs">
                                ${this.getStars(p.rating)}
                                <span class="text-gray-400 ml-1">(${p.reviews})</span>
                            </div>
                            
                            <h3 class="font-medium text-gray-900 mb-2 line-clamp-2 h-12 hover:text-daraz-orange transition-colors cursor-pointer">${p.name}</h3>
                            
                            <div class="flex items-baseline gap-2 mb-3">
                                <span class="text-xl font-bold text-daraz-orange">${this.formatPrice(p.price)}</span>
                                <span class="text-sm text-gray-400 line-through">${this.formatPrice(p.originalPrice)}</span>
                            </div>
                            
                            <div class="flex items-center justify-between text-xs text-gray-500 mb-3">
                                <span><i class="fa-solid fa-fire text-red-500 mr-1"></i>${p.sold} বিক্রি</span>
                                <span class="text-green-600">স্টকে আছে</span>
                            </div>
                            
                            <button onclick="app.addToCart(${p.id})" class="w-full bg-daraz-orange text-white py-2.5 rounded-lg font-semibold hover:bg-orange-600 transition-colors flex items-center justify-center gap-2">
                                <i class="fa-solid fa-cart-plus"></i>
                                কার্টে যোগ করুন
                            </button>
                        </div>
                    </div>
                `).join('');
            },

            getStars(rating) {
                let stars = '';
                for (let i = 1; i <= 5; i++) {
                    if (i <= rating) stars += '<i class="fa-solid fa-star"></i>';
                    else if (i - 0.5 <= rating) stars += '<i class="fa-solid fa-star-half-stroke"></i>';
                    else stars += '<i class="fa-regular fa-star"></i>';
                }
                return stars;
            },

            filterCategory(cat) {
                document.querySelectorAll('.category-btn').forEach(btn => {
                    const isActive = btn.getAttribute('onclick').includes(cat);
                    btn.classList.toggle('active', isActive);
                    btn.classList.toggle('bg-daraz-orange', isActive);
                    btn.classList.toggle('text-white', isActive);
                    btn.classList.toggle('bg-gray-200', !isActive);
                    btn.classList.toggle('text-gray-700', !isActive);
                });

                const filtered = cat === 'All' ? this.products : this.products.filter(p => p.category === cat);
                this.renderProducts(filtered);
                
                if (document.getElementById('products-section').classList.contains('hidden')) {
                    this.navigate('products');
                }
            },

            addToCart(id) {
                const product = this.products.find(p => p.id === id);
                const existing = this.cart.find(item => item.id === id);
                
                if (existing) {
                    existing.quantity++;
                } else {
                    this.cart.push({ ...product, quantity: 1 });
                }
                
                this.updateCartUI();
                this.showToast(`${product.name.substring(0, 30)}... কার্টে যোগ করা হয়েছে!`);
            },

            updateCartUI() {
                const container = document.getElementById('cart-items');
                const totalItems = this.cart.reduce((sum, item) => sum + item.quantity, 0);
                const total = this.cart.reduce((sum, item) => sum + (item.price * item.quantity), 0);

                document.getElementById('cart-total').textContent = this.formatPrice(total);
                document.getElementById('cart-badge').textContent = totalItems;
                document.getElementById('cart-badge').style.opacity = totalItems > 0 ? '1' : '0';
                document.getElementById('cart-badge').style.transform = totalItems > 0 ? 'scale(1)' : 'scale(0)';

                if (this.cart.length === 0) {
                    container.innerHTML = '<div class="text-center text-gray-400 py-8">কার্ট খালি</div>';
                } else {
                    container.innerHTML = this.cart.map(item => `
                        <div class="flex gap-4 mb-4 p-3 bg-gray-50 rounded-lg">
                            <img src="${item.image}" class="w-20 h-20 object-cover rounded-lg" onerror="this.src='https://via.placeholder.com/80'">
                            <div class="flex-1">
                                <h4 class="font-medium text-sm line-clamp-2 mb-1">${item.name}</h4>
                                <p class="text-daraz-orange font-bold">${this.formatPrice(item.price)}</p>
                                <div class="flex items-center gap-2 mt-2">
                                    <button onclick="app.updateQuantity(${item.id}, -1)" class="w-8 h-8 rounded bg-white border hover:bg-gray-100 flex items-center justify-center">-</button>
                                    <span class="font-medium">${item.quantity}</span>
                                    <button onclick="app.updateQuantity(${item.id}, 1)" class="w-8 h-8 rounded bg-white border hover:bg-gray-100 flex items-center justify-center">+</button>
                                    <button onclick="app.removeFromCart(${item.id})" class="ml-auto text-red-500 text-sm hover:underline">মুছুন</button>
                                </div>
                            </div>
                        </div>
                    `).join('');
                }
            },

            updateQuantity(id, change) {
                const item = this.cart.find(i => i.id === id);
                if (item) {
                    item.quantity += change;
                    if (item.quantity <= 0) this.removeFromCart(id);
                    else this.updateCartUI();
                }
            },

            removeFromCart(id) {
                this.cart = this.cart.filter(i => i.id !== id);
                this.updateCartUI();
            },

            toggleCart() {
                const sidebar = document.getElementById('cart-sidebar');
                const overlay = document.getElementById('cart-overlay');
                const isOpen = !sidebar.classList.contains('translate-x-full');
                
                if (isOpen) {
                    sidebar.classList.add('translate-x-full');
                    overlay.classList.add('hidden', 'opacity-0');
                } else {
                    sidebar.classList.remove('translate-x-full');
                    overlay.classList.remove('hidden');
                    setTimeout(() => overlay.classList.remove('opacity-0'), 10);
                }
            },

            showCheckout() {
                if (!this.cart.length) return;
                this.toggleCart();
                
                const total = this.cart.reduce((sum, item) => sum + (item.price * item.quantity), 0);
                document.getElementById('checkout-total').textContent = this.formatPrice(total);
                document.getElementById('bkash-amount').textContent = this.formatPrice(total);
                
                document.getElementById('checkout-items').innerHTML = this.cart.map(item => `
                    <div class="flex justify-between text-sm py-1">
                        <span class="line-clamp-1 flex-1">${item.name} × ${item.quantity}</span>
                        <span class="font-medium">${this.formatPrice(item.price * item.quantity)}</span>
                    </div>
                `).join('');
                
                document.getElementById('checkout-modal').classList.remove('hidden');
            },

            closeCheckout() {
                document.getElementById('checkout-modal').classList.add('hidden');
            },

            selectPayment(method) {
                this.selectedPayment = method;
                const btn = document.getElementById('pay-button');
                
                if (method === 'bkash') {
                    btn.innerHTML = '<span>বিকাশে পেমেন্ট করুন (ডেমো)</span><i class="fa-solid fa-mobile-screen"></i>';
                    btn.className = 'w-full bg-bkash-pink text-white py-4 rounded-xl font-bold text-lg hover:bg-pink-700 transition-colors flex items-center justify-center gap-2';
                } else {
                    btn.innerHTML = '<span>ক্যাশ অন ডেলিভারি অর্ডার করুন</span><i class="fa-solid fa-truck"></i>';
                    btn.className = 'w-full bg-green-600 text-white py-4 rounded-xl font-bold text-lg hover:bg-green-700 transition-colors flex items-center justify-center gap-2';
                }
            },

            processPayment() {
                const name = document.getElementById('customer-name').value;
                const phone = document.getElementById('customer-phone').value;
                const address = document.getElementById('customer-address').value;
                
                if (!name || !phone || !address) {
                    this.showToast('সব তথ্য পূরণ করুন', 'error');
                    return;
                }
                
                if (!this.selectedPayment) {
                    this.showToast('পেমেন্ট মেথড নির্বাচন করুন', 'error');
                    return;
                }

                if (this.selectedPayment === 'bkash') {
                    document.getElementById('bkash-modal').classList.remove('hidden');
                } else {
                    this.createOrder('cod', 'pending');
                }
            },

            closeBkashModal() {
                document.getElementById('bkash-modal').classList.add('hidden');
            },

            confirmBkashPayment() {
                const btn = document.getElementById('bkash-confirm-btn');
                btn.innerHTML = '<div class="loading-spinner w-5 h-5 border-2 border-white/30 border-t-white"></div> প্রসেসিং...';
                
                setTimeout(() => {
                    this.closeBkashModal();
                    this.createOrder('bKash', 'paid');
                    btn.innerHTML = '<span>কনফার্ম</span><i class="fa-solid fa-check"></i>';
                }, 2000);
            },

            createOrder(paymentMethod, paymentStatus) {
                const total = this.cart.reduce((sum, item) => sum + (item.price * item.quantity), 0);
                const orderId = 'ORD-' + Date.now().toString().slice(-6);
                
                const order = {
                    id: orderId,
                    customer: document.getElementById('customer-name').value,
                    phone: document.getElementById('customer-phone').value,
                    address: document.getElementById('customer-address').value,
                    items: [...this.cart],
                    total: total,
                    paymentMethod: paymentMethod,
                    paymentStatus: paymentStatus,
                    status: 'pending',
                    date: new Date().toLocaleString('bn-BD')
                };
                
                this.orders.unshift(order);
                this.currentOrder = order;
                
                this.cart = [];
                this.updateCartUI();
                this.closeCheckout();
                
                document.getElementById('success-order-id').textContent = '#' + orderId;
                document.getElementById('success-modal').classList.remove('hidden');
                
                this.renderOrders();
                this.renderAdminOrders();
            },

            closeSuccessModal() {
                document.getElementById('success-modal').classList.add('hidden');
            },

            renderOrders() {
                const container = document.getElementById('orders-list');
                
                if (!this.orders.length) {
                    container.innerHTML = `
                        <div class="text-center py-12 text-gray-400">
                            <i class="fa-solid fa-box-open text-6xl mb-4 opacity-30"></i>
                            <p>কোনো অর্ডার নেই। শপিং শুরু করুন!</p>
                        </div>`;
                    return;
                }

                container.innerHTML = this.orders.map(order => {
                    const statusColors = {
                        pending: 'bg-yellow-100 text-yellow-700',
                        processing: 'bg-blue-100 text-blue-700',
                        shipped: 'bg-purple-100 text-purple-700',
                        delivered: 'bg-green-100 text-green-700'
                    };
                    
                    const statusText = {
                        pending: 'পেন্ডিং',
                        processing: 'প্রসেসিং',
                        shipped: 'শিপড',
                        delivered: 'ডেলিভার্ড'
                    };

                    return `
                    <div class="bg-white rounded-xl shadow-sm border border-gray-100 overflow-hidden mb-4">
                        <div class="p-4 border-b bg-gray-50 flex justify-between items-center">
                            <div>
                                <span class="font-bold text-lg">${order.id}</span>
                                <span class="text-gray-400 text-sm ml-2">${order.date}</span>
                            </div>
                            <span class="px-3 py-1 rounded-full text-xs font-bold ${order.paymentStatus === 'paid' ? 'bg-green-100 text-green-700' : 'bg-yellow-100 text-yellow-700'}">
                                ${order.paymentStatus === 'paid' ? 'পেইড' : 'পেমেন্ড পেন্ডিং'}
                            </span>
                        </div>
                        <div class="p-4">
                            <div class="space-y-2 mb-4">
                                ${order.items.map(item => `
                                    <div class="flex justify-between text-sm">
                                        <span class="line-clamp-1 flex-1">${item.name} × ${item.quantity}</span>
                                        <span>${this.formatPrice(item.price * item.quantity)}</span>
                                    </div>
                                `).join('')}
                            </div>
                            <div class="border-t pt-3 flex justify-between items-center">
                                <div>
                                    <p class="text-xs text-gray-500">মোট: <span class="text-lg font-bold text-daraz-orange">${this.formatPrice(order.total)}</span></p>
                                    <p class="text-xs text-gray-400">${order.paymentMethod.toUpperCase()}</p>
                                </div>
                                <span class="px-3 py-1 rounded-full text-xs font-bold ${statusColors[order.status]}">
                                    ${statusText[order.status]}
                                </span>
                            </div>
                        </div>
                    </div>
                    `;
                }).join('');
            },

            renderAdminOrders() {
                const tbody = document.getElementById('admin-orders-table');
                document.getElementById('admin-total-orders').textContent = this.orders.length;
                
                const paidRevenue = this.orders
                    .filter(o => o.paymentStatus === 'paid')
                    .reduce((sum, o) => sum + o.total, 0);
                document.getElementById('admin-revenue').textContent = this.formatPrice(paidRevenue);

                tbody.innerHTML = this.orders.map(order => `
                    <tr class="hover:bg-gray-50">
                        <td class="px-6 py-4 font-medium">${order.id}</td>
                        <td class="px-6 py-4">
                            <div class="font-medium">${order.customer}</div>
                            <div class="text-sm text-gray-500">${order.phone}</div>
                        </td>
                        <td class="px-6 py-4">${order.items.length} আইটেম</td>
                        <td class="px-6 py-4 font-bold">${this.formatPrice(order.total)}</td>
                        <td class="px-6 py-4">
                            <span class="px-2 py-1 rounded text-xs font-bold ${order.paymentMethod === 'bkash' ? 'bg-pink-100 text-pink-700' : 'bg-green-100 text-green-700'}">
                                ${order.paymentMethod.toUpperCase()}
                            </span>
                        </td>
                        <td class="px-6 py-4">
                            <select onchange="app.updateOrderStatus('${order.id}', this.value)" class="text-sm border rounded px-2 py-1">
                                <option value="pending" ${order.status === 'pending' ? 'selected' : ''}>পেন্ডিং</option>
                                <option value="processing" ${order.status === 'processing' ? 'selected' : ''}>প্রসেসিং</option>
                                <option value="shipped" ${order.status === 'shipped' ? 'selected' : ''}>শিপড</option>
                                <option value="delivered" ${order.status === 'delivered' ? 'selected' : ''}>ডেলিভার্ড</option>
                            </select>
                        </td>
                        <td class="px-6 py-4">
                            <button onclick="app.viewOrderDetails('${order.id}')" class="text-blue-600 hover:text-blue-800 text-sm">দেখুন</button>
                        </td>
                    </tr>
                `).join('');
            },

            updateOrderStatus(orderId, status) {
                const order = this.orders.find(o => o.id === orderId);
                if (order) {
                    order.status = status;
                    this.renderOrders();
                    this.renderAdminOrders();
                    this.showToast(`অর্ডার ${orderId} আপডেট হয়েছে`);
                }
            },

            viewOrderDetails(orderId) {
                const order = this.orders.find(o => o.id === orderId);
                alert(`অর্ডার বিস্তারিত:\n\nকাস্টমার: ${order.customer}\nফোন: ${order.phone}\nঠিকানা: ${order.address}\n\nআইটেম:\n${order.items.map(i => `- ${i.name} x${i.quantity}`).join('\n')}\n\nমোট: ${this.formatPrice(order.total)}`);
            },

            loadSampleOrders() {
                this.orders = [
                    {
                        id: 'ORD-001234',
                        customer: 'আহমেদ খান',
                        phone: '01712345678',
                        address: '১২৩ গুলশান এভিনিউ, ঢাকা',
                        items: [{ name: 'realme C53', price: 30159, quantity: 1 }],
                        total: 30159,
                        paymentMethod: 'bkash',
                        paymentStatus: 'paid',
                        status: 'shipped',
                        date: '১০ ডিসেম্বর ২০২৪, ১৪:৩০'
                    },
                    {
                        id: 'ORD-001235',
                        customer: 'ফাতেমা রহমান',
                        phone: '01898765432',
                        address: '৪৫ ধানমন্ডি, ঢাকা',
                        items: [{ name: 'Philips Air Fryer', price: 25999, quantity: 1 }],
                        total: 25999,
                        paymentMethod: 'cod',
                        paymentStatus: 'pending',
                        status: 'processing',
                        date: '১১ ডিসেম্বর ২০২৪, ০৯:১৫'
                    }
                ];
                this.renderOrders();
                this.renderAdminOrders();
            },

            navigate(section) {
                ['home', 'products', 'orders', 'admin'].forEach(s => {
                    document.getElementById(`${s}-section`).classList.add('hidden');
                });
                document.getElementById(`${section}-section`).classList.remove('hidden');
                window.scrollTo(0, 0);
            },

            showToast(message, type = 'success') {
                const container = document.getElementById('toast-container');
                const toast = document.createElement('div');
                toast.className = `toast bg-gray-900 text-white px-6 py-3 rounded-lg shadow-lg flex items-center gap-3 ${type === 'error' ? 'border-l-4 border-red-500' : ''}`;
                toast.innerHTML = `<i class="fa-solid ${type === 'error' ? 'fa-circle-exclamation text-red-400' : 'fa-check-circle text-green-400'}"></i><span>${message}</span>`;
                container.appendChild(toast);
                setTimeout(() => toast.remove(), 3000);
            }
        };

        document.addEventListener('DOMContentLoaded', () => app.init());
    </script>
</body>
</html>
