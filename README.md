<!DOCTYPE html>
<html lang="bn">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>TikTok ভিডিও ডাউনলোডার | Shohag Vai</title>
    <style>
        body {
            font-family: 'Poppins', sans-serif;
            text-align: center;
            padding: 20px;
            margin: 0;
            height: auto;  /* Height auto to allow scrolling */
            background: linear-gradient(to right, #0f2027, #203a43, #2c5364);
            color: white;
            overflow-y: auto;  /* Enable scrolling */
            position: relative;
        }

        /* Moving lines animation */
        .line {
            position: absolute;
            width: 2px;
            height: 100px;
            background-color: rgba(255, 255, 255, 0.6);
            animation: moveLines 10s linear infinite;
        }

        /* Keyframe for moving lines */
        @keyframes moveLines {
            0% { top: 50%; left: 0; transform: rotate(0deg); }
            25% { top: 10%; left: 50%; transform: rotate(90deg); }
            50% { top: 80%; left: 100%; transform: rotate(180deg); }
            75% { top: 50%; left: 50%; transform: rotate(270deg); }
            100% { top: 50%; left: 0; transform: rotate(360deg); }
        }

        /* Multiple lines with different animation delays */
        .line1 { animation-delay: 0s; }
        .line2 { animation-delay: 2s; }
        .line3 { animation-delay: 4s; }
        .line4 { animation-delay: 6s; }
        .line5 { animation-delay: 8s; }
        .line6 { width: 2px; height: 150px; animation: moveLines 15s linear infinite; }
        .line7 { width: 150px; height: 2px; animation: moveLines 12s linear infinite; }

        /* Container for input fields and buttons */
        .container {
            position: relative;
            z-index: 1;
            max-width: 600px;
            margin: auto;
            background: rgba(255, 255, 255, 0.1);
            padding: 20px;
            border-radius: 10px;
            box-shadow: 0px 0px 15px rgba(255, 255, 255, 0.2);
        }

        h2 {
            font-size: 24px;
            font-weight: bold;
            margin-bottom: 15px;
        }

        input {
            width: 90%;
            padding: 12px;
            margin: 10px 0;
            border-radius: 5px;
            border: none;
            outline: none;
            background-color: #1c1c1c;
            color: white;
        }

        button {
            padding: 12px 25px;
            cursor: pointer;
            border: none;
            border-radius: 5px;
            background: #ff4b5c;
            color: white;
            font-size: 16px;
            transition: 0.3s;
        }

        button:hover {
            background: #ff1e3c;
        }

        video {
            width: 100%;
            max-width: 500px;
            margin-top: 20px;
            display: none;
            border-radius: 10px;
        }

        .download-options {
            margin-top: 20px;
            display: none;
        }

        .download-options button {
            margin: 5px;
            padding: 10px 15px;
            font-size: 14px;
            background: #28a745;
            border-radius: 5px;
        }

        .download-options button:hover {
            background: #218838;
        }

        .credit {
            margin-top: 30px;
            padding: 15px;
            background: rgba(255, 255, 255, 0.2);
            border-radius: 8px;
        }

        .credit p {
            margin: 5px 0;
            font-size: 14px;
        }

        .credit a {
            color: #ffcc00;
            font-weight: bold;
            text-decoration: none;
        }

        .credit a:hover {
            text-decoration: underline;
        }
    </style>
</head>
<body>
    <!-- Moving Lines in Background -->
    <div class="line line1" style="top: 30%; left: 10%;"></div>
    <div class="line line2" style="top: 40%; left: 20%;"></div>
    <div class="line line3" style="top: 60%; left: 30%;"></div>
    <div class="line line4" style="top: 20%; left: 50%;"></div>
    <div class="line line5" style="top: 50%; left: 70%;"></div>
    <div class="line line6" style="top: 60%; left: 90%;"></div>
    <div class="line line7" style="top: 20%; left: 40%;"></div>

    <div class="container">
        <h2>TikTok ভিডিও ডাউনলোডার (No Watermark)</h2>
        <input type="text" id="videoUrl" placeholder="এখানে TikTok ভিডিও লিংক দিন...">
        <button onclick="fetchVideo()">ডাউনলোড</button>
        <video id="preview" controls></video>
        <div class="download-options" id="downloadOptions">
            <h3>📥 ভিডিও / অডিও কোয়ালিটি নির্বাচন করুন</h3>
            <button id="download720p">720p MP4</button>
            <button id="download1080p">1080p MP4</button>
            <button id="downloadMp3">🎵 MP3 অডিও</button>
        </div>
    </div>

    <div class="credit">
        <h3>🚀 Developed by <span style="color: #ffcc00;">Shohag Vai</span></h3>
        <p>📧 Email: <a href="mailto:Shohagvaiiofc@gmail.com">Shohagvaiiofc@gmail.com</a></p>
        <p>💬 Telegram: <a href="https://t.me/SHOHAG_VAII" target="_blank">@SHOHAG_VAII</a></p>
    </div>

    <script>
        async function fetchVideo() {
            let url = document.getElementById('videoUrl').value;
            if (!url) {
                alert('অনুগ্রহ করে একটি TikTok ভিডিও লিংক দিন!');
                return;
            }

            if (!url.includes("tiktok.com")) {
                alert('অনুগ্রহ করে সঠিক TikTok লিংক দিন!');
                return;
            }

            let apiUrl = `https://tikwm.com/api/?url=${encodeURIComponent(url)}`;

            try {
                let response = await fetch(apiUrl);
                let data = await response.json();

                if (data && data.data) {
                    let videoSrc720p = data.data.play;
                    let videoSrc1080p = data.data.hdplay || data.data.play;
                    let audioSrc = data.data.music;

                    let preview = document.getElementById('preview');
                    let downloadOptions = document.getElementById('downloadOptions');

                    preview.src = videoSrc720p;
                    preview.style.display = 'block';
                    downloadOptions.style.display = 'block';

                    document.getElementById('download720p').onclick = function () {
                        window.location.href = videoSrc720p;
                    };
                    document.getElementById('download1080p').onclick = function () {
                        window.location.href = videoSrc1080p;
                    };
                    document.getElementById('downloadMp3').onclick = function () {
                        window.location.href = audioSrc;
                    };
                } else {
                    alert('ভিডিও ডাউনলোড করতে ব্যর্থ! অনুগ্রহ করে লিংক চেক করুন।');
                }
            } catch (error) {
                alert('ভুল হয়েছে! অনুগ্রহ করে আবার চেষ্টা করুন।');
            }
        }
    </script>
</body>
</html>
