<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Jame AI — Gemini Powered</title>
    <style>
        * { margin: 0; padding: 0; box-sizing: border-box; font-family: 'Segoe UI', Arial, sans-serif; }
        body {
            background: linear-gradient(135deg, #0f0f1a 0%, #1a1a3a 100%);
            color: #fff;
            min-height: 100vh;
            padding: 20px;
        }
        .container { max-width: 750px; margin: 0 auto; }
        h1 {
            text-align: center;
            color: #4ecdc4;
            font-size: 40px;
            margin: 30px 0 5px;
            text-shadow: 0 0 15px rgba(78,205,196,0.4);
        }
        .subtitle { text-align: center; color: #888; margin-bottom: 35px; }
        .chat-card {
            background: rgba(26, 26, 46, 0.85);
            border-radius: 16px;
            padding: 25px;
            box-shadow: 0 0 30px rgba(78,205,196,0.15);
            border: 1px solid rgba(78,205,196,0.2);
        }
        textarea {
            width: 100%;
            height: 130px;
            background: #16213e;
            border: 2px solid #2a3a5c;
            border-radius: 10px;
            padding: 15px;
            color: #fff;
            font-size: 16px;
            resize: none;
            transition: 0.3s;
        }
        textarea:focus { outline: none; border-color: #4ecdc4; }
        button {
            width: 100%;
            margin-top: 15px;
            padding: 15px;
            background: linear-gradient(90deg, #4ecdc4, #44a08d);
            border: none;
            border-radius: 10px;
            font-size: 18px;
            font-weight: bold;
            color: #0f0f1a;
            cursor: pointer;
            transition: 0.3s;
        }
        button:hover { transform: scale(1.02); }
        button:disabled { opacity: 0.6; cursor: not-allowed; transform: none; }
        #response {
            margin-top: 20px;
            padding: 20px;
            background: #16213e;
            border-radius: 10px;
            min-height: 80px;
            line-height: 1.7;
            white-space: pre-wrap;
            border-left: 3px solid #4ecdc4;
        }
        .loading { color: #4ecdc4; }
        .error { color: #ff6b6b; }
        .api-note {
            margin-top: 20px;
            padding: 12px;
            background: rgba(255,170,0,0.1);
            border-radius: 8px;
            font-size: 13px;
            color: #ffcc66;
        }
    </style>
</head>
<body>
    <div class="container">
        <h1>🔥 JAME AI</h1>
        <p class="subtitle">Powered by Gemini API</p>
        
        <div class="chat-card">
            <textarea id="promptInput" placeholder="Type your message here..."></textarea>
            <button id="sendBtn" onclick="callGemini()">SEND TO AI</button>
            <div id="response"></div>
        </div>

        <div class="api-note">
            ⚠️ Your API key is embedded here. For public sharing, use the hidden method below.
        </div>
    </div>

    <script>
        // --------------------------
        // PASTE YOUR KEY HERE
        // --------------------------
        const API_KEY = "YOUR_KEY_HERE"; 
        const API_URL = "https://generativelanguage.googleapis.com/v1beta/models/gemini-2.0-flash:generateContent?key=" + API_KEY;

        async function callGemini() {
            const prompt = document.getElementById('promptInput').value.trim();
            if (!prompt) return;

            const resBox = document.getElementById('response');
            const sendBtn = document.getElementById('sendBtn');
            
            sendBtn.disabled = true;
            resBox.innerHTML = '<span class="loading">🧠 Gemini is thinking...</span>';

            try {
                const response = await fetch(API_URL, {
                    method: 'POST',
                    headers: { 'Content-Type': 'application/json' },
                    body: JSON.stringify({
                        contents: [{ parts: [{ text: prompt }] }]
                    })
                });

                const data = await response.json();
                
                if (data.error) {
                    throw new Error(data.error.message || "API Error");
                }

                const aiText = data.candidates[0].content.parts[0].text;
                resBox.textContent = aiText;

            } catch (err) {
                resBox.innerHTML = `<span class="error">❌ Error: ${err.message}</span>`;
            } finally {
                sendBtn.disabled = false;
            }
        }
    </script>
</body>
</html>
