<!DOCTYPE html>
<html lang="ar" dir="rtl">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>نظام إدارة السعرات المصري</title>
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.4.0/css/all.min.css">
    <style>
        * {
            box-sizing: border-box;
            margin: 0;
            padding: 0;
        }
        body {
            font-family: 'Arial', 'Helvetica', sans-serif;
            background: linear-gradient(135deg, #e0f7fa, #b2ebf2);
            margin: 0;
            padding: 20px;
            transition: background 0.3s ease;
        }
        body.dark-mode {
            background: linear-gradient(135deg, #263238, #455a64);
            color: #eceff1;
        }
        .container {
            max-width: 1600px;
            margin: 0 auto;
            background: #ffffff;
            padding: 30px;
            border-radius: 20px;
            box-shadow: 0 8px 30px rgba(0, 0, 0, 0.1);
            transition: background 0.3s ease, transform 0.3s ease;
        }
        .container:hover {
            transform: translateY(-5px);
        }
        .container.dark-mode {
            background: #37474f;
            box-shadow: 0 8px 30px rgba(255, 255, 255, 0.1);
        }
        .navbar {
            display: flex;
            justify-content: space-between;
            background: #0288d1;
            padding: 15px 30px;
            border-radius: 15px;
            margin-bottom: 20px;
            box-shadow: 0 4px 15px rgba(0, 0, 0, 0.1);
        }
        .nav-item {
            color: white;
            cursor: pointer;
            padding: 10px 20px;
            border-radius: 10px;
            transition: background 0.3s ease, transform 0.3s ease;
        }
        .nav-item:hover {
            background: #0277bd;
            transform: scale(1.05);
        }
        .header {
            text-align: center;
            margin-bottom: 30px;
        }
        .header h1 {
            color: #0277bd;
            font-size: 2.8em;
            text-shadow: 1px 1px 3px rgba(0, 0, 0, 0.1);
        }
        .dark-mode .header h1 {
            color: #4fc3f7;
            text-shadow: 1px 1px 3px rgba(255, 255, 255, 0.1);
        }
        .breadcrumbs {
            font-size: 0.9em;
            color: #0288d1;
            margin-bottom: 20px;
        }
        .dark-mode .breadcrumbs {
            color: #4fc3f7;
        }
        .login-container, .stats, .calculator, .owner-options, .meals {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(250px, 1fr));
            gap: 25px;
            margin-bottom: 40px;
            padding: 20px;
            background: #f5f5f5;
            border-radius: 15px;
            box-shadow: 0 4px 15px rgba(0, 0, 0, 0.05);
            transition: background 0.3s ease;
        }
        .dark-mode .login-container, .dark-mode .stats, .dark-mode .calculator, .dark-mode .owner-options, .dark-mode .meals {
            background: #455a64;
            box-shadow: 0 4px 15px rgba(255, 255, 255, 0.05);
        }
        .login-box, .stat-box, .calc-box, .option-box, .meal-box {
            background: #e1f5fe;
            padding: 20px;
            border-radius: 15px;
            text-align: center;
            box-shadow: 0 3px 12px rgba(0, 0, 0, 0.05);
            transition: transform 0.3s ease, background 0.3s ease;
        }
        .dark-mode .login-box, .dark-mode .stat-box, .dark-mode .calc-box, .dark-mode .option-box, .dark-mode .meal-box {
            background: #546e7a;
        }
        .login-box:hover, .stat-box:hover, .calc-box:hover, .option-box:hover, .meal-box:hover {
            transform: translateY(-5px);
        }
        h3 {
            color: #0277bd;
            margin: 0 0 15px;
            font-size: 1.5em;
        }
        .dark-mode h3 {
            color: #4fc3f7;
        }
        .food-item {
            display: flex;
            flex-wrap: wrap;
            gap: 15px;
            align-items: center;
            margin: 15px 0;
            background: #f5f5f5;
            padding: 15px;
            border-radius: 10px;
            box-shadow: 0 2px 8px rgba(0, 0, 0, 0.03);
            transition: background 0.3s ease, transform 0.3s ease;
        }
        .dark-mode .food-item {
            background: #455a64;
        }
        .food-item:hover {
            transform: scale(1.02);
        }
        .food-item.completed {
            background: #b3e5fc;
        }
        .dark-mode .food-item.completed {
            background: #78909c;
        }
        .checkmark {
            color: #0288d1;
            font-size: 1.8em;
            margin-left: 15px;
        }
        .hidden {
            display: none !important;
            visibility: hidden !important;
            opacity: 0 !important;
        }
        select, button, input {
            padding: 12px 18px;
            border-radius: 10px;
            border: 1px solid #b0bec5;
            background: #ffffff;
            cursor: pointer;
            font-size: 1em;
            transition: all 0.3s ease;
            margin: 5px;
            width: 100%;
        }
        .dark-mode select, .dark-mode button, .dark-mode input {
            background: #607d8b;
            color: #eceff1;
            border: 1px solid #90a4ae;
        }
        button {
            background: #0288d1;
            color: white;
            border: none;
            display: flex;
            align-items: center;
            gap: 8px;
        }
        .dark-mode button {
            background: #4fc3f7;
            color: #263238;
        }
        button:hover {
            background: #0277bd;
            transform: scale(1.05);
        }
        .dark-mode button:hover {
            background: #29b6f6;
        }
        .category {
            margin: 40px 0;
            padding: 25px;
            background: #f5f5f5;
            border-radius: 15px;
            box-shadow: 0 3px 15px rgba(0, 0, 0, 0.05);
        }
        .dark-mode .category {
            background: #455a64;
        }
        h2 {
            color: #0277bd;
            font-size: 2em;
            margin-bottom: 20px;
        }
        .dark-mode h2 {
            color: #4fc3f7;
        }
        .negative {
            color: #ef5350;
        }
        .owner-only, .client-only, #add-client-form, #food-modal, #custom-food-modal {
            display: none;
        }
        .owner-only.active, .client-only.active, #add-client-form.active {
            display: block;
        }
        #client-details, #client-macros {
            margin-top: 20px;
            padding: 20px;
            background: #e1f5fe;
            border-radius: 15px;
        }
        .dark-mode #client-details, .dark-mode #client-macros {
            background: #546e7a;
        }
        .modal {
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            background: rgba(0, 0, 0, 0.5);
            display: flex !important; /* التأكد من إن المودال دايما يكون flex لما يظهر */
            justify-content: center;
            align-items: center;
            z-index: 1000;
            visibility: hidden;
            opacity: 0;
            transition: visibility 0.3s, opacity 0.3s;
        }
        .modal:not(.hidden) {
            visibility: visible;
            opacity: 1;
        }
        .modal-content {
            background: white;
            padding: 20px;
            border-radius: 15px;
            text-align: center;
            width: 350px;
            box-shadow: 0 4px 20px rgba(0, 0, 0, 0.2);
            border: 2px solid #0288d1;
        }
        .dark-mode .modal-content {
            background: #546e7a;
            border: 2px solid #4fc3f7;
        }
        .close-modal {
            float: left;
            font-size: 1.5em;
            cursor: pointer;
            color: #ef5350;
        }
    </style>
</head>
<body>
    <div class="container">
        <nav class="navbar hidden" id="navbar">
            <div class="nav-item" onclick="showSection('owner-meals')">إدارة العملاء</div>
            <div class="nav-item" onclick="showSection('add-client-form')">إضافة عميل</div>
            <div class="nav-item" onclick="toggleTheme()">تغيير الثيم</div>
            <div class="nav-item" onclick="clearDatabase()">حذف قاعدة البيانات</div>
            <div class="nav-item" onclick="logout()">تسجيل الخروج</div>
        </nav>
        <div class="header">
            <h1>نظام إدارة السعرات المصري</h1>
        </div>
        <div class="breadcrumbs hidden" id="breadcrumbs">الرئيسية</div>

        <!-- شاشة تسجيل الدخول -->
        <div class="login-container" id="login-screen">
            <div class="login-box">
                <h3>تسجيل الدخول</h3>
                <select id="user-type">
                    <option value="owner">المالك</option>
                    <option value="client">العميل</option>
                </select>
                <input type="text" id="username" placeholder="اسم المستخدم">
                <input type="password" id="password" placeholder="كلمة المرور">
                <button onclick="login()"><i class="fas fa-sign-in-alt"></i> تسجيل الدخول</button>
            </div>
        </div>

        <!-- واجهة المالك -->
        <div class="owner-only hidden" id="owner-interface">
            <!-- قسم إضافة عميل -->
            <div id="add-client-form" class="hidden">
                <h2>إضافة عميل جديد</h2>
                <input type="text" id="client-username" placeholder="اسم المستخدم للعميل">
                <input type="password" id="client-password" placeholder="كلمة المرور للعميل">
                <input type="number" id="client-age" placeholder="العمر">
                <input type="number" id="client-height" placeholder="الطول (سم)">
                <input type="number" id="client-weight" placeholder="الوزن (كجم)">
                <select id="client-gender">
                    <option value="male">ذكر</option>
                    <option value="female">أنثى</option>
                </select>
                <select id="client-activity">
                    <option value="1.2">قليل النشاط</option>
                    <option value="1.375">خفيف</option>
                    <option value="1.55">متوسط</option>
                    <option value="1.725">نشط</option>
                </select>
                <select id="client-goal">
                    <option value="loss">فقدان الوزن</option>
                    <option value="gain">زيادة الوزن</option>
                    <option value="maintain">المحافظة على الوزن</option>
                </select>
                <input type="number" id="target-calories" placeholder="السعرات المستهدفة (اختياري)">
                <input type="number" id="protein-grams" placeholder="جرام بروتين">
                <input type="number" id="carbs-grams" placeholder="جرام كارب">
                <input type="number" id="fats-grams" placeholder="جرام دهون">
                <input type="number" id="fiber-grams" placeholder="جرام ألياف">
                <input type="number" id="usage-days" placeholder="عدد أيام الاستخدام">
                <button onclick="addClient()"><i class="fas fa-user-plus"></i> حفظ العميل</button>
            </div>

            <!-- قسم إدارة العملاء -->
            <div id="owner-meals" class="hidden">
                <h2>إدارة العملاء والدايت</h2>
                <select id="client-selector" onchange="loadOwnerClientData()">
                    <option value="">اختر عميل</option>
                </select>
                <div id="client-details"></div>
                <div id="client-macros"></div>
                <button onclick="addMeal()"><i class="fas fa-plus"></i> إضافة وجبة</button>
                <button onclick="showCustomFoodForm()"><i class="fas fa-utensils"></i> إضافة طعام مخصص</button>
                <div id="meals-container"></div>
                <button onclick="shareClientLink()"><i class="fas fa-share-alt"></i> مشاركة للعميل</button>
            </div>
        </div>

        <!-- واجهة العميل -->
        <div class="client-only hidden" id="client-interface">
            <div class="stats">
                <div class="stat-box">
                    <h3>السعرات المتبقية</h3>
                    <p id="client-calories">0</p>
                </div>
                <div class="stat-box">
                    <h3>الكارب (جم)</h3>
                    <p id="client-carbs">0</p>
                </div>
                <div class="stat-box">
                    <h3>البروتين (جم)</h3>
                    <p id="client-protein">0</p>
                </div>
                <div class="stat-box">
                    <h3>الدهون (جم)</h3>
                    <p id="client-fats">0</p>
                </div>
                <div class="stat-box">
                    <h3>الألياف (جم)</h3>
                    <p id="client-fiber">0</p>
                </div>
            </div>
            <div id="client-meals" class="meals"></div>
        </div>

        <!-- مودال إضافة طعام من قاعدة البيانات -->
        <div id="food-modal" class="modal hidden">
            <div class="modal-content">
                <span class="close-modal" onclick="closeModal('food-modal')">×</span>
                <h3>إضافة طعام</h3>
                <select id="modal-food-type" onchange="updateModalFoodOptions()">
                    <option value="">اختر نوع الطعام</option>
                    <option value="carbs">كربوهيدرات</option>
                    <option value="protein">بروتين</option>
                    <option value="fats">دهون</option>
                    <option value="custom">مخصص</option>
                </select>
                <select id="modal-food-name">
                    <option value="">اختر الطعام</option>
                </select>
                <button onclick="addFoodFromModal()"><i class="fas fa-plus"></i> إضافة</button>
            </div>
        </div>

        <!-- مودال إضافة طعام مخصص -->
        <div id="custom-food-modal" class="modal hidden">
            <div class="modal-content">
                <span class="close-modal" onclick="closeModal('custom-food-modal')">×</span>
                <h3>إضافة طعام مخصص</h3>
                <input type="text" id="custom-food-name" placeholder="اسم الطعام">
                <input type="number" id="custom-food-calories" placeholder="السعرات">
                <input type="number" id="custom-food-carbs" placeholder="الكارب (جم)">
                <input type="number" id="custom-food-protein" placeholder="البروتين (جم)">
                <input type="number" id="custom-food-fats" placeholder="الدهون (جم)">
                <input type="number" id="custom-food-fiber" placeholder="الألياف (جم)">
                <input type="text" id="custom-food-vitamins" placeholder="الفيتامينات (اختياري)">
                <button onclick="addCustomFoodFromModal()"><i class="fas fa-plus"></i> حفظ الطعام</button>
            </div>
        </div>
    </div>

    <script src="https://cdnjs.cloudflare.com/ajax/libs/jspdf/2.5.1/jspdf.umd.min.js"></script>
    <script>
        const { jsPDF } = window.jspdf;

        // متغيرات عالمية
        let isOwnerLoggedIn = false;
        let currentUserType = null;
        let currentClientId = null;
        let currentMealIndex = null;
        let currentClientIdForModal = null;

        // دالة SHA-256 بسيطة لتشفير كلمة المرور
        function simpleSHA256(str) {
            let hash = 0;
            for (let i = 0; i < str.length; i++) {
                const char = str.charCodeAt(i);
                hash = ((hash << 5) - hash) + char;
                hash = hash & hash;
            }
            return hash.toString(16);
        }

        // بيانات تسجيل الدخول للمالك
        const OWNER_CREDENTIALS = {
            usernameHash: simpleSHA256("admin"),
            passwordHash: simpleSHA256("123456")
        };

        // قاعدة بيانات الأطعمة
        let foodDatabase = JSON.parse(localStorage.getItem('foodDatabase')) || {
            carbs: [
                { name: "أرز", calories: 240, carbs: 54, protein: 6, fat: 1, fiber: 1, vitamins: "B1, B3" },
                { name: "شوفان", calories: 240, carbs: 42, protein: 9, fat: 5, fiber: 6, vitamins: "B1, B5" }
            ],
            protein: [
                { name: "صدور دجاج", calories: 200, carbs: 0, protein: 42, fat: 2, fiber: 0, vitamins: "B3, B6" },
                { name: "سمك", calories: 230, carbs: 0, protein: 36, fat: 8, fiber: 0, vitamins: "D, B12" }
            ],
            fats: [
                { name: "زبدة فول سوداني", calories: 180, carbs: 6, protein: 8, fat: 15, fiber: 2, vitamins: "E, B3" },
                { name: "مكسرات", calories: 200, carbs: 7, protein: 6, fat: 18, fiber: 3, vitamins: "E, B6" }
            ],
            custom: []
        };

        let ownerData = JSON.parse(localStorage.getItem('ownerData')) || { clients: [] };

        // تسجيل الدخول
        function login() {
            try {
                const userType = document.getElementById('user-type').value;
                const username = document.getElementById('username').value;
                const password = document.getElementById('password').value;
                const usernameHash = simpleSHA256(username);
                const passwordHash = simpleSHA256(password);

                // إخفاء كل الواجهات أولاً
                document.getElementById('login-screen').classList.add('hidden');
                document.getElementById('owner-interface').classList.add('hidden');
                document.getElementById('client-interface').classList.add('hidden');
                document.getElementById('navbar').classList.add('hidden');
                document.getElementById('breadcrumbs').classList.add('hidden');

                if (userType === 'owner' && usernameHash === OWNER_CREDENTIALS.usernameHash && passwordHash === OWNER_CREDENTIALS.passwordHash) {
                    isOwnerLoggedIn = true;
                    currentUserType = 'owner';
                    document.getElementById('owner-interface').classList.remove('hidden');
                    document.getElementById('owner-interface').classList.add('active');
                    document.getElementById('navbar').classList.remove('hidden');
                    document.getElementById('breadcrumbs').classList.remove('hidden');
                    showSection('owner-meals');
                    loadClientSelector();
                } else if (userType === 'client') {
                    isOwnerLoggedIn = false;
                    currentUserType = 'client';
                    const client = ownerData.clients.find(c => simpleSHA256(c.username) === usernameHash && c.password === passwordHash);
                    if (client) {
                        currentClientId = client.id;
                        document.getElementById('client-interface').classList.remove('hidden');
                        document.getElementById('client-interface').classList.add('active');
                        document.getElementById('navbar').classList.add('hidden');
                        document.getElementById('breadcrumbs').classList.add('hidden');
                        loadClientData(client); // تحميل بيانات العميل
                    } else {
                        alert('اسم المستخدم أو كلمة المرور غير صحيحة!');
                        document.getElementById('login-screen').classList.remove('hidden');
                    }
                } else {
                    alert('اسم المستخدم أو كلمة المرور غير صحيحة!');
                    document.getElementById('login-screen').classList.remove('hidden');
                }
            } catch (error) {
                console.error('خطأ في تسجيل الدخول:', error);
                alert('حدث خطأ أثناء تسجيل الدخول! تحقق من الكونسول للتفاصيل.');
                document.getElementById('login-screen').classList.remove('hidden');
            }
        }

        // تحميل بيانات العميل في واجهة العميل
        function loadClientData(client) {
            const days = client.days || {};
            let consumedCalories = 0, consumedCarbs = 0, consumedProtein = 0, consumedFats = 0, consumedFiber = 0;
            for (let day in days) {
                consumedCalories += days[day].calories || 0;
                consumedCarbs += days[day].carbs || 0;
                consumedProtein += days[day].protein || 0;
                consumedFats += days[day].fats || 0;
                consumedFiber += days[day].fiber || 0;
            }
            document.getElementById('client-calories').textContent = Math.round(client.targetCalories - consumedCalories);
            document.getElementById('client-carbs').textContent = Math.round(client.carbs - consumedCarbs);
            document.getElementById('client-protein').textContent = Math.round(client.protein - consumedProtein);
            document.getElementById('client-fats').textContent = Math.round(client.fats - consumedFats);
            document.getElementById('client-fiber').textContent = Math.round(client.fiber - consumedFiber);

            // تحميل وجبات العميل
            const mealsContainer = document.getElementById('client-meals');
            mealsContainer.innerHTML = '';
            client.meals.forEach((meal, index) => {
                const mealDiv = document.createElement('div');
                mealDiv.className = 'meal-box';
                mealDiv.innerHTML = `
                    <h3>وجبة ${index + 1} <span class="checkmark ${meal.completed ? '' : 'hidden'}">✔</span></h3>
                    <div id="client-meal-${index}-items"></div>
                    <p>السعرات: ${meal.totalCalories} | الكارب: ${meal.totalCarbs} | البروتين: ${meal.totalProtein} | الدهون: ${meal.totalFats} | الألياف: ${meal.totalFiber}</p>
                    <button onclick="markMealAsEaten(${client.id}, ${index})"><i class="fas fa-check"></i> أكلت الوجبة</button>
                `;
                const itemsContainer = mealDiv.querySelector(`#client-meal-${index}-items`);
                meal.items.forEach((item, itemIndex) => {
                    const itemDiv = document.createElement('div');
                    itemDiv.className = 'food-item';
                    itemDiv.innerHTML = `
                        <span>${item.name} (${item.type})</span>
                        <span>سعرات: ${item.calories} | ماكروز: ${item.carbs}ك, ${item.protein}ب, ${item.fat}د, ${item.fiber}أ | فيتامينات: ${item.vitamins}</span>
                        <span class="checkmark ${item.completed ? '' : 'hidden'}">✔</span>
                    `;
                    itemsContainer.appendChild(itemDiv);
                });
                mealsContainer.appendChild(mealDiv);
            });
        }

        // تسجيل إن العميل أكل الوجبة
        function markMealAsEaten(clientId, mealIndex) {
            const client = ownerData.clients.find(c => c.id === clientId);
            const meal = client.meals[mealIndex];
            if (meal.completed) {
                alert('تم تسجيل هذه الوجبة بالفعل!');
                return;
            }
            meal.completed = true;
            meal.items.forEach(item => item.completed = true);

            // تحديث الماكروز في اليوم الحالي
            const today = new Date().toISOString().split('T')[0];
            if (!client.days) client.days = {};
            if (!client.days[today]) {
                client.days[today] = { calories: 0, carbs: 0, protein: 0, fats: 0, fiber: 0 };
            }
            client.days[today].calories = (client.days[today].calories || 0) + meal.totalCalories;
            client.days[today].carbs = (client.days[today].carbs || 0) + meal.totalCarbs;
            client.days[today].protein = (client.days[today].protein || 0) + meal.totalProtein;
            client.days[today].fats = (client.days[today].fats || 0) + meal.totalFats;
            client.days[today].fiber = (client.days[today].fiber || 0) + meal.totalFiber;

            localStorage.setItem('ownerData', JSON.stringify(ownerData));
            loadClientData(client);
        }

        // تسجيل الخروج
        function logout() {
            isOwnerLoggedIn = false;
            currentUserType = null;
            currentClientId = null;
            document.getElementById('owner-interface').classList.add('hidden');
            document.getElementById('client-interface').classList.add('hidden');
            document.getElementById('navbar').classList.add('hidden');
            document.getElementById('breadcrumbs').classList.add('hidden');
            document.getElementById('food-modal').classList.add('hidden');
            document.getElementById('custom-food-modal').classList.add('hidden');
            document.getElementById('login-screen').classList.remove('hidden');
            document.getElementById('username').value = '';
            document.getElementById('password').value = '';
            document.getElementById('client-details').innerHTML = '';
            document.getElementById('client-macros').innerHTML = '';
            document.getElementById('meals-container').innerHTML = '';
        }

        // حذف قاعدة البيانات
        function clearDatabase() {
            if (confirm('هل أنت متأكد من حذف قاعدة البيانات؟ سيتم حذف كل العملاء والأطعمة المخصصة!')) {
                localStorage.removeItem('ownerData');
                localStorage.removeItem('foodDatabase');
                foodDatabase = {
                    carbs: [
                        { name: "أرز", calories: 240, carbs: 54, protein: 6, fat: 1, fiber: 1, vitamins: "B1, B3" },
                        { name: "شوفان", calories: 240, carbs: 42, protein: 9, fat: 5, fiber: 6, vitamins: "B1, B5" }
                    ],
                    protein: [
                        { name: "صدور دجاج", calories: 200, carbs: 0, protein: 42, fat: 2, fiber: 0, vitamins: "B3, B6" },
                        { name: "سمك", calories: 230, carbs: 0, protein: 36, fat: 8, fiber: 0, vitamins: "D, B12" }
                    ],
                    fats: [
                        { name: "زبدة فول سوداني", calories: 180, carbs: 6, protein: 8, fat: 15, fiber: 2, vitamins: "E, B3" },
                        { name: "مكسرات", calories: 200, carbs: 7, protein: 6, fat: 18, fiber: 3, vitamins: "E, B6" }
                    ],
                    custom: []
                };
                ownerData = { clients: [] };
                localStorage.setItem('foodDatabase', JSON.stringify(foodDatabase));
                localStorage.setItem('ownerData', JSON.stringify(ownerData));
                loadClientSelector();
                document.getElementById('client-details').innerHTML = '';
                document.getElementById('client-macros').innerHTML = '';
                document.getElementById('meals-container').innerHTML = '';
                alert('تم حذف قاعدة البيانات وإعادة إنشائها بنجاح!');
            }
        }

        // تبديل الثيم
        function toggleTheme() {
            if (!currentUserType) {
                alert('يرجى تسجيل الدخول أولاً!');
                return;
            }
            document.body.classList.toggle('dark-mode');
            document.querySelector('.container').classList.toggle('dark-mode');
        }

        // إظهار قسم معين في واجهة المالك
        function showSection(sectionId) {
            if (!isOwnerLoggedIn) {
                alert('يرجى تسجيل الدخول كمالك أولاً!');
                return;
            }
            document.querySelectorAll('#owner-interface > div').forEach(div => {
                div.classList.remove('active');
                div.classList.add('hidden');
            });
            const section = document.getElementById(sectionId);
            if (section) {
                section.classList.remove('hidden');
                section.classList.add('active');
                document.getElementById('breadcrumbs').textContent = sectionId === 'owner-meals' ? 'الرئيسية > إدارة العملاء' : 'الرئيسية > إضافة عميل';
            } else {
                console.error(`القسم ${sectionId} غير موجود!`);
            }
        }

        // حساب BMR
        function calculateBMR(weight, height, age, gender) {
            return gender === 'male' ?
                10 * weight + 6.25 * height - 5 * age + 5 :
                10 * weight + 6.25 * height - 5 * age - 161;
        }

        // إضافة عميل
        function addClient() {
            if (!isOwnerLoggedIn) {
                alert('يرجى تسجيل الدخول كمالك أولاً!');
                return;
            }
            const username = document.getElementById('client-username').value;
            const password = document.getElementById('client-password').value;
            if (!username || !password) {
                alert('يرجى إدخال اسم المستخدم وكلمة المرور للعميل!');
                return;
            }
            const weight = parseFloat(document.getElementById('client-weight').value) || 70;
            const height = parseFloat(document.getElementById('client-height').value) || 170;
            const age = parseFloat(document.getElementById('client-age').value) || 30;
            const gender = document.getElementById('client-gender').value;
            const activity = parseFloat(document.getElementById('client-activity').value);
            const bmr = calculateBMR(weight, height, age, gender);
            const maintainCalories = Math.round(bmr * activity);

            const client = {
                id: Date.now(),
                username: username,
                password: simpleSHA256(password),
                age,
                height,
                weight,
                gender,
                activity,
                maintainCalories,
                goal: document.getElementById('client-goal').value,
                targetCalories: parseFloat(document.getElementById('target-calories').value) || (document.getElementById('client-goal').value === 'loss' ? maintainCalories - 500 : document.getElementById('client-goal').value === 'gain' ? maintainCalories + 500 : maintainCalories),
                protein: parseFloat(document.getElementById('protein-grams').value) || 0,
                carbs: parseFloat(document.getElementById('carbs-grams').value) || 0,
                fats: parseFloat(document.getElementById('fats-grams').value) || 0,
                fiber: parseFloat(document.getElementById('fiber-grams').value) || 0,
                usageDays: parseFloat(document.getElementById('usage-days').value) || 30,
                startDate: new Date().toISOString().split('T')[0],
                meals: [],
                days: {}
            };

            if (ownerData.clients.some(c => c.username === client.username)) {
                alert('اسم المستخدم موجود بالفعل! اختر اسم مستخدم آخر.');
                return;
            }

            ownerData.clients.push(client);
            localStorage.setItem('ownerData', JSON.stringify(ownerData));
            alert(`تم إضافة العميل ${client.username} بنجاح!`);
            showSection('owner-meals');
            loadClientSelector();
        }

        // تحميل قائمة العملاء في selector
        function loadClientSelector() {
            if (!isOwnerLoggedIn) return;
            const selector = document.getElementById('client-selector');
            if (selector) {
                selector.innerHTML = '<option value="">اختر عميل</option>';
                ownerData.clients.forEach(client => {
                    selector.innerHTML += `<option value="${client.id}">${client.username}</option>`;
                });
            } else {
                console.error('عنصر client-selector غير موجود!');
            }
        }

        // تحميل بيانات العميل في واجهة المالك
        function loadOwnerClientData() {
            if (!isOwnerLoggedIn) {
                alert('يرجى تسجيل الدخول كمالك أولاً!');
                return;
            }
            const clientId = parseInt(document.getElementById('client-selector').value);
            if (!clientId) {
                document.getElementById('client-details').innerHTML = '';
                document.getElementById('client-macros').innerHTML = '';
                document.getElementById('meals-container').innerHTML = '';
                document.getElementById('breadcrumbs').textContent = 'الرئيسية > إدارة العملاء';
                return;
            }
            const client = ownerData.clients.find(c => c.id === clientId);
            document.getElementById('breadcrumbs').textContent = `الرئيسية > إدارة العملاء > ${client.username}`;
            document.getElementById('client-details').innerHTML = `
                <h3>بيانات العميل: ${client.username}</h3>
                <p>العمر: ${client.age} سنة</p>
                <p>الطول: ${client.height} سم</p>
                <p>الوزن: ${client.weight} كجم</p>
                <p>الجنس: ${client.gender === 'male' ? 'ذكر' : 'أنثى'}</p>
                <p>مستوى النشاط: ${client.activity}</p>
                <p>سعرات الثبات: ${client.maintainCalories}</p>
                <p>الهدف: ${client.goal === 'loss' ? 'فقدان الوزن' : client.goal === 'gain' ? 'زيادة الوزن' : 'المحافظة على الوزن'}</p>
            `;

            const days = client.days || {};
            let consumedCalories = 0, consumedCarbs = 0, consumedProtein = 0, consumedFats = 0, consumedFiber = 0;
            for (let day in days) {
                consumedCalories += days[day].calories || 0;
                consumedCarbs += days[day].carbs || 0;
                consumedProtein += days[day].protein || 0;
                consumedFats += days[day].fats || 0;
                consumedFiber += days[day].fiber || 0;
            }
            document.getElementById('client-macros').innerHTML = `
                <h3>الماكروز</h3>
                <p>السعرات المستهدفة: ${client.targetCalories} | المتبقية: ${Math.round(client.targetCalories - consumedCalories)}</p>
                <p>الكارب المستهدف: ${client.carbs} جم | المتبقي: ${Math.round(client.carbs - consumedCarbs)}</p>
                <p>البروتين المستهدف: ${client.protein} جم | المتبقي: ${Math.round(client.protein - consumedProtein)}</p>
                <p>الدهون المستهدفة: ${client.fats} جم | المتبقية: ${Math.round(client.fats - consumedFats)}</p>
                <p>الألياف المستهدفة: ${client.fiber} جم | المتبقية: ${Math.round(client.fiber - consumedFiber)}</p>
                <p>مدة الاستخدام: ${client.usageDays} يوم</p>
            `;
            loadOwnerMeals(clientId);
        }

        // تحميل وجبات العميل في واجهة المالك
        function loadOwnerMeals(clientId) {
            if (!isOwnerLoggedIn) return;
            const client = ownerData.clients.find(c => c.id === clientId);
            const container = document.getElementById('meals-container');
            container.innerHTML = '';
            client.meals.forEach((meal, index) => {
                const mealDiv = createMealDiv(meal, index, clientId);
                container.appendChild(mealDiv);
            });
        }

        // إضافة وجبة جديدة
        function addMeal() {
            console.log("تم الضغط على زر إضافة وجبة");
            if (!isOwnerLoggedIn) {
                alert('يرجى تسجيل الدخول كمالك أولاً!');
                return;
            }
            const clientId = parseInt(document.getElementById('client-selector').value);
            if (!clientId) {
                alert('يرجى اختيار عميل أولاً!');
                return;
            }
            const client = ownerData.clients.find(c => c.id === clientId);
            const meal = { items: [], completed: false, totalCalories: 0, totalCarbs: 0, totalProtein: 0, totalFats: 0, totalFiber: 0 };
            client.meals.push(meal);
            localStorage.setItem('ownerData', JSON.stringify(ownerData));
            console.log("تم إضافة وجبة جديدة للعميل:", clientId);
            loadOwnerMeals(clientId);
        }

        // إظهار نموذج إضافة طعام مخصص
        function showCustomFoodForm() {
            console.log("تم الضغط على زر إضافة طعام مخصص");
            if (!isOwnerLoggedIn) {
                alert('يرجى تسجيل الدخول كمالك أولاً!');
                return;
            }
            const modal = document.getElementById('custom-food-modal');
            if (modal) {
                modal.classList.remove('hidden');
                console.log("تم فتح المودال بنجاح");
            } else {
                console.error("المودال custom-food-modal غير موجود!");
            }
        }

        // إضافة طعام مخصص من المودال
        function addCustomFoodFromModal() {
            console.log("تم الضغط على زر حفظ الطعام في المودال");
            if (!isOwnerLoggedIn) {
                alert('يرجى تسجيل الدخول كمالك أولاً!');
                return;
            }
            const name = document.getElementById('custom-food-name').value.trim();
            const calories = parseFloat(document.getElementById('custom-food-calories').value) || 0;
            const carbs = parseFloat(document.getElementById('custom-food-carbs').value) || 0;
            const protein = parseFloat(document.getElementById('custom-food-protein').value) || 0;
            const fat = parseFloat(document.getElementById('custom-food-fats').value) || 0;
            const fiber = parseFloat(document.getElementById('custom-food-fiber').value) || 0;
            const vitamins = document.getElementById('custom-food-vitamins').value.trim() || "غير محدد";

            console.log("البيانات المدخلة:", { name, calories, carbs, protein, fat, fiber, vitamins });

            if (!name) {
                alert('يرجى إدخال اسم الطعام!');
                return;
            }

            const newFood = { name, calories, carbs, protein, fat, fiber, vitamins };
            foodDatabase.custom.push(newFood);
            localStorage.setItem('foodDatabase', JSON.stringify(foodDatabase));
            console.log("تم حفظ الطعام في قاعدة البيانات:", foodDatabase.custom);

            alert(`تم إضافة ${name} إلى قاعدة البيانات!`);

            // إعادة تعيين الحقول
            document.getElementById('custom-food-name').value = '';
            document.getElementById('custom-food-calories').value = '';
            document.getElementById('custom-food-carbs').value = '';
            document.getElementById('custom-food-protein').value = '';
            document.getElementById('custom-food-fats').value = '';
            document.getElementById('custom-food-fiber').value = '';
            document.getElementById('custom-food-vitamins').value = '';

            closeModal('custom-food-modal');
        }

        // إنشاء div للوجبة
        function createMealDiv(meal, mealIndex, clientId) {
            const div = document.createElement('div');
            div.className = 'meal-box';
            div.innerHTML = `
                <h3>وجبة ${mealIndex + 1} <span class="checkmark ${meal.completed ? '' : 'hidden'}">✔</span></h3>
                <button onclick="showAddFoodForm(${mealIndex}, ${clientId})"><i class="fas fa-plus"></i> إضافة طعام</button>
                <div id="meal-${mealIndex}-items"></div>
                <p>السعرات: ${meal.totalCalories} | الكارب: ${meal.totalCarbs} | البروتين: ${meal.totalProtein} | الدهون: ${meal.totalFats} | الألياف: ${meal.totalFiber}</p>
            `;
            const itemsContainer = div.querySelector(`#meal-${mealIndex}-items`);
            meal.items.forEach((item, itemIndex) => {
                const itemDiv = document.createElement('div');
                itemDiv.className = 'food-item';
                itemDiv.innerHTML = `
                    <span>${item.name} (${item.type})</span>
                    <span>سعرات: ${item.calories} | ماكروز: ${item.carbs}ك, ${item.protein}ب, ${item.fat}د, ${item.fiber}أ | فيتامينات: ${item.vitamins}</span>
                    <span class="checkmark ${item.completed ? '' : 'hidden'}">✔</span>
                    <select onchange="replaceFood(${mealIndex}, ${itemIndex}, this.value, ${clientId})">
                        <option value="">بدائل</option>
                        ${Object.values(foodDatabase).flat().map(food => `<option value="${food.name}">${food.name}</option>`).join('')}
                    </select>
                `;
                itemsContainer.appendChild(itemDiv);
            });
            return div;
        }

        // إظهار نموذج إضافة طعام
        function showAddFoodForm(mealIndex, clientId) {
            console.log("تم الضغط على زر إضافة طعام", { mealIndex, clientId });
            if (!isOwnerLoggedIn) {
                alert('يرجى تسجيل الدخول كمالك أولاً!');
                return;
            }
            const selectedClientId = parseInt(document.getElementById('client-selector').value);
            if (!selectedClientId) {
                alert('يرجى اختيار عميل أولاً!');
                return;
            }
            currentMealIndex = mealIndex;
            currentClientIdForModal = clientId;
            const modal = document.getElementById('food-modal');
            if (modal) {
                modal.classList.remove('hidden');
                console.log("تم فتح مودال إضافة طعام بنجاح");
                console.log("حالة المودال بعد إزالة hidden:", modal.classList);
            } else {
                console.error("المودال food-modal غير موجود!");
            }
            updateModalFoodOptions();
        }

        // إغلاق المودال
        function closeModal(modalId) {
            console.log("تم إغلاق المودال:", modalId);
            const modal = document.getElementById(modalId);
            if (modal) {
                modal.classList.add('hidden');
                console.log("حالة المودال بعد إضافة hidden:", modal.classList);
            }
        }

        // تحديث خيارات الطعام في المودال
        function updateModalFoodOptions() {
            const type = document.getElementById('modal-food-type').value;
            const foodSelect = document.getElementById('modal-food-name');
            if (!foodSelect) {
                console.error("عنصر modal-food-name غير موجود!");
                return;
            }
            foodSelect.innerHTML = '<option value="">اختر الطعام</option>';
            if (type && foodDatabase[type]) {
                foodDatabase[type].forEach(food => {
                    foodSelect.innerHTML += `<option value="${food.name}">${food.name}</option>`;
                });
            }
            console.log("تم تحديث خيارات الطعام في المودال:", type);
        }

        // إضافة طعام من المودال
        function addFoodFromModal() {
            console.log("تم الضغط على زر إضافة طعام من المودال");
            if (!isOwnerLoggedIn) {
                alert('يرجى تسجيل الدخول كمالك أولاً!');
                return;
            }
            const type = document.getElementById('modal-food-type').value;
            const foodName = document.getElementById('modal-food-name').value;
            console.log("البيانات المختارة:", { type, foodName });
            if (!type || !foodName) {
                alert('يرجى اختيار نوع الطعام والطعام!');
                return;
            }
            const food = Object.values(foodDatabase).flat().find(f => f.name === foodName);
            if (food) {
                const client = ownerData.clients.find(c => c.id === currentClientIdForModal);
                if (!client) {
                    console.error("العميل غير موجود:", currentClientIdForModal);
                    return;
                }
                const meal = client.meals[currentMealIndex];
                if (!meal) {
                    console.error("الوجبة غير موجودة:", currentMealIndex);
                    return;
                }
                meal.items.push({ ...food, type, completed: false });
                updateMealTotals(meal);
                localStorage.setItem('ownerData', JSON.stringify(ownerData));
                console.log("تم إضافة الطعام للوجبة:", food);
                console.log("الوجبة بعد الإضافة:", meal);
                loadOwnerMeals(currentClientIdForModal);
                closeModal('food-modal');
            } else {
                alert('يرجى اختيار طعام!');
            }
        }

        // استبدال طعام
        function replaceFood(mealIndex, itemIndex, newFoodName, clientId) {
            if (!isOwnerLoggedIn) return;
            const client = ownerData.clients.find(c => c.id === clientId);
            const meal = client.meals[mealIndex];
            const oldItem = meal.items[itemIndex];
            const newFood = Object.values(foodDatabase).flat().find(f => f.name === newFoodName);
            if (newFood) {
                meal.items[itemIndex] = { ...newFood, type: oldItem.type, completed: false };
                updateMealTotals(meal);
                localStorage.setItem('ownerData', JSON.stringify(ownerData));
                loadOwnerMeals(clientId);
            }
        }

        // تحديث إجمالي الماكروز للوجبة
        function updateMealTotals(meal) {
            meal.totalCalories = meal.items.reduce((sum, item) => sum + (item.calories || 0), 0);
            meal.totalCarbs = meal.items.reduce((sum, item) => sum + (item.carbs || 0), 0);
            meal.totalProtein = meal.items.reduce((sum, item) => sum + (item.protein || 0), 0);
            meal.totalFats = meal.items.reduce((sum, item) => sum + (item.fat || 0), 0);
            meal.totalFiber = meal.items.reduce((sum, item) => sum + (item.fiber || 0), 0);
            meal.completed = meal.items.every(item => item.completed);
        }

        // مشاركة رابط العميل
        function shareClientLink() {
            if (!isOwnerLoggedIn) {
                alert('يرجى تسجيل الدخول كمالك أولاً!');
                return;
            }
            const clientId = parseInt(document.getElementById('client-selector').value);
            const client = ownerData.clients.find(c => c.id === clientId);
            const link = `${window.location.href}?client=${client.id}&username=${client.username}`;
            alert(`رابط العميل: ${link}`);
        }
    </script>
</body>
</html>
