---
title: "Rhine & Moselle 2026"
layout: "single"
---

<div style="text-align: center; margin-bottom: 3rem;">
    <h1>Rhine & Moselle Expedition 2026 🇩🇪</h1>
    <p style="color: #aaa;">The ultimate trip portal for <strong>Alex, Archie, Joseph, and Stanley</strong></p>
    
    <div id="countdown-box" style="background: #1d1e20; border: 1px solid #333; padding: 1.5rem; border-radius: 8px; display: inline-block; margin-top: 1rem;">
        <h3 style="margin: 0 0 0.5rem 0; font-size: 0.9rem; text-transform: uppercase; letter-spacing: 1px; color: #888;">Time Until Departure</h3>
        <div id="timer" style="font-size: 2rem; font-weight: bold; font-family: monospace; color: #4ba3ff;">Calculating...</div>
    </div>
</div>

## 🕒 The Master Itinerary

### Day 1 — Sunday 5th July
* **15:00** 🏫 Meet at school
* **15:30** 🚌 Depart school and travel down to Dover *(stop en route)*
* **22:20** 🛳️ Check in at Irish Ferries terminal, Dover

### Day 2 — Monday 6th July
* **00:20** 🌊 Ferry crossing time
* **02:50** 🇫🇷 Arrive in Calais *(local time)* — travel to Cologne with breakfast stop in Aachen
* **09:00** 🏰 Arrive in Cologne & drop off luggage. Visit Cathedral / free time
* **15:00** 🍫 Visit the **Lindt Chocolate Museum**
* **18:00** 🏨 Check in at Jugendherberge Köln-Deutz
* **18:30** 🍽️ Evening meal at the hostel
* **20:00** 🌙 Walk along the river Rhine and visit the Old Town

### Day 3 — Tuesday 7th July
* **07:00** 🍳 Breakfast at the hostel
* **08:00** 🚌 Depart for Boppard
* **10:00** 🚠 Free time in Boppard with town trail & **Boppard cable car lift**
* **12:45** 🚢 **River cruise** from Boppard to St. Goar
* **14:40** 🚌 Arrive in St. Goarshausen. Meet coach, stop to visit the *Deutsches Eck*
* **16:30** 🏨 Arrive back at hostel
* **19:00** 🎳 Evening spent bowling

### Day 4 — Wednesday 8th July
* **07:30** 🍳 Breakfast at the hostel
* **08:30** 🎢 Depart hostel for **Phantasialand Theme Park**!
* **17:15** 🚌 Depart for the hostel
* **18:30** 🍽️ Evening meal at the hostel & packing

### Day 5 — Thursday 9th July
* **06:00** 🍳 Early breakfast
* **06:30** 🧳 Vacate rooms and load luggage
* **07:45** 🚌 Depart hostel
* **13:55** 🛳️ Check in at Irish Ferries terminal, Calais
* **15:55** 🌊 Ferry departs
* **16:25** 🇬🇧 Arrive in Dover *(UK time)*
* **23:00** 🏡 Estimated arrival back in Knaresborough

---

## 🔒 Locked Section (Unlocks 7 Days Before Trip)

<div id="locked-section" style="position: relative; filter: blur(5px); pointer-events: none; user-select: none; transition: filter 0.5s ease;">
    <h3>🧳 Trip Packing Hub</h3>
    <p>Get ready for the trip! Here is your essential checklist:</p>
    
    <input type="checkbox"> Refillable water bottle *(Essential)*<br>
    <input type="checkbox"> Travel bag for the coach *(Food, medication, blanket)*<br>
    <input type="checkbox"> Comfortable walking shoes *(No heels, good grip)*<br>
    <input type="checkbox"> 2 changes of clothes + inside hostel shoes<br>
    <input type="checkbox"> German 'survival guide' + small notebook<br>
    <input type="checkbox"> Euros (&euro;60 recommended for lunches/snacks)<br>
    <input type="checkbox"> English money (&pound;15 for motorway stops)<br>
    <input type="checkbox"> Fully charged phone + Charger/UK-to-EU Adapter<br>
    
    <h4 style="margin-top:1.5rem;">❌ Strictly Banned Items:</h4>
    <ul>
        <li>Chewing gum</li>
        <li>Glass bottles</li>
        <li>Fizzy drinks</li>
        <li>Strong smelling snacks</li>
    </ul>
</div>

<div id="lock-overlay" style="background: rgba(29, 30, 32, 0.95); border: 2px dashed #ff4b4b; padding: 2rem; text-align: center; border-radius: 8px; margin-top: -10rem; position: relative; z-index: 10;">
    <span style="font-size: 3rem;">🔒</span>
    <h3 style="color: #ff4b4b; margin: 0.5rem 0;">Packing Checklist Locked</h3>
    <p style="margin: 0; color: #bbb;">This area automatically unlocks exactly 7 days before departure.</p>
</div>

<script>
    // TARGET DEPARTURE DATE: July 5, 2026 at 15:00:00
    const targetDate = new Date("July 5, 2026 15:00:00").getTime();

    function updatePortal() {
        const now = new Date().getTime();
        const difference = targetDate - now;

        // Calculations for time
        const days = Math.floor(difference / (1000 * 60 * 60 * 24));
        const hours = Math.floor((difference % (1000 * 60 * 60 * 24)) / (1000 * 60 * 60));
        const minutes = Math.floor((difference % (1000 * 60 * 60)) / (1000 * 60));
        const seconds = Math.floor((difference % (1000 * 60)) / 1000);

        // Display the clock
        if (difference < 0) {
            document.getElementById("timer").innerHTML = "TRIP HAS STARTED! 🇩🇪";
        } else {
            document.getElementById("timer").innerHTML = days + "d " + hours + "h " + minutes + "m " + seconds + "s";
        }

        // UNLOCK LOGIC: Unlock if we are within 7 days of the trip (or if the trip has passed)
        if (days <= 7) {
            const lockedSec = document.getElementById("locked-section");
            const lockOverlay = document.getElementById("lock-overlay");
            
            if(lockedSec && lockOverlay) {
                lockedSec.style.filter = "none";
                lockedSec.style.pointerEvents = "auto";
                lockedSec.style.userSelect = "auto";
                lockOverlay.style.display = "none";
            }
        }
    }

    // Run clock immediately and refresh every second
    updatePortal();
    setInterval(updatePortal, 1000);
</script>