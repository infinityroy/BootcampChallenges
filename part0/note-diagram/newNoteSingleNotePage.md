sequenceDiagram
    participant browser
    participant spa
    participant server
    participant user

    Note right of user: User interacts with the SPA

    user->>spa: Open SPA
    activate spa
    spa->>server: GET https://studies.cs.helsinki.fi/exampleapp/spa
    activate server
    server-->>spa: Initial JSON data
    deactivate server

    Note right of spa: User writes something in the text field

    user->>spa: Write a new note in the text field
    activate spa

    Note right of spa: User clicks on the Save button

    user->>spa: Click Save button
    spa->>server: POST https://studies.cs.helsinki.fi/exampleapp/spa
    activate server
    server-->>spa: 201 Created (Note saved successfully)
    deactivate server
    deactivate spa

    Note right of user: The new note is successfully saved in the SPA without a page reload