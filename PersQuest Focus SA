<!DOCTYPE html>
<html lang="de">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Schulfest-Team Chat 💬</title>
    <style>
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
        }

        body {
            font-family: -apple-system, BlinkMacSystemFont, "Segoe UI", Roboto, sans-serif;
            background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
            height: 100vh;
            display: flex;
            justify-content: center;
            align-items: center;
            padding: 20px;
        }

        .chat-container {
            background: white;
            border-radius: 20px;
            box-shadow: 0 20px 60px rgba(0, 0, 0, 0.3);
            width: 100%;
            max-width: 500px;
            height: 90vh;
            max-height: 800px;
            display: flex;
            flex-direction: column;
            overflow: hidden;
        }

        .chat-header {
            background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
            color: white;
            padding: 20px;
            display: flex;
            align-items: center;
            gap: 15px;
            box-shadow: 0 2px 10px rgba(0, 0, 0, 0.1);
        }

        .chat-header-icon {
            font-size: 32px;
        }

        .chat-header-info h2 {
            font-size: 18px;
            font-weight: 600;
            margin-bottom: 4px;
        }

        .chat-header-info p {
            font-size: 13px;
            opacity: 0.9;
        }

        .chat-messages {
            flex: 1;
            padding: 20px;
            overflow-y: auto;
            background: #f5f7fb;
            scroll-behavior: smooth;
        }

        .chat-messages::-webkit-scrollbar {
            width: 6px;
        }

        .chat-messages::-webkit-scrollbar-track {
            background: transparent;
        }

        .chat-messages::-webkit-scrollbar-thumb {
            background: #cbd5e0;
            border-radius: 3px;
        }

        .message {
            display: flex;
            gap: 12px;
            margin-bottom: 20px;
            opacity: 0;
            transform: translateY(10px);
            animation: messageAppear 0.3s ease forwards;
        }

        @keyframes messageAppear {
            to {
                opacity: 1;
                transform: translateY(0);
            }
        }

        .avatar {
            width: 40px;
            height: 40px;
            border-radius: 50%;
            display: flex;
            align-items: center;
            justify-content: center;
            font-weight: 600;
            font-size: 16px;
            color: white;
            flex-shrink: 0;
        }

        .message-content {
            flex: 1;
        }

        .message-header {
            display: flex;
            align-items: baseline;
            gap: 8px;
            margin-bottom: 6px;
        }

        .username {
            font-weight: 600;
            font-size: 14px;
            color: #2d3748;
        }

        .timestamp {
            font-size: 11px;
            color: #a0aec0;
        }

        .message-bubble {
            background: white;
            padding: 12px 16px;
            border-radius: 12px;
            font-size: 14px;
            line-height: 1.5;
            color: #2d3748;
            box-shadow: 0 1px 2px rgba(0, 0, 0, 0.05);
            max-width: 100%;
            word-wrap: break-word;
        }

        .typing-indicator {
            display: flex;
            gap: 12px;
            margin-bottom: 20px;
            opacity: 0;
            animation: messageAppear 0.3s ease forwards;
        }

        .typing-bubble {
            background: white;
            padding: 16px 20px;
            border-radius: 12px;
            box-shadow: 0 1px 2px rgba(0, 0, 0, 0.05);
        }

        .typing-dots {
            display: flex;
            gap: 4px;
        }

        .typing-dots span {
            width: 8px;
            height: 8px;
            border-radius: 50%;
            background: #cbd5e0;
            animation: typingDot 1.4s infinite;
        }

        .typing-dots span:nth-child(2) {
            animation-delay: 0.2s;
        }

        .typing-dots span:nth-child(3) {
            animation-delay: 0.4s;
        }

        @keyframes typingDot {
            0%, 60%, 100% {
                transform: translateY(0);
                opacity: 0.5;
            }
            30% {
                transform: translateY(-8px);
                opacity: 1;
            }
        }

        .date-divider {
            text-align: center;
            margin: 30px 0 20px;
            position: relative;
        }

        .date-divider span {
            background: #e2e8f0;
            color: #718096;
            padding: 6px 16px;
            border-radius: 20px;
            font-size: 12px;
            font-weight: 500;
        }

        /* Character specific colors */
        .mia { background: linear-gradient(135deg, #667eea, #764ba2); }
        .leon { background: linear-gradient(135deg, #f093fb, #f5576c); }
        .jonas { background: linear-gradient(135deg, #4facfe, #00f2fe); }
        .emma { background: linear-gradient(135deg, #43e97b, #38f9d7); }
        .sarah { background: linear-gradient(135deg, #fa709a, #fee140); }

        .system-message {
            text-align: center;
            margin: 20px 0;
            opacity: 0;
            animation: messageAppear 0.3s ease forwards;
        }

        .system-message span {
            background: #e2e8f0;
            color: #4a5568;
            padding: 8px 16px;
            border-radius: 20px;
            font-size: 13px;
            font-style: italic;
        }

        .emoji {
            font-size: 18px;
        }

        @media (max-width: 600px) {
            .chat-container {
                height: 100vh;
                max-height: none;
                border-radius: 0;
            }
        }
    </style>
</head>
<body>
    <div class="chat-container">
        <div class="chat-header">
            <div class="chat-header-icon">🎪</div>
            <div class="chat-header-info">
                <h2>Schulfest-Orga-Team</h2>
                <p>5 Mitglieder • Planung läuft...</p>
            </div>
        </div>

        <div class="chat-messages" id="chatMessages">
            <!-- Messages will be added here dynamically -->
        </div>
    </div>

    <script>
        const messages = [
            {
                type: 'date',
                text: 'Montag, 15. April 2024'
            },
            {
                type: 'message',
                user: 'Leon',
                avatar: 'L',
                color: 'leon',
                text: 'Hey Team! 👋 Ich hab mal eine erste Aufgabenliste für unser Schulfest erstellt',
                time: '09:23',
                delay: 2000
            },
            {
                type: 'message',
                user: 'Jonas',
                avatar: 'J',
                color: 'jonas',
                text: 'Nice! Zeig mal her',
                time: '09:24',
                delay: 2500
            },
            {
                type: 'message',
                user: 'Leon',
                avatar: 'L',
                color: 'leon',
                text: 'Also: Ich kümmere mich um Technik und Bühne, Jonas du machst die Musik, Emma Social Media, Sarah Dekoration und Mia die Catering-Organisation',
                time: '09:25',
                delay: 4000
            },
            {
                type: 'message',
                user: 'Emma',
                avatar: 'E',
                color: 'emma',
                text: 'Perfekt! Ich starte gleich mit Posts für Instagram 📱✨',
                time: '09:26',
                delay: 3000
            },
            {
                type: 'message',
                user: 'Sarah',
                avatar: 'S',
                color: 'sarah',
                text: 'Ich hab schon ein paar Deko-Ideen! Wir könnten mit Lichterketten arbeiten 💡',
                time: '09:27',
                delay: 3500
            },
            {
                type: 'message',
                user: 'Mia',
                avatar: 'M',
                color: 'mia',
                text: 'Okay, ich check mal die Caterer durch. Hat jemand Empfehlungen?',
                time: '09:28',
                delay: 3000
            },
            {
                type: 'message',
                user: 'Jonas',
                avatar: 'J',
                color: 'jonas',
                text: 'Btw, ich hab schon mit DJ Alex gesprochen, der würde uns unterstützen! 🎵',
                time: '09:30',
                delay: 3000
            },
            {
                type: 'system',
                text: 'Sarah hat ein Foto geteilt',
                delay: 2000
            },
            {
                type: 'message',
                user: 'Sarah',
                avatar: 'S',
                color: 'sarah',
                text: 'Schaut mal, so könnte die Deko aussehen! Was meint ihr?',
                time: '09:32',
                delay: 2500
            },
            {
                type: 'message',
                user: 'Leon',
                avatar: 'L',
                color: 'leon',
                text: 'Wow! Das sieht mega aus! 😍',
                time: '09:32',
                delay: 2000
            },
            {
                type: 'message',
                user: 'Emma',
                avatar: 'E',
                color: 'emma',
                text: 'Kann ich das für Insta verwenden?',
                time: '09:33',
                delay: 2000
            },
            {
                type: 'message',
                user: 'Sarah',
                avatar: 'S',
                color: 'sarah',
                text: 'Klar! 💚',
                time: '09:33',
                delay: 1500
            },
            {
                type: 'date',
                text: 'Dienstag, 16. April 2024',
                delay: 2000
            },
            {
                type: 'message',
                user: 'Mia',
                avatar: 'M',
                color: 'mia',
                text: 'Morgen! Ich hab jetzt drei Caterer angeschrieben, warte noch auf Antworten',
                time: '08:45',
                delay: 3000
            },
            {
                type: 'message',
                user: 'Leon',
                avatar: 'L',
                color: 'leon',
                text: 'Super! Ich hab ein kleines Problem mit den Kabeln... Die sind teilweise beschädigt 😬',
                time: '09:15',
                delay: 3500
            },
            {
                type: 'message',
                user: 'Jonas',
                avatar: 'J',
                color: 'jonas',
                text: 'Oh nein! Brauchst du Hilfe beim Besorgen neuer?',
                time: '09:16',
                delay: 2500
            },
            {
                type: 'message',
                user: 'Leon',
                avatar: 'L',
                color: 'leon',
                text: 'Wäre cool! Ich schick dir gleich ne Liste',
                time: '09:17',
                delay: 2500
            },
            {
                type: 'message',
                user: 'Emma',
                avatar: 'E',
                color: 'emma',
                text: 'Hab grad den ersten Post hochgeladen! 127 Likes in 10 Minuten 🎉',
                time: '10:30',
                delay: 3000
            },
            {
                type: 'message',
                user: 'Sarah',
                avatar: 'S',
                color: 'sarah',
                text: 'Nice! Der Post sieht echt professionell aus 👏',
                time: '10:32',
                delay: 2000
            },
            {
                type: 'message',
                user: 'Mia',
                avatar: 'M',
                color: 'mia',
                text: 'Hab von einem Caterer Absage bekommen... Budget zu klein. Ich frag noch bei den anderen nach',
                time: '11:45',
                delay: 3500
            },
            {
                type: 'date',
                text: 'Mittwoch, 17. April 2024',
                delay: 2000
            },
            {
                type: 'message',
                user: 'Leon',
                avatar: 'L',
                color: 'leon',
                text: 'Good News! Kabel-Problem gelöst! Jonas hat mir geholfen, die neuen sind top! 🔌✅',
                time: '08:20',
                delay: 3000
            },
            {
                type: 'message',
                user: 'Jonas',
                avatar: 'J',
                color: 'jonas',
                text: 'Teamwork! 💪',
                time: '08:21',
                delay: 1500
            },
            {
                type: 'message',
                user: 'Sarah',
                avatar: 'S',
                color: 'sarah',
                text: 'Kleines Update von mir: Die Firma hat die Deko-Materialien bestätigt! Kommt Donnerstag an',
                time: '09:00',
                delay: 3000
            },
            {
                type: 'message',
                user: 'Mia',
                avatar: 'M',
                color: 'mia',
                text: 'Bei mir läufts nicht so gut... Zweiter Caterer hat auch abgesagt. Der dritte reagiert nicht.',
                time: '09:15',
                delay: 3500
            },
            {
                type: 'message',
                user: 'Emma',
                avatar: 'E',
                color: 'emma',
                text: 'Oh man, das ist echt blöd... Soll ich dir helfen zu suchen?',
                time: '09:17',
                delay: 2500
            },
            {
                type: 'message',
                user: 'Mia',
                avatar: 'M',
                color: 'mia',
                text: 'Ne, geht schon. Ich find schon noch jemanden. Danke aber!',
                time: '09:19',
                delay: 2500
            },
            {
                type: 'system',
                text: 'Mia hat die Gruppe um 14:30 Uhr verlassen',
                delay: 4000
            },
            {
                type: 'system',
                text: 'Mia ist der Gruppe um 14:35 Uhr wieder beigetreten',
                delay: 2000
            },
            {
                type: 'message',
                user: 'Leon',
                avatar: 'L',
                color: 'leon',
                text: 'Hey Mia, alles ok?',
                time: '14:36',
                delay: 2500
            },
            {
                type: 'message',
                user: 'Mia',
                avatar: 'M',
                color: 'mia',
                text: 'Ja ja, hatte nur kurz schlechtes Netz',
                time: '14:40',
                delay: 3000
            },
            {
                type: 'date',
                text: 'Donnerstag, 18. April 2024',
                delay: 2000
            },
            {
                type: 'message',
                user: 'Jonas',
                avatar: 'J',
                color: 'jonas',
                text: 'SCHLECHTE NEWS 😭 Der Headliner hat abgesagt!!!',
                time: '10:00',
                delay: 3000
            },
            {
                type: 'message',
                user: 'Leon',
                avatar: 'L',
                color: 'leon',
                text: 'WAS?! Warum denn?',
                time: '10:01',
                delay: 2000
            },
            {
                type: 'message',
                user: 'Jonas',
                avatar: 'J',
                color: 'jonas',
                text: 'Krankheit... Aber ich bin schon am Suchen nach Ersatz!',
                time: '10:02',
                delay: 2500
            },
            {
                type: 'message',
                user: 'Emma',
                avatar: 'E',
                color: 'emma',
                text: 'Mist... Meine Reichweite ist heute auch total eingebrochen 📉 Keine Ahnung warum',
                time: '10:30',
                delay: 3000
            },
            {
                type: 'message',
                user: 'Sarah',
                avatar: 'S',
                color: 'sarah',
                text: 'Ist heute irgendwie alles stressig... Meine Deko-Lieferung ist zu spät gekommen',
                time: '11:00',
                delay: 3000
            },
            {
                type: 'message',
                user: 'Mia',
                avatar: 'M',
                color: 'mia',
                text: 'Ja, bei mir auch Stress. Immer noch kein Caterer...',
                time: '11:15',
                delay: 2500
            },
            {
                type: 'message',
                user: 'Mia',
                avatar: 'M',
                color: 'mia',
                text: 'Vielleicht sollte ich das echt an jemand anderen abgeben. Ich krieg das nicht hin.',
                time: '11:16',
                delay: 3500
            },
            {
                type: 'message',
                user: 'Leon',
                avatar: 'L',
                color: 'leon',
                text: 'Hey, nicht aufgeben! Wir schaffen das alle zusammen 💪',
                time: '11:18',
                delay: 2500
            },
            {
                type: 'date',
                text: 'Freitag, 19. April 2024',
                delay: 2000
            },
            {
                type: 'message',
                user: 'Jonas',
                avatar: 'J',
                color: 'jonas',
                text: 'GUTE NACHRICHTEN! 🎉 Ich hab einen NOCH besseren Headliner gefunden! DJ Sarah Connor ist dabei!',
                time: '08:00',
                delay: 3000
            },
            {
                type: 'message',
                user: 'Leon',
                avatar: 'L',
                color: 'leon',
                text: 'WHAAAAT?! Das ist ja der Hammer!! 🔥',
                time: '08:01',
                delay: 2000
            },
            {
                type: 'message',
                user: 'Emma',
                avatar: 'E',
                color: 'emma',
                text: 'Meine Reichweite ist auch wieder voll da! Sogar besser als vorher! 📈✨',
                time: '08:30',
                delay: 3000
            },
            {
                type: 'message',
                user: 'Sarah',
                avatar: 'S',
                color: 'sarah',
                text: 'Und meine Deko ist komplett angekommen! Alles perfekt 🎨',
                time: '09:00',
                delay: 2500
            },
            {
                type: 'message',
                user: 'Leon',
                avatar: 'L',
                color: 'leon',
                text: 'Nice! Läuft bei euch! 😊',
                time: '09:05',
                delay: 2000
            },
            {
                type: 'message',
                user: 'Jonas',
                avatar: 'J',
                color: 'jonas',
                text: 'Und bei dir Mia? Schon was gefunden beim Catering?',
                time: '09:30',
                delay: 2500
            },
            {
                type: 'message',
                user: 'Mia',
                avatar: 'M',
                color: 'mia',
                text: '...',
                time: '09:35',
                delay: 4000
            },
            {
                type: 'message',
                user: 'Mia',
                avatar: 'M',
                color: 'mia',
                text: 'Nein. Immer noch nichts.',
                time: '09:36',
                delay: 3000
            },
            {
                type: 'message',
                user: 'Mia',
                avatar: 'M',
                color: 'mia',
                text: 'Ich glaub ich bin einfach nicht gut genug dafür.',
                time: '09:37',
                delay: 3500
            },
            {
                type: 'message',
                user: 'Emma',
                avatar: 'E',
                color: 'emma',
                text: 'Mia, so ein Quatsch! Du machst das super!',
                time: '09:39',
                delay: 2500
            },
            {
                type: 'message',
                user: 'Mia',
                avatar: 'M',
                color: 'mia',
                text: 'Ich weiß nicht... Vielleicht sollte wirklich jemand anders das übernehmen',
                time: '09:42',
                delay: 3500
            },
            {
                type: 'system',
                text: 'Mia ist offline',
                delay: 3000
            },
            {
                type: 'message',
                user: 'Leon',
                avatar: 'L',
                color: 'leon',
                text: 'Leute, macht ihr euch auch Sorgen um Mia?',
                time: '10:00',
                delay: 3000
            },
            {
                type: 'message',
                user: 'Sarah',
                avatar: 'S',
                color: 'sarah',
                text: 'Ja... Sie wirkt in letzter Zeit echt down',
                time: '10:02',
                delay: 2500
            },
            {
                type: 'message',
                user: 'Jonas',
                avatar: 'J',
                color: 'jonas',
                text: 'Sollten wir mit ihr reden?',
                time: '10:03',
                delay: 2500
            },
            {
                type: 'message',
                user: 'Emma',
                avatar: 'E',
                color: 'emma',
                text: 'Ja, definitiv. Sie braucht unsere Unterstützung 💚',
                time: '10:05',
                delay: 2500
            },
            {
                type: 'system',
                text: 'Ende der Vorschau',
                delay: 3000
            }
        ];

        const chatMessages = document.getElementById('chatMessages');
        let messageIndex = 0;
        let currentTimeout;

        function addDateDivider(text) {
            const divider = document.createElement('div');
            divider.className = 'date-divider';
            divider.innerHTML = `<span>${text}</span>`;
            chatMessages.appendChild(divider);
            scrollToBottom();
        }

        function addSystemMessage(text) {
            const systemMsg = document.createElement('div');
            systemMsg.className = 'system-message';
            systemMsg.innerHTML = `<span>${text}</span>`;
            chatMessages.appendChild(systemMsg);
            scrollToBottom();
        }

        function showTypingIndicator(user, avatar, color) {
            const typing = document.createElement('div');
            typing.className = 'typing-indicator';
            typing.id = 'typing-indicator';
            typing.innerHTML = `
                <div class="avatar ${color}">${avatar}</div>
                <div class="message-content">
                    <div class="message-header">
                        <span class="username">${user}</span>
                    </div>
                    <div class="typing-bubble">
                        <div class="typing-dots">
                            <span></span>
                            <span></span>
                            <span></span>
                        </div>
                    </div>
                </div>
            `;
            chatMessages.appendChild(typing);
            scrollToBottom();
        }

        function removeTypingIndicator() {
            const typing = document.getElementById('typing-indicator');
            if (typing) {
                typing.remove();
            }
        }

        function addMessage(user, avatar, color, text, time) {
            const message = document.createElement('div');
            message.className = 'message';
            message.innerHTML = `
                <div class="avatar ${color}">${avatar}</div>
                <div class="message-content">
                    <div class="message-header">
                        <span class="username">${user}</span>
                        <span class="timestamp">${time}</span>
                    </div>
                    <div class="message-bubble">${text}</div>
                </div>
            `;
            chatMessages.appendChild(message);
            scrollToBottom();
        }

        function scrollToBottom() {
            chatMessages.scrollTop = chatMessages.scrollHeight;
        }

        function processNextMessage() {
            if (messageIndex >= messages.length) {
                return;
            }

            const msg = messages[messageIndex];
            messageIndex++;

            if (msg.type === 'date') {
                addDateDivider(msg.text);
                currentTimeout = setTimeout(processNextMessage, msg.delay || 1000);
            } else if (msg.type === 'system') {
                addSystemMessage(msg.text);
                currentTimeout = setTimeout(processNextMessage, msg.delay || 2000);
            } else if (msg.type === 'message') {
                // Show typing indicator
                showTypingIndicator(msg.user, msg.avatar, msg.color);
                
                // After typing delay, show message
                currentTimeout = setTimeout(() => {
                    removeTypingIndicator();
                    addMessage(msg.user, msg.avatar, msg.color, msg.text, msg.time);
                    currentTimeout = setTimeout(processNextMessage, 1000);
                }, msg.delay || 2000);
            }
        }

        // Start the chat animation
        setTimeout(() => {
            processNextMessage();
        }, 1000);
    </script>
</body>
</html>
