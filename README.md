<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Vehicle Import Cost Calculator - Sri Lanka</title>
    <style>
        body {
            font-family: Arial, sans-serif;
            margin: 0;
            padding: 20px;
            background-color: #3D8D7A; /* Background color */
            display: flex;
            flex-wrap: wrap; /* Allow sections to wrap on smaller screens */
            justify-content: center; /* Center the content horizontally */
            gap: 20px; /* Space between sections */
        }

        /* Common styling for all sections */
        .section {
            background-color: #B3D8A8; /* Section color */
            padding: 20px;
            border-radius: 10px;
            box-shadow: 0 0 10px rgba(0, 0, 0, 0.1);
            width: 100%; /* Full width on mobile by default */
            max-width: 400px; /* Maximum width for consistency */
        }

        /* Styling for the result box */
        .result {
            margin-top: 20px;
            padding: 10px;
            border: 1px solid #ddd;
            background-color: #FBFFE4; /* Selection and select box color */
            border-radius: 5px;
        }

        /* Styling for labels, select, and input fields */
        label, select, input {
            display: block;
            margin-bottom: 10px;
            width: 100%;
            padding: 8px;
            background-color: #FBFFE4; /* Selection and select box color */
            border: 1px solid #ccc;
            border-radius: 5px;
            color: #27667B; /* Normal text color */
            font-size: 16px; /* Larger font size for better readability on mobile */
        }

        /* Styling for headings */
        h1, h2, h3 {
            color: #143D60; /* Title and headline color */
        }

        /* Styling for contact info and social links */
        .contact-info p {
            font-size: 18px;
            margin: 5px 0;
            color: #27667B; /* Normal text color */
        }

        .social-links a {
            text-decoration: none;
            color: #143D60; /* Title and headline color */
            margin-right: 15px;
            font-size: 18px;
        }

        /* Styling for WhatsApp link */
        .whatsapp-link {
            display: inline-block;
            background-color: #25D366; /* WhatsApp green color */
            color: white;
            padding: 10px 15px;
            border-radius: 5px;
            text-decoration: none;
            margin-top: 10px;
            font-size: 16px; /* Larger font size for better readability on mobile */
        }

        .whatsapp-link:hover {
            background-color: #128C7E; /* Darker green for hover */
        }

        /* Responsive Design for Laptop/Desktop */
        @media (min-width: 768px) {
            .section {
                width: 30%; /* Three sections side-by-side on larger screens */
            }
        }

        /* Responsive Design for Mobile */
        @media (max-width: 767px) {
            body {
                flex-direction: column; /* Stack sections vertically on mobile */
                align-items: center; /* Center sections on mobile */
                padding: 10px; /* Reduce padding for better use of space */
            }
            .section {
                width: 100%; /* Full width on mobile */
                max-width: 100%; /* Allow sections to take full width */
                padding: 15px; /* Adjust padding for better spacing */
            }
            label, select, input {
                font-size: 14px; /* Slightly smaller font size for mobile */
            }
            .whatsapp-link {
                font-size: 14px; /* Slightly smaller font size for mobile */
            }
        }
    </style>
</head>
<body>
    <!-- Vehicle Import Cost Calculator Section -->
    <div class="section">
        <h1>Vehicle Import Cost Calculator - Sri Lanka</h1>
        
        <label for="vehicleType">Select Vehicle Category:</label>
        <select id="vehicleType" onchange="updateModels()">
            <option value="cars">Cars (87.03)</option>
            <option value="vans">Vans/Dual Purpose Vehicles (87.04)</option>
            <option value="lorries">Lorries/Trucks (87.04)</option>
            <option value="special">Special Purpose Vehicles (87.05)</option>
            <option value="bikes">Motor Bikes (87.11)</option>
            <option value="threewheelers">Three-Wheelers (87.11)</option>
        </select>
        
        <label for="vehicleModel">Select Vehicle Model:</label>
        <select id="vehicleModel" onchange="calculateCost()"></select>
        
        <label for="cifValue">Enter CIF Value (LKR):</label>
        <input type="number" id="cifValue" placeholder="CIF Value" oninput="calculateCost()">
        
        <label for="engineCapacity">Enter Engine Capacity (CC):</label>
        <input type="number" id="engineCapacity" placeholder="Engine Capacity (CC)" oninput="calculateCost()">
        
        <label for="hybrid">Hybrid or Non-Hybrid:</label>
        <select id="hybrid" onchange="calculateCost()">
            <option value="nonHybrid">Non-Hybrid</option>
            <option value="hybrid">Hybrid</option>
        </select>
        
        <label for="electric">Electric or Non-Electric:</label>
        <select id="electric" onchange="calculateCost()">
            <option value="nonElectric">Non-Electric</option>
            <option value="electric">Electric</option>
        </select>
        
        <div id="result" class="result"></div>
    </div>

    <!-- Sri Lanka Vehicle Import Tax Calculation Overview Section -->
    <div class="section">
        <h2>Sri Lanka Vehicle Import Tax Calculation Overview 🚗💼</h2>
        <p>When importing a vehicle to Sri Lanka, the following taxes and duties are applied based on the <strong>CIF (Cost, Insurance, Freight)</strong> value. Here's a breakdown of how the total import cost is calculated:</p>
        
        <h3>Taxes & Duties Breakdown:</h3>
        <p><strong>1. Customs Import Duty (CID):</strong></p>
        <ul>
            <li><strong>30%</strong> of the CIF value</li>
        </ul>
        
        <p><strong>2. Port and Airport Development Levy (PAL):</strong></p>
        <ul>
            <li><strong>10%</strong> of the CIF value</li>
        </ul>
        
        <p><strong>3. Excise Duty:</strong></p>
        <ul>
            <li>Depends on factors such as HS Code, fuel consumption, vehicle type, and engine capacity.</li>
            <li>Typically <strong>150% to 200%</strong> for small commercial vehicles (under 1,500cc).</li>
        </ul>
        
        <p><strong>4. Luxury Tax:</strong></p>
        <ul>
            <li>Applicable if the <strong>CIF value exceeds LKR 5 million</strong>.</li>
            <li>Based on factors such as fuel consumption, vehicle type, and price.</li>
        </ul>
        
        <p><strong>5. Value Added Tax (VAT):</strong></p>
        <ul>
            <li><strong>18%</strong> on the total of <strong>CIF + CID + PAL</strong></li>
        </ul>
        
        <h3>Total Import Cost Calculation Formula:</h3>
        <p>
            \[
            \text{Total Import Cost} = \text{CIF Value} + \text{CID} + \text{PAL} + \text{Excise Duty} + \text{Luxury Tax} + \text{VAT}
            \]
        </p>
        <p>Where:</p>
        <ul>
            <li><strong>CIF Value</strong> = Vehicle cost including shipping and insurance</li>
            <li><strong>CID</strong> = 30% of CIF</li>
            <li><strong>PAL</strong> = 10% of CIF</li>
            <li><strong>Excise Duty</strong> = Typically 150%-200% of CIF</li>
            <li><strong>Luxury Tax</strong> = If CIF > LKR 5 million</li>
            <li><strong>VAT</strong> = 18% on CIF + CID + PAL</li>
        </ul>
        
        <h3>Important Notes:</h3>
        <ul>
            <li><strong>Excise Duty</strong> and <strong>Luxury Tax</strong> vary based on the vehicle’s specific details, including engine capacity, fuel consumption, and price.</li>
            <li><strong>Luxury Tax</strong> only applies to high-value vehicles (CIF > LKR 5 million).</li>
        </ul>
    </div>

    <!-- About Me Section -->
    <div class="section">
        <h2>About Me</h2>
        <p>This website is powered by Suresh Jayasekara, an experienced professional with expertise in IT, surveillance, and tourism services. Feel free to check out my <a href="https://www.linkedin.com/in/suresh-srimal-jayasekara-489021252/" target="_blank">LinkedIn Profile</a> to learn more about my professional background.</p>

        <h2>Contact Information</h2>
        <div class="contact-info">
            <p><strong>Email:</strong> <a href="mailto:suresh2srimal@gmail.com">suresh2srimal@gmail.com</a></p>
            <p><strong>Phone:</strong> +94 76 9030615</p>
        </div>

        <h2>Get in Touch</h2>
        <p>If you have any questions, feel free to reach out to me on WhatsApp:</p>
        <a href="https://wa.me/94769030615" class="whatsapp-link" target="_blank">
            Chat on WhatsApp
        </a>

        <h2>Connect With Me</h2>
        <div class="social-links">
            <a href="https://www.linkedin.com/in/suresh-srimal-jayasekara-489021252/" target="_blank">LinkedIn</a>
            <!-- Add any other social media links you want here -->
        </div>
    </div>

    <script>
        const vehicleModels = {
            cars: ["Toyota Aqua", "Toyota Axio", "Toyota Prius", "Toyota Vitz", "Honda Vezel", "Honda Fit", "Nissan Leaf", "Nissan X-Trail", "Suzuki Wagon R", "Suzuki Swift", "Mitsubishi Outlander", "Mitsubishi Lancer", "Maruti Suzuki Alto"],
            vans: ["Toyota HiAce", "Nissan Caravan"],
            lorries: ["Mitsubishi Canter", "Isuzu Elf", "Toyota Dyna", "Tata Motors Trucks", "Mahindra Bolero City Pick-Up"],
            special: ["Crane Lorry", "Fire Fighting Vehicle", "Concrete Mixer Lorry"],
            bikes: ["Honda Dio", "Yamaha FZ", "Bajaj Pulsar", "TVS Apache", "Hero Splendor"],
            threewheelers: ["Bajaj RE", "TVS King", "Piaggio Ape"]
        };

        function updateModels() {
            const vehicleType = document.getElementById("vehicleType").value;
            const modelSelect = document.getElementById("vehicleModel");
            modelSelect.innerHTML = ""; // Clear existing options
            
            // Populate the dropdown with vehicle models
            vehicleModels[vehicleType].forEach(model => {
                let option = document.createElement("option");
                option.value = model;
                option.textContent = model;
                modelSelect.appendChild(option);
            });

            // Trigger cost calculation after updating models
            calculateCost();
        }

        function calculateCost() {
            const cifValue = parseFloat(document.getElementById("cifValue").value) || 0;
            const engineCapacity = parseFloat(document.getElementById("engineCapacity").value) || 0;
            const hybrid = document.getElementById("hybrid").value;
            const electric = document.getElementById("electric").value;

            let customsDutyRate = 0.30;
            let exciseDutyRate = 2.0; // Default excise duty rate
            let luxuryTaxThreshold = 5000000;

            // Adjust excise duty based on engine capacity
            if (engineCapacity <= 1000) {
                exciseDutyRate = 0.75;
            } else if (engineCapacity <= 1500) {
                exciseDutyRate = 1.0;
            } else if (engineCapacity <= 1800) {
                exciseDutyRate = 1.25;
            } else if (engineCapacity <= 2000) {
                exciseDutyRate = 1.5;
            } else if (engineCapacity <= 2500) {
                exciseDutyRate = 1.75;
            } else {
                exciseDutyRate = 2.0;
            }

            // Adjust excise duty for hybrid and electric vehicles
            if (hybrid === "hybrid") {
                exciseDutyRate *= 0.5; // 50% reduction for hybrid vehicles
            }
            if (electric === "electric") {
                exciseDutyRate *= 0.25; // 75% reduction for electric vehicles
            }

            let exciseDuty = cifValue * exciseDutyRate;
            let customsImportDuty = cifValue * customsDutyRate * 1.5;
            let portAirportLevy = cifValue * 0.10;
            let luxuryTax = cifValue > luxuryTaxThreshold ? (cifValue - luxuryTaxThreshold) * 0.15 : 0;
            let vat = (cifValue + customsImportDuty + portAirportLevy + exciseDuty + luxuryTax) * 0.18;
            let totalCost = cifValue + customsImportDuty + portAirportLevy + exciseDuty + luxuryTax + vat;

            document.getElementById("result").innerHTML = `
                <h3>Cost Breakdown:</h3>
                <p><strong>Base CIF Value:</strong> LKR ${cifValue.toLocaleString()}</p>
                <p><strong>Customs Import Duty:</strong> LKR ${customsImportDuty.toLocaleString()}</p>
                <p><strong>Port & Airport Levy:</strong> LKR ${portAirportLevy.toLocaleString()}</p>
                <p><strong>Excise Duty:</strong> LKR ${exciseDuty.toLocaleString()}</p>
                <p><strong>Luxury Tax:</strong> LKR ${luxuryTax.toLocaleString()}</p>
                <p><strong>VAT (18%):</strong> LKR ${vat.toLocaleString()}</p>
                <h3><strong>Total Import Cost:</strong> LKR ${totalCost.toLocaleString()}</h3>
            `;
        }

        // Initialize the models dropdown when the page loads
        updateModels();
    </script>
</body>
</html>
