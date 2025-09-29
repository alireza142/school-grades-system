<!DOCTYPE html>
<html lang="fa" dir="rtl">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>سامانه مدیریت آموزشی - مدرسه نمونه دولتی امام حسین (ع)</title>
    <link href="https://cdn.jsdelivr.net/npm/bootstrap@5.1.3/dist/css/bootstrap.min.css" rel="stylesheet">
    <link rel="stylesheet" href="https://cdn.jsdelivr.net/npm/bootstrap-icons@1.10.0/font/bootstrap-icons.css">
    <style>
        :root {
            --moe-blue: #1e3a8a;
            --moe-red: #dc2626;
            --moe-green: #059669;
            --moe-gold: #d97706;
        }
        
        body {
            background: linear-gradient(135deg, #1e3a8a 0%, #2d4fa1 100%);
            font-family: 'B Nazanin', 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
            min-height: 100vh;
            padding: 20px;
        }
        
        .login-container {
            background: white;
            border-radius: 10px;
            box-shadow: 0 10px 30px rgba(0,0,0,0.3);
            margin: 30px auto;
            max-width: 500px;
            border: 3px solid var(--moe-red);
        }
        
        .moe-header {
            background: linear-gradient(135deg, var(--moe-blue), #2d4fa1);
            color: white;
            padding: 25px;
            text-align: center;
            border-radius: 10px 10px 0 0;
            border-bottom: 4px solid var(--moe-red);
            position: relative;
        }
        
        .school-title {
            font-family: 'B Titr', 'Segoe UI', sans-serif;
            font-size: 1.4rem;
            margin-bottom: 5px;
        }
        
        .moe-stamp {
            border: 2px solid var(--moe-gold);
            padding: 8px 15px;
            border-radius: 20px;
            background: rgba(255,255,255,0.1);
            font-size: 0.9rem;
        }
        
        .btn-moe {
            background: linear-gradient(135deg, var(--moe-blue), #2d4fa1);
            border: 2px solid var(--moe-red);
            color: white;
            padding: 12px 25px;
            font-weight: bold;
            border-radius: 8px;
            font-family: 'B Nazanin', sans-serif;
        }
        
        .btn-moe:hover {
            background: linear-gradient(135deg, #2d4fa1, var(--moe-blue));
            transform: translateY(-2px);
            box-shadow: 0 5px 15px rgba(0,0,0,0.2);
            color: white;
        }
        
        .card-moe {
            border: 2px solid var(--moe-blue);
            border-radius: 8px;
            box-shadow: 0 4px 12px rgba(0,0,0,0.1);
            margin-bottom: 20px;
            background: white;
        }
        
        .card-header-moe {
            background: linear-gradient(135deg, var(--moe-blue), #2d4fa1);
            color: white;
            font-weight: bold;
            border-bottom: 3px solid var(--moe-red);
            padding: 15px;
            font-family: 'B Nazanin', sans-serif;
        }
        
        .official-table {
            width: 100%;
            border-collapse: collapse;
            font-family: 'B Nazanin', sans-serif;
            font-size: 0.95rem;
        }
        
        .official-table th {
            background: var(--moe-blue);
            color: white;
            padding: 12px 8px;
            text-align: center;
            border: 1px solid #ddd;
            font-weight: bold;
        }
        
        .official-table td {
            padding: 10px 8px;
            border: 1px solid #ddd;
            text-align: center;
        }
        
        .report-card-official {
            background: white;
            border: 3px solid var(--moe-blue);
            border-radius: 8px;
            padding: 0;
            margin: 15px 0;
            box-shadow: 0 4px 15px rgba(0,0,0,0.1);
            font-family: 'B Nazanin', sans-serif;
        }
        
        .report-header {
            background: linear-gradient(135deg, var(--moe-blue), #2d4fa1);
            color: white;
            padding: 20px;
            text-align: center;
            border-bottom: 4px solid var(--moe-red);
        }
        
        .student-info-section {
            padding: 25px;
            background: #f8f9fa;
            border-bottom: 2px solid #dee2e6;
        }
        
        .grades-table-section {
            padding: 20px;
        }
        
        .grade-excellent { background-color: #d4edda !important; }
        .grade-good { background-color: #fff3cd !important; }
        .grade-weak { background-color: #f8d7da !important; }
        
        .official-stamp {
            border: 3px double var(--moe-red);
            padding: 20px;
            text-align: center;
            font-weight: bold;
            color: var(--moe-blue);
            margin: 25px;
            font-family: 'B Titr', 'Times New Roman', serif;
            background: #f8f9fa;
        }
        
        .teacher-panel {
            background: linear-gradient(135deg, #f8f9fa, #e9ecef);
            border: 2px solid var(--moe-green);
            border-radius: 8px;
            padding: 15px;
            margin-bottom: 15px;
        }
        
        .subject-badge {
            background: var(--moe-green);
            color: white;
            padding: 4px 12px;
            border-radius: 15px;
            font-size: 0.8rem;
            margin: 2px;
        }
        
        .navbar-moe {
            background: linear-gradient(135deg, var(--moe-blue), #2d4fa1);
            border-bottom: 4px solid var(--moe-red);
            padding: 15px 0;
        }
        
        .admin-panel {
            background: linear-gradient(135deg, #fff3cd, #ffeaa7);
            border: 2px solid var(--moe-gold);
            border-radius: 8px;
            padding: 15px;
            margin-bottom: 15px;
        }
        
        /* چاپ کارنامه */
        @media print {
            body * {
                visibility: hidden;
            }
            .report-card-official, .report-card-official * {
                visibility: visible;
            }
            .report-card-official {
                position: absolute;
                left: 0;
                top: 0;
                width: 100%;
                box-shadow: none;
                border: none;
            }
            .no-print {
                display: none !important;
            }
        }

        .student-report-item {
            cursor: pointer;
            transition: all 0.3s ease;
        }
        
        .student-report-item:hover {
            background-color: #f8f9fa;
            transform: translateX(-5px);
        }
    </style>
</head>
<body>
    <!-- صفحه لاگین -->
    <div id="loginPage">
        <div class="login-container">
            <div class="moe-header">
                <div class="school-title">مدرسه نمونه دولتی امام حسین (ع)</div>
                <div class="moe-stamp">سامانه یکپارچه مدیریت آموزشی</div>
                <div style="margin-top: 15px; font-size: 0.9rem;">
                    <i class="bi bi-geo-alt-fill"></i> استان البرز - شهرستان کرج
                </div>
            </div>
            <div class="p-4">
                <h5 class="text-center mb-4" style="color: var(--moe-blue); font-family: 'B Nazanin';">
                    <i class="bi bi-shield-lock"></i> سامانه ورود معلمین
                </h5>
                <form id="loginForm">
                    <div class="mb-3">
                        <label for="username" class="form-label">کد پرسنلی</label>
                        <input type="text" class="form-control text-center" id="username" placeholder="شش رقم" required style="font-family: 'B Nazanin';">
                    </div>
                    <div class="mb-3">
                        <label for="password" class="form-label">رمز عبور</label>
                        <input type="password" class="form-control text-center" id="password" placeholder="رمز اختصاصی" required style="font-family: 'B Nazanin';">
                    </div>
                    <button type="submit" class="btn btn-moe w-100">
                        <i class="bi bi-box-arrow-in-right"></i> ورود به سامانه
                    </button>
                </form>
                <div class="mt-4 text-center">
                    <div class="alert alert-info">
                        <h6>دسترسی‌های آزمایشی:</h6>
                        <div class="row text-start">
                            <div class="col-6">
                                <small>• ریاضی دهم: ۱۴۰۲۰۱/۱۲۳۴</small><br>
                                <small>• فیزیک یازدهم: ۱۴۰۲۰۲/۱۲۳۴</small>
                            </div>
                            <div class="col-6">
                                <small>• ادبیات دوازدهم: ۱۴۰۲۰۳/۱۲۳۴</small><br>
                                <small>• مدیریت: ۱۴۰۲۰۰/۱۲۳۴</small>
                            </div>
                        </div>
                    </div>
                </div>
            </div>
        </div>
    </div>

    <!-- داشبورد اصلی -->
    <div id="dashboard" style="display: none;">
        <!-- نوار بالایی -->
        <nav class="navbar navbar-moe rounded mb-4">
            <div class="container-fluid">
                <div class="d-flex align-items-center">
                    <span class="navbar-brand text-white fw-bold" style="font-family: 'B Titr';">
                        <i class="bi bi-mortarboard-fill"></i> مدرسه نمونه دولتی امام حسین (ع)
                    </span>
                    <span class="badge bg-warning text-dark me-3" style="font-family: 'B Nazanin';">سامانه آموزشی</span>
                </div>
                <div class="text-white">
                    <span id="teacherName" class="me-3" style="font-family: 'B Nazanin';"></span>
                    <span id="teacherSpecialty" class="badge bg-success me-2"></span>
                    <button class="btn btn-sm btn-light" onclick="logout()" style="font-family: 'B Nazanin';">
                        <i class="bi bi-box-arrow-right"></i> خروج
                    </button>
                </div>
            </div>
        </nav>

        <!-- پنل مدیریت (فقط برای مدیر) -->
        <div id="adminPanel" style="display: none;">
            <div class="admin-panel">
                <h6 style="color: var(--moe-blue); font-family: 'B Nazanin';">
                    <i class="bi bi-person-gear"></i> پنل مدیریت سیستم
                </h6>
                <div class="row mt-3">
                    <div class="col-md-8">
                        <div class="card card-moe">
                            <div class="card-header card-header-moe">
                                <h6 class="mb-0"><i class="bi bi-people"></i> مدیریت معلمین</h6>
                            </div>
                            <div class="card-body">
                                <form id="teacherForm">
                                    <div class="row">
                                        <div class="col-md-3">
                                            <input type="text" class="form-control mb-2" id="teacherUsername" placeholder="کد پرسنلی" required>
                                        </div>
                                        <div class="col-md-3">
                                            <input type="password" class="form-control mb-2" id="teacherPassword" placeholder="رمز عبور" required>
                                        </div>
                                        <div class="col-md-3">
                                            <input type="text" class="form-control mb-2" id="teacherNameInput" placeholder="نام معلم" required>
                                        </div>
                                        <div class="col-md-3">
                                            <select class="form-select mb-2" id="teacherSpecialtyInput" required>
                                                <option value="">تخصص</option>
                                                <option value="ریاضی">ریاضی</option>
                                                <option value="فیزیک">فیزیک</option>
                                                <option value="شیمی">شیمی</option>
                                                <option value="ادبیات">ادبیات</option>
                                                <option value="زبان انگلیسی">زبان انگلیسی</option>
                                                <option value="عربی">عربی</option>
                                                <option value="دین و زندگی">دین و زندگی</option>
                                                <option value="تاریخ">تاریخ</option>
                                                <option value="جغرافیا">جغرافیا</option>
                                            </select>
                                        </div>
                                    </div>
                                    <div class="row">
                                        <div class="col-md-12">
                                            <label class="form-label">پایه‌های مجاز:</label>
                                            <div class="form-check form-check-inline">
                                                <input class="form-check-input" type="checkbox" id="grade10" value="10">
                                                <label class="form-check-label" for="grade10">دهم</label>
                                            </div>
                                            <div class="form-check form-check-inline">
                                                <input class="form-check-input" type="checkbox" id="grade11" value="11">
                                                <label class="form-check-label" for="grade11">یازدهم</label>
                                            </div>
                                            <div class="form-check form-check-inline">
                                                <input class="form-check-input" type="checkbox" id="grade12" value="12">
                                                <label class="form-check-label" for="grade12">دوازدهم</label>
                                            </div>
                                            <div class="form-check form-check-inline">
                                                <input class="form-check-input" type="checkbox" id="gradeAll" value="all">
                                                <label class="form-check-label" for="gradeAll">همه پایه‌ها</label>
                                            </div>
                                        </div>
                                    </div>
                                    <button type="submit" class="btn btn-moe w-100 mt-3">
                                        <i class="bi bi-person-plus"></i> ثبت معلم جدید
                                    </button>
                                </form>
                            </div>
                        </div>
                    </div>
                    <div class="col-md-4">
                        <div class="card card-moe">
                            <div class="card-header card-header-moe">
                                <h6 class="mb-0"><i class="bi bi-list-check"></i> لیست معلمین</h6>
                            </div>
                            <div class="card-body">
                                <div id="teacherList">
                                    <!-- لیست معلمین -->
                                </div>
                            </div>
                        </div>
                    </div>
                </div>
            </div>
        </div>

        <div class="row">
            <!-- پنل معلم -->
            <div class="col-md-4">
                <div class="teacher-panel">
                    <h6 style="color: var(--moe-blue); font-family: 'B Nazanin';">
                        <i class="bi bi-person-badge"></i> پنل اختصاصی معلم
                    </h6>
                    <div id="teacherInfo" class="mt-3">
                        <!-- اطلاعات معلم -->
                    </div>
                </div>

                <!-- مدیریت کلاس‌ها (فقط برای مدیر) -->
                <div id="classManagementPanel" class="card card-moe">
                    <div class="card-header card-header-moe">
                        <h6 class="mb-0"><i class="bi bi-house-door"></i> مدیریت کلاس‌ها</h6>
                    </div>
                    <div class="card-body">
                        <form id="classForm">
                            <div class="mb-3">
                                <select class="form-select" id="gradeLevel" required style="font-family: 'B Nazanin';">
                                    <option value="">پایه تحصیلی</option>
                                    <option value="10">پایه دهم</option>
                                    <option value="11">پایه یازدهم</option>
                                    <option value="12">پایه دوازدهم</option>
                                </select>
                            </div>
                            <div class="mb-3">
                                <select class="form-select" id="field" required style="font-family: 'B Nazanin';">
                                    <option value="">رشته تحصیلی</option>
                                    <option value="riazi">ریاضی فیزیک</option>
                                    <option value="tajrobi">علوم تجربی</option>
                                    <option value="ensani">علوم انسانی</option>
                                </select>
                            </div>
                            <div class="mb-3">
                                <input type="text" class="form-control text-center" id="className" placeholder="شماره کلاس" required style="font-family: 'B Nazanin';">
                            </div>
                            <button type="submit" class="btn btn-moe w-100">
                                <i class="bi bi-plus-circle"></i> ایجاد کلاس جدید
                            </button>
                        </form>
                        <div id="classList" class="mt-3">
                            <!-- لیست کلاس‌ها -->
                        </div>
                    </div>
                </div>
            </div>

            <!-- بخش دانش‌آموزان و نمرات -->
            <div class="col-md-8">
                <!-- ثبت دانش‌آموز (فقط برای مدیر) -->
                <div id="studentManagementPanel" class="card card-moe mb-3">
                    <div class="card-header card-header-moe">
                        <h6 class="mb-0"><i class="bi bi-people-fill"></i> ثبت نام دانش‌آموزان</h6>
                    </div>
                    <div class="card-body">
                        <form id="studentForm">
                            <div class="row">
                                <div class="col-md-3">
                                    <input type="text" class="form-control mb-2 text-center" id="studentFirstName" placeholder="نام" required style="font-family: 'B Nazanin';">
                                </div>
                                <div class="col-md-3">
                                    <input type="text" class="form-control mb-2 text-center" id="studentLastName" placeholder="نام خانوادگی" required style="font-family: 'B Nazanin';">
                                </div>
                                <div class="col-md-3">
                                    <input type="text" class="form-control mb-2 text-center" id="studentNationalCode" placeholder="کد ملی" required maxlength="10" style="font-family: 'B Nazanin';">
                                </div>
                                <div class="col-md-3">
                                    <input type="text" class="form-control mb-2 text-center" id="studentId" placeholder="ش دانش‌آموزی" required style="font-family: 'B Nazanin';">
                                </div>
                            </div>
                            <div class="row">
                                <div class="col-md-6">
                                    <input type="date" class="form-control mb-2" id="studentBirthDate" required>
                                </div>
                                <div class="col-md-6">
                                    <select class="form-select" id="studentClass" required style="font-family: 'B Nazanin';">
                                        <option value="">انتخاب کلاس</option>
                                    </select>
                                </div>
                            </div>
                            <button type="submit" class="btn btn-moe w-100">
                                <i class="bi bi-person-plus"></i> ثبت نام دانش‌آموز
                            </button>
                        </form>
                    </div>
                </div>

                <!-- لیست دانش‌آموزان -->
                <div class="card card-moe mb-3">
                    <div class="card-header card-header-moe">
                        <h6 class="mb-0"><i class="bi bi-list-ul"></i> لیست دانش‌آموزان</h6>
                    </div>
                    <div class="card-body">
                        <div class="table-responsive">
                            <table class="official-table">
                                <thead>
                                    <tr>
                                        <th>ردیف</th>
                                        <th>شماره</th>
                                        <th>نام و نام خانوادگی</th>
                                        <th>کد ملی</th>
                                        <th>کلاس</th>
                                        <th>عملیات</th>
                                    </tr>
                                </thead>
                                <tbody id="studentList">
                                    <!-- داده‌های دانش‌آموزان -->
                                </tbody>
                            </table>
                        </div>
                    </div>
                </div>

                <!-- ورود نمرات -->
                <div class="card card-moe">
                    <div class="card-header card-header-moe">
                        <h6 class="mb-0"><i class="bi bi-journal-text"></i> سیستم ورود نمرات</h6>
                    </div>
                    <div class="card-body">
                        <div class="row g-3 align-items-end mb-4">
                            <div class="col-md-4">
                                <label class="form-label">انتخاب کلاس</label>
                                <select class="form-select" id="gradeClass" required style="font-family: 'B Nazanin';" onchange="loadClassStudentsForGrades()">
                                    <option value="">انتخاب کلاس</option>
                                </select>
                            </div>
                            <div class="col-md-3">
                                <label class="form-label">نوبت</label>
                                <select class="form-select" id="gradeTerm" required style="font-family: 'B Nazanin';" onchange="loadClassStudentsForGrades()">
                                    <option value="1">نوبت اول</option>
                                    <option value="2">نوبت دوم</option>
                                </select>
                            </div>
                            <div class="col-md-3">
                                <label class="form-label">درس</label>
                                <input type="text" class="form-control text-center" id="gradeSubject" readonly style="font-family: 'B Nazanin'; background: #f8f9fa;">
                            </div>
                            <div class="col-md-2">
                                <button type="button" class="btn btn-moe w-100" onclick="saveAllGrades()">
                                    <i class="bi bi-check-lg"></i> ذخیره همه
                                </button>
                            </div>
                        </div>
                        
                        <!-- جدول دانش‌آموزان برای ثبت نمره -->
                        <div id="classStudentsGradesTable" class="mt-4" style="display: none;">
                            <h6>لیست دانش‌آموزان کلاس انتخاب شده</h6>
                            <div class="table-responsive">
                                <table class="official-table">
                                    <thead>
                                        <tr>
                                            <th>ردیف</th>
                                            <th>شماره دانش‌آموزی</th>
                                            <th>نام و نام خانوادگی</th>
                                            <th>نمره قبلی</th>
                                            <th>نمره جدید</th>
                                        </tr>
                                    </thead>
                                    <tbody id="classStudentsGradesList">
                                        <!-- لیست دانش‌آموزان برای ثبت نمره -->
                                    </tbody>
                                </table>
                            </div>
                        </div>
                    </div>
                </div>
            </div>
        </div>

        <!-- بخش کارنامه‌ها -->
        <div class="row mt-4">
            <div class="col-12">
                <div class="card card-moe">
                    <div class="card-header card-header-moe d-flex justify-content-between align-items-center">
                        <h6 class="mb-0"><i class="bi bi-file-earmark-text"></i> کارنامه‌های تحصیلی</h6>
                        <div>
                            <button class="btn btn-sm btn-light" onclick="generateAllReportCards()">
                                <i class="bi bi-printer"></i> چاپ همه کارنامه‌ها
                            </button>
                            <button class="btn btn-sm btn-danger ms-2" onclick="clearAllReportCards()">
                                <i class="bi bi-trash"></i> پاک کردن همه
                            </button>
                        </div>
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

    <script src="https://cdn.jsdelivr.net/npm/bootstrap@5.1.3/dist/js/bootstrap.bundle.min.js"></script>
    <script>
        // داده‌های معلمین با تخصص‌های مختلف
        let teachers = [
            { 
                username: '140201', 
                password: '1234', 
                name: 'محمد رضایی',
                personalCode: '۱۴۰۲۰۱',
                specialty: 'ریاضی',
                grades: ['10', '11', '12'],
                subjects: ['math'],
                type: 'teacher'
            },
            { 
                username: '140202', 
                password: '1234', 
                name: 'فاطمه کریمی',
                personalCode: '۱۴۰۲۰۲', 
                specialty: 'فیزیک',
                grades: ['11', '12'],
                subjects: ['physics'],
                type: 'teacher'
            },
            { 
                username: '140203', 
                password: '1234', 
                name: 'علی محمدی',
                personalCode: '۱۴۰۲۰۳',
                specialty: 'ادبیات',
                grades: ['10', '11', '12'],
                subjects: ['literature'],
                type: 'teacher'
            },
            { 
                username: '140200', 
                password: '1234', 
                name: 'مدیریت سیستم',
                personalCode: '۱۴۰۲۰۰',
                specialty: 'مدیریت',
                grades: ['all'],
                subjects: ['all'],
                type: 'admin'
            }
        ];

        let currentTeacher = null;

        // بارگذاری داده‌ها از localStorage
        let classes = JSON.parse(localStorage.getItem('imamHusseinClasses')) || [];
        let students = JSON.parse(localStorage.getItem('imamHusseinStudents')) || [];
        let grades = JSON.parse(localStorage.getItem('imamHusseinGrades')) || [];
        let savedTeachers = JSON.parse(localStorage.getItem('imamHusseinTeachers'));

        // اگر داده‌های معلمین در localStorage وجود دارد، از آن استفاده کن
        if (savedTeachers) {
            teachers = savedTeachers;
        }

        // ذخیره داده‌ها
        function saveAllData() {
            localStorage.setItem('imamHusseinClasses', JSON.stringify(classes));
            localStorage.setItem('imamHusseinStudents', JSON.stringify(students));
            localStorage.setItem('imamHusseinGrades', JSON.stringify(grades));
            localStorage.setItem('imamHusseinTeachers', JSON.stringify(teachers));
        }

        // لاگین
        document.getElementById('loginForm').addEventListener('submit', function(e) {
            e.preventDefault();
            
            const username = document.getElementById('username').value;
            const password = document.getElementById('password').value;
            
            const teacher = teachers.find(t => t.username === username && t.password === password);
            
            if (teacher) {
                currentTeacher = teacher;
                document.getElementById('loginPage').style.display = 'none';
                document.getElementById('dashboard').style.display = 'block';
                document.getElementById('teacherName').textContent = teacher.name;
                document.getElementById('teacherSpecialty').textContent = teacher.specialty;
                document.getElementById('gradeSubject').value = teacher.specialty;
                
                // نمایش پنل مدیریت فقط برای مدیر
                if (teacher.type === 'admin') {
                    document.getElementById('adminPanel').style.display = 'block';
                    document.getElementById('classManagementPanel').style.display = 'block';
                    document.getElementById('studentManagementPanel').style.display = 'block';
                    loadTeacherList();
                } else {
                    document.getElementById('classManagementPanel').style.display = 'none';
                    document.getElementById('studentManagementPanel').style.display = 'none';
                }
                
                loadTeacherInfo();
                loadDashboard();
            } else {
                alert('کد پرسنلی یا رمز عبور اشتباه است!');
            }
        });

        // ثبت معلم جدید
        document.getElementById('teacherForm').addEventListener('submit', function(e) {
            e.preventDefault();
            
            const username = document.getElementById('teacherUsername').value;
            const password = document.getElementById('teacherPassword').value;
            const name = document.getElementById('teacherNameInput').value;
            const specialty = document.getElementById('teacherSpecialtyInput').value;
            
            // بررسی تکراری نبودن کد پرسنلی
            if (teachers.find(t => t.username === username)) {
                alert('این کد پرسنلی قبلاً ثبت شده است!');
                return;
            }
            
            // جمع‌آوری پایه‌های مجاز
            const selectedGrades = [];
            if (document.getElementById('grade10').checked) selectedGrades.push('10');
            if (document.getElementById('grade11').checked) selectedGrades.push('11');
            if (document.getElementById('grade12').checked) selectedGrades.push('12');
            if (document.getElementById('gradeAll').checked) selectedGrades.push('all');
            
            if (selectedGrades.length === 0) {
                alert('حداقل یک پایه باید انتخاب شود!');
                return;
            }
            
            // ایجاد معلم جدید
            const newTeacher = {
                username: username,
                password: password,
                name: name,
                personalCode: username,
                specialty: specialty,
                grades: selectedGrades,
                subjects: [specialty],
                type: 'teacher'
            };
            
            teachers.push(newTeacher);
            
            // پاک کردن فرم
            document.getElementById('teacherForm').reset();
            
            saveAllData();
            loadTeacherList();
            
            alert(`معلم ${name} با موفقیت ثبت شد!\nکد پرسنلی: ${username}\nرمز عبور: ${password}`);
        });

        // بارگذاری لیست معلمین
        function loadTeacherList() {
            const teacherList = document.getElementById('teacherList');
            teacherList.innerHTML = '';
            
            const regularTeachers = teachers.filter(t => t.type === 'teacher');
            
            if (regularTeachers.length === 0) {
                teacherList.innerHTML = '<div class="alert alert-info text-center">هنوز معلمی ثبت نشده است</div>';
                return;
            }
            
            regularTeachers.forEach(teacher => {
                const teacherElement = document.createElement('div');
                teacherElement.className = 'alert alert-secondary d-flex justify-content-between align-items-center mb-2';
                teacherElement.innerHTML = `
                    <div>
                        <strong>${teacher.name}</strong>
                        <br>
                        <small>کد: ${teacher.personalCode} | تخصص: ${teacher.specialty}</small>
                        <br>
                        <small>پایه‌ها: ${teacher.grades.map(g => getGradeName(g)).join('، ')}</small>
                    </div>
                    <button class="btn btn-sm btn-danger" onclick="deleteTeacher('${teacher.username}')">
                        <i class="bi bi-trash"></i>
                    </button>
                `;
                teacherList.appendChild(teacherElement);
            });
        }

        // حذف معلم
        function deleteTeacher(username) {
            if (confirm('آیا از حذف این معلم مطمئن هستید؟')) {
                teachers = teachers.filter(t => t.username !== username);
                saveAllData();
                loadTeacherList();
            }
        }

        // نمایش اطلاعات معلم
        function loadTeacherInfo() {
            const teacherInfo = document.getElementById('teacherInfo');
            teacherInfo.innerHTML = `
                <div class="text-center">
                    <div class="fw-bold" style="color: var(--moe-blue);">${currentTeacher.name}</div>
                    <div class="text-muted">کد پرسنلی: ${currentTeacher.personalCode}</div>
                    <div class="mt-2">
                        <span class="subject-badge">${currentTeacher.specialty}</span>
                    </div>
                    <div class="mt-2">
                        <small class="text-muted">پایه‌های مجاز:</small><br>
                        ${currentTeacher.grades.map(grade => 
                            `<span class="badge bg-secondary me-1">${getGradeName(grade)}</span>`
                        ).join('')}
                    </div>
                </div>
            `;
        }

        // ایجاد کلاس جدید (فقط مدیر)
        document.getElementById('classForm').addEventListener('submit', function(e) {
            e.preventDefault();
            
            const gradeLevel = document.getElementById('gradeLevel').value;
            const field = document.getElementById('field').value;
            const className = document.getElementById('className').value;
            
            const classId = Date.now().toString();
            const fieldName = getFieldName(field);
            const gradeName = getGradeName(gradeLevel);
            
            // ایجاد کلاس اصلی (بدون teacherId خاص)
            classes.push({
                id: classId,
                grade: gradeLevel,
                gradeName: gradeName,
                field: field,
                fieldName: fieldName,
                name: className,
                fullName: `پایه ${gradeName} - ${fieldName} - کلاس ${className}`,
                createdBy: currentTeacher.username
            });
            
            // پاک کردن فرم
            document.getElementById('gradeLevel').value = '';
            document.getElementById('field').value = '';
            document.getElementById('className').value = '';
            
            saveAllData();
            loadClasses();
            loadStudentClassSelect();
            loadGradeClassSelect();
            
            alert(`کلاس ${className} با موفقیت ایجاد شد و برای همه معلم‌ها قابل دسترس است`);
        });

        // ثبت دانش‌آموز جدید (فقط مدیر)
        document.getElementById('studentForm').addEventListener('submit', function(e) {
            e.preventDefault();
            
            const firstName = document.getElementById('studentFirstName').value;
            const lastName = document.getElementById('studentLastName').value;
            const nationalCode = document.getElementById('studentNationalCode').value;
            const studentId = document.getElementById('studentId').value;
            const birthDate = document.getElementById('studentBirthDate').value;
            const classId = document.getElementById('studentClass').value;
            
            const selectedClass = classes.find(c => c.id === classId);
            
            students.push({
                id: Date.now().toString(),
                firstName: firstName,
                lastName: lastName,
                nationalCode: nationalCode,
                studentId: studentId,
                birthDate: birthDate,
                classId: classId,
                className: selectedClass.fullName,
                grade: selectedClass.grade,
                field: selectedClass.field,
                createdBy: currentTeacher.username
            });
            
            // پاک کردن فرم
            document.getElementById('studentFirstName').value = '';
            document.getElementById('studentLastName').value = '';
            document.getElementById('studentNationalCode').value = '';
            document.getElementById('studentId').value = '';
            document.getElementById('studentBirthDate').value = '';
            
            saveAllData();
            loadStudents();
            loadGradeClassSelect();
            
            alert(`دانش‌آموز ${firstName} ${lastName} با موفقیت ثبت شد`);
        });

        // بارگذاری انتخاب کلاس برای نمره‌دهی
        function loadGradeClassSelect() {
            const select = document.getElementById('gradeClass');
            select.innerHTML = '<option value="">انتخاب کلاس</option>';
            
            // همه کلاس‌ها برای همه معلم‌ها قابل دسترس است
            classes.forEach(classItem => {
                const option = document.createElement('option');
                option.value = classItem.id;
                option.textContent = classItem.fullName;
                select.appendChild(option);
            });
        }

        // بارگذاری دانش‌آموزان کلاس برای ثبت نمره
        function loadClassStudentsForGrades() {
            const classId = document.getElementById('gradeClass').value;
            const table = document.getElementById('classStudentsGradesTable');
            const list = document.getElementById('classStudentsGradesList');
            
            if (!classId) {
                table.style.display = 'none';
                return;
            }
            
            const classStudents = students.filter(s => s.classId === classId);
            const term = document.getElementById('gradeTerm').value;
            
            list.innerHTML = '';
            
            if (classStudents.length === 0) {
                list.innerHTML = '<tr><td colspan="5" class="text-center py-4">هیچ دانش‌آموزی در این کلاس ثبت نشده است</td></tr>';
                table.style.display = 'block';
                return;
            }
            
            classStudents.forEach((student, index) => {
                const existingGrade = grades.find(g => 
                    g.studentId === student.id && 
                    g.subject === currentTeacher.specialty && 
                    g.term === term
                );
                
                const row = document.createElement('tr');
                row.innerHTML = `
                    <td>${index + 1}</td>
                    <td>${student.studentId}</td>
                    <td>${student.firstName} ${student.lastName}</td>
                    <td class="text-center">${existingGrade ? existingGrade.grade : '-'}</td>
                    <td>
                        <input type="number" 
                               min="0" 
                               max="20" 
                               step="0.25" 
                               class="form-control form-control-sm text-center grade-input" 
                               data-student-id="${student.id}"
                               value="${existingGrade ? existingGrade.grade : ''}"
                               placeholder="0-20">
                    </td>
                `;
                list.appendChild(row);
            });
            
            table.style.display = 'block';
        }

        // ذخیره همه نمرات
        function saveAllGrades() {
            const classId = document.getElementById('gradeClass').value;
            const term = document.getElementById('gradeTerm').value;
            
            if (!classId) {
                alert('لطفاً ابتدا یک کلاس انتخاب کنید!');
                return;
            }
            
            const gradeInputs = document.querySelectorAll('.grade-input');
            let savedCount = 0;
            let errorCount = 0;
            
            gradeInputs.forEach(input => {
                const studentId = input.getAttribute('data-student-id');
                const gradeValue = parseFloat(input.value);
                
                if (!isNaN(gradeValue) && gradeValue >= 0 && gradeValue <= 20) {
                    // حذف نمره قبلی اگر وجود دارد
                    grades = grades.filter(g => 
                        !(g.studentId === studentId && 
                          g.subject === currentTeacher.specialty && 
                          g.term === term)
                    );
                    
                    // اضافه کردن نمره جدید
                    grades.push({
                        id: Date.now().toString() + Math.random(),
                        studentId: studentId,
                        subject: currentTeacher.specialty,
                        grade: gradeValue,
                        term: term,
                        teacher: currentTeacher.name,
                        date: new Date().toLocaleDateString('fa-IR')
                    });
                    
                    savedCount++;
                } else if (input.value.trim() !== '') {
                    errorCount++;
                }
            });
            
            saveAllData();
            
            if (errorCount > 0) {
                alert(`${savedCount} نمره ذخیره شد! ${errorCount} نمره نامعتبر بود.`);
            } else {
                alert(`${savedCount} نمره با موفقیت ذخیره شد!`);
            }
            
            // بروزرسانی نمایش
            loadClassStudentsForGrades();
        }

        // بارگذاری داشبورد
        function loadDashboard() {
            loadClasses();
            loadStudents();
            loadStudentClassSelect();
            loadGradeClassSelect();
        }

        // بارگذاری کلاس‌ها
        function loadClasses() {
            const classList = document.getElementById('classList');
            classList.innerHTML = '';
            
            if (classes.length === 0) {
                classList.innerHTML = '<div class="alert alert-info text-center">هنوز کلاسی ایجاد نشده است</div>';
                return;
            }
            
            classes.forEach(classItem => {
                const classElement = document.createElement('div');
                classElement.className = 'alert alert-secondary mb-2';
                classElement.innerHTML = `
                    <div class="d-flex justify-content-between align-items-center">
                        <div>
                            <strong>${classItem.fullName}</strong>
                            <br>
                            <small>تعداد دانش‌آموزان: ${students.filter(s => s.classId === classItem.id).length} نفر</small>
                        </div>
                        <button class="btn btn-sm btn-danger" onclick="deleteClass('${classItem.id}')">
                            <i class="bi bi-trash"></i>
                        </button>
                    </div>
                `;
                classList.appendChild(classElement);
            });
        }

        // بارگذاری دانش‌آموزان
        function loadStudents() {
            const studentList = document.getElementById('studentList');
            studentList.innerHTML = '';
            
            if (students.length === 0) {
                studentList.innerHTML = '<tr><td colspan="6" class="text-center py-4">هنوز دانش‌آموزی ثبت نشده است</td></tr>';
                return;
            }
            
            students.forEach((student, index) => {
                const row = document.createElement('tr');
                row.innerHTML = `
                    <td>${index + 1}</td>
                    <td>${student.studentId}</td>
                    <td>${student.firstName} ${student.lastName}</td>
                    <td>${student.nationalCode}</td>
                    <td>${student.className}</td>
                    <td>
                        <button class="btn btn-sm btn-info" onclick="viewStudentReport('${student.id}')">
                            <i class="bi bi-eye"></i> مشاهده کارنامه
                        </button>
                        <button class="btn btn-sm btn-danger" onclick="deleteStudent('${student.id}')">
                            <i class="bi bi-trash"></i> حذف
                        </button>
                    </td>
                `;
                studentList.appendChild(row);
            });
        }

        // بارگذاری انتخاب کلاس برای ثبت دانش‌آموز
        function loadStudentClassSelect() {
            const select = document.getElementById('studentClass');
            select.innerHTML = '<option value="">انتخاب کلاس</option>';
            
            classes.forEach(classItem => {
                const option = document.createElement('option');
                option.value = classItem.id;
                option.textContent = classItem.fullName;
                select.appendChild(option);
            });
        }

        // مشاهده کارنامه دانش‌آموز
        function viewStudentReport(studentId) {
            const student = students.find(s => s.id === studentId);
            if (!student) {
                alert('دانش‌آموز پیدا نشد!');
                return;
            }
            
            const studentGrades = grades.filter(g => g.studentId === studentId);
            const reportCards = document.getElementById('reportCards');
            
            // گروه‌بندی نمرات بر اساس درس و ترم
            const subjectGrades = {};
            
            studentGrades.forEach(grade => {
                if (!subjectGrades[grade.subject]) {
                    subjectGrades[grade.subject] = {};
                }
                subjectGrades[grade.subject][grade.term] = grade.grade;
            });
            
            let reportHTML = `
                <div class="report-card-official" id="report-${student.id}">
                    <div class="report-header">
                        <h4>کارنامه تحصیلی</h4>
                        <h5>مدرسه نمونه دولتی امام حسین (ع)</h5>
                        <div class="mt-3">
                            <span class="badge bg-warning">پایه ${getGradeName(student.grade)} - ${getFieldName(student.field)}</span>
                        </div>
                    </div>
                    
                    <div class="student-info-section">
                        <div class="row">
                            <div class="col-md-6">
                                <strong>نام و نام خانوادگی:</strong> ${student.firstName} ${student.lastName}
                            </div>
                            <div class="col-md-6">
                                <strong>شماره دانش‌آموزی:</strong> ${student.studentId}
                            </div>
                            <div class="col-md-6">
                                <strong>کد ملی:</strong> ${student.nationalCode}
                            </div>
                            <div class="col-md-6">
                                <strong>تاریخ تولد:</strong> ${new Date(student.birthDate).toLocaleDateString('fa-IR')}
                            </div>
                            <div class="col-md-6">
                                <strong>کلاس:</strong> ${student.className}
                            </div>
                        </div>
                    </div>
                    
                    <div class="grades-table-section">
                        <h6 class="text-center mb-3">نمرات تحصیلی</h6>
                        <div class="table-responsive">
                            <table class="official-table">
                                <thead>
                                    <tr>
                                        <th>ردیف</th>
                                        <th>نام درس</th>
                                        <th>نوبت اول</th>
                                        <th>نوبت دوم</th>
                                        <th>معدل</th>
                                        <th>وضعیت</th>
                                    </tr>
                                </thead>
                                <tbody>
            `;
            
            let rowNumber = 1;
            let totalSum = 0;
            let subjectCount = 0;
            
            // لیست همه دروس ممکن
            const allSubjects = ['ریاضی', 'فیزیک', 'شیمی', 'ادبیات', 'زبان انگلیسی', 'عربی', 'دین و زندگی', 'تاریخ', 'جغرافیا'];
            
            allSubjects.forEach(subject => {
                if (subjectGrades[subject]) {
                    const grade1 = subjectGrades[subject]['1'] || '-';
                    const grade2 = subjectGrades[subject]['2'] || '-';
                    
                    let average = '-';
                    let status = '-';
                    let rowClass = '';
                    
                    if (grade1 !== '-' && grade2 !== '-') {
                        average = ((grade1 + grade2) / 2).toFixed(2);
                        totalSum += parseFloat(average);
                        subjectCount++;
                        
                        if (average >= 17) {
                            status = 'عالی';
                            rowClass = 'grade-excellent';
                        } else if (average >= 12) {
                            status = 'قبول';
                            rowClass = 'grade-good';
                        } else {
                            status = 'مردود';
                            rowClass = 'grade-weak';
                        }
                    } else if (grade1 !== '-') {
                        average = grade1;
                        status = 'ناقص';
                    } else if (grade2 !== '-') {
                        average = grade2;
                        status = 'ناقص';
                    }
                    
                    reportHTML += `
                        <tr class="${rowClass}">
                            <td>${rowNumber}</td>
                            <td>${subject}</td>
                            <td>${grade1}</td>
                            <td>${grade2}</td>
                            <td>${average}</td>
                            <td>${status}</td>
                        </tr>
                    `;
                    rowNumber++;
                }
            });
            
            const overallAverage = subjectCount > 0 ? (totalSum / subjectCount).toFixed(2) : '-';
            
            reportHTML += `
                                </tbody>
                            </table>
                        </div>
                        
                        <div class="row mt-4">
                            <div class="col-md-6">
                                <div class="alert alert-info">
                                    <strong>معدل کل:</strong> ${overallAverage}
                                </div>
                            </div>
                            <div class="col-md-6 text-end">
                                <button class="btn btn-moe" onclick="printReportCard('${student.id}')">
                                    <i class="bi bi-printer"></i> چاپ کارنامه
                                </button>
                                <button class="btn btn-danger ms-2" onclick="removeReportCard('${student.id}')">
                                    <i class="bi bi-x-circle"></i> حذف
                                </button>
                            </div>
                        </div>
                        
                        <div class="official-stamp">
                            <div>مهر و امضای مدیر مدرسه</div>
                            <div>مدرسه نمونه دولتی امام حسین (ع)</div>
                            <div>${new Date().toLocaleDateString('fa-IR')}</div>
                        </div>
                    </div>
                </div>
            `;
            
            // اضافه کردن کارنامه جدید به ابتدای لیست
            reportCards.innerHTML = reportHTML + reportCards.innerHTML;
            
            alert(`کارنامه ${student.firstName} ${student.lastName} نمایش داده شد`);
        }

        // حذف یک کارنامه
        function removeReportCard(studentId) {
            const reportCard = document.getElementById(`report-${studentId}`);
            if (reportCard) {
                reportCard.remove();
            }
        }

        // پاک کردن همه کارنامه‌ها
        function clearAllReportCards() {
            if (confirm('آیا از پاک کردن همه کارنامه‌های نمایش داده شده مطمئن هستید؟')) {
                document.getElementById('reportCards').innerHTML = '';
            }
        }

        // چاپ کارنامه
        function printReportCard(studentId) {
            const reportCard = document.getElementById(`report-${studentId}`);
            if (!reportCard) {
                alert('کارنامه پیدا نشد!');
                return;
            }
            
            const originalDisplay = reportCard.style.display;
            const originalReportsDisplay = document.getElementById('reportCards').style.display;
            
            // مخفی کردن بقیه عناصر
            document.querySelectorAll('.report-card-official').forEach(card => {
                if (card.id !== `report-${studentId}`) {
                    card.style.display = 'none';
                }
            });
            
            reportCard.style.display = 'block';
            window.print();
            
            // بازگرداندن نمایش به حالت اولیه
            document.querySelectorAll('.report-card-official').forEach(card => {
                card.style.display = 'block';
            });
        }

        // تولید همه کارنامه‌ها
        function generateAllReportCards() {
            const reportCards = document.getElementById('reportCards');
            
            if (students.length === 0) {
                alert('هیچ دانش‌آموزی برای نمایش کارنامه وجود ندارد');
                return;
            }
            
            // پاک کردن کارنامه‌های قبلی
            reportCards.innerHTML = '';
            
            students.forEach(student => {
                viewStudentReport(student.id);
            });
            
            alert(`کارنامه‌های ${students.length} دانش‌آموز تولید شد`);
        }

        // حذف دانش‌آموز
        function deleteStudent(studentId) {
            if (confirm('آیا از حذف این دانش‌آموز مطمئن هستید؟')) {
                students = students.filter(s => s.id !== studentId);
                // حذف نمرات مربوط به این دانش‌آموز
                grades = grades.filter(g => g.studentId !== studentId);
                saveAllData();
                loadStudents();
                loadGradeClassSelect();
            }
        }

        // حذف کلاس
        function deleteClass(classId) {
            if (confirm('آیا از حذف این کلاس مطمئن هستید؟ تمام دانش‌آموزان و نمرات مربوطه نیز حذف خواهند شد.')) {
                // حذف کلاس
                classes = classes.filter(c => c.id !== classId);
                // حذف دانش‌آموزان این کلاس
                const studentsToDelete = students.filter(s => s.classId === classId);
                students = students.filter(s => s.classId !== classId);
                // حذف نمرات دانش‌آموزان حذف شده
                studentsToDelete.forEach(student => {
                    grades = grades.filter(g => g.studentId !== student.id);
                });
                
                saveAllData();
                loadClasses();
                loadStudents();
                loadStudentClassSelect();
                loadGradeClassSelect();
            }
        }

        // خروج از سیستم
        function logout() {
            if (confirm('آیا می‌خواهید از سیستم خارج شوید؟')) {
                currentTeacher = null;
                document.getElementById('dashboard').style.display = 'none';
                document.getElementById('loginPage').style.display = 'block';
                document.getElementById('loginForm').reset();
            }
        }

        // توابع کمکی
        function getGradeName(grade) {
            const grades = {
                '10': 'دهم',
                '11': 'یازدهم', 
                '12': 'دوازدهم',
                'all': 'همه'
            };
            return grades[grade] || grade;
        }

        function getFieldName(field) {
            const fields = {
                'riazi': 'ریاضی فیزیک',
                'tajrobi': 'علوم تجربی',
                'ensani': 'علوم انسانی'
            };
            return fields[field] || field;
        }

        // مقداردهی اولیه
        window.onload = function() {
            // بارگذاری اولیه داده‌ها
            loadStudentClassSelect();
        };
    </script>
</body>
</html>
