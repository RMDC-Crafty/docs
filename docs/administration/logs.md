This page shows several logs from your system as opposed to just the default `latest.log` from your server. All logs are presented in a tabbed interface,  *newest* at the bottom. To quickly scroll to the bottom, just click in the text box and it should auto-scroll you to the bottom. 

For performance reasons, these logs are trimmed to the last 100 lines or so with the exception of the latest.log. The latest.log is trimmed to the last 300 lines. At the bottom are any and all warning or error lines found in `latest.log` in an easy to search table. The line number is listed along with the log item so you can easily find these lines in your logs.

*  Latest.log – This is the main log from your server. This is as busy as your server is.
*  Crafty.log – This is Crafty Controllers log. This is pretty quiet unless Crafty is doing something.
*  Schedule.log – This is the scheduler log. This is a very busy log. Access.log – These are the access logs to your Crafty interface.
*  Access.log – These are Tornado access logs. Tornado is the web server behind Crafty.

![logs-b2_1_](/images/crafty-logs.png)