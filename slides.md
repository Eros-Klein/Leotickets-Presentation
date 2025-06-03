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

👥 - Für alle

🎯 - Für alles

---

# Technologien

<div class="flex gap-4 w-full justify-evenly h-full items-center">
  <div class="flex flex-col items-center">
    <img class="w-20" src="./assets/react.svg" alt="React" />
    <p class="text-center">React</p>
  </div>
  <div class="flex flex-col items-center">
    <img class="w-20" src="./assets/angular.svg" alt="Angular" />
    <p class="text-center">Angular</p>
  </div>
  <div class="flex flex-col items-center">
    <img class="w-20" src="./assets/quarkus.svg" alt="Quarkus" />
    <p class="text-center">Quarkus</p>
  </div>
</div>

---

# Die Architektur

```sh
├── apps
│   ├── Client
│   │   ├── Dashboard (React-Admin-Dashboard)
│   │   │   └── ...
│   │   └── Web (Angular-Web-Frontend)
│   │       └── ...
│   └── Server (Quarkus)
│       ├── api
│       │   └── ...
│       ├── interface
│       │   └── ...
│       ├── logic
│       │   └── ...
│       └── service
│           └── ...
├── Docker (Docker-Configuration)
│   └── docker-compose.yml
├── package.json
├── packages
│   └── ...
├── README.md
└── turbo.json
```
