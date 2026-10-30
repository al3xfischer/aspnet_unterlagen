# ASP.NET Web API – Kursunterlagen

Folien und Beispielcode zum viertägigen Kurs. Ihr baut Schritt für Schritt eine REST-API mit ASP.NET Core und .NET 10, von den Grundlagen bis zum Betrieb.

## Inhalt

| Tag | Thema | Übungen | Folien | Code |
| --- | --- | --- | --- | --- |
| 1 | REST-Grundlagen und erste API | 1–4, Challenge 1 | [PDF](tag1.pdf) | [tag1](tag1) |
| 2 | Konzepte in .NET und Datenmodelle | 5–9, Challenge 2 | [PDF](tag2.pdf) | [tag2](tag2) |
| 3 | Datenbanken, Logging und Testen | 10–13, Challenge 3 | [PDF](tag3.pdf) | [tag3](tag3) |
| 4 | Fehlerbehandlung, Sicherheit und Betrieb | 14–18, Abschluss-Challenge | [PDF](tag4.pdf) | [tag4](tag4) |

Jeder Code-Ordner enthält den fertigen Stand am Ende des jeweiligen Tages, also auch die Lösungen der Übungen und Challenges. Die Tage bauen aufeinander auf, aber jeder Ordner lässt sich für sich starten. Am besten löst ihr die Übungen zuerst selbst und vergleicht danach.

## Voraussetzungen

- [.NET 10 SDK](https://dotnet.microsoft.com/download/dotnet/10.0)
- Visual Studio, VS Code mit C# Dev Kit oder Rider

Einmalig ausführen:

```bash
dotnet dev-certs https --trust
dotnet tool install --global dotnet-ef
```

`dotnet-ef` braucht ihr ab Tag 3.

## Projekt starten

Beispiel für Tag 1, die anderen Tage funktionieren genauso:

```bash
cd projekt/tag1/KursApi
dotnet run --launch-profile https
```

Swagger UI läuft dann unter <https://localhost:7020/swagger>.

In jedem Projekt liegt eine `KursApi.http` mit fertigen Requests zu den Übungen. Visual Studio und Rider führen sie direkt aus, VS Code braucht die Erweiterung REST Client.

### Ab Tag 3: Datenbank anlegen

Die SQLite-Datenbank ist nicht im Repo und wird beim Start nicht automatisch erzeugt. Legt sie einmal pro Ordner an, sonst antworten die Datenbank-Endpunkte mit 500:

```bash
cd projekt/tag3/KursApi
dotnet ef database update
```

### Tag 4: Tokens erzeugen

Die geschützten Endpunkte brauchen einen JWT. Erzeugt die Tokens im Ordner `projekt/tag4/KursApi`, **bevor** ihr die API startet:

```bash
dotnet user-jwts create --name anna
dotnet user-jwts create --name admin --role Admin
```

Tragt die ausgegebenen Tokens oben in der `KursApi.http` bei `@token` und `@adminToken` ein. Lief die API beim ersten Erzeugen schon, startet sie neu, sonst kommt trotz Token ein 401.

## Tests

Tag 3 und 4 enthalten Unit-Tests:

```bash
cd projekt/tag3
dotnet test
```

## Fragen

Alexander Fischer, [af@mit.at](mailto:af@mit.at)
