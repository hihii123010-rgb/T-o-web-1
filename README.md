# T-o-web-1
<!DOCTYPE html>
<html lang="vi">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>MOON SIGNATURE COFFEE</title>

<link href="https://fonts.googleapis.com/css2?family=Playfair+Display:wght@600;700&family=Inter:wght@300;400;500&display=swap" rel="stylesheet">

<style>
:root{
--dark:#111;
--gold:#c6a769;
--light:#f8f6f2;
}

*{margin:0;padding:0;box-sizing:border-box;}
body{
font-family:'Inter',sans-serif;
background:var(--light);
color:#222;
overflow-x:hidden;
}

/* HEADER */
header{
position:fixed;
width:100%;
display:flex;
justify-content:space-between;
align-items:center;
padding:20px 60px;
background:rgba(0,0,0,0.4);
backdrop-filter:blur(8px);
z-index:1000;
transition:0.4s;
}
header.scrolled{background:#111;}

.logo{
color:white;
font-family:'Playfair Display',serif;
letter-spacing:2px;
}
nav a{
color:white;
margin-left:25px;
text-decoration:none;
position:relative;
}
nav a::after{
content:'';
position:absolute;
bottom:-5px;
left:0;
width:0;
height:1px;
background:var(--gold);
transition:0.3s;
}
nav a:hover::after{width:100%;}

/* HERO */
.hero{
height:100vh;
position:relative;
overflow:hidden;
}
.slide{
position:absolute;
width:100%;
height:100%;
background-size:cover;
background-position:center;
opacity:0;
transition:opacity 1.5s ease;
}
.slide.active{opacity:1;}

.hero-content{
position:absolute;
top:50%;
left:50%;
transform:translate(-50%,-50%);
text-align:center;
color:white;
}
.hero-content h1{
font-family:'Playfair Display',serif;
font-size:60px;
margin-bottom:20px;
}
.hero-content button{
padding:14px 30px;
background:var(--gold);
border:none;
cursor:pointer;
transition:0.3s;
}
.hero-content button:hover{background:white;}

/* SECTION */
section{
padding:100px 80px;
text-align:center;
}

.title{
font-family:'Playfair Display',serif;
font-size:40px;
margin-bottom:50px;
}

/* MENU */
.menu-grid{
display:grid;
grid-template-columns:repeat(auto-fit,minmax(250px,1fr));
gap:40px;
}
.card{
background:white;
border-radius:15px;
overflow:hidden;
box-shadow:0 10px 25px rgba(0,0,0,0.1);
transition:0.4s;
}
.card img{
width:100%;
height:250px;
object-fit:cover;
}
.card:hover{transform:translateY(-12px);}
.price{
color:var(--gold);
font-weight:600;
margin-bottom:20px;
}

/* COUNTER */
.stats{
display:flex;
justify-content:space-around;
background:#111;
color:white;
padding:80px 20px;
}
.stat h2{
font-size:40px;
color:var(--gold);
}

/* FORM */
form{
max-width:400px;
margin:auto;
display:flex;
flex-direction:column;
gap:15px;
}
input,textarea{
padding:12px;
border-radius:8px;
border:1px solid #ccc;
}
button.submit{
background:#111;
color:white;
padding:12px;
border:none;
cursor:pointer;
}
button.submit:hover{background:var(--gold);color:black;}

/* FOOTER */
footer{
background:#111;
color:white;
padding:40px;
}

/* SCROLL REVEAL */
.reveal{
opacity:0;
transform:translateY(60px);
transition:1s ease;
}
.reveal.active{
opacity:1;
transform:translateY(0);
}

/* RESPONSIVE */
@media(max-width:768px){
header{padding:20px;}
section{padding:80px 30px;}
.hero-content h1{font-size:40px;}
.stats{flex-direction:column;gap:30px;}
}
</style>
</head>

<body>

<header id="header">
<div class="logo">MOON SIGNATURE</div>
<nav>
<a href="#menu">Menu</a>
<a href="#contact">Contact</a>
</nav>
</header>

<div class="hero">
<div class="slide active" style="background-image:url('https://images.unsplash.com/photo-1509042239860-f550ce710b93');"></div>
<div class="slide" style="background-image:url('https://images.unsplash.com/photo-1511920170033-f8396924c348');"></div>

<div class="hero-content">
<h1>Premium Coffee Experience</h1>
<button onclick="document.getElementById('menu').scrollIntoView()">Explore</button>
</div>
</div>

<section id="menu">
<h2 class="title reveal">Signature Menu</h2>
<div class="menu-grid">
<div class="card reveal">
<img src="https://images.unsplash.com/photo-1511920170033-f8396924c348">
<h3>Espresso Gold</h3>
<p class="price">55.000đ</p>
</div>
<div class="card reveal">
<img src="https://images.unsplash.com/photo-1509042239860-f550ce710b93">
<h3>Latte Signature</h3>
<p class="price">65.000đ</p>
</div>
<div class="card reveal">
<img src="https://images.unsplash.com/photo-1495474472287-4d71bcdd2085">
<h3>Cold Brew Premium</h3>
<p class="price">70.000đ</p>
</div>
</div>
</section>

<section class="stats reveal">
<div class="stat">
<h2 class="counter" data-target="1500">0</h2>
<p>Khách hàng</p>
</div>
<div class="stat">
<h2 class="counter" data-target="12">0</h2>
<p>Chi nhánh</p>
</div>
<div class="stat">
<h2 class="counter" data-target="8">0</h2>
<p>Năm kinh nghiệm</p>
</div>
</section>

<section id="contact">
<h2 class="title reveal">Liên Hệ</h2>
<form class="reveal" onsubmit="event.preventDefault(); alert('Đã gửi thành công!')">
<input type="text" placeholder="Tên của bạn" required>
<input type="email" placeholder="Email" required>
<textarea rows="4" placeholder="Tin nhắn"></textarea>
<button class="submit">Gửi</button>
</form>
</section>

<footer>
© 2026 Moon Signature Coffee
</footer>

<script>
/* HEADER SCROLL */
window.addEventListener("scroll",()=>{
document.getElementById("header").classList.toggle("scrolled",window.scrollY>50);
});

/* SLIDER */
let slides=document.querySelectorAll(".slide");
let index=0;
setInterval(()=>{
slides[index].classList.remove("active");
index=(index+1)%slides.length;
slides[index].classList.add("active");
},4000);

/* SCROLL REVEAL */
function reveal(){
let reveals=document.querySelectorAll(".reveal");
for(let el of reveals){
let windowHeight=window.innerHeight;
let elementTop=el.getBoundingClientRect().top;
if(elementTop < windowHeight - 100){
el.classList.add("active");
}
}
}
window.addEventListener("scroll",reveal);

/* COUNTER */
let counters=document.querySelectorAll(".counter");
counters.forEach(counter=>{
let update=()=>{
let target=+counter.getAttribute("data-target");
let current=+counter.innerText;
let increment=target/100;
if(current<target){
counter.innerText=Math.ceil(current+increment);
setTimeout(update,20);
}else{
counter.innerText=target;
}
}
update();
});
</script>

</body>
</html>
