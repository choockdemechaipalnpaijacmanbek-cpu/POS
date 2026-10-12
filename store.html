<!DOCTYPE html>
<html lang="th">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>ระบบ POS & จัดการสต็อกสินค้า (FIFO Cloud)</title>
    <script src="https://cdn.tailwindcss.com"></script>
    <link href="https://fonts.googleapis.com/css2?family=Prompt:wght@300;400;500;600;700&display=swap" rel="stylesheet">
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.4.0/css/all.min.css">
    <script type="text/javascript" src="https://unpkg.com/@zxing/library@latest"></script>
    <style>
        body { font-family: 'Prompt', sans-serif; }
    </style>
</head>
<body class="bg-slate-100 min-h-screen text-slate-800 pb-12">

<header class="bg-gradient-to-r from-indigo-600 to-violet-600 text-white shadow-md sticky top-0 z-40">
    <div class="max-w-6xl mx-auto px-4 py-3.5 flex flex-col sm:flex-row items-center justify-between gap-3">
        <div class="flex items-center gap-2">
            <div class="w-9 h-9 rounded-xl bg-white/10 flex items-center justify-center text-xl">
                <i class="fa-solid fa-store text-amber-300"></i>
            </div>
            <div>
                <h1 class="text-lg sm:text-xl font-bold leading-tight">Mini Store POS (FIFO)</h1>
                <p id="syncStatus" class="text-xs text-indigo-200">กำลังเชื่อมต่อคลาวด์...</p>
            </div>
        </div>
        <div class="flex bg-black/20 p-1 rounded-xl text-xs font-medium">
            <button onclick="switchTab('pos')" id="tabBtn-pos" class="px-4 py-2 rounded-lg transition bg-white text-indigo-700 shadow-sm">
                <i class="fa-solid fa-cash-register mr-1"></i> หน้าขาย (POS)
            </button>
            <button onclick="switchTab('inventory')" id="tabBtn-inventory" class="px-4 py-2 rounded-lg transition text-white hover:bg-white/10">
                <i class="fa-solid fa-boxes-stacked mr-1"></i> สต็อกสินค้า
            </button>
            <button onclick="switchTab('summary')" id="tabBtn-summary" class="px-4 py-2 rounded-lg transition text-white hover:bg-white/10">
                <i class="fa-solid fa-chart-line mr-1"></i> สรุปยอด/กำไร
            </button>
        </div>
    </div>
</header>

<main class="max-w-6xl mx-auto px-4 mt-6">

    <!-- 1. TAB: POS -->
    <div id="tabContent-pos" class="space-y-6">
        <div class="grid grid-cols-1 lg:grid-cols-3 gap-6">
            <div class="lg:col-span-2 space-y-4">
                <div class="bg-white rounded-2xl p-5 shadow-sm border border-slate-200">
                    <div class="flex items-center justify-between mb-3">
                        <h2 class="text-sm font-bold text-slate-700 flex items-center gap-2">
                            <i class="fa-solid fa-barcode text-indigo-600"></i> สแกนหรือเลือกสินค้าลงตะกร้า
                        </h2>
                        <button onclick="openScanner('pos')" class="bg-indigo-50 hover:bg-indigo-100 text-indigo-600 text-xs px-3 py-1.5 rounded-xl font-medium transition flex items-center gap-1.5">
                            <i class="fa-solid fa-camera"></i> เปิดกล้องสแกนขาย
                        </button>
                    </div>
                    <div id="posProductGrid" class="grid grid-cols-2 sm:grid-cols-3 gap-3 mt-4 max-h-[380px] overflow-y-auto pr-1"></div>
                </div>
            </div>

            <div class="space-y-4">
                <div class="bg-white rounded-2xl p-5 shadow-sm border border-slate-200 flex flex-col justify-between h-[510px]">
                    <div>
                        <h2 class="text-sm font-bold text-slate-700 mb-3 flex items-center justify-between">
                            <span><i class="fa-solid fa-cart-shopping text-indigo-600"></i> ตะกร้าสินค้าในบิลนี้</span>
                            <button onclick="clearCart()" class="text-xs text-red-500 hover:underline">ล้างตะกร้า</button>
                        </h2>
                        <div id="cartItemList" class="divide-y divide-slate-100 max-h-[300px] overflow-y-auto pr-1 space-y-2">
                            <p class="text-xs text-slate-400 text-center py-10">ยังไม่มีสินค้าในตะกร้า</p>
                        </div>
                    </div>

                    <div class="border-t border-slate-100 pt-4 space-y-3">
                        <div class="flex justify-between items-center text-sm">
                            <span class="text-slate-500">ยอดรวมทั้งสิ้น:</span>
                            <span id="cartTotalPrice" class="text-xl font-bold text-indigo-600">0.00 ฿</span>
                        </div>
                        <button onclick="checkout()" class="w-full bg-indigo-600 hover:bg-indigo-700 active:bg-indigo-800 text-white font-medium py-3 rounded-xl shadow-sm transition flex items-center justify-center gap-2">
                            <i class="fa-solid fa-check-to-slot"></i> ยืนยันการขาย (Checkout)
                        </button>
                    </div>
                </div>
            </div>
        </div>
    </div>

    <!-- 2. TAB: INVENTORY -->
    <div id="tabContent-inventory" class="hidden space-y-6">
        <div class="bg-white rounded-2xl p-5 sm:p-6 shadow-sm border border-slate-200">
            <div class="flex items-center justify-between mb-4">
                <h2 class="text-base font-semibold text-slate-800 flex items-center gap-2">
                    <i class="fa-solid fa-box-archive text-indigo-600"></i> เพิ่มสินค้าใหม่ / นำสินค้าเข้าสต็อก (FIFO)
                </h2>
                <button onclick="openScanner('inv')" class="bg-indigo-50 hover:bg-indigo-100 text-indigo-600 text-xs px-3 py-1.5 rounded-xl font-medium transition flex items-center gap-1.5">
                    <i class="fa-solid fa-camera"></i> สแกนบาร์โค้ดรับเข้า
                </button>
            </div>
            <form onsubmit="addInventoryBatch(event)" class="grid grid-cols-1 sm:grid-cols-2 lg:grid-cols-5 gap-3.5">
                <div>
                    <label class="block text-xs font-medium text-slate-600 mb-1">รหัสบาร์โค้ด</label>
                    <input type="text" id="invBarcode" oninput="checkExistingBarcode(this.value)" placeholder="เช่น 885001" required class="w-full px-3 py-2 border border-slate-300 rounded-xl text-sm outline-none">
                </div>
                <div>
                    <label class="block text-xs font-medium text-slate-600 mb-1">ชื่อสินค้า</label>
                    <input type="text" id="invName" placeholder="เช่น น้ำดื่ม" required class="w-full px-3 py-2 border border-slate-300 rounded-xl text-sm outline-none">
                </div>
                <div>
                    <label class="block text-xs font-medium text-slate-600 mb-1">จำนวนรับเข้า</label>
                    <input type="number" id="invQty" min="1" placeholder="0" required class="w-full px-3 py-2 border border-slate-300 rounded-xl text-sm outline-none">
                </div>
                <div>
                    <label class="block text-xs font-medium text-slate-600 mb-1">ต้นทุน/หน่วย (บาท)</label>
                    <input type="number" id="invCost" min="0.01" step="any" placeholder="0.00" required class="w-full px-3 py-2 border border-slate-300 rounded-xl text-sm outline-none">
                </div>
                <div>
                    <label class="block text-xs font-medium text-slate-600 mb-1">ราคาขาย/หน่วย (บาท)</label>
                    <input type="number" id="invPrice" min="0.01" step="any" placeholder="0.00" required class="w-full px-3 py-2 border border-slate-300 rounded-xl text-sm outline-none">
                </div>
                <div class="sm:col-span-2 lg:col-span-5 mt-1">
                    <button type="submit" class="w-full bg-indigo-600 hover:bg-indigo-700 text-white font-medium py-2.5 rounded-xl transition text-xs">
                        บันทึกรับเข้าสต็อก
                    </button>
                </div>
            </form>
        </div>

        <div class="bg-white rounded-2xl p-5 sm:p-6 shadow-sm border border-slate-200">
            <h2 class="text-base font-semibold text-slate-800 mb-4">สต็อกสินค้าคงเหลือแยกตามล็อต (FIFO)</h2>
            <div class="overflow-x-auto">
                <table class="w-full text-left border-collapse min-w-[600px]">
                    <thead>
                        <tr class="border-b border-slate-200 text-xs font-semibold text-slate-500 bg-slate-50">
                            <th class="py-2.5 px-3">บาร์โค้ด</th>
                            <th class="py-2.5 px-3">ชื่อสินค้า</th>
                            <th class="py-2.5 px-3">วันที่รับเข้า</th>
                            <th class="py-2.5 px-3 text-right">คงเหลือ</th>
                            <th class="py-2.5 px-3 text-right">ต้นทุน/หน่วย</th>
                            <th class="py-2.5 px-3 text-right">ราคาขาย/หน่วย</th>
                            <th class="py-2.5 px-3 text-center">จัดการ</th>
                        </tr>
                    </thead>
                    <tbody id="inventoryTableBody" class="divide-y divide-slate-100 text-sm"></tbody>
                </table>
            </div>
        </div>
    </div>

    <!-- 3. TAB: SUMMARY -->
    <div id="tabContent-summary" class="hidden space-y-6">
        <div class="bg-white rounded-2xl p-5 sm:p-6 shadow-sm border border-slate-200">
            <h2 class="text-base font-semibold text-slate-800 mb-4">บันทึกค่าใช้จ่ายเพิ่มเติม</h2>
            <form onsubmit="addExtraExpense(event)" class="grid grid-cols-1 sm:grid-cols-3 gap-3.5">
                <div>
                    <label class="block text-xs font-medium text-slate-600 mb-1">วันที่</label>
                    <input type="date" id="exDate" required class="w-full px-3 py-2 border border-slate-300 rounded-xl text-sm outline-none">
                </div>
                <div>
                    <label class="block text-xs font-medium text-slate-600 mb-1">รายการ</label>
                    <input type="text" id="exTitle" placeholder="เช่น ค่าเช่าร้าน" required class="w-full px-3 py-2 border border-slate-300 rounded-xl text-sm outline-none">
                </div>
                <div>
                    <label class="block text-xs font-medium text-slate-600 mb-1">จำนวนเงิน (บาท)</label>
                    <input type="number" id="exAmount" min="0.01" step="any" placeholder="0.00" required class="w-full px-3 py-2 border border-slate-300 rounded-xl text-sm outline-none">
                </div>
                <div class="sm:col-span-3">
                    <button type="submit" class="w-full bg-slate-800 hover:bg-slate-900 text-white font-medium py-2.5 rounded-xl transition text-xs">บันทึกค่าใช้จ่าย</button>
                </div>
            </form>
        </div>

        <div class="grid grid-cols-2 sm:grid-cols-4 gap-4">
            <div class="bg-white p-4 rounded-2xl border border-slate-200 shadow-sm">
                <span class="text-xs text-slate-500 block mb-1">ยอดขายรวมทั้งหมด</span>
                <span id="sumTotalSales" class="text-xl font-bold text-indigo-600">0.00 ฿</span>
            </div>
            <div class="bg-white p-4 rounded-2xl border border-slate-200 shadow-sm">
                <span class="text-xs text-slate-500 block mb-1">ต้นทุนสินค้าที่ขาย</span>
                <span id="sumTotalCost" class="text-xl font-bold text-amber-600">0.00 ฿</span>
            </div>
            <div class="bg-white p-4 rounded-2xl border border-slate-200 shadow-sm">
                <span class="text-xs text-slate-500 block mb-1">ค่าใช้จ่ายเพิ่มเติม</span>
                <span id="sumTotalExtra" class="text-xl font-bold text-rose-600">0.00 ฿</span>
            </div>
            <div class="bg-emerald-50 p-4 rounded-2xl border border-emerald-200 shadow-sm">
                <span class="text-xs text-emerald-700 font-medium block mb-1">กำไรสุทธิ</span>
                <span id="sumNetProfit" class="text-xl font-bold text-emerald-600">0.00 ฿</span>
            </div>
        </div>

        <div class="bg-white rounded-2xl p-5 sm:p-6 shadow-sm border border-slate-200">
            <h2 class="text-base font-semibold text-slate-800 mb-4">ประวัติการขายสินค้า (Bills History)</h2>
            <div class="overflow-x-auto">
                <table class="w-full text-left border-collapse min-w-[500px]">
                    <thead>
                        <tr class="border-b border-slate-200 text-xs font-semibold text-slate-500 bg-slate-50">
                            <th class="py-2.5 px-3">เวลา</th>
                            <th class="py-2.5 px-3">รายการ</th>
                            <th class="py-2.5 px-3 text-right">ยอดรวม</th>
                            <th class="py-2.5 px-3 text-right">ต้นทุน</th>
                            <th class="py-2.5 px-3 text-right">กำไรสุทธิ</th>
                        </tr>
                    </thead>
                    <tbody id="salesHistoryTableBody" class="divide-y divide-slate-100 text-sm"></tbody>
                </table>
            </div>
        </div>
    </div>
</main>

<div id="scannerModal" class="fixed inset-0 bg-slate-900/65 backdrop-blur-sm hidden items-center justify-center p-4 z-50">
    <div class="bg-white rounded-2xl max-w-md w-full p-5 text-center shadow-2xl space-y-4">
        <h3 id="scannerTitle" class="text-base font-bold text-slate-800">สแกนบาร์โค้ด</h3>
        <div class="relative w-full aspect-square bg-black rounded-xl overflow-hidden flex items-center justify-center">
            <video id="videoPreview" class="w-full h-full object-cover"></video>
        </div>
        <button onclick="closeScanner()" class="w-full bg-slate-200 text-slate-700 text-xs py-2.5 rounded-xl font-medium">ปิดกล้อง</button>
    </div>
</div>

<div id="customModal" class="fixed inset-0 bg-slate-900/40 backdrop-blur-sm hidden items-center justify-center p-4 z-50">
    <div class="bg-white rounded-2xl max-w-sm w-full p-5 text-center shadow-xl">
        <h3 id="modalTitle" class="text-base font-bold text-slate-800 mb-1">แจ้งเตือน</h3>
        <p id="modalMessage" class="text-xs text-slate-600 mb-4"></p>
        <button onclick="closeModal()" class="bg-indigo-600 text-white text-xs px-4 py-2 rounded-xl font-medium">ตกลง</button>
    </div>
</div>

<script>
    const BIN_ID = "6acc57a1ac6210605a296392";
    const API_KEY = "$2a$10$d2fLdBv0Y.E2.UzQ5UWGzu7.mfMdKXWfwKeKCbS28PZFe4LrdC1XS";

    const urlParams = new URLSearchParams(window.location.search);
    let storeId = urlParams.get('store');
    if (!storeId) {
        storeId = 'store_' + Math.random().toString(36).substring(2, 9);
        const newUrl = window.location.protocol + "//" + window.location.host + window.location.pathname + '?store=' + storeId;
        window.history.replaceState({path: newUrl}, '', newUrl);
    }

    let inventory = [];
    let cart = [];
    let sales = [];
    let extraExpenses = [];
    let codeReader = null;
    let scannerMode = 'pos'; // 'pos' หรือ 'inv'

    async function loadData() {
        try {
            const res = await fetch(`https://api.jsonbin.io/v3/b/${BIN_ID}/latest`, {
                headers: { 'X-Master-Key': API_KEY }
            });
            const json = await res.json();
            const data = json.record && json.record[storeId] ? json.record[storeId] : {};
            inventory = data.inventory || [];
            sales = data.sales || [];
            extraExpenses = data.extraExpenses || [];
            document.getElementById('syncStatus').innerText = 'เชื่อมต่อคลาวด์เรียบร้อย';
        } catch (e) {
            inventory = JSON.parse(localStorage.getItem('pos_inv_' + storeId)) || [];
            sales = JSON.parse(localStorage.getItem('pos_sales_' + storeId)) || [];
            extraExpenses = JSON.parse(localStorage.getItem('pos_ex_' + storeId)) || [];
        }
        renderAll();
    }

    async function saveData() {
        localStorage.setItem('pos_inv_' + storeId, JSON.stringify(inventory));
        localStorage.setItem('pos_sales_' + storeId, JSON.stringify(sales));
        localStorage.setItem('pos_ex_' + storeId, JSON.stringify(extraExpenses));

        try {
            const res = await fetch(`https://api.jsonbin.io/v3/b/${BIN_ID}/latest`, {
                headers: { 'X-Master-Key': API_KEY }
            });
            const json = await res.json();
            let allData = json.record || {};
            allData[storeId] = { inventory, sales, extraExpenses };

            await fetch(`https://api.jsonbin.io/v3/b/${BIN_ID}`, {
                method: 'PUT',
                headers: { 'Content-Type': 'application/json', 'X-Master-Key': API_KEY },
                body: JSON.stringify(allData)
            });
            document.getElementById('syncStatus').innerText = 'ซิงค์คลาวด์สำเร็จ';
        } catch (e) {}
    }

    window.onload = function() {
        document.getElementById('exDate').value = new Date().toISOString().split('T')[0];
        loadData();
    };

    function switchTab(tab) {
        ['pos', 'inventory', 'summary'].forEach(t => {
            document.getElementById(`tabContent-${t}`).classList.add('hidden');
            document.getElementById(`tabBtn-${t}`).className = "px-4 py-2 rounded-lg transition text-white hover:bg-white/10";
        });
        document.getElementById(`tabContent-${tab}`).classList.remove('hidden');
        document.getElementById(`tabBtn-${tab}`).className = "px-4 py-2 rounded-lg transition bg-white text-indigo-700 shadow-sm";
    }

    // ฟังก์ชันเช็คว่ามีบาร์โค้ดนี้อยู่แล้วไหม ถ้ามี ดึงชื่อและราคาขายมาเติมให้ทันที
    window.checkExistingBarcode = function(barcode) {
        if (!barcode) return;
        const found = inventory.find(i => i.barcode === barcode.trim());
        if (found) {
            document.getElementById('invName').value = found.name;
            document.getElementById('invPrice').value = found.price;
            document.getElementById('invCost').value = found.cost; // เติมต้นทุนรอบล่าสุดให้เป็นแนวทางด้วย
        }
    };

    window.addInventoryBatch = async function(e) {
        e.preventDefault();
        const barcode = document.getElementById('invBarcode').value.trim();
        const name = document.getElementById('invName').value.trim();
        const qty = parseInt(document.getElementById('invQty').value);
        const cost = parseFloat(document.getElementById('invCost').value);
        const price = parseFloat(document.getElementById('invPrice').value);

        if (!barcode || !name || isNaN(qty) || qty <= 0) return;

        inventory.push({
            id: 'lot_' + Date.now() + Math.random().toString(36).substring(2,5),
            barcode, name, qty, remainingQty: qty, cost, price, date: new Date().toISOString()
        });

        document.getElementById('invBarcode').value = '';
        document.getElementById('invName').value = '';
        document.getElementById('invQty').value = '';
        document.getElementById('invCost').value = '';
        document.getElementById('invPrice').value = '';

        renderAll();
        await saveData();
        showAlert('สำเร็จ', 'นำสินค้าเข้าสต็อกเรียบร้อย');
    };

    window.deleteLot = async function(id) {
        inventory = inventory.filter(item => item.id !== id);
        renderAll();
        await saveData();
    };

    window.addToCart = function(barcode) {
        const availableLots = inventory.filter(i => i.barcode === barcode && i.remainingQty > 0);
        if (availableLots.length === 0) {
            showAlert('สินค้าหมด', 'สินค้ารายการนี้หมดจากสต็อกแล้ว');
            return;
        }
        const retailPrice = availableLots[0].price;
        const productName = availableLots[0].name;

        const existing = cart.find(i => i.barcode === barcode);
        if (existing) {
            existing.qty += 1;
        } else {
            cart.push({ barcode, name: productName, price: retailPrice, qty: 1 });
        }
        renderCart();
    };

    window.updateCartQty = function(barcode, delta) {
        const item = cart.find(i => i.barcode === barcode);
        if (!item) return;
        item.qty += delta;
        if (item.qty <= 0) {
            cart = cart.filter(i => i.barcode !== barcode);
        }
        renderCart();
    };

    window.clearCart = function() {
        cart = [];
        renderCart();
    };

    window.renderCart = function() {
        const container = document.getElementById('cartItemList');
        container.innerHTML = '';
        let total = 0;

        if (cart.length === 0) {
            container.innerHTML = '<p class="text-xs text-slate-400 text-center py-10">ยังไม่มีสินค้าในตะกร้า</p>';
            document.getElementById('cartTotalPrice').innerText = '0.00 ฿';
            return;
        }

        cart.forEach(item => {
            const subtotal = item.price * item.qty;
            total += subtotal;
            const div = document.createElement('div');
            div.className = "flex items-center justify-between py-2";
            div.innerHTML = `
                <div>
                    <h4 class="text-xs font-bold text-slate-800">${item.name}</h4>
                    <span class="text-[10px] text-slate-500">${item.price} ฿ × ${item.qty}</span>
                </div>
                <div class="flex items-center gap-2">
                    <span class="text-xs font-bold text-indigo-600">${subtotal.toLocaleString()} ฿</span>
                    <div class="flex items-center border border-slate-200 rounded-lg overflow-hidden">
                        <button onclick="updateCartQty('${item.barcode}', -1)" class="px-2 py-0.5 bg-slate-50 text-xs">-</button>
                        <span class="px-2 text-xs font-medium">${item.qty}</span>
                        <button onclick="updateCartQty('${item.barcode}', 1)" class="px-2 py-0.5 bg-slate-50 text-xs">+</button>
                    </div>
                </div>
            `;
            container.appendChild(div);
        });

        document.getElementById('cartTotalPrice').innerText = total.toLocaleString() + ' ฿';
    };

    window.checkout = async function() {
        if (cart.length === 0) return;

        let totalSaleAmount = 0;
        let totalCostAmount = 0;
        let billItemsDetail = [];

        for (let cartItem of cart) {
            let qtyNeeded = cartItem.qty;
            let itemCostSum = 0;

            let matchingLots = inventory
                .filter(i => i.barcode === cartItem.barcode && i.remainingQty > 0)
                .sort((a, b) => new Date(a.date) - new Date(b.date));

            let totalAvailableQty = matchingLots.reduce((sum, l) => sum + l.remainingQty, 0);
            if (totalAvailableQty < qtyNeeded) {
                showAlert('สินค้าไม่พอ', `สินค้า ${cartItem.name} ในสต็อกไม่เพียงพอ`);
                return;
            }

            for (let lot of matchingLots) {
                if (qtyNeeded <= 0) break;
                let takeQty = Math.min(lot.remainingQty, qtyNeeded);
                lot.remainingQty -= takeQty;
                qtyNeeded -= takeQty;
                itemCostSum += (takeQty * lot.cost);
            }

            let itemSale = cartItem.price * cartItem.qty;
            totalSaleAmount += itemSale;
            totalCostAmount += itemCostSum;
            billItemsDetail.push(`${cartItem.name} (${cartItem.qty} ชิ้น)`);
        }

        sales.push({
            id: 'bill_' + Date.now(),
            date: new Date().toISOString(),
            items: billItemsDetail.join(', '),
            totalSale: totalSaleAmount,
            totalCost: totalCostAmount,
            netProfit: totalSaleAmount - totalCostAmount
        });

        cart = [];
        renderCart();
        renderAll();
        await saveData();
        showAlert('สำเร็จ', 'บันทึกบิลขายและตัดสต็อก FIFO สำเร็จ');
    };

    window.addExtraExpense = async function(e) {
        e.preventDefault();
        const date = document.getElementById('exDate').value;
        const title = document.getElementById('exTitle').value.trim();
        const amount = parseFloat(document.getElementById('exAmount').value);

        if (!date || !title || isNaN(amount)) return;
        extraExpenses.push({ id: Date.now(), date, title, amount });
        document.getElementById('exTitle').value = '';
        document.getElementById('exAmount').value = '';

        renderAll();
        await saveData();
        showAlert('สำเร็จ', 'บันทึกค่าใช้จ่ายเพิ่มเติมเรียบร้อย');
    };

    function renderAll() {
        const invBody = document.getElementById('inventoryTableBody');
        invBody.innerHTML = '';
        inventory.forEach(item => {
            const tr = document.createElement('tr');
            tr.className = "hover:bg-slate-50";
            tr.innerHTML = `
                <td class="py-3 px-3 font-mono text-xs text-slate-600">${item.barcode}</td>
                <td class="py-3 px-3 font-medium text-slate-800">${item.name}</td>
                <td class="py-3 px-3 text-xs text-slate-500">${new Date(item.date).toLocaleDateString('th-TH')}</td>
                <td class="py-3 px-3 text-right font-bold text-indigo-600">${item.remainingQty}</td>
                <td class="py-3 px-3 text-right text-slate-600">${item.cost.toLocaleString()} ฿</td>
                <td class="py-3 px-3 text-right text-slate-600">${item.price.toLocaleString()} ฿</td>
                <td class="py-3 px-3 text-center"><button onclick="deleteLot('${item.id}')" class="text-slate-400 hover:text-red-500"><i class="fa-solid fa-trash-can"></i></button></td>
            `;
            invBody.appendChild(tr);
        });

        const posGrid = document.getElementById('posProductGrid');
        posGrid.innerHTML = '';
        const uniqueProducts = {};
        inventory.forEach(i => {
            if (i.remainingQty > 0) {
                if (!uniqueProducts[i.barcode]) {
                    uniqueProducts[i.barcode] = { name: i.name, price: i.price, totalStock: 0, barcode: i.barcode };
                }
                uniqueProducts[i.barcode].totalStock += i.remainingQty;
            }
        });

        Object.values(uniqueProducts).forEach(prod => {
            const card = document.createElement('div');
            card.className = "bg-slate-50 hover:bg-indigo-50/50 border border-slate-200 p-3.5 rounded-xl cursor-pointer transition flex flex-col justify-between";
            card.onclick = () => addToCart(prod.barcode);
            card.innerHTML = `
                <div>
                    <h4 class="text-xs font-bold text-slate-800 line-clamp-1">${prod.name}</h4>
                    <span class="text-[10px] text-slate-400 font-mono">บาร์โค้ด: ${prod.barcode}</span>
                </div>
                <div class="mt-2 flex items-center justify-between">
                    <span class="text-xs font-bold text-indigo-600">${prod.price} ฿</span>
                    <span class="text-[10px] bg-indigo-100 text-indigo-700 px-2 py-0.5 rounded-full">เหลือ ${prod.totalStock}</span>
                </div>
            `;
            posGrid.appendChild(card);
        });

        let totalSales = sales.reduce((s, i) => s + i.totalSale, 0);
        let totalCost = sales.reduce((s, i) => s + i.totalCost, 0);
        let totalExtra = extraExpenses.reduce((s, i) => s + i.amount, 0);
        let netProfit = totalSales - totalCost - totalExtra;

        document.getElementById('sumTotalSales').innerText = totalSales.toLocaleString() + ' ฿';
        document.getElementById('sumTotalCost').innerText = totalCost.toLocaleString() + ' ฿';
        document.getElementById('sumTotalExtra').innerText = totalExtra.toLocaleString() + ' ฿';
        document.getElementById('sumNetProfit').innerText = netProfit.toLocaleString() + ' ฿';

        const salesBody = document.getElementById('salesHistoryTableBody');
        salesBody.innerHTML = '';
        sales.slice().reverse().forEach(bill => {
            const tr = document.createElement('tr');
            tr.className = "hover:bg-slate-50";
            tr.innerHTML = `
                <td class="py-3 px-3 text-xs text-slate-600">${new Date(bill.date).toLocaleTimeString('th-TH')}</td>
                <td class="py-3 px-3 text-xs text-slate-800 font-medium">${bill.items}</td>
                <td class="py-3 px-3 text-right font-bold text-indigo-600">${bill.totalSale.toLocaleString()} ฿</td>
                <td class="py-3 px-3 text-right text-slate-500">${bill.totalCost.toLocaleString()} ฿</td>
                <td class="py-3 px-3 text-right font-bold text-emerald-600">+${bill.netProfit.toLocaleString()} ฿</td>
            `;
            salesBody.appendChild(tr);
        });
    }

    window.openScanner = function(mode) {
        scannerMode = mode;
        document.getElementById('scannerTitle.innerText') = mode === 'pos' ? '스แกนบาร์โค้ดขายสินค้า' : 'สแกนบาร์โค้ดรับเข้าสต็อก';
        document.getElementById('scannerModal').classList.remove('hidden');
        document.getElementById('scannerModal').classList.add('flex');
        
        codeReader = new ZXing.BrowserBarcodeReader();
        codeReader.decodeFromVideoDevice(null, 'videoPreview', (result, err) => {
            if (result) {
                const code = result.text;
                closeScanner();
                if (scannerMode === 'pos') {
                    addToCart(code);
                } else {
                    document.getElementById('invBarcode').value = code;
                    checkExistingBarcode(code);
                    switchTab('inventory');
                }
            }
        }).catch(e => console.error(e));
    };

    window.closeScanner = function() {
        if (codeReader) codeReader.reset();
        document.getElementById('scannerModal').classList.add('hidden');
        document.getElementById('scannerModal').classList.remove('flex');
    };

    function showAlert(title, message) {
        document.getElementById('modalTitle').innerText = title;
        document.getElementById('modalMessage').innerText = message;
        const modal = document.getElementById('customModal');
        modal.classList.remove('hidden');
        modal.classList.add('flex');
    }

    window.closeModal = function() {
        const modal = document.getElementById('customModal');
        modal.classList.add('hidden');
        modal.classList.remove('flex');
    };
</script>
</body>
</html>
