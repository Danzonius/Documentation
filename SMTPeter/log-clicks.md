# Clicks logfiles

Log files with the prefix "clicks" hold information about the clicks that
are generated by your sent messages. You can download the content of these
files in CSV format using the [REST logfiles API](rest-logfiles). These
log files contain the following data in the respective order: 

| Name        | Description                                                               |
| ----------- | ------------------------------------------------------------------------- |
| id          | The id of the message that generated the click                            |
| time        | The time of the click in the form YYYY-MM-DD hh:mm:ss                     |
| headers     | The headers that where used to make the call, separated by newlines       |
| ip          | The IP address of the system where the link was clicked                   |
| url         | The URL in the message that was clicked                                   |
| destination | The URL to which the clicker was directed to                              |
| tags        | The tags of the message that generated the click, separated by semicolons |
| recipient   | The recipient of the message that generated the click                     |
| city        | The city in which the click was generated                                 |
| countryname | The name of the country in which the click was generated                  |
| countrycode | The code (alpha-2) of the country in which the click was generated        |
| regioncode  | The code of the region in which the click was generated                   |
