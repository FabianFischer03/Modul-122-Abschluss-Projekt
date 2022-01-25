# git-autocommit
Ein Bash-Skript zum automatisierten Übertragen von Änderungen an Github

Es verwendet inotifywait (einen Linux-Systemaufruf aus der inotify-Familie), um ein Verzeichnis rekursiv auf Änderungen zu überwachen.
Löst Befehle aus, um Änderungen zu pushen, wenn sie entdeckt werden.

Dieses Skript kann leicht für jeden VCS/Cloud-Anbieter modifiziert werden, der eine Kommandozeilenschnittstelle bietet.

## Vor der Benutzung: 
1. Vergewissern Sie sich, dass git oder das von Ihnen verwendete VCS richtig konfiguriert ist (SSH-Schlüssel) und dass Sie das Ziel-Repository bereits auf Ihren lokalen Rechner geklont haben.
2. Stellen Sie sicher, dass Sie inotify-tools installiert haben.
3. Stellen Sie sicher, dass Sie den korrekten Pfad des geklonten Repos im Skript angeben.

## Verwendung des Skripts: 
- Verwenden Sie `./watch.sh`, um es im Vordergrund auszuführen
- Verwenden Sie `./watch.sh &`, um es im Hintergrund laufen zu lassen 

## Wie stoppen Sie die Ausführung des Skripts im Hintergrund:
- Wenn Sie das Skript mit `./watch.sh` ausführen, wird es beendet, sobald man Strg+C drückt oder die Terminal-Sitzung beendet.


- Wenn Sie das Skript im Hintergrund ausführen (was praktisch ist), indem Sie `./watch.sh &` verwenden

  Das &-Zeichen sorgt dafür, dass der Prozess oder jeder andere Prozess im Hintergrund läuft
  
  Wenn Sie mit der Verwendung des Skripts fertig sind, wird es schwierig, das Skript zu beenden. Eine Möglichkeit besteht darin, den Rechner neu zu starten, was zwar einfach, aber nicht sehr bequem ist.
  
  Hier ist die intelligente Methode: 
  
  Benutzen Sie `ps aux | grep "watch.sh"`, finden Sie die PID des Skripts und töten Sie es dann mit `kill PID_of_watch.sh`.
  
  Danach müssen Sie `ps aux | grep "inotify"` ausführen, die PID von inotify finden und es dann mit `kill PID_of_inotify` töten

Sie können keine Dateien hochladen, deren einzelne Größe 50 MB übersteigt.
Sie können so viele Dateien mit geringerer Größe hochladen, wie Sie benötigen.
