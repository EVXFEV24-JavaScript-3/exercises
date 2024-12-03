# Övningar - Lektion 4

## 1.

Förklara varje variabel, funktion, klass, constructor och interface med en kommentar i följande kod.

```ts
// book.model.ts
export interface Book {
  id: number;
  title: string;
  author: string;
}
```

```html
<!-- book-list.component.html -->
<div>
    <h2>Böcker</h2>
    <ul>
        <li *ngFor="let book of books">
            {{ book.title }} av {{ book.author }}
        </li>
    </ul>

    <form (ngSubmit)="onSubmit()">
        <input [(ngModel)]="newBook.title" name="title" placeholder="Titel">
        <input [(ngModel)]="newBook.author" name="author" placeholder="Författare">
        <button type="submit">Lägg till bok</button>
    </form>
</div>
```

```ts
// book-list.component.ts
@Component({
  selector: "app-book-list",
  templateUrl: "./book-list.component.html",
  styleUrls: ["./book-list.component.css"],
})
export class BookListComponent {
  newBook: Book = { id: 0, title: "", author: "" };

  constructor(private bookService: BookService) {}

  get books(): Book[] {
    return this.bookService.books;
  }

  onSubmit() {
    this.bookService.addBook(this.newBook);
  }
}
```

```ts
// book.service.ts
@Injectable({
  providedIn: "root",
})
export class BookService {
  private apiUrl = "https://fake-api.com/api/books";
  private apiBooks: Book[] = [];

  constructor() {
    fetch(this.apiUrl)
      .then(res => res.json())
      .then(res => this.apiBooks = res);
  }

  public get books(): Book[] {
    return this.apiBooks;
  }

  addBook(book: Book): void {
    this.books.push(book);
  }
}
```

## 2.

**Samma övning som Övningar - Lektion 3, men med dependency injection.**

Skapa en sida som består av en knapp och en box. Vid knapptryck ska ett slumpat citat dyka upp i boxen. Använd citat från DummyJSON. Hantera alla citat genom Dependency Injection och Angular services.
