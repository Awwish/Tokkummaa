<!DOCTYPE html>
<html lang="om">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Awish Website Full System</title>
<style>
*{margin:0;padding:0;box-sizing:border-box;font-family:Arial,Helvetica,sans-serif;}
body{background:#f4f6f8;color:#333;}
header{background:linear-gradient(to right,#004d4d,#00a8a8);color:white;padding:25px;text-align:center;}
nav{display:flex;justify-content:center;background:#003333;flex-wrap:wrap;}
nav a{color:white;padding:15px 20px;text-decoration:none;font-weight:bold;}
nav a:hover{background:#00a8a8;}
.hero{background:white;padding:70px 20px;text-align:center;}
.hero h1{font-size:2.5em;margin-bottom:15px;}
.hero p{font-size:1.1em;margin-bottom:25px;}
.hero button{padding:14px 30px;background:#004d4d;color:white;border:none;font-size:16px;border-radius:6px;cursor:pointer;}
.hero button:hover{background:#00a8a8;}
section{padding:50px 20px;max-width:1100px;margin:auto;}
.post-form{max-width:600px;margin:auto;background:white;padding:20px;border-radius:8px;box-shadow:0 0 10px rgba(0,0,0,0.1);text-align:center;margin-bottom:40px;}
.post-form textarea,.post-form input{width:100%;padding:10px;margin:5px 0;border-radius:6px;border:1px solid #ccc;}
#postsContainer .post{background:white;padding:20px;margin:20px auto;max-width:600px;border-radius:8px;box-shadow:0 0 10px rgba(0,0,0,0.1);}
#postsContainer img,#postsContainer video{max-width:100%;margin-top:10px;border-radius:6px;}
.share-buttons{margin-top:10px;display:flex;gap:10px;justify-content:center;}
.share-buttons a,.share-buttons button{text-decoration:none;background:#004d4d;color:white;padding:6px 12px;border-radius:4px;border:none;cursor:pointer;}
.share-buttons a:hover,.share-buttons button:hover{background:#00a8a8;}
.post-actions{margin-top:10px;display:flex;gap:10px;justify-content:center;}
.post-actions button{padding:6px 12px;border:none;border-radius:4px;cursor:pointer;}
.post-actions button.edit{background:#ffa500;color:white;}
.post-actions button.edit:hover{background:#ffb733;}
.post-actions button.delete{background:#ff4d4d;color:white;}
.post-actions button.delete:hover{background:#ff6666;}
.post-actions button.like{background:#4CAF50;color:white;}
.post-actions button.like:hover{background:#66BB6A;}
#loginModal,#registerModal{display:flex;justify-content:center;align-items:center;position:fixed;top:0;left:0;width:100%;height:100%;background:rgba(0,0,0,0.7);z-index:1000;}
#loginModal .login-box,#registerModal .login-box{background:white;padding:30px;border-radius:8px;max-width:400px;text-align:center;}
#loginModal input,#registerModal input,#registerModal select{width:80%;padding:10px;margin:10px 0;border-radius:6px;border:1px solid #ccc;}
#loginModal button,#registerModal button{padding:10px 20px;background:#004d4d;color:white;border:none;border-radius:6px;cursor:pointer;}
#loginModal button:hover,#registerModal button:hover{background:#00a8a8;}
#adminDashboard{display:none;margin-top:30px;}
#adminDashboard table{width:100%;border-collapse:collapse;margin-top:15px;}
#adminDashboard th,#adminDashboard td{border:1px solid #ccc;padding:8px;}
footer{background:#003333;color:white;text-align:center;padding:20px;margin-top:40px;}
</style>
</head>
<body>

<header>
<h1>Awish Website</h1>
<p>Member & Admin System with Posts</p>
</header>

<nav>
<a href="#home">Home</a>
<a href="#posts">Posts</a>
<a href="#adminDashboard">Admin Dashboard</a>
<a href="#contact">Contact</a>
</nav>

<div class="hero" id="home">
<h1>Baga Nagaan Dhuftan</h1>
<p>Member registration, admin dashboard, posts & share</p>
<button onclick="welcome()">Eegaluu</button>
</div>

<section id="posts">
<h2>Postoota Haaraa</h2>
<div class="post-form" id="memberPostForm" style="display:none;">
<textarea id="postText" placeholder="Barreeffama kee asitti galchi..."></textarea><br>
<input type="text" id="postImage" placeholder="URL Suuraa (optional)"><br>
<input type="file" id="postVideo" accept="video/*"><br>
<button onclick="addPost()">Post</button>
</div>
<div id="postsContainer"></div>
</section>

<section id="adminDashboard">
<h2>Admin Dashboard</h2>
<p>Total Members: <span id="memberCount">0</span></p>
<table>
<thead>
<tr><th>#</th><th>First Name</th><th>Last Name</th><th>Gender</th><th>Age</th><th>Education</th><th>Username</th></tr>
</thead>
<tbody id="memberTableBody"></tbody>
</table>
</section>

<section id="contact">
<h2>Quunnamtii</h2>
<div class="contact-box">
<p><strong>Email:</strong> awwishrobe@gmail.com</p>
<p><strong>Bilbila:</strong> 0926645165</p>
<p><strong>Bakka:</strong> Oromia, Ethiopia</p>
</div>
</section>

<footer>
<p>&copy; 2026 Awish Website | All Rights Reserved</p>
</footer>

<!-- LOGIN MODAL -->
<div id="loginModal">
<div class="login-box">
<h2>Login</h2>
<input type="text" id="username" placeholder="Username/Email"><br>
<input type="password" id="password" placeholder="Password"><br>
<button onclick="login()">Login</button>
<p>Haa galmaa’uuf <a href="#" onclick="showRegister()">Member Registration</a></p>
</div>
</div>

<!-- REGISTER MODAL -->
<div id="registerModal">
<div class="login-box">
<h2>Member Registration</h2>
<input type="text" id="firstName" placeholder="First Name"><br>
<input type="text" id="lastName" placeholder="Last Name"><br>
<select id="gender">
<option value="">Select Gender</option>
<option value="Male">Male</option>
<option value="Female">Female</option>
<option value="Other">Other</option>
</select><br>
<input type="number" id="age" placeholder="Age"><br>
<input type="text" id="education" placeholder="Education"><br>
<input type="text" id="memberUsername" placeholder="Username"><br>
<input type="password" id="memberPassword" placeholder="Password"><br>
<button onclick="registerMember()">Register</button>
<p>Already member? <a href="#" onclick="showLogin()">Login</a></p>
</div>
</div>

<script>
const websiteURL = "https://www.awwishwebsite.com";

function welcome(){ alert("Baga gara Website Awish dhuftan 🚀"); }
function showRegister(){ document.getElementById("loginModal").style.display="none"; document.getElementById("registerModal").style.display="flex"; }
function showLogin(){ document.getElementById("registerModal").style.display="none"; document.getElementById("loginModal").style.display="flex"; }

const adminUser={username:"admin@awwishwebsite.com",password:"123456"};

function registerMember(){
const f=document.getElementById("firstName").value;
const l=document.getElementById("lastName").value;
const g=document.getElementById("gender").value;
const a=document.getElementById("age").value;
const e=document.getElementById("education").value;
const u=document.getElementById("memberUsername").value;
const p=document.getElementById("memberPassword").value;
if(!f||!l||!g||!a||!e||!u||!p){ alert("Hunda guutuu qaba!"); return; }
let members=JSON.parse(localStorage.getItem("members")||"[]");
if(members.some(m=>m.username===u)){ alert("Username dursee jira!"); return; }
members.push({firstName:f,lastName:l,gender:g,age:a,education:e,username:u,password:p,role:"member"});
localStorage.setItem("members",JSON.stringify(members));
alert("Member galmaa’eera! Login gochuu dandeessa");
document.getElementById("registerModal").style.display="none";
showLogin();
}

function login(){
const u=document.getElementById("username").value;
const p=document.getElementById("password").value;
if(u===adminUser.username && p===adminUser.password){
localStorage.setItem("loggedIn","admin");
document.getElementById("loginModal").style.display="none";
document.getElementById("adminDashboard").style.display="block";
renderMembers();
alert("Admin login success"); return;
}
let members=JSON.parse(localStorage.getItem("members")||"[]");
const member=members.find(m=>m.username===u && m.password===p);
if(member){ localStorage.setItem("loggedIn",member.username); document.getElementById("loginModal").style.display="none"; document.getElementById("memberPostForm").style.display="block"; alert("Member login success"); return;}
alert("Username ykn password sirrii miti!");
}

function renderMembers(){
let members=JSON.parse(localStorage.getItem("members")||"[]");
document.getElementById("memberCount").textContent=members.length;
const tbody=document.getElementById("memberTableBody");
tbody.innerHTML="";
members.forEach((m,index)=>{
let tr=document.createElement("tr");
tr.innerHTML=`<td>${index+1}</td><td>${m.firstName}</td><td>${m.lastName}</td><td>${m.gender}</td><td>${m.age}</td><td>${m.education}</td><td>${m.username}</td>`;
tbody.appendChild(tr);
});
}

// Posts
function addPost(){
if(!localStorage.getItem("loggedIn")){ alert("Login duratti post gochuu hin dandeessu!"); return; }
const text=document.getElementById("postText").value;
const image=document.getElementById("postImage").value;
const videoInput=document.getElementById("postVideo");
const videoFile=videoInput.files[0];
if(!text && !image && !videoFile){ alert("Mee waa tokko galchi!"); return; }
let posts=JSON.parse(localStorage.getItem("posts")||"[]");
const postId=Date.now();
let videoURL="";
if(videoFile){ videoURL=URL.createObjectURL(videoFile); }
posts.unshift({id:postId,text,image,video:videoURL,author:localStorage.getItem("loggedIn"),likes:0});
localStorage.setItem("posts",JSON.stringify(posts));
document.getElementById("postText").value=""; document.getElementById("postImage").value=""; videoInput.value="";
renderPosts();
}

function renderPosts(){
const container=document.getElementById("postsContainer"); container.innerHTML="";
let posts=JSON.parse(localStorage.getItem("posts")||"[]");
posts.forEach(post=>{
const div=document.createElement("div"); div.classList.add("post"); div.dataset.id=post.id;
if(post.text){ const p=document.createElement("p"); p.textContent=post.text; div.appendChild(p);}
if(post.image){ const img=document.createElement("img"); img.src=post.image; div.appendChild(img);}
if(post.video){ const vid=document.createElement("video"); vid.src=post.video; vid.controls=true; div.appendChild(vid);}
const actions=document.createElement("div"); actions.classList.add("post-actions");

const editBtn=document.createElement("button"); editBtn.textContent="Edit"; editBtn.classList.add("edit");
editBtn.onclick=()=>editPost(post.id);
const deleteBtn=document.createElement("button"); deleteBtn.textContent="Delete"; deleteBtn.classList.add("delete");
deleteBtn.onclick=()=>deletePost(post.id);
const likeBtn=document.createElement("button"); likeBtn.textContent=`Like (${post.likes})`; likeBtn.classList.add("like");
likeBtn.onclick=()=>likePost(post.id);

actions.appendChild(editBtn); actions.appendChild(deleteBtn); actions.appendChild(likeBtn);
div.appendChild(actions);

const shareDiv=document.createElement("div"); shareDiv.classList.add("share-buttons");
const urlWithId=websiteURL+"?post="+post.id;
const fb=document.createElement("a"); fb.href=`https://www.facebook.com/sharer/sharer.php?u=${encodeURIComponent(urlWithId)}`; fb.target="_blank"; fb.textContent="Share FB";
const tw=document.createElement("a"); tw.href=`https://twitter.com/intent/tweet?url=${encodeURIComponent(urlWithId)}&text=${encodeURIComponent(post.text)}`; tw.target="_blank"; tw.textContent="Share TW";
const copy=document.createElement("button"); copy.textContent="Copy Link"; copy.onclick=()=>{navigator.clipboard.writeText(urlWithId); alert("Link copied!");};
shareDiv.appendChild(fb); shareDiv.appendChild(tw); shareDiv.appendChild(copy);
div.appendChild(shareDiv);
container.appendChild(div);
});
}

function deletePost(id){ if(confirm("Dhugaa post kana delete gochuu barbaadda?")){ let posts=JSON.parse(localStorage.getItem("posts")||"[]"); posts=posts.filter(p=>p.id!==id); localStorage.setItem("posts",JSON.stringify(posts)); renderPosts();}}
function editPost(id){ let posts=JSON.parse(localStorage.getItem("posts")||"[]"); const post=posts.find(p=>p.id===id); const newText=prompt("Edit barreeffama:",post.text); if(newText!==null){ post.text=newText; localStorage.setItem("posts",JSON.stringify(posts)); renderPosts(); }}
function likePost(id){ let posts=JSON.parse(localStorage.getItem("posts")||"[]"); const post=posts.find(p=>p.id===id); post.likes+=1; localStorage.setItem("posts",JSON.stringify(posts)); renderPosts(); }

window.onload=function(){
const params=new URLSearchParams(window.location.search);
const postId=params.get("post");
if(postId){ renderPosts(); const postDiv=document.querySelector(`.post[data-id='${postId}']`); if(postDiv) postDiv.scrollIntoView({behavior:"smooth"}); postDiv.style.border="2px solid #004d4d"; }
else{ renderPosts(); }

if(localStorage.getItem("loggedIn")==="admin"){ document.getElementById("loginModal").style.display="none"; document.getElementById("adminDashboard").style.display="block"; renderMembers();}
else if(localStorage.getItem("loggedIn")){ document.getElementById("loginModal").style.display="none"; document.getElementById("memberPostForm").style.display="block";}
else{ document.getElementById("loginModal").style.display="flex"; }
}
</script>

</body>
</html>
