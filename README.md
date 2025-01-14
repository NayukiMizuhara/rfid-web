<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>RFID Reader</title>
    <script>
        async function fetchRFID() {
            try {
                const response = await fetch('http://192.168.1.100/read_rfid'); // Ganti dengan IP ESP32 Anda
                if (!response.ok) {
                    throw new Error('Failed to fetch RFID data');
                }
                const data = await response.json();
                document.getElementById('rfidDisplay').textContent = data.rfid || "No data received";
            } catch (error) {
                document.getElementById('rfidDisplay').textContent = error.message;
            }
        }

        setInterval(fetchRFID, 2000); // Auto-refresh every 2 seconds
    </script>
    <style>
        body {
            font-family: Arial, sans-serif;
            text-align: center;
            margin: 50px;
        }

        #rfidDisplay {
            font-size: 2em;
            color: #333;
            margin-top: 20px;
        }

        .info {
            margin-top: 10px;
            color: #555;
        }
    </style>
</head>
<body>
    <h1>RFID Reader</h1>
    <p id="rfidDisplay">Waiting for data...</p>
    <p class="info">Make sure your RFID is scanned.</p>
</body>
</html>
