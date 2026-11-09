# al-resource-and-utility-directory
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Local Resource & Utility Directory</title>
    <style>
        :root {
            --primary: #2563eb;
            --primary-hover: #1d4ed8;
            --bg-color: #f8fafc;
            --card-bg: #ffffff;
            --text-main: #1e293b;
            --text-muted: #64748b;
            --border: #e2e8f0;
            --radius: 12px;
        }

        * {
            box-sizing: border-box;
            margin: 0;
            padding: 0;
            font-family: system-ui, -apple-system, BlinkMacSystemFont, 'Segoe UI', Roboto, Oxygen, Ubuntu, Cantarell, sans-serif;
        }

        body {
            background-color: var(--bg-color);
            color: var(--text-main);
            min-height: 100vh;
            display: flex;
            justify-content: center;
            align-items: center;
        }

        /* Authentication Container */
        #auth-container {
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            background: rgba(15, 23, 42, 0.6);
            backdrop-filter: blur(4px);
            display: flex;
            justify-content: center;
            align-items: center;
            z-index: 1000;
            padding: 1rem;
        }

        .auth-card {
            background: var(--card-bg);
            width: 100%;
            max-width: 400px;
            padding: 2.5rem 2rem;
            border-radius: var(--radius);
            box-shadow: 0 20px 25px -5px rgba(0, 0, 0, 0.1), 0 8px 10px -6px rgba(0, 0, 0, 0.1);
            text-align: center;
        }

        .auth-card h2 {
            margin-bottom: 0.5rem;
            font-size: 1.5rem;
            color: var(--text-main);
        }

        .auth-card p {
            color: var(--text-muted);
            font-size: 0.9rem;
            margin-bottom: 1.5rem;
        }

        .input-group {
            margin-bottom: 1.25rem;
            text-align: left;
        }

        .input-group label {
            display: block;
            font-size: 0.85rem;
            font-weight: 600;
            margin-bottom: 0.5rem;
            color: var(--text-main);
        }

        .input-group input {
            width: 100%;
            padding: 0.75rem 1rem;
            border: 1px solid var(--border);
            border-radius: 8px;
            font-size: 1rem;
            outline: none;
            transition: border-color 0.2s;
        }

        .input-group input:focus {
            border-color: var(--primary);
        }

        .btn {
            width: 100%;
            padding: 0.75rem;
            background-color: var(--primary);
            color: white;
            border: none;
            border-radius: 8px;
            font-size: 1rem;
            font-weight: 600;
            cursor: pointer;
            transition: background-color 0.2s;
        }

        .btn:hover {
            background-color: var(--primary-hover);
        }

        .hidden {
            display: none !important;
        }

        /* Main App Layout */
        #app-container {
            width: 100%;
            max-width: 800px;
            min-height: 100vh;
            background: var(--card-bg);
            display: flex;
            flex-direction: column;
            box-shadow: 0 0 15px rgba(0,0,0,0.05);
        }

        header {
            padding: 1.5rem;
            border-bottom: 1px solid var(--border);
            text-align: center;
            background: #ffffff;
            position: sticky;
            top: 0;
            z-index: 10;
        }

        header h1 {
            font-size: 1.25rem;
            color: var(--text-main);
            margin-bottom: 0.25rem;
        }

        header p {
            font-size: 0.85rem;
            color: var(--text-muted);
        }

        .content {
            padding: 1.5rem;
            flex: 1;
        }

        /* Search & Filters */
        .search-bar {
            width: 100%;
            padding: 0.75rem 1rem;
            border: 1px solid var(--border);
            border-radius: 8px;
            font-size: 0.95rem;
            margin-bottom: 1rem;
            outline: none;
        }

        .search-bar:focus {
            border-color: var(--primary);
        }

        .categories {
            display: flex;
            gap: 0.5rem;
            overflow-x: auto;
            padding-bottom: 0.5rem;
            margin-bottom: 1.5rem;
            scrollbar-width: none;
        }

        .categories::-webkit-scrollbar {
            display: none;
        }

        .category-btn {
            padding: 0.5rem 1rem;
            background: var(--bg-color);
            border: 1px solid var(--border);
            border-radius: 20px;
            font-size: 0.85rem;
            font-weight: 500;
            color: var(--text-muted);
            cursor: pointer;
            white-space: nowrap;
            transition: all 0.2s;
        }

        .category-btn.active, .category-btn:hover {
            background: var(--primary);
            color: white;
            border-color: var(--primary);
        }

        /* Directory Cards List */
        .directory-list {
            display: grid;
            gap: 1rem;
        }

        .directory-card {
            background: #ffffff;
            border: 1px solid var(--border);
            border-radius: var(--radius);
            padding: 1rem 1.25rem;
            display: flex;
            flex-direction: column;
            gap: 0.5rem;
            transition: transform 0.1s, box-shadow 0.1s;
        }

        .directory-card:hover {
            box-shadow: 0 4px 12px rgba(0,0,0,0.05);
        }

        .card-header {
            display: flex;
            justify-content: space-between;
            align-items: flex-start;
        }

        .card-title {
            font-size: 1rem;
            font-weight: 600;
            color: var(--text-main);
        }

        .card-badge {
            font-size: 0.7rem;
            padding: 0.2rem 0.5rem;
            border-radius: 4px;
            font-weight: 600;
            text-transform: uppercase;
        }

        .badge-emergency { background: #fee2e2; color: #991b1b; }
        .badge-education { background: #e0f2fe; color: #0369a1; }
        .badge-utilities { background: #fef3c7; color: #92400e; }

        .card-desc {
            font-size: 0.85rem;
            color: var(--text-muted);
        }

        .card-footer {
            display: flex;
            justify-content: space-between;
            align-items: center;
            margin-top: 0.25rem;
            font-size: 0.85rem;
        }

        .card-contact {
            font-weight: 600;
            color: var(--primary);
            text-decoration: none;
        }

        .no-results {
            text-align: center;
            color: var(--text-muted);
            padding: 2rem;
            font-size: 0.9rem;
        }

        /* Responsive styling for desktop */
        @media (min-width: 768px) {
            body {
                background-color: #e2e8f0;
                padding: 2rem 0;
            }
            #app-container {
                border-radius: var(--radius);
                min-height: 85vh;
            }
        }
    </style>
</head>
<body>

    <!-- Authentication Overlay -->
    <div id="auth-container">
        <!-- Step 1: Mobile Number Input -->
        <div id="step-phone" class="auth-card">
            <h2>Welcome</h2>
            <p>Enter your mobile number to access the local directory</p>
            <div class="input-group">
                <label for="phone-input">Mobile Number</label>
                <input type="tel" id="phone-input" placeholder="e.g., 9876543210" maxlength="10">
            </div>
            <button class="btn" id="send-otp-btn">Send OTP</button>
        </div>

        <!-- Step 2: OTP Verification -->
        <div id="step-otp" class="auth-card hidden">
            <h2>Verify OTP</h2>
            <p>Enter the 4-digit code sent to your mobile number <br><strong id="display-phone"></strong></p>
            <div class="input-group">
                <label for="otp-input">Verification Code (Hint: <span id="hint-otp" style="color:var(--primary)"></span>)</label>
                <input type="text" id="otp-input" placeholder="Enter 4-digit OTP" maxlength="4">
            </div>
            <button class="btn" id="verify-otp-btn">Verify & Login</button>
        </div>
    </div>

    <!-- Main Application Container -->
    <div id="app-container" class="hidden">
        <header>
            <h1>Neighborhood Directory</h1>
            <p>Essential local services & resources at your fingertips</p>
        </header>

        <div class="content">
            <!-- Search Input -->
            <input type="text" id="search-input" class="search-bar" placeholder="Search services, mechanics, medical stores...">

            <!-- Category Filter Buttons -->
            <div class="categories">
                <button class="category-btn active" data-category="All">All</button>
                <button class="category-btn" data-category="Emergency">Emergency</button>
                <button class="category-btn" data-category="Education">Education</button>
                <button class="category-btn" data-category="Utilities">Utilities</button>
            </div>

            <!-- Directory Cards Container -->
            <div id="directory-list" class="directory-list">
                <!-- Dynamically populated via JS -->
            </div>
        </div>
    </div>

    <script>
        // Mock Database of Local Services
        const servicesData = [
            { id: 1, name: "City General Hospital", category: "Emergency", desc: "24/7 Emergency care, trauma center, and pharmacy.", contact: "102 / 040-2345678" },
            { id: 2, name: "Community Police Station", category: "Emergency", desc: "Local neighborhood law enforcement and assistance.", contact: "100 / 040-2345111" },
            { id: 3, name: "Public Library & Study Hall", category: "Education", desc: "Quiet reading rooms, reference books, and free high-speed Wi-Fi.", contact: "040-9876543" },
            { id: 4, name: "Shree Medical & General Store", category: "Utilities", desc: "All prescription medicines, first-aid, and healthcare items.", contact: "9848012345" },
            { id: 5, name: "Apex Coaching & Tuition Center", category: "Education", desc: "Math, Science, and Coding classes for school students.", contact: "9123456789" },
            { id: 6, name: "Ramesh Two-Wheeler Mechanic", category: "Utilities", desc: "Quick puncture repairs, servicing, and emergency towing.", contact: "9988776655" },
            { id: 7, name: "Fire & Rescue Department", category: "Emergency", desc: "Emergency fire response and disaster management.", contact: "101" },
            { id: 8, name: "Municipal Water Supply Office", category: "Utilities", desc: "Report pipeline leaks, tanker bookings, and drainage complaints.", contact: "040-5555666" }
        ];

        // State variables for authentication & filters
        let generatedOtp = "";
        let currentCategory = "All";

        // DOM Elements
        const authContainer = document.getElementById('auth-container');
        const appContainer = document.getElementById('app-container');
        const stepPhone = document.getElementById('step-phone');
        const stepOtp = document.getElementById('step-otp');
        const phoneInput = document.getElementById('phone-input');
        const otpInput = document.getElementById('otp-input');
        const sendOtpBtn = document.getElementById('send-otp-btn');
        const verifyOtpBtn = document.getElementById('verify-otp-btn');
        const displayPhone = document.getElementById('display-phone');
        const hintOtp = document.getElementById('hint-otp');
        
        const searchInput = document.getElementById('search-input');
        const directoryList = document.getElementById('directory-list');
        const categoryButtons = document.querySelectorAll('.category-btn');

        // Step 1: Send OTP Action
        sendOtpBtn.addEventListener('click', () => {
            const phone = phoneInput.value.trim();
            if (phone.length < 10) {
                alert("Please enter a valid 10-digit mobile number.");
                return;
            }

            // Generate a random 4-digit OTP
            generatedOtp = Math.floor(1000 + Math.random() * 9000).toString();
            displayPhone.textContent = "+91 " + phone;
            hintOtp.textContent = generatedOtp; // Displayed as a hint for seamless testing

            stepPhone.classList.add('hidden');
            stepOtp.classList.remove('hidden');
        });

        // Step 2: Verify OTP Action
        verifyOtpBtn.addEventListener('click', () => {
            const enteredOtp = otpInput.value.trim();
            if (enteredOtp === generatedOtp) {
                authContainer.classList.add('hidden');
                appContainer.classList.remove('hidden');
                renderDirectory(servicesData);
            } else {
                alert("Incorrect OTP. Please check the hint code and try again.");
            }
        });

        // Render Directory List
        function renderDirectory(items) {
            directoryList.innerHTML = "";
            
            if (items.length === 0) {
                directoryList.innerHTML = `<div class="no-results">No local services found matching your search.</div>`;
                return;
            }

            items.forEach(item => {
                const badgeClass = `badge-${item.category.toLowerCase()}`;
                const card = document.createElement('div');
                card.className = 'directory-card';
                card.innerHTML = `
                    <div class="card-header">
                        <span class="card-title">${item.name}</span>
                        <span class="card-badge ${badgeClass}">${item.category}</span>
                    </div>
                    <div class="card-desc">${item.desc}</div>
                    <div class="card-footer">
                        <span>Contact: <a href="tel:${item.contact}" class="card-contact">${item.contact}</a></span>
                    </div>
                `;
                directoryList.appendChild(card);
            });
        }

        // Search Filtering Logic
        searchInput.addEventListener('input', (e) => {
            filterAndRender();
        });

        // Category Filtering Logic
        categoryButtons.forEach(button => {
            button.addEventListener('click', () => {
                categoryButtons.forEach(btn => btn.classList.remove('active'));
                button.classList.add('active');
                currentCategory = button.getAttribute('data-category');
                filterAndRender();
            });
        });

        // Combine Search & Category Filters
        function filterAndRender() {
            const query = searchInput.value.toLowerCase().trim();
            
            const filtered = servicesData.filter(item => {
                const matchesCategory = (currentCategory === "All" || item.category === currentCategory);
                const matchesSearch = item.name.toLowerCase().includes(query) || 
                                      item.desc.toLowerCase().includes(query) || 
                                      item.category.toLowerCase().includes(query);
                return matchesCategory && matchesSearch;
            });

            renderDirectory(filtered);
        }
    </script>
</body>
</html>
