<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>PromoMantra</title>
    <style>
        body {
            font-family: Arial;
            background: #f4f4f4;
            margin: 0;
            text-align: center;
        }

        .header {
            background: #ff4d4d;
            color: white;
            padding: 20px;
        }

        .container {
            padding: 20px;
        }

        input {
            padding: 10px;
            margin: 5px;
            width: 250px;
        }

        button {
            padding: 10px 15px;
            background: #ff4d4d;
            color: white;
            border: none;
            cursor: pointer;
        }

        .post-box {
            background: white;
            width: 80%;
            margin: 15px auto;
            padding: 15px;
            box-shadow: 0 0 10px gray;
        }

        .post-box a {
            display: block;
            margin: 10px 0;
            color: blue;
        }

        .delete-btn {
            background: black;
            color: white;
            padding: 5px 10px;
        }
    </style>
</head>
<body>

<div class="header">
    <h1>PromoMantra</h1>
    <p>Promote Your Content for Free</p>
</div>

<div class="container">
    <!-- Login Section -->
    <div id="login-section">
        <h2>Login / Enter Details</h2>
        <input type="text" id="name" placeholder="Enter Name"><br>
        <input type="text" id="number" placeholder="Enter Phone Number"><br>
        <button onclick="login()">Login</button>
    </div>

    <!-- Home Section -->
    <div id="home-section" style="display:none;">
        <h2>Welcome, <span id="user-name"></span></h2>
        <h3>Create a Promotion</h3>
        <input type="text" id="title" placeholder="Enter Title">
        <input type="text" id="link" placeholder="Enter Link">
        <button onclick="addPost()">Post Now</button>

        <h3>All Promotions</h3>
        <div id="posts"></div>
    </div>
</div>

<script>
let userNumber = "";
let userName = "";
let posts = [];
const dailyLimit = 3;

// Login function
function login() {
    userName = document.getElementById("name").value.trim();
    userNumber = document.getElementById("number").value.trim();

    if(userName === "" || userNumber === "") {
        alert("Please enter both Name and Number");
        return;
    }

    // Hide login, show home
    document.getElementById("login-section").style.display = "none";
    document.getElementById("home-section").style.display = "block";
    document.getElementById("user-name").innerText = userName;

    // Load posts from localStorage
    const savedPosts = JSON.parse(localStorage.getItem(userNumber));
    if(savedPosts) posts = savedPosts;
    renderPosts();
}

// Add new post
function addPost() {
    if(posts.length >= dailyLimit) {
        alert("Daily post limit reached!");
        return;
    }

    const title = document.getElementById("title").value.trim();
    const link = document.getElementById("link").value.trim();

    if(title === "" || link === "") {
        alert("Please fill all fields");
        return;
    }

    const newPost = { title, link };
    posts.push(newPost);

    // Save to localStorage
    localStorage.setItem(userNumber, JSON.stringify(posts));
    renderPosts();

    document.getElementById("title").value = "";
    document.getElementById("link").value = "";
}

// Render posts
function renderPosts() {
    const postsDiv = document.getElementById("posts");
    postsDiv.innerHTML = "";
    posts.forEach((post, index) => {
        const div = document.createElement("div");
        div.className = "post-box";
        div.innerHTML = `
            <h3>${post.title}</h3>
            <a href="${post.link}" target="_blank">Visit Link</a>
            <button class='delete-btn' onclick='deletePost(${index})'>Delete</button>
        `;
        postsDiv.appendChild(div);
    });
}

// Delete post
function deletePost(index) {
    posts.splice(index, 1);
    localStorage.setItem(userNumber, JSON.stringify(posts));
    renderPosts();
}
</script>

</body>
</html>
