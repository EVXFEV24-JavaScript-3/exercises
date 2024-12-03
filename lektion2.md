# Övningar - Lektion 2

## 1.

Skapa en ny komponent med namnet `heading`:

```
ng generate component heading
```

Lägg in följande i template filen:

```html
<h1 *ngIf="size === 'large'">{{ text }}</h1>
<h3 *ngIf="size === 'medium'">{{ text }}</h3>
<h6 *ngIf="size === 'small'">{{ text }}</h6>
```

Modifiera komponenten så att den går att återanvändas, genom att lägga till två egenskaper `text` och `size` som tas in genom `@Input` (props ekvivalent i React.) Lägg sedan in tre olika headings på sidan (en för varje storlek.)

## 2.

Skapa en ny komponent med namnet `user-card`. Lägg in följande i template filen:

```html
<div class="card">
    <h2>{{ name }}</h2>
    <p>Ålder: {{ age }}</p>
    <p *ngIf="isOnline">Online</p>
    <p *ngIf="!isOnline">Offline</p>
</div>
```

Modifiera komponenten så att den tar emot properties för `name`, `age` och `isOnline` genom `@Input`. Skapa sedan tre olika user-cards på sidan med olika värden för varje property.

## 3.

_Detta är en fortsättning på övning 6 från lektion 1_

Du får följande TypeScript kod för en komponent:

```typescript
import { Component } from "@angular/core";

class Country {
  name: string;
  continent: string;
  population: number;

  constructor(name: string, continent: string, population: number) {
    this.name = name;
    this.continent = continent;
    this.population = population;
  }
}

@Component({
  selector: "app-country-table",
  templateUrl: "./country-table.component.html",
  styleUrls: ["./country-table.component.css"],
})
export class CountryTableComponent {
  countries: Country[] = [
    new Country("France", "Europe", 64766868),
    new Country("Sweden", "Europe", 10617537),
    new Country("Japan", "Asia", 123235518),
    new Country("China", "Asia", 1425627628),
    new Country("Spain", "Europe", 47515521),
    new Country("Brazil", "South America", 216529995),
    new Country("Canada", "North America", 38810093),
  ];
}
```

Generera en egen komponent som heter `country-table` och lägg in koden ovanför i `.ts` filen. Ändra sedan i HTML filen för komponenten så att en tabell med följande struktur visas:

```html
<table>
  <tr>
    <th>Country</th>
    <th>Continent</th>
    <th>Population</th>
  </tr>
  <tr>
    <td>France</td>
    <td>Europe</td>
    <td>64766868</td>
  </tr>
</table>
```

Alla länder som komponenten innehåller (`countries` egenskapen) ska visas i tabellen. Den första tabell-raden som visas i HTML koden ovanför är till för att visa ett hårdkodat exempel och den skall du ta bort.

**Nu till det som är nytt för denna övning**: (i jämförelse med övning 6 från lektion 1)
Istället för att lägga in alla rader direkt i `CountryTableComponent` (som var lösningen för lektion 1) så ska du ha en egen komponent för alla rader. Du kan exempelvis skapa en komponent som heter `CountryTableRowComponent` som du återanvänder för varje rad/land.

## 4.

Skapa en `counter` komponent som implementerar det klassiska counter exemplet. Komponenten skall bestå av en knapp och en textruta med ett nummer. Vid knapptryck skall numret ökas med ett, och detta skall även visas på webbsidan.

## 5.

Skapa ett counter exempel igen (som förra övningen), men lägg in numret i App komponenten denna gång:

```typescript
import { Component } from "@angular/core";

@Component({
  selector: "app-root",
  templateUrl: "./app.component.html",
  styleUrls: ["./app.component.css"],
})
export class AppComponent {
  counter: number = 1;
}
```

Skapa sedan en ny komponent som innehåller knappen, och länka den i `AppComponent`.

```html
<!-- app.component.html -->
<span>{{ counter }}</span>
<app-counter-button></app-counter-button>
```

Gör så att numret ökas, med hjälp av @Output, vid knapptryck, i din nya komponent.

## 6.

Använd [DummyJson quotes](https://dummyjson.com/docs/quotes) för att hämta citat. Ladda in dem i en komponent genom att använda lifecycles. Rendera sedan ut dem på valfritt sätt.

## 7.

Kopiera lösningen från övning 4 (counter). Printa ut valfri text varje gång numret ökas, men utan att modifiera `(click)` funktionen. Hint: `OnChanges` lifecycle.

## 8.

Skapa en ny komponent med namnet `toggle-button`. Lägg in följande i template filen:

```html
<button 
    [class.active]="isActive" 
    (click)="toggleActive()">
    {{ buttonText }}
</button>
```

Lägg till en property `buttonText` som tas in genom `@Input`, en property `isActive` som är en boolean, och en metod `toggleActive()` som växlar värdet på `isActive`. Skapa sedan två knappar på sidan med olika texter.

## 9.

Skapa en ny komponent med namnet `task-item`. Lägg in följande i template filen:

```html
<div class="task" [class.completed]="isDone">
    <span>{{ taskName }}</span>
    <button *ngIf="!isDone" (click)="markAsDone()">Klar</button>
    <button *ngIf="isDone" (click)="markAsUndone()">Ångra</button>
</div>
```

Gör följande:

1. Lägg till `taskName` som en `@Input` property
2. Skapa en boolean property `isDone` som är `false` från början
3. Implementera metoderna `markAsDone()` och `markAsUndone()`
4. Skapa tre olika task-items på sidan med olika uppgifter
