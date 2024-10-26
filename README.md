<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Bet Calculator</title>
</head>
<body>
    <h2>Betting Calculator</h2>

    <label for="betType">Select Bet Type:</label>
    <select id="betType" onchange="toggleOptions()">
        <option value="number">Number</option>
        <option value="color">Color</option>
        <option value="range">Range (Low/High)</option>
    </select>

    <div id="numberInput" style="display: none;">
        <label for="betNumber">Choose Number (1-10):</label>
        <input type="number" id="betNumber" min="1" max="10">
    </div>

    <div id="colorInput" style="display: none;">
        <label for="betColor">Choose Color:</label>
        <select id="betColor">
            <option value="red">Red</option>
            <option value="black">Black</option>
        </select>
    </div>

    <div id="rangeInput" style="display: none;">
        <label for="betRange">Choose Range:</label>
        <select id="betRange">
            <option value="low">Low (1-5)</option>
            <option value="high">High (6-10)</option>
        </select>
    </div>

    <label for="betAmount">Enter Bet Amount:</label>
    <input type="number" id="betAmount" placeholder="Bet amount">

    <button onclick="calculateWinnings()">Calculate Winnings</button>

    <h3 id="result"></h3>

    <script>
        function toggleOptions() {
            document.getElementById('numberInput').style.display = 'none';
            document.getElementById('colorInput').style.display = 'none';
            document.getElementById('rangeInput').style.display = 'none';

            const betType = document.getElementById('betType').value;
            if (betType === 'number') {
                document.getElementById('numberInput').style.display = 'block';
            } else if (betType === 'color') {
                document.getElementById('colorInput').style.display = 'block';
            } else if (betType === 'range') {
                document.getElementById('rangeInput').style.display = 'block';
            }
        }

        function calculateWinnings() {
            const betType = document.getElementById('betType').value;
            const betAmount = parseFloat(document.getElementById('betAmount').value);
            let odds = 0;

            if (betType === 'number') {
                odds = 10; // High odds for specific number
            } else if (betType === 'color') {
                odds = 2; // Lower odds for color
            } else if (betType === 'range') {
                odds = 3; // Medium odds for range
            }

            const winnings = betAmount * odds;
            document.getElementById('result').innerHTML = `Potential Winnings: $${winnings}`;
        }
    </script>
</body>
</html>
