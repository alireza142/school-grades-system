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

        .pdf-section {
            background: linear-gradient(135deg, #e3f2fd, #bbdefb);
            border: 2px solid var(--moe-blue);
            border-radius: 8px;
            padding: 20px;
            margin-bottom: 20px;
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
                    <i class="bi bi-geo-alt-fill"></i> استان خراسان رضوی - شهرستان مشهد
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

        <!-- بخش خروجی PDF -->
        <div class="pdf-section">
            <h5 class="text-center mb-4" style="color: var(--moe-blue); font-family: 'B Nazanin';">
                <i class="bi bi-file-earmark-pdf"></i> سیستم تولید کارنامه PDF
            </h5>
            
            <div class="row g-3">
                <!-- خروجی برای دانش‌آموز خاص -->
                <div class="col-md-6">
                    <div class="card card-moe">
                        <div class="card-header card-header-moe">
                            <h6 class="mb-0"><i class="bi bi-person"></i> کارنامه فردی</h6>
                        </div>
                        <div class="card-body">
                            <div class="mb-3">
                                <label class="form-label">انتخاب دانش‌آموز</label>
                                <select class="form-select" id="singleStudentSelect" style="font-family: 'B Nazanin';">
                                    <option value="">انتخاب دانش‌آموز</option>
                                </select>
                            </div>
                            <button class="btn btn-moe w-100" onclick="generateSinglePDF()">
                                <i class="bi bi-download"></i> تولید کارنامه فردی (PDF)
                            </button>
                        </div>
                    </div>
                </div>

                <!-- خروجی برای کل کلاس -->
                <div class="col-md-6">
                    <div class="card card-moe">
                        <div class="card-header card-header-moe">
                            <h6 class="mb-0"><i class="bi bi-people"></i> کارنامه گروهی</h6>
                        </div>
                        <div class="card-body">
                            <div class="mb-3">
                                <label class="form-label">انتخاب کلاس</label>
                                <select class="form-select" id="classSelect" style="font-family: 'B Nazanin';">
                                    <option value="">انتخاب کلاس</option>
                                </select>
                            </div>
                            <button class="btn btn-success w-100" onclick="generateClassPDF()">
                                <i class="bi bi-download"></i> تولید کارنامه کل کلاس (PDF)
                            </button>
                        </div>
                    </div>
                </div>

                <!-- خروجی برای همه دانش‌آموزان -->
                <div class="col-12">
                    <div class="card card-moe">
                        <div class="card-header card-header-moe">
                            <h6 class="mb-0"><i class="bi bi-collection"></i> کارنامه کامل</h6>
                        </div>
                        <div class="card-body">
                            <div class="row">
                                <div class="col-md-8">
                                    <p class="mb-0">تولید کارنامه PDF برای تمامی دانش‌آموزان مدرسه</p>
                                    <small class="text-muted">تعداد دانش‌آموزان: <span id="totalStudentsCount">0</span> نفر</small>
                                </div>
                                <div class="col-md-4 text-end">
                                    <button class="btn btn-warning w-100" onclick="generateAllPDF()">
                                        <i class="bi bi-download"></i> تولید همه کارنامه‌ها (PDF)
                                    </button>
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
                <div id="classManagementPanel" class="card card-moe" style="display: none;">
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
                <div id="studentManagementPanel" class="card card-moe mb-3" style="display: none;">
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
    </div>

    <!-- بارگذاری کتابخانه‌ها در انتهای صفحه -->
    <script src="https://cdn.jsdelivr.net/npm/bootstrap@5.1.3/dist/js/bootstrap.bundle.min.js"></script>
    <script src="https://cdnjs.cloudflare.com/ajax/libs/jspdf/2.5.1/jspdf.umd.min.js"></script>
    <script src="https://cdnjs.cloudflare.com/ajax/libs/jspdf-autotable/3.5.28/jspdf.plugin.autotable.min.js"></script>
    
    <script>
        // داده‌های اولیه
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
        let classes = JSON.parse(localStorage.getItem('imamHusseinClasses')) || [];
        let students = JSON.parse(localStorage.getItem('imamHusseinStudents')) || [];
        let grades = JSON.parse(localStorage.getItem('imamHusseinGrades')) || [];
        let savedTeachers = JSON.parse(localStorage.getItem('imamHusseinTeachers'));

        if (savedTeachers) {
            teachers = savedTeachers;
        }

        // توابع اصلی
        function saveAllData() {
            localStorage.setItem('imamHusseinClasses', JSON.stringify(classes));
            localStorage.setItem('imamHusseinStudents', JSON.stringify(students));
            localStorage.setItem('imamHusseinGrades', JSON.stringify(grades));
            localStorage.setItem('imamHusseinTeachers', JSON.stringify(teachers));
        }

        // سیستم لاگین
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
                
                // تنظیم دسترسی‌ها - فقط مدیر به پنل مدیریت دسترسی دارد
                if (teacher.type === 'admin') {
                    document.getElementById('adminPanel').style.display = 'block';
                    document.getElementById('classManagementPanel').style.display = 'block';
                    document.getElementById('studentManagementPanel').style.display = 'block';
                    loadTeacherList();
                } else {
                    document.getElementById('adminPanel').style.display = 'none';
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
            console.log('ثبت معلم جدید فراخوانی شد');
            
            const username = document.getElementById('teacherUsername').value;
            const password = document.getElementById('teacherPassword').value;
            const name = document.getElementById('teacherNameInput').value;
            const specialty = document.getElementById('teacherSpecialtyInput').value;
            
            if (!username || !password || !name || !specialty) {
                alert('لطفاً تمام فیلدها را پر کنید!');
                return;
            }
            
            if (teachers.find(t => t.username === username)) {
                alert('این کد پرسنلی قبلاً ثبت شده است!');
                return;
            }
            
            const selectedGrades = [];
            if (document.getElementById('grade10').checked) selectedGrades.push('10');
            if (document.getElementById('grade11').checked) selectedGrades.push('11');
            if (document.getElementById('grade12').checked) selectedGrades.push('12');
            if (document.getElementById('gradeAll').checked) selectedGrades.push('all');
            
            if (selectedGrades.length === 0) {
                alert('حداقل یک پایه باید انتخاب شود!');
                return;
            }
            
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
            document.getElementById('teacherForm').reset();
            saveAllData();
            loadTeacherList();
            
            alert(`معلم ${name} با موفقیت ثبت شد!\nکد پرسنلی: ${username}\nرمز عبور: ${password}`);
        });

        // ایجاد کلاس جدید
        document.getElementById('classForm').addEventListener('submit', function(e) {
            e.preventDefault();
            console.log('ایجاد کلاس جدید فراخوانی شد');
            
            const gradeLevel = document.getElementById('gradeLevel').value;
            const field = document.getElementById('field').value;
            const className = document.getElementById('className').value;
            
            if (!gradeLevel || !field || !className) {
                alert('لطفاً تمام فیلدها را پر کنید!');
                return;
            }
            
            const classId = Date.now().toString();
            const fieldName = getFieldName(field);
            const gradeName = getGradeName(gradeLevel);
            
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
            
            document.getElementById('classForm').reset();
            saveAllData();
            loadClasses();
            loadStudentClassSelect();
            loadGradeClassSelect();
            loadPDFSelects();
            
            alert(`کلاس ${className} با موفقیت ایجاد شد!`);
        });

        // ثبت دانش‌آموز جدید
        document.getElementById('studentForm').addEventListener('submit', function(e) {
            e.preventDefault();
            console.log('ثبت دانش‌آموز جدید فراخوانی شد');
            
            const firstName = document.getElementById('studentFirstName').value;
            const lastName = document.getElementById('studentLastName').value;
            const nationalCode = document.getElementById('studentNationalCode').value;
            const studentId = document.getElementById('studentId').value;
            const birthDate = document.getElementById('studentBirthDate').value;
            const classId = document.getElementById('studentClass').value;
            
            if (!firstName || !lastName || !nationalCode || !studentId || !birthDate || !classId) {
                alert('لطفاً تمام فیلدها را پر کنید!');
                return;
            }
            
            const selectedClass = classes.find(c => c.id === classId);
            if (!selectedClass) {
                alert('کلاس انتخاب شده معتبر نیست!');
                return;
            }
            
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
            
            document.getElementById('studentForm').reset();
            saveAllData();
            loadStudents();
            loadPDFSelects();
            
            alert(`دانش‌آموز ${firstName} ${lastName} با موفقیت ثبت شد!`);
        });

        // بارگذاری داشبورد
        function loadDashboard() {
            loadClasses();
            loadStudents();
            loadStudentClassSelect();
            loadGradeClassSelect();
            loadPDFSelects();
        }

        // بارگذاری انتخاب‌های PDF
        function loadPDFSelects() {
            const singleSelect = document.getElementById('singleStudentSelect');
            const classSelect = document.getElementById('classSelect');
            
            singleSelect.innerHTML = '<option value="">انتخاب دانش‌آموز</option>';
            students.forEach(student => {
                const option = document.createElement('option');
                option.value = student.id;
                option.textContent = `${student.firstName} ${student.lastName} - ${student.className}`;
                singleSelect.appendChild(option);
            });
            
            classSelect.innerHTML = '<option value="">انتخاب کلاس</option>';
            classes.forEach(classItem => {
                const option = document.createElement('option');
                option.value = classItem.id;
                option.textContent = classItem.fullName;
                classSelect.appendChild(option);
            });
            
            document.getElementById('totalStudentsCount').textContent = students.length;
        }

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
                    </div>
                    <button class="btn btn-sm btn-danger" onclick="deleteTeacher('${teacher.username}')">
                        <i class="bi bi-trash"></i>
                    </button>
                `;
                teacherList.appendChild(teacherElement);
            });
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

        // بارگذاری انتخاب کلاس برای نمره‌دهی
        function loadGradeClassSelect() {
            const select = document.getElementById('gradeClass');
            select.innerHTML = '<option value="">انتخاب کلاس</option>';
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

        // تولید PDF برای یک دانش‌آموز
        function generateSinglePDF() {
            try {
                const studentId = document.getElementById('singleStudentSelect').value;
                if (!studentId) {
                    alert('لطفاً یک دانش‌آموز انتخاب کنید!');
                    return;
                }
                
                const student = students.find(s => s.id === studentId);
                if (!student) {
                    alert('دانش‌آموز پیدا نشد!');
                    return;
                }

                const { jsPDF } = window.jspdf;
                const doc = new jsPDF();
                
                // اضافه کردن فونت فارسی (استفاده از فونت استاندارد)
                doc.setFont('helvetica');
                
                // هدر کارنامه - طراحی رسمی
                doc.setFillColor(30, 58, 138);
                doc.rect(0, 0, 210, 40, 'F');
                doc.setTextColor(255, 255, 255);
                doc.setFontSize(18);
                doc.text('کارنامه تحصیلی', 105, 15, { align: 'center' });
                doc.setFontSize(12);
                doc.text('مدرسه نمونه دولتی امام حسین (ع)', 105, 25, { align: 'center' });
                doc.setFontSize(10);
                doc.text('سال تحصیلی ۱۴۰۳-۱۴۰۴', 105, 32, { align: 'center' });
                
                // اطلاعات دانش‌آموز - جدول بندی شده
                doc.setTextColor(0, 0, 0);
                doc.setFontSize(11);
                
                // ایجاد جدول اطلاعات دانش‌آموز
                const studentInfo = [
                    ['نام و نام خانوادگی:', student.firstName + ' ' + student.lastName],
                    ['شماره دانش‌آموزی:', student.studentId],
                    ['کد ملی:', student.nationalCode],
                    ['کلاس:', student.className],
                    ['تاریخ تولد:', new Date(student.birthDate).toLocaleDateString('fa-IR')]
                ];
                
                let y = 50;
                studentInfo.forEach(([label, value]) => {
                    doc.setFillColor(240, 240, 240);
                    doc.rect(20, y, 170, 8, 'F');
                    doc.setTextColor(0, 0, 0);
                    doc.text(label, 25, y + 5);
                    doc.text(value, 120, y + 5);
                    y += 10;
                });
                
                y += 10;
                
                // جدول نمرات - طراحی رسمی
                const studentGrades = grades.filter(g => g.studentId === studentId);
                const subjectGrades = {};
                
                studentGrades.forEach(grade => {
                    if (!subjectGrades[grade.subject]) {
                        subjectGrades[grade.subject] = {};
                    }
                    subjectGrades[grade.subject][grade.term] = grade.grade;
                });
                
                // دروس مختلف
                const subjects = [
                    'ریاضی', 'فیزیک', 'شیمی', 'ادبیات فارسی', 
                    'زبان انگلیسی', 'عربی', 'دین و زندگی', 
                    'تاریخ', 'جغرافیا', 'هنر', 'تربیت بدنی'
                ];
                
                // ایجاد جدول نمرات
                const tableData = [];
                let totalSum = 0;
                let subjectCount = 0;
                
                subjects.forEach(subject => {
                    const grade1 = subjectGrades[subject]?.['1'] || '-';
                    const grade2 = subjectGrades[subject]?.['2'] || '-';
                    
                    let average = '-';
                    let status = '-';
                    
                    if (grade1 !== '-' && grade2 !== '-') {
                        average = ((grade1 + grade2) / 2).toFixed(2);
                        totalSum += parseFloat(average);
                        subjectCount++;
                        
                        if (average >= 17) status = 'عالی';
                        else if (average >= 15) status = 'خیلی خوب';
                        else if (average >= 12) status = 'خوب';
                        else if (average >= 10) status = 'قابل قبول';
                        else status = 'نیاز به تلاش';
                    }
                    
                    tableData.push([
                        subject,
                        grade1.toString(),
                        grade2.toString(),
                        average,
                        status
                    ]);
                });
                
                // سرستون جدول
                doc.setFillColor(30, 58, 138);
                doc.rect(10, y, 190, 10, 'F');
                doc.setTextColor(255, 255, 255);
                doc.text('ردیف', 25, y + 6);
                doc.text('نام درس', 60, y + 6);
                doc.text('نوبت اول', 120, y + 6);
                doc.text('نوبت دوم', 150, y + 6);
                doc.text('معدل', 170, y + 6);
                doc.text('وضعیت', 190, y + 6);
                
                y += 10;
                
                // محتوای جدول
                doc.setTextColor(0, 0, 0);
                tableData.forEach((row, index) => {
                    if (y > 250) {
                        doc.addPage();
                        y = 20;
                    }
                    
                    // رنگ‌آمیزی سطرها
                    if (index % 2 === 0) {
                        doc.setFillColor(245, 245, 245);
                    } else {
                        doc.setFillColor(255, 255, 255);
                    }
                    doc.rect(10, y, 190, 8, 'F');
                    
                    doc.text((index + 1).toString(), 25, y + 5);
                    doc.text(row[0], 60, y + 5);
                    doc.text(row[1], 120, y + 5);
                    doc.text(row[2], 150, y + 5);
                    doc.text(row[3], 170, y + 5);
                    doc.text(row[4], 190, y + 5);
                    
                    y += 8;
                });
                
                y += 10;
                
                // محاسبه معدل کل
                const overallAverage = subjectCount > 0 ? (totalSum / subjectCount).toFixed(2) : '0.00';
                
                // نمایش معدل کل
                doc.setFillColor(220, 237, 200);
                doc.rect(120, y, 80, 12, 'F');
                doc.setTextColor(0, 100, 0);
                doc.setFontSize(12);
                doc.text(`معدل کل: ${overallAverage}`, 160, y + 8, { align: 'center' });
                
                y += 20;
                
                // مهر و امضای رسمی
                doc.setDrawColor(220, 38, 38);
                doc.setLineWidth(1);
                doc.rect(50, y, 110, 40);
                
                doc.setTextColor(0, 0, 0);
                doc.setFontSize(10);
                doc.text('مهر و امضای مدیر مدرسه', 105, y + 10, { align: 'center' });
                doc.text('مدرسه نمونه دولتی امام حسین (ع)', 105, y + 20, { align: 'center' });
                doc.text('تاریخ: ' + new Date().toLocaleDateString('fa-IR'), 105, y + 30, { align: 'center' });
                
                // ذخیره فایل با نام فارسی
                doc.save(`کارنامه_${student.firstName}_${student.lastName}.pdf`);
                alert('کارنامه با موفقیت تولید شد!');
                
            } catch (error) {
                console.error('خطا در تولید PDF:', error);
                alert('خطا در تولید PDF! لطفاً دوباره تلاش کنید.');
            }
        }

        // تولید PDF برای کل کلاس
        function generateClassPDF() {
            try {
                const classId = document.getElementById('classSelect').value;
                if (!classId) {
                    alert('لطفاً یک کلاس انتخاب کنید!');
                    return;
                }
                
                const classStudents = students.filter(s => s.classId === classId);
                if (classStudents.length === 0) {
                    alert('این کلاس دانش‌آموزی ندارد!');
                    return;
                }

                const { jsPDF } = window.jspdf;
                const className = classes.find(c => c.id === classId).fullName;
                
                classStudents.forEach((student, index) => {
                    if (index > 0) {
                        doc.addPage();
                    }
                    
                    const doc = new jsPDF();
                    
                    // طراحی مشابه کارنامه فردی اما برای هر دانش‌آموز
                    doc.setFont('helvetica');
                    
                    // هدر
                    doc.setFillColor(30, 58, 138);
                    doc.rect(0, 0, 210, 40, 'F');
                    doc.setTextColor(255, 255, 255);
                    doc.setFontSize(18);
                    doc.text('کارنامه تحصیلی', 105, 15, { align: 'center' });
                    doc.setFontSize(12);
                    doc.text('مدرسه نمونه دولتی امام حسین (ع)', 105, 25, { align: 'center' });
                    doc.setFontSize(10);
                    doc.text('سال تحصیلی ۱۴۰۳-۱۴۰۴', 105, 32, { align: 'center' });
                    
                    // اطلاعات دانش‌آموز
                    doc.setTextColor(0, 0, 0);
                    doc.setFontSize(11);
                    
                    const studentInfo = [
                        ['نام و نام خانوادگی:', student.firstName + ' ' + student.lastName],
                        ['شماره دانش‌آموزی:', student.studentId],
                        ['کلاس:', student.className]
                    ];
                    
                    let y = 50;
                    studentInfo.forEach(([label, value]) => {
                        doc.setFillColor(240, 240, 240);
                        doc.rect(20, y, 170, 8, 'F');
                        doc.setTextColor(0, 0, 0);
                        doc.text(label, 25, y + 5);
                        doc.text(value, 120, y + 5);
                        y += 10;
                    });
                    
                    y += 10;
                    
                    // جدول نمرات
                    const studentGrades = grades.filter(g => g.studentId === student.id);
                    const subjectGrades = {};
                    
                    studentGrades.forEach(grade => {
                        if (!subjectGrades[grade.subject]) {
                            subjectGrades[grade.subject] = {};
                        }
                        subjectGrades[grade.subject][grade.term] = grade.grade;
                    });
                    
                    const subjects = [
                        'ریاضی', 'فیزیک', 'شیمی', 'ادبیات فارسی', 
                        'زبان انگلیسی', 'عربی', 'دین و زندگی', 
                        'تاریخ', 'جغرافیا', 'هنر', 'تربیت بدنی'
                    ];
                    
                    const tableData = [];
                    let totalSum = 0;
                    let subjectCount = 0;
                    
                    subjects.forEach(subject => {
                        const grade1 = subjectGrades[subject]?.['1'] || '-';
                        const grade2 = subjectGrades[subject]?.['2'] || '-';
                        
                        let average = '-';
                        let status = '-';
                        
                        if (grade1 !== '-' && grade2 !== '-') {
                            average = ((grade1 + grade2) / 2).toFixed(2);
                            totalSum += parseFloat(average);
                            subjectCount++;
                            
                            if (average >= 17) status = 'عالی';
                            else if (average >= 15) status = 'خیلی خوب';
                            else if (average >= 12) status = 'خوب';
                            else if (average >= 10) status = 'قابل قبول';
                            else status = 'نیاز به تلاش';
                        }
                        
                        tableData.push([
                            subject,
                            grade1.toString(),
                            grade2.toString(),
                            average,
                            status
                        ]);
                    });
                    
                    // سرستون جدول
                    doc.setFillColor(30, 58, 138);
                    doc.rect(10, y, 190, 10, 'F');
                    doc.setTextColor(255, 255, 255);
                    doc.text('ردیف', 25, y + 6);
                    doc.text('نام درس', 60, y + 6);
                    doc.text('نوبت اول', 120, y + 6);
                    doc.text('نوبت دوم', 150, y + 6);
                    doc.text('معدل', 170, y + 6);
                    doc.text('وضعیت', 190, y + 6);
                    
                    y += 10;
                    
                    // محتوای جدول
                    doc.setTextColor(0, 0, 0);
                    tableData.forEach((row, index) => {
                        if (y > 250) {
                            doc.addPage();
                            y = 20;
                        }
                        
                        if (index % 2 === 0) {
                            doc.setFillColor(245, 245, 245);
                        } else {
                            doc.setFillColor(255, 255, 255);
                        }
                        doc.rect(10, y, 190, 8, 'F');
                        
                        doc.text((index + 1).toString(), 25, y + 5);
                        doc.text(row[0], 60, y + 5);
                        doc.text(row[1], 120, y + 5);
                        doc.text(row[2], 150, y + 5);
                        doc.text(row[3], 170, y + 5);
                        doc.text(row[4], 190, y + 5);
                        
                        y += 8;
                    });
                    
                    y += 10;
                    
                    // معدل کل
                    const overallAverage = subjectCount > 0 ? (totalSum / subjectCount).toFixed(2) : '0.00';
                    
                    doc.setFillColor(220, 237, 200);
                    doc.rect(120, y, 80, 12, 'F');
                    doc.setTextColor(0, 100, 0);
                    doc.setFontSize(12);
                    doc.text(`معدل کل: ${overallAverage}`, 160, y + 8, { align: 'center' });
                    
                    y += 20;
                    
                    // مهر و امضا
                    doc.setDrawColor(220, 38, 38);
                    doc.setLineWidth(1);
                    doc.rect(50, y, 110, 40);
                    
                    doc.setTextColor(0, 0, 0);
                    doc.setFontSize(10);
                    doc.text('مهر و امضای مدیر مدرسه', 105, y + 10, { align: 'center' });
                    doc.text('مدرسه نمونه دولتی امام حسین (ع)', 105, y + 20, { align: 'center' });
                    doc.text('تاریخ: ' + new Date().toLocaleDateString('fa-IR'), 105, y + 30, { align: 'center' });
                    
                    if (index === 0) {
                        var finalDoc = doc;
                    }
                });
                
                finalDoc.save(`کارنامه_${className}.pdf`);
                alert(`کارنامه کلاس ${className} با موفقیت تولید شد!`);
                
            } catch (error) {
                console.error('خطا در تولید PDF:', error);
                alert('خطا در تولید PDF! لطفاً دوباره تلاش کنید.');
            }
        }

        // تولید PDF برای همه دانش‌آموزان
        function generateAllPDF() {
            try {
                if (students.length === 0) {
                    alert('هیچ دانش‌آموزی برای تولید کارنامه وجود ندارد!');
                    return;
                }

                const { jsPDF } = window.jspdf;
                const doc = new jsPDF();
                
                students.forEach((student, index) => {
                    if (index > 0) {
                        doc.addPage();
                    }
                    
                    // محتوای مشابه کارنامه فردی برای هر دانش‌آموز
                    doc.setFont('helvetica');
                    
                    doc.setFillColor(30, 58, 138);
                    doc.rect(0, 0, 210, 40, 'F');
                    doc.setTextColor(255, 255, 255);
                    doc.setFontSize(18);
                    doc.text('کارنامه تحصیلی', 105, 15, { align: 'center' });
                    doc.setFontSize(12);
                    doc.text('مدرسه نمونه دولتی امام حسین (ع)', 105, 25, { align: 'center' });
                    doc.setFontSize(10);
                    doc.text('سال تحصیلی ۱۴۰۳-۱۴۰۴', 105, 32, { align: 'center' });
                    
                    doc.setTextColor(0, 0, 0);
                    doc.setFontSize(11);
                    
                    const studentInfo = [
                        ['نام و نام خانوادگی:', student.firstName + ' ' + student.lastName],
                        ['شماره دانش‌آموزی:', student.studentId],
                        ['کلاس:', student.className]
                    ];
                    
                    let y = 50;
                    studentInfo.forEach(([label, value]) => {
                        doc.setFillColor(240, 240, 240);
                        doc.rect(20, y, 170, 8, 'F');
                        doc.setTextColor(0, 0, 0);
                        doc.text(label, 25, y + 5);
                        doc.text(value, 120, y + 5);
                        y += 10;
                    });
                    
                    y += 10;
                    
                    const studentGrades = grades.filter(g => g.studentId === student.id);
                    const subjectGrades = {};
                    
                    studentGrades.forEach(grade => {
                        if (!subjectGrades[grade.subject]) {
                            subjectGrades[grade.subject] = {};
                        }
                        subjectGrades[grade.subject][grade.term] = grade.grade;
                    });
                    
                    const subjects = [
                        'ریاضی', 'فیزیک', 'شیمی', 'ادبیات فارسی', 
                        'زبان انگلیسی', 'عربی', 'دین و زندگی', 
                        'تاریخ', 'جغرافیا', 'هنر', 'تربیت بدنی'
                    ];
                    
                    const tableData = [];
                    let totalSum = 0;
                    let subjectCount = 0;
                    
                    subjects.forEach(subject => {
                        const grade1 = subjectGrades[subject]?.['1'] || '-';
                        const grade2 = subjectGrades[subject]?.['2'] || '-';
                        
                        let average = '-';
                        let status = '-';
                        
                        if (grade1 !== '-' && grade2 !== '-') {
                            average = ((grade1 + grade2) / 2).toFixed(2);
                            totalSum += parseFloat(average);
                            subjectCount++;
                            
                            if (average >= 17) status = 'عالی';
                            else if (average >= 15) status = 'خیلی خوب';
                            else if (average >= 12) status = 'خوب';
                            else if (average >= 10) status = 'قابل قبول';
                            else status = 'نیاز به تلاش';
                        }
                        
                        tableData.push([
                            subject,
                            grade1.toString(),
                            grade2.toString(),
                            average,
                            status
                        ]);
                    });
                    
                    doc.setFillColor(30, 58, 138);
                    doc.rect(10, y, 190, 10, 'F');
                    doc.setTextColor(255, 255, 255);
                    doc.text('ردیف', 25, y + 6);
                    doc.text('نام درس', 60, y + 6);
                    doc.text('نوبت اول', 120, y + 6);
                    doc.text('نوبت دوم', 150, y + 6);
                    doc.text('معدل', 170, y + 6);
                    doc.text('وضعیت', 190, y + 6);
                    
                    y += 10;
                    
                    doc.setTextColor(0, 0, 0);
                    tableData.forEach((row, index) => {
                        if (y > 250) {
                            doc.addPage();
                            y = 20;
                        }
                        
                        if (index % 2 === 0) {
                            doc.setFillColor(245, 245, 245);
                        } else {
                            doc.setFillColor(255, 255, 255);
                        }
                        doc.rect(10, y, 190, 8, 'F');
                        
                        doc.text((index + 1).toString(), 25, y + 5);
                        doc.text(row[0], 60, y + 5);
                        doc.text(row[1], 120, y + 5);
                        doc.text(row[2], 150, y + 5);
                        doc.text(row[3], 170, y + 5);
                        doc.text(row[4], 190, y + 5);
                        
                        y += 8;
                    });
                    
                    y += 10;
                    
                    const overallAverage = subjectCount > 0 ? (totalSum / subjectCount).toFixed(2) : '0.00';
                    
                    doc.setFillColor(220, 237, 200);
                    doc.rect(120, y, 80, 12, 'F');
                    doc.setTextColor(0, 100, 0);
                    doc.setFontSize(12);
                    doc.text(`معدل کل: ${overallAverage}`, 160, y + 8, { align: 'center' });
                    
                    y += 20;
                    
                    doc.setDrawColor(220, 38, 38);
                    doc.setLineWidth(1);
                    doc.rect(50, y, 110, 40);
                    
                    doc.setTextColor(0, 0, 0);
                    doc.setFontSize(10);
                    doc.text('مهر و امضای مدیر مدرسه', 105, y + 10, { align: 'center' });
                    doc.text('مدرسه نمونه دولتی امام حسین (ع)', 105, y + 20, { align: 'center' });
                    doc.text('تاریخ: ' + new Date().toLocaleDateString('fa-IR'), 105, y + 30, { align: 'center' });
                });
                
                doc.save('کارنامه_همه_دانش_آموزان.pdf');
                alert(`کارنامه ${students.length} دانش‌آموز با موفقیت تولید شد!`);
                
            } catch (error) {
                console.error('خطا در تولید PDF:', error);
                alert('خطا در تولید PDF! لطفاً دوباره تلاش کنید.');
            }
        }

        // توابع کمکی
        function loadTeacherInfo() {
            const teacherInfo = document.getElementById('teacherInfo');
            if (currentTeacher) {
                teacherInfo.innerHTML = `
                    <div class="text-center">
                        <div class="fw-bold" style="color: var(--moe-blue);">${currentTeacher.name}</div>
                        <div class="text-muted">کد پرسنلی: ${currentTeacher.personalCode}</div>
                        <div class="mt-2">
                            <span class="subject-badge">${currentTeacher.specialty}</span>
                        </div>
                    </div>
                `;
            }
        }

        function logout() {
            if (confirm('آیا می‌خواهید از سیستم خارج شوید؟')) {
                currentTeacher = null;
                document.getElementById('dashboard').style.display = 'none';
                document.getElementById('loginPage').style.display = 'block';
                document.getElementById('loginForm').reset();
            }
        }

        function deleteTeacher(username) {
            if (confirm('آیا از حذف این معلم مطمئن هستید؟')) {
                teachers = teachers.filter(t => t.username !== username);
                saveAllData();
                loadTeacherList();
            }
        }

        function deleteClass(classId) {
            if (confirm('آیا از حذف این کلاس مطمئن هستید؟')) {
                classes = classes.filter(c => c.id !== classId);
                students = students.filter(s => s.classId !== classId);
                saveAllData();
                loadClasses();
                loadStudents();
                loadPDFSelects();
            }
        }

        function deleteStudent(studentId) {
            if (confirm('آیا از حذف این دانش‌آموز مطمئن هستید؟')) {
                students = students.filter(s => s.id !== studentId);
                grades = grades.filter(g => g.studentId !== studentId);
                saveAllData();
                loadStudents();
                loadPDFSelects();
            }
        }

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

        // بارگذاری اولیه
        window.onload = function() {
            loadStudentClassSelect();
            console.log('سیستم آماده است...');
        };
    </script>
</body>
</html>
