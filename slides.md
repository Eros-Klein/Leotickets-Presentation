---
theme: unicorn
title: Fortschritte - Der Ballkönig
info: Eine Präsentation über die Fortschritte des Ballkönigs
drawings:
  persist: false
transition: slide-left
---

# Erste Seite

---
layout: intro
introImage: './assets/logo.png'
---

# Die Lösung: <span class="font-bold">Der Ballkönig</span>

Nur das Beste vom Besten

---

# Die Vision

- Für immer
- Für alle
- Für alles

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
