# Car-Dealership
Project completed by using the sql, html,css  languages
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Car Dealership Dashboard</title>
    <style>
        :root {
            --primary: #2563eb;
            --primary-dark: #1d4ed8;
            --secondary: #64748b;
            --accent: #10b981;
            --danger: #ef4444;
            --warning: #f59e0b;
            --light: #f8fafc;
            --dark: #1e293b;
            --border: #e2e8f0;
            --card-shadow: 0 4px 6px rgba(0, 0, 0, 0.1);
            --transition: all 0.3s ease;
        }
        
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
            font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
        }
        
        body {
            background-color: #f1f5f9;
            color: var(--dark);
            line-height: 1.6;
        }
        
        .container {
            max-width: 1200px;
            margin: 0 auto;
            padding: 0 20px;
        }
        
        header {
            background: linear-gradient(135deg, var(--primary), var(--primary-dark));
            color: white;
            padding: 2rem 0;
            box-shadow: 0 4px 6px rgba(0, 0, 0, 0.1);
        }
        
        .header-content {
            display: flex;
            justify-content: space-between;
            align-items: center;
        }
        
        h1 {
            font-size: 2.5rem;
            margin-bottom: 0.5rem;
        }
        
        .subtitle {
            font-size: 1.1rem;
            opacity: 0.9;
        }
        
        .stats-container {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(250px, 1fr));
            gap: 20px;
            margin: 30px 0;
        }
        
        .stat-card {
            background: white;
            border-radius: 12px;
            padding: 20px;
            box-shadow: var(--card-shadow);
            transition: var(--transition);
        }
        
        .stat-card:hover {
            transform: translateY(-5px);
            box-shadow: 0 10px 15px rgba(0, 0, 0, 0.1);
        }
        
        .stat-value {
            font-size: 2rem;
            font-weight: bold;
            color: var(--primary);
            margin: 10px 0;
        }
        
        .stat-label {
            color: var(--secondary);
            font-size: 0.9rem;
        }
        
        .dashboard-section {
            background: white;
            border-radius: 12px;
            padding: 25px;
            margin-bottom: 30px;
            box-shadow: var(--card-shadow);
        }
        
        .section-header {
            display: flex;
            justify-content: space-between;
            align-items: center;
            margin-bottom: 20px;
            padding-bottom: 15px;
            border-bottom: 1px solid var(--border);
        }
        
        .section-title {
            font-size: 1.5rem;
            color: var(--dark);
        }
        
        table {
            width: 100%;
            border-collapse: collapse;
            margin-top: 15px;
        }
        
        th, td {
            padding: 12px 15px;
            text-align: left;
            border-bottom: 1px solid var(--border);
        }
        
        th {
            background-color: #f8fafc;
            font-weight: 600;
            color: var(--dark);
        }
        
        tr:hover {
            background-color: #f8fafc;
        }
        
        .price {
            font-weight: bold;
            color: var(--accent);
        }
        
        .badge {
            display: inline-block;
            padding: 5px 10px;
            border-radius: 20px;
            font-size: 0.8rem;
            font-weight: 500;
        }
        
        .badge-success {
            background-color: #d1fae5;
            color: #065f46;
        }
        
        .badge-warning {
            background-color: #fef3c7;
            color: #92400e;
        }
        
        .filters {
            display: flex;
            gap: 15px;
            margin-bottom: 20px;
        }
        
        .filter-btn {
            padding: 8px 16px;
            background: white;
            border: 1px solid var(--border);
            border-radius: 6px;
            cursor: pointer;
            transition: var(--transition);
        }
        
        .filter-btn.active {
            background: var(--primary);
            color: white;
            border-color: var(--primary);
        }
        
        footer {
            text-align: center;
            padding: 20px 0;
            margin-top: 40px;
            color: var(--secondary);
            font-size: 0.9rem;
        }
        
        @media (max-width: 768px) {
            .header-content {
                flex-direction: column;
                text-align: center;
            }
            
            .stats-container {
                grid-template-columns: 1fr;
            }
            
            table {
                display: block;
                overflow-x: auto;
            }
            
            .filters {
                flex-wrap: wrap;
            }
        }
    </style>
</head>
<body>
    <header>
        <div class="container">
            <div class="header-content">
                <div>
                    <h1>Car Dealership Dashboard</h1>
                    <p class="subtitle">Manage your inventory, sales, and customers</p>
                </div>
            </div>
        </div>
    </header>

    <main class="container">
        <!-- Stats Overview -->
        <div class="stats-container">
            <div class="stat-card">
                <div class="stat-label">Total Cars in Inventory</div>
                <div class="stat-value">12</div>
                <div>Across 2 dealerships</div>
            </div>
            <div class="stat-card">
                <div class="stat-label">Total Sales</div>
                <div class="stat-value">₹15.7L</div>
                <div>From 2 transactions</div>
            </div>
            <div class="stat-card">
                <div class="stat-label">Average Sale Price</div>
                <div class="stat-value">₹7.85L</div>
                <div>Across all sales</div>
            </div>
            <div class="stat-card">
                <div class="stat-label">Active Customers</div>
                <div class="stat-value">2</div>
                <div>With purchase history</div>
            </div>
        </div>

        <!-- Cars with Dealer Information -->
        <section class="dashboard-section">
            <div class="section-header">
                <h2 class="section-title">Cars with Dealer Information</h2>
            </div>
            <table>
                <thead>
                    <tr>
                        <th>Model</th>
                        <th>Brand</th>
                        <th>Price</th>
                        <th>Dealer</th>
                    </tr>
                </thead>
                <tbody>
                    <tr>
                        <td>Swift</td>
                        <td>Maruti</td>
                        <td class="price">₹600,000</td>
                        <td>AutoWorld</td>
                    </tr>
                    <tr>
                        <td>City</td>
                        <td>Honda</td>
                        <td class="price">₹1,000,000</td>
                        <td>SpeedMotors</td>
                    </tr>
                </tbody>
            </table>
        </section>

        <!-- Total Cars Sold per Dealer -->
        <section class="dashboard-section">
            <div class="section-header">
                <h2 class="section-title">Total Cars Sold per Dealer</h2>
            </div>
            <table>
                <thead>
                    <tr>
                        <th>Dealer Name</th>
                        <th>Total Cars Sold</th>
                    </tr>
                </thead>
                <tbody>
                    <tr>
                        <td>AutoWorld</td>
                        <td>1</td>
                    </tr>
                    <tr>
                        <td>SpeedMotors</td>
                        <td>1</td>
                    </tr>
                </tbody>
            </table>
        </section>

        <!-- High Value Sales -->
        <section class="dashboard-section">
            <div class="section-header">
                <h2 class="section-title">High Value Sales (> ₹900,000)</h2>
            </div>
            <table>
                <thead>
                    <tr>
                        <th>Customer Name</th>
                        <th>Sale Price</th>
                    </tr>
                </thead>
                <tbody>
                    <tr>
                        <td>Anita Sharma</td>
                        <td class="price">₹980,000</td>
                    </tr>
                </tbody>
            </table>
        </section>

        <!-- Total Revenue per Dealer -->
        <section class="dashboard-section">
            <div class="section-header">
                <h2 class="section-title">Total Revenue per Dealer</h2>
            </div>
            <table>
                <thead>
                    <tr>
                        <th>Dealer Name</th>
                        <th>Total Revenue</th>
                    </tr>
                </thead>
                <tbody>
                    <tr>
                        <td>AutoWorld</td>
                        <td class="price">₹590,000</td>
                    </tr>
                    <tr>
                        <td>SpeedMotors</td>
                        <td class="price">₹980,000</td>
                    </tr>
                </tbody>
            </table>
        </section>

        <!-- Full Sales Report -->
        <section class="dashboard-section">
            <div class="section-header">
                <h2 class="section-title">Full Sales Report</h2>
            </div>
            <table>
                <thead>
                    <tr>
                        <th>Sale ID</th>
                        <th>Dealer Name</th>
                        <th>Car Model</th>
                        <th>Customer Name</th>
                        <th>Sale Date</th>
                        <th>Sale Price</th>
                    </tr>
                </thead>
                <tbody>
                    <tr>
                        <td>301</td>
                        <td>AutoWorld</td>
                        <td>Swift</td>
                        <td>Ravi Kumar</td>
                        <td>2025-07-01</td>
                        <td class="price">₹590,000</td>
                    </tr>
                    <tr>
                        <td>302</td>
                        <td>SpeedMotors</td>
                        <td>City</td>
                        <td>Anita Sharma</td>
                        <td>2025-07-15</td>
                        <td class="price">₹980,000</td>
                    </tr>
                </tbody>
            </table>
        </section>

        <!-- Total Sales per Dealer -->
        <section class="dashboard-section">
            <div class="section-header">
                <h2 class="section-title">Total Sales per Dealer</h2>
            </div>
            <table>
                <thead>
                    <tr>
                        <th>Dealer Name</th>
                        <th>Total Sales</th>
                    </tr>
                </thead>
                <tbody>
                    <tr>
                        <td>AutoWorld</td>
                        <td class="price">₹590,000</td>
                    </tr>
                    <tr>
                        <td>SpeedMotors</td>
                        <td class="price">₹980,000</td>
                    </tr>
                </tbody>
            </table>
        </section>

        <!-- Cars with Optional Sales -->
        <section class="dashboard-section">
            <div class="section-header">
                <h2 class="section-title">Cars with Optional Sales</h2>
            </div>
            <table>
                <thead>
                    <tr>
                        <th>Model</th>
                        <th>Brand</th>
                        <th>Dealer Name</th>
                        <th>Sale ID</th>
                    </tr>
                </thead>
                <tbody>
                    <tr>
                        <td>Swift</td>
                        <td>Maruti</td>
                        <td>AutoWorld</td>
                        <td><span class="badge badge-success">301</span></td>
                    </tr>
                    <tr>
                        <td>City</td>
                        <td>Honda</td>
                        <td>SpeedMotors</td>
                        <td><span class="badge badge-success">302</span></td>
                    </tr>
                </tbody>
            </table>
        </section>

        <!-- July 2025 Sales -->
        <section class="dashboard-section">
            <div class="section-header">
                <h2 class="section-title">July 2025 Sales</h2>
            </div>
            <table>
                <thead>
                    <tr>
                        <th>Sale ID</th>
                        <th>Model</th>
                        <th>Customer</th>
                        <th>Sale Date</th>
                        <th>Sale Price</th>
                    </tr>
                </thead>
                <tbody>
                    <tr>
                        <td>301</td>
                        <td>Swift</td>
                        <td>Ravi Kumar</td>
                        <td>2025-07-01</td>
                        <td class="price">₹590,000</td>
                    </tr>
                    <tr>
                        <td>302</td>
                        <td>City</td>
                        <td>Anita Sharma</td>
                        <td>2025-07-15</td>
                        <td class="price">₹980,000</td>
                    </tr>
                </tbody>
            </table>
        </section>
    </main>

    <footer>
        <div class="container">
            <p>Car Dealership Management System © 2025</p>
        </div>
    </footer>

    <script>
        // Simple JavaScript for interactive elements
        document.addEventListener('DOMContentLoaded', function() {
            // Add interactivity to filter buttons if needed
            const filterButtons = document.querySelectorAll('.filter-btn');
            
            filterButtons.forEach(button => {
                button.addEventListener('click', function() {
                    filterButtons.forEach(btn => btn.classList.remove('active'));
                    this.classList.add('active');
                });
            });
        });
    </script>
</body>
</html>

