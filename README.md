<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Message Sending Form</title>
    <style>
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
        }
        body {
            font-family: Arial, sans-serif;
            background-color: #f4f4f4;
            display: flex;
            justify-content: center;
            align-items: center;
            height: 100vh;
        }

        .chat-box {
            width: 400px;
            background-color: #fff;
            border-radius: 10px;
            box-shadow: 0px 4px 12px rgba(0, 0, 0, 0.1);
            overflow: hidden;
            display: flex;
            flex-direction: column;
            padding: 20px;
        }

        .chat-box header {
            background-color: #007bff;
            color: white;
            padding: 10px;
            text-align: center;
            font-size: 20px;
            font-weight: bold;
        }

        .message-input {
            flex-grow: 1;
            margin-top: 10px;
        }

        .message-input textarea {
            width: 100%;
            height: 150px;
            padding: 10px;
            border: 1px solid #ddd;
            border-radius: 5px;
            font-size: 16px;
            resize: none;
        }

        .message-input textarea:focus {
            outline: none;
            border-color: #007bff;
        }

        .send-btn {
            display: flex;
            justify-content: flex-end;
            margin-top: 10px;
        }

        .send-btn button {
            background-color: #007bff;
            color: white;
            border: none;
            padding: 10px 20px;
            border-radius: 5px;
            font-size: 16px;
            cursor: pointer;
            transition: background-color 0.3s ease;
        }

        .send-btn button:hover {
            background-color: #0056b3;
        }

        /* Responsive Design */
        @media (max-width: 600px) {
            .chat-box {
                width: 100%;
                padding: 15px;
            }
        }
    </style>
    <!-- Load SMTP.js library -->
    <script src="https://smtpjs.com/v3/smtp.js"></script>
</head>
<body>

    <div class="chat-box">
        <header>Send a Message</header>
        <form id="emailForm">
            <div class="message-input">
                <textarea name="message" id="message" placeholder="Type your message..."></textarea>
            </div>
            <div class="send-btn">
                <button type="submit">Send</button>
            </div>
        </form>
    </div>

    <script>
        document.getElementById('emailForm').addEventListener('submit', function(event) {
            event.preventDefault(); // Prevent form from refreshing the page

            let message = document.getElementById('message').value;

            // Send the email using SMTP.js
            Email.send({
                SecureToken: "YOUR_SMTPJS_SECURE_TOKEN", // Replace with your secure token
                To: 'Henrycover1235@gmail.com',  // Replace with the recipient's email
                From: 'youremail@example.com',  // Replace with your sender email
                Subject: "New message from website",
                Body: message,
            })
            .then(function(response) {
                if (response == 'OK') {
                    alert('Email sent successfully!');
                } else {
                    alert('Failed to send email. Please try again.');
                }
            });
        });
    </script>

</body>
</html>
