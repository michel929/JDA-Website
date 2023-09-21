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

    **More Examples**:
    We provide a small set of Examples in the [Example Directory](https://github.com/DV8FromTheWorld/JDA/tree/master/src/examples/java).

## Download
Hier kannst du das letzte Update herunterladen:
[Promoted Downloads](https://github.com/DV8FromTheWorld/JDA/releases)

If you want the most up-to-date builds, you can get them here: [Latest Build Downloads](https://ci.dv8tion.net/job/JDA5/)

## Dokumente
Javadokumente sind in beiden Formaten verfügbar, in jar Format und web Format.<br>
Das jar Format steht dir hier zur Verfügung: [Promoted Downloads](https://github.com/DV8FromTheWorld/JDA/releases). Oder auf einer der folegenden Seiten: [legacy v4 Downloads](https://ci.dv8tion.net/job/JDA/) oder [v5 Downloads](https://ci.dv8tion.net/job/JDA5/).<br>
<br>
The web format allows for viewing of the [Latest Docs](https://ci.dv8tion.net/job/JDA5/javadoc/) or [legacy Docs](https://ci.dv8tion.net/job/JDA/javadoc/) 
and also viewing of each individual build's javadoc. To view the javadoc for a specific build, you will need to go to that build's page
on [the build server](https://ci.dv8tion.net/job/JDA5/) and download the javadoc jar for the specific build.<br>
A shortcut would be: `https://ci.dv8tion.net/job/JDA5/BUILD_NUMBER_GOES_HERE`, you just need to replace the 
"BUILD_NUMBER_GOES_HERE" with the build you want.<br>
Once you have the jar extract the files with the zip tool of your preference (winrar or 7zip, etc.) and open the `index.html` file with your internet browser.

## Getting Help
If you need help, or just want to talk with the JDA or other Devs, you can join the [Official JDA Discord Guild](https://discord.gg/0hMr4ce0tIl3SLv5).

Alternatively you can also join the [Unofficial Discord API Guild](https://discord.gg/discord-api).
Once you joined, you can find JDA-specific help in the `#java_jda` channel.
The JDA specific server will often have faster responses than the `#java_jda` channel in the Discord API server.

For guides and setup help you can also take a look at this wiki.
<br>Especially interesting are the [Getting Started](../using-jda/getting-started.md) Pages.

## Contributing to JDA
Wenn du zu JDA beitragen möchtest, stell sicher, dass dein Branch auf unserem **Master-Branch** (oder einem Feature-Branch)
basiert und dein PR in **demselben** Branch erstellt. **Wir lehnen jegliche PRs zwischen Zweigen oder in Release-Zweigs ab!**

It is also highly recommended to get in touch with the Devs before opening Pull Requests (either through an issue or the Discord servers mentioned above).<br>
It is very possible that your change might already be in development or you missed something.

More information can be found at the wiki page [Contributing](../contributing/contributing.md)

## Dependencies
Das Projekt benötigt **Java 8**.<br>
Für andere Dependencies: [README](https://github.com/DV8FromTheWorld/JDA/tree/master/README.md)
