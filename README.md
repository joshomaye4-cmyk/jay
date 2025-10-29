<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>CoreX - Electronic Health Record System</title>
    <style>
        :root {
            --primary: #2c6fbb;
            --primary-dark: #1a4a7a;
            --secondary: #4CAF50;
            --danger: #f44336;
            --warning: #ff9800;
            --light: #f8f9fa;
            --dark: #343a40;
            --gray: #6c757d;
            --border: #dee2e6;
        }
        
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
            font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
        }
        
        body {
            background-color: #f5f7fa;
            color: #333;
            line-height: 1.6;
        }
        
        .container {
            display: flex;
            min-height: 100vh;
        }
        
        /* Sidebar Styles */
        .sidebar {
            width: 250px;
            background-color: var(--primary-dark);
            color: white;
            transition: all 0.3s;
        }
        
        .sidebar-header {
            padding: 20px;
            background-color: var(--primary);
            display: flex;
            align-items: center;
        }
        
        .sidebar-header h2 {
            margin-left: 10px;
        }
        
        .sidebar-menu {
            padding: 15px 0;
        }
        
        .sidebar-menu ul {
            list-style: none;
        }
        
        .sidebar-menu li {
            padding: 12px 20px;
            cursor: pointer;
            transition: background-color 0.2s;
        }
        
        .sidebar-menu li:hover {
            background-color: rgba(255, 255, 255, 0.1);
        }
        
        .sidebar-menu li.active {
            background-color: rgba(255, 255, 255, 0.2);
            border-left: 4px solid white;
        }
        
        .sidebar-menu i {
            margin-right: 10px;
            width: 20px;
            text-align: center;
        }
        
        /* Main Content Styles */
        .main-content {
            flex: 1;
            display: flex;
            flex-direction: column;
        }
        
        .top-nav {
            background-color: white;
            padding: 15px 30px;
            box-shadow: 0 2px 5px rgba(0,0,0,0.1);
            display: flex;
            justify-content: space-between;
            align-items: center;
        }
        
        .search-bar {
            display: flex;
            align-items: center;
            background-color: var(--light);
            border-radius: 4px;
            padding: 8px 15px;
            width: 400px;
        }
        
        .search-bar input {
            border: none;
            background: transparent;
            margin-left: 10px;
            width: 100%;
            outline: none;
        }
        
        .user-info {
            display: flex;
            align-items: center;
        }
        
        .user-info img {
            width: 40px;
            height: 40px;
            border-radius: 50%;
            margin-right: 10px;
        }
        
        .content {
            padding: 30px;
            flex: 1;
        }
        
        .page-header {
            display: flex;
            justify-content: space-between;
            align-items: center;
            margin-bottom: 30px;
        }
        
        .btn {
            padding: 10px 20px;
            border: none;
            border-radius: 4px;
            cursor: pointer;
            font-weight: 500;
            transition: background-color 0.2s;
        }
        
        .btn-primary {
            background-color: var(--primary);
            color: white;
        }
        
        .btn-primary:hover {
            background-color: var(--primary-dark);
        }
        
        .btn-secondary {
            background-color: var(--secondary);
            color: white;
        }
        
        .btn-secondary:hover {
            background-color: #3d8b40;
        }
        
        /* Dashboard Styles */
        .stats-container {
            display: grid;
            grid-template-columns: repeat(auto-fill, minmax(250px, 1fr));
            gap: 20px;
            margin-bottom: 30px;
        }
        
        .stat-card {
            background-color: white;
            border-radius: 8px;
            padding: 20px;
            box-shadow: 0 2px 5px rgba(0,0,0,0.05);
            display: flex;
            align-items: center;
        }
        
        .stat-icon {
            width: 50px;
            height: 50px;
            border-radius: 50%;
            display: flex;
            align-items: center;
            justify-content: center;
            margin-right: 15px;
            font-size: 20px;
        }
        
        .stat-icon.patients {
            background-color: rgba(44, 111, 187, 0.2);
            color: var(--primary);
        }
        
        .stat-icon.appointments {
            background-color: rgba(76, 175, 80, 0.2);
            color: var(--secondary);
        }
        
        .stat-icon.prescriptions {
            background-color: rgba(255, 152, 0, 0.2);
            color: var(--warning);
        }
        
        .stat-icon.labs {
            background-color: rgba(244, 67, 54, 0.2);
            color: var(--danger);
        }
        
        .stat-info h3 {
            font-size: 24px;
            margin-bottom: 5px;
        }
        
        .stat-info p {
            color: var(--gray);
            font-size: 14px;
        }
        
        .recent-patients {
            background-color: white;
            border-radius: 8px;
            box-shadow: 0 2px 5px rgba(0,0,0,0.05);
            overflow: hidden;
        }
        
        .section-header {
            padding: 15px 20px;
            border-bottom: 1px solid var(--border);
            display: flex;
            justify-content: space-between;
            align-items: center;
        }
        
        table {
            width: 100%;
            border-collapse: collapse;
        }
        
        th, td {
            padding: 12px 15px;
            text-align: left;
            border-bottom: 1px solid var(--border);
        }
        
        th {
            background-color: var(--light);
            font-weight: 600;
        }
        
        tr:hover {
            background-color: rgba(0,0,0,0.02);
        }
        
        .status {
            padding: 5px 10px;
            border-radius: 20px;
            font-size: 12px;
            font-weight: 500;
        }
        
        .status.active {
            background-color: rgba(76, 175, 80, 0.2);
            color: var(--secondary);
        }
        
        .status.inactive {
            background-color: rgba(108, 117, 125, 0.2);
            color: var(--gray);
        }
        
        /* Patient Details Styles */
        .patient-details {
            display: grid;
            grid-template-columns: 300px 1fr;
            gap: 30px;
        }
        
        .patient-profile {
            background-color: white;
            border-radius: 8px;
            box-shadow: 0 2px 5px rgba(0,0,0,0.05);
            overflow: hidden;
        }
        
        .profile-header {
            background-color: var(--primary);
            color: white;
            padding: 20px;
            text-align: center;
        }
        
        .profile-img {
            width: 100px;
            height: 100px;
            border-radius: 50%;
            margin: 0 auto 15px;
            background-color: white;
            display: flex;
            align-items: center;
            justify-content: center;
            font-size: 40px;
            color: var(--primary);
        }
        
        .profile-info {
            padding: 20px;
        }
        
        .info-item {
            margin-bottom: 15px;
        }
        
        .info-label {
            font-size: 12px;
            color: var(--gray);
            margin-bottom: 5px;
        }
        
        .patient-tabs {
            display: flex;
            border-bottom: 1px solid var(--border);
            margin-bottom: 20px;
        }
        
        .tab {
            padding: 10px 20px;
            cursor: pointer;
            border-bottom: 2px solid transparent;
        }
        
        .tab.active {
            border-bottom: 2px solid var(--primary);
            color: var(--primary);
            font-weight: 500;
        }
        
        .tab-content {
            display: none;
        }
        
        .tab-content.active {
            display: block;
        }
        
        .medical-history-item {
            background-color: white;
            border-radius: 8px;
            padding: 15px;
            margin-bottom: 15px;
            box-shadow: 0 2px 5px rgba(0,0,0,0.05);
        }
        
        .medical-history-item h4 {
            margin-bottom: 10px;
        }
        
        .medical-history-item p {
            color: var(--gray);
            font-size: 14px;
        }
        
        /* Modal Styles */
        .modal {
            display: none;
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            background-color: rgba(0,0,0,0.5);
            z-index: 1000;
            align-items: center;
            justify-content: center;
        }
        
        .modal-content {
            background-color: white;
            border-radius: 8px;
            width: 500px;
            max-width: 90%;
            box-shadow: 0 5px 15px rgba(0,0,0,0.2);
        }
        
        .modal-header {
            padding: 15px 20px;
            border-bottom: 1px solid var(--border);
            display: flex;
            justify-content: space-between;
            align-items: center;
        }
        
        .modal-body {
            padding: 20px;
        }
        
        .form-group {
            margin-bottom: 15px;
        }
        
        .form-group label {
            display: block;
            margin-bottom: 5px;
            font-weight: 500;
        }
        
        .form-control {
            width: 100%;
            padding: 10px;
            border: 1px solid var(--border);
            border-radius: 4px;
            font-size: 14px;
        }
        
        .form-row {
            display: flex;
            gap: 15px;
        }
        
        .form-row .form-group {
            flex: 1;
        }
        
        .modal-footer {
            padding: 15px 20px;
            border-top: 1px solid var(--border);
            display: flex;
            justify-content: flex-end;
            gap: 10px;
        }
        
        .close {
            background: none;
            border: none;
            font-size: 20px;
            cursor: pointer;
        }
        
        /* Responsive Styles */
        @media (max-width: 992px) {
            .patient-details {
                grid-template-columns: 1fr;
            }
            
            .stats-container {
                grid-template-columns: repeat(2, 1fr);
            }
        }
        
        @media (max-width: 768px) {
            .container {
                flex-direction: column;
            }
            
            .sidebar {
                width: 100%;
                height: auto;
            }
            
            .sidebar-menu ul {
                display: flex;
                overflow-x: auto;
            }
            
            .sidebar-menu li {
                white-space: nowrap;
            }
            
            .search-bar {
                width: 200px;
            }
            
            .stats-container {
                grid-template-columns: 1fr;
            }
        }
    </style>
</head>
<body>
    <div class="container">
        <!-- Sidebar -->
        <div class="sidebar">
            <div class="sidebar-header">
                <div class="logo">
                    <i>⚕</i>
                </div>
                <h2>CoreX EHR</h2>
            </div>
            <div class="sidebar-menu">
                <ul>
                    <li class="active" data-page="dashboard">
                        <i>📊</i> Dashboard
                    </li>
                    <li data-page="patients">
                        <i>👥</i> Patients
                    </li>
                    <li data-page="appointments">
                        <i>📅</i> Appointments
                    </li>
                    <li data-page="prescriptions">
                        <i>💊</i> Prescriptions
                    </li>
                    <li data-page="labs">
                        <i>🔬</i> Lab Results
                    </li>
                    <li data-page="billing">
                        <i>💰</i> Billing
                    </li>
                    <li data-page="settings">
                        <i>⚙</i> Settings
                    </li>
                </ul>
            </div>
        </div>
        
        <!-- Main Content -->
        <div class="main-content">
            <!-- Top Navigation -->
            <div class="top-nav">
                <div class="search-bar">
                    <i>🔍</i>
                    <input type="text" placeholder="Search patients, records...">
                </div>
                <div class="user-info">
                    <img src="https://i.pravatar.cc/150?img=12" alt="User">
                    <div>
                        <div>Dr. Sarah Johnson</div>
                        <div style="font-size: 12px; color: var(--gray);">Cardiologist</div>
                    </div>
                </div>
            </div>
            
            <!-- Content Area -->
            <div class="content">
                <!-- Dashboard Page -->
                <div id="dashboard" class="page active">
                    <div class="page-header">
                        <h1>Dashboard</h1>
                        <div>
                            <button class="btn btn-primary" id="addPatientBtn">Add New Patient</button>
                        </div>
                    </div>
                    
                    <div class="stats-container">
                        <div class="stat-card">
                            <div class="stat-icon patients">
                                <i>👥</i>
                            </div>
                            <div class="stat-info">
                                <h3>1,248</h3>
                                <p>Total Patients</p>
                            </div>
                        </div>
                        <div class="stat-card">
                            <div class="stat-icon appointments">
                                <i>📅</i>
                            </div>
                            <div class="stat-info">
                                <h3>24</h3>
                                <p>Today's Appointments</p>
                            </div>
                        </div>
                        <div class="stat-card">
                            <div class="stat-icon prescriptions">
                                <i>💊</i>
                            </div>
                            <div class="stat-info">
                                <h3>156</h3>
                                <p>Pending Prescriptions</p>
                            </div>
                        </div>
                        <div class="stat-card">
                            <div class="stat-icon labs">
                                <i>🔬</i>
                            </div>
                            <div class="stat-info">
                                <h3>42</h3>
                                <p>Lab Results Pending</p>
                            </div>
                        </div>
                    </div>
                    
                    <div class="recent-patients">
                        <div class="section-header">
                            <h3>Recent Patients</h3>
                            <a href="#" style="color: var(--primary);">View All</a>
                        </div>
                        <table>
                            <thead>
                                <tr>
                                    <th>Patient Name</th>
                                    <th>ID</th>
                                    <th>Last Visit</th>
                                    <th>Condition</th>
                                    <th>Status</th>
                                    <th>Actions</th>
                                </tr>
                            </thead>
                            <tbody>
                                <tr>
                                    <td>John Smith</td>
                                    <td>#PT-0012</td>
                                    <td>Oct 12, 2023</td>
                                    <td>Hypertension</td>
                                    <td><span class="status active">Active</span></td>
                                    <td>
                                        <button class="btn" style="padding: 5px 10px; font-size: 12px;">View</button>
                                    </td>
                                </tr>
                                <tr>
                                    <td>Emily Johnson</td>
                                    <td>#PT-0045</td>
                                    <td>Oct 10, 2023</td>
                                    <td>Diabetes Type 2</td>
                                    <td><span class="status active">Active</span></td>
                                    <td>
                                        <button class="btn" style="padding: 5px 10px; font-size: 12px;">View</button>
                                    </td>
                                </tr>
                                <tr>
                                    <td>Michael Brown</td>
                                    <td>#PT-0038</td>
                                    <td>Oct 8, 2023</td>
                                    <td>Asthma</td>
                                    <td><span class="status active">Active</span></td>
                                    <td>
                                        <button class="btn" style="padding: 5px 10px; font-size: 12px;">View</button>
                                    </td>
                                </tr>
                                <tr>
                                    <td>Sarah Williams</td>
                                    <td>#PT-0021</td>
                                    <td>Oct 5, 2023</td>
                                    <td>Migraine</td>
                                    <td><span class="status inactive">Inactive</span></td>
                                    <td>
                                        <button class="btn" style="padding: 5px 10px; font-size: 12px;">View</button>
                                    </td>
                                </tr>
                            </tbody>
                        </table>
                    </div>
                </div>
                
                <!-- Patients Page -->
                <div id="patients" class="page">
                    <div class="page-header">
                        <h1>Patients</h1>
                        <div>
                            <button class="btn btn-primary" id="addPatientBtn2">Add New Patient</button>
                        </div>
                    </div>
                    
                    <div class="recent-patients">
                        <div class="section-header">
                            <h3>All Patients</h3>
                            <div>
                                <input type="text" placeholder="Search patients..." class="form-control" style="width: 200px; display: inline-block;">
                            </div>
                        </div>
                        <table>
                            <thead>
                                <tr>
                                    <th>Patient Name</th>
                                    <th>ID</th>
                                    <th>Date of Birth</th>
                                    <th>Phone</th>
                                    <th>Condition</th>
                                    <th>Status</th>
                                    <th>Actions</th>
                                </tr>
                            </thead>
                            <tbody>
                                <tr>
                                    <td>John Smith</td>
                                    <td>#PT-0012</td>
                                    <td>05/15/1978</td>
                                    <td>(555) 123-4567</td>
                                    <td>Hypertension</td>
                                    <td><span class="status active">Active</span></td>
                                    <td>
                                        <button class="btn" style="padding: 5px 10px; font-size: 12px;">View</button>
                                        <button class="btn" style="padding: 5px 10px; font-size: 12px; background-color: var(--warning); color: white;">Edit</button>
                                    </td>
                                </tr>
                                <tr>
                                    <td>Emily Johnson</td>
                                    <td>#PT-0045</td>
                                    <td>11/22/1985</td>
                                    <td>(555) 987-6543</td>
                                    <td>Diabetes Type 2</td>
                                    <td><span class="status active">Active</span></td>
                                    <td>
                                        <button class="btn" style="padding: 5px 10px; font-size: 12px;">View</button>
                                        <button class="btn" style="padding: 5px 10px; font-size: 12px; background-color: var(--warning); color: white;">Edit</button>
                                    </td>
                                </tr>
                                <tr>
                                    <td>Michael Brown</td>
                                    <td>#PT-0038</td>
                                    <td>03/08/1965</td>
                                    <td>(555) 456-7890</td>
                                    <td>Asthma</td>
                                    <td><span class="status active">Active</span></td>
                                    <td>
                                        <button class="btn" style="padding: 5px 10px; font-size: 12px;">View</button>
                                        <button class="btn" style="padding: 5px 10px; font-size: 12px; background-color: var(--warning); color: white;">Edit</button>
                                    </td>
                                </tr>
                                <tr>
                                    <td>Sarah Williams</td>
                                    <td>#PT-0021</td>
                                    <td>07/30/1992</td>
                                    <td>(555) 234-5678</td>
                                    <td>Migraine</td>
                                    <td><span class="status inactive">Inactive</span></td>
                                    <td>
                                        <button class="btn" style="padding: 5px 10px; font-size: 12px;">View</button>
                                        <button class="btn" style="padding: 5px 10px; font-size: 12px; background-color: var(--warning); color: white;">Edit</button>
                                    </td>
                                </tr>
                            </tbody>
                        </table>
                    </div>
                </div>
                
                <!-- Patient Details Page -->
                <div id="patient-details" class="page">
                    <div class="page-header">
                        <h1>Patient Details</h1>
                        <div>
                            <button class="btn btn-primary">Edit Patient</button>
                            <button class="btn btn-secondary">Print Record</button>
                        </div>
                    </div>
                    
                    <div class="patient-details">
                        <div class="patient-profile">
                            <div class="profile-header">
                                <div class="profile-img">
                                    <i>👤</i>
                                </div>
                                <h3>John Smith</h3>
                                <p>Patient ID: #PT-0012</p>
                            </div>
                            <div class="profile-info">
                                <div class="info-item">
                                    <div class="info-label">Date of Birth</div>
                                    <div>May 15, 1978 (45 years)</div>
                                </div>
                                <div class="info-item">
                                    <div class="info-label">Gender</div>
                                    <div>Male</div>
                                </div>
                                <div class="info-item">
                                    <div class="info-label">Phone</div>
                                    <div>(555) 123-4567</div>
                                </div>
                                <div class="info-item">
                                    <div class="info-label">Email</div>
                                    <div>john.smith@example.com</div>
                                </div>
                                <div class="info-item">
                                    <div class="info-label">Address</div>
                                    <div>123 Main St, Anytown, USA</div>
                                </div>
                                <div class="info-item">
                                    <div class="info-label">Emergency Contact</div>
                                    <div>Jane Smith - (555) 765-4321</div>
                                </div>
                                <div class="info-item">
                                    <div class="info-label">Primary Insurance</div>
                                    <div>Blue Cross Blue Shield</div>
                                </div>
                            </div>
                        </div>
                        
                        <div class="patient-info">
                            <div class="patient-tabs">
                                <div class="tab active" data-tab="overview">Overview</div>
                                <div class="tab" data-tab="medical-history">Medical History</div>
                                <div class="tab" data-tab="appointments">Appointments</div>
                                <div class="tab" data-tab="prescriptions">Prescriptions</div>
                                <div class="tab" data-tab="lab-results">Lab Results</div>
                            </div>
                            
                            <div id="overview" class="tab-content active">
                                <div class="medical-history-item">
                                    <h4>Current Conditions</h4>
                                    <ul>
                                        <li>Hypertension (Diagnosed 2018)</li>
                                        <li>High Cholesterol (Diagnosed 2020)</li>
                                    </ul>
                                </div>
                                
                                <div class="medical-history-item">
                                    <h4>Allergies</h4>
                                    <ul>
                                        <li>Penicillin - Causes rash</li>
                                        <li>No known food allergies</li>
                                    </ul>
                                </div>
                                
                                <div class="medical-history-item">
                                    <h4>Current Medications</h4>
                                    <ul>
                                        <li>Lisinopril 10mg - Once daily</li>
                                        <li>Atorvastatin 20mg - Once daily</li>
                                    </ul>
                                </div>
                                
                                <div class="medical-history-item">
                                    <h4>Recent Vital Signs (Last Visit: Oct 12, 2023)</h4>
                                    <div class="form-row">
                                        <div class="form-group">
                                            <div class="info-label">Blood Pressure</div>
                                            <div>132/84 mmHg</div>
                                        </div>
                                        <div class="form-group">
                                            <div class="info-label">Heart Rate</div>
                                            <div>72 bpm</div>
                                        </div>
                                        <div class="form-group">
                                            <div class="info-label">Temperature</div>
                                            <div>98.6°F</div>
                                        </div>
                                    </div>
                                </div>
                            </div>
                            
                            <div id="medical-history" class="tab-content">
                                <div class="medical-history-item">
                                    <h4>Hypertension Diagnosis</h4>
                                    <p><strong>Date:</strong> March 15, 2018</p>
                                    <p><strong>Description:</strong> Patient presented with elevated blood pressure readings on three separate occasions. Lifestyle modifications recommended initially.</p>
                                </div>
                                
                                <div class="medical-history-item">
                                    <h4>High Cholesterol Diagnosis</h4>
                                    <p><strong>Date:</strong> January 22, 2020</p>
                                    <p><strong>Description:</strong> Routine blood work showed elevated LDL cholesterol levels. Started on statin therapy.</p>
                                </div>
                                
                                <div class="medical-history-item">
                                    <h4>Appendectomy</h4>
                                    <p><strong>Date:</strong> June 5, 2005</p>
                                    <p><strong>Description:</strong> Emergency surgery for acute appendicitis. Recovery was uncomplicated.</p>
                                </div>
                            </div>
                        </div>
                    </div>
                </div>
                
                <!-- Other pages would go here -->
                <div id="appointments" class="page">
                    <div class="page-header">
                        <h1>Appointments</h1>
                    </div>
                    <p>Appointments management page content would go here.</p>
                </div>
                
                <div id="prescriptions" class="page">
                    <div class="page-header">
                        <h1>Prescriptions</h1>
                    </div>
                    <p>Prescriptions management page content would go here.</p>
                </div>
                
                <div id="labs" class="page">
                    <div class="page-header">
                        <h1>Lab Results</h1>
                    </div>
                    <p>Lab results management page content would go here.</p>
                </div>
                
                <div id="billing" class="page">
                    <div class="page-header">
                        <h1>Billing</h1>
                    </div>
                    <p>Billing management page content would go here.</p>
                </div>
                
                <div id="settings" class="page">
                    <div class="page-header">
                        <h1>Settings</h1>
                    </div>
                    <p>System settings page content would go here.</p>
                </div>
            </div>
        </div>
    </div>
    
    <!-- Add Patient Modal -->
    <div class="modal" id="addPatientModal">
        <div class="modal-content">
            <div class="modal-header">
                <h3>Add New Patient</h3>
                <button class="close">&times;</button>
            </div>
            <div class="modal-body">
                <form id="addPatientForm">
                    <div class="form-row">
                        <div class="form-group">
                            <label for="firstName">First Name</label>
                            <input type="text" id="firstName" class="form-control" required>
                        </div>
                        <div class="form-group">
                            <label for="lastName">Last Name</label>
                            <input type="text" id="lastName" class="form-control" required>
                        </div>
                    </div>
                    
                    <div class="form-row">
                        <div class="form-group">
                            <label for="dob">Date of Birth</label>
                            <input type="date" id="dob" class="form-control" required>
                        </div>
                        <div class="form-group">
                            <label for="gender">Gender</label>
                            <select id="gender" class="form-control" required>
                                <option value="">Select</option>
                                <option value="male">Male</option>
                                <option value="female">Female</option>
                                <option value="other">Other</option>
                            </select>
                        </div>
                    </div>
                    
                    <div class="form-group">
                        <label for="phone">Phone</label>
                        <input type="tel" id="phone" class="form-control" required>
                    </div>
                    
                    <div class="form-group">
                        <label for="email">Email</label>
                        <input type="email" id="email" class="form-control">
                    </div>
                    
                    <div class="form-group">
                        <label for="address">Address</label>
                        <textarea id="address" class="form-control" rows="3"></textarea>
                    </div>
                    
                    <div class="form-group">
                        <label for="insurance">Primary Insurance</label>
                        <input type="text" id="insurance" class="form-control">
                    </div>
                </form>
            </div>
            <div class="modal-footer">
                <button class="btn" id="cancelPatientBtn">Cancel</button>
                <button class="btn btn-primary" id="savePatientBtn">Save Patient</button>
            </div>
        </div>
    </div>

    <script>
        // Page Navigation
        document.querySelectorAll('.sidebar-menu li').forEach(item => {
            item.addEventListener('click', function() {
                // Remove active class from all menu items
                document.querySelectorAll('.sidebar-menu li').forEach(li => {
                    li.classList.remove('active');
                });
                
                // Add active class to clicked menu item
                this.classList.add('active');
                
                // Hide all pages
                document.querySelectorAll('.page').forEach(page => {
                    page.classList.remove('active');
                });
                
                // Show selected page
                const pageId = this.getAttribute('data-page');
                document.getElementById(pageId).classList.add('active');
            });
        });
        
        // Tab Navigation
        document.querySelectorAll('.tab').forEach(tab => {
            tab.addEventListener('click', function() {
                // Remove active class from all tabs
                document.querySelectorAll('.tab').forEach(t => {
                    t.classList.remove('active');
                });
                
                // Add active class to clicked tab
                this.classList.add('active');
                
                // Hide all tab contents
                document.querySelectorAll('.tab-content').forEach(content => {
                    content.classList.remove('active');
                });
                
                // Show selected tab content
                const tabId = this.getAttribute('data-tab');
                document.getElementById(tabId).classList.add('active');
            });
        });
        
        // Modal Handling
        const addPatientModal = document.getElementById('addPatientModal');
        const addPatientBtn = document.getElementById('addPatientBtn');
        const addPatientBtn2 = document.getElementById('addPatientBtn2');
        const cancelPatientBtn = document.getElementById('cancelPatientBtn');
        const closeModalBtn = document.querySelector('.close');
        
        // Open modal
        addPatientBtn.addEventListener('click', () => {
            addPatientModal.style.display = 'flex';
        });
        
        addPatientBtn2.addEventListener('click', () => {
            addPatientModal.style.display = 'flex';
        });
        
        // Close modal
        cancelPatientBtn.addEventListener('click', () => {
            addPatientModal.style.display = 'none';
        });
        
        closeModalBtn.addEventListener('click', () => {
            addPatientModal.style.display = 'none';
        });
        
        // Close modal when clicking outside
        window.addEventListener('click', (event) => {
            if (event.target === addPatientModal) {
                addPatientModal.style.display = 'none';
            }
        });
        
        // Form submission
        document.getElementById('savePatientBtn').addEventListener('click', () => {
            // In a real application, you would send this data to a server
            alert('Patient information saved successfully!');
            addPatientModal.style.display = 'none';
            document.getElementById('addPatientForm').reset();
        });
        
        // View Patient Details
        document.querySelectorAll('table button').forEach(button => {
            button.addEventListener('click', function() {
                // Hide all pages
                document.querySelectorAll('.page').forEach(page => {
                    page.classList.remove('active');
                });
                
                // Show patient details page
                document.getElementById('patient-details').classList.add('active');
                
                // Update sidebar active state
                document.querySelectorAll('.sidebar-menu li').forEach(li => {
                    li.classList.remove('active');
                });
                document.querySelector('[data-page="patients"]').classList.add('active');
            });
        });
    </script>
</body>
</html>
