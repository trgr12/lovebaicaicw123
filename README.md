<!DOCTYPE html>
<html lang="zh-CN">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0, maximum-scale=1.0, user-scalable=no">
    <title>给小白菜的表白</title>
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.4.0/css/all.min.css">
    <style>
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
            user-select: none;
        }
        
        body {
            font-family: 'Segoe UI', 'Microsoft YaHei', sans-serif;
            background: linear-gradient(135deg, #ff9a9e 0%, #fad0c4 100%);
            min-height: 100vh;
            display: flex;
            flex-direction: column;
            align-items: center;
            justify-content: center;
            padding: 20px;
            overflow-x: hidden;
        }
        
        .container {
            max-width: 500px;
            width: 100%;
            background-color: rgba(255, 255, 255, 0.92);
            border-radius: 20px;
            box-shadow: 0 15px 35px rgba(0, 0, 0, 0.15);
            padding: 30px;
            text-align: center;
            position: relative;
            overflow: hidden;
            animation: fadeIn 1s ease-out;
        }
        
        .container::before {
            content: '';
            position: absolute;
            top: -50%;
            left: -50%;
            width: 200%;
            height: 200%;
            background: radial-gradient(circle, rgba(255,255,255,0.1) 1px, transparent 1px);
            background-size: 20px 20px;
            animation: float 20s linear infinite;
            z-index: 0;
        }
        
        .content {
            position: relative;
            z-index: 1;
        }
        
        h1 {
            color: #ff4d6d;
            margin-bottom: 20px;
            font-size: 2.2rem;
            text-shadow: 2px 2px 4px rgba(0, 0, 0, 0.1);
            animation: pulse 2s infinite;
        }
        
        .heart-icon {
            color: #ff4d6d;
            font-size: 60px;
            margin: 20px 0;
            animation: heartbeat 1.5s infinite;
        }
        
        .message {
            font-size: 1.2rem;
            line-height: 1.6;
            color: #555;
            margin-bottom: 30px;
            padding: 0 10px;
        }
        
        .message .name {
            color: #ff4d6d;
            font-weight: bold;
        }
        
        .buttons-container {
            display: flex;
            justify-content: center;
            gap: 20px;
            margin-top: 40px;
            flex-wrap: wrap;
            position: relative;
            min-height: 150px;
        }
        
        .btn {
            padding: 18px 40px;
            font-size: 1.3rem;
            border: none;
            border-radius: 50px;
            cursor: pointer;
            transition: all 0.3s ease;
            font-weight: bold;
            box-shadow: 0 8px 20px rgba(0, 0, 0, 0.15);
            position: relative;
            overflow: hidden;
            z-index: 2;
        }
        
        .btn:active {
            transform: scale(0.98);
        }
        
        .btn-yes {
            background: linear-gradient(to right, #36d1dc, #5b86e5);
            color: white;
            transition: all 0.5s ease;
        }
        
        .btn-no {
            background: linear-gradient(to right, #ff9a9e, #fad0c4);
            color: #333;
            position: relative;
        }
        
        .btn-yes:hover {
            transform: translateY(-5px);
            box-shadow: 0 12px 25px rgba(91, 134, 229, 0.4);
        }
        
        .btn-yes::after {
            content: '';
            position: absolute;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            background: rgba(255, 255, 255, 0.1);
            transform: translateX(-100%);
            transition: transform 0.5s ease;
        }
        
        .btn-yes:hover::after {
            transform: translateX(100%);
        }
        
        .hearts-fall {
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            pointer-events: none;
            z-index: 1000;
        }
        
        .heart {
            position: absolute;
            color: #ff4d6d;
            font-size: 20px;
            opacity: 0;
            top: -20px;
            animation: fall linear forwards;
        }
        
        .result-message {
            display: none;
            margin-top: 30px;
            padding: 25px;
            background: linear-gradient(135deg, #a8edea 0%, #fed6e3 100%);
            border-radius: 15px;
            font-size: 1.4rem;
            color: #333;
            box-shadow: 0 10px 25px rgba(0, 0, 0, 0.1);
            animation: fadeIn 1s ease-out;
        }
        
        .result-message i {
            color: #ff4d6d;
            margin-right: 10px;
        }
        
        .counter {
            margin-top: 15px;
            font-size: 1rem;
            color: #777;
        }
        
        @keyframes fadeIn {
            from { opacity: 0; transform: translateY(30px); }
            to { opacity: 1; transform: translateY(0); }
        }
        
        @keyframes heartbeat {
            0%, 100% { transform: scale(1); }
            50% { transform: scale(1.1); }
        }
        
        @keyframes pulse {
            0%, 100% { opacity: 1; }
            50% { opacity: 0.9; }
        }
        
        @keyframes float {
            from { transform: rotate(0deg); }
            to { transform: rotate(360deg); }
        }
        
        @keyframes fall {
            to {
                transform: translateY(100vh) rotate(360deg);
                opacity: 0.7;
            }
        }
        
        /* 响应式设计 */
        @media (max-width: 600px) {
            .container {
                padding: 25px 20px;
            }
            
            h1 {
                font-size: 1.8rem;
            }
            
            .message {
                font-size: 1.1rem;
            }
            
            .btn {
                padding: 16px 35px;
                font-size: 1.2rem;
            }
            
            .buttons-container {
                gap: 15px;
            }
        }
        
        @media (max-width: 400px) {
            .buttons-container {
                flex-direction: column;
                align-items: center;
            }
            
            .btn {
                width: 100%;
                max-width: 250px;
            }
        }
    </style>
</head>
<body>
    <div class="container">
        <div class="content">
            <h1>给小白菜 ❤️</h1>
            
            <div class="heart-icon">
                <i class="fas fa-heart"></i>
            </div>
            
            <div class="message">
                从第一次遇见你，我的世界就变得不同了。<br>
                你的笑容像阳光一样温暖，你的存在让我的每一天都充满意义。<br>
                <span class="name">小白菜</span>，你愿意给我一个机会，让我陪你走过未来的每一天吗？
            </div>
            
            <div class="buttons-container">
                <button class="btn btn-yes" id="yesBtn">我愿意 💖</button>
                <button class="btn btn-no" id="noBtn">再考虑一下</button>
            </div>
            
            <div class="result-message" id="resultMessage">
                <i class="fas fa-heart"></i>
                <span id="messageText">太棒了！我保证会让你成为世界上最幸福的人！期待我们的未来！</span>
                <div class="counter" id="counter">这是你第 <span id="clickCount">0</span> 次点击"不同意"，你真的确定吗？😉</div>
            </div>
        </div>
    </div>
    
    <div class="hearts-fall" id="heartsFall"></div>

    <script>
        document.addEventListener('DOMContentLoaded', function() {
            const yesBtn = document.getElementById('yesBtn');
            const noBtn = document.getElementById('noBtn');
            const resultMessage = document.getElementById('resultMessage');
            const messageText = document.getElementById('messageText');
            const clickCountElement = document.getElementById('clickCount');
            const heartsFall = document.getElementById('heartsFall');
            
            let clickCount = 0;
            let yesBtnSize = 1;
            let noBtnAttempts = 0;
            let yesBtnTexts = [
                "我真的喜欢你",
                "请给我一个机会",
                "我会好好珍惜你",
                "你是我最重要的人",
                "没有你我会很难过",
                "我保证会让你幸福",
                "请相信我",
                "这是我真诚的心意"
            ];
            let currentTextIndex = 0;
            
            // 为"不同意"按钮添加点击事件
            noBtn.addEventListener('click', function() {
                clickCount++;
                clickCountElement.textContent = clickCount;
                noBtnAttempts++;
                
                // 每次点击"不同意"，"同意"按钮变大
                yesBtnSize += 0.2;
                yesBtn.style.transform = `scale(${yesBtnSize})`;
                
                // 随机移动"不同意"按钮的位置
                const maxX = window.innerWidth - noBtn.offsetWidth;
                const maxY = window.innerHeight - noBtn.offsetHeight;
                
                const randomX = Math.floor(Math.random() * maxX);
                const randomY = Math.floor(Math.random() * maxY);
                
                // 在移动设备上，我们只做有限的移动
                if (window.innerWidth > 768) {
                    noBtn.style.position = 'fixed';
                    noBtn.style.left = `${randomX}px`;
                    noBtn.style.top = `${randomY}px`;
                } else {
                    // 移动设备上，我们让按钮在容器内移动
                    const container = document.querySelector('.buttons-container');
                    const containerRect = container.getBoundingClientRect();
                    
                    const containerX = Math.floor(Math.random() * (containerRect.width - noBtn.offsetWidth));
                    const containerY = Math.floor(Math.random() * (containerRect.height - noBtn.offsetHeight));
                    
                    noBtn.style.position = 'absolute';
                    noBtn.style.left = `${containerX}px`;
                    noBtn.style.top = `${containerY}px`;
                }
                
                // 创建飘落的心形
                createHearts(5);
                
                // 每点击3次，改变"同意"按钮的文字
                if (noBtnAttempts % 3 === 0) {
                    yesBtn.innerHTML = yesBtnTexts[currentTextIndex] + " 💖";
                    currentTextIndex = (currentTextIndex + 1) % yesBtnTexts.length;
                }
                
                // 如果点击超过8次，显示特殊提示
                if (clickCount === 8) {
                    messageText.innerHTML = "你已经点了8次'不同意'了，看来你需要更多时间考虑。我会一直等你！";
                    resultMessage.style.display = 'block';
                }
                
                // 如果点击超过15次，改变"不同意"按钮的文字
                if (clickCount >= 15) {
                    noBtn.textContent = "真的不再考虑一下吗？";
                }
            });
            
            // 为"同意"按钮添加点击事件
            yesBtn.addEventListener('click', function() {
                // 创建大量心形飘落效果
                createHearts(50);
                
                // 显示成功消息
                messageText.innerHTML = "太棒了！小白菜，我保证会让你成为世界上最幸福的人！期待我们的未来！ 💑";
                resultMessage.style.display = 'block';
                
                // 隐藏按钮
                yesBtn.style.display = 'none';
                noBtn.style.display = 'none';
                
                // 添加庆祝动画
                setTimeout(() => {
                    document.querySelector('.heart-icon').style.animation = 'heartbeat 0.5s infinite';
                }, 100);
                
                // 更新计数器文本
                document.getElementById('counter').innerHTML = `你点击了 <span style="color:#ff4d6d;font-weight:bold">${clickCount}</span> 次"不同意"才同意，我会记住这一天！ ❤️`;
            });
            
            // 创建飘落的心形
            function createHearts(count) {
                for (let i = 0; i < count; i++) {
                    const heart = document.createElement('div');
                    heart.classList.add('heart');
                    heart.innerHTML = '❤️';
                    
                    // 随机大小
                    const size = Math.random() * 25 + 15;
                    heart.style.fontSize = `${size}px`;
                    
                    // 随机位置
                    const startX = Math.random() * window.innerWidth;
                    heart.style.left = `${startX}px`;
                    
                    // 随机动画持续时间
                    const duration = Math.random() * 3 + 2;
                    heart.style.animation = `fall ${duration}s linear forwards`;
                    
                    heartsFall.appendChild(heart);
                    
                    // 动画结束后移除元素
                    setTimeout(() => {
                        heart.remove();
                    }, duration * 1000);
                }
            }
            
            // 初始创建一些心形
            createHearts(10);
            
            // 为移动设备调整触摸事件
            if ('ontouchstart' in window) {
                noBtn.addEventListener('touchstart', function(e) {
                    e.preventDefault();
                    // 模拟点击事件
                    const clickEvent = new MouseEvent('click', {
                        view: window,
                        bubbles: true,
                        cancelable: true
                    });
                    this.dispatchEvent(clickEvent);
                }, { passive: false });
            }
        });
    </script>
</body>
</html>
