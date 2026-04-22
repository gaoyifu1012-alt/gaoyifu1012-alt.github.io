[deepseek_html_20260422_b4db51 (1).html](https://github.com/user-attachments/files/26968808/deepseek_html_20260422_b4db51.1.html)
<!DOCTYPE html>
<html lang="zh-CN">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>YL API · 霓虹中转站</title>
    <!-- Tailwind CSS (实用框架) -->
    <script src="https://cdn.tailwindcss.com"></script>
    <!-- 赛博朋克风格字体: Orbitron + Rajdhani + Inter fallback -->
    <link href="https://fonts.googleapis.com/css2?family=Orbitron:wght@400;600;800;900&family=Rajdhani:wght@300;400;500;600;700&display=swap" rel="stylesheet">
    <!-- Font Awesome 6 (免费图标库) -->
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.0.0-beta3/css/all.min.css">
    <style>
        /* ===== 赛博朋克核心风格 ===== */
        * { margin: 0; padding: 0; box-sizing: border-box; }
        
        body {
            font-family: 'Rajdhani', 'Inter', sans-serif;
            background-color: #0b0515;
            background-image: 
                /* 动态网格线 (通过动画平移) */
                repeating-linear-gradient(0deg, rgba(0, 255, 255, 0.03) 0px, rgba(0, 255, 255, 0.03) 2px, transparent 2px, transparent 40px),
                repeating-linear-gradient(90deg, rgba(255, 0, 255, 0.03) 0px, rgba(255, 0, 255, 0.03) 2px, transparent 2px, transparent 40px),
                /* 径向渐变光晕 */
                radial-gradient(circle at 20% 30%, rgba(157, 0, 255, 0.2) 0%, transparent 40%),
                radial-gradient(circle at 80% 70%, rgba(0, 255, 255, 0.15) 0%, transparent 45%),
                radial-gradient(circle at 40% 80%, rgba(255, 0, 255, 0.1) 0%, transparent 50%);
            min-height: 100vh;
            color: #e0f0ff;
            position: relative;
            overflow-x: hidden;
        }

        /* 扫描线噪点叠加 */
        body::after {
            content: "";
            position: fixed;
            top: 0; left: 0; width: 100%; height: 100%;
            background: repeating-linear-gradient(0deg, rgba(0,0,0,0.15) 0px, rgba(255,255,255,0.02) 1px, transparent 2px, transparent 4px);
            pointer-events: none;
            z-index: 9999;
            opacity: 0.35;
        }

        /* 网格平移动画 */
        @keyframes gridPan {
            0% { background-position: 0 0, 0 0; }
            100% { background-position: 0 40px, 40px 0; }
        }
        body {
            animation: gridPan 18s linear infinite;
        }

        /* 自定义字体家族覆盖 */
        h1, h2, h3, h4, .font-display {
            font-family: 'Orbitron', 'Rajdhani', sans-serif;
            letter-spacing: 0.05em;
        }

        /* 故障效果 (Glitch) — 用于主标题 */
        .glitch {
            position: relative;
            text-shadow: 0.05em 0 0 rgba(255, 0, 255, 0.6), -0.05em -0.025em 0 rgba(0, 255, 255, 0.6);
            animation: glitch-shake 0.3s infinite alternate;
        }
        .glitch::before,
        .glitch::after {
            content: attr(data-text);
            position: absolute;
            top: 0; left: 0;
            width: 100%; height: 100%;
            background: transparent;
        }
        .glitch::before {
            color: #0ff;
            z-index: -1;
            clip-path: polygon(0 0, 100% 0, 100% 35%, 0 35%);
            transform: translate(-0.04em, -0.03em);
            opacity: 0.7;
        }
        .glitch::after {
            color: #f0f;
            z-index: -2;
            clip-path: polygon(0 65%, 100% 65%, 100% 100%, 0 100%);
            transform: translate(0.04em, 0.03em);
            opacity: 0.7;
        }
        @keyframes glitch-shake {
            0% { transform: translate(0); }
            20% { transform: translate(-0.5px, 0.5px); }
            40% { transform: translate(0.5px, -0.5px); }
            60% { transform: translate(-0.5px, -0.5px); }
            80% { transform: translate(0.5px, 0.5px); }
            100% { transform: translate(0); }
        }

        /* 霓虹边框工具类 */
        .neon-border-cyan {
            border: 1px solid rgba(0, 255, 255, 0.35);
            box-shadow: 0 0 12px rgba(0, 255, 255, 0.25), inset 0 0 6px rgba(0, 255, 255, 0.1);
        }
        .neon-border-magenta {
            border: 1px solid rgba(255, 0, 255, 0.35);
            box-shadow: 0 0 12px rgba(255, 0, 255, 0.25), inset 0 0 6px rgba(255, 0, 255, 0.1);
        }

        /* 斜切多边形裁切 (卡片) */
        .clip-cyber {
            clip-path: polygon(0% 0%, 94% 0%, 100% 8%, 100% 100%, 6% 100%, 0% 92%);
        }
        .clip-cyber-sm {
            clip-path: polygon(0% 0%, 92% 0%, 100% 10%, 100% 100%, 8% 100%, 0% 90%);
        }

        /* 卡片背景：半透明毛玻璃+深色渐变 */
        .cyber-card {
            background: rgba(8, 4, 22, 0.65);
            backdrop-filter: blur(12px);
            -webkit-backdrop-filter: blur(12px);
            border: 1px solid rgba(0, 255, 255, 0.3);
            box-shadow: 0 0 20px rgba(0, 180, 255, 0.2), inset 0 0 15px rgba(0, 255, 255, 0.05);
            transition: all 0.25s ease;
        }
        .cyber-card:hover {
            border-color: #ff00ff;
            box-shadow: 0 0 30px #ff00ff55, inset 0 0 12px #0ff3;
            transform: translateY(-3px);
        }

        /* 霓虹发光文字 */
        .neon-text-cyan {
            text-shadow: 0 0 8px #0ff, 0 0 20px #0ff8;
        }
        .neon-text-magenta {
            text-shadow: 0 0 8px #f0f, 0 0 20px #f0f8;
        }

        /* 按钮样式 */
        .cyber-btn-primary {
            background: transparent;
            border: 1.5px solid #0ff;
            color: #0ff;
            font-weight: 600;
            text-transform: uppercase;
            letter-spacing: 2px;
            box-shadow: 0 0 15px #0ff6, inset 0 0 8px #0ff3;
            clip-path: polygon(8% 0%, 100% 0%, 92% 100%, 0% 100%);
            transition: 0.2s;
        }
        .cyber-btn-primary:hover {
            background: #0ff;
            color: #0a0515;
            box-shadow: 0 0 30px #0ff, 0 0 60px #0ff;
            border-color: #fff;
        }
        .cyber-btn-secondary {
            background: transparent;
            border: 1.5px solid #f0f;
            color: #f0f;
            font-weight: 600;
            text-transform: uppercase;
            letter-spacing: 2px;
            box-shadow: 0 0 12px #f0f6;
            clip-path: polygon(8% 0%, 100% 0%, 92% 100%, 0% 100%);
        }
        .cyber-btn-secondary:hover {
            background: #f0f;
            color: #0a0515;
            box-shadow: 0 0 30px #f0f;
        }

        /* 步骤序号——六边形 */
        .hex-step {
            width: 70px; height: 70px;
            background: rgba(0, 255, 255, 0.08);
            border: 1.5px solid #0ff;
            clip-path: polygon(25% 0%, 75% 0%, 100% 25%, 100% 75%, 75% 100%, 25% 100%, 0% 75%, 0% 25%);
            display: flex;
            align-items: center;
            justify-content: center;
            font-size: 1.8rem;
            font-weight: 800;
            font-family: 'Orbitron';
            color: #0ff;
            text-shadow: 0 0 12px #0ff;
            box-shadow: 0 0 20px #0ff4, inset 0 0 8px #0ff3;
            transition: 0.2s;
        }
        .step-connector {
            background: linear-gradient(90deg, transparent, #0ff, #f0f, transparent);
            height: 2px;
            filter: drop-shadow(0 0 6px cyan);
        }

        /* 图标霓虹效果 */
        .icon-neon {
            filter: drop-shadow(0 0 6px currentColor);
        }

        /* 数值卡片文字发光 */
        .stat-number {
            text-shadow: 0 0 15px cyan, 0 0 30px magenta;
        }

        /* 浮动装饰元素 (HUD) */
        .hud-circle {
            position: absolute;
            border: 1px dashed #0ff4;
            border-radius: 50%;
            width: 300px; height: 300px;
            top: 10%; left: -100px;
            opacity: 0.2;
            pointer-events: none;
            animation: rotateSlow 40s linear infinite;
        }
        .hud-circle2 {
            position: absolute;
            border: 1px solid #f0f3;
            border-radius: 50%;
            width: 500px; height: 500px;
            bottom: -150px; right: -150px;
            opacity: 0.15;
            pointer-events: none;
            animation: rotateSlow 30s linear infinite reverse;
        }
        @keyframes rotateSlow {
            from { transform: rotate(0deg); }
            to { transform: rotate(360deg); }
        }

        /* 链接占位提示 */
        .link-placeholder-note {
            opacity: 0.5;
            font-size: 0.7rem;
        }
        
        /* 新增：Logo区域自定义 */
        .logo-wrapper {
            display: flex;
            align-items: center;
            justify-content: center;
            gap: 15px;
            flex-wrap: wrap;
        }
        .logo-icon-placeholder {
            width: 60px;
            height: 60px;
            background: rgba(0, 255, 255, 0.1);
            border: 2px solid #0ff;
            box-shadow: 0 0 25px #0ff, inset 0 0 12px #0ff;
            clip-path: polygon(30% 0%, 70% 0%, 100% 30%, 100% 70%, 70% 100%, 30% 100%, 0% 70%, 0% 30%);
            display: flex;
            align-items: center;
            justify-content: center;
            font-size: 32px;
            color: #0ff;
            text-shadow: 0 0 15px cyan;
            transition: 0.2s;
        }
        .logo-icon-placeholder i {
            filter: drop-shadow(0 0 8px cyan);
        }
        .logo-text-main {
            font-family: 'Orbitron', sans-serif;
            font-size: 3.5rem;
            font-weight: 900;
            background: linear-gradient(135deg, #0ff 0%, #f0f 80%);
            -webkit-background-clip: text;
            background-clip: text;
            color: transparent;
            text-shadow: 0 0 25px #0ff, 0 0 40px #f0f;
            letter-spacing: 6px;
            line-height: 1.2;
        }
        .logo-tagline {
            font-family: 'Rajdhani', sans-serif;
            font-size: 1.1rem;
            font-weight: 500;
            letter-spacing: 3px;
            color: #a0f0ff;
            text-shadow: 0 0 10px cyan;
            text-transform: uppercase;
            border-left: 2px solid #f0f;
            padding-left: 20px;
            margin-left: 10px;
        }
        @media (max-width: 640px) {
            .logo-text-main { font-size: 2.4rem; }
            .logo-tagline { font-size: 0.8rem; border-left: none; padding-left: 0; margin-left: 0; }
        }
    </style>
</head>
<body class="relative">

<!-- HUD 装饰元素 -->
<div class="hud-circle"></div>
<div class="hud-circle2"></div>
<div class="fixed top-0 left-0 w-full h-full pointer-events-none" style="background: radial-gradient(circle at 20% 30%, #0ff1 0%, transparent 30%);"></div>

<!-- 主要内容区 (不包含导航/公告，仅首页模块) -->
<main class="relative max-w-7xl mx-auto px-4 sm:px-6 lg:px-8 py-6 md:py-10 z-10">
    
    <!-- ========== 🆕 新增 Logo 区域 (占位图标 + YL API + 标语) ========== -->
    <div class="flex flex-col items-center justify-center mb-8 md:mb-12">
        <div class="logo-wrapper">
            <!-- Logo 图标占位符 (你可以替换为图片) -->
           
                <img src="https://i.imgs.ovh/2026/04/22/ZNLnvg.png" alt="ZNLnvg.png" border="0" class="w-32 h-32 object-contain">
     
            <div class="text-center sm:text-left">
                <div class="logo-text-main">YL API</div>
                <div class="logo-tagline">—— 一站式高性价比API中转解决方案 ——</div>
            </div>
        </div>
        <!-- 微装饰线 -->
        <div class="w-40 h-px bg-gradient-to-r from-transparent via-cyan-400 to-transparent mt-4"></div>
    </div>

    <!-- ========== 核心 Banner 区域 (故障标题) ========== -->
    <section class="text-center mb-20">
        <h1 class="glitch text-5xl md:text-6xl lg:text-7xl font-black uppercase tracking-widest mb-4" data-text="高速稳定 · 低耗智能">
            高速稳定 · 低耗智能
        </h1>
        <p class="text-xl md:text-2xl text-cyan-200/80 max-w-3xl mx-auto font-light tracking-wide" style="text-shadow: 0 0 15px #0ff;">
            <i class="fas fa-bolt text-cyan-300 mr-2"></i> 为开发者提供极速、安全的 API 中转服务 <i class="fas fa-bolt text-cyan-300 ml-2"></i>
        </p>
        <!-- 按钮组 (链接占位符) -->
        <div class="mt-10 flex flex-wrap gap-5 justify-center">
            <!-- 开始使用 链接占位 -->
            <a href="#" class="cyber-btn-primary px-8 py-3.5 text-lg inline-flex items-center gap-2">
                <i class="fas fa-rocket"></i> 开始使用
                <!-- 请替换 href="#" 为实际链接 -->
            </a>
            <!-- 查看文档 链接占位 -->
            <a href="#" class="cyber-btn-secondary px-8 py-3.5 text-lg inline-flex items-center gap-2">
                <i class="fas fa-code"></i> 查看文档
                <!-- 请替换 href="#" 为实际链接 -->
            </a>
        </div>
        <div class="mt-3 text-cyan-400/40 text-xs font-mono">
            &lt; 链接占位符 · 替换 # 为你的控制台/文档地址 &gt;
        </div>
    </section>

    <!-- ========== 数据看板 (斜切卡片+霓虹数值) ========== -->
    <section class="grid grid-cols-2 md:grid-cols-4 gap-5 mb-20">
        <div class="cyber-card clip-cyber p-5 text-center">
            <div class="text-5xl font-bold stat-number bg-gradient-to-r from-cyan-300 to-magenta-300 bg-clip-text text-transparent">99.99%</div>
            <div class="text-sm uppercase tracking-widest text-cyan-300 mt-2 font-orbitron">可用性</div>
        </div>
        <div class="cyber-card clip-cyber p-5 text-center">
            <div class="text-5xl font-bold stat-number bg-gradient-to-r from-cyan-300 to-magenta-300 bg-clip-text text-transparent">&lt;80ms</div>
            <div class="text-sm uppercase tracking-widest text-cyan-300 mt-2 font-orbitron">平均延迟</div>
        </div>
        <div class="cyber-card clip-cyber p-5 text-center">
            <div class="text-5xl font-bold stat-number bg-gradient-to-r from-cyan-300 to-magenta-300 bg-clip-text text-transparent">50+</div>
            <div class="text-sm uppercase tracking-widest text-cyan-300 mt-2 font-orbitron">全球节点</div>
        </div>
        <div class="cyber-card clip-cyber p-5 text-center">
            <div class="text-5xl font-bold stat-number bg-gradient-to-r from-cyan-300 to-magenta-300 bg-clip-text text-transparent">10K+</div>
            <div class="text-sm uppercase tracking-widest text-cyan-300 mt-2 font-orbitron">活跃用户</div>
        </div>
    </section>

    <!-- ========== 产品特性区 (6个斜切卡片，霓虹图标) ========== -->
    <section class="mb-20">
        <div class="text-center mb-14">
            <h2 class="text-4xl md:text-5xl font-black uppercase tracking-wider neon-text-cyan">为规模化而生</h2>
            <div class="h-1 w-32 mx-auto mt-3 bg-gradient-to-r from-transparent via-cyan-400 to-transparent"></div>
        </div>
        <div class="grid grid-cols-1 sm:grid-cols-2 lg:grid-cols-3 gap-7">
            <!-- 卡片 1 -->
            <div class="cyber-card clip-cyber p-6">
                <div class="w-14 h-14 rounded-none clip-cyber-sm bg-cyan-500/10 flex items-center justify-center mb-5 border border-cyan-400/40 icon-neon">
                    <i class="fas fa-bolt text-3xl text-cyan-300"></i>
                </div>
                <h3 class="text-2xl font-bold text-cyan-200 mb-2 uppercase tracking-wide">极速响应</h3>
                <p class="text-gray-300/80 text-sm">毫秒级延迟优化，骨干网专用通道，每次请求快如闪电。</p>
            </div>
            <!-- 卡片 2 -->
            <div class="cyber-card clip-cyber p-6">
                <div class="w-14 h-14 clip-cyber-sm bg-fuchsia-500/10 flex items-center justify-center mb-5 border border-fuchsia-400/40 icon-neon">
                    <i class="fas fa-shield-alt text-3xl text-fuchsia-300"></i>
                </div>
                <h3 class="text-2xl font-bold text-fuchsia-200 mb-2 uppercase">安全可靠</h3>
                <p class="text-gray-300/80 text-sm">TLS 1.3 加密 + 实时风控，敏感数据全程装甲防护。</p>
            </div>
            <!-- 卡片 3 -->
            <div class="cyber-card clip-cyber p-6">
                <div class="w-14 h-14 clip-cyber-sm bg-purple-500/10 flex items-center justify-center mb-5 border border-purple-400/40 icon-neon">
                    <i class="fas fa-globe text-3xl text-purple-300"></i>
                </div>
                <h3 class="text-2xl font-bold text-purple-200 mb-2 uppercase">全球节点</h3>
                <p class="text-gray-300/80 text-sm">亚美欧智能调度，就近接入，跨洲延迟降至最低。</p>
            </div>
            <!-- 卡片 4 -->
            <div class="cyber-card clip-cyber p-6">
                <div class="w-14 h-14 clip-cyber-sm bg-amber-500/10 flex items-center justify-center mb-5 border border-amber-400/40 icon-neon">
                    <i class="fas fa-arrow-rotate-right text-3xl text-amber-300"></i>
                </div>
                <h3 class="text-2xl font-bold text-amber-200 mb-2 uppercase">高可用性</h3>
                <p class="text-gray-300/80 text-sm">多副本冗余 + 自动故障切换，全年可用性99.99%。</p>
            </div>
            <!-- 卡片 5 -->
            <div class="cyber-card clip-cyber p-6">
                <div class="w-14 h-14 clip-cyber-sm bg-rose-500/10 flex items-center justify-center mb-5 border border-rose-400/40 icon-neon">
                    <i class="fas fa-lock text-3xl text-rose-300"></i>
                </div>
                <h3 class="text-2xl font-bold text-rose-200 mb-2 uppercase">隐私保护</h3>
                <p class="text-gray-300/80 text-sm">日志脱敏处理，不存储业务内容，符合GDPR。</p>
            </div>
            <!-- 卡片 6 -->
            <div class="cyber-card clip-cyber p-6">
                <div class="w-14 h-14 clip-cyber-sm bg-emerald-500/10 flex items-center justify-center mb-5 border border-emerald-400/40 icon-neon">
                    <i class="fas fa-headset text-3xl text-emerald-300"></i>
                </div>
                <h3 class="text-2xl font-bold text-emerald-200 mb-2 uppercase">7x24 支持</h3>
                <p class="text-gray-300/80 text-sm">技术团队全天候值守，工单/邮件极速响应。</p>
            </div>
        </div>
    </section>

    <!-- ========== 快速开始流程 (六边形步骤 + 发光连接线) ========== -->
    <section class="mb-20">
        <div class="text-center mb-12">
            <h2 class="text-4xl font-black uppercase neon-text-magenta">接入协议</h2>
            <p class="text-gray-400 mt-2 font-mono">/// 四步完成初始化 ///</p>
        </div>
        <div class="relative">
            <!-- 桌面连接线 (发光虚线) -->
            <div class="hidden md:block absolute top-40 left-[10%] right-[10%] h-0.5 step-connector opacity-70"></div>
            <div class="grid grid-cols-1 md:grid-cols-4 gap-8 relative">
                <!-- Step 1 -->
                <div class="flex flex-col items-center text-center group z-10">
                    <div class="hex-step group-hover:scale-110 group-hover:border-fuchsia-400 group-hover:text-fuchsia-300 transition-all duration-200">
                        1
                    </div>
                    <div class="mt-5 cyber-card clip-cyber-sm p-5 w-full">
                        <i class="fas fa-user-plus text-3xl text-cyan-300 icon-neon mb-3"></i>
                        <h4 class="text-xl font-bold text-white">注册账号</h4>
                        <p class="text-xs text-gray-400 mt-1">一分钟完成，无需实名</p>
                    </div>
                </div>
                <!-- Step 2 -->
                <div class="flex flex-col items-center text-center group z-10">
                    <div class="hex-step group-hover:scale-110 transition-all">2</div>
                    <div class="mt-5 cyber-card clip-cyber-sm p-5 w-full">
                        <i class="fas fa-key text-3xl text-fuchsia-300 icon-neon mb-3"></i>
                        <h4 class="text-xl font-bold text-white">获取密钥</h4>
                        <p class="text-xs text-gray-400 mt-1">控制台一键生成 API Key</p>
                    </div>
                </div>
                <!-- Step 3 -->
                <div class="flex flex-col items-center text-center group z-10">
                    <div class="hex-step group-hover:scale-110 transition-all">3</div>
                    <div class="mt-5 cyber-card clip-cyber-sm p-5 w-full">
                        <i class="fas fa-plug text-3xl text-purple-300 icon-neon mb-3"></i>
                        <h4 class="text-xl font-bold text-white">接入 API</h4>
                        <p class="text-xs text-gray-400 mt-1">替换 base URL 即刻使用</p>
                    </div>
                </div>
                <!-- Step 4 -->
                <div class="flex flex-col items-center text-center group z-10">
                    <div class="hex-step group-hover:scale-110 transition-all">4</div>
                    <div class="mt-5 cyber-card clip-cyber-sm p-5 w-full">
                        <i class="fas fa-check-circle text-3xl text-emerald-300 icon-neon mb-3"></i>
                        <h4 class="text-xl font-bold text-white">开始使用</h4>
                        <p class="text-xs text-gray-400 mt-1">监控用量，畅享高速通道</p>
                    </div>
                </div>
            </div>
        </div>
            </section>

   </main>

<!-- 额外的扫描线动画(通过背景已实现) 及 提示：所有按钮链接均为占位符 # -->
<!-- 左上角Logo由New API框架管理，此处未生成。系统公告栏亦未包含。 -->
<!-- Logo区域中的图标占位符：如需替换为你的图片，将 <i class="fas fa-bolt"></i> 替换为 <img src="你的logo.png" class="w-8 h-8"> -->

</body>
</html>
