# <!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>My Daily Journal</title>
    <style>
        body {
            font-family: Arial, sans-serif;
            text-align: center;
        }
        .container {
            display: flex;
            flex-wrap: wrap;
            justify-content: center;
            gap: 10px;
            margin-top: 20px;
        }
        .box {
            border: 1px solid #ccc;
            padding: 15px;
            width: 250px;
        }
        .image-preview {
            margin-top: 10px;
            max-width: 100%;
            height: auto;
            display: none;
        }
        .divider {
            width: 80%;
            height: 2px;
            background-color: black;
            margin: 10px auto;
        }
    </style>
</head>
<body>
    <h1>STUDENT OF RIYDO TRADING</h1>
    <div class="container">
        <div class="box">
            <label for="date">Select Date:</label>
            <input type="date" id="date">
        </div>
        <div class="box">
            <label for="market">Market Name:</label>
            <select id="market">
                <option>Euro GBP</option>
                <option>GBP USD</option>
                <option>Euro USD</option>
                <option>USD CID</option>
                <option>GBP JPY</option>
                <option>AUD NZD</option>
                <option>AUD USD</option>
                <option>XAUUSD</option>
            </select>
        </div>
        <div class="box">
            <label for="time">Select Time:</label>
            <input type="time" id="time">
        </div>
        <div class="box">
            <p>Stop Loss & Take Profit</p>
            <input type="checkbox" id="profit"><label for="profit">Profit</label>
            <br>
            <input type="checkbox" id="loss"><label for="loss">Loss</label>
        </div>
        <div class="box">
            <label for="reason">Reason:</label>
            <textarea id="reason" rows="5" placeholder="Write your reason..."></textarea>
            <br><br>
            <label for="photo">Upload Photo:</label>
            <input type="file" id="photo" accept="image/*" onchange="previewImage(event)">
            <br>
            <img id="imagePreview" class="image-preview">
        </div>
    </div>
    <button onclick="generateReport()">OK</button>
    <div class="divider"></div>
    <div class="divider"></div>
    <div id="reportSection"></div>
    <script>
        let reportCount = 1;
        
        function previewImage(event) {
            const reader = new FileReader();
            reader.onload = function () {
                const imagePreview = document.getElementById("imagePreview");
                imagePreview.src = reader.result;
                imagePreview.style.display = "block";
            };
            reader.readAsDataURL(event.target.files[0]);
        }
        
        function generateReport() {
            const date = document.getElementById("date").value;
            const market = document.getElementById("market").value;
            const time = document.getElementById("time").value;
            const profit = document.getElementById("profit").checked ? "Profit" : "";
            const loss = document.getElementById("loss").checked ? "Loss" : "";
            const reason = document.getElementById("reason").value;
            
            let report = `<h3>Report ${reportCount}</h3>`;
            report += `<p><strong>Date:</strong> ${date}</p>`;
            report += `<p><strong>Market:</strong> ${market}</p>`;
            report += `<p><strong>Time:</strong> ${time}</p>`;
            report += `<p><strong>Outcome:</strong> ${profit} ${loss}</p>`;
            report += `<p><strong>Reason:</strong> ${reason}</p>`;
            
            const reportSection = document.getElementById("reportSection");
            reportSection.innerHTML += report + "<hr>";
            
            reportCount++;
        }
    </script>
</body>
</html>
