# DarwinforGames UMLDiagrams

[chrome拡張のPegmatite](https://chrome.google.com/webstore/search/Pegmatite)のインストールでgithub上でダイアグラムを確認可能

```puml
@startuml
title DarwinforGames : Get GameItem(Unit,Material) Information Sequence

actor User

User -> WebServer : Request an GameItem

note left:Get /{GameItems}/{Id}[.json]

activate Controller

WebServer -> Controller : Notify Request

activate Model
database DB

Controller -> Model : Query the Requested Model By Id

Model -> DB : Query Relation By Id

DB -> Model : Response Relation By Id

Model -> Controller : Response Model

alt Requested Json Response
    Controller -> WebServer : Response json
    WebServer -> User : Response json
else
    Controller -> WebServer : Response html
    WebServer -> User : Response html
end
@enduml
```

