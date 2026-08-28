<!DOCTYPE html>
<html lang="hi">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">

<title>Sorry ❤️</title>

<style>
*{
    box-sizing:border-box;
}

body{
    margin:0;
    height:100vh;
    overflow:hidden;
    font-family:Arial,sans-serif;
    display:flex;
    justify-content:center;
    align-items:center;
    background:linear-gradient(135deg,#ffd1e3,#fff1f7);
}

/* Floating hearts */
.heart{
    position:fixed;
    bottom:-30px;
    font-size:25px;
    animation:float 5s linear infinite;
    pointer-events:none;
}

@keyframes float{
    0%{
        transform:translateY(0) rotate(0deg);
        opacity:1;
    }
    100%{
        transform:translateY(-110vh) rotate(360deg);
        opacity:0;
    }
}

/* Cute decorations */
.teddy{
    position:fixed;
    font-size:65px;
    opacity:.9;
}

.t1{
    top:25px;
    left:20px;
}

.t2{
    bottom:20px;
    right:20px;
}

.box{
    width:90%;
    max-width:400px;
    padding:32px 20px;
    text-align:center;
    background:rgba(255,255,255,.94);
    border-radius:30px;
    box-shadow:0 12px 35px rgba(0,0,0,.15);
    z-index:10;
}

h1{
    color:#ff3b70;
    font-size:29px;
    margin-bottom:15px;
}

p{
    color:#555;
    font-size:19px;
    line-height:1.5;
}

.sorry{
    font-size:38px;
    animation:pulse 1.2s infinite;
}

@keyframes pulse{
    50%{
        transform:scale(1.15);
    }
}

button{
    border:0;
    padding:14px 27px;
    margin:10px;
    border-radius:30px;
    font-size:17px;
    cursor:pointer;
}

#yes{
    background:#ff3b70;
    color:white;
    box-shadow:0 5px 15px rgba(255,59,112,.3);
}

#no{
    background:#eee;
    color:#333;
}

#message{
    display:none;
    color:#ff3b70;
    font-size:20px;
    font-weight:bold;
    line-height:1.6;
}

/* Hearts after YES */
.bigheart{
    position:fixed;
    font-size:35px;
    animation:explode 2s ease-out forwards;
    pointer-events:none;
    z-index:20;
}

@keyframes explode{
    0%{
        transform:scale(.5);
        opacity:1;
    }
    100%{
        transform:translate(
            calc((var(--x) - 50vw)),
            calc((var(--y) - 50vh))
        ) scale(1.5);
        opacity:0;
    }
}
</style>
</head>

<body>

<!-- Cute pookie decorations -->
<div class="teddy t1">🧸💗</div>
<div class="teddy t2">🧸💕</div>

<div class="box">

    <div class="sorry">🥺💗</div>

    <h1>Ek chhota sa sawaal ❤️</h1>

    <p id="question">
        Kya tum mujhse love karti ho? 🥺❤️
    </p>

    <button id="yes" onclick="yesClicked()">
        Haan ❤️
    </button>

    <button id="no" onclick="noClicked()">
        Nahi 😤
    </button>

    <div id="message">
        Mujhe pata tha 😭❤️
        <br><br>
        Sorry agar tum mujhse gussa ho 🥺
        <br>
        Ab maan bhi jao na 💗
        <br><br>
        I Love You ❤️🧸
    </div>

</div>

<script>

/* Moving NO button */
function noClicked(){

    const no=document.getElementById("no");

    const maxX=window.innerWidth-no.offsetWidth-20;
    const maxY=window.innerHeight-no.offsetHeight-20;

    const x=Math.max(10,Math.random()*maxX);
    const y=Math.max(10,Math.random()*maxY);

    no.style.position="fixed";
    no.style.left=x+"px";
    no.style.top=y+"px";
}

/* YES button */
function yesClicked(){

    document.getElementById("question").style.display="none";
    document.getElementById("yes").style.display="none";
    document.getElementById("no").style.display="none";
    document.querySelector(".sorry").style.display="none";

    document.getElementById("message").style.display="block";

    createBigHearts();
}

/* Floating hearts */
function createHeart(){

    const heart=document.createElement("div");

    heart.className="heart";

    const hearts=["❤️","💗","💕","💖","💓","🩷"];

    heart.innerHTML=
        hearts[Math.floor(Math.random()*hearts.length)];

    heart.style.left=Math.random()*100+"vw";
    heart.style.animationDuration=
        (3+Math.random()*4)+"s";

    document.body.appendChild(heart);

    setTimeout(()=>{
        heart.remove();
    },7000);
}

setInterval(createHeart,500);


/* YES के बाद बहुत सारे hearts */
function createBigHearts(){

    for(let i=0;i<35;i++){

        const heart=document.createElement("div");

        heart.className="bigheart";
        heart.innerHTML="❤️";

        heart.style.left="50%";
        heart.style.top="50%";

        heart.style.setProperty(
            "--x",
            Math.random()*100+"vw"
        );

        heart.style.setProperty(
            "--y",
            Math.random()*100+"vh"
        );

        document.body.appendChild(heart);

        setTimeout(()=>{
            heart.remove();
        },2000);
    }
}

</script>

</body>
</html>
