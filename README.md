<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>TradeZeella Pro | Ultimate Trading Journal</title>
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.4.0/css/all.min.css">
    <script src="https://cdn.jsdelivr.net/npm/chart.js"></script>
    <link href="https://fonts.googleapis.com/css2?family=Poppins:wght@300;400;500;600;700&family=Roboto+Mono:wght@400;500&display=swap" rel="stylesheet">
    <style>
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
            font-family: 'Poppins', sans-serif;
        }
        
        :root {
            --primary: #2563eb;
            --primary-light: #3b82f6;
            --secondary: #8b5cf6;
            --success: #10b981;
            --danger: #ef4444;
            --warning: #f59e0b;
            --dark: #0f172a;
            --darker: #0b1120;
            --card-bg: rgba(30, 41, 59, 0.85);
            --card-border: rgba(100, 116, 139, 0.2);
            --text-light: #f1f5f9;
            --text-gray: #94a3b8;
            --accent: #0ea5e9;
            --purple: #a855f7;
            --pink: #ec4899;
        }
        
        body {
            background: radial-gradient(circle at top left, var(--darker), var(--dark));
            color: var(--text-light);
            min-height: 100vh;
            overflow-x: hidden;
            position: relative;
        }
        
        /* Animated background elements */
        .bg-element {
            position: absolute;
            border-radius: 50%;
            background: radial-gradient(circle, var(--primary-light) 0%, transparent 70%);
            opacity: 0.1;
            z-index: -1;
        }
        
        /* Header styling */
        header {
            display: flex;
            justify-content: space-between;
            align-items: center;
            padding: 20px 40px;
            background: rgba(15, 23, 42, 0.8);
            backdrop-filter: blur(10px);
            border-bottom: 1px solid var(--card-border);
        }
        
        .logo-container {
            display: flex;
            align-items: center;
            gap: 15px;
        }
        
        .logo {
            width: 50px;
            height: 50px;
            background: linear-gradient(135deg, var(--primary), var(--secondary));
            border-radius: 12px;
            display: flex;
            align-items: center;
            justify-content: center;
            font-size: 24px;
            font-weight: bold;
            color: white;
        }
        
        .brand-text h1 {
            font-size: 28px;
            background: linear-gradient(90deg, var(--primary-light), var(--purple));
            -webkit-background-clip: text;
            -webkit-text-fill-color: transparent;
        }
        
        .brand-text p {
            font-size: 14px;
            color: var(--text-gray);
            letter-spacing: 1px;
        }
        
        /* Main layout */
        .container {
            display: grid;
            grid-template-columns: 250px 1fr;
            max-width: 1800px;
            margin: 0 auto;
            padding: 20px;
            gap: 25px;
        }
        
        /* Sidebar navigation */
        .sidebar {
            background: var(--card-bg);
            border-radius: 20px;
            padding: 25px 0;
            border: 1px solid var(--card-border);
            backdrop-filter: blur(10px);
            box-shadow: 0 10px 30px rgba(0, 0, 0, 0.3);
            height: fit-content;
        }
        
        .nav-section {
            padding: 0 20px;
            margin-bottom: 25px;
        }
        
        .nav-title {
            color: var(--text-gray);
            font-size: 14px;
            text-transform: uppercase;
            letter-spacing: 1px;
            margin-bottom: 15px;
        }
        
        .nav-item {
            display: flex;
            align-items: center;
            gap: 12px;
            padding: 12px 15px;
            border-radius: 12px;
            margin-bottom: 8px;
            color: var(--text-light);
            text-decoration: none;
            transition: all 0.3s ease;
            font-weight: 500;
        }
        
        .nav-item:hover, .nav-item.active {
            background: rgba(59, 130, 246, 0.15);
            color: var(--primary-light);
            transform: translateX(5px);
        }
        
        .nav-item i {
            width: 24px;
            text-align: center;
        }
        
        /* Main content area */
        .main-content {
            display: grid;
            grid-template-columns: 1fr 350px;
            gap: 25px;
        }
        
        /* Dashboard grid */
        .dashboard-grid {
            display: grid;
            grid-template-columns: repeat(2, 1fr);
            gap: 25px;
            margin-bottom: 25px;
        }
        
        /* Card styling */
        .card {
            background: var(--card-bg);
            border-radius: 20px;
            padding: 25px;
            border: 1px solid var(--card-border);
            backdrop-filter: blur(10px);
            box-shadow: 0 10px 30px rgba(0, 0, 0, 0.2);
        }
        
        .card-header {
            display: flex;
            justify-content: space-between;
            align-items: center;
            margin-bottom: 20px;
        }
        
        .card-title {
            font-size: 20px;
            font-weight: 600;
            color: var(--primary-light);
            display: flex;
            align-items: center;
            gap: 10px;
        }
        
        .card-actions {
            display: flex;
            gap: 10px;
        }
        
        /* Stats grid */
        .stats-grid {
            display: grid;
            grid-template-columns: repeat(4, 1fr);
            gap: 20px;
            margin-bottom: 25px;
        }
        
        .stat-card {
            background: rgba(30, 41, 59, 0.7);
            border-radius: 16px;
            padding: 20px;
            text-align: center;
            border: 1px solid var(--card-border);
            transition: all 0.3s ease;
        }
        
        .stat-card:hover {
            transform: translateY(-5px);
            box-shadow: 0 10px 20px rgba(0, 0, 0, 0.3);
        }
        
        .stat-value {
            font-size: 32px;
            font-weight: 700;
            margin: 10px 0;
            background: linear-gradient(90deg, var(--primary-light), var(--pink));
            -webkit-background-clip: text;
            -webkit-text-fill-color: transparent;
            font-family: 'Roboto Mono', monospace;
        }
        
        .stat-label {
            color: var(--text-gray);
            font-size: 14px;
        }
        
        /* Trades table */
        .trades-table {
            width: 100%;
            border-collapse: collapse;
            margin-top: 15px;
            font-size: 14px;
        }
        
        .trades-table th {
            text-align: left;
            padding: 15px;
            color: var(--primary-light);
            font-weight: 600;
            border-bottom: 1px solid var(--card-border);
            background: rgba(30, 41, 59, 0.5);
        }
        
        .trades-table td {
            padding: 15px;
            border-bottom: 1px solid var(--card-border);
        }
        
        .trades-table tr:hover {
            background: rgba(59, 130, 246, 0.05);
        }
        
        .trade-badge {
            padding: 6px 12px;
            border-radius: 20px;
            font-size: 12px;
            font-weight: 600;
            display: inline-block;
        }
        
        .trade-long {
            background: rgba(16, 185, 129, 0.15);
            color: var(--success);
        }
        
        .trade-short {
            background: rgba(239, 68, 68, 0.15);
            color: var(--danger);
        }
        
        /* Buttons */
        .btn {
            padding: 10px 20px;
            border-radius: 12px;
            font-weight: 600;
            cursor: pointer;
            transition: all 0.3s ease;
            border: none;
            font-size: 14px;
            display: inline-flex;
            align-items: center;
            gap: 8px;
        }
        
        .btn-primary {
            background: linear-gradient(135deg, var(--primary), var(--secondary));
            color: white;
        }
        
        .btn-primary:hover {
            transform: translateY(-3px);
            box-shadow: 0 5px 15px rgba(59, 130, 246, 0.4);
        }
        
        .btn-outline {
            background: transparent;
            border: 1px solid var(--primary-light);
            color: var(--primary-light);
        }
        
        .btn-outline:hover {
            background: rgba(59, 130, 246, 0.1);
        }
        
        /* Trade replay */
        .trade-replay {
            display: flex;
            flex-direction: column;
            gap: 20px;
        }
        
        .replay-controls {
            display: flex;
            gap: 10px;
            justify-content: center;
        }
        
        .replay-chart {
            height: 300px;
            background: rgba(30, 41, 59, 0.5);
            border-radius: 16px;
            padding: 20px;
        }
        
        /* Trade simulator */
        .simulator-container {
            display: flex;
            flex-direction: column;
            gap: 15px;
        }
        
        .simulator-actions {
            display: grid;
            grid-template-columns: repeat(3, 1fr);
            gap: 10px;
        }
        
        .sim-action-btn {
            padding: 12px;
            border-radius: 12px;
            background: rgba(30, 41, 59, 0.7);
            border: 1px solid var(--card-border);
            display: flex;
            flex-direction: column;
            align-items: center;
            justify-content: center;
            gap: 8px;
            cursor: pointer;
            transition: all 0.3s ease;
        }
        
        .sim-action-btn:hover {
            background: rgba(59, 130, 246, 0.15);
            transform: translateY(-3px);
        }
        
        .sim-action-btn i {
            font-size: 24px;
            color: var(--primary-light);
        }
        
        /* Performance chart */
        .performance-chart {
            height: 300px;
            margin-top: 20px;
        }
        
        /* Footer */
        footer {
            text-align: center;
            padding: 30px;
            color: var(--text-gray);
            font-size: 14px;
            margin-top: 50px;
            border-top: 1px solid var(--card-border);
        }
        
        /* Responsive design */
        @media (max-width: 1400px) {
            .stats-grid {
                grid-template-columns: repeat(2, 1fr);
            }
            
            .dashboard-grid {
                grid-template-columns: 1fr;
            }
        }
        
        @media (max-width: 1100px) {
            .container {
                grid-template-columns: 1fr;
            }
            
            .sidebar {
                display: none;
            }
            
            .main-content {
                grid-template-columns: 1fr;
            }
        }
        
        @media (max-width: 768px) {
            .stats-grid {
                grid-template-columns: 1fr;
            }
            
            header {
                flex-direction: column;
                gap: 20px;
                text-align: center;
            }
        }
    </style>
</head>
<body>
    <!-- Animated background elements -->
    <div class="bg-element" style="width: 600px; height: 600px; top: -300px; right: -300px;"></div>
    <div class="bg-element" style="width: 400px; height: 400px; bottom: -200px; left: -200px; background: radial-gradient(circle, var(--secondary) 0%, transparent 70%);"></div>
    
    <!-- Header -->
    <header>
        <div class="logo-container">
            <div class="logo">TZ</div>
            <div class="brand-text">
                <h1>TradeZeella Pro</h1>
                <p>World's Most Advanced Trading Journal</p>
            </div>
        </div>
        <div class="user-actions">
            <button class="btn btn-outline">
                <i class="fas fa-sync-alt"></i> Sync Accounts
            </button>
            <button class="btn btn-primary">
                <i class="fas fa-plus"></i> New Trade
            </button>
        </div>
    </header>
    
    <div class="container">
        <!-- Sidebar Navigation -->
        <div class="sidebar">
            <div class="nav-section">
                <div class="nav-title">Main</div>
                <a href="#" class="nav-item active">
                    <i class="fas fa-home"></i> Dashboard
                </a>
                <a href="#" class="nav-item">
                    <i class="fas fa-book"></i> Trade Journal
                </a>
                <a href="#" class="nav-item">
                    <i class="fas fa-chart-line"></i> Analytics
                </a>
                <a href="#" class="nav-item">
                    <i class="fas fa-play-circle"></i> Trade Replay
                </a>
            </div>
            
            <div class="nav-section">
                <div class="nav-title">Tools</div>
                <a href="#" class="nav-item">
                    <i class="fas fa-bullseye"></i> Strategy Tester
                </a>
                <a href="#" class="nav-item">
                    <i class="fas fa-calculator"></i> Risk Calculator
                </a>
                <a href="#" class="nav-item">
                    <i class="fas fa-brain"></i> Psychology Tracker
                </a>
                <a href="#" class="nav-item">
                    <i class="fas fa-trophy"></i> Goal Tracking
                </a>
            </div>
            
            <div class="nav-section">
                <div class="nav-title">Integrations</div>
                <a href="#" class="nav-item">
                    <i class="fab fa-meta"></i> MetaTrader
                </a>
                <a href="#" class="nav-item">
                    <i class="fas fa-chart-bar"></i> TradingView
                </a>
                <a href="#" class="nav-item">
                    <i class="fab fa-java"></i> JForex
                </a>
                <a href="#" class="nav-item">
                    <i class="fas fa-file-csv"></i> CSV Import
                </a>
            </div>
            
            <div class="nav-section">
                <div class="nav-title">Education</div>
                <a href="#" class="nav-item">
                    <i class="fas fa-graduation-cap"></i> Trading Academy
                </a>
                <a href="#" class="nav-item">
                    <i class="fas fa-video"></i> Video Library
                </a>
                <a href="#" class="nav-item">
                    <i class="fas fa-lightbulb"></i> Trade Ideas
                </a>
                <a href="#" class="nav-item">
                    <i class="fas fa-users"></i> Community
                </a>
            </div>
        </div>
        
        <!-- Main Content -->
        <div class="main-content">
            <div>
                <!-- Stats Overview -->
                <div class="stats-grid">
                    <div class="stat-card">
                        <div class="stat-value">$84,562</div>
                        <div class="stat-label">Account Balance</div>
                    </div>
                    <div class="stat-card">
                        <div class="stat-value">76.3%</div>
                        <div class="stat-label">Win Rate</div>
                    </div>
                    <div class="stat-card">
                        <div class="stat-value">2.84</div>
                        <div class="stat-label">Profit Factor</div>
                    </div>
                    <div class="stat-card">
                        <div class="stat-value">1:2.1</div>
                        <div class="stat-label">Risk/Reward</div>
                    </div>
                </div>
                
                <!-- Dashboard Grid -->
                <div class="dashboard-grid">
                    <!-- Trade Journal -->
                    <div class="card">
                        <div class="card-header">
                            <div class="card-title">
                                <i class="fas fa-book"></i>
                                <span>Recent Trades</span>
                            </div>
                            <div class="card-actions">
                                <button class="btn btn-outline">
                                    <i class="fas fa-filter"></i> Filter
                                </button>
                                <button class="btn btn-outline">
                                    <i class="fas fa-export"></i> Export
                                </button>
                            </div>
                        </div>
                        <div style="overflow-x: auto;">
                            <table class="trades-table">
                                <thead>
                                    <tr>
                                        <th>Asset</th>
                                        <th>Strategy</th>
                                        <th>Direction</th>
                                        <th>Entry</th>
                                        <th>Exit</th>
                                        <th>P/L</th>
                                        <th>Emotion</th>
                                    </tr>
                                </thead>
                                <tbody>
                                    <tr>
                                        <td><strong>TSLA</strong></td>
                                        <td>Breakout</td>
                                        <td><span class="trade-badge trade-long">LONG</span></td>
                                        <td>$265.34</td>
                                        <td>$272.15</td>
                                        <td style="color: var(--success);">+$681.00</td>
                                        <td><i class="fas fa-smile" style="color: var(--success);"></i> Confident</td>
                                    </tr>
                                    <tr>
                                        <td><strong>EUR/USD</strong></td>
                                        <td>Reversal</td>
                                        <td><span class="trade-badge trade-short">SHORT</span></td>
                                        <td>1.1054</td>
                                        <td>1.1021</td>
                                        <td style="color: var(--success);">+$330.00</td>
                                        <td><i class="fas fa-meh" style="color: var(--warning);"></i> Uncertain</td>
                                    </tr>
                                    <tr>
                                        <td><strong>GOLD</strong></td>
                                        <td>Trend</td>
                                        <td><span class="trade-badge trade-long">LONG</span></td>
                                        <td>$1,942</td>
                                        <td>$1,928</td>
                                        <td style="color: var(--danger);">-$420.00</td>
                                        <td><i class="fas fa-frown" style="color: var(--danger);"></i> Impulsive</td>
                                    </tr>
                                    <tr>
                                        <td><strong>BTC/USD</strong></td>
                                        <td>Scalp</td>
                                        <td><span class="trade-badge trade-long">LONG</span></td>
                                        <td>$30,422</td>
                                        <td>$30,580</td>
                                        <td style="color: var(--success);">+$158.00</td>
                                        <td><i class="fas fa-smile" style="color: var(--success);"></i> Calm</td>
                                    </tr>
                                    <tr>
                                        <td><strong>AMZN</strong></td>
                                        <td>Breakout</td>
                                        <td><span class="trade-badge trade-short">SHORT</span></td>
                                        <td>$135.80</td>
                                        <td>$136.40</td>
                                        <td style="color: var(--danger);">-$180.00</td>
                                        <td><i class="fas fa-frown" style="color: var(--danger);"></i> Frustrated</td>
                                    </tr>
                                </tbody>
                            </table>
                        </div>
                    </div>
                    
                    <!-- Performance Analytics -->
                    <div class="card">
                        <div class="card-header">
                            <div class="card-title">
                                <i class="fas fa-chart-line"></i>
                                <span>Performance Analytics</span>
                            </div>
                            <div class="card-actions">
                                <select class="btn btn-outline">
                                    <option>1 Month</option>
                                    <option selected>3 Months</option>
                                    <option>6 Months</option>
                                    <option>1 Year</option>
                                </select>
                            </div>
                        </div>
                        <div class="performance-chart">
                            <canvas id="analytics-chart"></canvas>
                        </div>
                    </div>
                    
                    <!-- Trade Replay -->
                    <div class="card">
                        <div class="card-header">
                            <div class="card-title">
                                <i class="fas fa-play-circle"></i>
                                <span>Trade Replay</span>
                            </div>
                            <div class="card-actions">
                                <button class="btn btn-outline">
                                    <i class="fas fa-random"></i> Random Trade
                                </button>
                            </div>
                        </div>
                        <div class="trade-replay">
                            <div class="replay-chart">
                                <canvas id="replay-chart"></canvas>
                            </div>
                            <div class="replay-controls">
                                <button class="btn btn-outline">
                                    <i class="fas fa-step-backward"></i>
                                </button>
                                <button class="btn btn-primary">
                                    <i class="fas fa-play"></i> Play
                                </button>
                                <button class="btn btn-outline">
                                    <i class="fas fa-step-forward"></i>
                                </button>
                            </div>
                        </div>
                    </div>
                    
                    <!-- Strategy Tester -->
                    <div class="card">
                        <div class="card-header">
                            <div class="card-title">
                                <i class="fas fa-flask"></i>
                                <span>Strategy Tester</span>
                            </div>
                            <div class="card-actions">
                                <button class="btn btn-outline">
                                    <i class="fas fa-history"></i> Backtest
                                </button>
                            </div>
                        </div>
                        <div class="simulator-container">
                            <div style="display: grid; grid-template-columns: 1fr 1fr; gap: 15px;">
                                <div class="form-group">
                                    <label>Strategy</label>
                                    <select class="btn btn-outline" style="width: 100%;">
                                        <option>Breakout Trading</option>
                                        <option>Trend Following</option>
                                        <option>Mean Reversion</option>
                                        <option>Scalping</option>
                                    </select>
                                </div>
                                <div class="form-group">
                                    <label>Timeframe</label>
                                    <select class="btn btn-outline" style="width: 100%;">
                                        <option>5 Minutes</option>
                                        <option>15 Minutes</option>
                                        <option selected>1 Hour</option>
                                        <option>4 Hours</option>
                                        <option>Daily</option>
                                    </select>
                                </div>
                            </div>
                            
                            <div class="simulator-actions">
                                <div class="sim-action-btn">
                                    <i class="fas fa-chart-line"></i>
                                    <span>Trend Analysis</span>
                                </div>
                                <div class="sim-action-btn">
                                    <i class="fas fa-bolt"></i>
                                    <span>Entry Points</span>
                                </div>
                                <div class="sim-action-btn">
                                    <i class="fas fa-signal"></i>
                                    <span>Risk Levels</span>
                                </div>
                                <div class="sim-action-btn">
                                    <i class="fas fa-arrow-up"></i>
                                    <span>Take Profit</span>
                                </div>
                                <div class="sim-action-btn">
                                    <i class="fas fa-arrow-down"></i>
                                    <span>Stop Loss</span>
                                </div>
                                <div class="sim-action-btn">
                                    <i class="fas fa-file-medical"></i>
                                    <span>Trade Report</span>
                                </div>
                            </div>
                        </div>
                    </div>
                </div>
            </div>
            
            <!-- Right Sidebar -->
            <div>
                <!-- Psychology Tracker -->
                <div class="card">
                    <div class="card-header">
                        <div class="card-title">
                            <i class="fas fa-brain"></i>
                            <span>Psychology Tracker</span>
                        </div>
                        <div class="card-actions">
                            <button class="btn btn-outline">
                                <i class="fas fa-plus"></i> Add
                            </button>
                        </div>
                    </div>
                    <div>
                        <div style="display: flex; justify-content: space-between; margin-bottom: 15px;">
                            <div>
                                <div style="font-size: 14px; color: var(--text-gray);">Current State</div>
                                <div style="font-size: 18px; color: var(--success);">Focused</div>
                            </div>
                            <div style="text-align: right;">
                                <div style="font-size: 14px; color: var(--text-gray);">Confidence</div>
                                <div style="font-size: 18px; color: var(--primary-light);">85%</div>
                            </div>
                        </div>
                        
                        <div style="margin: 20px 0;">
                            <div style="display: flex; justify-content: space-between; margin-bottom: 5px;">
                                <span>Discipline</span>
                                <span>92%</span>
                            </div>
                            <div style="height: 8px; background: rgba(100, 116, 139, 0.2); border-radius: 4px; overflow: hidden;">
                                <div style="height: 100%; width: 92%; background: var(--success);"></div>
                            </div>
                        </div>
                        
                        <div style="margin: 20px 0;">
                            <div style="display: flex; justify-content: space-between; margin-bottom: 5px;">
                                <span>Patience</span>
                                <span>78%</span>
                            </div>
                            <div style="height: 8px; background: rgba(100, 116, 139, 0.2); border-radius: 4px; overflow: hidden;">
                                <div style="height: 100%; width: 78%; background: var(--warning);"></div>
                            </div>
                        </div>
                        
                        <div style="margin: 20px 0;">
                            <div style="display: flex; justify-content: space-between; margin-bottom: 5px;">
                                <span>Emotional Control</span>
                                <span>86%</span>
                            </div>
                            <div style="height: 8px; background: rgba(100, 116, 139, 0.2); border-radius: 4px; overflow: hidden;">
                                <div style="height: 100%; width: 86%; background: var(--primary-light);"></div>
                            </div>
                        </div>
                    </div>
                </div>
                
                <!-- Market Overview -->
                <div class="card">
                    <div class="card-header">
                        <div class="card-title">
                            <i class="fas fa-globe"></i>
                            <span>Market Overview</span>
                        </div>
                        <div class="card-actions">
                            <button class="btn btn-outline">
                                <i class="fas fa-sync-alt"></i>
                            </button>
                        </div>
                    </div>
                    <div>
                        <div style="display: flex; justify-content: space-between; padding: 15px; border-bottom: 1px solid var(--card-border);">
                            <div>
                                <div><strong>NASDAQ</strong></div>
                                <div style="font-size: 14px; color: var(--text-gray);">Tech Stocks</div>
                            </div>
                            <div style="text-align: right; color: var(--success);">
                                <div>+1.42%</div>
                                <div style="font-size: 14px;">15,328.76</div>
                            </div>
                        </div>
                        
                        <div style="display: flex; justify-content: space-between; padding: 15px; border-bottom: 1px solid var(--card-border);">
                            <div>
                                <div><strong>DOW JONES</strong></div>
                                <div style="font-size: 14px; color: var(--text-gray);">Industrial</div>
                            </div>
                            <div style="text-align: right; color: var(--danger);">
                                <div>-0.28%</div>
                                <div style="font-size: 14px;">34,156.23</div>
                            </div>
                        </div>
                        
                        <div style="display: flex; justify-content: space-between; padding: 15px; border-bottom: 1px solid var(--card-border);">
                            <div>
                                <div><strong>GOLD</strong></div>
                                <div style="font-size: 14px; color: var(--text-gray);">Commodities</div>
                            </div>
                            <div style="text-align: right; color: var(--success);">
                                <div>+0.85%</div>
                                <div style="font-size: 14px;">$1,942.50</div>
                            </div>
                        </div>
                        
                        <div style="display: flex; justify-content: space-between; padding: 15px;">
                            <div>
                                <div><strong>BITCOIN</strong></div>
                                <div style="font-size: 14px; color: var(--text-gray);">Crypto</div>
                            </div>
                            <div style="text-align: right; color: var(--success);">
                                <div>+3.22%</div>
                                <div style="font-size: 14px;">$30,850.75</div>
                            </div>
                        </div>
                    </div>
                </div>
                
                <!-- Trading Goals -->
                <div class="card">
                    <div class="card-header">
                        <div class="card-title">
                            <i class="fas fa-bullseye"></i>
                            <span>Trading Goals</span>
                        </div>
                        <div class="card-actions">
                            <button class="btn btn-outline">
                                <i class="fas fa-plus"></i>
                            </button>
                        </div>
                    </div>
                    <div>
                        <div style="margin-bottom: 20px;">
                            <div style="display: flex; justify-content: space-between; margin-bottom: 5px;">
                                <span>Monthly Profit Target</span>
                                <span>$5,000 / $10,000</span>
                            </div>
                            <div style="height: 8px; background: rgba(100, 116, 139, 0.2); border-radius: 4px; overflow: hidden;">
                                <div style="height: 100%; width: 50%; background: var(--primary-light);"></div>
                            </div>
                        </div>
                        
                        <div style="margin-bottom: 20px;">
                            <div style="display: flex; justify-content: space-between; margin-bottom: 5px;">
                                <span>Win Rate Improvement</span>
                                <span>76.3% / 80%</span>
                            </div>
                            <div style="height: 8px; background: rgba(100, 116, 139, 0.2); border-radius: 4px; overflow: hidden;">
                                <div style="height: 100%; width: 95%; background: var(--success);"></div>
                            </div>
                        </div>
                        
                        <div style="margin-bottom: 20px;">
                            <div style="display: flex; justify-content: space-between; margin-bottom: 5px;">
                                <span>Risk Management</span>
                                <span>92% Compliance</span>
                            </div>
                            <div style="height: 8px; background: rgba(100, 116, 139, 0.2); border-radius: 4px; overflow: hidden;">
                                <div style="height: 100%; width: 92%; background: var(--purple);"></div>
                            </div>
                        </div>
                        
                        <div>
                            <div style="display: flex; justify-content: space-between; margin-bottom: 5px;">
                                <span>Education Hours</span>
                                <span>12h / 20h</span>
                            </div>
                            <div style="height: 8px; background: rgba(100, 116, 139, 0.2); border-radius: 4px; overflow: hidden;">
                                <div style="height: 100%; width: 60%; background: var(--warning);"></div>
                            </div>
                        </div>
                    </div>
                </div>
                
                <!-- Quick Actions -->
                <div class="card">
                    <div class="card-header">
                        <div class="card-title">
                            <i class="fas fa-bolt"></i>
                            <span>Quick Actions</span>
                        </div>
                    </div>
                    <div style="display: grid; grid-template-columns: repeat(2, 1fr); gap: 10px;">
                        <button class="btn btn-outline">
                            <i class="fas fa-file-import"></i> Import Trades
                        </button>
                        <button class="btn btn-outline">
                            <i class="fas fa-chart-pie"></i> Generate Report
                        </button>
                        <button class="btn btn-outline">
                            <i class="fas fa-video"></i> Record Video
                        </button>
                        <button class="btn btn-outline">
                            <i class="fas fa-book"></i> Journal Entry
                        </button>
                        <button class="btn btn-outline">
                            <i class="fas fa-user-friends"></i> Share Trade
                        </button>
                        <button class="btn btn-outline">
                            <i class="fas fa-graduation-cap"></i> Learn
                        </button>
                    </div>
                </div>
            </div>
        </div>
    </div>
    
    <footer>
        <p>TradeZeella Pro &copy; 2023 | The Ultimate Trading Journal System | Created by Prof Iftekhar</p>
        <p>All data is stored locally in your browser. For cloud backup, connect to Google Drive or Dropbox.</p>
    </footer>

    <script>
        // Initialize charts
        const analyticsCtx = document.getElementById('analytics-chart').getContext('2d');
        const analyticsChart = new Chart(analyticsCtx, {
            type: 'line',
            data: {
                labels: ['Jan', 'Feb', 'Mar', 'Apr', 'May', 'Jun', 'Jul'],
                datasets: [{
                    label: 'Account Balance',
                    data: [50000, 52000, 56500, 61000, 65500, 72500, 84562],
                    borderColor: '#3b82f6',
                    backgroundColor: 'rgba(59, 130, 246, 0.1)',
                    borderWidth: 3,
                    tension: 0.3,
                    fill: true
                }, {
                    label: 'Monthly Profit',
                    data: [0, 2000, 4500, 4500, 4500, 7000, 12062],
                    borderColor: '#10b981',
                    backgroundColor: 'rgba(16, 185, 129, 0.1)',
                    borderWidth: 3,
                    tension: 0.3,
                    fill: true
                }]
            },
            options: {
                responsive: true,
                maintainAspectRatio: false,
                plugins: {
                    legend: {
                        labels: {
                            color: '#f1f5f9'
                        }
                    }
                },
                scales: {
                    y: {
                        beginAtZero: true,
                        grid: {
                            color: 'rgba(100, 116, 139, 0.1)'
                        },
                        ticks: {
                            color: '#94a3b8',
                            callback: function(value) {
                                return '$' + value;
                            }
                        }
                    },
                    x: {
                        grid: {
                            display: false
                        },
                        ticks: {
                            color: '#94a3b8'
                        }
                    }
                }
            }
        });
        
        const replayCtx = document.getElementById('replay-chart').getContext('2d');
        const replayChart = new Chart(replayCtx, {
            type: 'line',
            data: {
                labels: ['09:30', '10:00', '10:30', '11:00', '11:30', '12:00', '12:30'],
                datasets: [{
                    label: 'Price',
                    data: [265, 267, 269, 268, 270, 272, 271],
                    borderColor: '#3b82f6',
                    borderWidth: 2,
                    tension: 0.3,
                    fill: false
                }]
            },
            options: {
                responsive: true,
                maintainAspectRatio: false,
                plugins: {
                    legend: {
                        display: false
                    }
                },
                scales: {
                    y: {
                        grid: {
                            color: 'rgba(100, 116, 139, 0.1)'
                        },
                        ticks: {
                            color: '#94a3b8'
                        }
                    },
                    x: {
                        grid: {
                            display: false
                        },
                        ticks: {
                            color: '#94a3b8'
                        }
                    }
                }
            }
        });
        
        // Animate stats on page load
        document.querySelectorAll('.stat-card').forEach((card, index) => {
            setTimeout(() => {
                card.style.transform = 'translateY(0)';
                card.style.opacity = '1';
            }, 300 + (index * 100));
        });
        
        // Add hover effect to trade rows
        document.querySelectorAll('.trades-table tr').forEach(row => {
            row.addEventListener('mouseenter', () => {
                row.style.backgroundColor = 'rgba(59, 130, 246, 0.05)';
            });
            row.addEventListener('mouseleave', () => {
                row.style.backgroundColor = '';
            });
        });
        
        // Simulate market data updates
        setInterval(() => {
            const marketItems = document.querySelectorAll('.card:last-child > div > div');
            marketItems.forEach(item => {
                const changeElement = item.querySelector('div:last-child > div:first-child');
                const valueElement = item.querySelector('div:last-child > div:last-child');
                
                // Simulate small market fluctuations
                const change = (Math.random() - 0.5) * 0.2;
                const currentValue = parseFloat(valueElement.textContent.replace(/[^\d.]/g, ''));
                const newValue = currentValue * (1 + change/100);
                
                // Determine color based on change direction
                const color = change >= 0 ? 'var(--success)' : 'var(--danger)';
                const sign = change >= 0 ? '+' : '';
                
                // Update values
                changeElement.textContent = `${sign}${change.toFixed(2)}%`;
                changeElement.style.color = color;
                valueElement.textContent = newValue.toLocaleString('en-US', {
                    style: 'currency',
                    currency: 'USD',
                    minimumFractionDigits: valueElement.textContent.includes('.') ? 2 : 0
                });
            });
        }, 5000);
    </script>
</body>
</html>

