---
layout: page
title: About
---

![me](/favicon.ico){: style="border-radius: 50%;width: 64px;height: 64px;"}

<style>
  .animated-title {
    font-size: 2rem;
    font-weight: bold;
    margin: 2rem 0;
  }
  
  .animated-text {
    color: #667eea;
    display: inline-block;
    min-width: 300px;
    animation: fadeIn 1s;
  }
  
  @keyframes fadeIn {
    from {
      opacity: 0;
      transform: translateY(-10px);
    }
    to {
      opacity: 1;
      transform: translateY(0);
    }
  }
</style>

<h2 class="animated-title">I'm <span class="animated-text" id="animatedText">Ertugrul</span></h2>

<script>
  (function() {
    const texts = ['Ertugrul', 'Software Engineer', "Full Stack Developer",'Laravel Developer', 'VueJS Developer', 'ITF&TTF Tennis Player', 'Tennis Trainer', 'Amateur Radio Operator', 'Amateur Sailor'];
    let currentIndex = 0;
    const element = document.getElementById('animatedText');
    
    function changeText() {
      element.style.animation = 'none';
      setTimeout(() => {
        currentIndex = (currentIndex + 1) % texts.length;
        element.textContent = texts[currentIndex];
        element.style.animation = 'fadeIn 1s';
      }, 50);
    }
    
    setInterval(changeText, 1000);
  })();
</script>

## Summary

Software Engineer with 6+ years of experience, including 4+ years in professional software teams. Specialized in building scalable web applications using Laravel and Vue.js. Strong experience in designing RESTful APIs, microservices-based systems, and maintainable frontend architectures, with a focus on performance, code quality, and ownership. I like social activities, smart home systems, playing tennis and reading books.

## Connect 

- 📧 [akcaertugrulgazi@gmail.com](mailto:akcaertugrulgazi@gmail.com)  
- 💼 [linkedin.com/in/ertugrulakca](https://www.linkedin.com/in/ertugrulakca/)  
- 💻 [github.com/ertugrulakca](https://github.com/ertugrulakca)  
