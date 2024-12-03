# Övningar - Lektion 1

Du behöver installera Angular CLI för att kunna göra följande övningar.

## Träna på TypeScript

Ta koden från ett valfritt React projekt (exempelvis från tidigare kurs) och gör om två filer till TypeScript. Om du känner att du behöver träna mer efter det så kan du omvandla fler filer.

## 1.

Skapa en ny Angular komponent med Angular CLI, genom följande kommando:

```
ng generate component <komponent namn>
```

## 2.

Skapa en till Angular komponent med namnet `shop`. Komponenten skall visa `Welcome to my shop!`. Länka till din nya komponent genom att lägga till en referens i `App` komponenten.

När du startar appen, eller sparar så att den laddas om (om du redan har startat den), så borde du se `Welcome to my shop!`.

## 3.

Skapa en ny komponent med valfritt namn. Lägg till en egenskap i komponentens klass som heter `hero` och skriv in en valfri superhjälte som värde (exempelvis `Ironman`). Rendera ut denna egenskap i HTML filen för komponenten.

## 4.

Något saknas i följande TypeScript fil för en komponent.

```typescript
@Component
class WelcomeComponent {
  title = "Welcome Page";
  subtitle: string = "Hello there";
}
```

Vad saknas, och fixas det?

## 5.

Identifiera alla fel i följande kod och fixa dem.

```typescript
@Component({
  selector: "app-user-profile",
  template: `
    <h1>{{ userName }}</h1>
    <p>Age: [userAge]</p>
    <p>Email: {{.userEmail}}</p>
  `,
})
export class UserProfileComponent {
  userName = "Ironman";
  userAge = 25;
  userEmail = "tony@stark.com";
}
```

## 6.

Du får följande TypeScript kod för en komponent:

```typescript
import { Component } from "@angular/core";

@Component({
  selector: "app-dice",
  templateUrl: "./dice.component.html",
  styleUrls: ["./dice.component.css"],
})
export class DiceComponent {
  random: number = Math.random();
}
```

Generera en egen komponent som heter `dice` och lägg in koden ovanför i `.ts` filen. Komponenten ska simulera ett spel och om `random` hamnar på `0.9` eller mer så vinner du en massa godis, men om den hamnar under `0.9` så förlorar du.

Rendera ut `Attans, denna gång vann jag inte.` om `random < 0.9`.

Rendera ut `Yay, jag vann!` om `random >= 0.9`.

Värdet `random` slumpas endast en gång, så du behöver ladda om sidan för att det ska slumpas om igen.

## 7.

Du får följande TypeScript kod för en komponent:

```typescript
import { Component } from "@angular/core";

@Component({
  selector: "app-languages",
  templateUrl: "./languages.component.html",
  styleUrls: ["./languages.component.css"],
})
export class LanguagesComponent {
  languages: string[] = [
    "JavaScript",
    "TypeScript",
    "Java",
    "C#",
    "C++",
    "Rust",
    "Go",
  ];
}
```

Generera en egen komponent som heter `languages` och lägg in koden ovanför i `.ts` filen. Gör sedan så att alla språk renderas ut som en lista (`ol` eller `ul`) i komponenten.

## 8.

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

## 9.

Skapa en ny komponent och lägg in ett inputfält. Det som skrivs in i fältet ska visas upp bredvid, samtidigt, i ett `span`. Använd `NgModel` för att implementera detta.

## 10.

Skapa en komponent som innehåller enkel routing genom `NgSwitch` (en egen form av routing, som att använda states för routing i React.) Lägg till tre vyer/routes med valfritt innehåll.

Vanligtvis byts routes med events (exempelvis knapptryck) och därför kan du använda följande kod för att slumpa fram en vy varje gång du laddar in sidan:

```typescript
import { Component } from "@angular/core";

function genNum() {
  return Math.floor(Math.random() * 3);
}

@Component({
  selector: "app-my-routes",
  templateUrl: "./my-routes.component.html",
  styleUrls: ["./my-routes.component.css"],
})
export class MyRoutesComponent {
  route: string = ["route1", "route2", "route3"][genNum()];
}
```

## 11.

Identifiera problemen med följande kod och fixa dem.

```typescript
@Component({
  selector: "app-task-list",
  template: `
      <ul>
       <li ngFor="task in tasks">
         <span ngIf="task.completed">✓</span>
         {{ task.name }}
       </li>
     </ul>
  `,
})
export class TaskListComponent {
  tasks = [
    { name: "Task 1", completed: true },
    { name: "Task 2", completed: false },
  ];
}
```

## 12.

Du får följande komponent:

```typescript
@Component({
  selector: "task-item",
  template: "<p>{{taskName}}</p>",
})
export class TaskItemComponent {
  taskName = "New Task";
}
```

I en annan komponent ser du följande:

```html
<div>
  <task-component></task-component>
</div>
```

Vad är felet?

## 13.

Identifiera och fixa alla fel i följande kod:

```typescript
@Component({
  selector: "app-highlight",
  template: `
        <div [ngclass]="{'highlight': isImportant, primary: isPrimary}">
            Important text
        </div>
    `,
})
export class HighlightComponent {
  isImportant = true;
  isPrimary = true;
}
```

## 14.

Identifiera och fixa alla fel i följande kod:

```typescript
@Component({
  selector: "app-style",
  template: `
        <div [ngStyle]="color: textColor; font-size: fontSize">
            Styled text
        </div>
    `,
})
export class StyleComponent {
  textColor = "blue";
  fontSize = "16px";
}
```

## 15.

Följande komponent har en if-sats ifall ett fel uppstår, genom `hasError` variabeln. Lägg till en `p` som säger `Success!` om det inte finns ett fel.

```typescript
@Component({
  selector: "app-message",
  template: `
        <div>
            <p *ngIf="hasError">Error occurred!</p>
        </div>
    `,
})
export class MessageComponent {
  hasError = false;
}
```

## 16.

Vilken av följande skall stå över klassen för en komponent?

a) `@component({...})`
b) `@Component({...})`
c) `@NgComponent({...})`
d) `@Angular.Component({...})`

## 17.

Vilken syntax är rätt för text interpolation?

a) `[[ value ]]`
b) `{{ value }}`
c) `{# value #}`
d) `[value]`

## 18.

Vilket directive används för att visa ett element baserat på ett villkor?

a) `*ngShow`
b) `*ngDisplay`
c) `*ngIf`
d) `*ngVisible`

## 19.

Vilken syntax är rätt för `ngFor` directives (då `items` är en array)?

a) `*ngFor="item in items"`
b) `*ngFor="var item of items"`
c) `*ngFor="let item from items"`
d) `*ngFor="let item of items"`

## 20.

Vilken egenskap i `@Component` (decorator, ovanför klass) bestämmer namnet på komponenten, som används i andra templates?

a) `name`
b) `selector`
c) `id`
d) `reference`

## 21.

Vilken syntax är rätt för `ngClass` med ett villkor?

a) `[ngClass]="{active: isActive}"`
b) `[ngClass]="active if isActive"`
c) `[ngClass]="isActive ? active"`
d) `[ngClass]="active when isActive"`

## 22.

Vilken syntax för `ngStyle` är rätt?

a) `[style]="{'color': 'red'}"`
b) `[ngStyle]="color: red"`
c) `[ngStyle]="{'color': 'red'}"`
d) `[styles]="{'color': 'red'}"`

## 23.

Vad betyder följande?

`*ngFor="let item of items; index as i"`

## 24.

Komponenter kan ha inline-templates eller ha separata (HTML-)filer. Vilken egenskap, i `@Component` (decorator, ovanför klass,) används för att använda en separat fil?

a) `template:`
b) `templateInline:`
c) `html:`
d) `templateUrl:`
