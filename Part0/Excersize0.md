# Exercise 0.4-6
Sequence Diagrams to depict the chain of events caused

## Excercise 0.4
Where the user creates a new note on the page https://studies.cs.helsinki.fi/exampleapp/notes

```mermaid
sequenceDiagram
    participant browser
    participant server

    Note right of browser: User writes a note and clicks the "Save" button

    browser->>server: POST https://studies.cs.helsinki.fi/exampleapp/new_note
    activate server
    Note left of server: The server receives the form data (text input). The server creates a new note object, and adds it to an array called notes.
    server-->>browser: HTTP 302 URL redirect to /exampleapp/notes
    deactivate server

    Note right of browser: The browser follows the redirect and reloads the Notes page

    browser->>server: GET https://studies.cs.helsinki.fi/exampleapp/notes
    activate server
    server->>browser:HTML Document
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
    server-->>browser: [{content: "Hello", date: "2026-02-17T20:19:14.556Z"},…]
    deactivate server

    Note right of browser: The browser executes the callback function that renders the notes
```
## Exercise 0.5
where the user goes to the single-page app version of the notes app at https://studies.cs.helsinki.fi/exampleapp/spa.

```mermaid
sequenceDiagram
    participant browser
    participant server

    browser->>server: GET https://studies.cs.helsinki.fi/exampleapp/spa
    activate server
    server-->>browser: HTML document
    deactivate server

    browser->>server: GET https://studies.cs.helsinki.fi/exampleapp/main.css
    activate server
    server-->>browser: the css file
    deactivate server

    browser->>server: GET https://studies.cs.helsinki.fi/exampleapp/spa.js
    activate server
    server-->>browser: the JavaScript file
    deactivate server

    Note right of browser: The browser starts executing the JavaScript code that fetches the JSON from the server

    browser->>server: GET https://studies.cs.helsinki.fi/exampleapp/data.json
    activate server
    server-->>browser: [{content: "✏️", date: "2026-02-17T20:32:15.579Z"},…]
    deactivate server

    Note right of browser: The browser executes the callback function that renders the notes
```

## Exercise 0.6
where the user creates a new note using the single-page version of the app.
```mermaid
sequenceDiagram
    participant browser
    participant server

    Note right of browser: User writes a note and clicks the "Save" button
    Note right of browser: JS intercepts the default form submit.<br>It creates a new note, adds it to the local list,<br>and re-renders the UI immediately.
    
    browser->>server: POST https://studies.cs.helsinki.fi/exampleapp/new_note_spa
    activate server
    Note left of server: Server parses the JSON payload and saves the note.
    server-->>browser: HTTP 201 Created {"message":"note created"}
    deactivate server
```
