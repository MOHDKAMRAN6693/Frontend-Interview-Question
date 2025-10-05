# HTML Interview Questions

## 🎯 Difficulty Levels
- **🟢 Beginner**: Basic HTML structure and elements
- **🟡 Intermediate**: Semantic HTML and accessibility
- **🔴 Advanced**: HTML5 features and optimization
- **🟣 Expert**: Performance and best practices

## 📋 Questions

### 🟢 Beginner Level

#### 1. What is HTML and what does it stand for?
**Answer:**
HTML stands for HyperText Markup Language. It's the standard markup language used to create web pages and web applications. HTML describes the structure of a web page semantically and originally included cues for the appearance of the document.

**Key Concepts:**
- Markup language
- Web page structure
- Semantic meaning

#### 2. What are HTML tags and attributes?
**Answer:**
HTML tags are the building blocks of HTML. They define the structure and content of web pages. Attributes provide additional information about HTML elements.

```html
<!-- Example of tag with attributes -->
<img src="image.jpg" alt="Description" width="300" height="200">
```

**Key Concepts:**
- Opening and closing tags
- Self-closing tags
- Attribute values

#### 3. What is the difference between `<div>` and `<span>`?
**Answer:**
- `<div>` is a block-level element that takes up the full width available
- `<span>` is an inline element that only takes up as much width as necessary

```html
<div>This is a block element</div>
<span>This is an inline element</span>
```

**Key Concepts:**
- Block vs inline elements
- Box model
- Layout behavior

#### 4. What are the basic HTML document structure elements?
**Answer:**
Every HTML document should have a basic structure:

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Document Title</title>
</head>
<body>
    <!-- Content goes here -->
</body>
</html>
```

**Key Concepts:**
- DOCTYPE declaration
- HTML document structure
- Meta tags
- Viewport meta tag

#### 5. How do you create links in HTML?
**Answer:**
Links are created using the `<a>` tag with the `href` attribute:

```html
<!-- External link -->
<a href="https://www.example.com">Visit Example</a>

<!-- Internal link -->
<a href="#section1">Go to Section 1</a>

<!-- Email link -->
<a href="mailto:contact@example.com">Send Email</a>

<!-- Phone link -->
<a href="tel:+1234567890">Call Us</a>

<!-- Link with target -->
<a href="https://www.example.com" target="_blank" rel="noopener">Open in New Tab</a>
```

**Key Concepts:**
- href attribute
- target attribute
- rel attribute
- Link types

#### 6. What are HTML headings and how do you use them?
**Answer:**
HTML headings are used to define the structure and hierarchy of content:

```html
<h1>Main Heading</h1>
<h2>Section Heading</h2>
<h3>Subsection Heading</h3>
<h4>Minor Heading</h4>
<h5>Small Heading</h5>
<h6>Smallest Heading</h6>
```

**Key Concepts:**
- Heading hierarchy
- SEO importance
- Accessibility
- Content structure

#### 7. How do you add images to HTML?
**Answer:**
Images are added using the `<img>` tag:

```html
<!-- Basic image -->
<img src="image.jpg" alt="Description of image">

<!-- Image with dimensions -->
<img src="image.jpg" alt="Description" width="300" height="200">

<!-- Responsive image -->
<img src="image.jpg" alt="Description" style="max-width: 100%; height: auto;">

<!-- Image with title -->
<img src="image.jpg" alt="Description" title="Image title">
```

**Key Concepts:**
- src attribute
- alt attribute
- Responsive images
- Accessibility

#### 8. What are HTML lists and how do you create them?
**Answer:**
HTML provides three types of lists:

```html
<!-- Unordered list -->
<ul>
  <li>Item 1</li>
  <li>Item 2</li>
  <li>Item 3</li>
</ul>

<!-- Ordered list -->
<ol>
  <li>First item</li>
  <li>Second item</li>
  <li>Third item</li>
</ol>

<!-- Description list -->
<dl>
  <dt>Term 1</dt>
  <dd>Definition 1</dd>
  <dt>Term 2</dt>
  <dd>Definition 2</dd>
</dl>
```

**Key Concepts:**
- List types
- Nested lists
- Accessibility
- Semantic meaning

#### 9. How do you create HTML tables?
**Answer:**
Tables are used to display tabular data:

```html
<table>
  <thead>
    <tr>
      <th>Name</th>
      <th>Age</th>
      <th>City</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>John</td>
      <td>25</td>
      <td>New York</td>
    </tr>
    <tr>
      <td>Jane</td>
      <td>30</td>
      <td>London</td>
    </tr>
  </tbody>
  <tfoot>
    <tr>
      <td colspan="3">Total: 2 people</td>
    </tr>
  </tfoot>
</table>
```

**Key Concepts:**
- Table structure
- thead, tbody, tfoot
- colspan and rowspan
- Accessibility

#### 10. What are HTML forms and how do you create them?
**Answer:**
Forms are used to collect user input:

```html
<form action="/submit" method="POST">
  <label for="name">Name:</label>
  <input type="text" id="name" name="name" required>
  
  <label for="email">Email:</label>
  <input type="email" id="email" name="email" required>
  
  <label for="message">Message:</label>
  <textarea id="message" name="message" rows="4"></textarea>
  
  <button type="submit">Submit</button>
</form>
```

**Key Concepts:**
- Form elements
- Input types
- Validation
- Accessibility

### 🟡 Intermediate Level

#### 11. What are semantic HTML elements and why are they important?
**Answer:**
Semantic HTML elements clearly describe their meaning in a human- and machine-readable way. They improve accessibility, SEO, and code maintainability.

```html
<header>
  <nav>
    <ul>
      <li><a href="#home">Home</a></li>
      <li><a href="#about">About</a></li>
    </ul>
  </nav>
</header>

<main>
  <article>
    <h1>Article Title</h1>
    <p>Article content...</p>
  </article>
</main>

<footer>
  <p>&copy; 2024 Company Name</p>
</footer>
```

**Key Concepts:**
- Semantic meaning
- Accessibility
- SEO benefits
- Screen readers

#### 12. What is the difference between `<ul>` and `<ol>`?
**Answer:**
- `<ul>` creates an unordered list (bullet points)
- `<ol>` creates an ordered list (numbered)

```html
<!-- Unordered list -->
<ul>
  <li>Item 1</li>
  <li>Item 2</li>
</ul>

<!-- Ordered list -->
<ol>
  <li>First item</li>
  <li>Second item</li>
</ol>
```

**Key Concepts:**
- List types
- Accessibility
- Styling considerations

#### 13. How do you create advanced forms in HTML?
**Answer:**
Advanced forms include various input types and validation:

```html
<form action="/submit" method="POST" novalidate>
  <fieldset>
    <legend>Personal Information</legend>
    
    <label for="name">Full Name:</label>
    <input type="text" id="name" name="name" required minlength="2" maxlength="50">
    
    <label for="email">Email:</label>
    <input type="email" id="email" name="email" required>
    
    <label for="age">Age:</label>
    <input type="number" id="age" name="age" min="18" max="100">
    
    <label for="birthdate">Birth Date:</label>
    <input type="date" id="birthdate" name="birthdate">
    
    <label for="website">Website:</label>
    <input type="url" id="website" name="website">
    
    <label for="phone">Phone:</label>
    <input type="tel" id="phone" name="phone" pattern="[0-9]{3}-[0-9]{3}-[0-9]{4}">
    
    <label for="password">Password:</label>
    <input type="password" id="password" name="password" minlength="8" required>
    
    <label for="color">Favorite Color:</label>
    <input type="color" id="color" name="color">
    
    <label for="range">Rating:</label>
    <input type="range" id="range" name="range" min="1" max="10" value="5">
    
    <button type="submit">Submit</button>
  </fieldset>
</form>
```

**Key Concepts:**
- Advanced input types
- Form validation
- Fieldset and legend
- Accessibility

#### 14. What are HTML5 semantic elements?
**Answer:**
HTML5 introduced new semantic elements for better document structure:

```html
<article>
  <header>
    <h1>Article Title</h1>
    <time datetime="2024-01-15">January 15, 2024</time>
  </header>
  
  <section>
    <h2>Introduction</h2>
    <p>Article content...</p>
  </section>
  
  <aside>
    <h3>Related Articles</h3>
    <ul>
      <li><a href="#">Related Article 1</a></li>
      <li><a href="#">Related Article 2</a></li>
    </ul>
  </aside>
  
  <footer>
    <p>Author: John Doe</p>
  </footer>
</article>
```

**Key Concepts:**
- HTML5 semantic elements
- Document structure
- SEO optimization
- Accessibility improvements

#### 15. How do you create accessible HTML?
**Answer:**
Accessible HTML follows WCAG guidelines:

```html
<!-- Proper heading hierarchy -->
<h1>Main Title</h1>
  <h2>Section Title</h2>
    <h3>Subsection Title</h3>

<!-- Form with proper labels -->
<label for="username">Username:</label>
<input type="text" id="username" name="username" required 
       aria-describedby="username-help">
<div id="username-help">Enter your username</div>

<!-- Table with proper headers -->
<table>
  <caption>Monthly Sales Report</caption>
  <thead>
    <tr>
      <th scope="col">Month</th>
      <th scope="col">Sales</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th scope="row">January</th>
      <td>$1000</td>
    </tr>
  </tbody>
</table>

<!-- Skip links for navigation -->
<a href="#main-content" class="skip-link">Skip to main content</a>

<!-- ARIA attributes -->
<button aria-expanded="false" aria-controls="menu">
  Menu
</button>
<div id="menu" aria-hidden="true">
  <ul>
    <li><a href="#">Home</a></li>
    <li><a href="#">About</a></li>
  </ul>
</div>
```

**Key Concepts:**
- WCAG guidelines
- ARIA attributes
- Semantic HTML
- Screen reader support

#### 16. What are HTML5 input types and their uses?
**Answer:**
HTML5 introduced many new input types for better user experience:

```html
<!-- Text inputs -->
<input type="text" placeholder="Text input">
<input type="email" placeholder="Email input">
<input type="url" placeholder="URL input">
<input type="tel" placeholder="Phone input">
<input type="search" placeholder="Search input">

<!-- Number inputs -->
<input type="number" min="0" max="100" step="1">
<input type="range" min="0" max="100" value="50">

<!-- Date and time inputs -->
<input type="date">
<input type="time">
<input type="datetime-local">
<input type="month">
<input type="week">

<!-- Color input -->
<input type="color" value="#ff0000">

<!-- File input -->
<input type="file" accept="image/*">
<input type="file" accept=".pdf,.doc,.docx">

<!-- Other inputs -->
<input type="password" placeholder="Password">
<input type="hidden" name="token" value="abc123">
```

**Key Concepts:**
- Input types
- Validation
- User experience
- Browser support

#### 17. How do you create responsive HTML?
**Answer:**
Responsive HTML uses flexible layouts and media queries:

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Responsive Page</title>
    <style>
        .container {
            max-width: 1200px;
            margin: 0 auto;
            padding: 0 20px;
        }
        
        .grid {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(300px, 1fr));
            gap: 20px;
        }
        
        @media (max-width: 768px) {
            .grid {
                grid-template-columns: 1fr;
            }
        }
    </style>
</head>
<body>
    <div class="container">
        <header>
            <h1>Responsive Website</h1>
            <nav>
                <ul>
                    <li><a href="#">Home</a></li>
                    <li><a href="#">About</a></li>
                    <li><a href="#">Contact</a></li>
                </ul>
            </nav>
        </header>
        
        <main>
            <div class="grid">
                <article>
                    <h2>Article 1</h2>
                    <p>Content here...</p>
                </article>
                <article>
                    <h2>Article 2</h2>
                    <p>Content here...</p>
                </article>
            </div>
        </main>
    </div>
</body>
</html>
```

**Key Concepts:**
- Responsive design
- Viewport meta tag
- Flexible layouts
- Media queries

#### 18. What are HTML5 multimedia elements?
**Answer:**
HTML5 provides native support for audio and video:

```html
<!-- Video element -->
<video width="320" height="240" controls>
    <source src="movie.mp4" type="video/mp4">
    <source src="movie.ogg" type="video/ogg">
    Your browser does not support the video tag.
</video>

<!-- Audio element -->
<audio controls>
    <source src="audio.mp3" type="audio/mpeg">
    <source src="audio.ogg" type="audio/ogg">
    Your browser does not support the audio tag.
</audio>

<!-- Canvas element -->
<canvas id="myCanvas" width="200" height="100"></canvas>
<script>
    const canvas = document.getElementById('myCanvas');
    const ctx = canvas.getContext('2d');
    ctx.fillStyle = 'red';
    ctx.fillRect(10, 10, 50, 50);
</script>

<!-- SVG element -->
<svg width="100" height="100">
    <circle cx="50" cy="50" r="40" stroke="black" stroke-width="3" fill="red" />
</svg>
```

**Key Concepts:**
- Multimedia support
- Canvas API
- SVG graphics
- Browser compatibility

#### 19. How do you create HTML5 drag and drop?
**Answer:**
HTML5 provides native drag and drop functionality:

```html
<div id="drop-zone" ondrop="drop(event)" ondragover="allowDrop(event)">
    <p>Drop files here</p>
</div>

<div id="drag-item" draggable="true" ondragstart="drag(event)">
    <p>Drag me</p>
</div>

<script>
function allowDrop(ev) {
    ev.preventDefault();
}

function drag(ev) {
    ev.dataTransfer.setData("text", ev.target.id);
}

function drop(ev) {
    ev.preventDefault();
    const data = ev.dataTransfer.getData("text");
    ev.target.appendChild(document.getElementById(data));
}
</script>
```

**Key Concepts:**
- Drag and drop API
- Event handling
- Data transfer
- User interaction

#### 20. What are HTML5 storage options?
**Answer:**
HTML5 provides several storage options:

```html
<!-- Local Storage -->
<script>
// Store data
localStorage.setItem('username', 'john');
localStorage.setItem('theme', 'dark');

// Retrieve data
const username = localStorage.getItem('username');
const theme = localStorage.getItem('theme');

// Remove data
localStorage.removeItem('username');

// Clear all data
localStorage.clear();
</script>

<!-- Session Storage -->
<script>
// Store data for session only
sessionStorage.setItem('tempData', 'temporary');
const tempData = sessionStorage.getItem('tempData');
</script>

<!-- IndexedDB (Advanced) -->
<script>
const request = indexedDB.open('MyDB', 1);

request.onupgradeneeded = function(event) {
    const db = event.target.result;
    const objectStore = db.createObjectStore('users', { keyPath: 'id' });
    objectStore.createIndex('name', 'name', { unique: false });
};
</script>
```

**Key Concepts:**
- Local storage
- Session storage
- IndexedDB
- Data persistence

### 🔴 Advanced Level

#### 21. What is the difference between `<script>`, `<script async>`, and `<script defer>`?
**Answer:**
- `<script>`: Blocks HTML parsing until script is downloaded and executed
- `<script async>`: Downloads script in parallel with HTML parsing, executes immediately when ready
- `<script defer>`: Downloads script in parallel with HTML parsing, executes after HTML parsing is complete

```html
<!-- Blocking -->
<script src="script.js"></script>

<!-- Non-blocking, executes when ready -->
<script async src="script.js"></script>

<!-- Non-blocking, executes after HTML parsing -->
<script defer src="script.js"></script>
```

**Key Concepts:**
- Script loading strategies
- Performance optimization
- DOM readiness
- Execution order

#### 22. How do you implement responsive images in HTML?
**Answer:**
Use the `<picture>` element with `<source>` elements for responsive images:

```html
<picture>
    <source media="(min-width: 800px)" srcset="large-image.jpg">
    <source media="(min-width: 400px)" srcset="medium-image.jpg">
    <img src="small-image.jpg" alt="Responsive image" style="width: 100%;">
</picture>

<!-- Alternative with srcset -->
<img src="image.jpg" 
     srcset="image-320w.jpg 320w,
             image-640w.jpg 640w,
             image-1280w.jpg 1280w"
     sizes="(max-width: 320px) 280px,
            (max-width: 640px) 600px,
            1200px"
     alt="Responsive image">
```

**Key Concepts:**
- Responsive design
- Image optimization
- Performance
- Art direction

#### 23. What are HTML5 form validation features?
**Answer:**
HTML5 provides built-in form validation:

```html
<form>
  <input type="email" required placeholder="Enter email">
  <input type="url" placeholder="Enter website URL">
  <input type="number" min="1" max="100" step="1">
  <input type="date" min="2024-01-01" max="2024-12-31">
  <input type="tel" pattern="[0-9]{3}-[0-9]{3}-[0-9]{4}">
  <input type="password" minlength="8" required>
  <input type="text" pattern="[A-Za-z]+" title="Only letters allowed">
  
  <button type="submit">Submit</button>
</form>
```

**Key Concepts:**
- Input types
- Validation attributes
- Pattern matching
- User experience

#### 24. How do you implement HTML5 geolocation?
**Answer:**
HTML5 provides geolocation API for location-based features:

```html
<button onclick="getLocation()">Get My Location</button>
<p id="location"></p>

<script>
function getLocation() {
    if (navigator.geolocation) {
        navigator.geolocation.getCurrentPosition(showPosition, showError);
    } else {
        document.getElementById("location").innerHTML = "Geolocation is not supported by this browser.";
    }
}

function showPosition(position) {
    const lat = position.coords.latitude;
    const lon = position.coords.longitude;
    document.getElementById("location").innerHTML = 
        "Latitude: " + lat + "<br>Longitude: " + lon;
}

function showError(error) {
    switch(error.code) {
        case error.PERMISSION_DENIED:
            document.getElementById("location").innerHTML = "User denied the request for Geolocation.";
            break;
        case error.POSITION_UNAVAILABLE:
            document.getElementById("location").innerHTML = "Location information is unavailable.";
            break;
        case error.TIMEOUT:
            document.getElementById("location").innerHTML = "The request to get user location timed out.";
            break;
        default:
            document.getElementById("location").innerHTML = "An unknown error occurred.";
            break;
    }
}
</script>
```

**Key Concepts:**
- Geolocation API
- User permissions
- Error handling
- Location services

#### 25. How do you create HTML5 Web Workers?
**Answer:**
Web Workers allow running JavaScript in background threads:

```html
<!-- main.html -->
<button onclick="startWorker()">Start Worker</button>
<button onclick="stopWorker()">Stop Worker</button>
<p id="result"></p>

<script>
let worker;

function startWorker() {
    if (typeof(Worker) !== "undefined") {
        worker = new Worker("worker.js");
        worker.onmessage = function(event) {
            document.getElementById("result").innerHTML = event.data;
        };
    } else {
        document.getElementById("result").innerHTML = "Web Workers not supported.";
    }
}

function stopWorker() {
    worker.terminate();
    worker = undefined;
}
</script>

<!-- worker.js -->
let i = 0;

function timedCount() {
    i = i + 1;
    postMessage(i);
    setTimeout("timedCount()", 500);
}

timedCount();
```

**Key Concepts:**
- Background processing
- Threading
- Message passing
- Performance optimization

#### 26. How do you implement HTML5 WebSockets?
**Answer:**
WebSockets provide real-time communication:

```html
<div id="messages"></div>
<input type="text" id="messageInput" placeholder="Type a message">
<button onclick="sendMessage()">Send</button>

<script>
const socket = new WebSocket('ws://localhost:8080');

socket.onopen = function(event) {
    console.log('Connection opened');
};

socket.onmessage = function(event) {
    const messages = document.getElementById('messages');
    messages.innerHTML += '<div>' + event.data + '</div>';
};

socket.onclose = function(event) {
    console.log('Connection closed');
};

socket.onerror = function(error) {
    console.log('Error: ' + error);
};

function sendMessage() {
    const input = document.getElementById('messageInput');
    socket.send(input.value);
    input.value = '';
}
</script>
```

**Key Concepts:**
- Real-time communication
- WebSocket API
- Event handling
- Server communication

#### 27. How do you create HTML5 offline applications?
**Answer:**
HTML5 provides offline capabilities through Application Cache and Service Workers:

```html
<!DOCTYPE html>
<html manifest="app.manifest">
<head>
    <title>Offline App</title>
</head>
<body>
    <h1>Offline Application</h1>
    <p>This app works offline!</p>
    
    <script>
        // Service Worker Registration
        if ('serviceWorker' in navigator) {
            navigator.serviceWorker.register('/sw.js')
                .then(registration => console.log('SW registered'))
                .catch(error => console.log('SW registration failed'));
        }
        
        // Application Cache Events
        window.applicationCache.addEventListener('updateready', function() {
            if (window.applicationCache.status === window.applicationCache.UPDATEREADY) {
                window.applicationCache.swapCache();
                window.location.reload();
            }
        });
    </script>
</body>
</html>

<!-- app.manifest -->
CACHE MANIFEST
# Version 1.0
CACHE:
index.html
style.css
script.js
image.jpg

NETWORK:
*

FALLBACK:
/ offline.html
```

**Key Concepts:**
- Offline functionality
- Application Cache
- Service Workers
- Caching strategies

#### 28. How do you implement HTML5 File API?
**Answer:**
HTML5 File API allows reading and manipulating files:

```html
<input type="file" id="fileInput" multiple>
<div id="fileInfo"></div>

<script>
document.getElementById('fileInput').addEventListener('change', function(e) {
    const files = e.target.files;
    const fileInfo = document.getElementById('fileInfo');
    
    for (let i = 0; i < files.length; i++) {
        const file = files[i];
        
        // File information
        fileInfo.innerHTML += `
            <p>Name: ${file.name}</p>
            <p>Size: ${file.size} bytes</p>
            <p>Type: ${file.type}</p>
            <p>Last Modified: ${file.lastModifiedDate}</p>
        `;
        
        // Read file content
        const reader = new FileReader();
        reader.onload = function(e) {
            console.log('File content:', e.target.result);
        };
        reader.readAsText(file);
    }
});
</script>
```

**Key Concepts:**
- File reading
- File manipulation
- File types
- User interaction

#### 29. How do you create HTML5 Web Components?
**Answer:**
Web Components allow creating reusable custom elements:

```html
<!-- Define custom element -->
<script>
class MyComponent extends HTMLElement {
    constructor() {
        super();
        this.attachShadow({ mode: 'open' });
    }
    
    connectedCallback() {
        this.render();
    }
    
    render() {
        this.shadowRoot.innerHTML = `
            <style>
                :host {
                    display: block;
                    padding: 20px;
                    border: 1px solid #ccc;
                }
                .title {
                    font-size: 24px;
                    color: #333;
                }
            </style>
            <div class="title">${this.getAttribute('title') || 'Default Title'}</div>
            <slot></slot>
        `;
    }
}

customElements.define('my-component', MyComponent);
</script>

<!-- Use custom element -->
<my-component title="Custom Component">
    <p>This is the content inside the custom component.</p>
</my-component>
```

**Key Concepts:**
- Custom elements
- Shadow DOM
- Component lifecycle
- Reusability

#### 30. How do you implement HTML5 Intersection Observer?
**Answer:**
Intersection Observer API provides efficient way to observe element visibility:

```html
<div class="container">
    <div class="item">Item 1</div>
    <div class="item">Item 2</div>
    <div class="item">Item 3</div>
    <div class="item">Item 4</div>
    <div class="item">Item 5</div>
</div>

<script>
const observer = new IntersectionObserver((entries) => {
    entries.forEach(entry => {
        if (entry.isIntersecting) {
            entry.target.style.opacity = '1';
            entry.target.style.transform = 'translateY(0)';
        } else {
            entry.target.style.opacity = '0.5';
            entry.target.style.transform = 'translateY(20px)';
        }
    });
}, {
    threshold: 0.1,
    rootMargin: '0px 0px -50px 0px'
});

document.querySelectorAll('.item').forEach(item => {
    observer.observe(item);
});
</script>
```

**Key Concepts:**
- Element visibility
- Performance optimization
- Lazy loading
- Animation triggers

### 🟣 Expert Level

#### 31. How do you optimize HTML for performance and SEO?
**Answer:**
Performance and SEO optimization techniques:

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <!-- Critical meta tags -->
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <meta name="description" content="Page description for SEO">
    <meta name="keywords" content="relevant, keywords, for, seo">
    
    <!-- Preconnect to external domains -->
    <link rel="preconnect" href="https://fonts.googleapis.com">
    <link rel="preconnect" href="https://cdn.example.com">
    
    <!-- Preload critical resources -->
    <link rel="preload" href="critical.css" as="style">
    <link rel="preload" href="hero-image.jpg" as="image">
    
    <!-- Critical CSS inline -->
    <style>
        /* Critical above-the-fold CSS */
        body { margin: 0; font-family: Arial, sans-serif; }
    </style>
    
    <!-- Non-critical CSS -->
    <link rel="stylesheet" href="styles.css" media="print" onload="this.media='all'">
    
    <!-- Structured data for SEO -->
    <script type="application/ld+json">
    {
        "@context": "https://schema.org",
        "@type": "WebPage",
        "name": "Page Title",
        "description": "Page description"
    }
    </script>
</head>
<body>
    <!-- Content with proper semantic structure -->
    <header>
        <nav aria-label="Main navigation">
            <ul>
                <li><a href="/" aria-current="page">Home</a></li>
                <li><a href="/about">About</a></li>
            </ul>
        </nav>
    </header>
    
    <main>
        <h1>Main Heading</h1>
        <section>
            <h2>Section Heading</h2>
            <p>Content with proper heading hierarchy...</p>
        </section>
    </main>
    
    <!-- Lazy load non-critical scripts -->
    <script defer src="analytics.js"></script>
</body>
</html>
```

**Key Concepts:**
- Performance optimization
- SEO best practices
- Resource loading strategies
- Accessibility compliance

#### 16. How do you implement progressive web app features in HTML?
**Answer:**
PWA features implementation:

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>PWA App</title>
    
    <!-- PWA Meta Tags -->
    <meta name="theme-color" content="#000000">
    <meta name="apple-mobile-web-app-capable" content="yes">
    <meta name="apple-mobile-web-app-status-bar-style" content="black">
    <meta name="apple-mobile-web-app-title" content="PWA App">
    
    <!-- Manifest -->
    <link rel="manifest" href="manifest.json">
    
    <!-- Icons -->
    <link rel="icon" type="image/png" sizes="32x32" href="icon-32x32.png">
    <link rel="icon" type="image/png" sizes="16x16" href="icon-16x16.png">
    <link rel="apple-touch-icon" href="apple-touch-icon.png">
    
    <!-- Service Worker Registration -->
    <script>
        if ('serviceWorker' in navigator) {
            window.addEventListener('load', () => {
                navigator.serviceWorker.register('/sw.js')
                    .then(registration => console.log('SW registered'))
                    .catch(error => console.log('SW registration failed'));
            });
        }
    </script>
</head>
<body>
    <div id="app">
        <h1>Progressive Web App</h1>
        <p>This app works offline!</p>
    </div>
</body>
</html>
```

**Key Concepts:**
- Progressive Web Apps
- Service Workers
- Offline functionality
- App-like experience

#### 32. How do you implement advanced form validation and accessibility?
**Answer:**
Advanced form implementation:

```html
<form novalidate id="advanced-form" aria-labelledby="form-title">
    <h2 id="form-title">Advanced Form</h2>
    
    <!-- Name field with validation -->
    <div class="field-group">
        <label for="fullname">Full Name *</label>
        <input type="text" 
               id="fullname" 
               name="fullname" 
               required 
               minlength="2" 
               maxlength="50"
               pattern="[A-Za-z\s]+"
               aria-describedby="name-error name-help"
               autocomplete="name">
        <div id="name-error" class="error" role="alert" aria-live="polite"></div>
        <div id="name-help" class="help-text">Enter your full name (2-50 characters)</div>
    </div>
    
    <!-- Email field with custom validation -->
    <div class="field-group">
        <label for="email">Email Address *</label>
        <input type="email" 
               id="email" 
               name="email" 
               required 
               aria-describedby="email-error email-help"
               autocomplete="email">
        <div id="email-error" class="error" role="alert" aria-live="polite"></div>
        <div id="email-help" class="help-text">We'll never share your email</div>
    </div>
    
    <!-- Password with strength indicator -->
    <div class="field-group">
        <label for="password">Password *</label>
        <input type="password" 
               id="password" 
               name="password" 
               required 
               minlength="8"
               aria-describedby="password-error password-strength password-help"
               autocomplete="new-password">
        <div id="password-error" class="error" role="alert" aria-live="polite"></div>
        <div id="password-strength" class="strength-meter" aria-live="polite"></div>
        <div id="password-help" class="help-text">Minimum 8 characters with letters and numbers</div>
    </div>
    
    <!-- File upload with validation -->
    <div class="field-group">
        <label for="avatar">Profile Picture</label>
        <input type="file" 
               id="avatar" 
               name="avatar" 
               accept="image/*"
               aria-describedby="avatar-error avatar-help">
        <div id="avatar-error" class="error" role="alert" aria-live="polite"></div>
        <div id="avatar-help" class="help-text">JPG, PNG, or GIF (max 5MB)</div>
    </div>
    
    <!-- Checkbox with proper labeling -->
    <div class="field-group">
        <label>
            <input type="checkbox" 
                   id="terms" 
                   name="terms" 
                   required 
                   aria-describedby="terms-error">
            I agree to the <a href="/terms" target="_blank">Terms of Service</a> *
        </label>
        <div id="terms-error" class="error" role="alert" aria-live="polite"></div>
    </div>
    
    <!-- Submit button -->
    <button type="submit" id="submit-btn" aria-describedby="submit-status">
        Create Account
    </button>
    <div id="submit-status" class="status" aria-live="polite"></div>
</form>
```

**Key Concepts:**
- Advanced form validation
- Accessibility compliance
- ARIA attributes
- User experience
- Error handling

#### 33. How do you implement HTML5 Microdata and Schema.org?
**Answer:**
Microdata provides structured data for search engines:

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>Product Page</title>
</head>
<body>
    <!-- Product with Microdata -->
    <div itemscope itemtype="https://schema.org/Product">
        <h1 itemprop="name">iPhone 15 Pro</h1>
        <img itemprop="image" src="iphone15pro.jpg" alt="iPhone 15 Pro">
        <p itemprop="description">Latest iPhone with advanced features</p>
        <div itemprop="offers" itemscope itemtype="https://schema.org/Offer">
            <span itemprop="price" content="999.00">$999.00</span>
            <span itemprop="priceCurrency" content="USD">USD</span>
            <link itemprop="availability" href="https://schema.org/InStock">
        </div>
        <div itemprop="brand" itemscope itemtype="https://schema.org/Brand">
            <span itemprop="name">Apple</span>
        </div>
    </div>
    
    <!-- Organization with Microdata -->
    <div itemscope itemtype="https://schema.org/Organization">
        <h2 itemprop="name">Tech Company</h2>
        <p itemprop="description">Leading technology company</p>
        <div itemprop="address" itemscope itemtype="https://schema.org/PostalAddress">
            <span itemprop="streetAddress">123 Tech Street</span>
            <span itemprop="addressLocality">San Francisco</span>
            <span itemprop="addressRegion">CA</span>
            <span itemprop="postalCode">94105</span>
        </div>
        <span itemprop="telephone">+1-555-123-4567</span>
        <a itemprop="url" href="https://techcompany.com">Visit Website</a>
    </div>
    
    <!-- Article with Microdata -->
    <article itemscope itemtype="https://schema.org/Article">
        <h1 itemprop="headline">How to Build Responsive Websites</h1>
        <div itemprop="author" itemscope itemtype="https://schema.org/Person">
            <span itemprop="name">John Doe</span>
        </div>
        <time itemprop="datePublished" datetime="2024-01-15">January 15, 2024</time>
        <div itemprop="articleBody">
            <p>Content of the article...</p>
        </div>
    </article>
</body>
</html>
```

**Key Concepts:**
- Structured data
- SEO optimization
- Search engine understanding
- Rich snippets

#### 34. How do you implement HTML5 WebRTC?
**Answer:**
WebRTC enables real-time communication:

```html
<!DOCTYPE html>
<html>
<head>
    <title>WebRTC Video Chat</title>
</head>
<body>
    <video id="localVideo" autoplay muted></video>
    <video id="remoteVideo" autoplay></video>
    <button id="startButton">Start Call</button>
    <button id="endButton">End Call</button>
    
    <script>
        const localVideo = document.getElementById('localVideo');
        const remoteVideo = document.getElementById('remoteVideo');
        const startButton = document.getElementById('startButton');
        const endButton = document.getElementById('endButton');
        
        let localStream;
        let peerConnection;
        
        const configuration = {
            iceServers: [
                { urls: 'stun:stun.l.google.com:19302' }
            ]
        };
        
        startButton.addEventListener('click', startCall);
        endButton.addEventListener('click', endCall);
        
        async function startCall() {
            try {
                localStream = await navigator.mediaDevices.getUserMedia({
                    video: true,
                    audio: true
                });
                localVideo.srcObject = localStream;
                
                peerConnection = new RTCPeerConnection(configuration);
                peerConnection.ontrack = (event) => {
                    remoteVideo.srcObject = event.streams[0];
                };
                
                localStream.getTracks().forEach(track => {
                    peerConnection.addTrack(track, localStream);
                });
                
            } catch (error) {
                console.error('Error accessing media devices:', error);
            }
        }
        
        function endCall() {
            if (localStream) {
                localStream.getTracks().forEach(track => track.stop());
            }
            if (peerConnection) {
                peerConnection.close();
            }
        }
    </script>
</body>
</html>
```

**Key Concepts:**
- Real-time communication
- Media streams
- Peer connections
- WebRTC API

#### 35. How do you implement HTML5 WebAssembly integration?
**Answer:**
WebAssembly provides high-performance execution:

```html
<!DOCTYPE html>
<html>
<head>
    <title>WebAssembly Example</title>
</head>
<body>
    <h1>WebAssembly Calculator</h1>
    <input type="number" id="num1" placeholder="First number">
    <input type="number" id="num2" placeholder="Second number">
    <button onclick="calculate()">Calculate</button>
    <p id="result"></p>
    
    <script>
        let wasmModule;
        
        // Load WebAssembly module
        async function loadWasm() {
            try {
                const wasmBytes = await fetch('calculator.wasm').then(response => response.arrayBuffer());
                wasmModule = await WebAssembly.instantiate(wasmBytes);
                console.log('WebAssembly module loaded');
            } catch (error) {
                console.error('Error loading WebAssembly:', error);
            }
        }
        
        function calculate() {
            if (!wasmModule) {
                document.getElementById('result').textContent = 'WebAssembly not loaded';
                return;
            }
            
            const num1 = parseInt(document.getElementById('num1').value);
            const num2 = parseInt(document.getElementById('num2').value);
            
            try {
                const result = wasmModule.instance.exports.add(num1, num2);
                document.getElementById('result').textContent = `Result: ${result}`;
            } catch (error) {
                console.error('Error in WebAssembly calculation:', error);
            }
        }
        
        // Load WebAssembly on page load
        loadWasm();
    </script>
</body>
</html>
```

**Key Concepts:**
- High performance
- Binary format
- JavaScript integration
- Cross-platform execution

## 🎯 Practice Exercises

### Beginner
1. Create a basic HTML page structure
2. Add semantic elements to a webpage
3. Create a simple contact form

### Intermediate
1. Build a responsive navigation
2. Implement form validation
3. Create an accessible image gallery

### Advanced
1. Optimize a webpage for performance
2. Implement PWA features
3. Create a complex form with advanced validation

### Expert
1. Design a scalable HTML architecture
2. Implement advanced accessibility features
3. Create a high-performance web application

## 📚 Additional Resources

- [MDN HTML Documentation](https://developer.mozilla.org/en-US/docs/Web/HTML)
- [HTML5 Semantic Elements](https://www.w3schools.com/html/html5_semantic_elements.asp)
- [Web Accessibility Guidelines](https://www.w3.org/WAI/WCAG21/quickref/)
- [HTML Best Practices](https://github.com/hail2u/html-best-practices)