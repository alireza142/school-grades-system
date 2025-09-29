<!DOCTYPE html>
<html lang="fa" dir="rtl">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>سیستم مدیریت نمرات مدرسه</title>
    <link href="https://cdn.jsdelivr.net/npm/bootstrap@5.1.3/dist/css/bootstrap.min.css" rel="stylesheet">
    <style>
        body {
            background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
            font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
            min-height: 100vh;
            padding: 20px;
        }
        .login-container {
            background: white;
            border-radius: 15px;
            box-shadow: 0 10px 30px rgba(0,0,0,0.3);
            margin: 50px auto;
            max-width: 500px;
        }
        .btn-primary {
            background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
            border: none;
        }
        .card {
            margin-bottom: 20px;
            border: none;
            border-radius: 10px;
            box-shadow: 0 4px 6px rgba(0,0,0,0.1);
        }
        .navbar-brand {
            font-weight: bold;
        }
    </style>
</head>
<body>
    <!-- نوار بالایی -->
    <nav class="navbar navbar-dark bg-dark rounded mb-4">
        <div class="container-fluid">
            <span class="navbar-brand">🏫 سیستم مدیریت نمرات مدرسه</span>
        </div>
    </nav>

    <!-- صفحه لاگین -->
    <div id="loginPage">
        <div class="login-container p-4">
            <h3 class="text-center mb-4">ورود معلمین</h3>
            <form id="loginForm">
                <div class="mb-3">
                    <label for="username" class="form-label">نام کاربری</label>
                    <input type="text" class="form-control" id="username" value="admin" required>
                </div>
                <div class="mb-3">
                    <label for="password" class="form-label">رمز عبور</label>
                    <input type="password" class="form-control" id="password" value="1234" required>
                </div>
                <button type="submit" class="btn btn-primary w-100">ورود به سیستم</button>
            </form>
            <div class="mt-3 text-center">
                <small class="text-muted"></small>
            </div>
        </div>
    </div>

    <!-- داشبورد (مخفی در ابتدا) -->
    <div id="dashboard" style="display: none;">
        <div class="d-flex justify-content-between align-items-center mb-4">
            <h3 class="text-white">خوش آمدید، <span id="teacherName">مدیر سیستم</span></h3>
            <button class="btn btn-light" onclick="logout()">خروج</button>
        </div>

        <!-- مدیریت کلاس‌ها -->
        <div class="row">
            <div class="col-md-4">
                <div class="card">
                    <div class="card-header bg-primary text-white">
                        <h5 class="mb-0">مدیریت کلاس‌ها</h5>
                    </div>
                    <div class="card-body">
                        <form id="classForm">
                            <div class="mb-3">
                                <input type="text" class="form-control" id="className" placeholder="نام کلاس" required>
                            </div>
                            <button type="submit" class="btn btn-success w-100">ایجاد کلاس جدید</button>
                        </form>
                        <div id="classList" class="mt-3">
                            <!-- لیست کلاس‌ها اینجا نمایش داده می‌شود -->
                        </div>
                    </div>
                </div>
            </div>

            <!-- مدیریت دانش‌آموزان -->
            <div class="col-md-8">
                <div class="card">
                    <div class="card-header bg-info text-white">
                        <h5 class="mb-0">مدیریت دانش‌آموزان</h5>
                    </div>
                    <div class="card-body">
                        <form id="studentForm">
                            <div class="row">
                                <div class="col-md-4">
                                    <input type="text" class="form-control mb-2" id="studentFirstName" placeholder="نام" required>
                                </div>
                                <div class="col-md-4">
                                    <input type="text" class="form-control mb-2" id="studentLastName" placeholder="نام خانوادگی" required>
                                </div>
                                <div class="col-md-4">
                                    <input type="text" class="form-control mb-2" id="studentId" placeholder="کد دانش‌آموزی" required>
                                </div>
                            </div>
                            <div class="mb-3">
                                <select class="form-select" id="studentClass" required>
                                    <option value="">انتخاب کلاس</option>
                                </select>
                            </div>
                            <button type="submit" class="btn btn-primary w-100">ثبت دانش‌آموز</button>
                        </form>
                        <div id="studentList" class="mt-3">
                            <!-- لیست دانش‌آموزان اینجا نمایش داده می‌شود -->
                        </div>
                    </div>
                </div>
            </div>
        </div>

        <!-- ورود نمرات -->
        <div class="row mt-4">
            <div class="col-12">
                <div class="card">
                    <div class="card-header bg-warning text-dark">
                        <h5 class="mb-0">ورود نمرات</h5>
                    </div>
                    <div class="card-body">
                        <form id="gradeForm">
                            <div class="row g-2">
                                <div class="col-md-3">
                                    <select class="form-select" id="gradeStudent" required>
                                        <option value="">انتخاب دانش‌آموز</option>
                                    </select>
                                </div>
                                <div class="col-md-3">
                                    <select class="form-select" id="gradeSubject" required>
                                        <option value="">انتخاب درس</option>
                                        <option value="math">ریاضی</option>
                                        <option value="science">علوم</option>
                                        <option value="literature">ادبیات</option>
                                        <option value="english">زبان انگلیسی</option>
                                    </select>
                                </div>
                                <div class="col-md-3">
                                    <input type="number" class="form-control" id="gradeScore" placeholder="نمره (از 20)" min="0" max="20" step="0.25" required>
                                </div>
                                <div class="col-md-3">
                                    <button type="submit" class="btn btn-success w-100">ثبت نمره</button>
                                </div>
                            </div>
                        </form>
                    </div>
                </div>
            </div>
        </div>

        <!-- نمایش کارنامه -->
        <div class="row mt-4">
            <div class="col-12">
                <div class="card">
                    <div class="card-header bg-success text-white d-flex justify-content-between align-items-center">
                        <h5 class="mb-0">کارنامه دانش‌آموزان</h5>
                        <button class="btn btn-light btn-sm" onclick="generateAllReportCards()">چاپ همه کارنامه‌ها</button>
                    </div>
                    <div class="card-body">
                        <div id="reportCards">
                            <!-- کارنامه‌ها اینجا نمایش داده می‌شوند -->
                        </div>
                    </div>
                </div>
            </div>
        </div>
    </div>

    <script>
        // داده‌های نمونه
        let teachers = [
            { username: 'admin', password: '1234', name: 'مدیر سیستم' }
        ];

        let classes = [];
        let students = [];
        let grades = [];

        // لاگین
        document.getElementById('loginForm').addEventListener('submit', function(e) {
            e.preventDefault();
            
            const username = document.getElementById('username').value;
            const password = document.getElementById('password').value;
            
            const teacher = teachers.find(t => t.username === username && t.password === password);
            
            if (teacher) {
                document.getElementById('loginPage').style.display = 'none';
                document.getElementById('dashboard').style.display = 'block';
                document.getElementById('teacherName').textContent = teacher.name;
                loadDashboard();
            } else {
                alert('نام کاربری یا رمز عبور اشتباه است!');
            }
        });

        // ایجاد کلاس جدید
        document.getElementById('classForm').addEventListener('submit', function(e) {
            e.preventDefault();
            
            const className = document.getElementById('className').value;
            const classId = Date.now().toString();
            
            classes.push({
                id: classId,
                name: className,
                teacher: document.getElementById('teacherName').textContent
            });
            
            document.getElementById('className').value = '';
            loadClasses();
            loadStudentClassSelect();
        });

        // ثبت دانش‌آموز جدید
        document.getElementById('studentForm').addEventListener('submit', function(e) {
            e.preventDefault();
            
            const firstName = document.getElementById('studentFirstName').value;
            const lastName = document.getElementById('studentLastName').value;
            const studentId = document.getElementById('studentId').value;
            const classId = document.getElementById('studentClass').value;
            
            const selectedClass = classes.find(c => c.id === classId);
            
            students.push({
                id: Date.now().toString(),
                firstName: firstName,
                lastName: lastName,
                studentId: studentId,
                classId: classId,
                className: selectedClass.name
            });
            
            // پاک کردن فرم
            document.getElementById('studentFirstName').value = '';
            document.getElementById('studentLastName').value = '';
            document.getElementById('studentId').value = '';
            
            loadStudents();
            loadGradeStudentSelect();
        });

        // ثبت نمره
        document.getElementById('gradeForm').addEventListener('submit', function(e) {
            e.preventDefault();
            
            const studentId = document.getElementById('gradeStudent').value;
            const subject = document.getElementById('gradeSubject').value;
            const score = parseFloat(document.getElementById('gradeScore').value);
            
            const student = students.find(s => s.id === studentId);
            
            grades.push({
                id: Date.now().toString(),
                studentId: studentId,
                studentName: `${student.firstName} ${student.lastName}`,
                subject: subject,
                score: score,
                date: new Date().toLocaleDateString('fa-IR')
            });
            
            document.getElementById('gradeScore').value = '';
            loadReportCards();
        });

        // بارگذاری کلاس‌ها
        function loadClasses() {
            const classList = document.getElementById('classList');
            classList.innerHTML = '';
            
            classes.forEach(classItem => {
                const classElement = document.createElement('div');
                classElement.className = 'alert alert-info d-flex justify-content-between align-items-center';
                classElement.innerHTML = `
                    <span>${classItem.name}</span>
                    <button class="btn btn-sm btn-danger" onclick="deleteClass('${classItem.id}')">حذف</button>
                `;
                classList.appendChild(classElement);
            });
        }

        // بارگذاری دانش‌آموزان
        function loadStudents() {
            const studentList = document.getElementById('studentList');
            studentList.innerHTML = '';
            
            students.forEach(student => {
                const studentElement = document.createElement('div');
                studentElement.className = 'alert alert-secondary d-flex justify-content-between align-items-center';
                studentElement.innerHTML = `
                    <div>
                        <strong>${student.firstName} ${student.lastName}</strong>
                        <br>
                        <small>کد: ${student.studentId} - کلاس: ${student.className}</small>
                    </div>
                    <button class="btn btn-sm btn-warning" onclick="viewReportCard('${student.id}')">کارنامه</button>
                `;
                studentList.appendChild(studentElement);
            });
        }

        // بارگذاری انتخاب کلاس برای دانش‌آموز
        function loadStudentClassSelect() {
            const select = document.getElementById('studentClass');
            select.innerHTML = '<option value="">انتخاب کلاس</option>';
            
            classes.forEach(classItem => {
                const option = document.createElement('option');
                option.value = classItem.id;
                option.textContent = classItem.name;
                select.appendChild(option);
            });
        }

        // بارگذاری انتخاب دانش‌آموز برای نمره
        function loadGradeStudentSelect() {
            const select = document.getElementById('gradeStudent');
            select.innerHTML = '<option value="">انتخاب دانش‌آموز</option>';
            
            students.forEach(student => {
                const option = document.createElement('option');
                option.value = student.id;
                option.textContent = `${student.firstName} ${student.lastName} - ${student.className}`;
                select.appendChild(option);
            });
        }

        // نمایش کارنامه
        function loadReportCards() {
            const reportCards = document.getElementById('reportCards');
            reportCards.innerHTML = '';
            
            students.forEach(student => {
                const studentGrades = grades.filter(g => g.studentId === student.id);
                
                if (studentGrades.length > 0) {
                    const average = studentGrades.reduce((sum, grade) => sum + grade.score, 0) / studentGrades.length;
                    
                    const reportCard = document.createElement('div');
                    reportCard.className = 'card mb-3';
                    reportCard.innerHTML = `
                        <div class="card-header">
                            <h6>کارنامه ${student.firstName} ${student.lastName}</h6>
                        </div>
                        <div class="card-body">
                            <p><strong>کد دانش‌آموزی:</strong> ${student.studentId}</p>
                            <p><strong>کلاس:</strong> ${student.className}</p>
                            
                            <table class="table table-bordered table-striped">
                                <thead>
                                    <tr>
                                        <th>درس</th>
                                        <th>نمره</th>
                                        <th>وضعیت</th>
                                    </tr>
                                </thead>
                                <tbody>
                                    ${studentGrades.map(grade => `
                                        <tr>
                                            <td>${getSubjectName(grade.subject)}</td>
                                            <td>${grade.score}</td>
                                            <td>
                                                <span class="badge ${grade.score >= 10 ? 'bg-success' : 'bg-danger'}">
                                                    ${grade.score >= 10 ? 'قبول' : 'مردود'}
                                                </span>
                                            </td>
                                        </tr>
                                    `).join('')}
                                </tbody>
                            </table>
                            
                            <div class="alert ${average >= 15 ? 'alert-success' : average >= 10 ? 'alert-warning' : 'alert-danger'}">
                                <strong>معدل:</strong> ${average.toFixed(2)}
                            </div>
                            
                            <button class="btn btn-primary" onclick="printReportCard('${student.id}')">چاپ کارنامه</button>
                        </div>
                    `;
                    reportCards.appendChild(reportCard);
                }
            });
        }

        // مشاهده کارنامه خاص
        function viewReportCard(studentId) {
            const student = students.find(s => s.id === studentId);
            const studentGrades = grades.filter(g => g.studentId === studentId);
            
            if (studentGrades.length === 0) {
                alert('برای این دانش‌آموز نمره‌ای ثبت نشده است!');
                return;
            }
            
            const average = studentGrades.reduce((sum, grade) => sum + grade.score, 0) / studentGrades.length;
            
            const reportCardHTML = `
                <div class="card">
                    <div class="card-header text-center">
                        <h4>🏫 مدرسه نمونه</h4>
                        <h5>کارنامه تحصیلی</h5>
                    </div>
                    <div class="card-body">
                        <div class="row">
                            <div class="col-md-6">
                                <p><strong>نام دانش‌آموز:</strong> ${student.firstName} ${student.lastName}</p>
                                <p><strong>کد دانش‌آموزی:</strong> ${student.studentId}</p>
                            </div>
                            <div class="col-md-6">
                                <p><strong>کلاس:</strong> ${student.className}</p>
                                <p><strong>تاریخ:</strong> ${new Date().toLocaleDateString('fa-IR')}</p>
                            </div>
                        </div>
                        
                        <table class="table table-bordered mt-3">
                            <thead class="table-dark">
                                <tr>
                                    <th>درس</th>
                                    <th>نمره</th>
                                    <th>وضعیت</th>
                                </tr>
                            </thead>
                            <tbody>
                                ${studentGrades.map(grade => `
                                    <tr>
                                        <td>${getSubjectName(grade.subject)}</td>
                                        <td>${grade.score}</td>
                                        <td>
                                            <span class="badge ${grade.score >= 10 ? 'bg-success' : 'bg-danger'}">
                                                ${grade.score >= 10 ? 'قبول' : 'مردود'}
                                            </span>
                                        </td>
                                    </tr>
                                `).join('')}
                            </tbody>
                        </table>
                        
                        <div class="alert ${average >= 15 ? 'alert-success' : average >= 10 ? 'alert-warning' : 'alert-danger'}">
                            <h5 class="text-center">معدل کل: ${average.toFixed(2)}</h5>
                        </div>
                    </div>
                </div>
            `;
            
            // نمایش در یک پنجره جدید
            const newWindow = window.open('', '_blank');
            newWindow.document.write(`
                <html dir="rtl">
                <head>
                    <title>کارنامه ${student.firstName} ${student.lastName}</title>
                    <link href="https://cdn.jsdelivr.net/npm/bootstrap@5.1.3/dist/css/bootstrap.min.css" rel="stylesheet">
                </head>
                <body>
                    <div class="container mt-4">
                        ${reportCardHTML}
                        <div class="text-center mt-3">
                            <button class="btn btn-success" onclick="window.print()">چاپ کارنامه</button>
                        </div>
                    </div>
                </body>
                </html>
            `);
        }

        // چاپ کارنامه
        function printReportCard(studentId) {
            viewReportCard(studentId);
        }

        // تولید همه کارنامه‌ها
        function generateAllReportCards() {
            students.forEach(student => {
                const studentGrades = grades.filter(g => g.studentId === student.id);
                if (studentGrades.length > 0) {
                    viewReportCard(student.id);
                }
            });
        }

        // حذف کلاس
        function deleteClass(classId) {
            if (confirm('آیا از حذف این کلاس مطمئن هستید؟')) {
                classes = classes.filter(c => c.id !== classId);
                students = students.filter(s => s.classId !== classId);
                loadClasses();
                loadStudentClassSelect();
                loadGradeStudentSelect();
                loadStudents();
                loadReportCards();
            }
        }

        // دریافت نام درس
        function getSubjectName(subjectCode) {
            const subjects = {
                'math': 'ریاضی',
                'science': 'علوم',
                'literature': 'ادبیات',
                'english': 'زبان انگلیسی'
            };
            return subjects[subjectCode] || subjectCode;
        }

        // خروج از سیستم
        function logout() {
            if (confirm('آیا می‌خواهید از سیستم خارج شوید؟')) {
                document.getElementById('dashboard').style.display = 'none';
                document.getElementById('loginPage').style.display = 'block';
                document.getElementById('loginForm').reset();
            }
        }

        // بارگذاری داشبورد
        function loadDashboard() {
            loadClasses();
            loadStudents();
            loadStudentClassSelect();
            loadGradeStudentSelect();
            loadReportCards();
        }

        // اطلاعات نمونه برای تست
        function addSampleData() {
            // کلاس نمونه
            if (classes.length === 0) {
                classes.push({
                    id: '1',
                    name: 'کلاس دهم ریاضی',
                    teacher: 'مدیر سیستم'
                });
                
                // دانش‌آموزان نمونه
                students.push({
                    id: '1',
                    firstName: 'علی',
                    lastName: 'محمدی',
                    studentId: '1001',
                    classId: '1',
                    className: 'کلاس دهم ریاضی'
                });
                
                students.push({
                    id: '2',
                    firstName: 'فاطمه',
                    lastName: 'کریمی',
                    studentId: '1002',
                    classId: '1',
                    className: 'کلاس دهم ریاضی'
                });
                
                // نمرات نمونه
                grades.push({
                    id: '1',
                    studentId: '1',
                    studentName: 'علی محمدی',
                    subject: 'math',
                    score: 18.5,
                    date: '1402/10/15'
                });
                
                grades.push({
                    id: '2',
                    studentId: '1',
                    studentName: 'علی محمدی',
                    subject: 'science',
                    score: 16,
                    date: '1402/10/15'
                });
            }
        }

        // اضافه کردن داده‌های نمونه هنگام بارگذاری صفحه
        window.addEventListener('load', function() {
            addSampleData();
        });
    </script>
</body>
</html>
