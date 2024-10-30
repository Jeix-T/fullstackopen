``` mermaid
sequenceDiagram
    participant browser
    participant server

    browser->>server: POST https://studies.cs.helsinki.fi/exampleapp/new_note
    activate server
    server-->>browser: Status code HTTP 302 Found Location /exampleapp/notes
    deactivate server

    Note right of browser: The server responds that it finds the path /exampleapp/notes

    browser->>server: GET https://studies.cs.helsinki.fi/exampleapp/notess
    activate server
    server-->>browser: HTML document
    deactivate server

    browser->>server: GET https://studies.cs.helsinki.fi/exampleapp/main.css
    activate server
    server-->>browser: the css file
    deactivate server

    browser->>server: GET https://studies.cs.helsinki.fi/exampleapp/main.js
    activate server
    server-->>browser: the JavaScript file
    deactivate server

    Note right of browser: The browser starts executing the JavaScript code that fetches the JSON from the server

    browser->>server: GET https://studies.cs.helsinki.fi/exampleapp/data.json
    activate server
    server-->>browser: [{"content":"Hola, desde Santander de Q","date":"2024-10-30T15:52:59.229Z"}, ... ]
    deactivate server

    Note right of browser: The browser executes the callback function that renders the notes
```
