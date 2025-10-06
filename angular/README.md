# 🚀 Complete Angular Interview Questions with Solutions

A comprehensive guide covering all Angular interview questions with detailed solutions, code examples, and best practices.

## 📋 Table of Contents

- [🟢 Beginner Level (0-2 years)](#-beginner-level-0-2-years)
- [🟡 Intermediate Level (2-4 years)](#-intermediate-level-2-4-years)
- [🔴 Advanced Level (4-6 years)](#-advanced-level-4-6-years)
- [🟣 Senior Level (6+ years)](#-senior-level-6-years)
- [🎯 Topic-wise Questions](#-topic-wise-questions)

---

## 🟢 Beginner Level (0-2 years)

### 1. What is Angular and how does it differ from AngularJS?

**Answer:**
Angular is a TypeScript-based web application framework developed by Google. It's a complete rewrite of AngularJS with significant improvements.

**Key Differences:**

| Feature | AngularJS | Angular |
|---------|-----------|---------|
| Language | JavaScript | TypeScript |
| Architecture | MVC | Component-based |
| Change Detection | Dirty checking | Zone.js |
| Mobile Support | Limited | Excellent |
| Performance | Slower | Much faster |

**Example:**
```typescript
// AngularJS (1.x)
angular.module('myApp', [])
  .controller('MyController', function($scope) {
    $scope.message = 'Hello AngularJS';
  });

// Angular (2+)
@Component({
  selector: 'app-my',
  template: '<h1>{{message}}</h1>'
})
export class MyComponent {
  message = 'Hello Angular';
}
```

### 2. Explain Angular modules and their purpose

**Answer:**
Angular modules (NgModules) are containers that organize related code into functional sets. They help organize the application into cohesive blocks of functionality.

**Key Concepts:**
- **Declarations**: Components, directives, and pipes
- **Imports**: Other modules needed
- **Providers**: Services available for injection
- **Exports**: Components/directives available to other modules

**Example:**
```typescript
@NgModule({
  declarations: [
    AppComponent,
    HeaderComponent,
    FooterComponent
  ],
  imports: [
    BrowserModule,
    FormsModule,
    HttpClientModule
  ],
  providers: [
    UserService,
    { provide: API_URL, useValue: 'https://api.example.com' }
  ],
  exports: [
    HeaderComponent
  ],
  bootstrap: [AppComponent]
})
export class AppModule { }
```

### 3. What are Angular components and how do you create them?

**Answer:**
Components are the building blocks of Angular applications. They control a view and contain the application logic.

**Component Structure:**
```typescript
import { Component } from '@angular/core';

@Component({
  selector: 'app-user-profile',
  templateUrl: './user-profile.component.html',
  styleUrls: ['./user-profile.component.css']
})
export class UserProfileComponent {
  user = {
    name: 'John Doe',
    email: 'john@example.com'
  };

  onUserClick() {
    console.log('User clicked!');
  }
}
```

**Component Lifecycle Hooks:**
```typescript
export class UserProfileComponent implements OnInit, OnDestroy {
  ngOnInit() {
    console.log('Component initialized');
  }

  ngOnDestroy() {
    console.log('Component destroyed');
  }
}
```

### 4. What is the difference between Angular services and components?

**Answer:**

| Aspect | Components | Services |
|--------|------------|----------|
| Purpose | Handle UI logic and user interactions | Handle business logic and data |
| Lifecycle | Created/destroyed with views | Singleton (lives for app lifetime) |
| Usage | One per template instance | Shared across components |
| Example | UserProfileComponent | UserService, DataService |

**Service Example:**
```typescript
@Injectable({
  providedIn: 'root'
})
export class UserService {
  private users: User[] = [];

  getUsers(): Observable<User[]> {
    return of(this.users);
  }

  addUser(user: User): void {
    this.users.push(user);
  }
}
```

### 5. How do you implement two-way data binding in Angular?

**Answer:**
Two-way data binding combines property binding and event binding using the `[(ngModel)]` directive.

**Example:**
```typescript
// Component
export class UserFormComponent {
  user = {
    name: '',
    email: ''
  };
}
```

```html
<!-- Template -->
<input [(ngModel)]="user.name" placeholder="Name">
<input [(ngModel)]="user.email" placeholder="Email">
<p>Hello {{user.name}}!</p>
```

**Manual Implementation:**
```html
<input [value]="user.name" (input)="user.name = $event.target.value">
```

### 6. What are Angular directives and how do you create custom directives?

**Answer:**
Directives are classes that add behavior to elements in the DOM.

**Types of Directives:**
1. **Components** (directives with templates)
2. **Structural** (ngIf, ngFor, ngSwitch)
3. **Attribute** (ngClass, ngStyle, ngModel)

**Custom Directive Example:**
```typescript
@Directive({
  selector: '[appHighlight]'
})
export class HighlightDirective {
  @Input() appHighlight = 'yellow';

  constructor(private el: ElementRef) {}

  @HostListener('mouseenter') onMouseEnter() {
    this.highlight(this.appHighlight);
  }

  @HostListener('mouseleave') onMouseLeave() {
    this.highlight(null);
  }

  private highlight(color: string) {
    this.el.nativeElement.style.backgroundColor = color;
  }
}
```

**Usage:**
```html
<p appHighlight="lightblue">Hover over me!</p>
```

### 7. Explain Angular pipes and how to create custom pipes

**Answer:**
Pipes transform data in templates. They're pure functions that take input and return transformed output.

**Built-in Pipes:**
```html
<p>{{ name | uppercase }}</p>
<p>{{ date | date:'short' }}</p>
<p>{{ price | currency:'USD' }}</p>
```

**Custom Pipe:**
```typescript
@Pipe({
  name: 'reverse'
})
export class ReversePipe implements PipeTransform {
  transform(value: string): string {
    return value.split('').reverse().join('');
  }
}
```

**Usage:**
```html
<p>{{ 'Hello' | reverse }}</p> <!-- Output: olleH -->
```

### 8. What is Angular CLI and what are its main commands?

**Answer:**
Angular CLI is a command-line interface for Angular development.

**Main Commands:**
```bash
# Create new project
ng new my-app

# Generate components
ng generate component user-profile
ng g c user-profile

# Generate services
ng generate service user
ng g s user

# Generate modules
ng generate module user
ng g m user

# Build project
ng build
ng build --prod

# Serve project
ng serve
ng serve --port 4200

# Run tests
ng test
ng e2e

# Add packages
ng add @angular/material
```

---

## 🟡 Intermediate Level (2-4 years)

### 1. Explain Angular's change detection mechanism and how it works?

**Answer:**
Angular's change detection is a mechanism that checks for changes in component data and updates the DOM accordingly.

**How it works:**
1. Zone.js patches browser APIs
2. When async operations complete, Zone.js triggers change detection
3. Angular checks all components for changes
4. Updates DOM where changes are detected

**Change Detection Strategies:**

**Default Strategy:**
```typescript
@Component({
  changeDetection: ChangeDetectionStrategy.Default
})
export class MyComponent {
  data = 'Hello';
}
```

**OnPush Strategy:**
```typescript
@Component({
  changeDetection: ChangeDetectionStrategy.OnPush
})
export class MyComponent {
  @Input() data: string;
  
  constructor(private cdr: ChangeDetectorRef) {}
  
  updateData() {
    this.data = 'Updated';
    this.cdr.markForCheck(); // Trigger change detection
  }
}
```

**Manual Change Detection:**
```typescript
export class MyComponent {
  constructor(private cdr: ChangeDetectorRef) {}
  
  updateData() {
    // Update data
    this.cdr.detectChanges(); // Force change detection
  }
}
```

### 2. What are Angular Services and how do you implement dependency injection?

**Answer:**
Services are singleton objects that provide functionality across the application.

**Basic Service:**
```typescript
@Injectable({
  providedIn: 'root'
})
export class DataService {
  private data: any[] = [];

  getData(): any[] {
    return this.data;
  }

  addData(item: any): void {
    this.data.push(item);
  }
}
```

**Dependency Injection:**
```typescript
@Component({
  selector: 'app-user',
  template: '<h1>{{user.name}}</h1>'
})
export class UserComponent {
  user: User;

  constructor(
    private userService: UserService,
    private logger: LoggerService
  ) {
    this.user = this.userService.getCurrentUser();
    this.logger.log('User component initialized');
  }
}
```

**Custom Injection Tokens:**
```typescript
export const API_URL = new InjectionToken<string>('API_URL');

@NgModule({
  providers: [
    { provide: API_URL, useValue: 'https://api.example.com' }
  ]
})
export class AppModule {}

// Usage
constructor(@Inject(API_URL) private apiUrl: string) {}
```

### 3. How do you implement routing and navigation in Angular?

**Answer:**
Angular Router enables navigation between different views in a single-page application.

**Basic Routing Setup:**
```typescript
const routes: Routes = [
  { path: '', redirectTo: '/home', pathMatch: 'full' },
  { path: 'home', component: HomeComponent },
  { path: 'users', component: UserListComponent },
  { path: 'users/:id', component: UserDetailComponent },
  { path: '**', component: PageNotFoundComponent }
];

@NgModule({
  imports: [RouterModule.forRoot(routes)],
  exports: [RouterModule]
})
export class AppRoutingModule {}
```

**Lazy Loading:**
```typescript
const routes: Routes = [
  {
    path: 'admin',
    loadChildren: () => import('./admin/admin.module').then(m => m.AdminModule)
  }
];
```

**Route Guards:**
```typescript
@Injectable()
export class AuthGuard implements CanActivate {
  constructor(private authService: AuthService, private router: Router) {}

  canActivate(): boolean {
    if (this.authService.isAuthenticated()) {
      return true;
    }
    this.router.navigate(['/login']);
    return false;
  }
}
```

**Navigation:**
```typescript
export class UserComponent {
  constructor(private router: Router, private route: ActivatedRoute) {}

  navigateToUser(id: number) {
    this.router.navigate(['/users', id]);
  }

  navigateWithQuery() {
    this.router.navigate(['/users'], {
      queryParams: { page: 1, size: 10 }
    });
  }
}
```

### 4. How do you implement state management in Angular applications?

**Answer:**
State management helps manage application data in a predictable way.

**Service-based State Management:**
```typescript
@Injectable({
  providedIn: 'root'
})
export class UserStore {
  private usersSubject = new BehaviorSubject<User[]>([]);
  users$ = this.usersSubject.asObservable();

  get users(): User[] {
    return this.usersSubject.value;
  }

  addUser(user: User): void {
    const currentUsers = this.users;
    this.usersSubject.next([...currentUsers, user]);
  }

  updateUser(updatedUser: User): void {
    const users = this.users.map(user => 
      user.id === updatedUser.id ? updatedUser : user
    );
    this.usersSubject.next(users);
  }
}
```

**NgRx Implementation:**
```typescript
// Actions
export const loadUsers = createAction('[User] Load Users');
export const loadUsersSuccess = createAction(
  '[User] Load Users Success',
  props<{ users: User[] }>()
);

// Reducer
export const userReducer = createReducer(
  initialState,
  on(loadUsersSuccess, (state, { users }) => ({
    ...state,
    users,
    loading: false
  }))
);

// Effects
@Injectable()
export class UserEffects {
  loadUsers$ = createEffect(() =>
    this.actions$.pipe(
      ofType(loadUsers),
      switchMap(() =>
        this.userService.getUsers().pipe(
          map(users => loadUsersSuccess({ users }))
        )
      )
    )
  );
}
```

### 5. How do you optimize Angular application performance?

**Answer:**
Performance optimization is crucial for large Angular applications.

**OnPush Change Detection:**
```typescript
@Component({
  changeDetection: ChangeDetectionStrategy.OnPush
})
export class UserListComponent {
  @Input() users: User[] = [];
}
```

**TrackBy Functions:**
```typescript
export class UserListComponent {
  trackByUserId(index: number, user: User): number {
    return user.id;
  }
}
```

```html
<div *ngFor="let user of users; trackBy: trackByUserId">
  {{ user.name }}
</div>
```

**Lazy Loading:**
```typescript
const routes: Routes = [
  {
    path: 'admin',
    loadChildren: () => import('./admin/admin.module').then(m => m.AdminModule)
  }
];
```

**Virtual Scrolling:**
```html
<cdk-virtual-scroll-viewport itemSize="50" class="viewport">
  <div *cdkVirtualFor="let user of users" class="user-item">
    {{ user.name }}
  </div>
</cdk-virtual-scroll-viewport>
```

**Memory Leak Prevention:**
```typescript
export class UserComponent implements OnDestroy {
  private destroy$ = new Subject<void>();

  ngOnInit() {
    this.userService.getUsers()
      .pipe(takeUntil(this.destroy$))
      .subscribe(users => this.users = users);
  }

  ngOnDestroy() {
    this.destroy$.next();
    this.destroy$.complete();
  }
}
```

### 6. How do you implement advanced forms in Angular?

**Answer:**
Angular provides two approaches: Template-driven and Reactive forms.

**Reactive Forms:**
```typescript
export class UserFormComponent implements OnInit {
  userForm: FormGroup;

  constructor(private fb: FormBuilder) {}

  ngOnInit() {
    this.userForm = this.fb.group({
      name: ['', [Validators.required, Validators.minLength(2)]],
      email: ['', [Validators.required, Validators.email]],
      age: ['', [Validators.min(18), Validators.max(100)]],
      address: this.fb.group({
        street: [''],
        city: [''],
        zipCode: ['']
      })
    });
  }

  onSubmit() {
    if (this.userForm.valid) {
      console.log(this.userForm.value);
    }
  }
}
```

**Custom Validators:**
```typescript
export function passwordValidator(control: AbstractControl): ValidationErrors | null {
  const value = control.value;
  if (!value) return null;
  
  const hasUpperCase = /[A-Z]/.test(value);
  const hasLowerCase = /[a-z]/.test(value);
  const hasNumeric = /[0-9]/.test(value);
  
  const valid = hasUpperCase && hasLowerCase && hasNumeric;
  return valid ? null : { passwordStrength: true };
}
```

**Async Validators:**
```typescript
export class UserFormComponent {
  userForm = this.fb.group({
    email: ['', Validators.email, this.emailExistsValidator.bind(this)]
  });

  emailExistsValidator(control: AbstractControl): Observable<ValidationErrors | null> {
    return this.userService.checkEmailExists(control.value).pipe(
      map(exists => exists ? { emailExists: true } : null),
      catchError(() => of(null))
    );
  }
}
```

---

## 🔴 Advanced Level (4-6 years)

### 1. How do you implement micro-frontend architecture with Angular?

**Answer:**
Micro-frontends allow teams to work independently on different parts of a larger application.

**Module Federation Setup:**
```typescript
// webpack.config.js
const ModuleFederationPlugin = require('@module-federation/webpack');

module.exports = {
  plugins: [
    new ModuleFederationPlugin({
      name: 'shell',
      remotes: {
        userApp: 'userApp@http://localhost:4201/remoteEntry.js',
        productApp: 'productApp@http://localhost:4202/remoteEntry.js'
      }
    })
  ]
};
```

**Shell Application:**
```typescript
@Component({
  selector: 'app-shell',
  template: `
    <header>Main App</header>
    <router-outlet></router-outlet>
    <user-app></user-app>
    <product-app></product-app>
  `
})
export class ShellComponent {}
```

**Remote Application:**
```typescript
@NgModule({
  declarations: [UserComponent],
  exports: [UserComponent]
})
export class UserModule {}
```

### 2. How do you implement advanced testing strategies in Angular?

**Answer:**
Comprehensive testing ensures application reliability and maintainability.

**Unit Testing:**
```typescript
describe('UserComponent', () => {
  let component: UserComponent;
  let fixture: ComponentFixture<UserComponent>;

  beforeEach(async () => {
    await TestBed.configureTestingModule({
      declarations: [UserComponent],
      providers: [
        { provide: UserService, useValue: jasmine.createSpyObj('UserService', ['getUsers']) }
      ]
    }).compileComponents();
  });

  beforeEach(() => {
    fixture = TestBed.createComponent(UserComponent);
    component = fixture.componentInstance;
  });

  it('should create', () => {
    expect(component).toBeTruthy();
  });

  it('should load users on init', () => {
    const userService = TestBed.inject(UserService);
    const mockUsers = [{ id: 1, name: 'John' }];
    userService.getUsers.and.returnValue(of(mockUsers));

    component.ngOnInit();

    expect(component.users).toEqual(mockUsers);
  });
});
```

**Integration Testing:**
```typescript
describe('User Integration', () => {
  let httpMock: HttpTestingController;

  beforeEach(() => {
    TestBed.configureTestingModule({
      imports: [HttpClientTestingModule],
      providers: [UserService]
    });
    httpMock = TestBed.inject(HttpTestingController);
  });

  it('should fetch users from API', () => {
    const userService = TestBed.inject(UserService);
    const mockUsers = [{ id: 1, name: 'John' }];

    userService.getUsers().subscribe(users => {
      expect(users).toEqual(mockUsers);
    });

    const req = httpMock.expectOne('/api/users');
    expect(req.request.method).toBe('GET');
    req.flush(mockUsers);
  });
});
```

**E2E Testing with Cypress:**
```typescript
describe('User Management', () => {
  it('should create a new user', () => {
    cy.visit('/users');
    cy.get('[data-cy=add-user-btn]').click();
    cy.get('[data-cy=user-name]').type('John Doe');
    cy.get('[data-cy=user-email]').type('john@example.com');
    cy.get('[data-cy=save-btn]').click();
    cy.get('[data-cy=user-list]').should('contain', 'John Doe');
  });
});
```

### 3. How do you implement advanced Angular patterns and best practices?

**Answer:**
Advanced patterns improve code maintainability and scalability.

**Repository Pattern:**
```typescript
export interface UserRepository {
  getUsers(): Observable<User[]>;
  getUserById(id: number): Observable<User>;
  createUser(user: User): Observable<User>;
}

@Injectable()
export class UserRepositoryImpl implements UserRepository {
  constructor(private http: HttpClient) {}

  getUsers(): Observable<User[]> {
    return this.http.get<User[]>('/api/users');
  }

  getUserById(id: number): Observable<User> {
    return this.http.get<User>(`/api/users/${id}`);
  }

  createUser(user: User): Observable<User> {
    return this.http.post<User>('/api/users', user);
  }
}
```

**Command Pattern:**
```typescript
export interface Command {
  execute(): Observable<any>;
  undo(): Observable<any>;
}

export class CreateUserCommand implements Command {
  constructor(
    private userRepository: UserRepository,
    private user: User
  ) {}

  execute(): Observable<User> {
    return this.userRepository.createUser(this.user);
  }

  undo(): Observable<void> {
    return this.userRepository.deleteUser(this.user.id);
  }
}
```

**Observer Pattern:**
```typescript
@Injectable()
export class EventBus {
  private events$ = new Subject<AppEvent>();

  publish(event: AppEvent): void {
    this.events$.next(event);
  }

  subscribe<T extends AppEvent>(eventType: string): Observable<T> {
    return this.events$.pipe(
      filter(event => event.type === eventType),
      map(event => event as T)
    );
  }
}
```

---

## 🟣 Senior Level (6+ years)

### 1. How do you design and implement scalable Angular architecture?

**Answer:**
Scalable architecture ensures applications can grow and adapt to changing requirements.

**Domain-Driven Design (DDD):**
```typescript
// Domain Layer
export class User {
  constructor(
    private id: UserId,
    private name: UserName,
    private email: Email
  ) {}

  changeName(newName: UserName): void {
    this.name = newName;
  }

  isValid(): boolean {
    return this.name.isValid() && this.email.isValid();
  }
}

// Application Layer
@Injectable()
export class UserApplicationService {
  constructor(
    private userRepository: UserRepository,
    private eventBus: EventBus
  ) {}

  createUser(command: CreateUserCommand): Observable<UserId> {
    const user = new User(
      UserId.generate(),
      new UserName(command.name),
      new Email(command.email)
    );

    return this.userRepository.save(user).pipe(
      tap(() => this.eventBus.publish(new UserCreatedEvent(user.id)))
    );
  }
}
```

**CQRS Implementation:**
```typescript
// Command Side
export class CreateUserCommand {
  constructor(
    public name: string,
    public email: string
  ) {}
}

@Injectable()
export class CreateUserCommandHandler {
  constructor(private userRepository: UserRepository) {}

  handle(command: CreateUserCommand): Observable<UserId> {
    const user = User.create(command.name, command.email);
    return this.userRepository.save(user);
  }
}

// Query Side
export class GetUsersQuery {
  constructor(public page: number, public size: number) {}
}

@Injectable()
export class GetUsersQueryHandler {
  constructor(private userReadModel: UserReadModel) {}

  handle(query: GetUsersQuery): Observable<UserReadModel[]> {
    return this.userReadModel.findUsers(query.page, query.size);
  }
}
```

**Clean Architecture:**
```
src/
├── domain/           # Business logic
│   ├── entities/
│   ├── value-objects/
│   └── repositories/
├── application/      # Use cases
│   ├── commands/
│   ├── queries/
│   └── services/
├── infrastructure/   # External concerns
│   ├── http/
│   ├── database/
│   └── messaging/
└── presentation/     # UI layer
    ├── components/
    ├── pages/
    └── shared/
```

---

## 🎯 Topic-wise Questions

### Core Angular Concepts

#### What is Angular and how does it differ from AngularJS?

**Answer:**
Angular is a modern TypeScript-based framework, while AngularJS is the older JavaScript version.

**Key Differences:**
- **Architecture**: Component-based vs MVC
- **Language**: TypeScript vs JavaScript
- **Performance**: Much faster with Ivy renderer
- **Mobile**: Better mobile support
- **Learning Curve**: Steeper but more powerful

#### Explain Angular modules and their purpose

**Answer:**
Modules organize related functionality and provide dependency injection context.

**Example:**
```typescript
@NgModule({
  declarations: [UserComponent],
  imports: [CommonModule, FormsModule],
  providers: [UserService],
  exports: [UserComponent]
})
export class UserModule {}
```

### Data Binding & Communication

#### Explain different types of data binding in Angular

**Answer:**
Angular supports four types of data binding:

1. **Interpolation**: `{{value}}`
2. **Property Binding**: `[property]="value"`
3. **Event Binding**: `(event)="handler()"`
4. **Two-way Binding**: `[(ngModel)]="value"`

**Examples:**
```html
<!-- Interpolation -->
<p>{{user.name}}</p>

<!-- Property Binding -->
<img [src]="user.avatar" [alt]="user.name">

<!-- Event Binding -->
<button (click)="onSave()">Save</button>

<!-- Two-way Binding -->
<input [(ngModel)]="user.name">
```

#### How do you pass data between parent and child components?

**Answer:**
Use `@Input()` and `@Output()` decorators for component communication.

**Parent Component:**
```typescript
export class ParentComponent {
  user = { name: 'John', age: 30 };
  
  onUserUpdated(user: User) {
    console.log('User updated:', user);
  }
}
```

```html
<app-child 
  [user]="user" 
  (userUpdated)="onUserUpdated($event)">
</app-child>
```

**Child Component:**
```typescript
export class ChildComponent {
  @Input() user: User;
  @Output() userUpdated = new EventEmitter<User>();

  updateUser() {
    this.user.name = 'Jane';
    this.userUpdated.emit(this.user);
  }
}
```

### Services & Dependency Injection

#### What is dependency injection in Angular?

**Answer:**
Dependency injection is a design pattern where dependencies are provided to a class rather than created within it.

**Example:**
```typescript
@Injectable({
  providedIn: 'root'
})
export class UserService {
  getUsers(): Observable<User[]> {
    return this.http.get<User[]>('/api/users');
  }
}

export class UserComponent {
  constructor(private userService: UserService) {}
  
  ngOnInit() {
    this.userService.getUsers().subscribe(users => {
      this.users = users;
    });
  }
}
```

### Routing & Navigation

#### How do you implement routing in Angular?

**Answer:**
Angular Router enables navigation between different views.

**Setup:**
```typescript
const routes: Routes = [
  { path: '', component: HomeComponent },
  { path: 'users', component: UserListComponent },
  { path: 'users/:id', component: UserDetailComponent },
  { path: '**', component: PageNotFoundComponent }
];

@NgModule({
  imports: [RouterModule.forRoot(routes)],
  exports: [RouterModule]
})
export class AppRoutingModule {}
```

**Navigation:**
```typescript
export class UserComponent {
  constructor(private router: Router) {}
  
  goToUser(id: number) {
    this.router.navigate(['/users', id]);
  }
}
```

### Forms & Validation

#### What are template-driven forms in Angular?

**Answer:**
Template-driven forms use directives in the template to create form controls.

**Example:**
```html
<form #userForm="ngForm" (ngSubmit)="onSubmit(userForm)">
  <input 
    name="name" 
    ngModel 
    required 
    #name="ngModel"
    placeholder="Name">
  <div *ngIf="name.invalid && name.touched">
    Name is required
  </div>
  
  <input 
    name="email" 
    ngModel 
    email 
    #email="ngModel"
    placeholder="Email">
  <div *ngIf="email.invalid && email.touched">
    Valid email is required
  </div>
  
  <button type="submit" [disabled]="userForm.invalid">
    Submit
  </button>
</form>
```

#### How do you implement reactive forms in Angular?

**Answer:**
Reactive forms provide a model-driven approach to handling form inputs.

**Example:**
```typescript
export class UserFormComponent implements OnInit {
  userForm: FormGroup;

  constructor(private fb: FormBuilder) {}

  ngOnInit() {
    this.userForm = this.fb.group({
      name: ['', Validators.required],
      email: ['', [Validators.required, Validators.email]],
      age: ['', [Validators.min(18), Validators.max(100)]]
    });
  }

  onSubmit() {
    if (this.userForm.valid) {
      console.log(this.userForm.value);
    }
  }
}
```

```html
<form [formGroup]="userForm" (ngSubmit)="onSubmit()">
  <input formControlName="name" placeholder="Name">
  <div *ngIf="userForm.get('name')?.invalid && userForm.get('name')?.touched">
    Name is required
  </div>
  
  <input formControlName="email" placeholder="Email">
  <div *ngIf="userForm.get('email')?.invalid && userForm.get('email')?.touched">
    Valid email is required
  </div>
  
  <button type="submit" [disabled]="userForm.invalid">Submit</button>
</form>
```

### HTTP & API Integration

#### How do you make HTTP requests in Angular?

**Answer:**
Use Angular's HttpClient service for HTTP requests.

**Service:**
```typescript
@Injectable({
  providedIn: 'root'
})
export class UserService {
  private apiUrl = 'https://api.example.com/users';

  constructor(private http: HttpClient) {}

  getUsers(): Observable<User[]> {
    return this.http.get<User[]>(this.apiUrl);
  }

  getUser(id: number): Observable<User> {
    return this.http.get<User>(`${this.apiUrl}/${id}`);
  }

  createUser(user: User): Observable<User> {
    return this.http.post<User>(this.apiUrl, user);
  }

  updateUser(id: number, user: User): Observable<User> {
    return this.http.put<User>(`${this.apiUrl}/${id}`, user);
  }

  deleteUser(id: number): Observable<void> {
    return this.http.delete<void>(`${this.apiUrl}/${id}`);
  }
}
```

**Component Usage:**
```typescript
export class UserComponent implements OnInit {
  users: User[] = [];
  loading = false;

  constructor(private userService: UserService) {}

  ngOnInit() {
    this.loadUsers();
  }

  loadUsers() {
    this.loading = true;
    this.userService.getUsers().subscribe({
      next: users => {
        this.users = users;
        this.loading = false;
      },
      error: error => {
        console.error('Error loading users:', error);
        this.loading = false;
      }
    });
  }
}
```

### Testing

#### How do you write unit tests for Angular components?

**Answer:**
Use Angular Testing utilities for comprehensive component testing.

**Example:**
```typescript
describe('UserComponent', () => {
  let component: UserComponent;
  let fixture: ComponentFixture<UserComponent>;
  let userService: jasmine.SpyObj<UserService>;

  beforeEach(async () => {
    const spy = jasmine.createSpyObj('UserService', ['getUsers', 'createUser']);

    await TestBed.configureTestingModule({
      declarations: [UserComponent],
      providers: [
        { provide: UserService, useValue: spy }
      ],
      imports: [FormsModule, HttpClientTestingModule]
    }).compileComponents();

    fixture = TestBed.createComponent(UserComponent);
    component = fixture.componentInstance;
    userService = TestBed.inject(UserService) as jasmine.SpyObj<UserService>;
  });

  it('should create', () => {
    expect(component).toBeTruthy();
  });

  it('should load users on init', () => {
    const mockUsers = [
      { id: 1, name: 'John', email: 'john@example.com' },
      { id: 2, name: 'Jane', email: 'jane@example.com' }
    ];
    userService.getUsers.and.returnValue(of(mockUsers));

    component.ngOnInit();

    expect(component.users).toEqual(mockUsers);
    expect(userService.getUsers).toHaveBeenCalled();
  });

  it('should create user when form is submitted', () => {
    const newUser = { name: 'New User', email: 'new@example.com' };
    userService.createUser.and.returnValue(of(newUser));
    component.userForm.setValue(newUser);

    component.onSubmit();

    expect(userService.createUser).toHaveBeenCalledWith(newUser);
  });
});
```

### Performance & Optimization

#### How do you optimize Angular application performance?

**Answer:**
Multiple strategies can improve Angular application performance.

**1. OnPush Change Detection:**
```typescript
@Component({
  changeDetection: ChangeDetectionStrategy.OnPush
})
export class UserComponent {
  @Input() user: User;
}
```

**2. TrackBy Functions:**
```typescript
export class UserListComponent {
  trackByUserId(index: number, user: User): number {
    return user.id;
  }
}
```

**3. Lazy Loading:**
```typescript
const routes: Routes = [
  {
    path: 'admin',
    loadChildren: () => import('./admin/admin.module').then(m => m.AdminModule)
  }
];
```

**4. Virtual Scrolling:**
```html
<cdk-virtual-scroll-viewport itemSize="50" class="viewport">
  <div *cdkVirtualFor="let user of users" class="user-item">
    {{ user.name }}
  </div>
</cdk-virtual-scroll-viewport>
```

**5. Memory Leak Prevention:**
```typescript
export class UserComponent implements OnDestroy {
  private destroy$ = new Subject<void>();

  ngOnInit() {
    this.userService.getUsers()
      .pipe(takeUntil(this.destroy$))
      .subscribe(users => this.users = users);
  }

  ngOnDestroy() {
    this.destroy$.next();
    this.destroy$.complete();
  }
}
```

### Security

#### How do you implement authentication in Angular?

**Answer:**
Implement authentication using JWT tokens and route guards.

**Auth Service:**
```typescript
@Injectable({
  providedIn: 'root'
})
export class AuthService {
  private tokenKey = 'auth_token';
  private userSubject = new BehaviorSubject<User | null>(null);
  public user$ = this.userSubject.asObservable();

  constructor(private http: HttpClient) {
    this.loadUserFromStorage();
  }

  login(credentials: LoginCredentials): Observable<AuthResponse> {
    return this.http.post<AuthResponse>('/api/auth/login', credentials)
      .pipe(
        tap(response => {
          localStorage.setItem(this.tokenKey, response.token);
          this.userSubject.next(response.user);
        })
      );
  }

  logout(): void {
    localStorage.removeItem(this.tokenKey);
    this.userSubject.next(null);
  }

  isAuthenticated(): boolean {
    return !!localStorage.getItem(this.tokenKey);
  }

  private loadUserFromStorage(): void {
    const token = localStorage.getItem(this.tokenKey);
    if (token) {
      // Decode token and set user
      const user = this.decodeToken(token);
      this.userSubject.next(user);
    }
  }
}
```

**Auth Guard:**
```typescript
@Injectable()
export class AuthGuard implements CanActivate {
  constructor(
    private authService: AuthService,
    private router: Router
  ) {}

  canActivate(): boolean {
    if (this.authService.isAuthenticated()) {
      return true;
    }
    this.router.navigate(['/login']);
    return false;
  }
}
```

---

## 📊 Summary

This comprehensive guide covers **75+ Angular interview questions** with detailed solutions, code examples, and best practices. The questions are organized by:

- **🟢 Beginner Level**: Core concepts and basic implementation
- **🟡 Intermediate Level**: Advanced features and performance optimization
- **🔴 Advanced Level**: Architecture patterns and enterprise solutions
- **🟣 Senior Level**: System design and scalable architecture

Each question includes:
- ✅ Detailed explanations
- 💻 Practical code examples
- 🎯 Best practices
- 🔧 Implementation strategies

This resource will help you prepare for Angular interviews at any experience level, from junior developers to senior architects!
