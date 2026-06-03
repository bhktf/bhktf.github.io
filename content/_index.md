---
title: "BHKTF"
layout: "single"
---

<link rel="preconnect" href="https://fonts.googleapis.com">
<link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
<link href="https://fonts.googleapis.com/css2?family=Outfit:wght@300;400;600;700&family=Space+Grotesk:wght@400;700&display=swap" rel="stylesheet">
<link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.5.1/css/all.min.css">

<style>
    /* Resetting default theme restrictions to create the fixed app view */
    .main, .page-content, .post-content {
        max-width: 100% !important;
        padding: 0 !important;
        margin: 0 !important;
    }
    
    .portal-body {
        background-color: #000000 !important;
        background-image: radial-gradient(circle at center, rgba(138, 43, 226, 0.18) 0%, #060606 70%) !important;
        font-family: 'Outfit', sans-serif;
        color: #f8fafc;
        min-height: 85vh;
        display: flex;
        flex-direction: column;
        border: 1px solid rgba(255, 255, 255, 0.1);
        border-radius: 20px;
        overflow: hidden;
        margin-top: 1rem;
    }

    /* Fixed Liquid Glass Navbar */
    .nav-bar {
        display: flex;
        justify-content: space-between;
        align-items: center;
        padding: 1.5rem 3rem;
        background: rgba(10, 10, 10, 0.6);
        backdrop-filter: blur(20px);
        border-bottom: 1px solid rgba(255, 255, 255, 0.1);
    }

    .nav-logo {
        font-family: 'Space Grotesk', sans-serif;
        font-size: 2rem;
        font-weight: 700;
        letter-spacing: 3px;
        color: #a855f7;
    }

    .nav-menu {
        display: flex;
        gap: 2rem;
        list-style: none;
        margin: 0;
        padding: 0;
    }

    .nav-menu li {
        font-size: 0.9rem;
        text-transform: uppercase;
        letter-spacing: 1.5px;
        color: #94a3b8;
        cursor: pointer;
        transition: 0.3s ease;
    }

    .nav-menu li.active, .nav-menu li:hover {
        color: #f8fafc;
        text-shadow: 0 0 15px rgba(168, 85, 247, 0.6);
    }

    /* App Views Window */
    .app-viewport {
        flex-grow: 1;
        padding: 3rem;
        position: relative;
    }

    .app-view {
        display: none;
        animation: fadeIn 0.4s ease forwards;
    }

    .app-view.active {
        display: block;
    }

    @keyframes fadeIn {
        from { opacity: 0; transform: translateY(10px); }
        to { opacity: 1; transform: translateY(0); }
    }

    /* Core Components */
    .glass-card {
        background: rgba(255, 255, 255, 0.03);
        backdrop-filter: blur(25px);
        border: 1px solid rgba(255, 255, 255, 0.08);
        border-radius: 16px;
        padding: 2rem;
        margin-bottom: 2rem;
    }

    /* Countdown Grid styling */
    .countdown-timer {
        display: flex;
        gap: 1.5rem;
        justify-content: center;
        margin: 3rem 0;
    }

    .timer-box {
        display: flex;
        flex-direction: column;
        align-items: center;
        background: rgba(168, 85, 247, 0.05);
        border: 1px solid rgba(168, 85, 247, 0.2);
        border-radius: 12px;
        padding: 1.5rem;
        min-width: 110px;
    }

    .timer-box .val {
        font-size: 3rem;
        font-weight: 700;
        font-family: 'Space Grotesk', sans-serif;
        color: #f8fafc;
    }

    .timer-box .lbl {
        font-size: 0.75rem;
        text-transform: uppercase;
        color: #a855f7;
        letter-spacing: 2px;
    }

    /* Redesigned Horizontal Itinerary Timeline */
    .timeline-container {
        display: flex;
        gap: 1.5rem;
        overflow-x: auto;
        padding: 1rem 0;
    }

    .timeline-card {
        flex: 0 0 300px;
        background: rgba(255, 255, 255, 0.02);
        border: 1px solid rgba(255, 255, 255, 0.05);
        border-radius: 12px;
        padding: 1.5rem;
    }

    .timeline-card h4 {
        color: #a855f7;
        margin-top: 0;
        margin-bottom: 1rem;
        border-bottom: 1px solid rgba(255, 255, 255, 0.1);
        padding-bottom: 0.5rem;
    }

    .event-line {
        margin-bottom: 1rem;
        font-size: 0.95rem;
    }

    .event-time {
        font-weight: 700;
        color: #e2e8f0;
    }

    /* Checklist & Lock Mechanics */
    .checklist-wrapper {
        position: relative;
    }

    .lock-blur {
        filter: blur(12px);
        pointer-events: none;
        user-select: none;
    }

    .lock-overlay {
        position: absolute;
        top: 0; left: 0; width: 100%; height: 100%;
        background: rgba(6, 6, 6, 0.75);
        backdrop-filter: blur(4px);
        display: flex;
        flex-direction: column;
        align-items: center;
        justify-content: center;
        z-index: 10;
        border-radius: 16px;
    }

    /* Posts Engine Layout */
    .posts-layout {
        display: grid;
        grid-template-columns: 1fr 1.5fr;
        gap: 2rem;
    }

    .composer-select {
        width: 100%;
        background: #111;
        border: 1px solid rgba(255,255,255,0.1);
        padding: 0.75rem;
        border-radius: 8px;
        color: #fff;
        margin-bottom: 1rem;
    }

    .composer-textarea {
        width: 100%;
        height: 120px;
        background: #111;
        border: 1px solid rgba(255,255,255,0.1);
        padding: 0.75rem;
        border-radius: 8px;
        color: #fff;
        resize: none;
        margin-bottom: 1rem;
    }

    .btn-action {
        background: #a855f7;
        color: #000;
        border: none;
        padding: 0.75rem 2rem;
        font-weight: 700;
        border-radius: 8px;
        cursor: pointer;
        text-transform: uppercase;
        letter-spacing: 1px;
        transition: 0.2s;
    }

    .btn-action:hover {
        background: #b975ff;
        box-shadow: 0 0 15px #a855f7;
    }

    .wall-feed {
        max-height: 400px;
        overflow-y: auto;
        display: flex;
        flex-direction: column;
        gap: 1rem;
    }

    .msg-bubble {
        background: rgba(255,255,255,0.02);
        border: 1px solid rgba(255,255,255,0.05);
        border-radius: 10px;
        padding: 1rem;
    }

    .msg-author {
        color: #a855f7;
        font-weight: 700;
        font-size: 0.9rem;
    }

    .fineprint {
        color: #475569;
        font-size: 0.75rem;
        margin-top: 0.5rem;
    }
</style>

<div class="portal-body">
    <nav class="nav-bar">
        <div class="nav-logo">BHKTF</div>
        <ul class="nav-menu">
            <li class="nav-tab active" onclick="switchView('home-view', this)">Home</li>
            <li class="nav-tab" onclick="switchView('itinerary-view', this)">Itinerary</li>
            <li class="nav-tab" onclick="switchView('checklist-view', this)">Checklist</li>
            <li class="nav-tab" onclick="switchView('posts-view', this)">Posts</li>
        </ul>
    </nav>

    <div class="app-viewport">

        <div id="home-view" class="app-view active">
            <div style="text-align: center; margin-top: 1.5rem;">
                <h1 style="font-size: 4rem; font-family: 'Space Grotesk'; letter-spacing: -3px; margin: 0;">BHKTF</h1>
                <p style="color: #94a3b8; font-size: 1.2rem; letter-spacing: 2px; text-transform: uppercase; margin: 0.5rem 0 0 0;">Rhine & Moselle Trip Portal</p>
                
                <div class="countdown-timer">
                    <div class="timer-box"><div class="val" id="time-w">00</div><div class="lbl">Weeks</div></div>
                    <div class="timer-box"><div class="val" id="time-d">00</div><div class="lbl">Days</div></div>
                    <div class="timer-box"><div class="val" id="time-h">00</div><div class="lbl">Hours</div></div>
                    <div class="timer-box"><div class="val" id="time-m">00</div><div class="lbl">Mins</div></div>
                    <div class="timer-box"><div class="val" id="time-s">00</div><div class="lbl">Secs</div></div>
                </div>

                <div style="display: flex; gap: 1rem; justify-content: center; margin-top: 2rem;">
                    <button class="btn-action" style="background: rgba(255,255,255,0.05); color: #fff; border: 1px solid rgba(255,255,255,0.1);" onclick="document.querySelectorAll('.nav-tab')[1].click()">Itinerary</button>
                    <button class="btn-action" style="background: rgba(255,255,255,0.05); color: #fff; border: 1px solid rgba(255,255,255,0.1);" onclick="document.querySelectorAll('.nav-tab')[2].click()">Checklist</button>
                    <button class="btn-action" style="background: rgba(255,255,255,0.05); color: #fff; border: 1px solid rgba(255,255,255,0.1);" onclick="document.querySelectorAll('.nav-tab')[3].click()">Posts</button>
                </div>
            </div>
        </div>

        <div id="itinerary-view" class="app-view">
            <h2 style="font-family: 'Space Grotesk'; margin-bottom: 1.5rem;">Master Itinerary</h2>
            <div class="timeline-container">
                <div class="timeline-card">
                    <h4>Day 1 — Sun 5th July</h4>
                    <div class="event-line"><span class="event-time">15:00</span> Meet at school</div>
                    <div class="event-line"><span class="event-time">15:30</span> Depart coach to Dover</div>
                    <div class="event-line"><span class="event-time">22:20</span> Ferry Check-in</div>
                </div>
                <div class="timeline-card">
                    <h4>Day 2 — Mon 6th July</h4>
                    <div class="event-line"><span class="event-time">02:50</span> Arrive Calais (FR Time)</div>
                    <div class="event-line"><span class="event-time">09:00</span> Cologne Cathedral visit</div>
                    <div class="event-line"><span class="event-time">15:00</span> Chocolate Museum 🍫</div>
                    <div class="event-line"><span class="event-time">18:00</span> Hostel Check-in</div>
                </div>
                <div class="timeline-card">
                    <h4>Day 3 — Tue 7th July</h4>
                    <div class="event-line"><span class="event-time">10:00</span> Boppard Cable Car Lift</div>
                    <div class="event-line"><span class="event-time">12:45</span> Rhine River Cruise 🚢</div>
                    <div class="event-line"><span class="event-time">19:00</span> Group Bowling Night</div>
                </div>
                <div class="timeline-card">
                    <h4>Day 4 — Wed 8th July</h4>
                    <div class="event-line"><span class="event-time">08:30</span> Phantasialand Theme Park Rollercoasters! 🎢</div>
                    <div class="event-line"><span class="event-time">18:30</span> Evening Meal & Room Packing</div>
                </div>
                <div class="timeline-card">
                    <h4>Day 5 — Thu 9th July</h4>
                    <div class="event-line"><span class="event-time">07:45</span> Depart Germany</div>
                    <div class="event-line"><span class="event-time">15:55</span> Ferry leaves Calais</div>
                    <div class="event-line"><span class="event-time">23:00</span> Return Knaresborough</div>
                </div>
            </div>
            <div class="glass-card" style="margin-top: 1.5rem; display: flex; align-items: center; gap: 2rem;">
                <div style="flex: 1;">
                    <h3 style="margin-top:0;">Phantasialand Preview</h3>
                    <p style="margin:0; font-size:0.95rem;">Get ready to hit Taron—the world's fastest multi-launch coaster situated inside the Klugheim realm.</p>
                    <div class="fineprint">from reddit.com/r/rollercoasters</div>
                </div>
            </div>
        </div>

        <div id="checklist-view" class="app-view">
            <h2 style="font-family: 'Space Grotesk'; margin-bottom: 1.5rem;">Packing Checklist</h2>
            <div class="checklist-wrapper">
                
                <div id="checklist-lock-layer" class="lock-overlay">
                    <i class="fa-solid fa-lock" style="font-size: 3.5rem; color: #a855f7; margin-bottom: 1rem;"></i>
                    <h3 style="margin:0; color:#fff;">Section Locked</h3>
                    <p style="margin: 0.25rem 0 0 0; font-size: 0.95rem; color: #94a3b8;">Unlocks automatically exactly 7 days before departure.</p>
                </div>

                <div id="checklist-content-layer" class="lock-blur" style="display: grid; grid-template-columns: 1fr 1fr; gap: 2rem;">
                    <div class="glass-card" style="margin:0;">
                        <h3 style="margin-top:0;"><i class="fa-solid fa-suitcase"></i> Essential Packing</h3>
                        <label><input type="checkbox"> Refillable water bottle</label><br>
                        <label><input type="checkbox"> European plug adapter</label><br>
                        <label><input type="checkbox"> Comfortable walking shoes</label><br>
                        <label><input type="checkbox"> Passport & ID copies</label><br>
                        <label><input type="checkbox"> €60 cash recommended</label>
                    </div>
                    <div class="glass-card" style="margin:0;">
                        <h3 style="margin-top:0; color: #f43f5e;"><i class="fa-solid fa-ban"></i> Coach Bans</h3>
                        <p style="margin: 0 0 0.5rem 0; font-size: 0.9rem;">Strictly prohibited on board:</p>
                        <ul style="margin: 0; padding-left: 1.25rem; color: #fda4af;">
                            <li>Chewing gum</li>
                            <li>Glass bottles</li>
                            <li>Fizzy drinks</li>
                            <li>Strong smelling snacks</li>
                        </ul>
                    </div>
                </div>

            </div>
        </div>

        <div id="posts-view" class="app-view">
            <h2 style="font-family: 'Space Grotesk'; margin-bottom: 1.5rem;">Group Wall</h2>
            <div class="posts-layout">
                <div class="glass-card">
                    <h3 style="margin-top:0;">Write Post</h3>
                    <select id="post-author-select" class="composer-select">
                        <option value="Alex">Alex</option>
                        <option value="Stanley">Stanley</option>
                        <option value="Joseph">Joseph</option>
                        <option value="Archie">Archie</option>
                    </select>
                    <textarea id="post-text-input" class="composer-textarea" placeholder="Type an update to the crew..."></textarea>
                    <button class="btn-action" style="width: 100%;" onclick="addCustomPost()">Publish</button>
                </div>
                <div class="glass-card">
                    <h3 style="margin-top:0;">Live Feed</h3>
                    <div id="wall-feed-box" class="wall-feed">
                        <div class="msg-bubble">
                            <span class="msg-author">Alex</span>
                            <p style="margin: 0.25rem 0 0 0; font-size: 0.95rem;">Liquid glass layout is fully running. Let's get packing lists tested.</p>
                        </div>
                        <div class="msg-bubble">
                            <span class="msg-author">Stanley</span>
                            <p style="margin: 0.25rem 0 0 0; font-size: 0.95rem;">Has anyone sorted out mobile data roaming plans for Germany yet?</p>
                        </div>
                    </div>
                </div>
            </div>
        </div>

    </div>
</div>

<script>
    // Tab Controller
    function switchView(viewId, tabElement) {
        document.querySelectorAll('.app-view').forEach(view => view.classList.remove('active'));
        document.querySelectorAll('.nav-tab').forEach(tab => tab.classList.remove('active'));
        
        document.getElementById(viewId).classList.add('active');
        tabElement.classList.add('active');
    }

    // Departure Date Tracker: Sunday 5th July 2026 at 15:00:00
    const departureTime = new Date("July 5, 2026 15:00:00").getTime();

    function runtimeEngine() {
        const now = new Date().getTime();
        const gap = departureTime - now;

        // Breakdown mathematical variables
        const msSec = 1000;
        const msMin = msSec * 60;
        const msHr = msMin * 60;
        const msDay = msHr * 24;
        const msWk = msDay * 7;

        const weeks = Math.floor(gap / msWk);
        const days = Math.floor((gap % msWk) / msDay);
        const hours = Math.floor((gap % msDay) / msHr);
        const minutes = Math.floor((gap % msHr) / msMin);
        const seconds = Math.floor((gap % msMin) / msSec);

        // Update HTML interface safely
        if (gap < 0) {
            document.getElementById("time-w").innerText = "0";
            document.getElementById("time-d").innerText = "0";
            document.getElementById("time-h").innerText = "0";
            document.getElementById("time-m").innerText = "0";
            document.getElementById("time-s").innerText = "0";
        } else {
            document.getElementById("time-w").innerText = weeks.toString().padStart(2, '0');
            document.getElementById("time-d").innerText = days.toString().padStart(2, '0');
            document.getElementById("time-h").innerText = hours.toString().padStart(2, '0');
            document.getElementById("time-m").innerText = minutes.toString().padStart(2, '0');
            document.getElementById("time-s").innerText = seconds.toString().padStart(2, '0');
        }

        // Automatic Lock / Unlock Assessment (7 days threshold)
        const totalDaysRemaining = gap / msDay;
        if (totalDaysRemaining <= 7) {
            document.getElementById("checklist-lock-layer").style.display = "none";
            document.getElementById("checklist-content-layer").classList.remove("lock-blur");
        }
    }

    // Initialize logic loop immediately
    runtimeEngine();
    setInterval(runtimeEngine, 1000);

    // Dynamic Live Feed Simulation
    function addCustomPost() {
        const author = document.getElementById("post-author-select").value;
        const msg = document.getElementById("post-text-input").value.trim();
        
        if(msg === "") return;

        const newPost = document.createElement("div");
        newPost.className = "msg-bubble";
        newPost.innerHTML = `<span class="msg-author">${author}</span><p style="margin: 0.25rem 0 0 0; font-size: 0.95rem;">${msg}</p>`;
        
        const feed = document.getElementById("wall-feed-box");
        feed.insertBefore(newPost, feed.firstChild);
        
        // Reset editor field
        document.getElementById("post-text-input").value = "";
    }
</script>
