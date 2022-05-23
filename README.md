# Functionality

The application simulates the stream of data by reading lines from a dataset(more on that below) and serving them through a stream channel to an analytics client. The client analyses each incoming line or object as it arrives and calculate 4 different types of metric / result:

1. Total number of video game copies sold in all regions (2 second rolling metric)
2. Average number of video game copies sold in all regions (2 second rolling metric)
3. Top selling video game genre (2 second rolling metric)
4. Name of the top selling video game (2 second rolling metric)
5. Average number of video game copies sold in all regions (3-minute-rolling metric)

# Application Architecture

The architecture includes 3 microservices:

1. One for data streaming client (Client)
2. One for analytics client (Server)
3. One for displaying analysed / metric data (Web_Server)

There is a single web page that displays the abovementioned metrics / results whenever the page is loaded or refreshed. The application streams an average of 2 records / lines / objects per second with random variability.

# Data

The dataset consists of a list of game sales greater than 100k copies. It contains game sales in different regions such as Europe, USA etc along with the game description such as name, year released, platform on which the game was released, game genre and game publishers.

The video game sales dataset can be found [here](https://www.kaggle.com/datasets/gregorut/videogamesales).

# Technical COnsiderations

1. gRPC used as the communication mechanism and use a stream channel to send the data to the client.
2. Flask for the web server and web page. The web page consists of a table which is updated every 2 seconds and a bar chart to visualize the analysis made in last 3 minutes (3-minute rolling metric).
