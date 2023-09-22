# JDA (Java Discord API)
JDA ist bestrebt, ein sauberer und vollständiger Wrapper für die Discord REST API und deren Websocket-Events für Java bereitzustellen.

Wenn du Vorschläge, Fragen oder Feedback zu diesem Wiki hast, dann besuch bitte den #wiki-dev Kanal auf dem [JDA Discord Server](https://discord.gg/0hMr4ce0tIk3pSjp).

!!! example "Examples"
    ```java
    public class ReadyListener implements EventListener
    {
        public static void main(String[] args)
                throws InterruptedException
        {
            // Note: It is important to register your ReadyListener before building
            JDA jda = JDABuilder.createDefault("token")
                .addEventListeners(new ReadyListener())
                .build();

            // optionally block until JDA is ready
            jda.awaitReady();
        }

        @Override
        public void onEvent(GenericEvent event)
        {
            if (event instanceof ReadyEvent)
                System.out.println("API is ready!");
        }
    }
    ```

    ```java
    public class MessageListener extends ListenerAdapter
    {
        public static void main(String[] args)
        {
            JDA jda = JDABuilder.createDefault("token")
                    .enableIntents(GatewayIntent.MESSAGE_CONTENT) // enables explicit access to message.getContentDisplay()
                    .build();
            //You can also add event listeners to the already built JDA instance
            // Note that some events may not be received if the listener is added after calling build()
            // This includes events such as the ReadyEvent
            jda.addEventListener(new MessageListener());
        }

        @Override
        public void onMessageReceived(MessageReceivedEvent event)
        {
            if (event.isFromType(ChannelType.PRIVATE))
            {
                System.out.printf("[PM] %s: %s\n", event.getAuthor().getName(),
                                        event.getMessage().getContentDisplay());
            }
            else
            {
                System.out.printf("[%s][%s] %s: %s\n", event.getGuild().getName(),
                            event.getTextChannel().getName(), event.getMember().getEffectiveName(),
                            event.getMessage().getContentDisplay());
            }
        }
    }
    ```

    **Weitere Beispiele**:
    Wir stellen eine kleine Auswahl an Beispielen zur Verfügung: [Beispiel Directory](https://github.com/DV8FromTheWorld/JDA/tree/master/src/examples/java).

## Download
Hier kannst du das neuste Update herunterladen:
[Promoted Downloads](https://github.com/DV8FromTheWorld/JDA/releases)

Wenn du die aktuellsten Builds möchtest, kannst du sie hier herunterladen: [Latest Build Downloads](https://ci.dv8tion.net/job/JDA5/)

## Dokumente
Javadokumente sind in beiden Formaten verfügbar, in jar Format und web Format.<br>
Das jar Format steht dir hier zur Verfügung: [Promoted Downloads](https://github.com/DV8FromTheWorld/JDA/releases). Oder auf einer der folegenden Seiten: [legacy v4 Downloads](https://ci.dv8tion.net/job/JDA/) oder [v5 Downloads](https://ci.dv8tion.net/job/JDA5/).<br>
<br>
Die Webseite ermöglicht die Anzeige der [neuesten](https://ci.dv8tion.net/job/JDA5/javadoc/) oder [älteren Dokumente](https://ci.dv8tion.net/job/JDA/javadoc/)  sowie die Javadocs jedes einzelnen Builds. 
Um die Javadocs für ein bestimmtes Build anzuzeigen, musst du die Seite dieses Builds auf dem [Build-Server](https://ci.dv8tion.net/job/JDA5/) aufrufen und 
die Javadoc-JAR für den jeweiligen Build herunterladen.<br>

Ein Beispiel wäre: `https://ci.dv8tion.net/job/JDA5/BUILD_NUMBER_GOES_HERE`, du musst nur „BUILD_NUMBER_GOES_HERE“ durch den gewünschten Build ersetzen.<br>
Sobald du die jar Datei mit dem Zip-Tool deiner Wahl (winrar oder 7zip usw.) 
extrahiert hast, öffne die `index.html` Datei mit Ihrem Internetbrowser.

## Getting Help
Wenn du Hilfe benötigst oder einfach nur mit den JDA Entwicklern oder anderen Entwicklern sprechen möchtest, dann kannst du dem [Official JDA Discord Server](https://discord.gg/0hMr4ce0tIl3SLv5) beitreten.

Alternativ kannst du auch der Inofficial  [Unofficial Discord API Guild](https://discord.gg/discord-api). beitreten. 
Sobald du beigetreten bist, findest du JDA-spezifische Hilfe im Kanal  `#java_jda`. 
Der JDA-spezifische Server reagiert oft schneller als der `#java_jda` Kanal auf dem Discord-API-Server.

Anleitungen und Einrichtungshilfe findest du auch in diesem Wiki.
Besonders interessant sind die [Getting Started](../using-jda/getting-started.md) Seiten.

## Contributing to JDA
Wenn du zu JDA beitragen möchtest, stell sicher, dass dein Branch auf unserem **Master-Branch** (oder einem Feature-Branch)
basiert und dein PR in **demselben** Branch erstellt wird. **Wir lehnen jegliche PRs zwischen Branches oder in Release-Branches ab!**

Es wird außerdem dringend empfohlen, mit den Entwicklern Kontakt aufzunehmen, bevor Pull Requests geöffnet werden (entweder über ein Issue oder über den oben genannten Discord-Server).<br>
Es ist durchaus möglich, dass sich deine Änderung bereits in der Entwicklung befindet oder dass du etwas verpasst hast.
 
Weitere Infos kannst du auf unserer Wiki Seite unter [Contributing](../contributing/contributing.md) finden.

## Dependencies
Das Projekt benötigt **Java 8**.<br>
Für andere Dependencies: [README](https://github.com/DV8FromTheWorld/JDA/tree/master/README.md)
