# Diagrama de creación de nota

```mermaid
sequenceDiagram
    participant browser
    participant server

    %% El usuario escribe una nota en el campo de texto
    browser->>browser: User types note in text field

    %% El usuario hace clic en el botón Save
    browser->>browser: User clicks Save button

    %% El navegador envía los datos al servidor (nota y fecha)
    browser->>server: POST https://studies.cs.helsinki.fi/exampleapp/notes { "content": "User's note", "date": "current date" }
    activate server
    server-->>browser: Response with updated note list or confirmation
    deactivate server

    %% El navegador actualiza la lista de notas
    Note right of browser: The browser updates the displayed notes with the new one

    %% (Opcional) Si el servidor responde con un JSON con la lista actualizada de notas
    browser->>server: GET https://studies.cs.helsinki.fi/exampleapp/data.json
    activate server
    server-->>browser: [{ "content": "User's note", "date": "current date" }, ...]
    deactivate server

    Note right of browser: The browser renders the updated list of notes

