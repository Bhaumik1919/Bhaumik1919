
<!DOCTYPE html>
<html lang="en"
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Chat Input Box</title>
    <link rel="stylesheet" href="style.css">
</head>
<body>
   
    <div class="chat-input-container">
        
        <div id="chat-box" class="chat-box"></div> <!-- Chat display area -->
        <div class="chat-input-box">
            <span class="attachment-icon">&#128206;</span> <!-- Unicode paperclip icon -->
            <input type="text" id="chat-input" placeholder="Message ChatGPT">
            <button class="send-button">&#9654;</button> <!-- Unicode play icon -->
        </div>
    </div>

    <style>
        body {
            /*background-color: #131212;*/
            display: flex;
            justify-content: center;
            align-items: center;
            height: 100vh;
            margin: 0;
            font-family: Arial, sans-serif;
            color: #000;
            background-image: url(../bhaumik/images/ok-school.jpg);
            background-size: cover;
    background-repeat: no-repeat;
        }

        .chat-input-container {
            width: 600px;
        }

        .chat-box {
            height: 300px;
            overflow-y: auto;
            background-color: #1a1a1a;
            border-radius: 10px;
            padding: 10px;
            margin-bottom: 10px;
            box-shadow: 0 2px 5px rgba(0, 0, 0, 0.2);
            color: #ffffff68;
        }

        .message {
            padding: 8px;
            border-radius: 5px;
            margin-bottom: 10px;
        }

        .user-message {
            background-color: #444;
            text-align: right;
        }

        .bot-message {
            background-color: #555;
            text-align: left;
            color:#fff;
            line-height: 25px;
        }

        .chat-input-box {
            display: flex;
            align-items: center;
            background-color: #2d2d2d;
            border-radius: 25px;
            padding: 10px;
            box-shadow: 0 2px 5px rgba(0, 0, 0, 0.2);
        }

        .attachment-icon {
            color: #888;
            font-size: 18px;
            margin-right: 10px;
            cursor: pointer;
        }

        .chat-input-box input {
            flex: 1;
            background-color: transparent;
            border: none;
            color: #ccc;
            outline: none;
            font-size: 16px;
        }

        .chat-input-box input::placeholder {
            color: #888;
        }

        .send-button {
            background-color: #444;
            border: none;
            color: #ccc;
            font-size: 18px;
            padding: 8px;
            border-radius: 50%;
            cursor: pointer;
            transition: background-color 0.3s;
        }

        .send-button:hover {
            background-color: #666;
        }
        .logo{
            width: 550px;
        }
    </style>

    <script>
        document.querySelector(".send-button").addEventListener("click", sendMessage);
document.getElementById("chat-input").addEventListener("keypress", function(event) {
    if (event.key === "Enter") {
        sendMessage();
    }
});

function sendMessage() {
    const userInput = document.getElementById("chat-input");
    const chatBox = document.getElementById("chat-box");

    // Get the user's message
    const userMessage = userInput.value.trim();
    if (userMessage === "") return;

    // Display the user's message
    const userMessageElement = document.createElement("div");
    userMessageElement.className = "message user-message";
    userMessageElement.textContent = userMessage;
    chatBox.appendChild(userMessageElement);

    // Scroll to the bottom of the chat
    chatBox.scrollTop = chatBox.scrollHeight;

    // Clear the input field
    userInput.value = "";

    // Simulate a bot response
    setTimeout(() => {
        const botMessage = getBotResponse(userMessage);
        const botMessageElement = document.createElement("div");
        botMessageElement.className = "message bot-message";
        
        // Check if the botMessage contains HTML content (for example, an <img> tag)
        if (userMessage === "2") {
            botMessageElement.innerHTML = botMessage; // Use innerHTML to render HTML content
        } else {
            botMessageElement.textContent = botMessage;
        }
        
        chatBox.appendChild(botMessageElement);

        // Scroll to the bottom of the chat
        chatBox.scrollTop = chatBox.scrollHeight;
    }, 1000);
}

function getBotResponse(message) {
    const responses = {
        "hi": "Hi there! How can I help you? 1.ABOUT US 2.MISSION 3.CONTACT US",
        "1": "Welcome to Oak Valley International School. We’re a schools dedicated to encouraging students to be themselves and explore beyond boundaries. We teach your children to think, explore, and learn with joy. With our exemplary education and facilities, we have built the best CBSE schools in India. Our school was started in 2014. and since then, it has grown over 10 years. Our core interests have since then developed but have remained in the sphere of quality education, commitment to excellence, and shaping the future. This futuristic approach towards education makes the best school in India. We believe in handling your child's future with utmost care.",
        "3": "Hence, Oak Valleians are Kings and Queens in the making. Our institutions focus on the all-round development of the child.",
        "": "Hi there! How can I help you?",
        "2": '<img src="" class="oakayhg" style="width:100%;" alt="Oak Valley Logo" />', 
        "how are you?": "I'm just a bot, but I'm here to assist you!",
        "bye": "Goodbye! Have a great day!",
        "oak valley international school": "Welcome to the ambient environment of the Oak Valley School campus.",
        "oak valley": "Oak Valley is known for its peaceful, clean, and healthy learning environment.",
        "oak valley school": "Oak Valley School offers a friendly atmosphere for teaching and learning.",
        "Who is Sai Manikanta": "Sai Manikanta is the best friend of Bhaumik Raghavan Bheemanathini."
    };

    return responses[message.toLowerCase()] || "I'm not sure how to respond to that.";
}

    </script>
</body>
</html>
