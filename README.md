<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0, user-scalable=no">
    <title>Frosty Farms</title>
    <style>
        body {
            font-family: 'Comic Sans MS', cursive, sans-serif;
            display: flex;
            flex-direction: column;
            align-items: center;
            justify-content: center;
            margin: 0;
            padding: 20px;
            background-color: #ffefd5; /* Light peach background */
        }
        .farm-status {
            margin-bottom: 20px;
            text-align: center;
            border: 3px solid #8b4513; /* Brown border for farm feel */
            padding: 15px;
            background-color: #fff8dc; /* Cornsilk background for farm charm */
            border-radius: 10px;
        }
        .buttons-container {
            display: flex;
            flex-wrap: wrap;
            justify-content: center;
            gap: 15px;
        }
        button, select {
            margin: 10px;
            padding: 12px;
            font-size: 18px;
            border: 2px solid #228b22; /* Forest green border */
            border-radius: 8px;
            background-color: #98fb98; /* Pale green button color */
            color: #4b0082; /* Indigo text for contrast */
            cursor: pointer;
            box-shadow: 2px 2px 5px #888888;
        }
        button:hover, select:hover {
            background-color: #7cfc00; /* Light green for hover effect */
        }
        h1 {
            color: #6b8e23; /* Olive green for farm theme */
            text-shadow: 2px 2px #fff;
            font-size: 3em;
            letter-spacing: 2px;
            text-transform: uppercase;
            font-weight: bold;
        }
        .rules {
            border: 3px dashed #8b4513;
            padding: 20px;
            margin-top: 20px;
            background-color: #f0e68c; /* Khaki background for rule book */
            border-radius: 10px;
        }
        .farmer-rank {
            font-weight: bold;
            font-size: 2em;
            color: #ff4500; /* Orange red to make it stand out */
            text-shadow: 2px 2px 4px #000; /* Shadow for emphasis */
            letter-spacing: 1px;
        }
        .money-display {
            font-size: 2em;
            color: #ffd700; /* Gold color for importance */
            font-weight: bold;
            text-shadow: 1px 1px 3px #000;
            padding: 10px;
            background-color: #fff8dc;
            border: 3px solid #228b22;
            border-radius: 10px;
            margin-top: 15px;
        }
    </style>
</head>
<body>
    <h1>Frosty Farms</h1>
    <div class="farm-status">
        <p>Chickens: <span id="chickens">2</span></p>
        <p>Eggs: <span id="eggs">0</span></p>
        <p>Cows: <span id="cows">0</span></p>
        <p>Milk: <span id="milk">0</span></p>
        <p>Goats: <span id="goats">0</span></p>
        <p>Goat Milk: <span id="goatMilk">0</span></p>
        <p>Sheep: <span id="sheep">0</span></p>
        <p>Wool: <span id="wool">0</span></p>
        <p>Roosters: <span id="roosters">0</span></p>
        <p>Egg Production Boost: <span id="eggBoost">0%</span></p>
        <p class="money-display">Money: $<span id="money">0</span></p>
        <p>Farmer Rank: <span id="farmerRank" class="farmer-rank">Backyard DIY Farmer</span></p>
    </div>

    <div class="buttons-container">
        <button onclick="collectEggs()">🐔 Collect Eggs</button>
        <button onclick="sellEggs()">💰 Sell Eggs</button>
        <button onclick="collectMilk()">🐄 Collect Milk</button>
        <button onclick="sellMilk()">💵 Sell Milk</button>
        <button onclick="collectGoatMilk()">🐐 Collect Goat Milk</button>
        <button onclick="sellGoatMilk()">💵 Sell Goat Milk</button>
        <button onclick="collectWool()">🐑 Collect Wool</button>
        <button onclick="sellWool()">💵 Sell Wool</button>
    </div>

    <select id="upgrade-options" onchange="buyUpgrade()">
        <option value="">-- Buy Upgrade --</option>
        <option value="chicken">🐔 Buy a Chicken ($20)</option>
        <option value="autoCollector">🤖 Automatic Egg Collector ($150)</option>
        <option value="biggerCoop">🏠 Upgrade Coop to Hold More Chickens ($500)</option>
        <option value="fertilizedFeed">🌾 Fertilized Feed for Faster Egg Production ($800)</option>
        <option value="buyCow">🐄 Buy a Cow ($1000)</option>
        <option value="autoMilker">🍼 Automatic Milking Machine ($2000)</option>
        <option value="buyGoat">🐐 Buy a Goat ($1500)</option>
        <option value="autoGoatMilker">🐐🍼 Automatic Goat Milker ($2500)</option>
        <option value="buyField">🌱 Buy a Crop Field ($2000)</option>
        <option value="buyTractor">🚜 Buy a Tractor for Automated Farming ($3000)</option>
        <option value="buyWindmill">🌬️ Buy a Windmill to Increase Crop Efficiency ($5000)</option>
        <option value="buildProcessingPlant">🏭 Build a Processing Plant ($8000)</option>
        <option value="buySolarPanels">🔆 Buy Solar Panels for Passive Income ($10000)</option>
        <option value="buyBarn">🏚️ Build a Barn for More Livestock ($12000)</option>
        <option value="buySheep">🐑 Buy a Sheep ($3000)</option>
        <option value="autoShearer">✂️ Automatic Sheep Shearer ($5000)</option>
        <option value="buyGreenhouse">🏡 Buy a Greenhouse to Grow Exotic Crops ($15000)</option>
        <option value="buyApiary">🐝 Buy an Apiary for Honey Production ($20000)</option>
        <option value="buyCombineHarvester">🚜 Buy a Combine Harvester for Crop Efficiency ($30000)</option>
        <option value="buildCreamery">🧀 Build a Creamery for Cheese Production ($35000)</option>
        <option value="buyRooster">🐓 Buy a Rooster to Boost Egg Production ($7000)</option>
    </select>

    <div class="rules">
        <h2>Game Rule Book & Directions</h2>
        <p>Welcome to Frosty Farms! Here is how you play:</p>
        <ul>
            <li>Start with a small farm and collect products such as eggs, milk, goat milk, wool, and more to earn money.</li>
            <li>Use your earnings to buy upgrades like more animals, automated collectors, and advanced farming equipment.</li>
            <li>Expand your farm and improve efficiency by purchasing items such as tractors, windmills, solar panels, and other tools.</li>
            <li>New addition: Buy roosters to boost egg production for your chickens!</li>
            <li>Your goal is to become the ultimate farm tycoon by reaching the highest farmer rank!</li>
        </ul>
        <h3>Farmer Ranks:</h3>
        <p>Your farmer rank will change as you earn more money and expand your farm. Here are the different titles you can achieve:</p>
        <ul>
            <li><strong>Backyard DIY Farmer</strong> - Starting rank</li>
            <li><strong>Hobbyist Homesteader</strong> - Reach $10,000</li>
            <li><strong>Local Produce Pro</strong> - Reach $100,000</li>
            <li><strong>Country Rancher</strong> - Reach $1,000,000</li>
            <li><strong>Regional Agronomist</strong> - Reach $10,000,000</li>
            <li><strong>National Harvest Hero</strong> - Reach $100,000,000</li>
            <li><strong>Continental Crop King/Queen</strong> - Reach $1,000,000,000</li>
            <li><strong>Global Farming Phenom</strong> - Reach $10,000,000,000</li>
            <li><strong>Legendary Uptime Land Farmer</strong> - Reach $100,000,000,000</li>
        </ul>
        <p>Each rank comes with its own unique rewards and challenges, pushing you to expand and automate your farm operations!</p>
        <h3>Directions:</h3>
        <p>Click the buttons to collect resources and sell them for money. Use the dropdown to buy upgrades to increase your farm's productivity.</p>
        <p>The game continues indefinitely, with each milestone becoming progressively harder to reach, but also offering greater rewards.</p>
    </div>

    <script>
        let chickens = 2;
        let eggs = 0;
        let money = 0;
        let autoCollector = false;
        let autoCollectorInterval = null;
        let cows = 0;
        let milk = 0;
        let autoMilker = false;
        let goats = 0;
        let goatMilk = 0;
        let autoGoatMilker = false;
        let sheep = 0;
        let wool = 0;
        let autoShearer = false;
        let roosters = 0;
        let eggProductionBoost = 0;
        let cropFields = 0;
        let crops = 0;
        let processingPlant = false;
        let solarPanels = 0;
        let passiveIncomeInterval = null;
        let farmerRank = "Backyard DIY Farmer";

        function collectEggs() {
            let boostedEggs = chickens + Math.floor(chickens * (eggProductionBoost / 100));
            eggs += boostedEggs;
            updateFarmStatus();
        }

        function sellEggs() {
            if (eggs > 0) {
                money += eggs * 0.3; // Eggs sell for $0.3 each
                eggs = 0;
                updateFarmStatus();
            } else {
                alert("No eggs to sell!");
            }
        }

        function collectMilk() {
            milk += cows;
            updateFarmStatus();
        }

        function sellMilk() {
            if (milk > 0) {
                money += milk * 2; // Milk sells for $2 each
                milk = 0;
                updateFarmStatus();
            } else {
                alert("No milk to sell!");
            }
        }

        function collectGoatMilk() {
            goatMilk += goats;
            updateFarmStatus();
        }

        function sellGoatMilk() {
            if (goatMilk > 0) {
                money += goatMilk * 3; // Goat milk sells for $3 each
                goatMilk = 0;
                updateFarmStatus();
            } else {
                alert("No goat milk to sell!");
            }
        }

        function collectWool() {
            wool += sheep;
            updateFarmStatus();
        }

        function sellWool() {
            if (wool > 0) {
                money += wool * 4; // Wool sells for $4 each
                wool = 0;
                updateFarmStatus();
            } else {
                alert("No wool to sell!");
            }
        }

        function buyUpgrade() {
            const upgrade = document.getElementById("upgrade-options").value;
            if (upgrade === "chicken" && money >= 20) {
                chickens++;
                money -= 20;
            } else if (upgrade === "autoCollector" && money >= 150) {
                autoCollector = true;
                money -= 150;
                startAutoCollector();
            } else if (upgrade === "biggerCoop" && money >= 500) {
                chickens += 2;
                money -= 500;
            } else if (upgrade === "fertilizedFeed" && money >= 800) {
                chickens += Math.floor(chickens / 3);
                money -= 800;
            } else if (upgrade === "buyCow" && money >= 1000) {
                cows++;
                money -= 1000;
            } else if (upgrade === "autoMilker" && money >= 2000) {
                autoMilker = true;
                money -= 2000;
                startAutoMilker();
            } else if (upgrade === "buyGoat" && money >= 1500) {
                goats++;
                money -= 1500;
            } else if (upgrade === "autoGoatMilker" && money >= 2500) {
                autoGoatMilker = true;
                money -= 2500;
                startAutoGoatMilker();
            } else if (upgrade === "buyField" && money >= 2000) {
                cropFields++;
                money -= 2000;
            } else if (upgrade === "buyTractor" && money >= 3000) {
                money -= 3000;
                startAutoFarming();
            } else if (upgrade === "buyWindmill" && money >= 5000) {
                money -= 5000;
                startWindmillBoost();
            } else if (upgrade === "buildProcessingPlant" && money >= 8000) {
                processingPlant = true;
                money -= 8000;
            } else if (upgrade === "buySolarPanels" && money >= 10000) {
                solarPanels++;
                money -= 10000;
                startSolarPanelIncome();
            } else if (upgrade === "buyBarn" && money >= 12000) {
                money -= 12000;
                startBarnExpansion();
            } else if (upgrade === "buySheep" && money >= 3000) {
                sheep++;
                money -= 3000;
            } else if (upgrade === "autoShearer" && money >= 5000) {
                autoShearer = true;
                money -= 5000;
                startAutoShearing();
            } else if (upgrade === "buyGreenhouse" && money >= 15000) {
                money -= 15000;
                startGreenhouse();
            } else if (upgrade === "buyApiary" && money >= 20000) {
                money -= 20000;
                startApiary();
            } else if (upgrade === "buyCombineHarvester" && money >= 30000) {
                money -= 30000;
                startCombineHarvesting();
            } else if (upgrade === "buildCreamery" && money >= 35000) {
                processingPlant = true;
                money -= 35000;
                startCreamery();
            } else if (upgrade === "buyRooster" && money >= 7000) {
                roosters++;
                eggProductionBoost += 5; // Each rooster boosts egg production by 5%
                money -= 7000;
            } else {
                alert("Not enough money for this upgrade or invalid option!");
            }
            updateFarmStatus();
        }

        function startAutoCollector() {
            if (!autoCollectorInterval) {
                autoCollectorInterval = setInterval(() => {
                    collectEggs();
                }, 2000); // Collect eggs every 2 seconds
            }
        }

        function startAutoMilker() {
            if (!autoMilker) return;
            setInterval(() => {
                collectMilk();
            }, 3000); // Collect milk every 3 seconds
        }

        function startAutoGoatMilker() {
            if (!autoGoatMilker) return;
            setInterval(() => {
                collectGoatMilk();
            }, 4000); // Collect goat milk every 4 seconds
        }

        function startAutoShearing() {
            if (!autoShearer) return;
            setInterval(() => {
                collectWool();
            }, 5000); // Collect wool every 5 seconds
        }

        function startSolarPanelIncome() {
            if (!passiveIncomeInterval) {
                passiveIncomeInterval = setInterval(() => {
                    money += solarPanels * 20; // Solar panels generate passive income
                    updateFarmStatus();
                }, 5000); // Every 5 seconds
            }
        }

        function updateFarmStatus() {
            document.getElementById("chickens").innerText = chickens;
            document.getElementById("eggs").innerText = eggs;
            document.getElementById("cows").innerText = cows;
            document.getElementById("milk").innerText = milk;
            document.getElementById("goats").innerText = goats;
            document.getElementById("goatMilk").innerText = goatMilk;
            document.getElementById("sheep").innerText = sheep;
            document.getElementById("wool").innerText = wool;
            document.getElementById("roosters").innerText = roosters;
            document.getElementById("eggBoost").innerText = eggProductionBoost + "%";
            document.getElementById("money").innerText = money;
            updateFarmerRank();
        }

        function updateFarmerRank() {
            if (money >= 100000000000) {
                farmerRank = "Legendary Uptime Land Farmer";
            } else if (money >= 10000000000) {
                farmerRank = "Global Farming Phenom";
            } else if (money >= 1000000000) {
                farmerRank = "Continental Crop King/Queen";
            } else if (money >= 100000000) {
                farmerRank = "National Harvest Hero";
            } else if (money >= 10000000) {
                farmerRank = "Regional Agronomist";
            } else if (money >= 1000000) {
                farmerRank = "Country Rancher";
            } else if (money >= 100000) {
                farmerRank = "Local Produce Pro";
            } else if (money >= 10000) {
                farmerRank = "Hobbyist Homesteader";
            } else {
                farmerRank = "Backyard DIY Farmer";
            }
            document.getElementById("farmerRank").innerText = farmerRank;
        }
    </script>
</body>
</html>
