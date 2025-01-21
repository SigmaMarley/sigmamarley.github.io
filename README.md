<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Senegal Adventure Game</title>
    <style>
        body {
            font-family: Arial, sans-serif;
            margin: 0;
            padding: 0;
            background-color: #f4f4f9;
        }
        .container {
            padding: 20px;
            max-width: 800px;
            margin: auto;
        }
        h1, h2 {
            text-align: center;
        }
        .location, .action, .message {
            margin-bottom: 20px;
        }
        button {
            display: block;
            width: 100%;
            padding: 10px;
            margin: 5px 0;
            font-size: 16px;
            background-color: #4caf50;
            color: white;
            border: none;
            cursor: pointer;
        }
        button:hover {
            background-color: #45a049;
        }
        .hidden {
            display: none;
        }
    </style>
</head>
<body>
    <div class="container">
        <h1>Welcome to the Senegal Adventure Game!</h1>
        <p>Explore fascinating locations in Senegal and learn fun facts along the way. Click your choices to proceed and enjoy the journey!</p>

        <div id="main-menu">
            <h2>Where would you like to go?</h2>
            <div id="locations">
                <button onclick="explore('dakar')">Dakar</button>
                <button onclick="explore('saintLouis')">Saint-Louis</button>
                <button onclick="explore('sineSaloum')">Sine-Saloum Delta</button>
                <button onclick="explore('casamance')">Casamance Region</button>
                <button onclick="explore('lakeRetba')">Lake Retba</button>
                <button onclick="explore('goreeIsland')">Gorée Island</button>
            </div>
        </div>

        <div id="location-content" class="hidden">
            <h2 id="location-title"></h2>
            <div id="action-buttons"></div>
            <div class="message" id="message-box"></div>
            <button onclick="goBack()">Go Back</button>
        </div>
    </div>

    <script>
        const locations = {
            dakar: {
                name: "Dakar",
                actions: [
                    { text: "Visit Gorée Island", message: "Gorée Island is a UNESCO World Heritage Site known for its role in the transatlantic slave trade." },
                    { text: "Explore the African Renaissance Monument", message: "The African Renaissance Monument is the tallest statue in Africa, symbolizing Africa's resilience and progress." },
                    { text: "Relax at Ngor Beach", message: "Ngor Beach is perfect for relaxing and enjoying vibrant nightlife." },
                    { text: "Pet stray dogs", message: "You find friendly stray dogs and enjoy their company!" }
                ]
            },
            saintLouis: {
                name: "Saint-Louis",
                actions: [
                    { text: "Stroll through the historic center", message: "The historic center of Saint-Louis is a UNESCO World Heritage Site with colorful colonial buildings." },
                    { text: "Visit the Djoudj Bird Sanctuary", message: "The Djoudj Bird Sanctuary hosts over 1.5 million birds, including pelicans and flamingos." },
                    { text: "Cross the Faidherbe Bridge", message: "The Faidherbe Bridge, designed by Gustave Eiffel, is an engineering marvel." }
                ]
            },
            sineSaloum: {
                name: "Sine-Saloum Delta",
                actions: [
                    { text: "Go on a boat tour", message: "A boat tour offers stunning views of waterways, wildlife, and mangroves." },
                    { text: "Visit a Serer village", message: "Experience warm hospitality and learn about the Serer people's rich culture and history." },
                    { text: "Learn about mangroves", message: "Mangroves protect coastlines and support marine life. Learn about their importance here." }
                ]
            },
            casamance: {
                name: "Casamance Region",
                actions: [
                    { text: "Explore the Cap Skirring beaches", message: "Cap Skirring offers pristine beaches and a laid-back atmosphere." },
                    { text: "Visit the Simenti National Park", message: "Simenti National Park is home to diverse wildlife and beautiful landscapes." },
                    { text: "Learn about the Diola culture", message: "Learn about the traditional arts, crafts, and music of the Diola people." }
                ]
            },
            lakeRetba: {
                name: "Lake Retba",
                actions: [
                    { text: "Take a boat ride", message: "Admire the vibrant pink water and unique beauty of Lake Retba." },
                    { text: "Learn about the salt harvesting", message: "Witness traditional salt harvesting methods and learn about their importance." },
                    { text: "Enjoy the pink water", message: "The lake's pink color comes from algae thriving in its salty waters. Take a dip!" }
                ]
            },
            goreeIsland: {
                name: "Gorée Island",
                actions: [
                    { text: "Visit the House of Slaves", message: "The House of Slaves is a poignant reminder of the slave trade's horrors." },
                    { text: "Explore historical sites", message: "Gorée Island is rich in historical sites, colonial buildings, and vibrant markets." },
                    { text: "Enjoy the beaches", message: "Gorée Island offers tranquil beaches with views of the Atlantic Ocean." }
                ]
            }
        };

        function explore(locationKey) {
            const location = locations[locationKey];
            document.getElementById("main-menu").classList.add("hidden");
            document.getElementById("location-content").classList.remove("hidden");
            document.getElementById("location-title").textContent = location.name;

            const actionButtons = document.getElementById("action-buttons");
            actionButtons.innerHTML = "";
            location.actions.forEach(action => {
                const button = document.createElement("button");
                button.textContent = action.text;
                button.onclick = () => {
                    document.getElementById("message-box").textContent = action.message;
                };
                actionButtons.appendChild(button);
            });
        }

        function goBack() {
            document.getElementById("main-menu").classList.remove("hidden");
            document.getElementById("location-content").classList.add("hidden");
            document.getElementById("message-box").textContent = "";
        }
    </script>
</body>
</html>
