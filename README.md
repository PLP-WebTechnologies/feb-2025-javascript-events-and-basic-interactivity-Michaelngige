# 🎯 JavaScript Event Handling & Interactive Elements Assignment

Welcome to the **ultimate JavaScript playground**! 🎉 This assignment is where we turn boring web pages into dynamic, responsive, *alive* experiences. Get ready to master **event handling**, build **interactive components**, and validate forms like a pro! 💪

## 📁 Assignment Structure

```
📂 js-event-assignment/
├── index.html         # Your playground – where it all comes together
├── style.css          # Keep it cute (optional but encouraged)
└── script.js          # The JavaScript wizardry happens here
```

---

## 🧪 What to Build

Here’s what your interactive bundle of joy should include:

### 1. Event Handling 🎈  
- Button click ✅  
- Hover effects ✅  
- Keypress detection ✅  
- Bonus: A secret action for a *double-click* or *long press* 🤫

### 2. Interactive Elements 🎮  
- A button that changes text or color  
- An image gallery or slideshow  
- Tabs or accordion-style content  
- Bonus: Add some animation using JS or CSS ✨

### 3. Form Validation 📋✅  
- Required field checks  
- Email format validation  
- Password rules (e.g., min 8 characters)  
- Bonus: Real-time feedback while typing

---

## 🧙‍♂️ Pro Tips

- Keep your code clean and commented – your future self will thank you!
- Think about **user experience** – what makes your site more *fun* to use?
- Don’t be afraid to **Google and experiment** – that’s how real developers roll!

---

## 🎉 Now Go Make It Fun!

Remember – this isn't just code. It's your **first step toward creating magical user experiences**. So play around, break stuff (then fix it), and most of all, have FUN! 😄

Happy Coding! 💻✨  
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Interactive Event Assignment</title>
  <style>
    body {
      font-family: Arial, sans-serif;
      padding: 20px;
    }
    button {
      padding: 10px 20px;
      margin: 10px;
      font-size: 16px;
      cursor: pointer;
    }
    .tab {
      display: inline-block;
      padding: 10px;
      margin: 5px;
      background-color: #f1f1f1;
      cursor: pointer;
    }
    .tab-content {
      display: none;
      margin-top: 10px;
    }
    .show {
      display: block;
    }
    input {
      padding: 10px;
      margin: 10px;
    }
    .modal {
      display: none;
      position: fixed;
      top: 0;
      left: 0;
      width: 100%;
      height: 100%;
      background-color: rgba(0, 0, 0, 0.5);
      justify-content: center;
      align-items: center;
    }
    .modal-content {
      background-color: white;
      padding: 20px;
      text-align: center;
    }
  </style>
</head>
<body>

  <h1>Interactive Event Assignment</h1>

  <!-- Button that changes text and color -->
  <button id="changeBtn">Click Me</button>

  <!-- Hover effect button -->
  <button id="hoverBtn">Hover Over Me</button>

  <!-- Keypress detection -->
  <input type="text" id="keyInput" placeholder="Type something">

  <!-- Image Slideshow -->
  <div>
    <img id="slideshow" src="https://via.placeholder.com/300x200?text=Image+1" alt="Slideshow" width="300">
  </div>
  <button onclick="changeImage()">Next Image</button>

  <!-- Tabs/Accordion -->
  <div class="tab" onclick="openTab('Tab1')">Tab 1</div>
  <div class="tab" onclick="openTab('Tab2')">Tab 2</div>
  <div id="Tab1" class="tab-content">This is Tab 1 content</div>
  <div id="Tab2" class="tab-content">This is Tab 2 content</div>

  <!-- Form Validation -->
  <form id="emailForm">
    <input type="email" id="email" placeholder="Enter your email" required>
    <button type="submit">Submit Email</button>
  </form>

  <form id="passwordForm">
    <input type="password" id="password" placeholder="Enter password" required>
    <button type="submit">Submit Password</button>
  </form>

  <div id="feedback"></div>

  <!-- Modal for hidden action -->
  <div id="myModal" class="modal">
    <div class="modal-content">
      <span onclick="closeModal()" style="cursor: pointer;">&times;</span>
      <p>Secret Modal Content!</p>
    </div>
  </div>

  <button onclick="openModal()">Open Secret Modal</button>

  <script>
    // Event handling for button click
    document.getElementById("changeBtn").addEventListener("click", function() {
      this.innerText = "You Clicked Me!";
      this.style.backgroundColor = "green";
    });

    // Hover effect
    const hoverButton = document.getElementById("hoverBtn");
    hoverButton.addEventListener("mouseover", function() {
      this.style.backgroundColor = "blue";
    });
    hoverButton.addEventListener("mouseout", function() {
      this.style.backgroundColor = "";
    });

    // Keypress detection
    document.getElementById("keyInput").addEventListener("keypress", function(event) {
      console.log(`Key pressed: ${event.key}`);
    });

    // Slideshow
    let imageIndex = 0;
    const images = [
      "https://via.placeholder.com/300x200?text=Image+1",
      "https://via.placeholder.com/300x200?text=Image+2",
      "https://via.placeholder.com/300x200?text=Image+3"
    ];

    function changeImage() {
      imageIndex = (imageIndex + 1) % images.length;
      document.getElementById("slideshow").src = images[imageIndex];
    }

    // Tabs/Accordion content display
    function openTab(tabName) {
      const contents = document.querySelectorAll('.tab-content');
      contents.forEach(content => content.style.display = 'none');
      document.getElementById(tabName).style.display = 'block';
    }

    // Default open tab
    openTab('Tab1');

    // Form Validation: Email and Password
    document.getElementById("emailForm").addEventListener("submit", function(event) {
      const email = document.getElementById("email").value;
      const emailPattern = /^[^\s@]+@[^\s@]+\.[^\s@]+$/;
      if (!emailPattern.test(email)) {
        alert("Please enter a valid email address!");
        event.preventDefault();
      }
    });

    document.getElementById("passwordForm").addEventListener("submit", function(event) {
      const password = document.getElementById("password").value;
      if (password.length < 8) {
        alert("Password must be at least 8 characters long!");
        event.preventDefault();
      }
    });

    // Modal functionality
    function openModal() {
      document.getElementById("myModal").style.display = "flex";
    }

    function closeModal() {
      document.getElementById("myModal").style.display = "none";
    }

    // Real-time feedback while typing
    document.getElementById("keyInput").addEventListener("input", function() {
      document.getElementById("feedback").textContent = "You are typing...";
    });

  </script>

</body>
</html>
