<!DOCTYPE html>
<html lang="vi">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Hệ thống quản lý công văn</title>

    <style>
        @import url('https://fonts.googleapis.com/css2?family=Be+Vietnam+Pro:wght@300;400;500;600;700;800;900&display=swap');

        *{
            margin:0;
            padding:0;
            box-sizing:border-box;
            font-family:'Be Vietnam Pro', sans-serif;
        }

        body{
            min-height:100vh;
            overflow:hidden;
            display:flex;
            justify-content:center;
            align-items:center;
            background:
                radial-gradient(circle at 15% 20%, rgba(93, 213, 255, 0.35), transparent 24%),
                radial-gradient(circle at 85% 80%, rgba(174, 90, 255, 0.34), transparent 25%),
                linear-gradient(135deg,#07182f 0%, #0d47d9 45%, #6436ff 100%);
            position:relative;
        }

        .blur-light{
            position:absolute;
            border-radius:50%;
            filter:blur(90px);
            opacity:.65;
            animation:moveLight 9s ease-in-out infinite alternate;
        }

        .light-1{
            width:520px;
            height:520px;
            background:#29d9ff;
            top:-170px;
            left:-140px;
        }

        .light-2{
            width:460px;
            height:460px;
            background:#a855f7;
            right:-120px;
            bottom:-150px;
        }

        .light-3{
            width:300px;
            height:300px;
            background:#ffffff;
            opacity:.15;
            top:20%;
            right:25%;
        }

        .paper{
            position:absolute;
            font-size:82px;
            opacity:.20;
            animation:floatPaper 5s ease-in-out infinite;
            user-select:none;
        }

        .paper-1{
            left:8%;
            top:42%;
            transform:rotate(-18deg);
        }

        .paper-2{
            right:8%;
            top:43%;
            transform:rotate(15deg);
            animation-delay:.6s;
        }

        .paper-3{
            left:28%;
            top:10%;
            font-size:64px;
            opacity:.16;
            animation-delay:1s;
        }

        .paper-4{
            right:28%;
            bottom:10%;
            font-size:58px;
            opacity:.12;
            animation-delay:1.4s;
        }

        .main-card{
            width:780px;
            min-height:520px;
            padding:68px 68px 58px;
            border-radius:34px;
            position:relative;
            z-index:5;
            text-align:center;

            background:linear-gradient(
                145deg,
                rgba(255,255,255,.22),
                rgba(255,255,255,.09)
            );

            border:1px solid rgba(255,255,255,.35);
            backdrop-filter:blur(22px);
            -webkit-backdrop-filter:blur(22px);

            box-shadow:
                0 35px 90px rgba(0,0,0,.35),
                inset 0 1px 0 rgba(255,255,255,.35);
        }

        .main-card::before{
            content:"";
            position:absolute;
            inset:0;
            border-radius:34px;
            background:
                linear-gradient(120deg, rgba(255,255,255,.18), transparent 35%, rgba(255,255,255,.08));
            pointer-events:none;
        }

        .main-card::after{
            content:"";
            position:absolute;
            width:420px;
            height:160px;
            left:50%;
            bottom:-70px;
            transform:translateX(-50%);
            background:rgba(255,255,255,.12);
            border-radius:50%;
            filter:blur(12px);
        }

        .content{
            position:relative;
            z-index:2;
        }

        .logo-box{
            width:124px;
            height:124px;
            margin:-128px auto 34px;
            border-radius:30px;
            display:flex;
            align-items:center;
            justify-content:center;
            font-size:66px;

            background:linear-gradient(
                145deg,
                rgba(255,255,255,.36),
                rgba(255,255,255,.12)
            );

            border:1px solid rgba(255,255,255,.45);
            backdrop-filter:blur(16px);

            box-shadow:
                0 22px 45px rgba(0,0,0,.30),
                inset 0 1px 0 rgba(255,255,255,.55);

            animation:logoFloat 4s ease-in-out infinite;
        }

        h1{
            color:white;
            font-size:56px;
            line-height:1.16;
            font-weight:900;
            letter-spacing:1.2px;
            margin-bottom:24px;
            text-transform:uppercase;

            text-shadow:
                0 0 18px rgba(255,255,255,.35),
                0 8px 24px rgba(0,0,0,.30);
        }

        .desc{
            color:rgba(255,255,255,.90);
            font-size:20px;
            line-height:1.75;
            font-weight:400;
            margin-bottom:36px;
        }

        .divider{
            width:160px;
            height:5px;
            margin:0 auto 36px;
            border-radius:20px;
            background:linear-gradient(
                90deg,
                transparent,
                rgba(255,255,255,.95),
                #4ee7ff,
                rgba(255,255,255,.95),
                transparent
            );
            box-shadow:0 0 18px rgba(78,231,255,.65);
        }

        .btn-start{
            display:inline-flex;
            align-items:center;
            gap:12px;
            padding:18px 72px;
            border-radius:999px;
            text-decoration:none;
            color:white;
            font-size:22px;
            font-weight:800;
            position:relative;
            overflow:hidden;

            background:linear-gradient(135deg,#35d7ff,#1677ff,#5145ff);

            box-shadow:
                0 0 24px rgba(53,215,255,.50),
                0 18px 40px rgba(0,0,0,.30);

            transition:.35s ease;
        }

        .btn-start::before{
            content:"";
            position:absolute;
            top:0;
            left:-120%;
            width:80%;
            height:100%;
            background:linear-gradient(90deg, transparent, rgba(255,255,255,.45), transparent);
            transform:skewX(-25deg);
            transition:.65s;
        }

        .btn-start:hover::before{
            left:130%;
        }

        .btn-start:hover{
            transform:translateY(-6px) scale(1.04);
            box-shadow:
                0 0 36px rgba(53,215,255,.85),
                0 26px 55px rgba(0,0,0,.38);
        }

        .btn-start span{
            transition:.3s;
        }

        .btn-start:hover span{
            transform:translateX(5px);
        }

        .bubble{
            position:absolute;
            width:9px;
            height:9px;
            border-radius:50%;
            background:white;
            opacity:.9;
            animation:bubbleUp 1s ease forwards;
            pointer-events:none;
        }

        @keyframes floatPaper{
            0%,100%{
                translate:0 0;
            }
            50%{
                translate:0 -18px;
            }
        }

        @keyframes logoFloat{
            0%,100%{
                transform:translateY(0);
            }
            50%{
                transform:translateY(-8px);
            }
        }

        @keyframes moveLight{
            from{
                transform:translate(0,0) scale(1);
            }
            to{
                transform:translate(60px,40px) scale(1.08);
            }
        }

        @keyframes bubbleUp{
            0%{
                transform:translateY(0) scale(1);
                opacity:1;
            }
            100%{
                transform:translateY(-95px) scale(.2);
                opacity:0;
            }
        }

        @media(max-width:850px){
            .main-card{
                width:88%;
                padding:58px 28px 46px;
            }

            h1{
                font-size:38px;
            }

            .desc{
                font-size:16px;
            }

            .btn-start{
                font-size:18px;
                padding:16px 48px;
            }

            .paper{
                display:none;
            }
        }
    </style>
</head>

<body>

    <div class="blur-light light-1"></div>
    <div class="blur-light light-2"></div>
    <div class="blur-light light-3"></div>

    <div class="paper paper-1">📄</div>
    <div class="paper paper-2">📁</div>
    <div class="paper paper-3">📋</div>
    <div class="paper paper-4">🗂️</div>

    <div class="main-card">
        <div class="content">

            <div class="logo-box">
                📋
            </div>

            <h1>
                Hệ thống quản lý<br>
                công văn
            </h1>

            <p class="desc">
                Website hỗ trợ quản lý, lưu trữ và tìm kiếm công văn<br>
                dành cho trường Đại học.
            </p>

            <div class="divider"></div>

            <a href="auth.php" class="btn-start" id="startBtn">
                Bắt đầu <span>→</span>
            </a>

        </div>
    </div>

    <script>
        const startBtn = document.getElementById("startBtn");

        startBtn.addEventListener("mouseenter", function(){
            for(let i = 0; i < 10; i++){
                const bubble = document.createElement("span");
                bubble.className = "bubble";

                bubble.style.left = Math.random() * startBtn.offsetWidth + "px";
                bubble.style.top = Math.random() * startBtn.offsetHeight + "px";
                bubble.style.animationDelay = Math.random() * 0.15 + "s";

                startBtn.appendChild(bubble);

                setTimeout(() => {
                    bubble.remove();
                }, 1000);
            }
        });
    </script>

</body>
</html>
