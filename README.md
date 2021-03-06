# Multithreaded TCP Client/Server using Sockets

The following program is devided into 3 units:
 - Web Site Creator
 - TCP Web Server
 - TCP Web Crawler
 
### Web Site Creator in Shell

Creates w websites which contain p pages (html files) and stores them into root_directory.

##### Running
```
./webcreator.sh root_directory text_file.txt w p
```
### TCP Web Server in C

Serves HTTP requests from specific websites' pages -by searching into root_directory- and returns the appropriate HTTP responce. A threadpool is used in order to manage all incoming requests. Each thread is responsible for one request.
Server can also listen to an other port in odrer to receive the following command requests:
 * STATS: Implements time up, number of pages served and number of bytes read.
 * SHUTDOWN: Closes connection.

##### Running
```
./myhttpd -p server_port -c command_port -t num_threads -d root_directory
```
### TCP Web Crawler in C

Starting from a given URL, it searches recursevly for other URLs - into that page - and sends a GET request for each of them. Process completes after all links from each page are downloaded. A threadpool is also used here in order to manage all responces. Each thread is responsible for one responce.
Crawler can also listen to an other port in odrer to receive the following command requests as above.
 
##### Running
```
./mycrawler -h host_or_IP -p server_port -c command_port -t num_threads -d save_dir starting_URL
```
### Compilation
To compile each program type ```make``` inside relevant directory. Type ```make clean``` to remove object files.

### Telnet
Command requests can be sent via Telnet, by typing:
``` telnet localhost command_port ```
Connection closes after sending a request.

### Http Requests
Http Requests can be also sent via Firefox by typing 
``` localhost:server_port/root_directory/page_name``` 
 


