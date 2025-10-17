<!DOCTYPE html>
<html lang="fa" dir="rtl">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>🔥 برنامه‌ریز درسی هوشمند</title>
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.4.0/css/all.min.css">
    <style>
        /* متغیرها و تنظیمات اولیه */
        :root {
            --primary: #6366f1;
            --primary-dark: #4f46e5;
            --secondary: #10b981;
            --danger: #ef4444;
            --warning: #f59e0b;
            --info: #3b82f6;
            --dark: #1e272e;
            --light: #f9fafb;
            --gray: #6b7280;
            --card-bg: #2d3436;
            --text-light: #e2e8f0;
            --shadow: 0 10px 25px rgba(0, 0, 0, 0.3);
            --radius: 12px;
            --transition: all 0.3s ease;
        }

        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
            font-family: 'Vazirmatn', 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
        }

        body {
            background: linear-gradient(135deg, #1e3c72 0%, #2a5298 100%);
            color: var(--text-light);
            min-height: 100vh;
            line-height: 1.6;
        }

        .container {
            max-width: 1400px;
            margin: 0 auto;
            padding: 20px;
        }

        /* هدر */
        header {
            background: rgba(45, 52, 54, 0.9);
            backdrop-filter: blur(10px);
            border-radius: var(--radius);
            padding: 20px;
            margin-bottom: 25px;
            box-shadow: var(--shadow);
            text-align: center;
        }

        .logo {
            display: flex;
            align-items: center;
            justify-content: center;
            gap: 15px;
            margin-bottom: 10px;
        }

        .logo i {
            font-size: 2.5rem;
            color: #ffd32a;
        }

        .logo h1 {
            font-size: 1.8rem;
            color: white;
        }

        .date-display {
            font-size: 1.1rem;
            color: var(--text-light);
        }

        /* منو */
        .main-menu {
            display: flex;
            justify-content: center;
            gap: 15px;
            margin-bottom: 25px;
            flex-wrap: wrap;
        }

        .menu-btn {
            background: var(--primary);
            color: white;
            border: none;
            padding: 12px 25px;
            border-radius: 30px;
            cursor: pointer;
            transition: var(--transition);
            font-size: 1rem;
            display: flex;
            align-items: center;
            gap: 8px;
        }

        .menu-btn:hover {
            background: var(--primary-dark);
            transform: translateY(-2px);
        }

        /* محتوای اصلی */
        .main-content {
            display: grid;
            grid-template-columns: 1fr 400px;
            gap: 25px;
        }

        /* کارت‌ها */
        .card {
            background: var(--card-bg);
            border-radius: var(--radius);
            padding: 25px;
            box-shadow: var(--shadow);
            margin-bottom: 25px;
            transition: var(--transition);
            border: 1px solid rgba(255, 255, 255, 0.1);
        }

        .card:hover {
            transform: translateY(-5px);
            box-shadow: 0 15px 30px rgba(0, 0, 0, 0.4);
        }

        .card-header {
            display: flex;
            justify-content: space-between;
            align-items: center;
            margin-bottom: 20px;
            padding-bottom: 15px;
            border-bottom: 1px solid rgba(255, 255, 255, 0.1);
        }

        .card-title {
            font-size: 1.3rem;
            font-weight: 700;
            color: #ffd32a;
            display: flex;
            align-items: center;
            gap: 10px;
        }

        /* برنامه روزانه */
        .date-info {
            display: flex;
            justify-content: space-between;
            background: rgba(255, 255, 255, 0.1);
            padding: 15px;
            border-radius: var(--radius);
            margin-bottom: 20px;
        }

        .today, .tomorrow {
            text-align: center;
        }

        .today .date {
            color: #ffd32a;
            font-weight: bold;
        }

        .tasks-container {
            min-height: 200px;
        }

        .task-item {
            background: rgba(255, 255, 255, 0.1);
            padding: 15px;
            border-radius: 8px;
            margin-bottom: 10px;
            display: flex;
            align-items: center;
            gap: 15px;
            transition: var(--transition);
        }

        .task-item:hover {
            background: rgba(255, 255, 255, 0.15);
        }

        .task-checkbox {
            width: 20px;
            height: 20px;
            border-radius: 50%;
            border: 2px solid #ffd32a;
            cursor: pointer;
            display: flex;
            align-items: center;
            justify-content: center;
            transition: var(--transition);
        }

        .task-checkbox.checked {
            background: #ffd32a;
        }

        .task-checkbox.checked::after {
            content: "✓";
            color: var(--dark);
            font-weight: bold;
            font-size: 12px;
        }

        .task-text {
            flex: 1;
        }

        .task-text.completed {
            text-decoration: line-through;
            opacity: 0.7;
        }

        /* تایمر */
        .timer-container {
            text-align: center;
        }

        .timer-circle {
            width: 200px;
            height: 200px;
            border-radius: 50%;
            background: conic-gradient(#ffd32a 0%, #34495e 0%);
            margin: 0 auto 20px;
            display: flex;
            align-items: center;
            justify-content: center;
            position: relative;
            box-shadow: 0 0 30px rgba(255, 211, 42, 0.3);
        }

        .timer-display {
            font-size: 2.5rem;
            font-weight: bold;
            color: #ffd32a;
        }

        .timer-controls {
            display: flex;
            justify-content: center;
            gap: 10px;
            margin-bottom: 20px;
        }

        .timer-btn {
            padding: 10px 20px;
            border: none;
            border-radius: 25px;
            cursor: pointer;
            transition: var(--transition);
            font-size: 1rem;
            display: flex;
            align-items: center;
            gap: 5px;
        }

        .timer-btn.start {
            background: var(--secondary);
            color: white;
        }

        .timer-btn.stop {
            background: var(--danger);
            color: white;
        }

        .timer-btn.reset {
            background: var(--warning);
            color: white;
        }

        .timer-btn:hover {
            transform: scale(1.05);
        }

        .timer-settings {
            display: flex;
            justify-content: center;
            align-items: center;
            gap: 10px;
            margin-top: 15px;
        }

        .timer-select {
            padding: 8px 12px;
            border-radius: 8px;
            border: 1px solid rgba(255, 255, 255, 0.2);
            background: rgba(255, 255, 255, 0.1);
            color: white;
        }

        /* برنامه مدرسه */
        .schedule-display {
            background: rgba(255, 255, 255, 0.05);
            padding: 15px;
            border-radius: var(--radius);
            max-height: 300px;
            overflow-y: auto;
        }

        .day-schedule {
            margin-bottom: 15px;
        }

        .day-title {
            color: #ffd32a;
            margin-bottom: 8px;
            font-weight: bold;
        }

        .session-item {
            padding: 5px 0;
            margin-left: 15px;
        }

        /* مودال */
        .modal {
            display: none;
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            background: rgba(0, 0, 0, 0.8);
            z-index: 1000;
            backdrop-filter: blur(5px);
        }

        .modal-content {
            position: absolute;
            top: 50%;
            left: 50%;
            transform: translate(-50%, -50%);
            background: var(--card-bg);
            padding: 30px;
            border-radius: var(--radius);
            width: 90%;
            max-width: 600px;
            max-height: 80vh;
            overflow-y: auto;
        }

        .modal-header {
            display: flex;
            justify-content: space-between;
            align-items: center;
            margin-bottom: 20px;
        }

        .close-btn {
            background: none;
            border: none;
            color: white;
            font-size: 1.5rem;
            cursor: pointer;
        }

        /* فرم‌ها */
        .input-group {
            margin-bottom: 15px;
        }

        .input-group label {
            display: block;
            margin-bottom: 5px;
            color: #ffd32a;
        }

        .input-group input,
        .input-group select {
            width: 100%;
            padding: 12px;
            border-radius: 8px;
            border: 1px solid rgba(255, 255, 255, 0.2);
            background: rgba(255, 255, 255, 0.1);
            color: white;
            font-size: 1rem;
        }

        .form-actions {
            display: flex;
            gap: 10px;
            margin-top: 20px;
        }

        .btn {
            padding: 12px 25px;
            border: none;
            border-radius: 8px;
            cursor: pointer;
            transition: var(--transition);
            font-size: 1rem;
        }

        .btn-primary {
            background: var(--primary);
            color: white;
        }

        .btn-success {
            background: var(--secondary);
            color: white;
        }

        .btn-danger {
            background: var(--danger);
            color: white;
        }

        .btn:hover {
            transform: translateY(-2px);
        }

        /* لیست‌ها */
        .list-container {
            max-height: 300px;
            overflow-y: auto;
            background: rgba(255, 255, 255, 0.05);
            border-radius: var(--radius);
            padding: 15px;
        }

        .list-item {
            padding: 12px;
            border-bottom: 1px solid rgba(255, 255, 255, 0.1);
            display: flex;
            justify-content: space-between;
            align-items: center;
        }

        .list-item:last-child {
            border-bottom: none;
        }

        .delete-btn {
            background: var(--danger);
            color: white;
            border: none;
            padding: 5px 10px;
            border-radius: 5px;
            cursor: pointer;
            font-size: 0.8rem;
        }

        /* آمار */
        .stats {
            display: grid;
            grid-template-columns: 1fr 1fr;
            gap: 15px;
            margin-top: 20px;
        }

        .stat-card {
            background: rgba(255, 255, 255, 0.1);
            padding: 15px;
            border-radius: var(--radius);
            text-align: center;
        }

        .stat-value {
            font-size: 1.5rem;
            font-weight: bold;
            color: #ffd32a;
        }

        /* رسپانسیو */
        @media (max-width: 1024px) {
            .main-content {
                grid-template-columns: 1fr;
            }
        }

        @media (max-width: 768px) {
            .main-menu {
                flex-direction: column;
                align-items: center;
            }
            
            .menu-btn {
                width: 100%;
                max-width: 300px;
                justify-content: center;
            }
            
            .date-info {
                flex-direction: column;
                gap: 15px;
            }
            
            .timer-controls {
                flex-wrap: wrap;
            }
            
            .stats {
                grid-template-columns: 1fr;
            }
        }
    </style>
</head>
<body>
    <div class="container">
        <!-- هدر -->
        <header>
            <div class="logo">
                <i class="fas fa-graduation-cap"></i>
                <h1>🔥 برنامه‌ریز درسی هوشمند</h1>
            </div>
            <div class="date-display" id="currentDate">
                <!-- تاریخ اینجا نمایش داده می‌شود -->
            </div>
        </header>

        <!-- منوی اصلی -->
        <div class="main-menu">
            <button class="menu-btn" onclick="showModal('subjectsModal')">
                <i class="fas fa-book"></i> مدیریت دروس
            </button>
            <button class="menu-btn" onclick="showModal('scheduleModal')">
                <i class="fas fa-calendar-alt"></i> برنامه هفتگی
            </button>
            <button class="menu-btn" onclick="showModal('examsModal')">
                <i class="fas fa-file-alt"></i> مدیریت امتحانات
            </button>
            <button class="menu-btn" onclick="generateSmartPlan()">
                <i class="fas fa-magic"></i> تولید برنامه هوشمند
            </button>
        </div>

        <!-- محتوای اصلی -->
        <div class="main-content">
            <!-- سمت چپ - برنامه روزانه -->
            <div class="left-column">
                <!-- برنامه امروز -->
                <div class="card">
                    <div class="card-header">
                        <h2 class="card-title">
                            <i class="fas fa-tasks"></i> برنامه امروز
                        </h2>
                    </div>
                    <div class="date-info">
                        <div class="today">
                            <div class="date" id="todayDate">امروز</div>
                            <div class="day" id="todayDay">شنبه</div>
                        </div>
                        <div class="tomorrow">
                            <div class="date" id="tomorrowDate">فردا</div>
                            <div class="day" id="tomorrowDay">یکشنبه</div>
                        </div>
                    </div>
                    <div class="tasks-container" id="todayTasks">
                        <!-- برنامه امروز اینجا نمایش داده می‌شود -->
                    </div>
                </div>

                <!-- برنامه فردا -->
                <div class="card">
                    <div class="card-header">
                        <h2 class="card-title">
                            <i class="fas fa-eye"></i> پیش‌خوانی فردا
                        </h2>
                    </div>
                    <div class="tasks-container" id="tomorrowTasks">
                        <!-- برنامه فردا اینجا نمایش داده می‌شود -->
                    </div>
                </div>
            </div>

            <!-- سمت راست - تایمر و اطلاعات -->
            <div class="right-column">
                <!-- تایمر -->
                <div class="card">
                    <div class="card-header">
                        <h2 class="card-title">
                            <i class="fas fa-clock"></i> تایمر مطالعه
                        </h2>
                    </div>
                    <div class="timer-container">
                        <div class="timer-circle" id="timerCircle">
                            <div class="timer-display" id="timerDisplay">25:00</div>
                        </div>
                        <div class="timer-controls">
                            <button class="timer-btn start" onclick="startTimer()">
                                <i class="fas fa-play"></i> شروع
                            </button>
                            <button class="timer-btn stop" onclick="stopTimer()">
                                <i class="fas fa-pause"></i> توقف
                            </button>
                            <button class="timer-btn reset" onclick="resetTimer()">
                                <i class="fas fa-redo"></i> ریست
                            </button>
                        </div>
                        <div class="timer-settings">
                            <select class="timer-select" id="timerMinutes" onchange="setTimer()">
                                <option value="25">25 دقیقه</option>
                                <option value="30">30 دقیقه</option>
                                <option value="45">45 دقیقه</option>
                                <option value="60">60 دقیقه</option>
                            </select>
                            <button class="btn btn-primary" onclick="setTimer()">
                                <i class="fas fa-cog"></i> تنظیم
                            </button>
                        </div>
                    </div>
                </div>

                <!-- اطلاعات مدرسه -->
                <div class="card">
                    <div class="card-header">
                        <h2 class="card-title">
                            <i class="fas fa-school"></i> برنامه مدرسه
                        </h2>
                    </div>
                    <div class="schedule-display" id="schoolSchedule">
                        <!-- برنامه مدرسه اینجا نمایش داده می‌شود -->
                    </div>
                </div>

                <!-- آمار -->
                <div class="card">
                    <div class="card-header">
                        <h2 class="card-title">
                            <i class="fas fa-chart-bar"></i> آمار
                        </h2>
                    </div>
                    <div class="stats">
                        <div class="stat-card">
                            <div class="stat-value" id="subjectsCount">0</div>
                            <div>درس</div>
                        </div>
                        <div class="stat-card">
                            <div class="stat-value" id="examsCount">0</div>
                            <div>امتحان</div>
                        </div>
                        <div class="stat-card">
                            <div class="stat-value" id="studyTime">0</div>
                            <div>دقیقه مطالعه</div>
                        </div>
                        <div class="stat-card">
                            <div class="stat-value" id="completedTasks">0</div>
                            <div>تکمیل شده</div>
                        </div>
                    </div>
                </div>
            </div>
        </div>
    </div>

    <!-- مودال مدیریت دروس -->
    <div id="subjectsModal" class="modal">
        <div class="modal-content">
            <div class="modal-header">
                <h2 class="card-title">
                    <i class="fas fa-book"></i> مدیریت دروس
                </h2>
                <button class="close-btn" onclick="closeModal('subjectsModal')">&times;</button>
            </div>
            <div class="input-group">
                <label for="newSubject">نام درس جدید:</label>
                <input type="text" id="newSubject" placeholder="مثال: ریاضی" onkeypress="handleSubjectKeyPress(event)">
            </div>
            <div class="form-actions">
                <button class="btn btn-success" onclick="addSubject()">
                    <i class="fas fa-plus"></i> افزودن درس
                </button>
            </div>
            <div class="list-container" id="subjectsList">
                <!-- لیست دروس اینجا نمایش داده می‌شود -->
            </div>
        </div>
    </div>

    <!-- مودال برنامه هفتگی -->
    <div id="scheduleModal" class="modal">
        <div class="modal-content">
            <div class="modal-header">
                <h2 class="card-title">
                    <i class="fas fa-calendar-alt"></i> برنامه هفتگی مدرسه
                </h2>
                <button class="close-btn" onclick="closeModal('scheduleModal')">&times;</button>
            </div>
            <div id="weeklyScheduleForm">
                <!-- فرم برنامه هفتگی اینجا نمایش داده می‌شود -->
            </div>
            <div class="form-actions">
                <button class="btn btn-success" onclick="saveWeeklySchedule()">
                    <i class="fas fa-save"></i> ذخیره برنامه
                </button>
            </div>
        </div>
    </div>

    <!-- مودال مدیریت امتحانات -->
    <div id="examsModal" class="modal">
        <div class="modal-content">
            <div class="modal-header">
                <h2 class="card-title">
                    <i class="fas fa-file-alt"></i> مدیریت امتحانات
                </h2>
                <button class="close-btn" onclick="closeModal('examsModal')">&times;</button>
            </div>
            <div class="input-group">
                <label for="examSubject">درس:</label>
                <select id="examSubject">
                    <!-- دروس اینجا لود می‌شوند -->
                </select>
            </div>
            <div class="input-group">
                <label for="examDate">تاریخ امتحان:</label>
                <input type="date" id="examDate">
            </div>
            <div class="form-actions">
                <button class="btn btn-success" onclick="addExam()">
                    <i class="fas fa-plus"></i> افزودن امتحان
                </button>
            </div>
            <div class="list-container" id="examsList">
                <!-- لیست امتحانات اینجا نمایش داده می‌شود -->
            </div>
        </div>
    </div>

    <script>
        // داده‌های برنامه
        let appData = {
            subjects: [],
            weeklySchedule: {},
            exams: [],
            completedTasks: [],
            studyTime: 0,
            timerSeconds: 25 * 60,
            timerRunning: false,
            timerInterval: null
        };

        // روزهای هفته
        const days = ['شنبه', 'یکشنبه', 'دوشنبه', 'سه‌شنبه', 'چهارشنبه', 'پنجشنبه', 'جمعه'];

        // تاریخ شمسی
        function getPersianDate() {
            const now = new Date();
            const options = { 
                year: 'numeric', 
                month: 'long', 
                day: 'numeric',
                calendar: 'persian',
                numberingSystem: 'arab'
            };
            return new Intl.DateTimeFormat('fa-IR', options).format(now);
        }

        function getPersianDay(date) {
            const day = date.getDay();
            return days[(day + 1) % 7]; // تطبیق با شنبه شروع هفته
        }

        // بارگذاری اولیه
        function initializeApp() {
            loadFromLocalStorage();
            updateDateDisplay();
            updateSubjectsList();
            updateExamsList();
            updateScheduleDisplay();
            updateStats();
            generateWeeklyScheduleForm();
        }

        // مدیریت localStorage
        function saveToLocalStorage() {
            localStorage.setItem('studyPlannerData', JSON.stringify(appData));
        }

        function loadFromLocalStorage() {
            const saved = localStorage.getItem('studyPlannerData');
            if (saved) {
                appData = JSON.parse(saved);
            }
        }

        // نمایش تاریخ
        function updateDateDisplay() {
            const now = new Date();
            const tomorrow = new Date(now);
            tomorrow.setDate(tomorrow.getDate() + 1);

            document.getElementById('currentDate').textContent = getPersianDate();
            document.getElementById('todayDate').textContent = getPersianDate(now);
            document.getElementById('todayDay').textContent = getPersianDay(now);
            document.getElementById('tomorrowDate').textContent = getPersianDate(tomorrow);
            document.getElementById('tomorrowDay').textContent = getPersianDay(tomorrow);
        }

        // مدیریت دروس
        function addSubject() {
            const subjectInput = document.getElementById('newSubject');
            const subjectName = subjectInput.value.trim();
            
            if (subjectName && !appData.subjects.includes(subjectName)) {
                appData.subjects.push(subjectName);
                subjectInput.value = '';
                updateSubjectsList();
                saveToLocalStorage();
                updateStats();
            }
        }

        function removeSubject(subjectName) {
            appData.subjects = appData.subjects.filter(sub => sub !== subjectName);
            updateSubjectsList();
            saveToLocalStorage();
            updateStats();
        }

        function updateSubjectsList() {
            const list = document.getElementById('subjectsList');
            const examSelect = document.getElementById('examSubject');
            
            list.innerHTML = '';
            examSelect.innerHTML = '<option value="">انتخاب درس</option>';
            
            appData.subjects.forEach(subject => {
                // برای لیست نمایش
                const listItem = document.createElement('div');
                listItem.className = 'list-item';
                listItem.innerHTML = `
                    <span>${subject}</span>
                    <button class="delete-btn" onclick="removeSubject('${subject}')">
                        <i class="fas fa-trash"></i> حذف
                    </button>
                `;
                list.appendChild(listItem);
                
                // برای انتخاب امتحان
                const option = document.createElement('option');
                option.value = subject;
                option.textContent = subject;
                examSelect.appendChild(option);
            });
        }

        function handleSubjectKeyPress(event) {
            if (event.key === 'Enter') {
                addSubject();
            }
        }

        // مدیریت امتحانات
        function addExam() {
            const subjectSelect = document.getElementById('examSubject');
            const dateInput = document.getElementById('examDate');
            
            const subject = subjectSelect.value;
            const date = dateInput.value;
            
            if (subject && date) {
                appData.exams.push({
                    subject: subject,
                    date: date,
                    id: Date.now()
                });
                
                subjectSelect.value = '';
                dateInput.value = '';
                updateExamsList();
                saveToLocalStorage();
                updateStats();
            }
        }

        function removeExam(examId) {
            appData.exams = appData.exams.filter(exam => exam.id !== examId);
            updateExamsList();
            saveToLocalStorage();
            updateStats();
        }

        function updateExamsList() {
            const list = document.getElementById('examsList');
            list.innerHTML = '';
            
            appData.exams.forEach(exam => {
                const listItem = document.createElement('div');
                listItem.className = 'list-item';
                listItem.innerHTML = `
                    <div>
                        <strong>${exam.subject}</strong>
                        <br>
                        <small>${new Date(exam.date).toLocaleDateString('fa-IR')}</small>
                    </div>
                    <button class="delete-btn" onclick="removeExam(${exam.id})">
                        <i class="fas fa-trash"></i> حذف
                    </button>
                `;
                list.appendChild(listItem);
            });
        }

        // برنامه هفتگی
        function generateWeeklyScheduleForm() {
            const form = document.getElementById('weeklyScheduleForm');
            form.innerHTML = '';
            
            days.forEach(day => {
                const daySection = document.createElement('div');
                daySection.className = 'day-schedule';
                daySection.innerHTML = `<div class="day-title">${day}</div>`;
                
                for (let i = 1; i <= 4; i++) {
                    const sessionDiv = document.createElement('div');
                    sessionDiv.className = 'input-group';
                    sessionDiv.innerHTML = `
                        <label for="${day}_${i}">زنگ ${i}:</label>
                        <select id="${day}_${i}">
                            <option value="">انتخاب درس</option>
                            ${appData.subjects.map(sub => 
                                `<option value="${sub}" ${appData.weeklySchedule[`${day}_${i}`] === sub ? 'selected' : ''}>${sub}</option>`
                            ).join('')}
                        </select>
                    `;
                    daySection.appendChild(sessionDiv);
                }
                
                form.appendChild(daySection);
            });
        }

        function saveWeeklySchedule() {
            const schedule = {};
            
            days.forEach(day => {
                for (let i = 1; i <= 4; i++) {
                    const select = document.getElementById(`${day}_${i}`);
                    if (select.value) {
                        schedule[`${day}_${i}`] = select.value;
                    }
                }
            });
            
            appData.weeklySchedule = schedule;
            saveToLocalStorage();
            updateScheduleDisplay();
            closeModal('scheduleModal');
            alert('برنامه هفتگی با موفقیت ذخیره شد!');
        }

        function updateScheduleDisplay() {
            const display = document.getElementById('schoolSchedule');
            display.innerHTML = '';
            
            let hasSchedule = false;
            
            days.forEach(day => {
                const dayDiv = document.createElement('div');
                dayDiv.className = 'day-schedule';
                
                let daySessions = [];
                for (let i = 1; i <= 4; i++) {
                    const subject = appData.weeklySchedule[`${day}_${i}`];
                    if (subject) {
                        daySessions.push(`زنگ ${i}: ${subject}`);
                        hasSchedule = true;
                    }
                }
                
                if (daySessions.length > 0) {
                    dayDiv.innerHTML = `
                        <div class="day-title">${day}</div>
                        ${daySessions.map(session => `<div class="session-item">${session}</div>`).join('')}
                    `;
                    display.appendChild(dayDiv);
                }
            });
            
            if (!hasSchedule) {
                display.innerHTML = '<div style="text-align: center; opacity: 0.7;">برنامه‌ای تنظیم نشده است</div>';
            }
        }

        // برنامه‌ریزی هوشمند
        function generateSmartPlan() {
            if (appData.subjects.length === 0) {
                alert('لطفا اول دروس را اضافه کنید!');
                return;
            }
            
            const today = new Date();
            const tomorrow = new Date(today);
            tomorrow.setDate(tomorrow.getDate() + 1);
            
            const todayDay = getPersianDay(today);
            const tomorrowDay = getPersianDay(tomorrow);
            
            // برنامه امروز
            const todayTasks = generateTodayPlan(todayDay);
            displayTasks('todayTasks', todayTasks, 'today');
            
            // برنامه فردا
            const tomorrowTasks = generateTomorrowPlan(tomorrowDay);
            displayTasks('tomorrowTasks', tomorrowTasks, 'tomorrow');
            
            alert('برنامه هوشمند با موفقیت تولید شد!');
        }

        function generateTodayPlan(todayDay) {
            const tasks = [];
            
            // دروس امروز مدرسه
            const todaySubjects = [];
            for (let i = 1; i <= 4; i++) {
                const subject = appData.weeklySchedule[`${todayDay}_${i}`];
                if (subject && !todaySubjects.includes(subject)) {
                    todaySubjects.push(subject);
                }
            }
            
            if (todaySubjects.length > 0) {
                tasks.push(`🏫 دروس امروز مدرسه: ${todaySubjects.join('، ')}`);
                todaySubjects.forEach(subject => {
                    // بررسی امتحانات نزدیک
                    const urgentExam = appData.exams.find(exam => 
                        exam.subject === subject && 
                        isUrgentExam(exam.date)
                    );
                    
                    if (urgentExam) {
                        tasks.push(`🎯 مرور فشرده ${subject} (امتحان نزدیک)`);
                    } else {
                        tasks.push(`📚 مطالعه و تمرین ${subject}`);
                    }
                });
            } else {
                tasks.push('📖 مطالعه دروس عمومی');
            }
            
            // امتحانات فردا
            const tomorrowExams = appData.exams.filter(exam => isTomorrowExam(exam.date));
            if (tomorrowExams.length > 0) {
                const examSubjects = tomorrowExams.map(exam => exam.subject);
                tasks.push(`⚠️ مرور فوری برای فردا: ${examSubjects.join('، ')}`);
            }
            
            tasks.push('⏰ حل تمرین و مرور');
            tasks.push('☕ استراحت بین دروس (۱۵ دقیقه)');
            
            return tasks;
        }

        function generateTomorrowPlan(tomorrowDay) {
            const tasks = [];
            
            // پیش‌خوانی دروس فردا
            const tomorrowSubjects = [];
            for (let i = 1; i <= 4; i++) {
                const subject = appData.weeklySchedule[`${tomorrowDay}_${i}`];
                if (subject && !tomorrowSubjects.includes(subject)) {
                    tomorrowSubjects.push(subject);
                }
            }
            
            if (tomorrowSubjects.length > 0) {
                tasks.push(`🔍 پیش‌خوانی دروس فردا: ${tomorrowSubjects.join('، ')}`);
                tomorrowSubjects.forEach(subject => {
                    tasks.push(`📖 آشنایی با مبحث جدید ${subject}`);
                });
            }
            
            // پیش‌خوانی امتحانات آینده
            const upcomingExams = appData.exams.filter(exam => isUpcomingExam(exam.date));
            if (upcomingExams.length > 0) {
                const examSubjects = upcomingExams.map(exam => exam.subject);
                tasks.push(`📝 پیش‌خوانی امتحان: ${examSubjects.join('، ')}`);
            }
            
            if (tasks.length === 0) {
                tasks.push('📚 پیش‌خوانی دروس هفته آینده');
            }
            
            return tasks;
        }

        function isUrgentExam(examDate) {
            const exam = new Date(examDate);
            const today = new Date();
            const diffTime = exam - today;
            const diffDays = Math.ceil(diffTime / (1000 * 60 * 60 * 24));
            return diffDays <= 2;
        }

        function isTomorrowExam(examDate) {
            const exam = new Date(examDate);
            const tomorrow = new Date();
            tomorrow.setDate(tomorrow.getDate() + 1);
            return exam.toDateString() === tomorrow.toDateString();
        }

        function isUpcomingExam(examDate) {
            const exam = new Date(examDate);
            const today = new Date();
            const diffTime = exam - today;
            const diffDays = Math.ceil(diffTime / (1000 * 60 * 60 * 24));
            return diffDays >= 3 && diffDays <= 5;
        }

        function displayTasks(containerId, tasks, type) {
            const container = document.getElementById(containerId);
            container.innerHTML = '';
            
            tasks.forEach((task, index) => {
                const taskId = `${type}_${index}`;
                const isCompleted = appData.completedTasks.includes(taskId);
                
                const taskDiv = document.createElement('div');
                taskDiv.className = 'task-item';
                taskDiv.innerHTML = `
                    <div class="task-checkbox ${isCompleted ? 'checked' : ''}" 
                         onclick="toggleTask('${taskId}', this)">
                    </div>
                    <div class="task-text ${isCompleted ? 'completed' : ''}">
                        ${task}
                    </div>
                `;
                container.appendChild(taskDiv);
            });
        }

        function toggleTask(taskId, checkbox) {
            const index = appData.completedTasks.indexOf(taskId);
            
            if (index === -1) {
                appData.completedTasks.push(taskId);
                checkbox.classList.add('checked');
                checkbox.nextElementSibling.classList.add('completed');
            } else {
                appData.completedTasks.splice(index, 1);
                checkbox.classList.remove('checked');
                checkbox.nextElementSibling.classList.remove('completed');
            }
            
            saveToLocalStorage();
            updateStats();
        }

        // تایمر
        function startTimer() {
            if (!appData.timerRunning) {
                appData.timerRunning = true;
                appData.timerInterval = setInterval(updateTimer, 1000);
                updateTimerCircle();
            }
        }

        function stopTimer() {
            if (appData.timerRunning) {
                appData.timerRunning = false;
                clearInterval(appData.timerInterval);
                // محاسبه زمان مطالعه
                const totalMinutes = parseInt(document.getElementById('timerMinutes').value);
                const studiedSeconds = (totalMinutes * 60) - appData.timerSeconds;
                appData.studyTime += Math.floor(studiedSeconds / 60);
                updateStats();
            }
        }

        function resetTimer() {
            stopTimer();
            setTimer();
        }

        function setTimer() {
            const minutes = parseInt(document.getElementById('timerMinutes').value);
            appData.timerSeconds = minutes * 60;
            updateTimerDisplay();
            updateTimerCircle();
        }

        function updateTimer() {
            if (appData.timerSeconds > 0) {
                appData.timerSeconds--;
                updateTimerDisplay();
                updateTimerCircle();
            } else {
                stopTimer();
                alert('⏰ زمان مطالعه به پایان رسید! استراحت کنید.');
                // اضافه کردن زمان مطالعه
                const totalMinutes = parseInt(document.getElementById('timerMinutes').value);
                appData.studyTime += totalMinutes;
                updateStats();
            }
        }

        function updateTimerDisplay() {
            const minutes = Math.floor(appData.timerSeconds / 60);
            const seconds = appData.timerSeconds % 60;
            document.getElementById('timerDisplay').textContent = 
                `${minutes.toString().padStart(2, '0')}:${seconds.toString().padStart(2, '0')}`;
        }

        function updateTimerCircle() {
            const totalMinutes = parseInt(document.getElementById('timerMinutes').value);
            const totalSeconds = totalMinutes * 60;
            const progress = 1 - (appData.timerSeconds / totalSeconds);
            const degrees = progress * 360;
            
            const circle = document.getElementById('timerCircle');
            circle.style.background = `conic-gradient(#ffd32a ${degrees}deg, #34495e ${degrees}deg)`;
        }

        // آمار
        function updateStats() {
            document.getElementById('subjectsCount').textContent = appData.subjects.length;
            document.getElementById('examsCount').textContent = appData.exams.length;
            document.getElementById('studyTime').textContent = appData.studyTime;
            document.getElementById('completedTasks').textContent = appData.completedTasks.length;
        }

        // مدیریت مودال
        function showModal(modalId) {
            document.getElementById(modalId).style.display = 'block';
        }

        function closeModal(modalId) {
            document.getElementById(modalId).style.display = 'none';
        }

        // بستن مودال با کلیک خارج
        window.onclick = function(event) {
            if (event.target.classList.contains('modal')) {
                event.target.style.display = 'none';
            }
        }

        // راه‌اندازی برنامه
        document.addEventListener('DOMContentLoaded', initializeApp);
    </script>
</body>
</html>
