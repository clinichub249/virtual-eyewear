<!DOCTYPE html>
<html>
<head>
<meta charset="utf-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Clinic Virtual Eyewear Fitting</title>

<style>
body {
    font-family: Arial, sans-serif;
    margin: 0;
    background: #f2f7fb;
}

.header {
    background: #1e88e5;
    color: white;
    padding: 20px;
    text-align: center;
}

.container {
    padding: 15px;
}

.camera-box {
    position: relative;
    width: 100%;
    max-width: 400px;
    aspect-ratio: 3/4;
    margin: auto;
    background: #ddd;
    border-radius: 20px;
    overflow: hidden;
}

video {
    width: 100%;
    height: 100%;
    object-fit: cover;
}

.overlay {
    position: absolute;
    top: 42%;
    left: 50%;
    transform: translate(-50%, -50%);
    font-size: 80px;
    display: none;
}

.frames {
    display: flex;
    gap: 10px;
    overflow: auto;
    margin-top: 15px;
}

.frame-btn {
    border: none;
    padding: 10px 15px;
    border-radius: 12px;
    background: white;
    box-shadow: 0 2px 6px rgba(0,0,0,0.15);
}

.action {
    margin-top: 20px;
    display: flex;
    gap: 10px;
}

.action button {
    flex: 1;
    padding: 15px;
    border: none;
    border-radius: 12px;
    color: white;
    font-size: 16px;
}

.save {
    background: #ff9800;
}

.select {
    background: #4caf50;
}
</style>
</head>

<body>

<div class="header">
    <h2>Virtual Eyewear Fitting</h2>
    <p>Try frames from our clinic</p>
</div>

<div class="container">

    <div class="camera-box">
        <video id="video" autoplay playsinline></video>

        <div class="overlay" id="overlay">
            👓
        </div>
    </div>

    <h3>Choose a Frame</h3>

    <div class="frames">
        <button class="frame-btn" onclick="showFrame('👓')">
            Classic
        </button>

        <button class="frame-btn" onclick="showFrame('🕶️')">
            Aviator
        </button>

        <button class="frame-btn" onclick="showFrame('🥽')">
            Kids
        </button>
    </div>

    <div class="action">
        <button class="save">
            Save
        </button>

        <button class="select">
            Select Frame
        </button>
    </div>

</div>

<script>

navigator.mediaDevices.getUserMedia({
    video: {
        facingMode: "user"
    }
})
.then(stream => {
    document.getElementById("video").srcObject = stream;
})
.catch(() => {
    alert("Camera access unavailable.");
});

function showFrame(frame) {
    const overlay = document.getElementById("overlay");

    overlay.textContent = frame;

    overlay.style.display = "block";
}

</script>

</body>
</html>
