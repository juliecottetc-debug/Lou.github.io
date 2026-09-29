<!DOCTYPE html>
<html lang="fr">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Invitation - Lady Whistledown</title>

<link href="https://fonts.googleapis.com/css2?family=Cinzel:wght@400;600&family=Cormorant+Garamond:wght@300;400;600&display=swap" rel="stylesheet">

<style>
*{
   margin:0;
   padding:0;
   box-sizing:border-box;
}

body{
   overflow:hidden;
   background:#3f2325;
   display:flex;
   justify-content:center;
   align-items:center;
   height:100vh;
   font-family:'Cormorant Garamond',serif;
}

/* Fond */

body::before{
   content:"";
   position:absolute;
   inset:0;
   background:
   radial-gradient(circle at top,#6d4046,#2b1718 70%);
   transition:transform 2s ease;
}

.open-bg::before{ 
transform:scale(1.08); }

/* Instruction */

.tap{
   position:absolute;
   bottom:40px;
   color:white;
   letter-spacing:2px;
   font-size:22px;
   animation:blink 1.8s infinite;
}

@keyframes blink{
50%{opacity:.3;}
}

/* Enveloppe */

.envelope{ 
position:relative; 
width:420px; 
height:280px; 
cursor:pointer; 
transition:1s; 
overflow:visible; 
}

.back{
   position:absolute;
   width:100%;
   height:100%;
   background:#e8d9bc;
   border-radius:4px;
}

.front{
   position:absolute;
   width:100%;
   height:100%;
   overflow:hidden;
}

.front:before{
content:"";
position:absolute;
border-left:210px solid transparent;
border-right:210px solid transparent;
border-bottom:140px solid #d9c5a1;
bottom:0;
}

.flap{
position:absolute;
transform-origin:top;
width:0;
height:0;
border-left:210px solid transparent;
border-right:210px solid transparent;
border-top:145px solid #f2e6cb;
transition:1.5s;
z-index:4;
}

.seal{
position:absolute;
left:50%;
top:125px;
transform:translateX(-50%);
width:72px;
height:72px;
background:#7a1e25;
border-radius:50%;
display:flex;
justify-content:center;
align-items:center;
color:#eec9a4;
font-size:28px;
font-family:'Cinzel',serif;
z-index:5;
transition:1s;
box-shadow:0 0 20px rgba(0,0,0,.4);
}

/* Lettre */

.letter{ 
position:absolute; 
left:50%; 
top:20px; 
width:370px; 
height:500px; 
background:#f7efd8; 
padding:35px; 
overflow:auto; 
border-radius:3px; 
box-shadow:0 10px 35px rgba(0,0,0,.4); 
transform-origin:bottom; 
transform:translate(-50%,430px) scale(.95); 
opacity:0; 
transition: transform 2s ease, opacity .8s ease; 
z-index:1; 
}

.letter h1{
font-family:'Cinzel',serif;
text-align:center;
font-size:18px;
margin-bottom:25px;
}

.letter p{
font-size:23px;
line-height:1.45;
margin-bottom:18px;
}

.signature{
text-align:right;
margin-top:30px;
font-style:italic;
font-size:30px;
}

/* Animation */

.open .flap{
transform:rotateX(180deg);
}

.open .seal{ 
opacity:0; 
transform:translateX(-50%) scale(.4); 
} 

.open .front, 
.open .back, 
.open .flap{ 
opacity:0; 
transition:opacity .8s ease; 
pointer-events:none; 
} 

.open .letter{ 
opacity:1; 
transform:translate(-50%,-90px) scale(1); 
}

.open .tap{
display:none;
}

</style>

</head>

<body>

<div class="tap">
Touchez l'écran pour ouvrir la lettre
</div>

<div class="envelope" id="env">

<div class="letter" id="letter">

<h1>LES CHRONIQUES DE LADY WHISTLEDOWN</h1>

<p><strong>Très chers amis lecteurs,</strong></p>

<p>
Il semblerait que la prochaine saison des mondanités
s'annonce déjà des plus prometteuses.
Une jeune demoiselle de notre estimée société
s'apprête à franchir un cap que nul ne saurait ignorer :
celui de son dix-huitième anniversaire.
</p>

<p>
Mademoiselle <strong>Lou-Anne</strong> aura l'honneur
de recevoir ses invités lors d'un bal qui,
à n'en point douter,
fera naître bien des conversations.
</p>

<p style="text-align:center;">
<b>Samedi 1er mai 2027</b><br>
19 heures<br>
Salle des fêtes de Béthisy-Saint-Pierre
</p>

<p style="text-align:center;">
Une tenue de bal sera naturellement de mise.
</p>

<p style="text-align:center;">
Réponse souhaitée avant le : 30 janvier 2027
_____________
</p>

<p>
Lady Whistledown ne doute pas un seul instant que cette
réception alimentera bien des conversations...
</p>

<div class="signature">
Lady Whistledown
</div>

</div>

<div class="back"></div>
<div class="front"></div>
<div class="flap"></div>
<div class="seal">LW</div>

</div>

<script>

const env=document.getElementById("env");

function openEnvelope(){ 
env.classList.add("open"); 
document.body.classList.add("open-bg"); 
document.querySelector(".tap").style.opacity = 0;
env.removeEventListener("click",openEnvelope); 
env.removeEventListener("touchstart",openEnvelope); 
}

env.addEventListener("click",openEnvelope);

env.addEventListener("touchstart",openEnvelope);

</script>

</body>
</html>
