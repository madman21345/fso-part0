# Exercise 0.4
Sequence Diagram of User creating a new note
```mermaid
sequenceDiagram;
    participant browser;
    participant server;

    Note right of browser: Form submission event
    browser->>server: POST note to https://studies.cs.helsinki.fi/exampleapp/new_note;
    activate server;
    server->>browser: 302, redirect browser to make GET request to https://studies.cs.helsinki.fi/exampleapp/notes;
    deactivate server;
    activate browser;

    browser->>server: GET https://studies.cs.helsinki.fi/exampleapp/notes;
    deactivate browser;
    activate server;
    server-->>browser: returns HTML document;
    deactivate server;

    browser->>server: GET https://studies.cs.helsinki.fi/exampleapp/main.css;
    activate server;
    server-->>browser: returns CSS file;
    deactivate server;

    browser->>server: GET https://studies.cs.helsinki.fi/exampleapp/main.js;
    activate server;
    server-->>browser: returns JavaScript file;
    deactivate server;

    Note right of browser: The browser starts executing the JavaScript code that fetches the JSON from the server;

    browser->>server: GET https://studies.cs.helsinki.fi/exampleapp/data.json;
    activate server;
    server-->>browser: returns raw data in json format;
    deactivate server;

    Note right of browser: The browser executes the callback function that renders the notes;
```

