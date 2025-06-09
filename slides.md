---
theme: unicorn
title: Fortschritte - Der Ballkönig
info: Eine Präsentation über die Fortschritte des Ballkönigs
drawings:
  persist: false
transition: slide-left
---

# Präsentation startet sogleich....

---

<div class="flex justify-evenly items-center h-full">
  <img src="./assets/story/couch.svg" alt="couch" class="w-50 bg-purple-300/75 rounded-lg aspect-square" />
  <Arrow class="text-purple-700" x1="425" y1="275" x2="550" y2="275" />
  <img src="./assets/story/cry.png" alt="cry" class="w-50 bg-purple-300/75 rounded-lg" />
  <span class="text-purple-700 position-absolute bottom-20 font-bold text-2xl bg-purple-300/20 p-2 rounded-lg">
    <span class="text-3xl">Ballarbeiter</span> = <span class="text-3xl">Unglücklich</span>
  </span>
  <span class="text-purple-700 position-absolute top-20 font-bold text-2xl bg-purple-300/20 p-2 rounded-lg">
    <span class="text-3xl">Benutzer</span> = <span class="text-3xl">Unglücklich</span>
  </span>
</div>

---
layout: intro
introImage: './assets/logo.png'
---

# Die Lösung: <span class="font-bold">Der Ballkönig</span>

Nur das Beste vom Besten

---
layout: table-contents
gradientColors: ['#8EC5FC', '#E0C3FC']
---

# Die Vision 

<br>

⏳ - Für immer

👥 - Einfach Konfigurierbar

🎯 - Keine nervigen Karten

---
layout: image-center
image: './assets/tool/plan.png'
imageWidth: '750'
imageHeight: '750'
---

### 🛠️ Technologien

---
layout: center
---

# Das Team
<div class="flex gap-4 justify-evenly w-full">
  <FoundingFathers />
  <div class="flex flex-row justify-evenly items-center gap-4 position-relative p-5 pt-25">
    <PersonFrame img="./assets/people/minihuber.png" name="Konstantin Minihuber" role="Fullstack" />
    <PersonFrame img="./assets/people/bernhofer.png" name="Moritz Bernhofer" role="Hardware + Backend" />
  </div>
</div>

---
layout: center
---

# Live Demo

<LiveDemoRedirect />

---
layout: image-center
image: './assets/tool/tool.png'
imageWidth: '450'
imageHeight: '950'
---

# Das Gerät

---
layout: center
---

# Roadmap

<Roadmap :data="[
  {
    time: '2024-10-01',
    title: 'Projektstart',
    description: 'Projektstart',
    color: 'bg-purple-500'
  },
  {
    time: '2025-02-01',
    title: 'Verkaufsstart 24',
    description: 'Erster öffentlicher Einsatz',
    color: 'bg-purple-500'
  },
  {
    time: '2025-09-07',
    title: 'Zweite Version',
    description: 'Neues Team konfiguriert',
    color: 'bg-purple-500'
  },
  {
    time: '2025-12-24',
    title: 'Verkaufsstart 25',
    description: 'Mit Kartenzahlung',
    color: 'bg-purple-500'
  },
  {
    time: '2026-03-04',
    title: 'Maturaball 26',
    description: 'Eintritt mit Kartenscan',
    color: 'bg-purple-500'
  }
]" />

---
layout: table-contents
gradientColors: ['#8EC5FC', '#E0C3FC']
---

# Errungenschaften

- 🎉 - Erfolgreicher Einsatz 2025
- 👥 - Verwendung für nächstes Jahr sichergestellt

---
layout: table-contents
gradientColors: ['#8EC5FC', '#E0C3FC']
---

# Zukunftsaussichten

<br>

- 💰 - Online Checkout
- 📱 - Scanner Gerät
- 🎫 - Kartendesigner

---
layout: end
---

# Dankeschön!
Ihr Ballkönig Team
<div class="flex flex-row justify-center items-center gap-4">
  <img src="./assets/logo.png" alt="Logo" class="w-20 rounded-full" />
</div>
