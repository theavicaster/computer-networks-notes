# What happens when you type in a URL?

* **Initial Typing** 
  * Lookahead for website suggestions based on history / popular websites / context of current page
  * Implemented using tries.
* **URL Parsing**
  * Is the text a URL or a search term?
  * If URL -&gt; HTTP GET request to that URL
  * If search term -&gt; https://www.google.com/search?query=term
* **Determine which protocol and which port to connect to**
  * HTTP at port 80 or HTTPS at port 443?
  * Browsers actually keep a list of popular websites cached. If a website like google.com is HTTPS then https:// :443 is applied. Besides popular websites, when you first visit a website, if it uses TLS, and we hit with HTTP, it redirects to HTTPS, and is added to this list. This is called Strict Transport Security which is a header that is returned on first access.
* **DNS \(Domain Name System\) Cache Lookup**
  * We need to find the IP address of google.com
  * Browser checks it's own cache first
  * Next, OS cache is checked
  * Next, router level cache is tried. Browser communicates with router
  * Next, the browser communicates with the ISP for ISP level cache 
  * If not found, time for lookup!
* **Initiate DNS Lookup**
  * A recursive search is started. DNS uses UDP. It first queries DNS server of top level domain \(.com\), then it narrows down \(.in\), then finaly reaches granular levels \(google\) until it hits the DNS server for that domain \(google DNS\)
* **Establish TCP Connection**
  * Standard three way handshake mechanism
* **Establish TLS Connection**
  * Standard TLS handshake to set up the symmetric key
* **Send GET request**
  * Data transfer details of this request will flow through the 7 layers \(or rather, post session layer\) of the OSI model. i.e Transport, Network, Datalink and Physical Layers.
  * HTTP specific details such as browser type, type of content accepted, any available cookies and connection headers to keep TCP alive are passed as HTTP headers
* **Web Server sends HTTP Response**
  * Before it reaches the server it may hit -
    * Load balancers - Redirection
    * Firewalls- Gatekeeping
  * The web server itself might hit more Application Servers, which communicate with databases
  * Data fetched back might be from caches, might be stored in caches, might set off an asynchronous action via a message queue etc.
  * Response sent back has Status Code as well as cookies, caching control, compression type etc. in headers
* **HTML Parsing**
  * It renders the barebones HTML document
  * GET additional resources \(images, CSS, JS\)
  * Additional resources are cached as static files

