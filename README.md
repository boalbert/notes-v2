# Notes (Vue.js, Spring, Docker)

Enkel applikation för att spara anteckningar. Anteckningar man vill ge extra fokus kan 'pinnas'.

## Allmänt

Varje anteckning hämtas via API från databasen. Array sorteras på `boolean: pinned`.

## Frontend

- Skapad i Vue.js
- Layout bygger på en CSS grid, flexibel höjd på anteckningar hjälper `Vue-masonry-css` till med.

## Backend

- API är skriven i Java (mha. Spring)
- Data sparas i en MariaDB datasbas
- Körs i docker

## Demo
