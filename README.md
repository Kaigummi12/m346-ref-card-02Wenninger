
## Dokumentation für die Aufgabe m346-ref-card-02 von Kai Wenninger

Als erstes habe ich das GitLab Repository https://gitlab.com/bbwrl/m346-ref-card-02 heruntergeladen und auf GitHub gepusht.

![image](https://github.com/user-attachments/assets/822390af-40ff-463e-93bf-853a9b15d788)

Anschliessend habe ich Internet nach einer möglichen Lösung gesucht und folgendes auf der Seite Medium gefunden. https://medium.com/@ravipatel.it/automating-docker-image-creation-and-push-to-docker-hub-for-a-react-app-using-github-actions-7fa092751fc0 Dieser Anleitung bin ich gefolgt und ich versuchte auch immer zu verstehen was in dieser Anleitung gemacht wird. Ebenfalls habe ich viele neue Dinge gelernt.

## Umsetzung

Als erster Schritt habe ich im Projekt ein Dockerfile hinzugefügt. Dieses braucht man immer wenn man mit Docker arbeitet.

![image](https://github.com/user-attachments/assets/45b6a352-9648-43e2-8643-a6eac3461293)

Das Dockerfile baut eine React-Anwendung mit Node.js, erstellt den Produktions-Build und serviert diesen dann mit einem Nginx-Webserver. So wird die Anwendung in einem leichten Webserver bereitgestellt, um sie live zu betreiben.

Kurze Zeit später habe ich dann noch ein docker-publish.yml file erstellt mit folgendem Inhalt.

![image](https://github.com/user-attachments/assets/c5dafe04-37e0-462a-9e59-a01051559e47)

Der Code baut ein Docker-Image, wenn Änderungen auf den main-Branch gepusht werden, und lädt es anschliessend in DockerHub hoch. Dabei wird der Benutzername und das Passwort aus den GitHub-Secrets verwendet.

## Hinzufügen von Logindaten (GitHub Secrets) auf GitHub (Actions)

Ich habe die beiden Files (Dockerfile, docker-publish.yml) ebenfalls in das Repository auf GitHub gepusht und nun weitere Einstellungen auf GitHub selber vorgenommen. Als nächstes müssen wir die Actions in GitHub hinzufügen. Dazu gehen wir auf das Repository -> Einstellungen -> Secrets variables -> Actions

![image](https://github.com/user-attachments/assets/bfeebb71-3b79-4015-8391-21bdb177a924)

Hier kann man dann ein neues "Repository Secret" erstellen.
Anschliessend gitb man seine Logindaten für Docker ein. Einma DOCKER_USERNAME und DOCKER_PASSWORD. Wenn man diese beiden hinzugefügt hat sieht es dann so aus.

![image](https://github.com/user-attachments/assets/3e4b2b53-942b-4855-81ec-842d812844bd)

Nachdem ich diese Schritte erfolgreich ausgeführt/hinzugefügt habe, konnte ich auf GitHub bereits beobachten, dass der Build schon am laufen ist. Bei mir ist er erfolgreich durchgelaufen, was man am Häcklein links sehen kann.

![image](https://github.com/user-attachments/assets/76942004-7d8b-4a37-9f2e-c4b322b48541)

# Best Practices für CI/CD mit GitHub Actions

1. **Sichere Secrets-Verwaltung**: Verwende GitHub Secrets für Passwörter und API-Keys.
2. **Automatisches Testen**: Führe Tests automatisch vor dem Deployment aus.
3. **Effizientes Caching**: Nutze Caching, um Build-Zeiten zu verkürzen.





