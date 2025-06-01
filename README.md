<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0"/>
  <title>Intro Presentation</title>
  <style>
    body {
      margin: 0;
      font-family: Arial, sans-serif;
      background-color: #f4f4f4;
      color: #333;
      display: flex;
      flex-direction: column;
      align-items: center;
      justify-content: center;
      height: 100vh;
      text-align: center;
    }
    .slide {
      max-width: 600px;
      padding: 30px;
      background: white;
      border-radius: 20px;
      box-shadow: 0 4px 12px rgba(0,0,0,0.2);
      display: none;
      flex-direction: column;
      align-items: center;
    }
    .slide.active {
      display: flex;
    }
    .avatar {
      width: 100px;
      height: 100px;
      margin-bottom: 20px;
      background: url('https://i.imgur.com/N7rlQYt.png') no-repeat center/cover;
      border-radius: 50%;
    }
    button {
      margin-top: 20px;
      padding: 10px 20px;
      font-size: 1rem;
      border: none;
      background-color: #007bff;
      color: white;
      border-radius: 8px;
      cursor: pointer;
    }
    button:hover {
      background-color: #0056b3;
    }
  </style>
</head>
<body>

  <div class="slide active">
    <div class="avatar"></div>
    <h2>Hi, I'm [Your Name]!</h2>
    <p>Thanks for checking out my intro. I'm excited to be part of this course.</p>
  </div>

  <div class="slide">
    <div class="avatar"></div>
    <h2>About Me</h2>
    <p>I'm currently a student passionate about learning new skills and working on creative projects.</p>
  </div>

  <div class="slide">
    <div class="avatar"></div>
    <h2>Why This Course?</h2>
    <p>I joined this course to improve my knowledge and explore new career opportunities.</p>
  </div>

  <div class="slide">
    <div class="avatar"></div>
    <h2>My Goal</h2>
    <p>One of my goals is to complete a strong portfolio and apply these skills in real-world projects.</p>
  </div>

  <div class="slide">
    <div class="avatar"></div>
    <h2>Thanks for Watching!</h2>
    <p>Looking forward to collaborating with everyone in this course.</p>
  </div>

  <button onclick="nextSlide()">Next</button>

  <script>
    const slides = document.querySelectorAll('.slide');
    let currentSlide = 0;

    const speechTexts = [
      "Hi, I'm [Your Name]! Thanks for checking out my intro. I'm excited to be part of this course.",
      "I'm currently a student passionate about learning new skills and working on creative projects.",
      "I joined this course to improve my knowledge and explore new career opportunities.",
      "One of my goals is to complete a strong portfolio and apply these skills in real-world projects.",
      "Looking forward to collaborating with everyone in this course. Thanks for watching!"
    ];

    function speak(text) {
      if ('speechSynthesis' in window) {
        const msg = new SpeechSynthesisUtterance(text);
        const voices = window.speechSynthesis.getVoices();
        msg.voice = voices.find(v => v.name.includes("Male")) || voices[0];
        msg.rate = 1;
        speechSynthesis.speak(msg);
      }
    }

    function nextSlide() {
      slides[currentSlide].classList.remove('active');
      currentSlide++;
      if (currentSlide < slides.length) {
        slides[currentSlide].classList.add('active');
        speak(speechTexts[currentSlide]);
      } else {
        document.querySelector('button').style.display = 'none';
      }
    }

    // Speak the first slide on load
    window.onload = () => {
      speak(speechTexts[0]);
    };
  </script>

</body>
</html>
