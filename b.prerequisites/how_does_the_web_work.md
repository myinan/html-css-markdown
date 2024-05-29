# How Does the Web Work?
### Knowledge Check
**Q1.** What is a web server?

**A1.** A web server is a software/application that serves the information(web pages) stored on the server's hardware per the request of a client(web browser).

**Q2.** What is a network?

**A2.** A network is a collection of interconnected computers. 

**Q3.** What is the internet?

**A3.** "Internet" is the network of networks. Smaller networks are connected to each other via the utilization of routers, constituting "the internet".

**Q4.** What is an IP address?

**A4.** An IP adress is a unique address assigned to each user connected to the internet. IP addresses are assigned to users by the Internet Service Providers(ISPs) and they are used to establish communication over the internet using the Internet Protocol. Since every user has a unique IP adress, with the utilization of Internet Protocol, communication between two different people anywhere in the world is possible if both are connected to the internet.

**Q5.** What is a router?

**A5.** A router is a "computer" that routes the traffic between different networks over the internet. Routers are also connected to each other, routing traffic to different routers if the target destination is not directly connected to that router, making the very fast internet connection we have today possible.

**Q6.** What is an ISP?

**A6.** An ISP(Internet Service Provider) is a type of company, government body or an another type of instution that provides services regarding to internet. These services range from laying cable connections between continents to setting up modems to homes to connect to internet. ISPs also run routers which are used to manage internet traffic.

**Q7.** What are packets and how are they used to transfer data?

**A7.** In the context of "internet", packets are little pieces of data which are utilized to make internet connection a more smooth experience using TCP. The main components of the TCP(Transfer Control Protocol) are as follows: If data which has been requested by the client from a web server indeed exist on the server, it's sent by the server to the requesting client using the Internet Protocol. But to not clog up the internet traffic, the requested data is split into smaller data "packages" and are sent to the requsting client independently from each other. Every package might take a different route to the target destination, depending on the current state of the traffic of routers. When all the packages reach to the destination, client's browser reassambles the packages into the complete data which was requested. If any of the packages were "dropped" by the routers along the way, these missing packages are requested from the server again with TCP.

**Q8.** What is a client?

**A8.** "Client" refers to the internet users requesting data from web servers on other networks.

**Q9.** What is a server?

**A9.** The term "server" is used to refer to the hardware component of the server, software component of the server or both. A server hosts information on it's hardware, for example web pages, and then "serves" this information to the requesting client over the internet using TCP/IP, and if it's a web server, HTTP. 

**Q10.** What is a web page?

**Q10.** A web page is an HTML page/file, usually constituting a component of a larger website. Web pages are stored on servers and served to the requesting clients using TCP/IP and HTTP. If the requested web page is succesfully returned from the server to the client, then the client web browser displays the web page to the user. 

**Q11.** What is a web browser?

**Q11.** A web browser is a special type of software/program that is used to display web pages on a computer. Browsers parse the requested and recieved web pages from a server on the internet, then display the said page to the user. Browsers first display the HTML elements of the page, then if CSS or JavaScript files are also included on the displayed page, these files are requested form the server subsequently and rendered in the browser.

**Q12.** What is a search engine?

**Q12.** A search engine is a type of web application that provides easier access to web pages on the internet. A search engine usually utilizes complex alghorithms to crawl and parse through different websites according to information provided by the client, then display the links to those websites to the user.

**Q13.** What is a DNS request?

**Q13.** A DNS request is a request made to the DNS server that stores the information regarding which DNS corresponds to which IP adress. 

**Q14.** Which browser are you currently using?

**Q14.** Opera.

**Q15.** In your own words, explain what happens when you run a search on google.com.

**Q15.** After running a search on google.com, google's alghorithm starts to parse and crawl through the web according to my input, then displays a list of links to those websites which are deemed to be most relevant to my search by the alghorithm.