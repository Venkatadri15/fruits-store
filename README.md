<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>AI InterviewPrep - Voice Interview Practice</title>
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.4.0/css/all.min.css">
    <style>
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
            font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
        }

        :root {
            --primary: #4361ee;
            --secondary: #3a0ca3;
            --accent: #4cc9f0;
            --light: #f8f9fa;
            --dark: #212529;
            --success: #4bb543;
            --gray: #6c757d;
            --light-gray: #e9ecef;
            --warning: #ff9e00;
            --danger: #e63946;
        }

        body {
            background-color: var(--light);
            color: var(--dark);
            overflow-x: hidden;
        }

        /* Header Styles */
        header {
            background-color: rgba(255, 255, 255, 0.95);
            backdrop-filter: blur(10px);
            box-shadow: 0 2px 20px rgba(0, 0, 0, 0.1);
            position: fixed;
            width: 100%;
            top: 0;
            z-index: 1000;
            transition: all 0.4s ease;
            transform: translateY(0);
        }

        header.scrolled {
            background-color: rgba(255, 255, 255, 0.98);
            box-shadow: 0 5px 25px rgba(0, 0, 0, 0.15);
            padding: 0.5rem 0;
        }

        .navbar {
            display: flex;
            justify-content: space-between;
            align-items: center;
            padding: 1.2rem 5%;
            transition: all 0.4s ease;
        }

        .logo {
            display: flex;
            align-items: center;
            font-weight: 800;
            font-size: 1.8rem;
            color: var(--primary);
            transition: all 0.3s ease;
            text-decoration: none;
        }

        .logo i {
            margin-right: 0.8rem;
            color: var(--secondary);
            font-size: 2rem;
            transition: all 0.3s ease;
        }

        .logo:hover {
            transform: translateY(-2px);
        }

        .logo:hover i {
            transform: rotate(15deg);
        }

        .nav-links {
            display: flex;
            list-style: none;
            gap: 2.5rem;
        }

        .nav-links li {
            position: relative;
        }

        .nav-links a {
            text-decoration: none;
            color: var(--dark);
            font-weight: 600;
            font-size: 1.1rem;
            transition: all 0.3s ease;
            padding: 0.5rem 0;
            position: relative;
        }

        .nav-links a::after {
            content: '';
            position: absolute;
            bottom: 0;
            left: 0;
            width: 0;
            height: 3px;
            background: linear-gradient(90deg, var(--primary), var(--secondary));
            transition: width 0.4s ease;
            border-radius: 2px;
        }

        .nav-links a:hover {
            color: var(--primary);
        }

        .nav-links a:hover::after {
            width: 100%;
        }

        .auth-buttons {
            display: flex;
            gap: 1.2rem;
        }

        .auth-buttons button {
            padding: 0.7rem 1.8rem;
            border: none;
            border-radius: 8px;
            font-weight: 700;
            cursor: pointer;
            transition: all 0.4s ease;
            font-size: 1rem;
            position: relative;
            overflow: hidden;
        }

        .login-btn {
            background: transparent;
            color: var(--primary);
            border: 2px solid var(--primary);
        }

        .login-btn::before {
            content: '';
            position: absolute;
            top: 0;
            left: -100%;
            width: 100%;
            height: 100%;
            background: linear-gradient(90deg, transparent, rgba(67, 97, 238, 0.1), transparent);
            transition: all 0.6s ease;
        }

        .login-btn:hover::before {
            left: 100%;
        }

        .login-btn:hover {
            transform: translateY(-3px);
            box-shadow: 0 8px 20px rgba(67, 97, 238, 0.2);
            background-color: rgba(67, 97, 238, 0.05);
        }

        .register-btn {
            background: linear-gradient(135deg, var(--primary), var(--secondary));
            color: white;
            box-shadow: 0 4px 15px rgba(67, 97, 238, 0.3);
        }

        .register-btn::before {
            content: '';
            position: absolute;
            top: 0;
            left: -100%;
            width: 100%;
            height: 100%;
            background: linear-gradient(90deg, transparent, rgba(255, 255, 255, 0.2), transparent);
            transition: all 0.6s ease;
        }

        .register-btn:hover::before {
            left: 100%;
        }

        .register-btn:hover {
            transform: translateY(-3px);
            box-shadow: 0 10px 25px rgba(67, 97, 238, 0.4);
        }

        /* Hero Section */
        .hero {
            height: 100vh;
            display: flex;
            align-items: center;
            justify-content: center;
            position: relative;
            overflow: hidden;
            background: linear-gradient(135deg, #4361ee, #3a0ca3);
            color: white;
            text-align: center;
            padding: 0 5%;
            margin-top: 0;
        }

        .hero-content {
            z-index: 2;
            max-width: 900px;
            animation: fadeInUp 1.2s ease-out;
        }

        .hero h1 {
            font-size: 4rem;
            margin-bottom: 1.8rem;
            font-weight: 800;
            line-height: 1.2;
            text-shadow: 0 2px 10px rgba(0, 0, 0, 0.2);
        }

        .hero p {
            font-size: 1.4rem;
            margin-bottom: 2.5rem;
            line-height: 1.6;
            opacity: 0.9;
            font-weight: 300;
        }

        .hero-buttons {
            display: flex;
            justify-content: center;
            gap: 1.5rem;
            animation: fadeInUp 1.2s ease-out 0.3s both;
        }

        .hero-buttons button {
            padding: 1rem 2.5rem;
            font-size: 1.2rem;
            border: none;
            border-radius: 10px;
            font-weight: 700;
            cursor: pointer;
            transition: all 0.4s ease;
            position: relative;
            overflow: hidden;
        }

        .start-btn {
            background-color: var(--accent);
            color: var(--dark);
            box-shadow: 0 6px 20px rgba(76, 201, 240, 0.4);
        }

        .start-btn:hover {
            transform: translateY(-5px);
            box-shadow: 0 12px 30px rgba(76, 201, 240, 0.6);
        }

        .demo-btn {
            background-color: transparent;
            color: white;
            border: 2px solid white;
        }

        .demo-btn:hover {
            background-color: rgba(255, 255, 255, 0.1);
            transform: translateY(-5px);
        }

        /* Background Animation */
        .bg-animation {
            position: absolute;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            overflow: hidden;
            z-index: 1;
        }

        .bg-animation div {
            position: absolute;
            width: 60px;
            height: 60px;
            background-color: rgba(255, 255, 255, 0.1);
            border-radius: 50%;
            bottom: -150px;
            animation: animate 25s linear infinite;
        }

        .bg-animation div:nth-child(1) {
            left: 25%;
            width: 80px;
            height: 80px;
            animation-delay: 0s;
        }

        .bg-animation div:nth-child(2) {
            left: 10%;
            width: 20px;
            height: 20px;
            animation-delay: 2s;
            animation-duration: 12s;
        }

        .bg-animation div:nth-child(3) {
            left: 70%;
            width: 20px;
            height: 20px;
            animation-delay: 4s;
        }

        .bg-animation div:nth-child(4) {
            left: 40%;
            width: 60px;
            height: 60px;
            animation-delay: 0s;
            animation-duration: 18s;
        }

        .bg-animation div:nth-child(5) {
            left: 65%;
            width: 20px;
            height: 20px;
            animation-delay: 0s;
        }

        .bg-animation div:nth-child(6) {
            left: 75%;
            width: 110px;
            height: 110px;
            animation-delay: 3s;
        }

        .bg-animation div:nth-child(7) {
            left: 35%;
            width: 150px;
            height: 150px;
            animation-delay: 7s;
        }

        .bg-animation div:nth-child(8) {
            left: 50%;
            width: 25px;
            height: 25px;
            animation-delay: 15s;
            animation-duration: 45s;
        }

        .bg-animation div:nth-child(9) {
            left: 20%;
            width: 15px;
            height: 15px;
            animation-delay: 2s;
            animation-duration: 35s;
        }

        .bg-animation div:nth-child(10) {
            left: 85%;
            width: 150px;
            height: 150px;
            animation-delay: 0s;
            animation-duration: 11s;
        }

        @keyframes animate {
            0% {
                transform: translateY(0) rotate(0deg);
                opacity: 1;
                border-radius: 0;
            }
            100% {
                transform: translateY(-1000px) rotate(720deg);
                opacity: 0;
                border-radius: 50%;
            }
        }

        /* Process Section */
        .process-section {
            padding: 8rem 5%;
            background-color: white;
        }

        .section-title {
            text-align: center;
            margin-bottom: 5rem;
        }

        .section-title h2 {
            font-size: 3rem;
            color: var(--secondary);
            margin-bottom: 1.5rem;
            font-weight: 800;
        }

        .section-title p {
            font-size: 1.3rem;
            color: var(--gray);
            max-width: 700px;
            margin: 0 auto;
            line-height: 1.6;
        }

        .process-steps {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(250px, 1fr));
            gap: 3rem;
            max-width: 1200px;
            margin: 0 auto;
        }

        .step {
            text-align: center;
            padding: 2.5rem 1.5rem;
            border-radius: 20px;
            background-color: var(--light);
            box-shadow: 0 10px 30px rgba(0, 0, 0, 0.05);
            transition: all 0.4s ease;
            position: relative;
            overflow: hidden;
        }

        .step:hover {
            transform: translateY(-10px);
            box-shadow: 0 20px 40px rgba(0, 0, 0, 0.1);
        }

        .step-number {
            position: absolute;
            top: 20px;
            left: 20px;
            width: 40px;
            height: 40px;
            background: linear-gradient(135deg, var(--primary), var(--secondary));
            color: white;
            border-radius: 50%;
            display: flex;
            align-items: center;
            justify-content: center;
            font-weight: 800;
            font-size: 1.2rem;
        }

        .step-icon {
            width: 80px;
            height: 80px;
            background: linear-gradient(135deg, var(--primary), var(--secondary));
            border-radius: 50%;
            display: flex;
            align-items: center;
            justify-content: center;
            margin: 0 auto 2rem;
            color: white;
            font-size: 2rem;
        }

        .step h3 {
            font-size: 1.5rem;
            margin-bottom: 1.5rem;
            color: var(--secondary);
            font-weight: 700;
        }

        .step p {
            color: var(--gray);
            line-height: 1.6;
        }

        /* Features Section */
        .features-section {
            padding: 8rem 5%;
            background-color: var(--light);
        }

        .features-grid {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(300px, 1fr));
            gap: 3rem;
            max-width: 1200px;
            margin: 0 auto;
        }

        .feature-card {
            background-color: white;
            border-radius: 20px;
            padding: 3rem 2rem;
            box-shadow: 0 10px 30px rgba(0, 0, 0, 0.05);
            text-align: center;
            transition: all 0.4s ease;
        }

        .feature-card:hover {
            transform: translateY(-10px);
            box-shadow: 0 20px 40px rgba(0, 0, 0, 0.1);
        }

        .feature-icon {
            width: 100px;
            height: 100px;
            background: linear-gradient(135deg, var(--primary), var(--secondary));
            border-radius: 50%;
            display: flex;
            align-items: center;
            justify-content: center;
            margin: 0 auto 2rem;
            color: white;
            font-size: 2.5rem;
        }

        .feature-card h3 {
            font-size: 1.8rem;
            margin-bottom: 1.5rem;
            color: var(--secondary);
            font-weight: 700;
        }

        .feature-card p {
            color: var(--gray);
            line-height: 1.6;
            margin-bottom: 2rem;
        }

        .feature-btn {
            padding: 0.8rem 2rem;
            background: linear-gradient(135deg, var(--primary), var(--secondary));
            color: white;
            border: none;
            border-radius: 8px;
            font-weight: 600;
            cursor: pointer;
            transition: all 0.3s ease;
        }

        .feature-btn:hover {
            transform: translateY(-3px);
            box-shadow: 0 10px 20px rgba(67, 97, 238, 0.3);
        }

        /* Stats Section */
        .stats-section {
            padding: 6rem 5%;
            background: linear-gradient(135deg, var(--primary), var(--secondary));
            color: white;
            text-align: center;
        }

        .stats-grid {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(200px, 1fr));
            gap: 3rem;
            max-width: 1200px;
            margin: 0 auto;
        }

        .stat-item {
            padding: 2rem;
        }

        .stat-number {
            display: block;
            font-size: 3.5rem;
            font-weight: 800;
            margin-bottom: 0.5rem;
        }

        .stat-label {
            font-size: 1.2rem;
            opacity: 0.9;
        }

        /* Footer */
        footer {
            background-color: var(--dark);
            color: white;
            padding: 4rem 5% 2rem;
            text-align: center;
        }

        .social-links {
            display: flex;
            justify-content: center;
            gap: 1.5rem;
            margin-bottom: 2rem;
        }

        .social-links a {
            width: 50px;
            height: 50px;
            border-radius: 50%;
            background-color: rgba(255, 255, 255, 0.1);
            display: flex;
            align-items: center;
            justify-content: center;
            color: white;
            font-size: 1.5rem;
            transition: all 0.3s ease;
            text-decoration: none;
        }

        .social-links a:hover {
            background-color: var(--primary);
            transform: translateY(-5px);
        }

        footer p {
            opacity: 0.7;
            font-size: 1rem;
        }

        /* Auth Pages */
        .auth-page {
            display: none;
            min-height: 100vh;
            background: linear-gradient(135deg, #4361ee, #3a0ca3);
            padding: 2rem 5%;
            align-items: center;
            justify-content: center;
        }

        .auth-container {
            background-color: white;
            border-radius: 20px;
            box-shadow: 0 15px 50px rgba(0, 0, 0, 0.2);
            width: 100%;
            max-width: 500px;
            overflow: hidden;
            animation: slideUp 0.4s ease;
        }

        .auth-header {
            background: linear-gradient(135deg, var(--primary), var(--secondary));
            color: white;
            padding: 2.5rem 2rem;
            text-align: center;
            position: relative;
        }

        .auth-header h2 {
            font-size: 2.2rem;
            margin-bottom: 0.5rem;
            font-weight: 800;
        }

        .auth-header p {
            opacity: 0.9;
            font-size: 1.1rem;
        }

        .back-to-home {
            position: absolute;
            top: 20px;
            left: 20px;
            background: rgba(255, 255, 255, 0.2);
            border: none;
            color: white;
            width: 40px;
            height: 40px;
            border-radius: 50%;
            display: flex;
            align-items: center;
            justify-content: center;
            cursor: pointer;
            transition: all 0.3s ease;
        }

        .back-to-home:hover {
            background: rgba(255, 255, 255, 0.3);
            transform: translateX(-3px);
        }

        .auth-form {
            padding: 2.5rem 2rem;
        }

        .form-group {
            margin-bottom: 1.5rem;
        }

        .form-group label {
            display: block;
            margin-bottom: 0.5rem;
            font-weight: 600;
            color: var(--dark);
            font-size: 1.1rem;
        }

        .form-group input {
            width: 100%;
            padding: 1rem 1.2rem;
            border: 1px solid var(--light-gray);
            border-radius: 10px;
            font-size: 1rem;
            transition: all 0.3s ease;
            background-color: var(--light);
        }

        .form-group input:focus {
            outline: none;
            border-color: var(--primary);
            box-shadow: 0 0 0 3px rgba(67, 97, 238, 0.1);
            background-color: white;
        }

        .form-options {
            display: flex;
            justify-content: space-between;
            align-items: center;
            margin-bottom: 1.5rem;
        }

        .remember-me {
            display: flex;
            align-items: center;
            gap: 0.5rem;
        }

        .remember-me input {
            width: auto;
        }

        .forgot-password {
            color: var(--primary);
            text-decoration: none;
            font-weight: 600;
            transition: all 0.3s ease;
        }

        .forgot-password:hover {
            color: var(--secondary);
            text-decoration: underline;
        }

        .auth-submit {
            width: 100%;
            padding: 1.2rem;
            background: linear-gradient(135deg, var(--primary), var(--secondary));
            color: white;
            border: none;
            border-radius: 10px;
            font-size: 1.1rem;
            font-weight: 700;
            cursor: pointer;
            transition: all 0.4s ease;
            margin-top: 1rem;
            position: relative;
            overflow: hidden;
        }

        .auth-submit::before {
            content: '';
            position: absolute;
            top: 0;
            left: -100%;
            width: 100%;
            height: 100%;
            background: linear-gradient(90deg, transparent, rgba(255, 255, 255, 0.2), transparent);
            transition: all 0.6s ease;
        }

        .auth-submit:hover::before {
            left: 100%;
        }

        .auth-submit:hover {
            transform: translateY(-3px);
            box-shadow: 0 10px 25px rgba(67, 97, 238, 0.4);
        }

        .auth-footer {
            text-align: center;
            padding: 1.5rem 2rem 2.5rem;
            color: var(--gray);
            border-top: 1px solid var(--light-gray);
        }

        .auth-footer a {
            color: var(--primary);
            text-decoration: none;
            font-weight: 600;
            transition: all 0.3s ease;
        }

        .auth-footer a:hover {
            color: var(--secondary);
            text-decoration: underline;
        }

        .social-login {
            margin: 2rem 0;
            text-align: center;
        }

        .social-login p {
            margin-bottom: 1rem;
            color: var(--gray);
            position: relative;
        }

        .social-login p::before, .social-login p::after {
            content: '';
            position: absolute;
            top: 50%;
            width: 30%;
            height: 1px;
            background-color: var(--light-gray);
        }

        .social-login p::before {
            left: 0;
        }

        .social-login p::after {
            right: 0;
        }

        .social-buttons {
            display: flex;
            gap: 1rem;
            justify-content: center;
        }

        .social-btn {
            width: 50px;
            height: 50px;
            border-radius: 50%;
            border: 1px solid var(--light-gray);
            background: white;
            display: flex;
            align-items: center;
            justify-content: center;
            cursor: pointer;
            transition: all 0.3s ease;
            font-size: 1.2rem;
        }

        .social-btn.google {
            color: #DB4437;
        }

        .social-btn.facebook {
            color: #4267B2;
        }

        .social-btn.linkedin {
            color: #0077B5;
        }

        .social-btn:hover {
            transform: translateY(-3px);
            box-shadow: 0 5px 15px rgba(0, 0, 0, 0.1);
        }

        @keyframes slideUp {
            from { 
                opacity: 0;
                transform: translateY(50px);
            }
            to { 
                opacity: 1;
                transform: translateY(0);
            }
        }

        @keyframes fadeIn {
            from { opacity: 0; }
            to { opacity: 1; }
        }

        /* Dashboard Styles */
        .dashboard {
            display: none;
            min-height: 100vh;
            background-color: var(--light);
        }

        .dashboard-header {
            background: white;
            padding: 1.5rem 5%;
            display: flex;
            justify-content: space-between;
            align-items: center;
            box-shadow: 0 2px 10px rgba(0, 0, 0, 0.05);
            border-bottom: 1px solid var(--light-gray);
        }

        .dashboard-logo {
            display: flex;
            align-items: center;
            font-weight: 800;
            font-size: 1.8rem;
            color: var(--primary);
        }

        .dashboard-logo i {
            margin-right: 0.8rem;
            color: var(--secondary);
            font-size: 2rem;
        }

        .user-profile {
            display: flex;
            align-items: center;
            gap: 1rem;
        }

        .profile-image {
            width: 50px;
            height: 50px;
            border-radius: 50%;
            background: linear-gradient(135deg, var(--primary), var(--secondary));
            display: flex;
            align-items: center;
            justify-content: center;
            color: white;
            font-size: 1.5rem;
        }

        .profile-info h3 {
            font-size: 1.2rem;
            font-weight: 700;
            margin-bottom: 0.2rem;
        }

        .profile-info p {
            color: var(--gray);
            font-size: 0.9rem;
        }

        .dashboard-content {
            display: flex;
            min-height: calc(100vh - 80px);
        }

        .sidebar {
            width: 300px;
            background: white;
            padding: 2rem 0;
            box-shadow: 2px 0 10px rgba(0, 0, 0, 0.05);
            border-right: 1px solid var(--light-gray);
        }

        .profile-card {
            padding: 0 2rem 2rem;
            border-bottom: 1px solid var(--light-gray);
            margin-bottom: 2rem;
            text-align: center;
        }

        .profile-avatar {
            width: 100px;
            height: 100px;
            border-radius: 50%;
            background: linear-gradient(135deg, var(--primary), var(--secondary));
            margin: 0 auto 1rem;
            display: flex;
            align-items: center;
            justify-content: center;
            color: white;
            font-size: 2.5rem;
        }

        .profile-name {
            font-size: 1.4rem;
            font-weight: 700;
            margin-bottom: 0.5rem;
        }

        .profile-title {
            color: var(--gray);
            font-size: 1rem;
            margin-bottom: 1rem;
        }

        .profile-stats {
            display: flex;
            justify-content: space-around;
            margin-top: 1.5rem;
        }

        .stat {
            text-align: center;
        }

        .stat-value {
            font-size: 1.5rem;
            font-weight: 800;
            color: var(--primary);
            display: block;
        }

        .stat-label {
            font-size: 0.8rem;
            color: var(--gray);
        }

        .sidebar-menu {
            list-style: none;
        }

        .sidebar-menu li {
            margin-bottom: 0.5rem;
        }

        .sidebar-menu a {
            display: flex;
            align-items: center;
            gap: 1rem;
            padding: 1rem 2rem;
            text-decoration: none;
            color: var(--dark);
            transition: all 0.3s ease;
        }

        .sidebar-menu a:hover, .sidebar-menu a.active {
            background-color: rgba(67, 97, 238, 0.1);
            color: var(--primary);
            border-right: 3px solid var(--primary);
        }

        .sidebar-menu a i {
            width: 20px;
            text-align: center;
        }

        .main-content {
            flex: 1;
            padding: 2rem;
            background-color: var(--light);
            overflow-y: auto;
        }

        .search-bar {
            background: white;
            border-radius: 10px;
            padding: 1rem 1.5rem;
            box-shadow: 0 5px 15px rgba(0, 0, 0, 0.05);
            margin-bottom: 2rem;
            display: flex;
            align-items: center;
            gap: 1rem;
        }

        .search-bar input {
            flex: 1;
            border: none;
            outline: none;
            font-size: 1.1rem;
            padding: 0.5rem 0;
        }

        .search-bar i {
            color: var(--gray);
            font-size: 1.2rem;
        }

        .levels-section {
            margin-bottom: 3rem;
        }

        .section-heading {
            font-size: 1.8rem;
            margin-bottom: 1.5rem;
            color: var(--secondary);
            font-weight: 700;
            display: flex;
            align-items: center;
            gap: 1rem;
        }

        .section-heading i {
            color: var(--primary);
        }

        .levels-grid {
            display: grid;
            grid-template-columns: repeat(auto-fill, minmax(300px, 1fr));
            gap: 1.5rem;
        }

        .level-card {
            background: white;
            border-radius: 15px;
            padding: 1.5rem;
            box-shadow: 0 5px 15px rgba(0, 0, 0, 0.05);
            transition: all 0.4s ease;
            cursor: pointer;
            position: relative;
            overflow: hidden;
        }

        .level-card::before {
            content: '';
            position: absolute;
            top: 0;
            left: 0;
            width: 5px;
            height: 100%;
            background: linear-gradient(to bottom, var(--primary), var(--secondary));
        }

        .level-card:hover {
            transform: translateY(-5px);
            box-shadow: 0 15px 30px rgba(0, 0, 0, 0.1);
        }

        .level-header {
            display: flex;
            justify-content: space-between;
            align-items: center;
            margin-bottom: 1rem;
        }

        .level-title {
            font-size: 1.3rem;
            font-weight: 700;
            color: var(--secondary);
        }

        .level-badge {
            background: linear-gradient(135deg, var(--primary), var(--secondary));
            color: white;
            padding: 0.3rem 0.8rem;
            border-radius: 20px;
            font-size: 0.8rem;
            font-weight: 600;
        }

        .level-roles {
            display: flex;
            flex-wrap: wrap;
            gap: 0.5rem;
        }

        .role-tag {
            background-color: var(--light-gray);
            padding: 0.4rem 0.8rem;
            border-radius: 20px;
            font-size: 0.9rem;
            transition: all 0.3s ease;
            cursor: pointer;
        }

        .role-tag:hover {
            background-color: var(--primary);
            color: white;
        }

        /* Interview Page */
        .interview-page {
            display: none;
            min-height: 100vh;
            background-color: var(--light);
        }

        .interview-container {
            max-width: 1200px;
            margin: 0 auto;
            padding: 2rem;
        }

        .interview-header {
            background: white;
            border-radius: 15px;
            padding: 2rem;
            box-shadow: 0 5px 15px rgba(0, 0, 0, 0.05);
            margin-bottom: 2rem;
            display: flex;
            justify-content: space-between;
            align-items: center;
        }

        .interview-info h2 {
            font-size: 2rem;
            color: var(--secondary);
            margin-bottom: 0.5rem;
        }

        .interview-info p {
            color: var(--gray);
            font-size: 1.1rem;
        }

        .interview-timer {
            background: linear-gradient(135deg, var(--primary), var(--secondary));
            color: white;
            padding: 1rem 1.5rem;
            border-radius: 10px;
            font-size: 1.5rem;
            font-weight: 700;
        }

        .interview-content {
            display: flex;
            gap: 2rem;
        }

        .interview-questions {
            flex: 1;
            background: white;
            border-radius: 15px;
            padding: 2rem;
            box-shadow: 0 5px 15px rgba(0, 0, 0, 0.05);
        }

        .question-section {
            margin-bottom: 2rem;
        }

        .section-title {
            font-size: 1.5rem;
            color: var(--secondary);
            margin-bottom: 1rem;
            font-weight: 700;
            display: flex;
            align-items: center;
            gap: 0.8rem;
        }

        .section-title i {
            color: var(--primary);
        }

        .question-list {
            list-style: none;
        }

        .question-item {
            padding: 1.2rem;
            border-radius: 10px;
            margin-bottom: 1rem;
            background-color: var(--light);
            transition: all 0.3s ease;
            cursor: pointer;
        }

        .question-item.active {
            background-color: rgba(67, 97, 238, 0.1);
            border-left: 4px solid var(--primary);
        }

        .question-item:hover {
            background-color: rgba(67, 97, 238, 0.05);
        }

        .interview-controls {
            width: 350px;
            background: white;
            border-radius: 15px;
            padding: 2rem;
            box-shadow: 0 5px 15px rgba(0, 0, 0, 0.05);
            display: flex;
            flex-direction: column;
            gap: 1.5rem;
        }

        .avatar-container {
            text-align: center;
            margin-bottom: 1rem;
        }

        .interview-avatar {
            width: 120px;
            height: 120px;
            border-radius: 50%;
            background: linear-gradient(135deg, var(--primary), var(--secondary));
            margin: 0 auto 1rem;
            display: flex;
            align-items: center;
            justify-content: center;
            color: white;
            font-size: 3rem;
            position: relative;
        }

        .avatar-pulse {
            position: absolute;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            border-radius: 50%;
            background: rgba(67, 97, 238, 0.3);
            animation: pulse 2s infinite;
        }

        .speaking .avatar-pulse {
            background: rgba(76, 201, 240, 0.5);
            animation: pulse 1s infinite;
        }

        .control-buttons {
            display: flex;
            flex-direction: column;
            gap: 1rem;
        }

        .control-btn {
            padding: 1rem;
            border: none;
            border-radius: 10px;
            font-weight: 600;
            cursor: pointer;
            transition: all 0.3s ease;
            display: flex;
            align-items: center;
            justify-content: center;
            gap: 0.8rem;
        }

        .start-btn {
            background: linear-gradient(135deg, var(--primary), var(--secondary));
            color: white;
        }

        .start-btn:hover {
            transform: translateY(-3px);
            box-shadow: 0 10px 25px rgba(67, 97, 238, 0.4);
        }

        .record-btn {
            background: var(--light);
            color: var(--dark);
            border: 1px solid var(--light-gray);
        }

        .record-btn:hover {
            background: var(--light-gray);
        }

        .record-btn.recording {
            background: var(--danger);
            color: white;
        }

        .download-btn {
            background: var(--success);
            color: white;
        }

        .download-btn:hover {
            background: #3a9a36;
            transform: translateY(-3px);
        }

        .progress-section {
            margin-top: 1rem;
        }

        .progress-bar {
            height: 8px;
            background-color: var(--light-gray);
            border-radius: 4px;
            overflow: hidden;
            margin-bottom: 0.5rem;
        }

        .progress-fill {
            height: 100%;
            background: linear-gradient(135deg, var(--primary), var(--secondary));
            border-radius: 4px;
            width: 0%;
            transition: width 0.5s ease;
        }

        .progress-text {
            font-size: 0.9rem;
            color: var(--gray);
            text-align: center;
        }

        .recordings-list {
            margin-top: 2rem;
        }

        .recordings-list h3 {
            font-size: 1.3rem;
            margin-bottom: 1rem;
            color: var(--secondary);
        }

        .recording-item {
            display: flex;
            justify-content: space-between;
            align-items: center;
            padding: 1rem;
            background: var(--light);
            border-radius: 10px;
            margin-bottom: 0.5rem;
        }

        .recording-info {
            display: flex;
            flex-direction: column;
        }

        .recording-name {
            font-weight: 600;
        }

        .recording-date {
            font-size: 0.8rem;
            color: var(--gray);
        }

        .recording-actions {
            display: flex;
            gap: 0.5rem;
        }

        .action-btn {
            padding: 0.5rem;
            border: none;
            border-radius: 5px;
            background: var(--light-gray);
            cursor: pointer;
            transition: all 0.3s ease;
        }

        .action-btn:hover {
            background: var(--primary);
            color: white;
        }

        /* Exit Button Styles */
        .exit-btn {
            position: absolute;
            top: 20px;
            right: 20px;
            background: var(--danger);
            color: white;
            border: none;
            width: 40px;
            height: 40px;
            border-radius: 50%;
            display: flex;
            align-items: center;
            justify-content: center;
            cursor: pointer;
            transition: all 0.3s ease;
            z-index: 10;
        }

        .exit-btn:hover {
            background: #c82333;
            transform: scale(1.1);
        }

        /* Voice Controls */
        .voice-controls {
            display: flex;
            gap: 1rem;
            margin-top: 1rem;
        }

        .voice-btn {
            flex: 1;
            padding: 0.8rem;
            border: none;
            border-radius: 8px;
            font-weight: 600;
            cursor: pointer;
            transition: all 0.3s ease;
            display: flex;
            align-items: center;
            justify-content: center;
            gap: 0.5rem;
        }

        .voice-btn.play {
            background: var(--primary);
            color: white;
        }

        .voice-btn.play:hover {
            background: #3a56d4;
        }

        .voice-btn.stop {
            background: var(--danger);
            color: white;
        }

        .voice-btn.stop:hover {
            background: #d32f2f;
        }

        .voice-btn:disabled {
            background: var(--light-gray);
            color: var(--gray);
            cursor: not-allowed;
        }

        /* Navigation Controls */
        .navigation-controls {
            display: flex;
            gap: 1rem;
            margin-top: 1rem;
        }

        .nav-btn {
            flex: 1;
            padding: 0.8rem;
            border: none;
            border-radius: 8px;
            font-weight: 600;
            cursor: pointer;
            transition: all 0.3s ease;
            display: flex;
            align-items: center;
            justify-content: center;
            gap: 0.5rem;
        }

        .nav-btn.back {
            background: var(--light);
            color: var(--dark);
            border: 1px solid var(--light-gray);
        }

        .nav-btn.back:hover {
            background: var(--light-gray);
        }

        .nav-btn.next {
            background: var(--primary);
            color: white;
        }

        .nav-btn.next:hover {
            background: #3a56d4;
        }

        .nav-btn:disabled {
            background: var(--light-gray);
            color: var(--gray);
            cursor: not-allowed;
        }

        /* Video Recording Styles */
        .video-recording {
            margin-top: 2rem;
            background: white;
            border-radius: 15px;
            padding: 1.5rem;
            box-shadow: 0 5px 15px rgba(0, 0, 0, 0.05);
        }

        .video-recording h3 {
            font-size: 1.3rem;
            margin-bottom: 1rem;
            color: var(--secondary);
            display: flex;
            align-items: center;
            gap: 0.8rem;
        }

        .video-recording h3 i {
            color: var(--primary);
        }

        .video-container {
            position: relative;
            width: 100%;
            height: 300px;
            background-color: var(--dark);
            border-radius: 10px;
            overflow: hidden;
            margin-bottom: 1rem;
        }

        .video-preview {
            width: 100%;
            height: 100%;
            object-fit: cover;
            background-color: var(--dark);
        }

        .video-overlay {
            position: absolute;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            display: flex;
            align-items: center;
            justify-content: center;
            background-color: rgba(0, 0, 0, 0.5);
            color: white;
            font-size: 1.2rem;
            text-align: center;
            padding: 1rem;
        }

        .recording-indicator {
            position: absolute;
            top: 10px;
            right: 10px;
            display: flex;
            align-items: center;
            gap: 0.5rem;
            background: rgba(0, 0, 0, 0.7);
            color: white;
            padding: 0.5rem 1rem;
            border-radius: 20px;
            font-size: 0.9rem;
            font-weight: 600;
        }

        .recording-dot {
            width: 12px;
            height: 12px;
            background-color: var(--danger);
            border-radius: 50%;
            animation: pulse 1.5s infinite;
        }

        .video-controls {
            display: flex;
            gap: 1rem;
            justify-content: center;
        }

        .video-btn {
            padding: 0.8rem 1.5rem;
            border: none;
            border-radius: 8px;
            font-weight: 600;
            cursor: pointer;
            transition: all 0.3s ease;
            display: flex;
            align-items: center;
            justify-content: center;
            gap: 0.5rem;
        }

        .video-btn.start {
            background: var(--primary);
            color: white;
        }

        .video-btn.start:hover {
            background: #3a56d4;
        }

        .video-btn.stop {
            background: var(--danger);
            color: white;
        }

        .video-btn.stop:hover {
            background: #d32f2f;
        }

        .video-btn.download {
            background: var(--success);
            color: white;
        }

        .video-btn.download:hover {
            background: #3a9a36;
        }

        .video-btn:disabled {
            background: var(--light-gray);
            color: var(--gray);
            cursor: not-allowed;
        }

        /* AI Feedback Section */
        .feedback-section {
            margin-top: 2rem;
            background: white;
            border-radius: 15px;
            padding: 1.5rem;
            box-shadow: 0 5px 15px rgba(0, 0, 0, 0.05);
        }

        .feedback-section h3 {
            font-size: 1.3rem;
            margin-bottom: 1rem;
            color: var(--secondary);
            display: flex;
            align-items: center;
            gap: 0.8rem;
        }

        .feedback-section h3 i {
            color: var(--primary);
        }

        .feedback-content {
            max-height: 300px;
            overflow-y: auto;
            padding: 1rem;
            background: var(--light);
            border-radius: 10px;
            margin-bottom: 1rem;
        }

        .feedback-item {
            padding: 1rem;
            margin-bottom: 1rem;
            border-radius: 8px;
            background: white;
            border-left: 4px solid var(--primary);
        }

        .feedback-question {
            font-weight: 600;
            margin-bottom: 0.5rem;
            color: var(--secondary);
        }

        .feedback-analysis {
            color: var(--dark);
            line-height: 1.5;
        }

        .feedback-metrics {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(150px, 1fr));
            gap: 1rem;
            margin-top: 1rem;
        }

        .metric {
            text-align: center;
            padding: 1rem;
            background: var(--light);
            border-radius: 8px;
        }

        .metric-value {
            font-size: 1.5rem;
            font-weight: 700;
            color: var(--primary);
            display: block;
        }

        .metric-label {
            font-size: 0.8rem;
            color: var(--gray);
        }

        .feedback-actions {
            display: flex;
            gap: 1rem;
            margin-top: 1rem;
        }

        .feedback-btn {
            flex: 1;
            padding: 0.8rem;
            border: none;
            border-radius: 8px;
            font-weight: 600;
            cursor: pointer;
            transition: all 0.3s ease;
            display: flex;
            align-items: center;
            justify-content: center;
            gap: 0.5rem;
        }

        .feedback-btn.analyze {
            background: var(--primary);
            color: white;
        }

        .feedback-btn.analyze:hover {
            background: #3a56d4;
        }

        .feedback-btn.download {
            background: var(--success);
            color: white;
        }

        .feedback-btn.download:hover {
            background: #3a9a36;
        }

        /* Animations */
        @keyframes fadeInUp {
            from {
                opacity: 0;
                transform: translateY(50px);
            }
            to {
                opacity: 1;
                transform: translateY(0);
            }
        }

        @keyframes pulse {
            0% {
                transform: scale(1);
                opacity: 1;
            }
            50% {
                transform: scale(1.1);
                opacity: 0.7;
            }
            100% {
                transform: scale(1);
                opacity: 1;
            }
        }

        .pulse {
            animation: pulse 2s infinite;
        }

        /* Responsive Design */
        @media (max-width: 768px) {
            .navbar {
                flex-direction: column;
                padding: 1rem;
            }

            .nav-links {
                margin: 1.5rem 0;
                flex-wrap: wrap;
                justify-content: center;
                gap: 1.5rem;
            }

            .auth-buttons {
                margin-top: 1rem;
            }

            .hero h1 {
                font-size: 2.8rem;
            }

            .hero p {
                font-size: 1.2rem;
            }

            .form-options {
                flex-direction: column;
                gap: 1rem;
                align-items: flex-start;
            }

            .social-buttons {
                flex-wrap: wrap;
            }

            .dashboard-content {
                flex-direction: column;
            }

            .sidebar {
                width: 100%;
                order: 2;
            }

            .main-content {
                order: 1;
            }

            .levels-grid {
                grid-template-columns: 1fr;
            }

            .interview-content {
                flex-direction: column;
            }

            .interview-controls {
                width: 100%;
            }
            
            .exit-btn {
                top: 15px;
                right: 15px;
                width: 35px;
                height: 35px;
            }

            .video-container {
                height: 250px;
            }

            .feedback-metrics {
                grid-template-columns: 1fr 1fr;
            }
        }
    </style>
</head>
<body>
    <!-- Main Landing Page -->
    <div id="landing-page">
        <!-- Header -->
        <header id="main-header">
            <nav class="navbar">
                <a href="#" class="logo">
                    <i class="fas fa-robot"></i>
                    AI InterviewPrep
                </a>
                <ul class="nav-links">
                    <li><a href="#">Home</a></li>
                    <li><a href="#" id="about-link">About</a></li>
                    <li><a href="#" id="process-link">Process</a></li>
                    <li><a href="#" id="features-link">Features</a></li>
                </ul>
                <div class="auth-buttons">
                    <button class="login-btn" id="login-btn">Login</button>
                    <button class="register-btn" id="register-btn">Register</button>
                </div>
            </nav>
        </header>

        <!-- Hero Section -->
        <section class="hero" id="hero-section">
            <div class="bg-animation">
                <div></div>
                <div></div>
                <div></div>
                <div></div>
                <div></div>
                <div></div>
                <div></div>
                <div></div>
                <div></div>
                <div></div>
            </div>
            <div class="hero-content">
                <h1>Master Your Interviews with AI</h1>
                <p>Our AI-powered platform helps you prepare for interviews with personalized questions, real-time feedback, and performance analytics. Practice with our intelligent system and boost your confidence for your next job interview.</p>
                <div class="hero-buttons">
                    <button class="start-btn pulse" id="start-practice-btn">Start Practice Now</button>
                    <button class="demo-btn" id="demo-btn">Watch Demo</button>
                </div>
            </div>
        </section>

        <!-- Process Section -->
        <section class="process-section" id="process">
            <div class="section-title">
                <h2>How It Works</h2>
                <p>Our step-by-step process helps you prepare effectively for any interview scenario</p>
            </div>
            <div class="process-steps">
                <div class="step">
                    <div class="step-number">1</div>
                    <div class="step-icon">
                        <i class="fas fa-user-plus"></i>
                    </div>
                    <h3>Create Account</h3>
                    <p>Sign up for free and set up your profile with your career interests and experience level. Our AI will personalize your practice sessions based on your goals.</p>
                </div>
                <div class="step">
                    <div class="step-number">2</div>
                    <div class="step-icon">
                        <i class="fas fa-clipboard-list"></i>
                    </div>
                    <h3>Select Interview Type</h3>
                    <p>Choose from various interview types - technical, behavioral, HR, or industry-specific. We cover all major job roles and industries.</p>
                </div>
                <div class="step">
                    <div class="step-number">3</div>
                    <div class="step-icon">
                        <i class="fas fa-microphone"></i>
                    </div>
                    <h3>Practice with AI</h3>
                    <p>Answer AI-generated questions and receive real-time feedback on your responses. Our system analyzes your content, clarity, and communication style.</p>
                </div>
                <div class="step">
                    <div class="step-number">4</div>
                    <div class="step-icon">
                        <i class="fas fa-chart-line"></i>
                    </div>
                    <h3>Track Progress</h3>
                    <p>Monitor your improvement with detailed analytics and personalized recommendations. See how you compare to other candidates and identify areas for growth.</p>
                </div>
            </div>
        </section>

        <!-- Features Section -->
        <section class="features-section" id="features">
            <div class="section-title">
                <h2>Our Powerful Features</h2>
                <p>Discover the advanced tools that will help you ace your interviews</p>
            </div>
            <div class="features-grid">
                <div class="feature-card">
                    <div class="feature-icon">
                        <i class="fas fa-comments"></i>
                    </div>
                    <h3>Mock Interviews</h3>
                    <p>Practice with realistic interview simulations tailored to your target job role and industry. Experience the pressure of real interviews in a safe environment.</p>
                    <button class="feature-btn" id="mock-interview-btn">Try Now</button>
                </div>
                <div class="feature-card">
                    <div class="feature-icon">
                        <i class="fas fa-brain"></i>
                    </div>
                    <h3>AI Feedback</h3>
                    <p>Get instant feedback on your answers, including content, clarity, and communication style. Our AI analyzes your responses like a human interviewer would.</p>
                    <button class="feature-btn" id="ai-feedback-btn">Try Now</button>
                </div>
                <div class="feature-card">
                    <div class="feature-icon">
                        <i class="fas fa-file-alt"></i>
                    </div>
                    <h3>Resume Analysis</h3>
                    <p>Upload your resume and get personalized interview questions based on your experience. We'll help you highlight your strengths and prepare for relevant questions.</p>
                    <button class="feature-btn" id="resume-analysis-btn">Try Now</button>
                </div>
            </div>
        </section>

        <!-- Stats Section -->
        <section class="stats-section">
            <div class="section-title">
                <h2>Our Impact</h2>
                <p>Join thousands of users who have improved their interview skills with our platform</p>
            </div>
            <div class="stats-grid">
                <div class="stat-item">
                    <span class="stat-number">10,000+</span>
                    <span class="stat-label">Users</span>
                </div>
                <div class="stat-item">
                    <span class="stat-number">95%</span>
                    <span class="stat-label">Success Rate</span>
                </div>
                <div class="stat-item">
                    <span class="stat-number">50,000+</span>
                    <span class="stat-label">Interviews Practiced</span>
                </div>
                <div class="stat-item">
                    <span class="stat-number">4.9/5</span>
                    <span class="stat-label">User Rating</span>
                </div>
            </div>
        </section>

        <!-- Footer -->
        <footer>
            <div class="social-links">
                <a href="#"><i class="fab fa-facebook"></i></a>
                <a href="#"><i class="fab fa-twitter"></i></a>
                <a href="#"><i class="fab fa-instagram"></i></a>
                <a href="#"><i class="fab fa-linkedin"></i></a>
            </div>
            <p>&copy; 2023 AI InterviewPrep. All rights reserved.</p>
        </footer>
    </div>

    <!-- Login Page -->
    <div class="auth-page" id="login-page">
        <div class="auth-container">
            <div class="auth-header">
                <button class="back-to-home" id="back-from-login">
                    <i class="fas fa-arrow-left"></i>
                </button>
                <h2>Welcome Back</h2>
                <p>Sign in to your account to continue your interview preparation</p>
            </div>
            <form class="auth-form" id="login-form">
                <div class="form-group">
                    <label for="login-email">Email Address</label>
                    <input type="email" id="login-email" placeholder="Enter your email" required>
                </div>
                <div class="form-group">
                    <label for="login-password">Password</label>
                    <input type="password" id="login-password" placeholder="Enter your password" required>
                </div>
                <div class="form-options">
                    <div class="remember-me">
                        <input type="checkbox" id="remember-me">
                        <label for="remember-me">Remember me</label>
                    </div>
                    <a href="#" class="forgot-password">Forgot password?</a>
                </div>
                <button type="submit" class="auth-submit">Sign In</button>
                
                <div class="social-login">
                    <p>Or continue with</p>
                    <div class="social-buttons">
                        <button type="button" class="social-btn google">
                            <i class="fab fa-google"></i>
                        </button>
                        <button type="button" class="social-btn facebook">
                            <i class="fab fa-facebook-f"></i>
                        </button>
                        <button type="button" class="social-btn linkedin">
                            <i class="fab fa-linkedin-in"></i>
                        </button>
                    </div>
                </div>
            </form>
            <div class="auth-footer">
                <p>Don't have an account? <a href="#" id="go-to-register">Sign up now</a></p>
            </div>
        </div>
    </div>

    <!-- Register Page -->
    <div class="auth-page" id="register-page">
        <div class="auth-container">
            <div class="auth-header">
                <button class="back-to-home" id="back-from-register">
                    <i class="fas fa-arrow-left"></i>
                </button>
                <h2>Create Account</h2>
                <p>Sign up to start preparing for your dream job interviews</p>
            </div>
            <form class="auth-form" id="register-form">
                <div class="form-group">
                    <label for="register-name">Full Name</label>
                    <input type="text" id="register-name" placeholder="Enter your full name" required>
                </div>
                <div class="form-group">
                    <label for="register-email">Email Address</label>
                    <input type="email" id="register-email" placeholder="Enter your email" required>
                </div>
                <div class="form-group">
                    <label for="register-password">Password</label>
                    <input type="password" id="register-password" placeholder="Create a password" required>
                </div>
                <div class="form-group">
                    <label for="register-confirm">Confirm Password</label>
                    <input type="password" id="register-confirm" placeholder="Confirm your password" required>
                </div>
                <button type="submit" class="auth-submit">Create Account</button>
                
                <div class="social-login">
                    <p>Or sign up with</p>
                    <div class="social-buttons">
                        <button type="button" class="social-btn google">
                            <i class="fab fa-google"></i>
                        </button>
                        <button type="button" class="social-btn facebook">
                            <i class="fab fa-facebook-f"></i>
                        </button>
                        <button type="button" class="social-btn linkedin">
                            <i class="fab fa-linkedin-in"></i>
                        </button>
                    </div>
                </div>
            </form>
            <div class="auth-footer">
                <p>Already have an account? <a href="#" id="go-to-login">Sign in</a></p>
            </div>
        </div>
    </div>

    <!-- Dashboard -->
    <div class="dashboard" id="dashboard">
        <button class="exit-btn" id="exit-dashboard-btn" title="Exit to Home">
            <i class="fas fa-times"></i>
        </button>
        <div class="dashboard-header">
            <div class="dashboard-logo">
                <i class="fas fa-robot"></i>
                AI InterviewPrep
            </div>
            <div class="user-profile">
                <div class="profile-image">
                    <i class="fas fa-user"></i>
                </div>
                <div class="profile-info">
                    <h3 id="dashboard-username">John Doe</h3>
                    <p>Software Engineer</p>
                </div>
            </div>
        </div>
        <div class="dashboard-content">
            <div class="sidebar">
                <div class="profile-card">
                    <div class="profile-avatar">
                        <i class="fas fa-user"></i>
                    </div>
                    <h3 class="profile-name" id="sidebar-username">John Doe</h3>
                    <p class="profile-title">Software Engineer</p>
                    <div class="profile-stats">
                        <div class="stat">
                            <span class="stat-value">85%</span>
                            <span class="stat-label">Progress</span>
                        </div>
                        <div class="stat">
                            <span class="stat-value">24</span>
                            <span class="stat-label">Interviews</span>
                        </div>
                        <div class="stat">
                            <span class="stat-value">12</span>
                            <span class="stat-label">Skills</span>
                        </div>
                    </div>
                </div>
                <ul class="sidebar-menu">
                    <li><a href="#" class="active"><i class="fas fa-home"></i> Dashboard</a></li>
                    <li><a href="#"><i class="fas fa-comments"></i> Mock Interviews</a></li>
                    <li><a href="#"><i class="fas fa-brain"></i> AI Feedback</a></li>
                    <li><a href="#"><i class="fas fa-file-alt"></i> Resume Analysis</a></li>
                    <li><a href="#"><i class="fas fa-chart-line"></i> Progress Tracking</a></li>
                    <li><a href="#"><i class="fas fa-book"></i> Resources</a></li>
                    <li><a href="#"><i class="fas fa-cog"></i> Settings</a></li>
                    <li><a href="#" id="logout-btn"><i class="fas fa-sign-out-alt"></i> Logout</a></li>
                </ul>
            </div>
            <div class="main-content">
                <div class="search-bar">
                    <i class="fas fa-search"></i>
                    <input type="text" placeholder="Search for roles, skills, or companies...">
                </div>
                
                <div class="levels-section">
                    <h2 class="section-heading">
                        <i class="fas fa-seedling"></i>
                        Beginner Level Roles
                    </h2>
                    <div class="levels-grid" id="beginner-roles">
                        <!-- Beginner roles will be populated by JavaScript -->
                    </div>
                </div>
                
                <div class="levels-section">
                    <h2 class="section-heading">
                        <i class="fas fa-rocket"></i>
                        Intermediate Level Roles
                    </h2>
                    <div class="levels-grid" id="intermediate-roles">
                        <!-- Intermediate roles will be populated by JavaScript -->
                    </div>
                </div>
                
                <div class="levels-section">
                    <h2 class="section-heading">
                        <i class="fas fa-crown"></i>
                        Advanced Level Roles
                    </h2>
                    <div class="levels-grid" id="advanced-roles">
                        <!-- Advanced roles will be populated by JavaScript -->
                    </div>
                </div>
            </div>
        </div>
    </div>

    <!-- Interview Page -->
    <div class="interview-page" id="interview-page">
        <button class="exit-btn" id="exit-interview-btn" title="Exit Interview">
            <i class="fas fa-times"></i>
        </button>
        <div class="interview-container">
            <div class="interview-header">
                <div class="interview-info">
                    <h2 id="interview-role">Software Engineer Interview</h2>
                    <p id="interview-level">Intermediate Level</p>
                </div>
                <div class="interview-timer" id="interview-timer">00:00</div>
            </div>
            <div class="interview-content">
                <div class="interview-questions">
                    <div class="question-section">
                        <h3 class="section-title">
                            <i class="fas fa-user"></i>
                            Self Introduction Questions
                        </h3>
                        <ul class="question-list" id="self-intro-questions">
                            <!-- Self introduction questions will be populated by JavaScript -->
                        </ul>
                    </div>
                    <div class="question-section">
                        <h3 class="section-title">
                            <i class="fas fa-code"></i>
                            Technical Questions
                        </h3>
                        <ul class="question-list" id="technical-questions">
                            <!-- Technical questions will be populated by JavaScript -->
                        </ul>
                    </div>
                    
                    <!-- AI Feedback Section -->
                    <div class="feedback-section">
                        <h3><i class="fas fa-robot"></i> AI Feedback Analysis</h3>
                        <div class="feedback-content" id="feedback-content">
                            <p class="no-feedback">Complete an interview to see AI feedback here. The AI will analyze your responses for content quality, communication skills, and technical accuracy.</p>
                        </div>
                        <div class="feedback-metrics" id="feedback-metrics">
                            <!-- Metrics will be populated by JavaScript -->
                        </div>
                        <div class="feedback-actions">
                            <button class="feedback-btn analyze" id="analyze-feedback-btn">
                                <i class="fas fa-brain"></i>
                                Analyze Responses
                            </button>
                            <button class="feedback-btn download" id="download-feedback-btn" disabled>
                                <i class="fas fa-download"></i>
                                Download Report
                            </button>
                        </div>
                    </div>
                    
                    <div class="recordings-list">
                        <h3>Your Recorded Sessions</h3>
                        <div id="recordings-container">
                            <!-- Recorded sessions will be populated here -->
                        </div>
                    </div>
                </div>
                <div class="interview-controls">
                    <div class="avatar-container">
                        <div class="interview-avatar" id="interview-avatar">
                            <i class="fas fa-robot"></i>
                            <div class="avatar-pulse"></div>
                        </div>
                        <h3>AI Interviewer</h3>
                        <p id="avatar-status">Ready to start your interview</p>
                    </div>
                    <div class="control-buttons">
                        <button class="control-btn start-btn" id="start-interview-btn">
                            <i class="fas fa-play"></i>
                            Start Interview
                        </button>
                        <button class="control-btn record-btn" id="record-btn" disabled>
                            <i class="fas fa-microphone"></i>
                            Start Recording
                        </button>
                        <button class="control-btn download-btn" id="download-btn" disabled>
                            <i class="fas fa-download"></i>
                            Download Recording
                        </button>
                    </div>
                    <div class="voice-controls">
                        <button class="voice-btn play" id="play-question-btn" disabled>
                            <i class="fas fa-volume-up"></i>
                            Play Question
                        </button>
                        <button class="voice-btn stop" id="stop-voice-btn" disabled>
                            <i class="fas fa-stop"></i>
                            Stop
                        </button>
                    </div>
                    
                    <!-- Navigation Controls -->
                    <div class="navigation-controls">
                        <button class="nav-btn back" id="back-question-btn" disabled>
                            <i class="fas fa-arrow-left"></i>
                            Previous
                        </button>
                        <button class="nav-btn next" id="next-question-btn" disabled>
                            <i class="fas fa-arrow-right"></i>
                            Next
                        </button>
                    </div>
                    
                    <div class="progress-section">
                        <div class="progress-bar">
                            <div class="progress-fill" id="progress-fill"></div>
                        </div>
                        <div class="progress-text" id="progress-text">Question 0 of 0</div>
                    </div>
                    
                    <!-- Video Recording Section -->
                    <div class="video-recording">
                        <h3><i class="fas fa-video"></i> Video Recording</h3>
                        <div class="video-container">
                            <video id="video-preview" class="video-preview" autoplay muted></video>
                            <div id="video-overlay" class="video-overlay">
                                <div>
                                    <i class="fas fa-video-slash fa-2x"></i>
                                    <p>Camera preview will appear here</p>
                                    <p>Click "Start Video" to begin</p>
                                </div>
                            </div>
                            <div id="recording-indicator" class="recording-indicator" style="display: none;">
                                <div class="recording-dot"></div>
                                <span>Recording</span>
                            </div>
                        </div>
                        <div class="video-controls">
                            <button class="video-btn start" id="start-video-btn">
                                <i class="fas fa-video"></i>
                                Start Video
                            </button>
                            <button class="video-btn stop" id="stop-video-btn" disabled>
                                <i class="fas fa-stop"></i>
                                Stop Video
                            </button>
                            <button class="video-btn download" id="download-video-btn" disabled>
                                <i class="fas fa-download"></i>
                                Download
                            </button>
                        </div>
                    </div>
                </div>
            </div>
        </div>
    </div>

    <script>
        // DOM Elements
        const landingPage = document.getElementById('landing-page');
        const loginPage = document.getElementById('login-page');
        const registerPage = document.getElementById('register-page');
        const dashboard = document.getElementById('dashboard');
        const interviewPage = document.getElementById('interview-page');
        const loginBtn = document.getElementById('login-btn');
        const registerBtn = document.getElementById('register-btn');
        const backFromLogin = document.getElementById('back-from-login');
        const backFromRegister = document.getElementById('back-from-register');
        const goToRegister = document.getElementById('go-to-register');
        const goToLogin = document.getElementById('go-to-login');
        const loginForm = document.getElementById('login-form');
        const registerForm = document.getElementById('register-form');
        const logoutBtn = document.getElementById('logout-btn');
        const dashboardUsername = document.getElementById('dashboard-username');
        const sidebarUsername = document.getElementById('sidebar-username');
        const startPracticeBtn = document.getElementById('start-practice-btn');
        const demoBtn = document.getElementById('demo-btn');
        const aboutLink = document.getElementById('about-link');
        const processLink = document.getElementById('process-link');
        const featuresLink = document.getElementById('features-link');
        const mockInterviewBtn = document.getElementById('mock-interview-btn');
        const aiFeedbackBtn = document.getElementById('ai-feedback-btn');
        const resumeAnalysisBtn = document.getElementById('resume-analysis-btn');
        const header = document.getElementById('main-header');
        const beginnerRolesContainer = document.getElementById('beginner-roles');
        const intermediateRolesContainer = document.getElementById('intermediate-roles');
        const advancedRolesContainer = document.getElementById('advanced-roles');
        const startInterviewBtn = document.getElementById('start-interview-btn');
        const recordBtn = document.getElementById('record-btn');
        const downloadBtn = document.getElementById('download-btn');
        const interviewTimer = document.getElementById('interview-timer');
        const avatarStatus = document.getElementById('avatar-status');
        const progressFill = document.getElementById('progress-fill');
        const progressText = document.getElementById('progress-text');
        const selfIntroQuestions = document.getElementById('self-intro-questions');
        const technicalQuestions = document.getElementById('technical-questions');
        const interviewRole = document.getElementById('interview-role');
        const interviewLevel = document.getElementById('interview-level');
        const interviewAvatar = document.getElementById('interview-avatar');
        const recordingsContainer = document.getElementById('recordings-container');
        const exitDashboardBtn = document.getElementById('exit-dashboard-btn');
        const exitInterviewBtn = document.getElementById('exit-interview-btn');
        const playQuestionBtn = document.getElementById('play-question-btn');
        const stopVoiceBtn = document.getElementById('stop-voice-btn');
        
        // Navigation buttons
        const backQuestionBtn = document.getElementById('back-question-btn');
        const nextQuestionBtn = document.getElementById('next-question-btn');
        
        // Video recording elements
        const videoPreview = document.getElementById('video-preview');
        const videoOverlay = document.getElementById('video-overlay');
        const recordingIndicator = document.getElementById('recording-indicator');
        const startVideoBtn = document.getElementById('start-video-btn');
        const stopVideoBtn = document.getElementById('stop-video-btn');
        const downloadVideoBtn = document.getElementById('download-video-btn');

        // AI Feedback elements
        const feedbackContent = document.getElementById('feedback-content');
        const feedbackMetrics = document.getElementById('feedback-metrics');
        const analyzeFeedbackBtn = document.getElementById('analyze-feedback-btn');
        const downloadFeedbackBtn = document.getElementById('download-feedback-btn');

        // Sample role data - 35 roles for each level
        const roleData = {
            beginner: [
                "Frontend Developer", "Backend Developer", "Full Stack Developer", 
                "Data Analyst", "UI/UX Designer", "QA Engineer", "Technical Support", 
                "IT Helpdesk", "Junior Project Manager", "Content Writer",
                "Digital Marketer", "Social Media Manager", "SEO Specialist",
                "Customer Service Representative", "Sales Development Representative",
                "Business Analyst", "HR Coordinator", "Recruitment Coordinator",
                "Accountant", "Financial Analyst", "Administrative Assistant",
                "Office Manager", "Graphic Designer", "Video Editor",
                "Web Designer", "Mobile App Developer", "Software Tester",
                "Network Administrator", "Systems Administrator", "Database Administrator",
                "IT Support Specialist", "Technical Writer", "Data Entry Specialist",
                "Junior Data Scientist", "IT Consultant"
            ],
            intermediate: [
                "Senior Software Engineer", "DevOps Engineer", "Data Scientist",
                "Machine Learning Engineer", "Product Manager", "Technical Lead",
                "Solutions Architect", "Cloud Engineer", "Security Analyst",
                "UX Researcher", "Product Designer", "Marketing Manager",
                "Content Strategist", "Brand Manager", "Sales Manager",
                "Account Manager", "Business Development Manager", "HR Manager",
                "Talent Acquisition Specialist", "Financial Controller", "Investment Analyst",
                "Operations Manager", "Project Manager", "Scrum Master",
                "IT Manager", "Systems Engineer", "Network Engineer",
                "Database Architect", "Data Engineer", "AI Specialist",
                "Software Architect", "Mobile Development Lead", "QA Manager",
                "Digital Marketing Manager", "IT Project Manager"
            ],
            advanced: [
                "Principal Engineer", "Engineering Manager", "CTO",
                "VP of Engineering", "Director of Product", "Head of Design",
                "Chief Data Officer", "AI Research Scientist", "Machine Learning Architect",
                "Chief Marketing Officer", "VP of Sales", "Director of Business Development",
                "Chief Financial Officer", "VP of Finance", "Investment Director",
                "Chief Operating Officer", "VP of Operations", "Program Director",
                "Chief Information Officer", "VP of IT", "Security Architect",
                "Chief HR Officer", "VP of Talent", "Director of Learning & Development",
                "Chief Strategy Officer", "Management Consultant", "Enterprise Architect",
                "Product Director", "Head of Growth", "Innovation Director",
                "Chief Technology Officer", "VP of Engineering", "Director of AI",
                "Head of Data Science", "Chief Product Officer"
            ]
        };

        // Interview questions data - Expanded to 25 questions each
        const interviewQuestions = {
            selfIntroduction: [
                "Can you tell me about yourself and your background?",
                "What motivated you to pursue a career in this field?",
                "What are your greatest strengths and weaknesses?",
                "Where do you see yourself in 5 years?",
                "Why are you interested in working for our company?",
                "What do you consider your most significant professional achievement?",
                "How do you handle pressure and tight deadlines?",
                "What kind of work environment do you prefer?",
                "How do you stay updated with industry trends?",
                "What are your salary expectations?",
                "Why should we hire you over other candidates?",
                "Tell me about a time you failed and what you learned from it.",
                "How do you handle constructive criticism?",
                "What are your hobbies and interests outside of work?",
                "Describe your ideal manager or supervisor.",
                "How do you prioritize your work when managing multiple projects?",
                "What skills do you bring to this role that others might not?",
                "Tell me about a time you had to work with a difficult colleague.",
                "What accomplishment are you most proud of?",
                "How do you approach learning new technologies or skills?",
                "What do you know about our company culture and values?",
                "Where do you need to improve professionally?",
                "How do you measure success in your work?",
                "What was your biggest professional challenge and how did you overcome it?",
                "What makes you unique compared to other candidates?"
            ],
            technical: {
                "Software Engineer": [
                    "Explain the concept of object-oriented programming.",
                    "What is the difference between SQL and NoSQL databases?",
                    "How would you optimize a slow database query?",
                    "Explain the MVC architectural pattern.",
                    "What are the principles of REST API design?",
                    "How does garbage collection work in Java?",
                    "What is the difference between authentication and authorization?",
                    "Explain the concept of microservices architecture.",
                    "How would you handle a memory leak in an application?",
                    "What are the advantages of using version control systems?",
                    "Explain the difference between unit testing and integration testing.",
                    "What is continuous integration and continuous deployment?",
                    "How do you ensure code quality in a large codebase?",
                    "What are design patterns and can you name a few?",
                    "Explain the concept of dependency injection.",
                    "How does HTTP/2 differ from HTTP/1.1?",
                    "What is the difference between synchronous and asynchronous programming?",
                    "How would you scale a web application to handle millions of users?",
                    "What are the security best practices for web applications?",
                    "Explain the concept of containerization and its benefits.",
                    "What is the difference between SQL injection and XSS attacks?",
                    "How do you approach debugging complex issues?",
                    "What is your experience with cloud platforms like AWS or Azure?",
                    "Explain the concept of load balancing and its importance.",
                    "How do you stay updated with new programming languages and frameworks?"
                ],
                "Data Scientist": [
                    "What is the difference between supervised and unsupervised learning?",
                    "Explain the bias-variance tradeoff.",
                    "How would you handle missing data in a dataset?",
                    "What is cross-validation and why is it important?",
                    "Explain the concept of regularization.",
                    "What evaluation metrics would you use for a classification problem?",
                    "What is the difference between precision and recall?",
                    "Explain the concept of feature engineering.",
                    "How would you detect outliers in a dataset?",
                    "What is the curse of dimensionality?",
                    "Explain the working of decision trees.",
                    "What is the difference between bagging and boosting?",
                    "How does the k-means clustering algorithm work?",
                    "What is principal component analysis (PCA)?",
                    "Explain the concept of neural networks and deep learning.",
                    "What are the assumptions of linear regression?",
                    "How would you handle imbalanced datasets?",
                    "What is natural language processing and its applications?",
                    "Explain the concept of time series analysis.",
                    "What is A/B testing and how is it used?",
                    "How do you validate the performance of a machine learning model?",
                    "What is the difference between machine learning and deep learning?",
                    "Explain the concept of reinforcement learning.",
                    "What are the ethical considerations in AI and data science?",
                    "How do you stay updated with the latest developments in data science?"
                ],
                "Product Manager": [
                    "How do you prioritize features in a product roadmap?",
                    "What metrics would you track to measure product success?",
                    "How do you gather and incorporate user feedback?",
                    "Explain the difference between OKRs and KPIs.",
                    "How would you handle conflicting stakeholder requirements?",
                    "What is your approach to competitive analysis?",
                    "How do you define and measure product-market fit?",
                    "What is the difference between a product vision and a product strategy?",
                    "How do you conduct user research?",
                    "What is your experience with agile development methodologies?",
                    "How do you communicate product requirements to engineering teams?",
                    "What is your approach to A/B testing?",
                    "How do you handle product launches?",
                    "What is your experience with data-driven decision making?",
                    "How do you balance short-term goals with long-term vision?",
                    "What is your approach to managing technical debt?",
                    "How do you work with cross-functional teams?",
                    "What is your experience with product analytics tools?",
                    "How do you handle situations where the product is not meeting its goals?",
                    "What is your approach to creating user stories?",
                    "How do you stay updated with market trends and customer needs?",
                    "What is your experience with pricing strategies?",
                    "How do you measure customer satisfaction?",
                    "What is your approach to risk management in product development?",
                    "How do you foster innovation within your product team?"
                ],
                "UI/UX Designer": [
                    "What is your design process from concept to final product?",
                    "How do you conduct user research?",
                    "What is the difference between UI and UX design?",
                    "How do you approach creating user personas?",
                    "What tools do you use for prototyping and why?",
                    "How do you measure the success of a design?",
                    "What is your experience with design systems?",
                    "How do you handle feedback from stakeholders?",
                    "What is your approach to accessibility in design?",
                    "How do you stay updated with design trends?",
                    "What is your experience with responsive design?",
                    "How do you approach designing for different user segments?",
                    "What is your process for conducting usability testing?",
                    "How do you balance user needs with business requirements?",
                    "What is your experience with mobile app design?",
                    "How do you approach information architecture?",
                    "What is your experience with interaction design?",
                    "How do you handle design critiques?",
                    "What is your approach to designing for different platforms?",
                    "How do you measure the impact of your design changes?",
                    "What is your experience with design collaboration tools?",
                    "How do you approach designing for international audiences?",
                    "What is your experience with animation in UI design?",
                    "How do you ensure consistency across different parts of a product?",
                    "What is your approach to designing for different user skill levels?"
                ],
                "Marketing Manager": [
                    "What is your approach to developing a marketing strategy?",
                    "How do you measure the ROI of marketing campaigns?",
                    "What channels have you found most effective for customer acquisition?",
                    "How do you approach market segmentation?",
                    "What is your experience with digital marketing?",
                    "How do you develop buyer personas?",
                    "What is your approach to content marketing?",
                    "How do you handle marketing budget allocation?",
                    "What is your experience with marketing automation tools?",
                    "How do you approach competitive analysis in marketing?",
                    "What is your experience with social media marketing?",
                    "How do you measure brand awareness?",
                    "What is your approach to email marketing campaigns?",
                    "How do you stay updated with marketing trends?",
                    "What is your experience with SEO and SEM?",
                    "How do you approach marketing to different customer segments?",
                    "What is your experience with marketing analytics?",
                    "How do you handle crisis communications?",
                    "What is your approach to influencer marketing?",
                    "How do you measure customer lifetime value?",
                    "What is your experience with ABM (Account-Based Marketing)?",
                    "How do you approach marketing in a B2B vs B2C context?",
                    "What is your experience with marketing attribution?",
                    "How do you foster collaboration between marketing and sales teams?",
                    "What is your approach to international marketing?"
                ]
            }
        };

        // Interview state
        let interviewState = {
            isActive: false,
            isRecording: false,
            currentQuestion: 0,
            totalQuestions: 0,
            timer: 0,
            timerInterval: null,
            selectedRole: "",
            selectedLevel: "",
            mediaRecorder: null,
            audioChunks: [],
            recordings: [],
            speechSynthesis: window.speechSynthesis,
            currentUtterance: null,
            // Video recording state
            videoStream: null,
            videoRecorder: null,
            videoChunks: [],
            isVideoRecording: false,
            recordedVideo: null,
            // AI Feedback state
            userResponses: [],
            feedbackGenerated: false
        };

        // AI Feedback Analysis Function
        function generateAIFeedback() {
            if (interviewState.userResponses.length === 0) {
                showNotification('No responses recorded yet. Complete the interview first.');
                return;
            }

            showNotification('AI is analyzing your responses...');
            
            // Simulate AI processing time
            setTimeout(() => {
                const feedback = analyzeResponsesWithAI();
                displayAIFeedback(feedback);
                interviewState.feedbackGenerated = true;
                downloadFeedbackBtn.disabled = false;
                showNotification('AI feedback generated successfully!');
            }, 2000);
        }

        // AI Analysis Engine
        function analyzeResponsesWithAI() {
            const responses = interviewState.userResponses;
            const role = interviewState.selectedRole;
            const feedback = {
                overallScore: 0,
                strengths: [],
                improvements: [],
                detailedAnalysis: [],
                metrics: {
                    contentQuality: 0,
                    communication: 0,
                    technicalAccuracy: 0,
                    confidence: 0,
                    relevance: 0
                }
            };

            // Analyze each response
            responses.forEach((response, index) => {
                const question = response.question;
                const analysis = analyzeSingleResponse(question, response.answer, role);
                feedback.detailedAnalysis.push(analysis);
                
                // Update metrics based on individual analysis
                feedback.metrics.contentQuality += analysis.scores.content;
                feedback.metrics.communication += analysis.scores.communication;
                feedback.metrics.technicalAccuracy += analysis.scores.technical;
                feedback.metrics.confidence += analysis.scores.confidence;
                feedback.metrics.relevance += analysis.scores.relevance;
            });

            // Calculate average scores
            const responseCount = responses.length;
            feedback.metrics.contentQuality = Math.round(feedback.metrics.contentQuality / responseCount);
            feedback.metrics.communication = Math.round(feedback.metrics.communication / responseCount);
            feedback.metrics.technicalAccuracy = Math.round(feedback.metrics.technicalAccuracy / responseCount);
            feedback.metrics.confidence = Math.round(feedback.metrics.confidence / responseCount);
            feedback.metrics.relevance = Math.round(feedback.metrics.relevance / responseCount);

            // Calculate overall score
            feedback.overallScore = Math.round(
                (feedback.metrics.contentQuality + 
                 feedback.metrics.communication + 
                 feedback.metrics.technicalAccuracy + 
                 feedback.metrics.confidence + 
                 feedback.metrics.relevance) / 5
            );

            // Generate strengths and improvements
            generateStrengthsAndImprovements(feedback);

            return feedback;
        }

        function analyzeSingleResponse(question, answer, role) {
            // Simulate AI analysis - in a real implementation, this would use NLP and ML models
            const analysis = {
                question: question,
                answer: answer,
                scores: {
                    content: Math.floor(Math.random() * 30) + 70, // 70-100
                    communication: Math.floor(Math.random() * 30) + 70,
                    technical: role.includes('Software') || role.includes('Data') || role.includes('Engineer') ? 
                              Math.floor(Math.random() * 30) + 70 : 85,
                    confidence: Math.floor(Math.random() * 30) + 70,
                    relevance: Math.floor(Math.random() * 30) + 70
                },
                feedback: {
                    positive: [],
                    constructive: []
                }
            };

            // Generate feedback based on answer characteristics
            const answerLength = answer.length;
            const hasKeywords = checkForKeywords(answer, role);
            const structureScore = evaluateStructure(answer);

            if (answerLength > 100) {
                analysis.feedback.positive.push("Good level of detail in your response");
            } else {
                analysis.feedback.constructive.push("Consider providing more specific examples and details");
            }

            if (hasKeywords) {
                analysis.feedback.positive.push("Relevant industry terminology used appropriately");
            } else {
                analysis.feedback.constructive.push("Try incorporating more role-specific keywords");
            }

            if (structureScore > 7) {
                analysis.feedback.positive.push("Well-structured and organized response");
            } else {
                analysis.feedback.constructive.push("Work on organizing your thoughts more clearly");
            }

            if (answer.includes('I think') || answer.includes('maybe') || answer.includes('perhaps')) {
                analysis.feedback.constructive.push("Try to be more confident and decisive in your statements");
            }

            return analysis;
        }

        function checkForKeywords(answer, role) {
            const keywords = {
                'Software Engineer': ['algorithm', 'database', 'API', 'framework', 'debugging', 'optimization'],
                'Data Scientist': ['machine learning', 'analysis', 'visualization', 'statistics', 'model', 'prediction'],
                'Product Manager': ['strategy', 'roadmap', 'metrics', 'user research', 'stakeholder', 'prioritization'],
                'UI/UX Designer': ['user experience', 'interface', 'prototype', 'wireframe', 'usability', 'accessibility'],
                'Marketing Manager': ['campaign', 'ROI', 'conversion', 'brand', 'audience', 'engagement']
            };

            const roleKeywords = keywords[role] || keywords['Software Engineer'];
            return roleKeywords.some(keyword => answer.toLowerCase().includes(keyword));
        }

        function evaluateStructure(answer) {
            // Simple structure evaluation
            let score = 5; // Base score
            
            if (answer.length > 50) score += 1;
            if (answer.includes('Firstly') || answer.includes('Secondly') || answer.includes('Finally')) score += 2;
            if (answer.split('.').length > 2) score += 1;
            if (answer.includes('example') || answer.includes('for instance')) score += 1;
            
            return Math.min(score, 10);
        }

        function generateStrengthsAndImprovements(feedback) {
            const metrics = feedback.metrics;
            
            // Strengths
            if (metrics.contentQuality >= 85) {
                feedback.strengths.push("Strong content knowledge and depth in responses");
            }
            if (metrics.communication >= 85) {
                feedback.strengths.push("Excellent communication skills and clarity");
            }
            if (metrics.technicalAccuracy >= 85) {
                feedback.strengths.push("High technical accuracy and understanding");
            }
            if (metrics.confidence >= 85) {
                feedback.strengths.push("Confident and professional delivery");
            }
            
            // Improvements
            if (metrics.contentQuality < 80) {
                feedback.improvements.push("Work on providing more detailed and specific examples");
            }
            if (metrics.communication < 80) {
                feedback.improvements.push("Practice structuring your responses more clearly");
            }
            if (metrics.technicalAccuracy < 80) {
                feedback.improvements.push("Review technical concepts and industry best practices");
            }
            if (metrics.confidence < 80) {
                feedback.improvements.push("Build confidence by practicing more and preparing thoroughly");
            }
            if (metrics.relevance < 80) {
                feedback.improvements.push("Focus on making responses more relevant to the specific question");
            }
        }

        function displayAIFeedback(feedback) {
            // Clear previous feedback
            feedbackContent.innerHTML = '';
            feedbackMetrics.innerHTML = '';

            // Display metrics
            const metricsHTML = `
                <div class="metric">
                    <span class="metric-value">${feedback.overallScore}%</span>
                    <span class="metric-label">Overall Score</span>
                </div>
                <div class="metric">
                    <span class="metric-value">${feedback.metrics.contentQuality}%</span>
                    <span class="metric-label">Content Quality</span>
                </div>
                <div class="metric">
                    <span class="metric-value">${feedback.metrics.communication}%</span>
                    <span class="metric-label">Communication</span>
                </div>
                <div class="metric">
                    <span class="metric-value">${feedback.metrics.technicalAccuracy}%</span>
                    <span class="metric-label">Technical Accuracy</span>
                </div>
                <div class="metric">
                    <span class="metric-value">${feedback.metrics.confidence}%</span>
                    <span class="metric-label">Confidence</span>
                </div>
            `;
            feedbackMetrics.innerHTML = metricsHTML;

            // Display detailed analysis
            feedback.detailedAnalysis.forEach((analysis, index) => {
                const feedbackItem = document.createElement('div');
                feedbackItem.className = 'feedback-item';
                feedbackItem.innerHTML = `
                    <div class="feedback-question">Q${index + 1}: ${analysis.question}</div>
                    <div class="feedback-analysis">
                        <strong>Strengths:</strong> ${analysis.feedback.positive.join(', ')}<br>
                        <strong>Areas for Improvement:</strong> ${analysis.feedback.constructive.join(', ')}
                    </div>
                `;
                feedbackContent.appendChild(feedbackItem);
            });

            // Add overall feedback
            const overallItem = document.createElement('div');
            overallItem.className = 'feedback-item';
            overallItem.style.background = 'linear-gradient(135deg, #4361ee, #3a0ca3)';
            overallItem.style.color = 'white';
            overallItem.innerHTML = `
                <div class="feedback-question" style="color: white;">Overall Performance Summary</div>
                <div class="feedback-analysis">
                    <strong>Key Strengths:</strong> ${feedback.strengths.join('; ')}<br>
                    <strong>Recommended Improvements:</strong> ${feedback.improvements.join('; ')}
                </div>
            `;
            feedbackContent.appendChild(overallItem);
        }

        function downloadFeedbackReport() {
            if (!interviewState.feedbackGenerated) {
                showNotification('Please generate feedback first');
                return;
            }

            showNotification('Downloading AI feedback report...');
            // In a real implementation, this would generate and download a PDF report
        }

        // Text-to-Speech function
        function speakText(text) {
            // Stop any ongoing speech
            if (interviewState.currentUtterance) {
                interviewState.speechSynthesis.cancel();
            }
            
            // Add speaking animation to avatar
            interviewAvatar.classList.add('speaking');
            avatarStatus.textContent = "Asking question...";
            
            // Create a new utterance
            const utterance = new SpeechSynthesisUtterance(text);
            utterance.rate = 0.9;
            utterance.pitch = 1;
            utterance.volume = 1;
            
            // Set up event listeners
            utterance.onstart = function() {
                playQuestionBtn.disabled = true;
                stopVoiceBtn.disabled = false;
                interviewAvatar.classList.add('speaking');
            };
            
            utterance.onend = function() {
                playQuestionBtn.disabled = false;
                stopVoiceBtn.disabled = true;
                interviewAvatar.classList.remove('speaking');
                avatarStatus.textContent = "Listening for your response...";
                
                // Auto-start recording after question is asked
                if (interviewState.isActive && !interviewState.isRecording) {
                    startRecording();
                }
            };
            
            utterance.onerror = function(event) {
                console.error('Speech synthesis error:', event);
                playQuestionBtn.disabled = false;
                stopVoiceBtn.disabled = true;
                interviewAvatar.classList.remove('speaking');
                avatarStatus.textContent = "Error with voice synthesis";
                showNotification('Voice synthesis error. Please try again.');
            };
            
            // Store the current utterance
            interviewState.currentUtterance = utterance;
            
            // Speak the text
            interviewState.speechSynthesis.speak(utterance);
        }

        // Stop speech function
        function stopSpeech() {
            if (interviewState.speechSynthesis.speaking) {
                interviewState.speechSynthesis.cancel();
                playQuestionBtn.disabled = false;
                stopVoiceBtn.disabled = true;
                interviewAvatar.classList.remove('speaking');
                avatarStatus.textContent = "Voice stopped";
            }
        }

        // Initialize camera for video recording
        async function initializeCamera() {
            try {
                // Request camera access
                interviewState.videoStream = await navigator.mediaDevices.getUserMedia({ 
                    video: { 
                        width: { ideal: 1280 },
                        height: { ideal: 720 }
                    }, 
                    audio: true 
                });
                
                // Set the video stream as the source for the video element
                videoPreview.srcObject = interviewState.videoStream;
                videoOverlay.style.display = 'none';
                
                // Enable the start video button
                startVideoBtn.disabled = false;
                
                showNotification('Camera access granted. You can now start video recording.');
            } catch (error) {
                console.error('Error accessing camera:', error);
                showNotification('Error accessing camera. Please check permissions and try again.');
                videoOverlay.innerHTML = `
                    <div>
                        <i class="fas fa-exclamation-triangle fa-2x"></i>
                        <p>Camera access denied or not available</p>
                        <p>Please check your permissions</p>
                    </div>
                `;
            }
        }

        // Start video recording
        function startVideoRecording() {
            if (!interviewState.videoStream) {
                showNotification('Camera not initialized. Please wait or try again.');
                return;
            }
            
            try {
                // Reset video chunks
                interviewState.videoChunks = [];
                
                // Create MediaRecorder instance
                interviewState.videoRecorder = new MediaRecorder(interviewState.videoStream, {
                    mimeType: 'video/webm;codecs=vp9,opus'
                });
                
                // Set up event handlers
                interviewState.videoRecorder.ondataavailable = (event) => {
                    if (event.data.size > 0) {
                        interviewState.videoChunks.push(event.data);
                    }
                };
                
                interviewState.videoRecorder.onstop = () => {
                    // Create a blob from the recorded chunks
                    const videoBlob = new Blob(interviewState.videoChunks, { type: 'video/webm' });
                    interviewState.recordedVideo = videoBlob;
                    
                    // Create a URL for the recorded video
                    const videoUrl = URL.createObjectURL(videoBlob);
                    
                    // Enable download button
                    downloadVideoBtn.disabled = false;
                    
                    showNotification('Video recording completed. You can now download it.');
                };
                
                // Start recording
                interviewState.videoRecorder.start(1000); // Collect data every second
                interviewState.isVideoRecording = true;
                
                // Update UI
                startVideoBtn.disabled = true;
                stopVideoBtn.disabled = false;
                recordingIndicator.style.display = 'flex';
                
                showNotification('Video recording started...');
            } catch (error) {
                console.error('Error starting video recording:', error);
                showNotification('Error starting video recording. Please try again.');
            }
        }

        // Stop video recording
        function stopVideoRecording() {
            if (interviewState.videoRecorder && interviewState.isVideoRecording) {
                interviewState.videoRecorder.stop();
                interviewState.isVideoRecording = false;
                
                // Update UI
                startVideoBtn.disabled = false;
                stopVideoBtn.disabled = true;
                recordingIndicator.style.display = 'none';
                
                showNotification('Video recording stopped.');
            }
        }

        // Download recorded video
        function downloadRecordedVideo() {
            if (interviewState.recordedVideo) {
                const url = URL.createObjectURL(interviewState.recordedVideo);
                const a = document.createElement('a');
                a.href = url;
                a.download = `interview_response_${new Date().toISOString().slice(0, 19).replace(/:/g, '-')}.webm`;
                document.body.appendChild(a);
                a.click();
                document.body.removeChild(a);
                URL.revokeObjectURL(url);
                
                showNotification('Video download started.');
            } else {
                showNotification('No video available to download.');
            }
        }

        // Stop camera when leaving interview page
        function stopCamera() {
            if (interviewState.videoStream) {
                interviewState.videoStream.getTracks().forEach(track => track.stop());
                interviewState.videoStream = null;
            }
            
            if (interviewState.isVideoRecording) {
                stopVideoRecording();
            }
            
            videoPreview.srcObject = null;
            videoOverlay.style.display = 'flex';
            videoOverlay.innerHTML = `
                <div>
                    <i class="fas fa-video-slash fa-2x"></i>
                    <p>Camera preview will appear here</p>
                    <p>Click "Start Video" to begin</p>
                </div>
            `;
            
            startVideoBtn.disabled = true;
            stopVideoBtn.disabled = true;
            downloadVideoBtn.disabled = true;
            recordingIndicator.style.display = 'none';
        }

        // Navigate to next question
        function nextQuestion() {
            if (interviewState.currentQuestion < interviewState.totalQuestions) {
                // Stop any ongoing recording
                if (interviewState.isRecording) {
                    stopRecording();
                }
                
                // Stop any ongoing speech
                stopSpeech();
                
                // Move to next question
                askQuestion(interviewState.currentQuestion);
                
                // Update navigation buttons
                updateNavigationButtons();
            }
        }

        // Navigate to previous question
        function previousQuestion() {
            if (interviewState.currentQuestion > 1) {
                // Stop any ongoing recording
                if (interviewState.isRecording) {
                    stopRecording();
                }
                
                // Stop any ongoing speech
                stopSpeech();
                
                // Move to previous question
                askQuestion(interviewState.currentQuestion - 2);
                
                // Update navigation buttons
                updateNavigationButtons();
            }
        }

        // Update navigation buttons state
        function updateNavigationButtons() {
            // Enable/disable back button
            backQuestionBtn.disabled = interviewState.currentQuestion <= 1;
            
            // Enable/disable next button
            nextQuestionBtn.disabled = interviewState.currentQuestion >= interviewState.totalQuestions;
        }

        // Page Navigation Functions
        function showLandingPage() {
            landingPage.style.display = 'block';
            loginPage.style.display = 'none';
            registerPage.style.display = 'none';
            dashboard.style.display = 'none';
            interviewPage.style.display = 'none';
            
            // Stop any ongoing speech when leaving interview page
            stopSpeech();
            stopCamera();
        }

        function showLoginPage() {
            landingPage.style.display = 'none';
            loginPage.style.display = 'flex';
            registerPage.style.display = 'none';
            dashboard.style.display = 'none';
            interviewPage.style.display = 'none';
        }

        function showRegisterPage() {
            landingPage.style.display = 'none';
            loginPage.style.display = 'none';
            registerPage.style.display = 'flex';
            dashboard.style.display = 'none';
            interviewPage.style.display = 'none';
        }

        function showDashboard(user) {
            landingPage.style.display = 'none';
            loginPage.style.display = 'none';
            registerPage.style.display = 'none';
            dashboard.style.display = 'block';
            interviewPage.style.display = 'none';
            
            // Update user info in dashboard
            if (user) {
                dashboardUsername.textContent = user.name;
                sidebarUsername.textContent = user.name;
            }
        }

        function showInterviewPage(role, level) {
            landingPage.style.display = 'none';
            loginPage.style.display = 'none';
            registerPage.style.display = 'none';
            dashboard.style.display = 'none';
            interviewPage.style.display = 'block';
            
            // Set interview details
            interviewState.selectedRole = role;
            interviewState.selectedLevel = level;
            interviewRole.textContent = `${role} Interview`;
            interviewLevel.textContent = `${level} Level`;
            
            // Populate questions
            populateInterviewQuestions(role);
            
            // Reset interview state
            resetInterviewState();
            
            // Load previous recordings
            loadRecordings();
            
            // Initialize camera for video recording
            initializeCamera();
        }

        // Initialize with landing page
        showLandingPage();

        // Populate role cards
        function populateRoleCards() {
            // Clear existing content
            beginnerRolesContainer.innerHTML = '';
            intermediateRolesContainer.innerHTML = '';
            advancedRolesContainer.innerHTML = '';
            
            // Populate beginner roles
            roleData.beginner.forEach(role => {
                beginnerRolesContainer.appendChild(createRoleCard(role, 'Beginner'));
            });
            
            // Populate intermediate roles
            roleData.intermediate.forEach(role => {
                intermediateRolesContainer.appendChild(createRoleCard(role, 'Intermediate'));
            });
            
            // Populate advanced roles
            roleData.advanced.forEach(role => {
                advancedRolesContainer.appendChild(createRoleCard(role, 'Advanced'));
            });
        }

        // Create a role card element
        function createRoleCard(role, level) {
            const card = document.createElement('div');
            card.className = 'level-card';
            card.innerHTML = `
                <div class="level-header">
                    <h3 class="level-title">${role}</h3>
                    <span class="level-badge">${level}</span>
                </div>
                <div class="level-roles">
                    <span class="role-tag">Interview Prep</span>
                    <span class="role-tag">Mock Tests</span>
                    <span class="role-tag">Skill Assessment</span>
                </div>
            `;
            
            // Add click event to start interview
            card.addEventListener('click', () => {
                showInterviewPage(role, level);
            });
            
            return card;
        }

        // Populate interview questions
        function populateInterviewQuestions(role) {
            // Clear existing questions
            selfIntroQuestions.innerHTML = '';
            technicalQuestions.innerHTML = '';
            
            // Populate self introduction questions
            interviewQuestions.selfIntroduction.forEach((question, index) => {
                const questionItem = document.createElement('li');
                questionItem.className = 'question-item';
                if (index === 0) questionItem.classList.add('active');
                questionItem.textContent = question;
                questionItem.dataset.index = index;
                selfIntroQuestions.appendChild(questionItem);
            });
            
            // Populate technical questions based on role
            const techQuestions = interviewQuestions.technical[role] || 
                                interviewQuestions.technical["Software Engineer"];
            
            techQuestions.forEach((question, index) => {
                const questionItem = document.createElement('li');
                questionItem.className = 'question-item';
                questionItem.textContent = question;
                questionItem.dataset.index = index + interviewQuestions.selfIntroduction.length;
                technicalQuestions.appendChild(questionItem);
            });
            
            // Update total questions count
            interviewState.totalQuestions = interviewQuestions.selfIntroduction.length + techQuestions.length;
            updateProgress();
        }

        // Reset interview state
        function resetInterviewState() {
            interviewState.isActive = false;
            interviewState.isRecording = false;
            interviewState.currentQuestion = 0;
            interviewState.timer = 0;
            interviewState.audioChunks = [];
            interviewState.userResponses = [];
            interviewState.feedbackGenerated = false;
            
            // Stop any ongoing speech
            stopSpeech();
            
            // Reset UI elements
            startInterviewBtn.disabled = false;
            startInterviewBtn.innerHTML = '<i class="fas fa-play"></i> Start Interview';
            recordBtn.disabled = true;
            recordBtn.innerHTML = '<i class="fas fa-microphone"></i> Start Recording';
            recordBtn.classList.remove('recording');
            downloadBtn.disabled = true;
            playQuestionBtn.disabled = true;
            stopVoiceBtn.disabled = true;
            backQuestionBtn.disabled = true;
            nextQuestionBtn.disabled = true;
            interviewTimer.textContent = '00:00';
            avatarStatus.textContent = 'Ready to start your interview';
            progressFill.style.width = '0%';
            progressText.textContent = 'Question 0 of 0';
            downloadFeedbackBtn.disabled = true;
            
            // Reset feedback section
            feedbackContent.innerHTML = '<p class="no-feedback">Complete an interview to see AI feedback here. The AI will analyze your responses for content quality, communication skills, and technical accuracy.</p>';
            feedbackMetrics.innerHTML = '';
            
            // Clear timer interval if exists
            if (interviewState.timerInterval) {
                clearInterval(interviewState.timerInterval);
                interviewState.timerInterval = null;
            }
            
            // Reset all question items to inactive
            document.querySelectorAll('.question-item').forEach(item => {
                item.classList.remove('active');
            });
            
            // Activate first question
            const firstQuestion = document.querySelector('.question-item');
            if (firstQuestion) firstQuestion.classList.add('active');
        }

        // Update progress bar and text
        function updateProgress() {
            const progress = (interviewState.currentQuestion / interviewState.totalQuestions) * 100;
            progressFill.style.width = `${progress}%`;
            progressText.textContent = `Question ${interviewState.currentQuestion} of ${interviewState.totalQuestions}`;
            
            // Update navigation buttons
            updateNavigationButtons();
        }

        // Start interview timer
        function startTimer() {
            interviewState.timer = 0;
            interviewState.timerInterval = setInterval(() => {
                interviewState.timer++;
                const minutes = Math.floor(interviewState.timer / 60);
                const seconds = interviewState.timer % 60;
                interviewTimer.textContent = `${minutes.toString().padStart(2, '0')}:${seconds.toString().padStart(2, '0')}`;
            }, 1000);
        }

        // Stop interview timer
        function stopTimer() {
            if (interviewState.timerInterval) {
                clearInterval(interviewState.timerInterval);
                interviewState.timerInterval = null;
            }
        }

        // Start voice recording
        async function startRecording() {
            try {
                // In a real implementation, this would use the MediaRecorder API
                // For demo purposes, we'll simulate the recording
                interviewState.isRecording = true;
                recordBtn.innerHTML = '<i class="fas fa-stop"></i> Stop Recording';
                recordBtn.classList.add('recording');
                avatarStatus.textContent = "Recording your response...";
                
                // Simulate recording for 30 seconds then auto-stop
                setTimeout(() => {
                    if (interviewState.isRecording) {
                        stopRecording();
                    }
                }, 30000);
                
            } catch (error) {
                console.error('Error starting recording:', error);
                showNotification('Error accessing microphone. Please check permissions.');
            }
        }

        // Stop voice recording
        function stopRecording() {
            if (interviewState.isRecording) {
                interviewState.isRecording = false;
                recordBtn.innerHTML = '<i class="fas fa-microphone"></i> Start Recording';
                recordBtn.classList.remove('recording');
                avatarStatus.textContent = "Recording saved";
                downloadBtn.disabled = false;
                
                // Save the recording and simulate user response
                saveRecording();
                
                // Simulate storing user response for AI analysis
                const currentQuestion = document.querySelector('.question-item.active');
                if (currentQuestion) {
                    interviewState.userResponses.push({
                        question: currentQuestion.textContent,
                        answer: `Simulated response to: "${currentQuestion.textContent}". This is a sample answer that would be analyzed by AI for content quality, communication skills, and technical accuracy.`,
                        timestamp: new Date().toISOString()
                    });
                }
            }
        }

        // Save recording to local storage
        function saveRecording() {
            const recording = {
                id: Date.now(),
                name: `Interview_${interviewState.selectedRole}_${new Date().toLocaleDateString()}`,
                date: new Date().toLocaleString(),
                role: interviewState.selectedRole,
                level: interviewState.selectedLevel,
                duration: interviewState.timer
            };
            
            interviewState.recordings.push(recording);
            localStorage.setItem('interviewRecordings', JSON.stringify(interviewState.recordings));
            
            // Refresh recordings list
            loadRecordings();
        }

        // Load recordings from local storage
        function loadRecordings() {
            const savedRecordings = localStorage.getItem('interviewRecordings');
            if (savedRecordings) {
                interviewState.recordings = JSON.parse(savedRecordings);
            }
            
            recordingsContainer.innerHTML = '';
            
            if (interviewState.recordings.length === 0) {
                recordingsContainer.innerHTML = '<p>No recordings yet. Complete an interview to see your recordings here.</p>';
                return;
            }
            
            interviewState.recordings.forEach(recording => {
                const recordingItem = document.createElement('div');
                recordingItem.className = 'recording-item';
                recordingItem.innerHTML = `
                    <div class="recording-info">
                        <div class="recording-name">${recording.name}</div>
                        <div class="recording-date">${recording.date} | ${recording.role} | ${recording.level}</div>
                    </div>
                    <div class="recording-actions">
                        <button class="action-btn download-recording" data-id="${recording.id}">
                            <i class="fas fa-download"></i>
                        </button>
                        <button class="action-btn delete-recording" data-id="${recording.id}">
                            <i class="fas fa-trash"></i>
                        </button>
                    </div>
                `;
                recordingsContainer.appendChild(recordingItem);
            });
            
            // Add event listeners for recording actions
            document.querySelectorAll('.download-recording').forEach(btn => {
                btn.addEventListener('click', (e) => {
                    const id = e.target.closest('button').getAttribute('data-id');
                    downloadRecording(id);
                });
            });
            
            document.querySelectorAll('.delete-recording').forEach(btn => {
                btn.addEventListener('click', (e) => {
                    const id = e.target.closest('button').getAttribute('data-id');
                    deleteRecording(id);
                });
            });
        }

        // Download a specific recording
        function downloadRecording(id) {
            const recording = interviewState.recordings.find(r => r.id == id);
            if (recording) {
                showNotification(`Downloading ${recording.name}...`);
                // In a real implementation, this would download the actual audio file
            }
        }

        // Delete a specific recording
        function deleteRecording(id) {
            interviewState.recordings = interviewState.recordings.filter(r => r.id != id);
            localStorage.setItem('interviewRecordings', JSON.stringify(interviewState.recordings));
            loadRecordings();
            showNotification('Recording deleted successfully');
        }

        // Simulate AI asking questions with voice
        function askQuestion(questionIndex) {
            const allQuestions = document.querySelectorAll('.question-item');
            
            // Remove active class from all questions
            allQuestions.forEach(q => q.classList.remove('active'));
            
            // Add active class to current question
            if (allQuestions[questionIndex]) {
                allQuestions[questionIndex].classList.add('active');
                
                // Enable the play button for this question
                playQuestionBtn.disabled = false;
                
                // Speak the question
                speakText(allQuestions[questionIndex].textContent);
            }
            
            // Update progress
            interviewState.currentQuestion = questionIndex + 1;
            updateProgress();
        }

        // Start the interview
        function startInterview() {
            interviewState.isActive = true;
            startInterviewBtn.disabled = true;
            startInterviewBtn.textContent = "Interview in Progress";
            startTimer();
            
            // Enable navigation buttons
            backQuestionBtn.disabled = false;
            nextQuestionBtn.disabled = false;
            
            // Start with first question
            askQuestion(0);
        }

        // Event Listeners for Navigation
        loginBtn.addEventListener('click', showLoginPage);
        registerBtn.addEventListener('click', showRegisterPage);
        backFromLogin.addEventListener('click', showLandingPage);
        backFromRegister.addEventListener('click', showLandingPage);
        goToRegister.addEventListener('click', showRegisterPage);
        goToLogin.addEventListener('click', showLoginPage);
        logoutBtn.addEventListener('click', showLandingPage);
        exitDashboardBtn.addEventListener('click', showLandingPage);
        exitInterviewBtn.addEventListener('click', showLandingPage);

        // Voice control event listeners
        playQuestionBtn.addEventListener('click', () => {
            const allQuestions = document.querySelectorAll('.question-item');
            const activeQuestion = document.querySelector('.question-item.active');
            
            if (activeQuestion) {
                speakText(activeQuestion.textContent);
            }
        });

        stopVoiceBtn.addEventListener('click', stopSpeech);

        // Navigation control event listeners
        backQuestionBtn.addEventListener('click', previousQuestion);
        nextQuestionBtn.addEventListener('click', nextQuestion);

        // Video control event listeners
        startVideoBtn.addEventListener('click', startVideoRecording);
        stopVideoBtn.addEventListener('click', stopVideoRecording);
        downloadVideoBtn.addEventListener('click', downloadRecordedVideo);

        // AI Feedback event listeners
        analyzeFeedbackBtn.addEventListener('click', generateAIFeedback);
        downloadFeedbackBtn.addEventListener('click', downloadFeedbackReport);

        // Form Submission Handlers
        loginForm.addEventListener('submit', (e) => {
            e.preventDefault();
            const email = document.getElementById('login-email').value;
            const password = document.getElementById('login-password').value;
            
            // Simple validation
            if (email && password) {
                // In a real app, you would make an API call here
                const user = {
                    name: email.split('@')[0],
                    email: email
                };
                
                showNotification('Login successful! Redirecting to dashboard...');
                // Reset form
                loginForm.reset();
                // Show dashboard
                setTimeout(() => {
                    showDashboard(user);
                }, 1000);
            } else {
                showNotification('Please fill in all fields');
            }
        });

        registerForm.addEventListener('submit', (e) => {
            e.preventDefault();
            const name = document.getElementById('register-name').value;
            const email = document.getElementById('register-email').value;
            const password = document.getElementById('register-password').value;
            const confirmPassword = document.getElementById('register-confirm').value;
            
            // Simple validation
            if (name && email && password && confirmPassword) {
                if (password !== confirmPassword) {
                    showNotification('Passwords do not match');
                    return;
                }
                
                // In a real app, you would make an API call here
                const user = {
                    name: name,
                    email: email
                };
                
                showNotification('Account created successfully! Redirecting to dashboard...');
                // Reset form
                registerForm.reset();
                // Show dashboard
                setTimeout(() => {
                    showDashboard(user);
                }, 1000);
            } else {
                showNotification('Please fill in all fields');
            }
        });

        // Interview control event listeners
        startInterviewBtn.addEventListener('click', startInterview);
        
        recordBtn.addEventListener('click', () => {
            if (interviewState.isRecording) {
                stopRecording();
            } else {
                startRecording();
            }
        });
        
        downloadBtn.addEventListener('click', () => {
            showNotification('Downloading your interview recording...');
            // In a real app, this would download the actual recording
        });

        // Question item click event listeners
        document.addEventListener('click', (e) => {
            if (e.target.classList.contains('question-item')) {
                const questionIndex = parseInt(e.target.dataset.index);
                if (!isNaN(questionIndex)) {
                    // Update current question
                    interviewState.currentQuestion = questionIndex + 1;
                    updateProgress();
                    
                    // Enable play button for this question
                    playQuestionBtn.disabled = false;
                    
                    // Speak the question if interview is active
                    if (interviewState.isActive) {
                        speakText(e.target.textContent);
                    }
                }
            }
        });

        // Scroll event for header animation
        window.addEventListener('scroll', () => {
            if (window.scrollY > 50) {
                header.classList.add('scrolled');
            } else {
                header.classList.remove('scrolled');
            }
            
            // Trigger animations when elements come into view
            animateOnScroll();
        });

        // Smooth scrolling for navigation links
        aboutLink.addEventListener('click', (e) => {
            e.preventDefault();
            document.querySelector('.process-section').scrollIntoView({ 
                behavior: 'smooth' 
            });
        });

        processLink.addEventListener('click', (e) => {
            e.preventDefault();
            document.getElementById('process').scrollIntoView({ 
                behavior: 'smooth' 
            });
        });

        featuresLink.addEventListener('click', (e) => {
            e.preventDefault();
            document.getElementById('features').scrollIntoView({ 
                behavior: 'smooth' 
            });
        });

        // Button click handlers
        startPracticeBtn.addEventListener('click', () => {
            showNotification('Starting practice session...');
        });

        demoBtn.addEventListener('click', () => {
            showNotification('Opening demo video...');
        });

        mockInterviewBtn.addEventListener('click', () => {
            showNotification('Opening mock interview feature...');
        });

        aiFeedbackBtn.addEventListener('click', () => {
            showNotification('Accessing AI feedback system...');
        });

        resumeAnalysisBtn.addEventListener('click', () => {
            showNotification('Launching resume analysis tool...');
        });

        // Social login buttons
        document.querySelectorAll('.social-btn').forEach(btn => {
            btn.addEventListener('click', () => {
                const platform = btn.classList.contains('google') ? 'Google' : 
                               btn.classList.contains('facebook') ? 'Facebook' : 'LinkedIn';
                showNotification(`Connecting with ${platform}...`);
            });
        });

        // Animation on scroll function
        function animateOnScroll() {
            const steps = document.querySelectorAll('.step');
            const features = document.querySelectorAll('.feature-card');
            const stats = document.querySelectorAll('.stat-item');
            
            const triggerBottom = window.innerHeight * 0.85;
            
            steps.forEach(step => {
                const stepTop = step.getBoundingClientRect().top;
                if (stepTop < triggerBottom) {
                    step.classList.add('animate');
                }
            });
            
            features.forEach(feature => {
                const featureTop = feature.getBoundingClientRect().top;
                if (featureTop < triggerBottom) {
                    feature.classList.add('animate');
                }
            });
            
            stats.forEach(stat => {
                const statTop = stat.getBoundingClientRect().top;
                if (statTop < triggerBottom) {
                    stat.classList.add('animate');
                }
            });
        }

        // Show notification function
        function showNotification(message) {
            // Create notification element
            const notification = document.createElement('div');
            notification.style.cssText = `
                position: fixed;
                top: 100px;
                right: 20px;
                background: linear-gradient(135deg, #4361ee, #3a0ca3);
                color: white;
                padding: 15px 25px;
                border-radius: 10px;
                box-shadow: 0 10px 25px rgba(0,0,0,0.2);
                z-index: 10000;
                font-weight: 600;
                transform: translateX(150%);
                transition: transform 0.5s ease;
                max-width: 300px;
            `;
            notification.textContent = message;
            document.body.appendChild(notification);
            
            // Animate in
            setTimeout(() => {
                notification.style.transform = 'translateX(0)';
            }, 100);
            
            // Animate out and remove
            setTimeout(() => {
                notification.style.transform = 'translateX(150%)';
                setTimeout(() => {
                    document.body.removeChild(notification);
                }, 500);
            }, 3000);
        }

        // Initialize the application
        function initApp() {
            populateRoleCards();
            animateOnScroll();
            
            // Check browser support for speech synthesis
            if (!('speechSynthesis' in window)) {
                console.warn('Speech synthesis not supported in this browser');
                showNotification('Voice features not supported in your browser');
            }
            
            // Check browser support for MediaRecorder
            if (!('MediaRecorder' in window)) {
                console.warn('MediaRecorder not supported in this browser');
                showNotification('Video recording not supported in your browser');
                startVideoBtn.disabled = true;
                startVideoBtn.textContent = 'Not Supported';
            }
        }

        // Initialize the app
        initApp();
    </script>
</body>
</html> 
