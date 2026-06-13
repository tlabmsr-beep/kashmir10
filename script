// 1. الإطراءات الروسية (Compliments)
const compliments = [
    "Ваша улыбка освещает этот день ✨",
    "Вы излучаете невероятную элегантность 🤍",
    "Этот момент тишины создан специально для вас 🌿",
    "Каждая деталь в вас совершенна 💎",
    "Наслаждайтесь каждой секундой, вы этого заслуживаете 🥂",
    "Ваша аура наполняет пространство гармонией ✨"
];

// 2. التحقق من الوقت لتغيير الثيم (النهار/الليل)
function checkTheme() {
    const hour = new Date().getHours();
    const body = document.getElementById('app-body');
    // من 6 مساءً حتى 6 صباحاً ثيم ليلي (زمردي)
    if (hour >= 18 || hour < 6) {
        body.className = 'theme-night';
    } else {
        body.className = 'theme-day';
    }
}
checkTheme();

// 3. نظام الشريط المزاجي وتسليط الضوء (Spotlight Effect)
let currentMood = null;

function toggleMood(mood) {
    // Haptic Feedback إذا دعمه الجهاز
    if (navigator.vibrate) navigator.vibrate(20);

    const cards = document.querySelectorAll('.menu-card');
    const buttons = document.querySelectorAll('.mood-btn');

    // إذا تم الضغط على نفس الزر مرتين (إلغاء الفلتر)
    if (currentMood === mood) {
        currentMood = null;
        cards.forEach(card => {
            card.classList.remove('dimmed', 'spotlight');
        });
        buttons.forEach(btn => btn.classList.remove('active'));
        return;
    }

    currentMood = mood;

    // تفعيل الزر المختار
    buttons.forEach(btn => {
        btn.classList.toggle('active', btn.dataset.target === mood);
    });

    // تطبيق التأثير على الكروت
    cards.forEach(card => {
        if (card.dataset.mood === mood) {
            card.classList.remove('dimmed');
            card.classList.add('spotlight');
        } else {
            card.classList.remove('spotlight');
            card.classList.add('dimmed');
        }
    });
}

// 4. نظام الطلب والحدث الأسطوري (30 ثانية)
function placeOrder(itemName, moodLabel) {
    // 1. Haptic Feedback (نبضتان)
    if (navigator.vibrate) navigator.vibrate([30, 50, 30]);

    // 2. تشغيل صوت ASMR الكريستالي
    const asmr = document.getElementById('asmr-sound');
    asmr.play().catch(e => console.log("Audio play blocked by browser"));

    // 3. إرسال الطلب نظرياً إلى تليجرام (هنا يتم ربط API)
    console.log(`[Telegram Bot] Новый заказ: ${itemName} | Настроение гостьи: ${moodLabel}`);

    // 4. تبديل الشاشات
    document.getElementById('menu-screen').classList.remove('active');
    document.getElementById('mood-bar').classList.add('hidden');
    document.getElementById('wait-screen').classList.add('active');

    generateCompliment();
    startLegendaryTimer();
}

// 5. زر الإطراءات الإضافية
function generateCompliment() {
    const randomIndex = Math.floor(Math.random() * compliments.length);
    const textElement = document.getElementById('compliment-text');
    // تأثير اختفاء وظهور ناعم
    textElement.style.opacity = 0;
    setTimeout(() => {
        textElement.innerText = compliments[randomIndex];
        textElement.style.opacity = 1;
    }, 300);
}

// 6. شريط التقدم (30 ثانية)
function startLegendaryTimer() {
    let timeLeft = 30; // 30 ثانية بالضبط
    const progressBar = document.getElementById('progress');
    const timerText = document.getElementById('timer-text');
    
    progressBar.style.width = '0%';

    const countdown = setInterval(() => {
        timeLeft--;
        const percentage = ((30 - timeLeft) / 30) * 100;
        progressBar.style.width = percentage + '%';
        timerText.innerText = `Осталось: ${timeLeft} сек`;

        if (timeLeft <= 0) {
            clearInterval(countdown);
            finishOrder();
        }
    }, 1000);
}

// 7. انتهاء الوقت وظهور التقييم
function finishOrder() {
    if (navigator.vibrate) navigator.vibrate([100, 50, 100]); // اهتزاز الختام
    document.getElementById('timer-text').classList.add('hidden');
    document.querySelector('.more-compliment-btn').classList.add('hidden');
    document.getElementById('ready-section').classList.remove('hidden');
}

// 8. أزرار إضافية
function callConcierge() {
    if (navigator.vibrate) navigator.vibrate(30);
    alert("Администратор уведомлен и скоро подойдет к вам 🤍");
}

function showRating() {
    alert("Спасибо! Ваш отзыв о Гостеприимстве отправлен руководству напрямую 🤍");
    // العودة للمنيو بعد التقييم
    location.reload(); 
}
