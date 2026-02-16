const romanticIcon = document.getElementById('romantic-icon');
const romanticWords = [
    "I love you", "aridje oumryy", "Forever yours",
    "nmout elik", "roujtyyy nti", "Endless love",
    "raki koulch", "denyaa ta3ii", "My soul loves you",
    "na3che9 fiik"
];

function createRomanticWord() {
    const word = document.createElement('div');
    word.className = 'romantic-word';
    word.textContent = romanticWords[Math.floor(Math.random() * romanticWords.length)];

    
    const maxX = window.innerWidth - 100;
    const maxY = window.innerHeight - 50;
    word.style.left = Math.random() * maxX + 'px';
    word.style.top = Math.random() * maxY + 'px';

    document.body.appendChild(word);

    
    let dx = (Math.random() - 0.5) * 2;
    let dy = (Math.random() - 0.5) * 2;

    function moveWord() {
        const rect = word.getBoundingClientRect();
        let x = rect.left + dx;
        let y = rect.top + dy;

      
        if (x < 0 || x + rect.width > window.innerWidth) dx = -dx;
        if (y < 0 || y + rect.height > window.innerHeight) dy = -dy;

        word.style.left = x + 'px';
        word.style.top = y + 'px';

        requestAnimationFrame(moveWord);
    }
    moveWord();

   
    setTimeout(() => {
        word.remove();
    }, 15000);
}


romanticIcon.addEventListener('click', () => {

    for (let i = 0; i < 5; i++) {
        createRomanticWord();
    }
});
const unlockBtn = document.getElementById('unlock-btn');
const passwordInput = document.getElementById('password-input');
const errorMsg = document.getElementById('error-msg');

unlockBtn.addEventListener('click', () => {
    const password = passwordInput.value;
    if(password === "roujtynhabek") { 
        document.getElementById('site-lock').style.display = 'none';
    } else {
        errorMsg.style.display = 'block';
        passwordInput.value = '';
    }
});
const word = document.getElementById('main-word');

function glowEffect() {
    word.style.textShadow = "0 0 20px #ff0000, 0 0 40px #ff0000, 0 0 60px #ff0000";
    
    setTimeout(() => {
        word.style.textShadow = "0 0 40px #ff0000, 0 0 80px #ff0000, 0 0 120px #ff0000";
    }, 1500);
}

setInterval(glowEffect, 3000);
glowEffect();
const musicBtn = document.getElementById('music-btn');
const myAudio = document.getElementById('myAudio');
const icon = document.getElementById('icon');
let isPlaying = false;

musicBtn.addEventListener('click', function() {
    if (isPlaying) {
        myAudio.pause();
        icon.innerHTML = "🎵";
    } else {
        myAudio.play();
        icon.innerHTML = "⏸️";
    }
    isPlaying = !isPlaying;
});
const openBtn = document.getElementById('open-letter');
const closeBtn = document.getElementById('close-letter');
const overlay = document.getElementById('letter-overlay');

openBtn.addEventListener('click', () => {
    overlay.classList.add('active');
});

closeBtn.addEventListener('click', () => {
    overlay.classList.remove('active');
});

overlay.addEventListener('click', (e) => {
    if (e.target === overlay) {
        overlay.classList.remove('active');
    }
});
const openCamera = document.getElementById('open-camera');
const closeCamera = document.getElementById('close-camera');
const cameraOverlay = document.getElementById('camera-overlay');

openCamera.addEventListener('click', () => {
    cameraOverlay.classList.add('active');
});

closeCamera.addEventListener('click', () => {
    cameraOverlay.classList.remove('active');
});
cameraOverlay.addEventListener('click', (e) => {
    if (e.target === cameraOverlay) {
        cameraOverlay.classList.remove('active');
    }
});
function enableRomanticMode() {
    document.body.classList.add("music-playing");
    word.classList.add("music-playing");
    musicBtn.classList.add("music-playing");
}

function disableRomanticMode() {
    document.body.classList.remove("music-playing");
    word.classList.remove("music-playing");
    musicBtn.classList.remove("music-playing");
}

musicBtn.addEventListener('click', function() {
    if (isPlaying) {
        disableRomanticMode();
    } else {
        enableRomanticMode();
    }
});
// --- تفعيل / إيقاف التفاعل الرومانسي ---
function enableRomanticMode() {
    document.body.classList.add("music-playing");
    word.classList.add("music-playing");
    musicBtn.classList.add("music-playing");
}

function disableRomanticMode() {
    document.body.classList.remove("music-playing");
    word.classList.remove("music-playing");
    musicBtn.classList.remove("music-playing");
}

// تعديل زر الموسيقى ليشمل التفاعل الرومانسي
musicBtn.addEventListener('click', function() {
    if (isPlaying) {
        myAudio.pause();
        icon.innerHTML = "🎵";
        disableRomanticMode();
    } else {
        myAudio.play();
        icon.innerHTML = "⏸️";
        enableRomanticMode();
    }
});
