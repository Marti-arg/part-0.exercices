```mermaid
sequenceDiagram
    participant user as Usuario
    participant browser as Navegador
    participant server as Servidor

    user->>browser: Escribe una nueva nota y presiona "Guardar"
    browser->>browser: Agrega la nueva nota a la lista en memoria
    browser->>server: POST https://studies.cs.helsinki.fi/exampleapp/new_note_spa con la nueva nota en formato JSON
    activate server
    server-->>browser: Respuesta 201 Created
    deactivate server

    Note right of browser: La nota ya se muestra en la página sin necesidad de recargar.

    browser->>server: GET https://studies.cs.helsinki.fi/exampleapp/data.json
    activate server
    server-->>browser: Lista actualizada de notas en formato JSON
    deactivate server

    browser->>browser: Vuelve a renderizar la lista de notas con la nueva nota incluida.
