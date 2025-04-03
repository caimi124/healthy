<!DOCTYPE html>
<html lang="zh-CN">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>健康导航 | 您的全方位健康资源指南</title>
    <style>
        :root {
            --primary-color: #4a89dc;
            --secondary-color: #3bafda;
            --accent-color: #37bc9b;
            --light-color: #f5f7fa;
            --dark-color: #333;
            --gray-color: #e6e9ed;
            --font-main: 'Helvetica Neue', Arial, 'PingFang SC', 'Microsoft YaHei', sans-serif;
        }
        
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
        }
        
        body {
            font-family: var(--font-main);
            line-height: 1.6;
            color: var(--dark-color);
            background-color: #f9fbfd;
        }
        
        .container {
            max-width: 1200px;
            margin: 0 auto;
            padding: 0 20px;
        }
        
        header {
            background: linear-gradient(135deg, var(--primary-color), var(--secondary-color));
            color: white;
            padding: 2rem 0;
            text-align: center;
            box-shadow: 0 2px 10px rgba(0,0,0,0.1);
        }
        
        .logo {
            font-size: 2.5rem;
            font-weight: 300;
            margin-bottom: 0.5rem;
        }
        
        .tagline {
            font-size: 1.2rem;
            opacity: 0.9;
            margin-bottom: 1.5rem;
        }
        
        .search-box {
            max-width: 600px;
            margin: 0 auto;
        }
        
        .search-box input {
            width: 100%;
            padding: 12px 20px;
            border: none;
            border-radius: 30px;
            font-size: 1rem;
            box-shadow: 0 2px 15px rgba(0,0,0,0.1);
        }
        
        .search-box input:focus {
            outline: none;
        }
        
        .main-nav {
            background-color: white;
            box-shadow: 0 2px 5px rgba(0,0,0,0.05);
            position: sticky;
            top: 0;
            z-index: 100;
        }
        
        .nav-container {
            display: flex;
            justify-content: center;
            flex-wrap: wrap;
        }
        
        .nav-item {
            padding: 15px 20px;
            cursor: pointer;
            font-weight: 500;
            color: var(--dark-color);
            transition: all 0.3s ease;
            position: relative;
        }
        
        .nav-item:hover {
            color: var(--primary-color);
        }
        
        .nav-item.active {
            color: var(--primary-color);
        }
        
        .nav-item.active:after {
            content: '';
            position: absolute;
            bottom: 0;
            left: 20px;
            right: 20px;
            height: 3px;
            background-color: var(--primary-color);
        }
        
        .content-section {
            padding: 3rem 0;
        }
        
        .section-title {
            text-align: center;
            margin-bottom: 2rem;
            color: var(--primary-color);
            position: relative;
        }
        
        .section-title:after {
            content: '';
            display: block;
            width: 60px;
            height: 3px;
            background-color: var(--accent-color);
            margin: 10px auto;
        }
        
        .category-grid {
            display: grid;
            grid-template-columns: repeat(auto-fill, minmax(300px, 1fr));
            gap: 20px;
            margin-bottom: 3rem;
        }
        
        .category-card {
            background-color: white;
            border-radius: 8px;
            overflow: hidden;
            box-shadow: 0 3px 15px rgba(0,0,0,0.05);
            transition: transform 0.3s ease, box-shadow 0.3s ease;
        }
        
        .category-card:hover {
            transform: translateY(-5px);
            box-shadow: 0 10px 25px rgba(0,0,0,0.1);
        }
        
        .category-header {
            background: linear-gradient(135deg, var(--secondary-color), var(--accent-color));
            color: white;
            padding: 15px 20px;
            font-size: 1.2rem;
            font-weight: 500;
        }
        
        .category-links {
            padding: 15px;
        }
        
        .category-link {
            display: block;
            padding: 8px 0;
            color: var(--dark-color);
            text-decoration: none;
            transition: color 0.3s ease;
            position: relative;
            padding-left: 20px;
        }
        
        .category-link:before {
            content: '•';
            position: absolute;
            left: 0;
            color: var(--accent-color);
        }
        
        .category-link:hover {
            color: var(--primary-color);
        }
        
        .featured-section {
            background-color: white;
            padding: 2rem;
            border-radius: 8px;
            box-shadow: 0 3px 15px rgba(0,0,0,0.05);
            margin-bottom: 3rem;
        }
        
        .featured-title {
            color: var(--primary-color);
            margin-bottom: 1.5rem;
            text-align: center;
        }
        
        .featured-grid {
            display: grid;
            grid-template-columns: repeat(3, 1fr);
            gap: 20px;
            margin-bottom: 20px;
        }
        
        .bmi-calculator,
        .symptom-checker,
        .depression-test {
            background-color: white;
            padding: 20px;
            border-radius: 8px;
            box-shadow: 0 3px 15px rgba(0,0,0,0.05);
            height: 600px;
            overflow-y: auto;
            scrollbar-width: thin;
            scrollbar-color: var(--accent-color) var(--light-color);
        }
        
        .bmi-calculator::-webkit-scrollbar,
        .symptom-checker::-webkit-scrollbar,
        .depression-test::-webkit-scrollbar {
            width: 6px;
        }
        
        .bmi-calculator::-webkit-scrollbar-track,
        .symptom-checker::-webkit-scrollbar-track,
        .depression-test::-webkit-scrollbar-track {
            background: var(--light-color);
            border-radius: 3px;
        }
        
        .bmi-calculator::-webkit-scrollbar-thumb,
        .symptom-checker::-webkit-scrollbar-thumb,
        .depression-test::-webkit-scrollbar-thumb {
            background-color: var(--accent-color);
            border-radius: 3px;
        }
        
        .bmi-calculator::-webkit-scrollbar-thumb:hover,
        .symptom-checker::-webkit-scrollbar-thumb:hover,
        .depression-test::-webkit-scrollbar-thumb:hover {
            background-color: #2da58a;
        }
        
        .bmi-title,
        .symptom-title,
        .test-title {
            color: var(--primary-color);
            margin-bottom: 20px;
            text-align: center;
            font-size: 1.2rem;
            position: sticky;
            top: 0;
            background-color: white;
            padding: 10px 0;
            z-index: 1;
        }
        
        .bmi-calculator {
            background-color: white;
            padding: 20px;
            border-radius: 8px;
            box-shadow: 0 3px 15px rgba(0,0,0,0.05);
            margin-bottom: 20px;
        }
        
        .bmi-title {
            color: var(--primary-color);
            margin-bottom: 15px;
            text-align: center;
        }
        
        .input-group {
            margin-bottom: 15px;
        }
        
        .input-group label {
            display: block;
            margin-bottom: 5px;
            font-weight: 500;
        }
        
        .input-group input {
            width: 100%;
            padding: 10px;
            border: 1px solid var(--gray-color);
            border-radius: 4px;
            font-size: 1rem;
        }
        
        .calculate-btn {
            background-color: var(--accent-color);
            color: white;
            border: none;
            padding: 10px 15px;
            border-radius: 4px;
            cursor: pointer;
            width: 100%;
            font-size: 1rem;
            transition: background-color 0.3s;
        }
        
        .calculate-btn:hover {
            background-color: #2da58a;
        }
        
        .result-container {
            margin-top: 20px;
            padding: 15px;
            background-color: var(--light-color);
            border-radius: 8px;
            display: none;
        }
        
        .result-title {
            font-weight: 500;
            margin-bottom: 10px;
            color: var(--primary-color);
        }
        
        .bmi-value {
            font-size: 1.5rem;
            font-weight: bold;
            margin: 10px 0;
        }
        
        .bmi-category {
            font-weight: 500;
            margin-bottom: 10px;
        }
        
        .bmi-advice {
            font-size: 0.95rem;
            line-height: 1.5;
        }
        
        /* 症状自检工具样式 */
        .symptom-checker {
            background-color: white;
            padding: 20px;
            border-radius: 8px;
            box-shadow: 0 3px 15px rgba(0,0,0,0.05);
            margin-bottom: 20px;
        }
        
        .symptom-title {
            color: var(--primary-color);
            margin-bottom: 20px;
            text-align: center;
        }
        
        .step {
            display: none;
            margin-bottom: 20px;
        }
        
        .step.active {
            display: block;
        }
        
        .step-title {
            font-weight: 500;
            margin-bottom: 15px;
            color: var(--dark-color);
            font-size: 1.1rem;
        }
        
        .symptom-options {
            display: grid;
            grid-template-columns: repeat(auto-fill, minmax(150px, 1fr));
            gap: 10px;
            margin-bottom: 15px;
        }
        
        .symptom-option {
            padding: 10px;
            border: 1px solid var(--gray-color);
            border-radius: 4px;
            text-align: center;
            cursor: pointer;
            transition: all 0.3s;
        }
        
        .symptom-option:hover {
            background-color: var(--light-color);
        }
        
        .symptom-option.selected {
            background-color: var(--primary-color);
            color: white;
            border-color: var(--primary-color);
        }
        
        .additional-info {
            margin-top: 15px;
        }
        
        .additional-info label {
            display: block;
            margin-bottom: 5px;
            font-weight: 500;
        }
        
        .additional-info select,
        .additional-info textarea {
            width: 100%;
            padding: 10px;
            border: 1px solid var(--gray-color);
            border-radius: 4px;
            margin-bottom: 15px;
        }
        
        .additional-info textarea {
            min-height: 80px;
            resize: vertical;
        }
        
        .nav-buttons {
            display: flex;
            justify-content: space-between;
            margin-top: 20px;
        }
        
        .nav-btn {
            padding: 10px 20px;
            border: none;
            border-radius: 4px;
            cursor: pointer;
            font-size: 1rem;
            transition: background-color 0.3s;
        }
        
        .prev-btn {
            background-color: var(--gray-color);
        }
        
        .next-btn {
            background-color: var(--accent-color);
            color: white;
        }
        
        .result-step {
            padding: 15px;
            background-color: var(--light-color);
            border-radius: 8px;
        }
        
        .result-title {
            font-weight: 500;
            margin-bottom: 10px;
            color: var(--primary-color);
        }
        
        .possible-conditions {
            margin: 15px 0;
        }
        
        .condition-item {
            margin-bottom: 10px;
            padding-left: 20px;
            position: relative;
        }
        
        .condition-item:before {
            content: '•';
            position: absolute;
            left: 5px;
            color: var(--accent-color);
        }
        
        .advice-section {
            margin-top: 20px;
        }
        
        .advice-title {
            font-weight: 500;
            margin-bottom: 10px;
        }
        
        .severity-indicator {
            display: inline-block;
            padding: 3px 8px;
            border-radius: 4px;
            font-size: 0.9rem;
            margin-bottom: 10px;
        }
        
        .low-severity {
            background-color: #a0d468;
            color: white;
        }
        
        .medium-severity {
            background-color: #ffce54;
            color: #333;
        }
        
        .high-severity {
            background-color: #ed5565;
            color: white;
        }
        
        footer {
            background-color: var(--dark-color);
            color: white;
            padding: 2rem 0;
            text-align: center;
        }
        
        .footer-links {
            display: flex;
            justify-content: center;
            flex-wrap: wrap;
            margin-bottom: 1rem;
        }
        
        .footer-link {
            color: white;
            margin: 0 15px;
            text-decoration: none;
            opacity: 0.8;
            transition: opacity 0.3s ease;
        }
        
        .footer-link:hover {
            opacity: 1;
        }
        
        .copyright {
            opacity: 0.6;
            font-size: 0.9rem;
        }
        
        @media (max-width: 1200px) {
            .featured-grid {
                grid-template-columns: 1fr;
            }
            
            .bmi-calculator,
            .symptom-checker,
            .depression-test {
                height: 500px;
            }
        }
        
        @media (max-width: 768px) {
            .bmi-calculator,
            .symptom-checker,
            .depression-test {
                height: 400px;
                padding: 15px;
            }
            
            .category-grid {
                grid-template-columns: 1fr;
            }
            
            .nav-container {
                flex-direction: column;
                align-items: center;
            }
            
            .nav-item {
                padding: 10px;
            }
        }
        
        /* 抑郁症测试样式 */
        .depression-test {
            background-color: white;
            padding: 20px;
            border-radius: 8px;
            box-shadow: 0 3px 15px rgba(0,0,0,0.05);
            margin-bottom: 20px;
        }
        
        .test-title {
            color: var(--primary-color);
            margin-bottom: 20px;
            text-align: center;
        }
        
        .test-question {
            margin-bottom: 20px;
            padding-bottom: 15px;
            border-bottom: 1px solid var(--gray-color);
        }
        
        .question-text {
            font-weight: 500;
            margin-bottom: 10px;
        }
        
        .option-group {
            display: flex;
            flex-direction: column;
            gap: 8px;
        }
        
        .option-label {
            display: flex;
            align-items: center;
            padding: 8px 10px;
            border-radius: 4px;
            cursor: pointer;
            transition: background-color 0.3s;
        }
        
        .option-label:hover {
            background-color: var(--light-color);
        }
        
        .option-input {
            margin-right: 10px;
        }
        
        .test-nav {
            display: flex;
            justify-content: space-between;
            margin-top: 20px;
        }
        
        .test-btn {
            padding: 10px 20px;
            border: none;
            border-radius: 4px;
            cursor: pointer;
            font-size: 1rem;
            transition: background-color 0.3s;
        }
        
        .submit-btn {
            background-color: var(--accent-color);
            color: white;
        }
        
        .submit-btn:hover {
            background-color: #2da58a;
        }
        
        .result-container {
            padding: 20px;
            background-color: var(--light-color);
            border-radius: 8px;
            margin-top: 20px;
            display: none;
        }
        
        .result-title {
            font-weight: 500;
            margin-bottom: 15px;
            color: var(--primary-color);
            text-align: center;
        }
        
        .score-display {
            font-size: 1.5rem;
            font-weight: bold;
            text-align: center;
            margin: 15px 0;
        }
        
        .severity-level {
            display: inline-block;
            padding: 5px 15px;
            border-radius: 20px;
            font-weight: 500;
            margin-bottom: 15px;
        }
        
        .minimal {
            background-color: #a0d468;
            color: white;
        }
        
        .mild {
            background-color: #48cfad;
            color: white;
        }
        
        .moderate {
            background-color: #ffce54;
            color: #333;
        }
        
        .moderately-severe {
            background-color: #fc6e51;
            color: white;
        }
        
        .severe {
            background-color: #ed5565;
            color: white;
        }
        
        .advice-section {
            margin-top: 20px;
        }
        
        .advice-title {
            font-weight: 500;
            margin-bottom: 10px;
        }
        
        .advice-list {
            padding-left: 20px;
        }
        
        .advice-item {
            margin-bottom: 8px;
            position: relative;
        }
        
        .advice-item:before {
            content: '•';
            position: absolute;
            left: -15px;
            color: var(--accent-color);
        }
        
        .disclaimer {
            font-size: 0.8rem;
            color: #666;
            margin-top: 20px;
            text-align: center;
        }
        
        @media (max-width: 768px) {
            .depression-test {
                padding: 15px;
            }
            
            .test-question {
                margin-bottom: 15px;
                padding-bottom: 10px;
            }
        }
    </style>
</head>
<body>
    <header>
        <div class="container">
            <h1 class="logo">健康导航</h1>
            <p class="tagline">一站式健康资源与工具集合</p>
            <div class="search-box">
                <input type="text" placeholder="搜索健康资源、工具或资讯...">
            </div>
        </div>
    </header>
    
    <nav class="main-nav">
        <div class="container">
            <div class="nav-container">
                <div class="nav-item active">首页</div>
                <div class="nav-item">传统医学</div>
                <div class="nav-item">母婴健康</div>
                <div class="nav-item">营养饮食</div>
                <div class="nav-item">心理健康</div>
                <div class="nav-item">慢性病管理</div>
                <div class="nav-item">运动健康</div>
                <div class="nav-item">医疗信息</div>
            </div>
        </div>
    </nav>
    
    <main class="container">
        <section class="content-section">
            <h2 class="section-title">热门健康资源</h2>
            
            <div class="featured-section">
                <h3 class="featured-title">推荐工具与平台</h3>
                <div class="featured-grid">
                    <!-- BMI计算器卡片 -->
                    <div class="bmi-calculator">
                        <h3 class="bmi-title">BMI健康计算器</h3>
                        <div class="input-group">
                            <label for="height">身高 (cm)</label>
                            <input type="number" id="height" placeholder="请输入您的身高">
                        </div>
                        <div class="input-group">
                            <label for="weight">体重 (kg)</label>
                            <input type="number" id="weight" placeholder="请输入您的体重">
                        </div>
                        <button class="calculate-btn" id="calculate">计算BMI</button>
                        <div class="result-container" id="result">
                            <div class="result-title">您的BMI结果</div>
                            <div class="bmi-value" id="bmi-value">--</div>
                            <div class="bmi-category" id="bmi-category"></div>
                            <div class="bmi-advice" id="bmi-advice"></div>
                        </div>
                    </div>
                    
                    <!-- 症状自检工具 -->
                    <div class="symptom-checker">
                        <h3 class="symptom-title">症状自检工具</h3>
                        
                        <!-- 步骤1: 选择身体部位 -->
                        <div class="step active" id="step1">
                            <div class="step-title">1. 请选择不适的身体部位</div>
                            <div class="symptom-options">
                                <div class="symptom-option" data-value="head">头部</div>
                                <div class="symptom-option" data-value="chest">胸部</div>
                                <div class="symptom-option" data-value="abdomen">腹部</div>
                                <div class="symptom-option" data-value="back">背部</div>
                                <div class="symptom-option" data-value="limbs">四肢</div>
                                <div class="symptom-option" data-value="skin">皮肤</div>
                                <div class="symptom-option" data-value="eyes">眼睛</div>
                                <div class="symptom-option" data-value="ears">耳朵</div>
                                <div class="symptom-option" data-value="nose">鼻子</div>
                                <div class="symptom-option" data-value="throat">咽喉</div>
                                <div class="symptom-option" data-value="urinary">泌尿系统</div>
                                <div class="symptom-option" data-value="general">全身症状</div>
                            </div>
                            <div class="nav-buttons">
                                <button class="nav-btn prev-btn" disabled>上一步</button>
                                <button class="nav-btn next-btn" id="next1">下一步</button>
                            </div>
                        </div>
                        
                        <!-- 步骤2: 选择具体症状 -->
                        <div class="step" id="step2">
                            <div class="step-title">2. 请选择您的具体症状</div>
                            <div class="symptom-options" id="specific-symptoms">
                                <!-- 这里会通过JavaScript动态加载症状选项 -->
                            </div>
                            <div class="nav-buttons">
                                <button class="nav-btn prev-btn" id="prev2">上一步</button>
                                <button class="nav-btn next-btn" id="next2">下一步</button>
                            </div>
                        </div>
                        
                        <!-- 步骤3: 补充信息 -->
                        <div class="step" id="step3">
                            <div class="step-title">3. 请补充更多信息</div>
                            <div class="additional-info">
                                <label for="duration">症状持续时间:</label>
                                <select id="duration" class="additional-input">
                                    <option value="less-than-day">少于1天</option>
                                    <option value="1-3-days">1-3天</option>
                                    <option value="4-7-days">4-7天</option>
                                    <option value="1-2-weeks">1-2周</option>
                                    <option value="more-than-2-weeks">超过2周</option>
                                </select>
                                
                                <label for="severity">症状严重程度:</label>
                                <select id="severity" class="additional-input">
                                    <option value="mild">轻微 - 不影响日常生活</option>
                                    <option value="moderate">中等 - 影响部分日常活动</option>
                                    <option value="severe">严重 - 无法进行日常活动</option>
                                </select>
                                
                                <label for="other-symptoms">其他伴随症状:</label>
                                <textarea id="other-symptoms" placeholder="请描述您同时出现的其他症状..."></textarea>
                            </div>
                            <div class="nav-buttons">
                                <button class="nav-btn prev-btn" id="prev3">上一步</button>
                                <button class="nav-btn next-btn" id="next3">查看结果</button>
                            </div>
                        </div>
                        
                        <!-- 步骤4: 结果显示 -->
                        <div class="step" id="step4">
                            <div class="result-step">
                                <div class="result-title">您的症状评估结果</div>
                                
                                <div id="severity-indicator" class="severity-indicator low-severity">低风险</div>
                                
                                <div class="possible-conditions">
                                    <div class="step-title">可能的健康问题:</div>
                                    <div id="possible-conditions-list">
                                        <!-- 这里会显示可能的疾病 -->
                                    </div>
                                </div>
                                
                                <div class="advice-section">
                                    <div class="advice-title">建议:</div>
                                    <div id="advice-content">
                                        <!-- 这里会显示建议 -->
                                    </div>
                                </div>
                            </div>
                            <div class="nav-buttons">
                                <button class="nav-btn prev-btn" id="prev4">返回修改</button>
                                <button class="nav-btn next-btn" id="restart">重新开始</button>
                            </div>
                        </div>
                    </div>
                    
                    <!-- 抑郁症自评工具 -->
                    <div class="depression-test">
                        <h3 class="test-title">抑郁症自评量表(PHQ-9)</h3>
                        
                        <form id="depressionTestForm">
                            <div class="test-question">
                                <div class="question-text">1. 做事时提不起劲或没有兴趣</div>
                                <div class="option-group">
                                    <label class="option-label">
                                        <input type="radio" name="q1" value="0" class="option-input"> 完全没有 (0分)
                                    </label>
                                    <label class="option-label">
                                        <input type="radio" name="q1" value="1" class="option-input"> 有几天 (1分)
                                    </label>
                                    <label class="option-label">
                                        <input type="radio" name="q1" value="2" class="option-input"> 一半以上时间 (2分)
                                    </label>
                                    <label class="option-label">
                                        <input type="radio" name="q1" value="3" class="option-input"> 几乎每天 (3分)
                                    </label>
                                </div>
                            </div>
                            
                            <div class="test-question">
                                <div class="question-text">2. 感到心情低落、沮丧或绝望</div>
                                <div class="option-group">
                                    <label class="option-label">
                                        <input type="radio" name="q2" value="0" class="option-input"> 完全没有 (0分)
                                    </label>
                                    <label class="option-label">
                                        <input type="radio" name="q2" value="1" class="option-input"> 有几天 (1分)
                                    </label>
                                    <label class="option-label">
                                        <input type="radio" name="q2" value="2" class="option-input"> 一半以上时间 (2分)
                                    </label>
                                    <label class="option-label">
                                        <input type="radio" name="q2" value="3" class="option-input"> 几乎每天 (3分)
                                    </label>
                                </div>
                            </div>
                            
                            <div class="test-question">
                                <div class="question-text">3. 入睡困难、睡不安稳或睡眠过多</div>
                                <div class="option-group">
                                    <label class="option-label">
                                        <input type="radio" name="q3" value="0" class="option-input"> 完全没有 (0分)
                                    </label>
                                    <label class="option-label">
                                        <input type="radio" name="q3" value="1" class="option-input"> 有几天 (1分)
                                    </label>
                                    <label class="option-label">
                                        <input type="radio" name="q3" value="2" class="option-input"> 一半以上时间 (2分)
                                    </label>
                                    <label class="option-label">
                                        <input type="radio" name="q3" value="3" class="option-input"> 几乎每天 (3分)
                                    </label>
                                </div>
                            </div>
                            
                            <div class="test-question">
                                <div class="question-text">4. 感觉疲倦或没有活力</div>
                                <div class="option-group">
                                    <label class="option-label">
                                        <input type="radio" name="q4" value="0" class="option-input"> 完全没有 (0分)
                                    </label>
                                    <label class="option-label">
                                        <input type="radio" name="q4" value="1" class="option-input"> 有几天 (1分)
                                    </label>
                                    <label class="option-label">
                                        <input type="radio" name="q4" value="2" class="option-input"> 一半以上时间 (2分)
                                    </label>
                                    <label class="option-label">
                                        <input type="radio" name="q4" value="3" class="option-input"> 几乎每天 (3分)
                                    </label>
                                </div>
                            </div>
                            
                            <div class="test-question">
                                <div class="question-text">5. 食欲不振或吃太多</div>
                                <div class="option-group">
                                    <label class="option-label">
                                        <input type="radio" name="q5" value="0" class="option-input"> 完全没有 (0分)
                                    </label>
                                    <label class="option-label">
                                        <input type="radio" name="q5" value="1" class="option-input"> 有几天 (1分)
                                    </label>
                                    <label class="option-label">
                                        <input type="radio" name="q5" value="2" class="option-input"> 一半以上时间 (2分)
                                    </label>
                                    <label class="option-label">
                                        <input type="radio" name="q5" value="3" class="option-input"> 几乎每天 (3分)
                                    </label>
                                </div>
                            </div>
                            
                            <div class="test-question">
                                <div class="question-text">6. 觉得自己很糟或觉得自己很失败，或让自己和家人失望</div>
                                <div class="option-group">
                                    <label class="option-label">
                                        <input type="radio" name="q6" value="0" class="option-input"> 完全没有 (0分)
                                    </label>
                                    <label class="option-label">
                                        <input type="radio" name="q6" value="1" class="option-input"> 有几天 (1分)
                                    </label>
                                    <label class="option-label">
                                        <input type="radio" name="q6" value="2" class="option-input"> 一半以上时间 (2分)
                                    </label>
                                    <label class="option-label">
                                        <input type="radio" name="q6" value="3" class="option-input"> 几乎每天 (3分)
                                    </label>
                                </div>
                            </div>
                            
                            <div class="test-question">
                                <div class="question-text">7. 对事物专注有困难，例如阅读报纸或看电视时</div>
                                <div class="option-group">
                                    <label class="option-label">
                                        <input type="radio" name="q7" value="0" class="option-input"> 完全没有 (0分)
                                    </label>
                                    <label class="option-label">
                                        <input type="radio" name="q7" value="1" class="option-input"> 有几天 (1分)
                                    </label>
                                    <label class="option-label">
                                        <input type="radio" name="q7" value="2" class="option-input"> 一半以上时间 (2分)
                                    </label>
                                    <label class="option-label">
                                        <input type="radio" name="q7" value="3" class="option-input"> 几乎每天 (3分)
                                    </label>
                                </div>
                            </div>
                            
                            <div class="test-question">
                                <div class="question-text">8. 动作或说话速度缓慢到别人已经察觉，或正好相反 - 烦躁或坐立不安、动来动去的情况更胜于平常</div>
                                <div class="option-group">
                                    <label class="option-label">
                                        <input type="radio" name="q8" value="0" class="option-input"> 完全没有 (0分)
                                    </label>
                                    <label class="option-label">
                                        <input type="radio" name="q8" value="1" class="option-input"> 有几天 (1分)
                                    </label>
                                    <label class="option-label">
                                        <input type="radio" name="q8" value="2" class="option-input"> 一半以上时间 (2分)
                                    </label>
                                    <label class="option-label">
                                        <input type="radio" name="q8" value="3" class="option-input"> 几乎每天 (3分)
                                    </label>
                                </div>
                            </div>
                            
                            <div class="test-question">
                                <div class="question-text">9. 有不如死掉或用某种方式伤害自己的念头</div>
                                <div class="option-group">
                                    <label class="option-label">
                                        <input type="radio" name="q9" value="0" class="option-input"> 完全没有 (0分)
                                    </label>
                                    <label class="option-label">
                                        <input type="radio" name="q9" value="1" class="option-input"> 有几天 (1分)
                                    </label>
                                    <label class="option-label">
                                        <input type="radio" name="q9" value="2" class="option-input"> 一半以上时间 (2分)
                                    </label>
                                    <label class="option-label">
                                        <input type="radio" name="q9" value="3" class="option-input"> 几乎每天 (3分)
                                    </label>
                                </div>
                            </div>
                            
                            <div class="test-nav">
                                <button type="submit" class="test-btn submit-btn">提交评估</button>
                            </div>
                        </form>
                        
                        <div class="result-container" id="depressionResult">
                            <div class="result-title">您的抑郁程度评估</div>
                            <div class="score-display">总分: <span id="testScore">0</span>/27</div>
                            <div class="severity-level" id="severityLevel">无抑郁</div>
                            
                            <div class="advice-section">
                                <div class="advice-title">建议:</div>
                                <div class="advice-list" id="adviceList">
                                    <!-- 建议将在这里动态生成 -->
                                </div>
                            </div>
                            
                            <p class="disclaimer">
                                注意: 此测试仅供参考，不能作为专业诊断依据。如有需要，请咨询心理健康专业人士。
                            </p>
                        </div>
                    </div>
                </div>
            </div>
            
            <h2 class="section-title">健康资源分类</h2>
            
            <div class="category-grid">
                <div class="category-card">
                    <div class="category-header">传统医学与替代疗法</div>
                    <div class="category-links">
                        <a href="http://www.satcm.gov.cn" class="category-link" target="_blank">国家中医药管理局官网</a>
                        <a href="https://www.zysj.com.cn" class="category-link" target="_blank">中医世家</a>
                        <a href="https://zhongyi.39.net" class="category-link" target="_blank">39中医频道</a>
                        <a href="http://www.wfas.org.cn" class="category-link" target="_blank">世界针灸学会联合会</a>
                        <a href="https://www.nccih.nih.gov" class="category-link" target="_blank">美国国家补充医学中心</a>
                    </div>
                </div>
                
                <div class="category-card">
                    <div class="category-header">母婴健康</div>
                    <div class="category-links">
                        <a href="https://www.babytree.com" class="category-link" target="_blank">宝宝树</a>
                        <a href="https://www.whattoexpect.com" class="category-link" target="_blank">What to Expect</a>
                        <a href="https://www.healthychildren.org" class="category-link" target="_blank">美国儿科学会</a>
                        <a href="https://www.llli.org" class="category-link" target="_blank">国际母乳会</a>
                        <a href="https://www.ci123.com" class="category-link" target="_blank">育儿网</a>
                    </div>
                </div>
                
                <div class="category-card">
                    <div class="category-header">营养与饮食</div>
                    <div class="category-links">
                        <a href="http://www.cnsoc.org" class="category-link" target="_blank">中国营养学会</a>
                        <a href="https://www.eatright.org" class="category-link" target="_blank">美国营养师协会</a>
                        <a href="https://www.ruled.me" class="category-link" target="_blank">生酮饮食资源库</a>
                        <a href="https://www.vegsoc.org" class="category-link" target="_blank">素食者协会</a>
                        <a href="https://www.calculator.net/health-fitness-calculator.html" class="category-link" target="_blank">健康计算器</a>
                    </div>
                </div>
                
                <div class="category-card">
                    <div class="category-header">心理健康</div>
                    <div class="category-links">
                        <a href="https://www.jiandanxinli.com" class="category-link" target="_blank">简单心理</a>
                        <a href="https://www.psychologytoday.com" class="category-link" target="_blank">Psychology Today</a>
                        <a href="https://www.headspace.com" class="category-link" target="_blank">Headspace冥想</a>
                        <a href="https://tide.fm" class="category-link" target="_blank">潮汐APP官网</a>
                        <a href="https://peterattiamd.com/podcast" class="category-link" target="_blank">健康播客</a>
                    </div>
                </div>
                
                <div class="category-card">
                    <div class="category-header">慢性病管理</div>
                    <div class="category-links">
                        <a href="https://www.idf.org" class="category-link" target="_blank">国际糖尿病联盟</a>
                        <a href="https://www.tnbz.com" class="category-link" target="_blank">甜蜜家园论坛</a>
                        <a href="https://www.heart.org" class="category-link" target="_blank">美国心脏协会</a>
                        <a href="https://www.alz.org" class="category-link" target="_blank">阿尔茨海默病协会</a>
                        <a href="http://www.chard.org.cn" class="category-link" target="_blank">中国罕见病联盟</a>
                    </div>
                </div>
                
                <div class="category-card">
                    <div class="category-header">运动健康</div>
                    <div class="category-links">
                        <a href="https://www.gotokeep.com" class="category-link" target="_blank">Keep官网</a>
                        <a href="https://www.acefitness.org" class="category-link" target="_blank">美国运动委员会</a>
                        <a href="https://www.physio-pedia.com" class="category-link" target="_blank">骨科康复库</a>
                        <a href="https://ergo-plus.com" class="category-link" target="_blank">办公人体工学</a>
                        <a href="https://aasm.org" class="category-link" target="_blank">美国睡眠医学会</a>
                    </div>
                </div>
                
                <div class="category-card">
                    <div class="category-header">医疗信息权威平台</div>
                    <div class="category-links">
                        <a href="https://www.who.int" class="category-link" target="_blank">世界卫生组织</a>
                        <a href="https://www.msdmanuals.com" class="category-link" target="_blank">默克手册</a>
                        <a href="https://www.drugs.com" class="category-link" target="_blank">用药助手</a>
                        <a href="http://nmpa.gov.cn" class="category-link" target="_blank">国家药品监督管理局</a>
                        <a href="https://pubmed.ncbi.nlm.nih.gov" class="category-link" target="_blank">PubMed医学文献</a>
                    </div>
                </div>
                
                <div class="category-card">
                    <div class="category-header">健康科技与工具</div>
                    <div class="category-links">
                        <a href="https://www.apple.com/researchkit" class="category-link" target="_blank">苹果健康研究平台</a>
                        <a href="https://www.23andme.com" class="category-link" target="_blank">23andMe基因检测</a>
                        <a href="https://www.mayoclinic.org/symptom-checker" class="category-link" target="_blank">梅奥症状检查器</a>
                        <a href="https://www.imicams.ac.cn/dict" class="category-link" target="_blank">医学术语词典</a>
                        <a href="https://aqicn.org" class="category-link" target="_blank">全球空气质量地图</a>
                    </div>
                </div>
            </div>
        </section>
    </main>
    
    <footer>
        <div class="container">
            <div class="footer-links">
                <a href="#" class="footer-link">关于我们</a>
                <a href="#" class="footer-link">隐私政策</a>
                <a href="#" class="footer-link">使用条款</a>
                <a href="#" class="footer-link">联系我们</a>
            </div>
            <p class="copyright">© 2023 健康导航 - 您的健康资源指南 | 所有内容仅供参考，不构成医疗建议</p>
        </div>
    </footer>
    
    <script>
        // 症状数据库
        const symptomDatabase = {
            head: [
                { name: "头痛", conditions: ["紧张性头痛", "偏头痛", "鼻窦炎", "高血压"], severity: "medium" },
                { name: "头晕", conditions: ["低血压", "贫血", "内耳问题", "脱水"], severity: "medium" },
                { name: "头皮发痒", conditions: ["头皮屑", "脂溢性皮炎", "银屑病", "过敏反应"], severity: "low" }
            ],
            chest: [
                { name: "胸痛", conditions: ["心绞痛", "胃食管反流", "肌肉拉伤", "焦虑症"], severity: "high" },
                { name: "胸闷", conditions: ["哮喘", "慢性阻塞性肺病", "焦虑发作", "心脏病"], severity: "high" },
                { name: "心悸", conditions: ["心律失常", "焦虑症", "甲状腺功能亢进", "咖啡因过量"], severity: "medium" }
            ],
            abdomen: [
                { name: "腹痛", conditions: ["胃炎", "肠易激综合征", "阑尾炎", "食物中毒"], severity: "medium" },
                { name: "腹泻", conditions: ["肠胃炎", "食物不耐受", "肠易激综合征", "细菌感染"], severity: "medium" },
                { name: "便秘", conditions: ["饮食纤维不足", "脱水", "药物副作用", "肠梗阻"], severity: "low" }
            ],
            back: [
                { name: "背痛", conditions: ["肌肉拉伤", "椎间盘突出", "骨质疏松", "姿势不良"], severity: "medium" },
                { name: "腰痛", conditions: ["腰椎间盘突出", "腰肌劳损", "肾结石", "妇科疾病"], severity: "medium" }
            ],
            limbs: [
                { name: "关节痛", conditions: ["关节炎", "痛风", "运动损伤", "风湿病"], severity: "medium" },
                { name: "肌肉酸痛", conditions: ["运动过度", "病毒感染", "纤维肌痛", "电解质失衡"], severity: "low" }
            ],
            skin: [
                { name: "皮疹", conditions: ["过敏反应", "湿疹", "荨麻疹", "病毒感染"], severity: "low" },
                { name: "瘙痒", conditions: ["皮肤干燥", "过敏", "真菌感染", "肝病"], severity: "low" }
            ],
            eyes: [
                { name: "眼痛", conditions: ["结膜炎", "干眼症", "青光眼", "视疲劳"], severity: "medium" },
                { name: "视力模糊", conditions: ["近视", "远视", "散光", "白内障"], severity: "medium" }
            ],
            ears: [
                { name: "耳痛", conditions: ["中耳炎", "外耳炎", "耳垢堵塞", "颞下颌关节紊乱"], severity: "medium" },
                { name: "耳鸣", conditions: ["听力损失", "压力", "药物副作用", "内耳问题"], severity: "low" }
            ],
            nose: [
                { name: "鼻塞", conditions: ["感冒", "过敏性鼻炎", "鼻窦炎", "鼻息肉"], severity: "low" },
                { name: "流鼻血", conditions: ["干燥", "高血压", "外伤", "血液病"], severity: "medium" }
            ],
            throat: [
                { name: "咽喉痛", conditions: ["感冒", "扁桃体炎", "咽喉炎", "胃食管反流"], severity: "low" },
                { name: "吞咽困难", conditions: ["咽喉炎", "食管炎", "焦虑症", "神经肌肉疾病"], severity: "medium" }
            ],
            urinary: [
                { name: "尿频", conditions: ["尿路感染", "糖尿病", "前列腺问题", "膀胱过度活动"], severity: "medium" },
                { name: "尿痛", conditions: ["尿路感染", "膀胱炎", "肾结石", "性传播疾病"], severity: "medium" }
            ],
            general: [
                { name: "发热", conditions: ["病毒感染", "细菌感染", "炎症反应", "免疫系统疾病"], severity: "medium" },
                { name: "疲劳", conditions: ["贫血", "甲状腺功能减退", "慢性疲劳综合征", "抑郁症"], severity: "medium" },
                { name: "体重下降", conditions: ["糖尿病", "甲状腺功能亢进", "恶性肿瘤", "吸收不良"], severity: "high" }
            ]
        };

        // 建议数据库
        const adviceDatabase = {
            low: [
                "您的症状可能不需要立即医疗干预",
                "建议观察症状变化，多休息，保持充足水分",
                "如症状持续超过一周或加重，请咨询医生",
                "可尝试非处方药物缓解症状，但请遵循说明书"
            ],
            medium: [
                "您的症状可能需要医疗关注",
                "建议在24-48小时内预约医生进行检查",
                "如症状突然加重或出现新症状，请立即就医",
                "在等待就医期间，保持休息并监测症状变化"
            ],
            high: [
                "您的症状可能需要立即医疗关注",
                "建议立即前往急诊或拨打急救电话",
                "不要忽视这些症状，特别是如果伴随胸痛、呼吸困难或意识改变",
                "在等待医疗救助时，保持冷静并尽量减少活动"
            ]
        };

        // 当前选择的状态
        let currentState = {
            bodyPart: null,
            specificSymptom: null,
            duration: null,
            severity: null,
            otherSymptoms: null
        };

        // DOM元素
        const steps = document.querySelectorAll('.step');
        const bodyPartOptions = document.querySelectorAll('#step1 .symptom-option');
        const specificSymptomsContainer = document.getElementById('specific-symptoms');
        const possibleConditionsList = document.getElementById('possible-conditions-list');
        const adviceContent = document.getElementById('advice-content');
        const severityIndicator = document.getElementById('severity-indicator');

        // 初始化事件监听
        function initEventListeners() {
            // 身体部位选择
            bodyPartOptions.forEach(option => {
                option.addEventListener('click', function() {
                    bodyPartOptions.forEach(opt => opt.classList.remove('selected'));
                    this.classList.add('selected');
                    currentState.bodyPart = this.getAttribute('data-value');
                });
            });

            // 下一步按钮
            document.getElementById('next1').addEventListener('click', function() {
                if (!currentState.bodyPart) {
                    alert('请选择身体部位');
                    return;
                }
                loadSpecificSymptoms(currentState.bodyPart);
                goToStep(2);
            });

            document.getElementById('next2').addEventListener('click', function() {
                if (!currentState.specificSymptom) {
                    alert('请选择具体症状');
                    return;
                }
                goToStep(3);
            });

            document.getElementById('next3').addEventListener('click', function() {
                currentState.duration = document.getElementById('duration').value;
                currentState.severity = document.getElementById('severity').value;
                currentState.otherSymptoms = document.getElementById('other-symptoms').value;
                showResults();
                goToStep(4);
            });

            // 上一步按钮
            document.getElementById('prev2').addEventListener('click', () => goToStep(1));
            document.getElementById('prev3').addEventListener('click', () => goToStep(2));
            document.getElementById('prev4').addEventListener('click', () => goToStep(3));

            // 重新开始
            document.getElementById('restart').addEventListener('click', restartChecker);
        }

        // 加载具体症状选项
        function loadSpecificSymptoms(bodyPart) {
            specificSymptomsContainer.innerHTML = '';
            const symptoms = symptomDatabase[bodyPart] || [];
            
            symptoms.forEach(symptom => {
                const option = document.createElement('div');
                option.className = 'symptom-option';
                option.textContent = symptom.name;
                option.setAttribute('data-value', symptom.name);
                option.addEventListener('click', function() {
                    document.querySelectorAll('#specific-symptoms .symptom-option').forEach(opt => {
                        opt.classList.remove('selected');
                    });
                    this.classList.add('selected');
                    currentState.specificSymptom = {
                        name: this.getAttribute('data-value'),
                        conditions: symptom.conditions,
                        severity: symptom.severity
                    };
                });
                specificSymptomsContainer.appendChild(option);
            });
        }

        // 显示结果
        function showResults() {
            // 显示可能的疾病
            possibleConditionsList.innerHTML = '';
            currentState.specificSymptom.conditions.forEach(condition => {
                const item = document.createElement('div');
                item.className = 'condition-item';
                item.textContent = condition;
                possibleConditionsList.appendChild(item);
            });

            // 设置严重程度指示器
            let severityLevel = currentState.specificSymptom.severity;
            let severityText = '';
            
            if (currentState.severity === 'severe') {
                severityLevel = 'high';
            } else if (currentState.severity === 'moderate' && severityLevel === 'low') {
                severityLevel = 'medium';
            }
            
            switch(severityLevel) {
                case 'high':
                    severityText = '高风险 - 需要立即关注';
                    severityIndicator.className = 'severity-indicator high-severity';
                    break;
                case 'medium':
                    severityText = '中等风险 - 建议就医';
                    severityIndicator.className = 'severity-indicator medium-severity';
                    break;
                default:
                    severityText = '低风险 - 建议观察';
                    severityIndicator.className = 'severity-indicator low-severity';
            }
            
            severityIndicator.textContent = severityText;

            // 显示建议
            adviceContent.innerHTML = '';
            const randomAdvice = adviceDatabase[severityLevel].sort(() => 0.5 - Math.random()).slice(0, 3);
            randomAdvice.forEach(advice => {
                const p = document.createElement('p');
                p.textContent = advice;
                p.style.marginBottom = '10px';
                adviceContent.appendChild(p);
            });

            // 添加免责声明
            const disclaimer = document.createElement('p');
            disclaimer.textContent = '注意: 此评估仅供参考，不能替代专业医疗建议。如有疑问或症状加重，请立即咨询医生。';
            disclaimer.style.fontSize = '0.8rem';
            disclaimer.style.color = '#666';
            disclaimer.style.marginTop = '15px';
            adviceContent.appendChild(disclaimer);
        }

        // 跳转到指定步骤
        function goToStep(stepNumber) {
            steps.forEach(step => step.classList.remove('active'));
            document.getElementById(`step${stepNumber}`).classList.add('active');
        }

        // 重新开始检查
        function restartChecker() {
            currentState = {
                bodyPart: null,
                specificSymptom: null,
                duration: null,
                severity: null,
                otherSymptoms: null
            };
            
            document.querySelectorAll('.symptom-option.selected').forEach(opt => {
                opt.classList.remove('selected');
            });
            
            document.getElementById('duration').value = 'less-than-day';
            document.getElementById('severity').value = 'mild';
            document.getElementById('other-symptoms').value = '';
            
            goToStep(1);
        }

        // 初始化
        initEventListeners();
        
        // BMI计算器功能
        document.getElementById('calculate').addEventListener('click', function() {
            const height = parseFloat(document.getElementById('height').value);
            const weight = parseFloat(document.getElementById('weight').value);
            
            if (isNaN(height) || isNaN(weight) || height <= 0 || weight <= 0) {
                alert('请输入有效的身高和体重数值');
                return;
            }
            
            // 计算BMI (体重kg / (身高m)^2)
            const heightInMeter = height / 100;
            const bmi = weight / (heightInMeter * heightInMeter);
            const roundedBMI = bmi.toFixed(1);
            
            // 获取BMI分类和建议
            const { category, advice } = getBMICategory(roundedBMI);
            
            // 显示结果
            document.getElementById('bmi-value').textContent = roundedBMI;
            document.getElementById('bmi-category').textContent = category;
            document.getElementById('bmi-advice').textContent = advice;
            document.getElementById('result').style.display = 'block';
        });
        
        // BMI分类和建议函数
        function getBMICategory(bmi) {
            let category, advice;
            
            if (bmi < 18.5) {
                category = "体重过轻";
                advice = "您的体重低于正常范围。建议咨询医生或营养师，制定合理的增重计划，确保获得足够的营养。";
            } else if (bmi >= 18.5 && bmi < 24) {
                category = "正常范围";
                advice = "恭喜！您的体重在健康范围内。继续保持均衡饮食和规律运动，维持这种健康状态。";
            } else if (bmi >= 24 && bmi < 28) {
                category = "超重";
                advice = "您的体重超出正常范围。建议适当控制饮食，增加运动量，防止发展为肥胖。可以咨询营养师制定减重计划。";
            } else if (bmi >= 28 && bmi < 32) {
                category = "肥胖(一级)";
                advice = "您已达到肥胖标准。建议尽快开始减重计划，调整饮食结构，增加运动量。可以考虑寻求专业医生或营养师的帮助。";
            } else if (bmi >= 32 && bmi < 40) {
                category = "肥胖(二级)";
                advice = "您处于严重肥胖范围。健康风险显著增加，建议立即就医，在专业指导下制定减重计划，可能需要医疗干预。";
            } else {
                category = "极度肥胖";
                advice = "您处于极度肥胖范围，健康风险极高。请立即就医，可能需要专业的医疗干预和治疗方案。";
            }
            
            return { category, advice };
        }
        
        // 简单的导航交互效果
        document.querySelectorAll('.nav-item').forEach(item => {
            item.addEventListener('click', function() {
                document.querySelector('.nav-item.active').classList.remove('active');
                this.classList.add('active');
                
                // 这里可以添加滚动到对应分类的功能
                const sectionId = this.textContent.trim();
                console.log('导航到: ' + sectionId);
            });
        });
        
        // 搜索功能占位
        document.querySelector('.search-box input').addEventListener('keypress', function(e) {
            if (e.key === 'Enter') {
                alert('搜索功能: ' + this.value);
                this.value = '';
            }
        });
        
        // 抑郁症测试功能
        document.getElementById('depressionTestForm').addEventListener('submit', function(e) {
            e.preventDefault();
            
            // 计算总分
            let totalScore = 0;
            for (let i = 1; i <= 9; i++) {
                const selectedOption = document.querySelector(`input[name="q${i}"]:checked`);
                if (selectedOption) {
                    totalScore += parseInt(selectedOption.value);
                } else {
                    alert(`请回答问题 ${i}`);
                    return;
                }
            }
            
            // 显示结果
            document.getElementById('testScore').textContent = totalScore;
            const resultContainer = document.getElementById('depressionResult');
            resultContainer.style.display = 'block';
            
            // 评估抑郁程度
            const severityLevel = document.getElementById('severityLevel');
            const adviceList = document.getElementById('adviceList');
            adviceList.innerHTML = '';
            
            let severityText = '';
            let severityClass = '';
            let adviceItems = [];
            
            if (totalScore <= 4) {
                severityText = '无或极轻微抑郁';
                severityClass = 'minimal';
                adviceItems = [
                    '您的情绪状态良好，继续保持健康的生活方式',
                    '定期进行自我情绪检查',
                    '保持社交活动和体育锻炼'
                ];
            } else if (totalScore <= 9) {
                severityText = '轻度抑郁';
                severityClass = 'mild';
                adviceItems = [
                    '您可能有轻度抑郁症状，建议关注情绪变化',
                    '尝试增加社交活动和体育锻炼',
                    '考虑与朋友或家人谈论您的感受',
                    '如症状持续2周以上，建议咨询医生'
                ];
            } else if (totalScore <= 14) {
                severityText = '中度抑郁';
                severityClass = 'moderate';
                adviceItems = [
                    '您可能有中度抑郁症状，建议寻求专业帮助',
                    '考虑预约心理咨询师或精神科医生',
                    '保持规律的作息和健康饮食',
                    '与信任的人分享您的感受',
                    '避免孤立自己，保持社交活动'
                ];
            } else if (totalScore <= 19) {
                severityText = '中重度抑郁';
                severityClass = 'moderately-severe';
                adviceItems = [
                    '您可能有中重度抑郁症状，强烈建议寻求专业帮助',
                    '请尽快预约精神科医生或心理咨询师',
                    '考虑告诉家人或朋友您的情况',
                    '避免酒精和药物滥用',
                    '如出现自伤念头，请立即寻求帮助'
                ];
            } else {
                severityText = '重度抑郁';
                severityClass = 'severe';
                adviceItems = [
                    '您可能有严重抑郁症状，请立即寻求专业帮助',
                    '强烈建议尽快预约精神科医生',
                    '告诉家人或朋友您的情况，寻求支持',
                    '如出现自伤或自杀念头，请立即拨打心理援助热线或前往医院',
                    '避免独处，确保有人陪伴'
                ];
            }
            
            severityLevel.textContent = severityText;
            severityLevel.className = 'severity-level ' + severityClass;
            
            // 添加建议
            adviceItems.forEach(item => {
                const li = document.createElement('div');
                li.className = 'advice-item';
                li.textContent = item;
                adviceList.appendChild(li);
            });
            
            // 滚动到结果
            resultContainer.scrollIntoView({ behavior: 'smooth' });
        });
    </script>
</body>
</html> 
