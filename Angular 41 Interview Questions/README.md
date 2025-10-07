# 🚀 41 Angular Interview Questions Every Frontend Developer Should Know

> Concise answers with essential code examples. Use Angular >= v12.

---

## 1) Bind dynamic HTML using [innerHTML]
```html
<div [innerHTML]="htmlContent"></div>
```
```ts
htmlContent = '<strong>Hello</strong> <em>Angular</em>';
```

## 2) Pass data parent ➜ child using @Input()
```ts
// child.component.ts
@Input() title!: string;
```
```html
<!-- parent.component.html -->
<app-child [title]="pageTitle"></app-child>
```

## 3) Call parent method from child using @Output() + EventEmitter
```ts
// child.component.ts
@Output() save = new EventEmitter<string>();
emitSave() { this.save.emit('payload'); }
```
```html
<!-- parent.component.html -->
<app-child (save)="onSave($event)"></app-child>
```
```ts
onSave(data: string) { /* handle */ }
```

## 4) Access DOM using @ViewChild / ElementRef
```ts
@ViewChild('inputRef') inputRef!: ElementRef<HTMLInputElement>;
ngAfterViewInit() { this.inputRef.nativeElement.focus(); }
```
```html
<input #inputRef />
```

## 5) Bind array/objects to dropdown using *ngFor
```html
<select [(ngModel)]="selectedId">
  <option *ngFor="let item of items" [value]="item.id">{{ item.name }}</option>
</select>
```
```ts
items = [{ id:1, name:'One' }, { id:2, name:'Two' }];
selectedId = 1;
```

## 6) Lazy-loaded modules in routing
```ts
const routes: Routes = [
  { path: 'admin', loadChildren: () => import('./admin/admin.module').then(m => m.AdminModule) }
];
```

## 7) Show user-entered data dynamically elsewhere
```html
<input [(ngModel)]="name" placeholder="Your name"/>
<p>You typed: {{ name }}</p>
```

## 8) Loop arrays/objects using *ngFor
```html
<li *ngFor="let u of users; index as i">{{ i+1 }}. {{ u.name }}</li>
```

## 9) Conditional render using *ngIf / ngSwitch
```html
<p *ngIf="isAdmin">Welcome, Admin</p>
<div [ngSwitch]="role">
  <p *ngSwitchCase="'admin'">Admin</p>
  <p *ngSwitchDefault>User</p>
</div>
```

## 10) Conditional styling with [ngClass] / [ngStyle]
```html
<div [ngClass]="{ active: isActive, danger: hasError }"
     [ngStyle]="{ color: isActive ? 'green' : 'gray' }">
  Status
</div>
```

## 11) Show/Hide based on condition
```html
<div *ngIf="show">Visible</div>
<button (click)="show = !show">Toggle</button>
```

## 12) Bind array to radio buttons
```html
<label *ngFor="let opt of options">
  <input type="radio" name="grp" [value]="opt" [(ngModel)]="selected" /> {{ opt }}
</label>
```

## 13) Display selected radio value
```html
<p>Selected: {{ selected }}</p>
```

## 14) Call a method on first render (ngOnInit)
```ts
ngOnInit() { this.loadData(); }
```

## 15) Loop object keys/values
```html
<div *ngFor="let k of objectKeys(obj)">{{ k }}: {{ obj[k] }}</div>
```
```ts
objectKeys = Object.keys;
obj = { a:1, b:2 };
```

## 16) How Angular detects re-render (Change Detection)
- Zone.js patches async tasks; change detection runs to reconcile bindings.
- Strategies: Default (checks all) vs OnPush (checks on input change, observable emit, event).

## 17) Run code on every re-render (ngDoCheck)
```ts
ngDoCheck() { // custom dirty checking if needed }
```

## 18) Add data dynamically to an array
```ts
items: string[] = [];
add(item: string) { this.items = [...this.items, item]; }
// or mutable: this.items.push(item);
```

## 19) Live search filter with ngModel + pipe
```html
<input [(ngModel)]="q" placeholder="Search" />
<li *ngFor="let u of users | filter:q">{{ u }}</li>
```
```ts
@Pipe({ name: 'filter', pure: true })
export class FilterPipe implements PipeTransform {
  transform(list: string[], q = '') { q = q.toLowerCase(); return list.filter(x => x.toLowerCase().includes(q)); }
}
```

## 20) Counter with RxJS (BehaviorSubject)
```ts
count$ = new BehaviorSubject(0);
increment() { this.count$.next(this.count$.value + 1); }
```
```html
<button (click)="increment()">+</button> {{ count$ | async }}
```

## 21) Counter with NgRx or service state
- NgRx: create action (increment), reducer, selector; dispatch on click; select count in template.
- Lightweight: service with BehaviorSubject shared via DI.

## 22) Control child input via @ViewChild
```ts
@ViewChild('childInput') childInput!: ElementRef<HTMLInputElement>;
enable() { this.childInput.nativeElement.disabled = false; }
```
```html
<input #childInput [disabled]="true" />
```

## 23) Debouncing with RxJS debounceTime()
```ts
search = new FormControl('');
results$ = this.search.valueChanges.pipe(
  debounceTime(300), distinctUntilChanged(), switchMap(q => this.api.search(q))
);
```

## 24) Fetch data using HttpClient
```ts
constructor(private http: HttpClient) {}
getUsers() { return this.http.get<User[]>('/api/users'); }
```

## 25) Force component re-render
- For OnPush: emit new reference (immutability) or use ChangeDetectorRef.markForCheck().
- As last resort: detach/reattach ChangeDetectorRef.

## 26) Run after view updates (ngAfterViewInit)
```ts
ngAfterViewInit() { // DOM is ready }
```

## 27) Remaining characters in textarea
```html
<textarea #ta (keyup)="update(ta.value)"></textarea>
<p>{{ max - current }}</p>
```
```ts
max = 200; current = 0;
update(val: string) { this.current = val.length; }
```

## 28) Dependent dropdowns (country ➜ state)
```html
<select [(ngModel)]="country" (change)="loadStates(country)">
  <option *ngFor="let c of countries" [value]="c">{{ c }}</option>
</select>
<select [(ngModel)]="state">
  <option *ngFor="let s of states" [value]="s">{{ s }}</option>
</select>
```
```ts
loadStates(country: string) { this.states = this.map[country] ?? []; }
```

## 29) Type checking with @Input()/interfaces
```ts
interface User { id: number; name: string; }
@Input() user!: User;
```

## 30) Share data via Services / BehaviorSubject
```ts
@Injectable({ providedIn: 'root' })
export class AppState {
  private user$ = new BehaviorSubject<User | null>(null);
  setUser(u: User) { this.user$.next(u); }
  getUser() { return this.user$.asObservable(); }
}
```

## 31) Optimize with ChangeDetectionStrategy.OnPush
```ts
@Component({ selector:'x', templateUrl:'x.html', changeDetection: ChangeDetectionStrategy.OnPush })
export class XComponent { @Input() data!: Data; }
```

## 32) Optimize with pure pipes / memoization
- Pure pipes run when input reference changes; cache expensive computations.
```ts
@Pipe({ name:'sum', pure: true })
export class SumPipe implements PipeTransform { transform(a:number[], b:number[]){ return a.length + b.length; } }
```

## 33) Error boundary equivalent with ErrorHandler
```ts
@Injectable()
export class GlobalErrorHandler implements ErrorHandler {
  handleError(error: unknown) {
    // log to server, show toast, etc.
    console.error(error);
  }
}
```
```ts
providers: [{ provide: ErrorHandler, useClass: GlobalErrorHandler }]
```

## 34) Display selected dropdown value elsewhere
```html
<select [(ngModel)]="city">
  <option *ngFor="let c of cities" [value]="c">{{ c }}</option>
</select>
<input [value]="city" readonly />
```

## 35) Pure component (stateless + OnPush)
```ts
@Component({ selector:'badge', template:`{{ label }}`, changeDetection: ChangeDetectionStrategy.OnPush })
export class BadgeComponent { @Input() label = ''; }
```

---

> Tip: Prefer immutable updates, leverage OnPush, async pipe, and typed interfaces for scalable Angular apps.
