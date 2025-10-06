# Angular Interview Questions for Experienced Developers (4-5 Years)

## 🎯 Difficulty Levels
- **🟢 Intermediate**: Core Angular concepts and best practices
- **🟡 Advanced**: Performance optimization and complex scenarios
- **🔴 Expert**: Architecture, scalability, and enterprise-level solutions
- **🟣 Senior**: System design, team leadership, and advanced patterns

## 📋 Questions

### 🟢 Intermediate Level

#### 1. Explain Angular's change detection mechanism and how it works?
**Answer:**
Angular's change detection is a mechanism that determines when and how to update the view when the model changes.

```typescript
// Default Change Detection Strategy
@Component({
  selector: 'app-user',
  template: `<div>{{ user.name }}</div>`,
  changeDetection: ChangeDetectionStrategy.Default
})
export class UserComponent {
  user = { name: 'John' };
  
  updateUser() {
    this.user.name = 'Jane'; // Triggers change detection
  }
}

// OnPush Change Detection Strategy
@Component({
  selector: 'app-user-push',
  template: `<div>{{ user.name }}</div>`,
  changeDetection: ChangeDetectionStrategy.OnPush
})
export class UserPushComponent {
  @Input() user: User;
  
  constructor(private cdr: ChangeDetectorRef) {}
  
  updateUser() {
    this.user.name = 'Jane';
    this.cdr.markForCheck(); // Manual trigger for OnPush
  }
}

// Custom Change Detection
@Component({
  selector: 'app-custom',
  template: `<div>{{ data }}</div>`,
  changeDetection: ChangeDetectionStrategy.OnPush
})
export class CustomComponent {
  data = 'Initial';
  
  constructor(private cdr: ChangeDetectorRef) {}
  
  updateData() {
    this.data = 'Updated';
    this.cdr.detectChanges(); // Immediate change detection
  }
}
```

**Key Concepts:**
- Change Detection Strategy
- OnPush vs Default
- ChangeDetectorRef
- Performance implications
- Zone.js integration

#### 2. What are Angular Services and how do you implement dependency injection?
**Answer:**
Services are singleton objects that provide functionality across the application:

```typescript
// Basic Service
@Injectable({
  providedIn: 'root' // Singleton service
})
export class UserService {
  private users: User[] = [];
  
  getUsers(): Observable<User[]> {
    return of(this.users);
  }
  
  addUser(user: User): void {
    this.users.push(user);
  }
  
  updateUser(id: number, user: User): void {
    const index = this.users.findIndex(u => u.id === id);
    if (index !== -1) {
      this.users[index] = user;
    }
  }
}

// Service with HTTP
@Injectable({
  providedIn: 'root'
})
export class ApiService {
  private apiUrl = 'https://api.example.com';
  
  constructor(private http: HttpClient) {}
  
  get<T>(endpoint: string): Observable<T> {
    return this.http.get<T>(`${this.apiUrl}/${endpoint}`);
  }
  
  post<T>(endpoint: string, data: any): Observable<T> {
    return this.http.post<T>(`${this.apiUrl}/${endpoint}`, data);
  }
}

// Custom Injection Token
export const API_CONFIG = new InjectionToken<ApiConfig>('API_CONFIG');

@Injectable({
  providedIn: 'root'
})
export class ConfigService {
  constructor(@Inject(API_CONFIG) private config: ApiConfig) {}
  
  getApiUrl(): string {
    return this.config.apiUrl;
  }
}

// Module-level Service
@NgModule({
  providers: [
    { provide: 'APP_CONFIG', useValue: { apiUrl: 'https://api.example.com' } }
  ]
})
export class AppModule {}
```

**Key Concepts:**
- Dependency Injection
- Service lifecycle
- Injection tokens
- Provider configuration
- Singleton pattern

#### 3. How do you implement routing and navigation in Angular?
**Answer:**
Angular Router provides navigation and routing capabilities:

```typescript
// App Routing Module
const routes: Routes = [
  { path: '', redirectTo: '/home', pathMatch: 'full' },
  { path: 'home', component: HomeComponent },
  { path: 'users', component: UserListComponent },
  { path: 'users/:id', component: UserDetailComponent },
  { path: 'users/:id/edit', component: UserEditComponent },
  { path: 'admin', loadChildren: () => import('./admin/admin.module').then(m => m.AdminModule) },
  { path: '**', component: PageNotFoundComponent }
];

@NgModule({
  imports: [RouterModule.forRoot(routes, {
    enableTracing: false,
    preloadingStrategy: PreloadAllModules
  })],
  exports: [RouterModule]
})
export class AppRoutingModule {}

// Component with Navigation
@Component({
  selector: 'app-user-list',
  template: `
    <div *ngFor="let user of users">
      <a [routerLink]="['/users', user.id]">{{ user.name }}</a>
      <button (click)="editUser(user.id)">Edit</button>
    </div>
  `
})
export class UserListComponent {
  users: User[] = [];
  
  constructor(
    private router: Router,
    private route: ActivatedRoute
  ) {}
  
  editUser(id: number): void {
    this.router.navigate(['/users', id, 'edit']);
  }
  
  navigateWithQuery(): void {
    this.router.navigate(['/users'], {
      queryParams: { page: 1, size: 10 },
      fragment: 'top'
    });
  }
}

// Route Guards
@Injectable({
  providedIn: 'root'
})
export class AuthGuard implements CanActivate {
  constructor(private authService: AuthService, private router: Router) {}
  
  canActivate(route: ActivatedRouteSnapshot, state: RouterStateSnapshot): boolean {
    if (this.authService.isAuthenticated()) {
      return true;
    }
    
    this.router.navigate(['/login'], { queryParams: { returnUrl: state.url } });
    return false;
  }
}

// Resolver
@Injectable({
  providedIn: 'root'
})
export class UserResolver implements Resolve<User> {
  constructor(private userService: UserService) {}
  
  resolve(route: ActivatedRouteSnapshot): Observable<User> {
    const id = route.paramMap.get('id');
    return this.userService.getUser(+id);
  }
}
```

**Key Concepts:**
- Route configuration
- Navigation methods
- Route guards
- Route resolvers
- Lazy loading
- Route parameters

### 🟡 Advanced Level

#### 4. How do you implement state management in Angular applications?
**Answer:**
State management patterns for complex Angular applications:

```typescript
// NgRx Store Implementation
// user.actions.ts
export const loadUsers = createAction('[User] Load Users');
export const loadUsersSuccess = createAction(
  '[User] Load Users Success',
  props<{ users: User[] }>()
);
export const loadUsersFailure = createAction(
  '[User] Load Users Failure',
  props<{ error: string }>()
);

// user.reducer.ts
export interface UserState {
  users: User[];
  loading: boolean;
  error: string | null;
}

const initialState: UserState = {
  users: [],
  loading: false,
  error: null
};

export const userReducer = createReducer(
  initialState,
  on(loadUsers, (state) => ({ ...state, loading: true })),
  on(loadUsersSuccess, (state, { users }) => ({
    ...state,
    users,
    loading: false
  })),
  on(loadUsersFailure, (state, { error }) => ({
    ...state,
    error,
    loading: false
  }))
);

// user.effects.ts
@Injectable()
export class UserEffects {
  loadUsers$ = createEffect(() =>
    this.actions$.pipe(
      ofType(loadUsers),
      switchMap(() =>
        this.userService.getUsers().pipe(
          map(users => loadUsersSuccess({ users })),
          catchError(error => of(loadUsersFailure({ error: error.message })))
        )
      )
    )
  );
  
  constructor(
    private actions$: Actions,
    private userService: UserService
  ) {}
}

// Component with NgRx
@Component({
  selector: 'app-user-list',
  template: `
    <div *ngIf="loading$ | async">Loading...</div>
    <div *ngFor="let user of users$ | async">
      {{ user.name }}
    </div>
  `
})
export class UserListComponent implements OnInit {
  users$ = this.store.select(selectUsers);
  loading$ = this.store.select(selectLoading);
  
  constructor(private store: Store) {}
  
  ngOnInit(): void {
    this.store.dispatch(loadUsers());
  }
}

// Alternative: Service-based State Management
@Injectable({
  providedIn: 'root'
})
export class UserStateService {
  private usersSubject = new BehaviorSubject<User[]>([]);
  private loadingSubject = new BehaviorSubject<boolean>(false);
  
  users$ = this.usersSubject.asObservable();
  loading$ = this.loadingSubject.asObservable();
  
  constructor(private userService: UserService) {}
  
  loadUsers(): void {
    this.loadingSubject.next(true);
    this.userService.getUsers().subscribe({
      next: (users) => {
        this.usersSubject.next(users);
        this.loadingSubject.next(false);
      },
      error: (error) => {
        this.loadingSubject.next(false);
        console.error('Error loading users:', error);
      }
    });
  }
  
  addUser(user: User): void {
    const currentUsers = this.usersSubject.value;
    this.usersSubject.next([...currentUsers, user]);
  }
}
```

**Key Concepts:**
- NgRx Store
- Actions, Reducers, Effects
- Selectors
- Service-based state
- State normalization

#### 5. How do you optimize Angular application performance?
**Answer:**
Advanced performance optimization techniques:

```typescript
// OnPush Change Detection
@Component({
  selector: 'app-user-card',
  template: `<div>{{ user.name }}</div>`,
  changeDetection: ChangeDetectionStrategy.OnPush
})
export class UserCardComponent {
  @Input() user: User;
  
  constructor(private cdr: ChangeDetectorRef) {}
}

// TrackBy Function for *ngFor
@Component({
  selector: 'app-user-list',
  template: `
    <div *ngFor="let user of users; trackBy: trackByUserId">
      {{ user.name }}
    </div>
  `
})
export class UserListComponent {
  users: User[] = [];
  
  trackByUserId(index: number, user: User): number {
    return user.id;
  }
}

// Lazy Loading with Preloading Strategy
const routes: Routes = [
  {
    path: 'admin',
    loadChildren: () => import('./admin/admin.module').then(m => m.AdminModule),
    data: { preload: true }
  }
];

@NgModule({
  imports: [RouterModule.forRoot(routes, {
    preloadingStrategy: CustomPreloadingStrategy
  })]
})
export class AppRoutingModule {}

// Custom Preloading Strategy
@Injectable({
  providedIn: 'root'
})
export class CustomPreloadingStrategy implements PreloadingStrategy {
  preload(route: Route, load: () => Observable<any>): Observable<any> {
    if (route.data && route.data['preload']) {
      return load();
    }
    return of(null);
  }
}

// Virtual Scrolling
@Component({
  selector: 'app-virtual-list',
  template: `
    <cdk-virtual-scroll-viewport itemSize="50" class="viewport">
      <div *cdkVirtualFor="let user of users" class="item">
        {{ user.name }}
      </div>
    </cdk-virtual-scroll-viewport>
  `,
  styles: [`
    .viewport {
      height: 400px;
    }
    .item {
      height: 50px;
    }
  `]
})
export class VirtualListComponent {
  users: User[] = [];
  
  constructor() {
    // Generate large dataset
    this.users = Array.from({ length: 10000 }, (_, i) => ({
      id: i,
      name: `User ${i}`
    }));
  }
}

// Memory Leak Prevention
@Component({
  selector: 'app-user-detail',
  template: `<div>{{ user.name }}</div>`
})
export class UserDetailComponent implements OnInit, OnDestroy {
  private destroy$ = new Subject<void>();
  user: User;
  
  constructor(private userService: UserService) {}
  
  ngOnInit(): void {
    this.userService.getUser(1)
      .pipe(takeUntil(this.destroy$))
      .subscribe(user => this.user = user);
  }
  
  ngOnDestroy(): void {
    this.destroy$.next();
    this.destroy$.complete();
  }
}

// Bundle Optimization
// webpack.config.js
module.exports = {
  optimization: {
    splitChunks: {
      chunks: 'all',
      cacheGroups: {
        vendor: {
          test: /[\\/]node_modules[\\/]/,
          name: 'vendors',
          chunks: 'all'
        }
      }
    }
  }
};
```

**Key Concepts:**
- Change detection optimization
- TrackBy functions
- Lazy loading
- Virtual scrolling
- Memory leak prevention
- Bundle optimization

#### 6. How do you implement advanced forms in Angular?
**Answer:**
Complex form handling with validation and dynamic forms:

```typescript
// Reactive Forms with Custom Validators
@Component({
  selector: 'app-user-form',
  template: `
    <form [formGroup]="userForm" (ngSubmit)="onSubmit()">
      <div>
        <label>Name:</label>
        <input formControlName="name" />
        <div *ngIf="name.invalid && name.touched">
          <div *ngIf="name.errors?.['required']">Name is required</div>
          <div *ngIf="name.errors?.['minlength']">Name must be at least 3 characters</div>
        </div>
      </div>
      
      <div>
        <label>Email:</label>
        <input formControlName="email" />
        <div *ngIf="email.invalid && email.touched">
          <div *ngIf="email.errors?.['email']">Invalid email format</div>
        </div>
      </div>
      
      <div formArrayName="addresses">
        <div *ngFor="let address of addresses.controls; let i = index" [formGroupName]="i">
          <input formControlName="street" placeholder="Street" />
          <input formControlName="city" placeholder="City" />
          <button type="button" (click)="removeAddress(i)">Remove</button>
        </div>
        <button type="button" (click)="addAddress()">Add Address</button>
      </div>
      
      <button type="submit" [disabled]="userForm.invalid">Submit</button>
    </form>
  `
})
export class UserFormComponent implements OnInit {
  userForm: FormGroup;
  
  constructor(private fb: FormBuilder) {
    this.userForm = this.fb.group({
      name: ['', [Validators.required, Validators.minLength(3)]],
      email: ['', [Validators.required, Validators.email]],
      addresses: this.fb.array([])
    });
  }
  
  get name() { return this.userForm.get('name'); }
  get email() { return this.userForm.get('email'); }
  get addresses() { return this.userForm.get('addresses') as FormArray; }
  
  addAddress(): void {
    const addressGroup = this.fb.group({
      street: ['', Validators.required],
      city: ['', Validators.required]
    });
    this.addresses.push(addressGroup);
  }
  
  removeAddress(index: number): void {
    this.addresses.removeAt(index);
  }
  
  onSubmit(): void {
    if (this.userForm.valid) {
      console.log(this.userForm.value);
    }
  }
}

// Custom Validator
export function customValidator(control: AbstractControl): ValidationErrors | null {
  const value = control.value;
  if (value && value.includes('test')) {
    return { customError: true };
  }
  return null;
}

// Async Validator
export function asyncEmailValidator(userService: UserService) {
  return (control: AbstractControl): Observable<ValidationErrors | null> => {
    if (!control.value) {
      return of(null);
    }
    
    return userService.checkEmailExists(control.value).pipe(
      map(exists => exists ? { emailExists: true } : null),
      catchError(() => of(null))
    );
  };
}

// Dynamic Forms
@Component({
  selector: 'app-dynamic-form',
  template: `
    <form [formGroup]="form" (ngSubmit)="onSubmit()">
      <div *ngFor="let field of fields" [formGroupName]="field.key">
        <ng-container [ngSwitch]="field.type">
          <input *ngSwitchCase="'text'" [formControlName]="field.control" [placeholder]="field.placeholder" />
          <select *ngSwitchCase="'select'" [formControlName]="field.control">
            <option *ngFor="let option of field.options" [value]="option.value">
              {{ option.label }}
            </option>
          </select>
        </ng-container>
      </div>
      <button type="submit">Submit</button>
    </form>
  `
})
export class DynamicFormComponent {
  form: FormGroup;
  fields: DynamicField[] = [];
  
  constructor(private fb: FormBuilder) {
    this.fields = [
      { key: 'name', type: 'text', control: 'name', placeholder: 'Name' },
      { key: 'email', type: 'text', control: 'email', placeholder: 'Email' },
      { key: 'country', type: 'select', control: 'country', options: [
        { value: 'us', label: 'United States' },
        { value: 'ca', label: 'Canada' }
      ]}
    ];
    
    this.form = this.fb.group({});
    this.fields.forEach(field => {
      this.form.addControl(field.key, this.fb.group({}));
      this.form.get(field.key)?.addControl(field.control, this.fb.control(''));
    });
  }
}
```

**Key Concepts:**
- Reactive forms
- Custom validators
- Async validators
- Dynamic forms
- Form arrays
- Validation patterns

### 🔴 Expert Level

#### 7. How do you implement micro-frontend architecture with Angular?
**Answer:**
Micro-frontend architecture for large-scale applications:

```typescript
// Shell Application (Main App)
// app.module.ts
@NgModule({
  declarations: [AppComponent],
  imports: [
    BrowserModule,
    RouterModule.forRoot([
      { path: 'users', loadChildren: () => import('user-mfe/UserModule') },
      { path: 'products', loadChildren: () => import('product-mfe/ProductModule') }
    ])
  ],
  providers: [
    {
      provide: 'SHARED_STATE',
      useValue: new BehaviorSubject({})
    }
  ],
  bootstrap: [AppComponent]
})
export class AppModule {}

// Micro-frontend Module
// user-mfe/user.module.ts
@NgModule({
  declarations: [UserListComponent, UserDetailComponent],
  imports: [
    CommonModule,
    RouterModule.forChild([
      { path: '', component: UserListComponent },
      { path: ':id', component: UserDetailComponent }
    ])
  ],
  providers: [
    UserService,
    {
      provide: 'SHARED_STATE',
      useExisting: 'SHARED_STATE'
    }
  ]
})
export class UserModule {}

// Shared State Service
@Injectable({
  providedIn: 'root'
})
export class SharedStateService {
  private state$ = new BehaviorSubject<any>({});
  
  setState(key: string, value: any): void {
    const currentState = this.state$.value;
    this.state$.next({ ...currentState, [key]: value });
  }
  
  getState(key: string): Observable<any> {
    return this.state$.pipe(
      map(state => state[key]),
      distinctUntilChanged()
    );
  }
}

// Module Federation Configuration
// webpack.config.js
const ModuleFederationPlugin = require('@module-federation/webpack');

module.exports = {
  mode: 'development',
  plugins: [
    new ModuleFederationPlugin({
      name: 'shell',
      remotes: {
        'user-mfe': 'userMfe@http://localhost:4201/remoteEntry.js',
        'product-mfe': 'productMfe@http://localhost:4202/remoteEntry.js'
      },
      shared: {
        '@angular/core': { singleton: true },
        '@angular/common': { singleton: true },
        '@angular/router': { singleton: true }
      }
    })
  ]
};

// Communication between Micro-frontends
@Injectable({
  providedIn: 'root'
})
export class MicroFrontendCommunication {
  private eventBus = new Subject<any>();
  
  emit(event: string, data: any): void {
    this.eventBus.next({ event, data });
  }
  
  listen(event: string): Observable<any> {
    return this.eventBus.pipe(
      filter(({ event: eventName }) => eventName === event),
      map(({ data }) => data)
    );
  }
}

// Shared Component Library
@Component({
  selector: 'lib-shared-button',
  template: `<button [class]="buttonClass" (click)="onClick.emit()">
    <ng-content></ng-content>
  </button>`
})
export class SharedButtonComponent {
  @Input() variant: 'primary' | 'secondary' = 'primary';
  @Input() size: 'small' | 'medium' | 'large' = 'medium';
  @Output() onClick = new EventEmitter<void>();
  
  get buttonClass(): string {
    return `btn btn-${this.variant} btn-${this.size}`;
  }
}
```

**Key Concepts:**
- Module Federation
- Micro-frontend architecture
- Shared state management
- Inter-micro-frontend communication
- Shared component libraries

#### 8. How do you implement advanced testing strategies in Angular?
**Answer:**
Comprehensive testing approaches for Angular applications:

```typescript
// Unit Testing with Jasmine and Karma
describe('UserService', () => {
  let service: UserService;
  let httpMock: HttpTestingController;
  
  beforeEach(() => {
    TestBed.configureTestingModule({
      imports: [HttpClientTestingModule],
      providers: [UserService]
    });
    service = TestBed.inject(UserService);
    httpMock = TestBed.inject(HttpTestingController);
  });
  
  afterEach(() => {
    httpMock.verify();
  });
  
  it('should fetch users', () => {
    const mockUsers: User[] = [
      { id: 1, name: 'John', email: 'john@example.com' }
    ];
    
    service.getUsers().subscribe(users => {
      expect(users).toEqual(mockUsers);
    });
    
    const req = httpMock.expectOne('/api/users');
    expect(req.request.method).toBe('GET');
    req.flush(mockUsers);
  });
  
  it('should handle errors', () => {
    service.getUsers().subscribe({
      next: () => fail('should have failed'),
      error: (error) => {
        expect(error).toBeTruthy();
      }
    });
    
    const req = httpMock.expectOne('/api/users');
    req.error(new ErrorEvent('Network error'));
  });
});

// Component Testing
describe('UserListComponent', () => {
  let component: UserListComponent;
  let fixture: ComponentFixture<UserListComponent>;
  let userService: jasmine.SpyObj<UserService>;
  
  beforeEach(async () => {
    const spy = jasmine.createSpyObj('UserService', ['getUsers']);
    
    await TestBed.configureTestingModule({
      declarations: [UserListComponent],
      providers: [
        { provide: UserService, useValue: spy }
      ]
    }).compileComponents();
    
    fixture = TestBed.createComponent(UserListComponent);
    component = fixture.componentInstance;
    userService = TestBed.inject(UserService) as jasmine.SpyObj<UserService>;
  });
  
  it('should display users', () => {
    const mockUsers: User[] = [
      { id: 1, name: 'John', email: 'john@example.com' }
    ];
    userService.getUsers.and.returnValue(of(mockUsers));
    
    fixture.detectChanges();
    
    const compiled = fixture.nativeElement;
    expect(compiled.querySelector('.user-name').textContent).toContain('John');
  });
  
  it('should handle user selection', () => {
    const mockUsers: User[] = [
      { id: 1, name: 'John', email: 'john@example.com' }
    ];
    userService.getUsers.and.returnValue(of(mockUsers));
    
    fixture.detectChanges();
    
    const userElement = fixture.debugElement.query(By.css('.user-item'));
    userElement.triggerEventHandler('click', null);
    
    expect(component.selectedUser).toEqual(mockUsers[0]);
  });
});

// Integration Testing
describe('User Management Integration', () => {
  let fixture: ComponentFixture<AppComponent>;
  let component: AppComponent;
  
  beforeEach(async () => {
    await TestBed.configureTestingModule({
      declarations: [AppComponent],
      imports: [RouterTestingModule, HttpClientTestingModule],
      providers: [UserService]
    }).compileComponents();
    
    fixture = TestBed.createComponent(AppComponent);
    component = fixture.componentInstance;
  });
  
  it('should navigate to user detail', fakeAsync(() => {
    const router = TestBed.inject(Router);
    spyOn(router, 'navigate');
    
    component.navigateToUser(1);
    tick();
    
    expect(router.navigate).toHaveBeenCalledWith(['/users', 1]);
  }));
});

// E2E Testing with Cypress
// cypress/integration/user-management.spec.ts
describe('User Management E2E', () => {
  beforeEach(() => {
    cy.visit('/users');
  });
  
  it('should display user list', () => {
    cy.get('[data-cy=user-list]').should('be.visible');
    cy.get('[data-cy=user-item]').should('have.length.greaterThan', 0);
  });
  
  it('should create new user', () => {
    cy.get('[data-cy=add-user-btn]').click();
    cy.get('[data-cy=user-form]').should('be.visible');
    
    cy.get('[data-cy=name-input]').type('Jane Doe');
    cy.get('[data-cy=email-input]').type('jane@example.com');
    cy.get('[data-cy=submit-btn]').click();
    
    cy.get('[data-cy=user-item]').should('contain', 'Jane Doe');
  });
  
  it('should edit user', () => {
    cy.get('[data-cy=user-item]').first().click();
    cy.get('[data-cy=edit-btn]').click();
    
    cy.get('[data-cy=name-input]').clear().type('Updated Name');
    cy.get('[data-cy=save-btn]').click();
    
    cy.get('[data-cy=user-item]').should('contain', 'Updated Name');
  });
});

// Performance Testing
describe('Performance Tests', () => {
  it('should render large user list efficiently', () => {
    const startTime = performance.now();
    
    const component = TestBed.createComponent(UserListComponent);
    component.componentInstance.users = generateLargeUserList(10000);
    component.detectChanges();
    
    const endTime = performance.now();
    const renderTime = endTime - startTime;
    
    expect(renderTime).toBeLessThan(1000); // Should render in less than 1 second
  });
  
  it('should handle memory leaks', () => {
    const component = TestBed.createComponent(UserListComponent);
    const initialMemory = (performance as any).memory?.usedJSHeapSize || 0;
    
    // Simulate component lifecycle
    for (let i = 0; i < 100; i++) {
      component.destroy();
      TestBed.createComponent(UserListComponent);
    }
    
    const finalMemory = (performance as any).memory?.usedJSHeapSize || 0;
    const memoryIncrease = finalMemory - initialMemory;
    
    expect(memoryIncrease).toBeLessThan(10000000); // Less than 10MB increase
  });
});
```

**Key Concepts:**
- Unit testing
- Component testing
- Integration testing
- E2E testing
- Performance testing
- Memory leak testing

#### 9. How do you implement advanced Angular patterns and best practices?
**Answer:**
Enterprise-level Angular patterns and architectural decisions:

```typescript
// Command Pattern for Undo/Redo
export interface Command {
  execute(): void;
  undo(): void;
}

export class AddUserCommand implements Command {
  constructor(
    private userService: UserService,
    private user: User
  ) {}
  
  execute(): void {
    this.userService.addUser(this.user);
  }
  
  undo(): void {
    this.userService.removeUser(this.user.id);
  }
}

@Injectable({
  providedIn: 'root'
})
export class CommandService {
  private history: Command[] = [];
  private currentIndex = -1;
  
  execute(command: Command): void {
    command.execute();
    this.history = this.history.slice(0, this.currentIndex + 1);
    this.history.push(command);
    this.currentIndex++;
  }
  
  undo(): void {
    if (this.canUndo()) {
      const command = this.history[this.currentIndex];
      command.undo();
      this.currentIndex--;
    }
  }
  
  redo(): void {
    if (this.canRedo()) {
      this.currentIndex++;
      const command = this.history[this.currentIndex];
      command.execute();
    }
  }
  
  canUndo(): boolean {
    return this.currentIndex >= 0;
  }
  
  canRedo(): boolean {
    return this.currentIndex < this.history.length - 1;
  }
}

// Observer Pattern for Event Handling
@Injectable({
  providedIn: 'root'
})
export class EventBus {
  private events$ = new Subject<Event>();
  
  emit(event: Event): void {
    this.events$.next(event);
  }
  
  on<T extends Event>(eventType: new (...args: any[]) => T): Observable<T> {
    return this.events$.pipe(
      filter(event => event instanceof eventType),
      map(event => event as T)
    );
  }
}

export class UserCreatedEvent {
  constructor(public user: User) {}
}

export class UserUpdatedEvent {
  constructor(public user: User) {}
}

// Repository Pattern
export interface UserRepository {
  findAll(): Observable<User[]>;
  findById(id: number): Observable<User>;
  save(user: User): Observable<User>;
  delete(id: number): Observable<void>;
}

@Injectable({
  providedIn: 'root'
})
export class UserRepositoryImpl implements UserRepository {
  constructor(private http: HttpClient) {}
  
  findAll(): Observable<User[]> {
    return this.http.get<User[]>('/api/users');
  }
  
  findById(id: number): Observable<User> {
    return this.http.get<User>(`/api/users/${id}`);
  }
  
  save(user: User): Observable<User> {
    if (user.id) {
      return this.http.put<User>(`/api/users/${user.id}`, user);
    } else {
      return this.http.post<User>('/api/users', user);
    }
  }
  
  delete(id: number): Observable<void> {
    return this.http.delete<void>(`/api/users/${id}`);
  }
}

// Factory Pattern for Component Creation
export interface ComponentFactory<T> {
  create(data: any): T;
}

@Injectable({
  providedIn: 'root'
})
export class UserComponentFactory implements ComponentFactory<UserComponent> {
  constructor(private componentFactoryResolver: ComponentFactoryResolver) {}
  
  create(user: User): UserComponent {
    const factory = this.componentFactoryResolver.resolveComponentFactory(UserComponent);
    const componentRef = factory.create(null);
    componentRef.instance.user = user;
    return componentRef.instance;
  }
}

// Strategy Pattern for Different User Types
export interface UserStrategy {
  process(user: User): Observable<User>;
}

@Injectable({
  providedIn: 'root'
})
export class AdminUserStrategy implements UserStrategy {
  process(user: User): Observable<User> {
    // Admin-specific processing
    return of({ ...user, role: 'admin' });
  }
}

@Injectable({
  providedIn: 'root'
})
export class RegularUserStrategy implements UserStrategy {
  process(user: User): Observable<User> {
    // Regular user processing
    return of({ ...user, role: 'user' });
  }
}

@Injectable({
  providedIn: 'root'
})
export class UserProcessingService {
  private strategies = new Map<string, UserStrategy>();
  
  constructor(
    private adminStrategy: AdminUserStrategy,
    private regularStrategy: RegularUserStrategy
  ) {
    this.strategies.set('admin', adminStrategy);
    this.strategies.set('regular', regularStrategy);
  }
  
  processUser(user: User, type: string): Observable<User> {
    const strategy = this.strategies.get(type);
    if (!strategy) {
      throw new Error(`No strategy found for type: ${type}`);
    }
    return strategy.process(user);
  }
}

// Decorator Pattern for Logging
export function LogMethod(target: any, propertyName: string, descriptor: PropertyDescriptor) {
  const method = descriptor.value;
  
  descriptor.value = function (...args: any[]) {
    console.log(`Calling ${propertyName} with args:`, args);
    const result = method.apply(this, args);
    console.log(`${propertyName} returned:`, result);
    return result;
  };
}

// Usage
export class UserService {
  @LogMethod
  getUser(id: number): Observable<User> {
    return this.http.get<User>(`/api/users/${id}`);
  }
}
```

**Key Concepts:**
- Design patterns
- Command pattern
- Observer pattern
- Repository pattern
- Factory pattern
- Strategy pattern
- Decorator pattern

### 🟣 Senior Level

#### 10. How do you design and implement scalable Angular architecture?
**Answer:**
Enterprise-level architecture design and implementation:

```typescript
// Domain-Driven Design Structure
// domain/entities/user.entity.ts
export class User {
  constructor(
    public readonly id: UserId,
    public readonly name: UserName,
    public readonly email: Email,
    public readonly role: UserRole
  ) {}
  
  changeName(newName: UserName): User {
    return new User(this.id, newName, this.email, this.role);
  }
  
  changeEmail(newEmail: Email): User {
    return new User(this.id, this.name, newEmail, this.role);
  }
}

// domain/value-objects/user-id.vo.ts
export class UserId {
  constructor(public readonly value: number) {
    if (value <= 0) {
      throw new Error('User ID must be positive');
    }
  }
  
  equals(other: UserId): boolean {
    return this.value === other.value;
  }
}

// domain/repositories/user.repository.ts
export interface UserRepository {
  findById(id: UserId): Promise<User>;
  save(user: User): Promise<void>;
  delete(id: UserId): Promise<void>;
}

// application/use-cases/create-user.use-case.ts
@Injectable()
export class CreateUserUseCase {
  constructor(
    private userRepository: UserRepository,
    private eventBus: EventBus
  ) {}
  
  async execute(command: CreateUserCommand): Promise<User> {
    const user = new User(
      new UserId(command.id),
      new UserName(command.name),
      new Email(command.email),
      new UserRole(command.role)
    );
    
    await this.userRepository.save(user);
    this.eventBus.emit(new UserCreatedEvent(user));
    
    return user;
  }
}

// infrastructure/persistence/user.repository.impl.ts
@Injectable()
export class UserRepositoryImpl implements UserRepository {
  constructor(private http: HttpClient) {}
  
  async findById(id: UserId): Promise<User> {
    const response = await this.http.get<any>(`/api/users/${id.value}`).toPromise();
    return this.mapToDomain(response);
  }
  
  async save(user: User): Promise<void> {
    const dto = this.mapToDto(user);
    await this.http.post('/api/users', dto).toPromise();
  }
  
  private mapToDomain(dto: any): User {
    return new User(
      new UserId(dto.id),
      new UserName(dto.name),
      new Email(dto.email),
      new UserRole(dto.role)
    );
  }
  
  private mapToDto(user: User): any {
    return {
      id: user.id.value,
      name: user.name.value,
      email: user.email.value,
      role: user.role.value
    };
  }
}

// CQRS Implementation
// commands/create-user.command.ts
export class CreateUserCommand {
  constructor(
    public readonly id: number,
    public readonly name: string,
    public readonly email: string,
    public readonly role: string
  ) {}
}

// commands/handlers/create-user.handler.ts
@Injectable()
export class CreateUserHandler {
  constructor(
    private userRepository: UserRepository,
    private eventBus: EventBus
  ) {}
  
  async handle(command: CreateUserCommand): Promise<void> {
    const user = new User(
      new UserId(command.id),
      new UserName(command.name),
      new Email(command.email),
      new UserRole(command.role)
    );
    
    await this.userRepository.save(user);
    this.eventBus.emit(new UserCreatedEvent(user));
  }
}

// queries/get-user.query.ts
export class GetUserQuery {
  constructor(public readonly id: number) {}
}

// queries/handlers/get-user.handler.ts
@Injectable()
export class GetUserHandler {
  constructor(private userRepository: UserRepository) {}
  
  async handle(query: GetUserQuery): Promise<User> {
    return await this.userRepository.findById(new UserId(query.id));
  }
}

// Event Sourcing
// events/user-created.event.ts
export class UserCreatedEvent {
  constructor(
    public readonly aggregateId: UserId,
    public readonly eventId: string,
    public readonly occurredOn: Date,
    public readonly user: User
  ) {}
}

// event-store/event.store.ts
@Injectable()
export class EventStore {
  private events: Event[] = [];
  
  append(event: Event): void {
    this.events.push(event);
  }
  
  getEvents(aggregateId: string): Event[] {
    return this.events.filter(e => e.aggregateId === aggregateId);
  }
}

// Microservices Communication
// services/user.service.ts
@Injectable({
  providedIn: 'root'
})
export class UserService {
  constructor(
    private http: HttpClient,
    private config: AppConfig
  ) {}
  
  getUsers(): Observable<User[]> {
    return this.http.get<User[]>(`${this.config.apiUrl}/users`);
  }
  
  getUser(id: number): Observable<User> {
    return this.http.get<User>(`${this.config.apiUrl}/users/${id}`);
  }
}

// Circuit Breaker Pattern
@Injectable({
  providedIn: 'root'
})
export class CircuitBreakerService {
  private failures = 0;
  private lastFailureTime = 0;
  private state: 'CLOSED' | 'OPEN' | 'HALF_OPEN' = 'CLOSED';
  
  constructor(private config: { threshold: number; timeout: number }) {}
  
  async execute<T>(operation: () => Promise<T>): Promise<T> {
    if (this.state === 'OPEN') {
      if (Date.now() - this.lastFailureTime > this.config.timeout) {
        this.state = 'HALF_OPEN';
      } else {
        throw new Error('Circuit breaker is OPEN');
      }
    }
    
    try {
      const result = await operation();
      this.onSuccess();
      return result;
    } catch (error) {
      this.onFailure();
      throw error;
    }
  }
  
  private onSuccess(): void {
    this.failures = 0;
    this.state = 'CLOSED';
  }
  
  private onFailure(): void {
    this.failures++;
    this.lastFailureTime = Date.now();
    
    if (this.failures >= this.config.threshold) {
      this.state = 'OPEN';
    }
  }
}
```

**Key Concepts:**
- Domain-Driven Design
- CQRS (Command Query Responsibility Segregation)
- Event Sourcing
- Microservices architecture
- Circuit Breaker pattern
- Clean Architecture
- SOLID principles

## 🎯 Practice Exercises

### Intermediate
1. Build a user management system with CRUD operations
2. Implement a shopping cart with state management
3. Create a dashboard with real-time data updates

### Advanced
1. Design a micro-frontend architecture
2. Implement a complex form with validation
3. Build a real-time chat application

### Expert
1. Create a scalable enterprise application
2. Implement advanced testing strategies
3. Design a performance-optimized application

### Senior
1. Architect a multi-tenant SaaS application
2. Design a microservices communication layer
3. Implement advanced security patterns

## 📚 Additional Resources

- [Angular Documentation](https://angular.io/docs)
- [Angular Style Guide](https://angular.io/guide/styleguide)
- [NgRx Documentation](https://ngrx.io/)
- [Angular Testing Guide](https://angular.io/guide/testing)
- [Angular Performance Guide](https://angular.io/guide/performance-checklist)
