```mermaid

sequenceDiagram
    participant browser
    participant server
    participant user
    participant spa

    Note right of user: User interacts with the web page

    user->>browser: Open https://studies.cs.helsinki.fi/exampleapp/spa
    activate browser
    browser->>server: GET https://studies.cs.helsinki.fi/exampleapp/spa
    activate server
    server-->>spa: Initial JSON data
    deactivate server


    Note right of browser: User access suscefully

    ```