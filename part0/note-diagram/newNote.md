sequenceDiagram
    participant browser
    participant server
    participant user

    Note right of user: User interacts with the web page

    user->>browser: Open https://studies.cs.helsinki.fi/exampleapp/notes
    activate browser
    browser->>server: GET https://studies.cs.helsinki.fi/exampleapp/notes
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


    Note right of browser: User writes something in the text field

    user->>browser: Write a new note in the text field
    activate browser

    Note right of browser: User clicks on the Save button

    user->>browser: Click Save button
    activate browser

    Note right of browser: The browser starts executing the JavaScript code that fetches the JSON from the server

    browser->>server: POST https://studies.cs.helsinki.fi/exampleapp/data.json
    activate server
    server-->>browser: 201 Created (Note saved successfully)
    deactivate server
    server-->>browser: [{ "content": "HTML is easy", "date": "2023-1-1" }, ... ]
    deactivate browser

    Note right of user: The new note is successfully saved