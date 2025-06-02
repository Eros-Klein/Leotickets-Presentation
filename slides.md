---
theme: seriph
background: https://cover.sli.dev
title: Welcome to Slidev
info: |
  ## Slidev Starter Template
  Presentation slides for developers.
  Learn more at [Sli.dev](https://sli.dev)
drawings:
  persist: false
transition: slide-left
mdc: true
---

# Die Lösung: Leotickets

Hallo ich bin du

<!--
Meine Notes
-->

---
transition: slide-left
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
transition: slide-left
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