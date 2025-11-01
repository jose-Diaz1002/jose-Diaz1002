<!doctype html>
<html lang="es">
<head>
<meta charset="utf-8" />
<title>Nombre de código</title>
<style>
  html,body{height:100%;margin:0;background:#020;overflow:hidden}
  canvas{display:block}
  #hint{position:fixed;left:12px;top:12px;color:#0f0;font-family:monospace}
</style>
</head>
<body>
<div id="hint">Jose Luis Diaz I — lluvia de código</div>
<canvas id="c"></canvas>
<script>
const phrase = "Jose Luis Diaz I";
const canvas = document.getElementById('c');
const ctx = canvas.getContext('2d');
let W, H;
function resize(){ W = canvas.width = innerWidth; H = canvas.height = innerHeight; prepareTargets(); }
addEventListener('resize', resize);
resize();

// medir y colocar objetivos para cada caracter
let targets = [];
function prepareTargets(){
  ctx.font = "bold 80px monospace";
  const textWidth = ctx.measureText(phrase).width;
  const startX = (W - textWidth) / 2;
  const y = H/2 + 20;
  targets = [];
  let x = startX;
  for (const ch of phrase) {
    const w = ctx.measureText(ch).width;
    targets.push({ch, x: x + w/2, y});
    x += w;
  }
  spawnParticles();
}

let particles = [];
function spawnParticles(){
  particles = [];
  for (let t of targets){
    // varios caracteres por objetivo para efecto
    const count = 6;
    for(let i=0;i<count;i++){
      particles.push({
        ch: randomChar(),
        x: Math.random()*W,
        y: -Math.random()*H,
        vx: (t.x - W/2)*0.0005 + (Math.random()-0.5)*0.6,
        vy: 1 + Math.random()*3,
        tx: t.x + (Math.random()-0.5)*12,
        ty: t.y + (Math.random()-0.5)*6,
        stuck: false,
        speedMult: 0.9 + Math.random()*0.8
      });
    }
  }
}

function randomChar(){
  const s = "01{}[]();<>/\\|!@#$%^&*-_=+abcdefghijklmnopqrstuvwxyzABCDEFGHIJKLMNOPQRSTUVWXYZ";
  return s.charAt(Math.floor(Math.random()*s.length));
}

function step(){
  ctx.fillStyle = "rgba(0,0,0,0.18)";
  ctx.fillRect(0,0,W,H);
  ctx.font = "18px monospace";
  // dibujar partículas
  for (let p of particles){
    if (p.stuck) {
      // cuando está pegado, mostrar el caracter objetivo (parte de la frase)
      ctx.font = "bold 80px monospace";
      ctx.fillStyle = "#6fef8a";
      ctx.fillText(p.ch, p.tx - 24, p.ty + 10);
      ctx.font = "18px monospace";
      continue;
    }
    // física simple
    p.vy += 0.08;
    p.x += p.vx * p.speedMult;
    p.y += p.vy * p.speedMult;
    // si está cerca del objetivo, "snap"
    const dx = p.tx - p.x, dy = p.ty - p.y;
    if (Math.hypot(dx,dy) < 6 || p.y > H+50) {
      p.stuck = true;
      // para que muestre la letra correcta del nombre, tomamos la letra objetivo según posición x más cercana
      p.ch = findTargetChar(p.tx);
    }
    ctx.fillStyle = "#0f0";
    ctx.fillText(p.ch, p.x, p.y);
  }

  // detectar cuando la mayoría esté pegada: si >80% stuck, dibujar la frase final con brillo
  const stuckCount = particles.filter(p=>p.stuck).length;
  if (stuckCount > particles.length * 0.8){
    ctx.font = "bold 96px monospace";
    ctx.fillStyle = "rgba(120,255,160,0.95)";
    const textWidth = ctx.measureText(phrase).width;
    ctx.fillText(phrase, (W-textWidth)/2, H/2 + 32);
    // efecto de pulsación
    ctx.globalCompositeOperation = 'lighter';
    ctx.fillStyle = "rgba(200,255,200,0.06)";
    ctx.fillText(phrase, (W-textWidth)/2 - 2, H/2 + 32 -2);
    ctx.globalCompositeOperation = 'source-over';
  }

  requestAnimationFrame(step);
}

function findTargetChar(tx){
  // aproximar el caracter del objetivo más cercano por X
  let best = targets[0], min = Infinity;
  for (let t of targets){
    const d = Math.abs(t.x - tx);
    if (d < min){ min = d; best = t; }
  }
  return best.ch;
}

step();
</script>
</body>
</html>





<img src="assets/nombre.gif" width="100%">



<div align="center">
  


### Backend Developer | Java & Spring Boot Specialist

[![Portfolio](https://img.shields.io/badge/Portfolio-FF5722?style=for-the-badge&logo=todoist&logoColor=white)](https://josediaz.vercel.app/)
[![GitHub](https://img.shields.io/badge/GitHub-100000?style=for-the-badge&logo=github&logoColor=white)](https://github.com/jose-Diaz1002)
[![Email](https://img.shields.io/badge/Email-D14836?style=for-the-badge&logo=gmail&logoColor=white)](mailto:jldi1002@hotmail.com)
[![Phone](https://img.shields.io/badge/Phone-25D366?style=for-the-badge&logo=whatsapp&logoColor=white)](tel:+34634601040)

<img src="https://readme-typing-svg.herokuapp.com?font=Fira+Code&weight=600&size=28&pause=1000&color=9333EA&center=true&vCenter=true&random=false&width=600&lines=Backend+Developer;Java+%26+Spring+Boot+Expert;Building+Scalable+APIs;Passionate+About+Clean+Code" alt="Typing SVG" />

</div>

---

## 🚀 Sobre Mí

Profesional en transición al desarrollo backend tras **cuatro años de formación intensiva**. Especializado en **Java y Spring Framework**, con certificaciones en programación de sistemas informáticos y desarrollo web.

Mi reconversión profesional refleja mi **pasión genuina por la tecnología** y mi compromiso con el aprendizaje continuo y las buenas prácticas de desarrollo.

\`\`\`java
public class Developer {
    private String name = "Jose Luis Diaz";
    private String role = "Backend Developer";
    private String[] languages = {"Java", "SQL", "JavaScript"};
    private String location = "España";
    
    public String getCurrentFocus() {
        return "Building scalable backend systems with Spring Boot";
    }
    
    public boolean isOpenToWork() {
        return true;
    }
}
\`\`\`

---

## 💻 Tech Stack

### Backend Development
![Java](https://img.shields.io/badge/Java-ED8B00?style=for-the-badge&logo=openjdk&logoColor=white)
![Spring Boot](https://img.shields.io/badge/Spring_Boot-6DB33F?style=for-the-badge&logo=spring-boot&logoColor=white)
![Spring](https://img.shields.io/badge/Spring-6DB33F?style=for-the-badge&logo=spring&logoColor=white)
![WebFlux](https://img.shields.io/badge/Spring_WebFlux-6DB33F?style=for-the-badge&logo=spring&logoColor=white)
![Maven](https://img.shields.io/badge/Maven-C71A36?style=for-the-badge&logo=apache-maven&logoColor=white)

### Database & Storage
![PostgreSQL](https://img.shields.io/badge/PostgreSQL-316192?style=for-the-badge&logo=postgresql&logoColor=white)
![MySQL](https://img.shields.io/badge/MySQL-005C84?style=for-the-badge&logo=mysql&logoColor=white)
![MongoDB](https://img.shields.io/badge/MongoDB-4EA94B?style=for-the-badge&logo=mongodb&logoColor=white)

### DevOps & Tools
![Docker](https://img.shields.io/badge/Docker-2496ED?style=for-the-badge&logo=docker&logoColor=white)
![Git](https://img.shields.io/badge/Git-F05032?style=for-the-badge&logo=git&logoColor=white)
![GitHub](https://img.shields.io/badge/GitHub-100000?style=for-the-badge&logo=github&logoColor=white)
![Postman](https://img.shields.io/badge/Postman-FF6C37?style=for-the-badge&logo=postman&logoColor=white)

### Frontend (Complementary)
![React](https://img.shields.io/badge/React-20232A?style=for-the-badge&logo=react&logoColor=61DAFB)
![Vite](https://img.shields.io/badge/Vite-646CFF?style=for-the-badge&logo=vite&logoColor=white)
![JavaScript](https://img.shields.io/badge/JavaScript-F7DF1E?style=for-the-badge&logo=javascript&logoColor=black)

---

## 📊 GitHub Stats

<div align="center">
  
![GitHub Stats](https://github-readme-stats.vercel.app/api?username=jose-Diaz1002&show_icons=true&theme=radical&hide_border=true&bg_color=0D1117&title_color=9333EA&icon_color=9333EA&text_color=FFFFFF)

![Top Languages](https://github-readme-stats.vercel.app/api/top-langs/?username=jose-Diaz1002&layout=compact&theme=radical&hide_border=true&bg_color=0D1117&title_color=9333EA&text_color=FFFFFF)

![GitHub Streak](https://github-readme-streak-stats.herokuapp.com/?user=jose-Diaz1002&theme=radical&hide_border=true&background=0D1117&ring=9333EA&fire=9333EA&currStreakLabel=9333EA)

</div>

---

## 🎯 Featured Projects

### 🐾 [Mascota Virtual - Full Stack App](https://github.com/jose-Diaz1002/MascotaBackend)
API & Dashboard que simula una mascota virtual con sistema completo de gestión.

**Tech Stack:** `Spring Boot` `React` `Vite` `PostgreSQL` `JWT Authentication`

**Features:**
- 🔐 Sistema de autenticación y autorización
- 📊 Dashboard interactivo para gestión de mascota
- 🎮 Lógica de negocio compleja con estados de mascota
- 💾 Persistencia de datos con JPA/Hibernate

[![Backend Repo](https://img.shields.io/badge/Backend-Repository-9333EA?style=flat-square&logo=github)](https://github.com/jose-Diaz1002/MascotaBackend)
[![Frontend Repo](https://img.shields.io/badge/Frontend-Repository-9333EA?style=flat-square&logo=github)](https://github.com/jose-Diaz1002/mascota-frontend)

---

### 🃏 [Blackjack WebFlux - Reactive API](https://github.com/jose-Diaz1002/5-01-Webflux)
API de Blackjack totalmente funcional y no bloqueante usando programación reactiva.

**Tech Stack:** `Spring Boot 3.x` `Spring WebFlux` `Reactor` `MongoDB`

**Features:**
-
