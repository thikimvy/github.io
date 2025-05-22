<!DOCTYPE html>
<html lang="zh-CN">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>凤凰单丛香型品鉴游戏</title>
    <script src="https://cdn.tailwindcss.com"></script>
    <link href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.7.2/css/all.min.css" rel="stylesheet">
    <script>
        tailwind.config = {
            theme: {
                extend: {
                    colors: {
                        primary: '#8B5A2B', // 茶色主色调
                        secondary: '#4A6741', // 绿色辅助色
                        accent: '#D4A017', // 金色点缀
                        neutral: '#F5F5DC', // 米白色背景
                    },
                    fontFamily: {
                        sans: ['Inter', 'system-ui', 'sans-serif'],
                    },
                }
            }
        }
    </script>
    <style type="text/tailwindcss">
        @layer utilities {
            .content-auto {
                content-visibility: auto;
            }
            .text-shadow {
                text-shadow: 0 2px 4px rgba(0,0,0,0.1);
            }
            .bg-tea-pattern {
                background-image: url("data:image/svg+xml,%3Csvg width='100' height='100' viewBox='0 0 100 100' xmlns='http://www.w3.org/2000/svg'%3E%3Cpath d='M11 18c3.866 0 7-3.134 7-7s-3.134-7-7-7-7 3.134-7 7 3.134 7 7 7zm48 25c3.866 0 7-3.134 7-7s-3.134-7-7-7-7 3.134-7 7 3.134 7 7 7zm-43-7c1.657 0 3-1.343 3-3s-1.343-3-3-3-3 1.343-3 3 1.343 3 3 3zm63 31c1.657 0 3-1.343 3-3s-1.343-3-3-3-3 1.343-3 3 1.343 3 3 3zM34 90c1.657 0 3-1.343 3-3s-1.343-3-3-3-3 1.343-3 3 1.343 3 3 3zm56-76c1.657 0 3-1.343 3-3s-1.343-3-3-3-3 1.343-3 3 1.343 3 3 3zM12 86c2.21 0 4-1.79 4-4s-1.79-4-4-4-4 1.79-4 4 1.79 4 4 4zm28-65c2.21 0 4-1.79 4-4s-1.79-4-4-4-4 1.79-4 4 1.79 4 4 4zm23-11c2.76 0 5-2.24 5-5s-2.24-5-5-5-5 2.24-5 5 2.24 5 5 5zm-6 60c2.21 0 4-1.79 4-4s-1.79-4-4-4-4 1.79-4 4 1.79 4 4 4zm29 22c2.76 0 5-2.24 5-5s-2.24-5-5-5-5 2.24-5 5 2.24 5 5 5zM32 63c2.76 0 5-2.24 5-5s-2.24-5-5-5-5 2.24-5 5 2.24 5 5 5zm57-13c2.76 0 5-2.24 5-5s-2.24-5-5-5-5 2.24-5 5 2.24 5 5 5zm-9-21c1.105 0 2-.895 2-2s-.895-2-2-2-2 .895-2 2 .895 2 2 2zM60 91c1.105 0 2-.895 2-2s-.895-2-2-2-2 .895-2 2 .895 2 2 2zM35 41c1.105 0 2-.895 2-2s-.895-2-2-2-2 .895-2 2 .895 2 2 2zM12 60c1.105 0 2-.895 2-2s-.895-2-2-2-2 .895-2 2 .895 2 2 2z' fill='%238b5a2b' fill-opacity='0.05' fill-rule='evenodd'/%3E%3C/svg%3E");
            }
            .card-hover {
                transition: transform 0.3s ease, box-shadow 0.3s ease;
            }
            .card-hover:hover {
                transform: translateY(-5px);
                box-shadow: 0 10px 25px -5px rgba(0, 0, 0, 0.1);
            }
            .fade-in {
                animation: fadeIn 0.5s ease-in-out;
            }
            @keyframes fadeIn {
                from { opacity: 0; transform: translateY(10px); }
                to { opacity: 1; transform: translateY(0); }
            }
            .scale-in {
                animation: scaleIn 0.3s ease-in-out;
            }
            @keyframes scaleIn {
                from { transform: scale(0.9); opacity: 0; }
                to { transform: scale(1); opacity: 1; }
            }
        }
    </style>
</head>
<body class="bg-neutral bg-tea-pattern min-h-screen">
    <!-- 导航栏 -->
    <nav class="bg-primary text-white shadow-md fixed w-full z-50 transition-all duration-300" id="navbar">
        <div class="container mx-auto px-4 py-3 flex justify-between items-center">
            <div class="flex items-center space-x-2">
                <i class="fa-solid fa-leaf text-accent text-2xl"></i>
                <h1 class="text-xl md:text-2xl font-bold">凤凰单丛香型品鉴</h1>
            </div>
            <div class="hidden md:flex items-center space-x-6">
                <a href="#game" class="hover:text-accent transition-colors duration-200">开始游戏</a>
                <a href="#info" class="hover:text-accent transition-colors duration-200">香型知识</a>
                <a href="#about" class="hover:text-accent transition-colors duration-200">关于我们</a>
            </div>
            <button class="md:hidden text-white text-xl" id="menu-toggle">
                <i class="fa-solid fa-bars"></i>
            </button>
        </div>
        <!-- 移动端菜单 -->
        <div class="md:hidden hidden bg-primary/95 backdrop-blur-sm" id="mobile-menu">
            <div class="container mx-auto px-4 py-3 flex flex-col space-y-3">
                <a href="#game" class="py-2 hover:text-accent transition-colors duration-200">开始游戏</a>
                <a href="#info" class="py-2 hover:text-accent transition-colors duration-200">香型知识</a>
                <a href="#about" class="py-2 hover:text-accent transition-colors duration-200">关于我们</a>
            </div>
        </div>
    </nav>

    <!-- 英雄区 -->
    <section class="pt-24 md:pt-32 pb-16 md:pb-24 bg-gradient-to-b from-primary/10 to-neutral">
        <div class="container mx-auto px-4 text-center">
            <div class="max-w-3xl mx-auto">
                <h1 class="text-[clamp(2rem,5vw,3.5rem)] font-bold text-primary mb-4 text-shadow">
                    凤凰单丛香型盲盒挑战
                </h1>
                <p class="text-[clamp(1rem,2vw,1.25rem)] text-gray-700 mb-8">
                    品鉴六大经典香型，解锁茶香秘境，成为单丛品鉴大师！
                </p>
                <a href="#game" class="inline-block bg-primary hover:bg-primary/90 text-white font-semibold py-3 px-8 rounded-full shadow-lg hover:shadow-xl transition-all duration-300 transform hover:-translate-y-1">
                    <i class="fa-solid fa-gamepad mr-2"></i>开始挑战
                </a>
            </div>
        </div>
    </section>

    <!-- 游戏区 -->
    <section id="game" class="py-16 bg-neutral">
        <div class="container mx-auto px-4">
            <div class="max-w-4xl mx-auto bg-white rounded-2xl shadow-xl overflow-hidden">
                <div class="bg-secondary text-white p-6 md:p-8">
                    <h2 class="text-2xl md:text-3xl font-bold mb-2">香型品鉴挑战</h2>
                    <p class="text-white/80">观察茶样、闻香、品饮后，猜猜这是哪种香型？</p>
                </div>
                
                <!-- 游戏内容区 -->
                <div class="p-6 md:p-8">
                    <!-- 游戏状态显示 -->
                    <div class="flex justify-between items-center mb-8">
                        <div class="flex items-center space-x-2">
                            <i class="fa-solid fa-trophy text-accent text-xl"></i>
                            <span class="font-medium">当前进度：<span id="progress">0/6</span></span>
                        </div>
                        <div class="flex items-center space-x-2">
                            <i class="fa-solid fa-star text-accent text-xl"></i>
                            <span class="font-medium">正确率：<span id="accuracy">0%</span></span>
                        </div>
                    </div>

                    <!-- 茶样展示 -->
                    <div class="mb-8 text-center">
                        <div class="relative w-full max-w-md mx-auto aspect-video bg-gray-100 rounded-xl overflow-hidden shadow-lg mb-4">
                            <img id="tea-image" src="https://picsum.photos/800/600?random=1" alt="茶样" class="w-full h-full object-cover">
                            <div class="absolute inset-0 bg-black/30 flex items-center justify-center">
                                <div class="text-white text-center">
                                    <span id="tea-number" class="text-4xl md:text-5xl font-bold">1号茶样</span>
                                </div>
                            </div>
                        </div>
                        <p class="text-gray-700 italic">请仔细观察、闻香、品饮后再作答</p>
                    </div>

                    <!-- 香型选项 -->
                    <div class="grid grid-cols-2 md:grid-cols-3 gap-4 mb-8">
                        <button class="scent-option card-hover bg-gray-100 hover:bg-gray-200 p-4 rounded-lg text-center" data-id="1">
                            <span>蜜兰香</span>
                        </button>
                        <button class="scent-option card-hover bg-gray-100 hover:bg-gray-200 p-4 rounded-lg text-center" data-id="2">
                            <span>鸭屎香</span>
                        </button>
                        <button class="scent-option card-hover bg-gray-100 hover:bg-gray-200 p-4 rounded-lg text-center" data-id="3">
                            <span>姜花香</span>
                        </button>
                        <button class="scent-option card-hover bg-gray-100 hover:bg-gray-200 p-4 rounded-lg text-center" data-id="4">
                            <span>大乌叶</span>
                        </button>
                        <button class="scent-option card-hover bg-gray-100 hover:bg-gray-200 p-4 rounded-lg text-center" data-id="5">
                            <span>锯朵仔</span>
                        </button>
                        <button class="scent-option card-hover bg-gray-100 hover:bg-gray-200 p-4 rounded-lg text-center" data-id="6">
                            <span>柚花香</span>
                        </button>
                    </div>

                    <!-- 结果反馈 -->
                    <div id="result" class="hidden mb-6 p-4 rounded-lg scale-in"></div>

                    <!-- 操作按钮 -->
                    <div class="flex justify-center space-x-4">
                        <button id="next-btn" class="hidden bg-secondary hover:bg-secondary/90 text-white font-semibold py-2 px-6 rounded-full shadow hover:shadow-md transition-all duration-200">
                            下一个 <i class="fa-solid fa-arrow-right ml-1"></i>
                        </button>
                        <button id="restart-btn" class="hidden bg-primary hover:bg-primary/90 text-white font-semibold py-2 px-6 rounded-full shadow hover:shadow-md transition-all duration-200">
                            <i class="fa-solid fa-refresh mr-1"></i> 重新开始
                        </button>
                    </div>
                </div>
            </div>
        </div>
    </section>

    <!-- 香型知识区 -->
    <section id="info" class="py-16 bg-gradient-to-b from-neutral to-primary/5">
        <div class="container mx-auto px-4">
            <h2 class="text-3xl md:text-4xl font-bold text-center text-primary mb-12">凤凰单丛六大香型</h2>
            
            <div class="grid grid-cols-1 md:grid-cols-2 lg:grid-cols-3 gap-8">
                <!-- 蜜兰香 -->
                <div class="bg-white rounded-xl shadow-md overflow-hidden card-hover">
                    <div class="h-48 overflow-hidden">
                        <img src="https://picsum.photos/600/400?random=10" alt="蜜兰香" class="w-full h-full object-cover">
                    </div>
                    <div class="p-6">
                        <h3 class="text-xl font-bold text-primary mb-2">蜜兰香</h3>
                        <p class="text-gray-700 mb-4">蜜兰香属凤凰单丛十大花蜜香型之一，干茶带蜜香+兰花香，茶汤甜润如蜜，回甘持久，似啜饮花蜜。</p>
                        <div class="flex items-center text-sm text-gray-600">
                            <i class="fa-solid fa-leaf text-secondary mr-1"></i>
                            <span>特点：蜜甜醇厚，兰香清幽</span>
                        </div>
                    </div>
                </div>
                
                <!-- 鸭屎香 -->
                <div class="bg-white rounded-xl shadow-md overflow-hidden card-hover">
                    <div class="h-48 overflow-hidden">
                        <img src="https://picsum.photos/600/400?random=11" alt="鸭屎香" class="w-full h-full object-cover">
                    </div>
                    <div class="p-6">
                        <h3 class="text-xl font-bold text-primary mb-2">鸭屎香</h3>
                        <p class="text-gray-700 mb-4">原名“银花香”，因茶农怕被偷而谎称“鸭屎香”，香气高扬持久，有自然的花香，滋味醇厚甘滑。</p>
                        <div class="flex items-center text-sm text-gray-600">
                            <i class="fa-solid fa-leaf text-secondary mr-1"></i>
                            <span>特点：高香浓郁，回甘迅猛</span>
                        </div>
                    </div>
                </div>
                
                <!-- 姜花香 -->
                <div class="bg-white rounded-xl shadow-md overflow-hidden card-hover">
                    <div class="h-48 overflow-hidden">
                        <img src="https://picsum.photos/600/400?random=12" alt="姜花香" class="w-full h-full object-cover">
                    </div>
                    <div class="p-6">
                        <h3 class="text-xl font-bold text-primary mb-2">姜花香</h3>
                        <p class="text-gray-700 mb-4">姜花香型凤凰单丛，香气中有轻微的姜花辛香，滋味鲜爽甘滑，回甘力强，耐冲泡。</p>
                        <div class="flex items-center text-sm text-gray-600">
                            <i class="fa-solid fa-leaf text-secondary mr-1"></i>
                            <span>特点：辛香蜜甜，滋味鲜爽</span>
                        </div>
                    </div>
                </div>
                
                <!-- 大乌叶 -->
                <div class="bg-white rounded-xl shadow-md overflow-hidden card-hover">
                    <div class="h-48 overflow-hidden">
                        <img src="https://picsum.photos/600/400?random=13" alt="大乌叶" class="w-full h-full object-cover">
                    </div>
                    <div class="p-6">
                        <h3 class="text-xl font-bold text-primary mb-2">大乌叶</h3>
                        <p class="text-gray-700 mb-4">叶片大而乌绿得名，香气高锐，滋味浓烈，回甘明显，适合喜欢重口味的茶友，耐泡度极高。</p>
                        <div class="flex items-center text-sm text-gray-600">
                            <i class="fa-solid fa-leaf text-secondary mr-1"></i>
                            <span>特点：浓烈霸气，回甘持久</span>
                        </div>
                    </div>
                </div>
                
                <!-- 锯朵仔 -->
                <div class="bg-white rounded-xl shadow-md overflow-hidden card-hover">
                    <div class="h-48 overflow-hidden">
                        <img src="https://picsum.photos/600/400?random=14" alt="锯朵仔" class="w-full h-full object-cover">
                    </div>
                    <div class="p-6">
                        <h3 class="text-xl font-bold text-primary mb-2">锯朵仔</h3>
                        <p class="text-gray-700 mb-4">因叶边缘呈锯齿状得名，香气清幽如杏仁香，滋味甘醇鲜爽，回甘力强，有独特的山韵。</p>
                        <div class="flex items-center text-sm text-gray-600">
                            <i class="fa-solid fa-leaf text-secondary mr-1"></i>
                            <span>特点：杏仁香显，鲜爽甘醇</span>
                        </div>
                    </div>
                </div>
                
                <!-- 柚花香 -->
                <div class="bg-white rounded-xl shadow-md overflow-hidden card-hover">
                    <div class="h-48 overflow-hidden">
                        <img src="https://picsum.photos/600/400?random=15" alt="柚花香" class="w-full h-full object-cover">
                    </div>
                    <div class="p-6">
                        <h3 class="text-xl font-bold text-primary mb-2">柚花香</h3>
                        <p class="text-gray-700 mb-4">香气带有柚子花的清新香气，滋味鲜爽甘滑，汤色黄绿明亮，回甘持久，饮后满口生津。</p>
                        <div class="flex items-center text-sm text-gray-600">
                            <i class="fa-solid fa-leaf text-secondary mr-1"></i>
                            <span>特点：清新柚香，鲜爽回甘</span>
                        </div>
                    </div>
                </div>
            </div>
        </div>
    </section>

    <!-- 关于我们 -->
    <section id="about" class="py-16 bg-white">
        <div class="container mx-auto px-4">
            <div class="max-w-4xl mx-auto">
                <h2 class="text-3xl md:text-4xl font-bold text-center text-primary mb-8">关于我们</h2>
                <div class="bg-neutral rounded-xl p-6 md:p-8 shadow-md">
                    <p class="text-gray-700 mb-4">我们是专业的凤凰单丛茶零售商，致力于为茶友们提供正宗、高品质的凤凰单丛茶。</p>
                    <p class="text-gray-700 mb-4">凤凰单丛茶是广东潮州特产，属于乌龙茶类，具有"形美、色翠、香郁、味甘"四绝。我们精选凤凰山脉核心产区的茶叶，由经验丰富的茶农手工采摘和制作，确保每一片茶叶都能呈现最佳的品质和口感。</p>
                    <p class="text-gray-700 mb-6">通过这个互动游戏，我们希望能让更多的茶友了解凤凰单丛的丰富香型，感受中国传统茶文化的魅力。</p>
                    
                    <div class="text-center">
                        <a href="#" class="inline-block bg-primary hover:bg-primary/90 text-white font-semibold py-3 px-8 rounded-full shadow-lg hover:shadow-xl transition-all duration-300 transform hover:-translate-y-1">
                            了解更多产品
                        </a>
                    </div>
                </div>
            </div>
        </div>
    </section>

    <!-- 页脚 -->
    <footer class="bg-primary text-white py-10">
        <div class="container mx-auto px-4">
            <div class="grid grid-cols-1 md:grid-cols-3 gap-8">
                <div>
                    <div class="flex items-center space-x-2 mb-4">
                        <i class="fa-solid fa-leaf text-accent text-2xl"></i>
                        <h3 class="text-xl font-bold">凤凰单丛品鉴</h3>
                    </div>
                    <p class="text-white/80 mb-4">体验凤凰单丛的香型魅力，感受传统茶文化的博大精深。</p>
                    <div class="flex space-x-4">
                        <a href="#" class="text-white hover:text-accent transition-colors duration-200">
                            <i class="fa-brands fa-weixin text-xl"></i>
                        </a>
                        <a href="#" class="text-white hover:text-accent transition-colors duration-200">
                            <i class="fa-brands fa-weibo text-xl"></i>
                        </a>
                        <a href="#" class="text-white hover:text-accent transition-colors duration-200">
                            <i class="fa-brands fa-instagram text-xl"></i>
                        </a>
                    </div>
                </div>
                
                <div>
                    <h3 class="text-lg font-semibold mb-4">快速链接</h3>
                    <ul class="space-y-2">
                        <li><a href="#game" class="text-white/80 hover:text-accent transition-colors duration-200">开始游戏</a></li>
                        <li><a href="#info" class="text-white/80 hover:text-accent transition-colors duration-200">香型知识</a></li>
                        <li><a href="#about" class="text-white/80 hover:text-accent transition-colors duration-200">关于我们</a></li>
                        <li><a href="#" class="text-white/80 hover:text-accent transition-colors duration-200">购买产品</a></li>
                    </ul>
                </div>
                
                <div>
                    <h3 class="text-lg font-semibold mb-4">联系我们</h3>
                    <ul class="space-y-2">
                        <li class="flex items-center space-x-2">
                            <i class="fa-solid fa-map-marker text-accent"></i>
                            <span class="text-white/80">广东省潮州市凤凰镇</span>
                        </li>
                        <li class="flex items-center space-x-2">
                            <i class="fa-solid fa-phone text-accent"></i>
                            <span class="text-white/80">400-888-8888</span>
                        </li>
                        <li class="flex items-center space-x-2">
                            <i class="fa-solid fa-envelope text-accent"></i>
                            <span class="text-white/80">contact@fenghuangtea.com</span>
                        </li>
                    </ul>
                </div>
            </div>
            
            <div class="border-t border-white/20 mt-8 pt-8 text-center text-white/60 text-sm">
                <p>© 2025 凤凰单丛品鉴游戏 | 保留所有权利</p>
            </div>
        </div>
    </footer>

    <!-- JavaScript -->
    <script>
        // 游戏数据
        const teas = [
            { id: 1, name: "蜜兰香", image: "https://picsum.photos/800/600?random=1" },
            { id: 2, name: "鸭屎香", image: "https://picsum.photos/800/600?random=2" },
            { id: 3, name: "姜花香", image: "https://picsum.photos/800/600?random=3" },
            { id: 4, name: "大乌叶", image: "https://picsum.photos/800/600?random=4" },
            { id: 5, name: "锯朵仔", image: "https://picsum.photos/800/600?random=5" },
            { id: 6, name: "柚花香", image: "https://picsum.photos/800/600?random=6" }
        ];
        
        // 香型介绍
        const teaInfo = {
            "蜜兰香": "蜜兰香属凤凰单丛十大花蜜香型之一，干茶带蜜香+兰花香，茶汤甜润如蜜，回甘持久，似啜饮花蜜。",
            "鸭屎香": "原名“银花香”，因茶农怕被偷而谎称“鸭屎香”，香气高扬持久，有自然的花香，滋味醇厚甘滑。",
            "姜花香": "姜花香型凤凰单丛，香气中有轻微的姜花辛香，滋味鲜爽甘滑，回甘力强，耐冲泡。",
            "大乌叶": "叶片大而乌绿得名，香气高锐，滋味浓烈，回甘明显，适合喜欢重口味的茶友，耐泡度极高。",
            "锯朵仔": "因叶边缘呈锯齿状得名，香气清幽如杏仁香，滋味甘醇鲜爽，回甘力强，有独特的山韵。",
            "柚花香": "香气带有柚子花的清新香气，滋味鲜爽甘滑，汤色黄绿明亮，回甘持久，饮后满口生津。"
        };
        
        // 游戏状态
        let currentTea = null;
        let shuffledTeas = [];
        let currentIndex = 0;
        let correctCount = 0;
        let totalAttempts = 0;
        
        // DOM 元素
        const teaImage = document.getElementById('tea-image');
        const teaNumber = document.getElementById('tea-number');
        const scentOptions = document.querySelectorAll('.scent-option');
        const resultDiv = document.getElementById('result');
        const nextBtn = document.getElementById('next-btn');
        const restartBtn = document.getElementById('restart-btn');
        const progressSpan = document.getElementById('progress');
        const accuracySpan = document.getElementById('accuracy');
        const menuToggle = document.getElementById('menu-toggle');
        const mobileMenu = document.getElementById('mobile-menu');
        const navbar = document.getElementById('navbar');
        
        // 初始化游戏
        function initGame() {
            // 打乱茶样顺序
            shuffledTeas = [...teas].sort(() => Math.random() - 0.5);
            currentIndex = 0;
            correctCount = 0;
            totalAttempts = 0;
            updateProgress();
            loadNextTea();
            
            // 重置UI状态
            resultDiv.classList.add('hidden');
            nextBtn.classList.add('hidden');
            restartBtn.classList.add('hidden');
            
            // 为选项添加点击事件
            scentOptions.forEach(option => {
                option.addEventListener('click', () => checkAnswer(parseInt(option.dataset.id)));
            });
            
            // 下一个按钮事件
            nextBtn.addEventListener('click', loadNextTea);
            
            // 重新开始按钮事件
            restartBtn.addEventListener('click', initGame);
            
            // 移动端菜单切换
            menuToggle.addEventListener('click', () => {
                mobileMenu.classList.toggle('hidden');
            });
            
            // 滚动导航栏效果
            window.addEventListener('scroll', () => {
                if (window.scrollY > 50) {
                    navbar.classList.add('py-2');
                    navbar.classList.add('bg-primary/95');
                    navbar.classList.add('backdrop-blur-sm');
                } else {
                    navbar.classList.remove('py-2');
                    navbar.classList.remove('bg-primary/95');
                    navbar.classList.remove('backdrop-blur-sm');
                }
            });
        }
        
        // 加载下一个茶样
        function loadNextTea() {
            if (currentIndex >= shuffledTeas.length) {
                showGameOver();
                return;
            }
            
            currentTea = shuffledTeas[currentIndex];
            teaImage.src = currentTea.image;
            teaNumber.textContent = `${currentIndex + 1}号茶样`;
            
            // 重置UI状态
            resultDiv.classList.add('hidden');
            nextBtn.classList.add('hidden');
            
            // 重置选项样式
            scentOptions.forEach(option => {
                option.classList.remove('bg-green-100', 'bg-red-100', 'border-green-500', 'border-red-500');
                option.classList.add('bg-gray-100', 'hover:bg-gray-200');
            });
            
            // 平滑滚动到游戏区域
            document.getElementById('game').scrollIntoView({ behavior: 'smooth' });
        }
        
        // 检查答案
        function checkAnswer(selectedId) {
            totalAttempts++;
            
            // 禁用所有选项
            scentOptions.forEach(option => {
                option.classList.remove('hover:bg-gray-200');
                option.classList.remove('bg-gray-100');
            });
            
            // 显示结果
            if (selectedId === currentTea.id) {
                // 回答正确
                correctCount++;
                resultDiv.innerHTML = `
                    <div class="bg-green-100 border border-green-400 text-green-700 px-4 py-3 rounded-lg">
                        <div class="flex items-center">
                            <div class="flex-shrink-0">
                                <i class="fa-solid fa-check-circle text-xl text-green-500"></i>
                            </div>
                            <div class="ml-3">
                                <h3 class="font-bold">恭喜您！答对了！</h3>
                                <div class="mt-2 text-sm">
                                    <p>这是<span class="font-semibold">${currentTea.name}</span>。</p>
                                    <p class="italic">${teaInfo[currentTea.name]}</p>
                                </div>
                            </div>
                        </div>
                    </div>
                `;
                
                // 高亮正确选项
                scentOptions.forEach(option => {
                    if (parseInt(option.dataset.id) === currentTea.id) {
                        option.classList.add('bg-green-100', 'border-green-500');
                    }
                });
            } else {
                // 回答错误
                resultDiv.innerHTML = `
                    <div class="bg-red-100 border border-red-400 text-red-700 px-4 py-3 rounded-lg">
                        <div class="flex items-center">
                            <div class="flex-shrink-0">
                                <i class="fa-solid fa-times-circle text-xl text-red-500"></i>
                            </div>
                            <div class="ml-3">
                                <h3 class="font-bold">很遗憾！答错了</h3>
                                <div class="mt-2 text-sm">
                                    <p>正确答案是<span class="font-semibold">${currentTea.name}</span>。</p>
                                    <p class="italic">${teaInfo[currentTea.name]}</p>
                                </div>
                            </div>
                        </div>
                    </div>
                `;
                
                // 高亮错误和正确选项
                scentOptions.forEach(option => {
                    if (parseInt(option.dataset.id) === selectedId) {
                        option.classList.add('bg-red-100', 'border-red-500');
                    } else if (parseInt(option.dataset.id) === currentTea.id) {
                        option.classList.add('bg-green-100', 'border-green-500');
                    }
                });
            }
            
            // 更新进度和准确率
            updateProgress();
            
            // 显示结果和下一个按钮
            resultDiv.classList.remove('hidden');
            resultDiv.classList.add('fade-in');
            
            if (currentIndex < shuffledTeas.length - 1) {
                nextBtn.classList.remove('hidden');
            } else {
                restartBtn.classList.remove('hidden');
            }
        }
        
        // 更新进度和准确率
        function updateProgress() {
            progressSpan.textContent = `${currentIndex}/${teas.length}`;
            const accuracy = totalAttempts > 0 ? Math.round((correctCount / totalAttempts) * 100) : 0;
            accuracySpan.textContent = `${accuracy}%`;
        }
        
        // 游戏结束
        function showGameOver() {
            resultDiv.innerHTML = `
                <div class="bg-blue-100 border border-blue-400 text-blue-700 px-4 py-3 rounded-lg">
                    <div class="flex items-center">
                        <div class="flex-shrink-0">
                            <i class="fa-solid fa-trophy text-xl text-yellow-500"></i>
                        </div>
                        <div class="ml-3">
                            <h3 class="font-bold">游戏结束！</h3>
                            <div class="mt-2 text-sm">
                                <p>您已完成所有茶样的品鉴挑战！</p>
                                <p>您的正确率是：<span class="font-semibold">${Math.round((correctCount / totalAttempts) * 100)}%</span></p>
                                <p class="italic">感谢参与凤凰单丛香型品鉴挑战，期待您的下次尝试！</p>
                            </div>
                        </div>
                    </div>
                </div>
            `;
            
            resultDiv.classList.remove('hidden');
            resultDiv.classList.add('fade-in');
            restartBtn.classList.remove('hidden');
        }
        
        // 初始化游戏
        document.addEventListener('DOMContentLoaded', initGame);
    </script>
</body>
</html>
    
