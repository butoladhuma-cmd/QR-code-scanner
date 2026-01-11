<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<title>QR Code Scanner</title>

<script src="https://unpkg.com/html5-qrcode"></script>

<style>
body {
  font-family: Arial, sans-serif;
  background: #121212;
  color: white;
  text-align: center;
  padding: 20px;
}

#reader {
  width: 300px;
  margin: auto;
  border-radius: 10px;
}

.result {
  margin-top: 20px;
  padding: 10px;
  background: #1f1f1f;
  border-radius: 8px;
  word-break: break-all;
}

button {
  margin-top: 15px;
  padding: 10px 20px;
  font-size: 16px;
  border: none;
  border-radius: 8px;
  background: #00c853;
  color: white;
  cursor: pointer;
}
</style>
</head>

<body>

<h2>📷 QR Code Scanner</h2>

<div id="reader"></div>

<div class="result" id="result">Scan result will appear here</div>

<button onclick="startScanner()">Start Scanner</button>

<script>
function startScanner() {
  const html5QrCode = new Html5Qrcode("reader");

  html5QrCode.start(
    { facingMode: "environment" },
    {
      fps: 10,
      qrbox: 250
    },
    (decodedText) => {
      document.getElementById("result").innerText = decodedText;
      html5QrCode.stop();
