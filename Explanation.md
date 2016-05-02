## How Browsers Work

_So this is the bigger picture of how this works. There are many low level details which i left out intentionally because this is a question whose answer could grow into an entire course on networking, so here's a version that only details some of the cases._ 

When you enter _https://www.google.com_ or simply _www.google.com_ in the address bar of the browser then the following series of things happens

1. The browser need to know the numerical IP address so it first looks into;
  * __its browser cache__ followed by
  * __OS cache__, router cache, ISP DNS cache__ then
  * __a recursive search into ISP's DNS server begins with__ through the [TLD nameserver] (http://www.dnsknowledge.com/whatis/tld-name-server/) until it finds the required ip address. 

  _there is a concept of load balancer which also comes into play. it is just a  piece of hardware that listens on a particular  IP address and forwards the requests to other servers. Major sites will  typically use expensive high-performance load balancers._

2. After obtaining the IP the browser sends a [HTTP](https://en.wikipedia.org/wiki/Hypertext_Transfer_Protocol) request to the web server

3. the google server then responds with a [permanent redirect (301)](https://support.google.com/webmasters/answer/93633?hl=en). it tells the browser to go to "http://www.google.com/" instead of "http://google.com/"

4. The browser follows the redirect and sends a another Get request

5. The server sends a HTML response back to the client. The Content-type of header instructs the browser to render the response content as HTML, instead of 'downloading it as a file'. 

6. The browser begins rendering the HTML and sends the request for object embedded in HTML as many sites deliver their CSS,Images files and scripts file from a [content delivery network (CDN)](http://www.webopedia.com/TERM/C/CDN.html). The browser will again send the [GET request](http://www.w3schools.com/tags/ref_httpmethods.asp) for each of the embedded URL which again goes by the same procedure of look up and other above mention steps.

7. After this the browser may send further [AJAX request](http://stackoverflow.com/questions/2130239/what-is-exactly-is-ajax-request-is-it-different-from-servlet-request) to communicate with the web server even after the page is rendered. 



_Thanks [Sumit Jha](https://www.quora.com/What-are-the-series-of-steps-that-happen-when-an-URL-is-requested-from-the-address-field-of-a-browser) for helping me understand this._

