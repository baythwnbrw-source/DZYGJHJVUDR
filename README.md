<!DOCTYPE html>
<html lang="ar" dir="rtl">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>تحميل فيديو تيك توك المتقدم</title>
<style>
body {
    font-family: Arial, sans-serif;
    margin:0; padding:0;
    background: linear-gradient(to bottom, #f0f0f0, #ffffff);
    text-align: center;
}
header {
    background-color: #69C9D0;
    color: white;
    padding: 20px;
    font-size: 24px;
    font-weight: bold;
}
main {
    margin-top: 30px;
    padding: 0 10px;
}
input[type="text"], textarea {
    width: 80%;
    padding: 12px;
    font-size: 16px;
    border-radius: 8px;
    border: 1px solid #ccc;
    margin-bottom: 15px;
    resize: none;
}
button {
    padding: 12px 25px;
    font-size: 16px;
    background-color: #69C9D0;
    border: none;
    border-radius: 8px;
    color: white;
    cursor: pointer;
    margin: 5px;
}
button:hover {
    background-color: #3da1a5;
}
a.download-link {
    display: block;
    margin-top: 10px;
    text-decoration: none;
    color: white;
    background-color: #1977f2;
    padding: 10px 20px;
    border-radius: 8px;
    font-weight: bold;
}
a.download-link:hover {
    background-color: #145dbf;
}
video {
    max-width: 80%;
    margin-top: 15px;
    border-radius: 8px;
}
footer {
    margin-top: 50px;
    background-color: #69C9D0;
    color: white;
    padding: 15px;
}
.notification {
    background-color: #1977f2;
    color: white;
    padding: 10px;
    margin-top: 15px;
    border-radius: 8px;
    display: none;
}
</style>
</head>
<body>

<header>تحميل فيديو تيك توك المتقدم</header>

<main>
<h2>ضع رابط أو عدة روابط فيديوهات (واحد في كل سطر):</h2>
<textarea id="tiktokUrls" rows="4" placeholder="https://www.tiktok.com/..." ></textarea>
<br>
<button onclick="previewVideos()">معاينة الفيديوهات</button>
<button onclick="downloadVideos()">تحميل الفيديوهات</button>

<div id="previewContainer"></div>
<div id="downloadContainer"></div>
<div id="notification" class="notification"></div>
</main>

<footer>
جميع الحقوق محفوظة &copy; 2025
</footer>

<script>
function showNotification(msg) {
    const note = document.getElementById('notification');
    note.textContent = msg;
    note.style.display = "block";
    setTimeout(() => { note.style.display = "none"; }, 4000);
}

function previewVideos() {
    const urls = document.getElementById('tiktokUrls').value.trim().split('\n');
    const container = document.getElementById('previewContainer');
    container.innerHTML = '';
    if(urls.length === 0 || urls[0]===''){
        alert("ضع رابط فيديو تيك توك أولاً!");
        return;
    }
    urls.forEach(url => {
        const apiUrl = "https://api.tiktokdownloader.com/download?url=" + encodeURIComponent(url);
        const videoEl = document.createElement('video');
        videoEl.src = apiUrl;
        videoEl.controls = true;
        container.appendChild(videoEl);
    });
    showNotification("تمت معاينة الفيديوهات!");
}

function downloadVideos() {
    const urls = document.getElementById('tiktokUrls').value.trim().split('\n');
    const container = document.getElementById('downloadContainer');
    container.innerHTML = '';
    if(urls.length === 0 || urls[0]===''){
        alert("ضع رابط فيديو تيك توك أولاً!");
        return;
    }
    urls.forEach((url, index) => {
        const apiUrl = "https://api.tiktokdownloader.com/download?url=" + encodeURIComponent(url);
        const link = document.createElement('a');
        link.href = apiUrl;
        link.download = "tiktok_video_" + (index+1) + ".mp4";
        link.className = "download-link";
        link.textContent = "⬇️ تحميل الفيديو رقم " + (index+1);
        container.appendChild(link);
    });
    showNotification("روابط التحميل جاهزة!");
}
</script>

</body>
</html>
