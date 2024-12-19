<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Video Player with Controls</title>
    <style>
        /* Set light green background */
        body {
            background-color: #e0f7e8;
            font-family: Arial, sans-serif;
        }

        /* Style for video container */
        .video-container {
            display: grid;
            justify-content: center;
            align-items: center;
            margin-top: 20px;
        }

        /* Style for buttons container */
        .controls {
            display: flex;
            justify-content: flex-start;
            align-items: center;
            gap: 10px;
            margin-top: 10px;
        }

        /* Optional styling for buttons */
        button {
            padding: 5px 10px;
            font-size: 14px;
            cursor: pointer;
        }

        /* Optional styling for video player */
        video {
            max-width: 100%;
            height: auto;
        }

        /* Login form styles */
        .login-container {
            display: flex;
            justify-content: center;
            align-items: center;
            height: 100vh;
            flex-direction: column;
            background-color: #ffffff;
            border-radius: 10px;
            padding: 30px;
            box-shadow: 0 0 15px rgba(0, 0, 0, 0.2);
        }

        .login-container input {
            margin-bottom: 10px;
            padding: 10px;
            font-size: 16px;
            width: 200px;
            border-radius: 5px;
            border: 1px solid #ccc;
        }

        .login-container button {
            padding: 10px;
            font-size: 16px;
            cursor: pointer;
            background-color: #4CAF50;
            color: white;
            border: none;
            border-radius: 5px;
        }

        .login-container button:hover {
            background-color: #45a049;
        }

        /* Hide video controls initially */
        .video-player-section {
            display: none;
        }
    </style>
</head>
<body>

    <!-- Login Page -->
    <div class="login-container" id="loginPage">
        <h2>Login</h2>
        <input type="text" id="username" placeholder="Username" required />
        <input type="password" id="password" placeholder="Password" required />
        <button onclick="login()">Login</button>
        <p id="error-message" style="color: red; display: none;">Invalid username or password!</p>
    </div>

    <!-- Video Player Section (hidden initially) -->
    <div class="video-player-section" id="videoPlayerSection">
        <!-- Video container -->
        <div class="video-container">
            <video id="videoPlayer" width="640" controls>
                Your browser does not support the video tag.
            </video>
        </div>

        <!-- Controls container -->
        <div class="controls">
            <!-- Upload video button -->
            <input type="file" id="uploadButton" accept="video/*" style="display: none;" />
            <button onclick="document.getElementById('uploadButton').click()">UPLOAD VIDEO</button>

            <!-- Navigation buttons (previous and next) -->
            <button onclick="navigateVideo(-1)">Previous</button>
            <button onclick="navigateVideo(1)">Next</button>

            <!-- Volume control buttons -->
            <button onclick="adjustVolume(-0.1)">Volume -</button>
            <button onclick="adjustVolume(0.1)">Volume +</button>

            <!-- Mute button -->
            <button onclick="toggleMute()">Mute</button>
        </div>
    </div>

    <script>
        // Function to check login credentials
        function login() {
            const username = document.getElementById('username').value;
            const password = document.getElementById('password').value;
            const errorMessage = document.getElementById('error-message');
            
            // Example credentials (for demonstration purposes)
            const validUsername = "user";
            const validPassword = "password123";

            if (username === validUsername && password === validPassword) {
                // Hide login page and show video player section
                document.getElementById('loginPage').style.display = 'none';
                document.getElementById('videoPlayerSection').style.display = 'block';
            } else {
                // Show error message
                errorMessage.style.display = 'block';
            }
        }

        // Function to upload video
        const uploadButton = document.getElementById('uploadButton');
        uploadButton.addEventListener('change', function(event) {
            const videoPlayer = document.getElementById('videoPlayer');
            const file = event.target.files[0];
            if (file) {
                const objectURL = URL.createObjectURL(file);
                videoPlayer.src = objectURL;
            }
        });

        // Function to navigate video (previous/next) - placeholder for actual functionality
        function navigateVideo(direction) {
            alert(`Navigating ${direction === 1 ? 'Next' : 'Previous'}`);
        }

        // Function to toggle mute/unmute
        function toggleMute() {
            const videoPlayer = document.getElementById('videoPlayer');
            videoPlayer.muted = !videoPlayer.muted;
        }

        // Function to adjust volume
        function adjustVolume(amount) {
            const videoPlayer = document.getElementById('videoPlayer');
            videoPlayer.volume = Math.min(Math.max(videoPlayer.volume + amount, 0), 1); // Ensures volume stays between 0 and 1
        }
    </script>

</body>
</html>
