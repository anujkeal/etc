# ETC Episode 01 — What Actually Happens When You Open a Website?

**Series:** The Hidden Technology Behind Everyday Life  
**Format:** Documentary-style explainer  
**Target runtime:** 9–12 minutes  
**Audience:** Curious viewers with little or no technical background  
**Working title:** What Actually Happens When You Open a Website?  
**Thumbnail:** A browser window connected to a hidden network. Minimal text: “WHERE DOES IT GO?”

## Creative direction

This episode follows the storytelling approach we admire in the quantum physics documentary: begin with something familiar, reveal a surprising question, investigate the hidden process step by step, use simple demonstrations, and finish with a bigger idea.

This is an original ETC script. The reference guides our pacing and explanatory ambition—not wording, scenes, or structure to copy.

**Tone:** Curious, calm, cinematic, conversational.  
**Language:** Plain English. Explain technical words immediately.  
**Visual rule:** Every graphic must clarify an idea. Keep the screen clean.

---

# SCRIPT

## 00:00 — The ordinary action

**[VISUAL]** Extreme close-up of a finger tapping a phone screen. A browser opens. Someone types a website address and presses Enter.

**[SOUND]** A quiet tap. The ordinary sound of a page loading.

**[VISUAL]** The website appears. Hold on the screen.

**[HOST / ON CAMERA]**

This looks simple, doesn't it?

You open a browser. You type a name. You press Enter.

And a moment later, a website appears.

But let me ask you something.

Where was that website before you opened it?

Was it already inside your phone?

Did your phone somehow know where to find it?

And when you press Enter, what actually travels through the internet?

**[VISUAL]** The website freezes. The camera moves through the screen, revealing a stylised network of devices, cables, routers, and servers.

**[NARRATION]**

Behind this ordinary action is a remarkable chain of events.

Your browser has to work out which website you mean, find where it can be reached, establish a connection, ask for information, receive the answer, and turn that information into the page you can see.

And all of this happens so quickly that most of us never think about it.

So today, let's follow one website request from your screen to the computers that make the web possible.

---

## 01:10 — First, what is a website?

**[VISUAL]** A website appears as a single page. It separates into text, images, buttons, colours, and layout elements.

**[HOST]**

When you think of a website, you probably imagine one thing: a page.

But a website is not usually one single picture sitting somewhere on the internet.

It is made from different resources.

There may be text, images, videos, fonts, styles, and code that controls how the page behaves.

**[ON-SCREEN TEXT]**

- HTML — structure and content
- CSS — appearance and layout
- JavaScript — behaviour and interaction
- Images, fonts, video, and other files

**[NARRATION]**

Think of a website like a theatre performance.

HTML gives us the stage and the objects on it.

CSS decides how everything looks: the colours, positions, sizes, and arrangement.

JavaScript can make things respond when someone interacts with them.

And images, fonts, and videos provide the other material the page needs.

This comparison is not perfect, but it gives us a useful starting point.

The important thing is that your browser needs to collect and process these resources before it can show you the finished page.

But first, it needs to find the website.

---

## 02:20 — The name is not the address

**[VISUAL]** On screen: example.com. The text transforms into a numerical IP address. Do not present a real site's IP as a permanent example.

**[HOST]**

Imagine I ask you to visit my house.

I tell you my name, but I don't give you the address.

You know who I am, but you still don't know where to go.

The internet has a similar problem.

We use names such as example.com because they are easy for humans to remember.

But computers need network addresses to communicate.

One important kind of address is called an IP address.

**[ON-SCREEN TEXT]**

Domain name: example.com  
IP address: a numerical network address

**[NARRATION]**

So how does the browser connect a name we can remember with an address computers can use?

This is where DNS comes in.

DNS stands for Domain Name System.

You can think of it as a distributed directory for domain names.

When your device needs to find a domain, it asks a DNS resolver for the information.

The resolver may already know the answer because it has it stored in a cache.

If it doesn't, it can follow the DNS hierarchy, asking the appropriate name servers until it finds the information it needs.

Eventually, it can return an IP address for the requested name.

**[VISUAL]** A clean animation:
1. Browser asks: “Where is example.com?”
2. DNS resolver checks its cache.
3. If needed, the resolver follows the DNS hierarchy.
4. An IP address comes back.
5. The browser now has an address to use.

**[HOST]**

And that's the key idea.

DNS does not download the website.

It helps your device find the network address associated with the name.

It's like looking up a person's address before sending them a letter.

**[VISUAL]** The domain name remains on screen. Beside it appears: “Name → Address”.

---

## 03:50 — Finding the server is not the same as reaching it

**[VISUAL]** A map-like animation shows a phone, several network nodes, and a distant server. A line begins to form between them.

**[NARRATION]**

Now the browser has an address.

But knowing where a destination is does not automatically mean you have reached it.

Your data still has to travel across networks.

Your phone may connect through Wi-Fi to a router, or through a mobile network.

From there, data can pass through many other networks and routers before reaching the destination.

The internet is not one giant computer.

It is a network of networks.

**[VISUAL]** Show many independent networks joining together. Highlight routers as small nodes forwarding packets.

**[HOST]**

And the information does not usually travel as one enormous object.

It is carried in smaller units of data.

At the network layer, IP is responsible for addressing and forwarding packets toward their destinations.

Routers examine the information needed to forward those packets onward.

A useful way to picture this is to imagine sending a large book as many numbered pages through a delivery system.

But remember: this is only an analogy. Real network protocols have their own rules, and packets do not always follow one identical route.

**[VISUAL]** A digital message divides into smaller packet-like pieces. They move through different network paths and arrive at a destination.

**[NARRATION]**

This is one reason the internet is so powerful.

It allows separate networks and devices to exchange information without every computer needing a direct physical cable to every other computer.

But our browser still needs a way to communicate with the web server.

---

## 05:05 — Making a connection, and keeping it private

**[VISUAL]** Browser and server appear at opposite ends of the screen. A connection line forms between them.

**[HOST]**

Before the browser asks for the page, it needs a way to communicate with the server.

For many web connections, this involves TCP.

TCP helps two devices establish a connection and provides reliable, ordered delivery of data.

You may have heard of the TCP three-way handshake.

**[ON-SCREEN GRAPHIC]**

Browser → Server: SYN  
Server → Browser: SYN-ACK  
Browser → Server: ACK

**[NARRATION]**

These are the three messages used to establish a TCP connection.

But there is another important part of the address we typed.

**[ON-SCREEN TEXT]**  
https://example.com

**[HOST]**

That little HTTPS matters.

HTTPS is HTTP protected by TLS.

TLS helps authenticate the server and encrypt communication, so other people on the network cannot simply read the contents of the connection.

**[VISUAL]** Show a lock forming around the communication line. Sample readable text transforms into encrypted-looking data.

**[NARRATION]**

The browser and server negotiate the security details, and the browser checks the server's certificate as part of verifying that it is talking to the intended website.

This does not mean the internet becomes magically safe.

It does not guarantee that a website itself is honest, or that the information you send to it is harmless.

It means the connection is protected in important ways while data travels between the browser and the server.

**[HOST]**

One technical detail: not every modern web connection uses TCP.

HTTP/3 uses QUIC, which runs over UDP and includes its own integrated security mechanisms.

We'll keep our main example focused on the common HTTPS-over-TCP path, but the real web has more than one way to establish a connection.

---

## 06:45 — The browser finally asks for the page

**[VISUAL]** A request travels from the browser to the server.

**[ON-SCREEN GRAPHIC]**

Browser: “GET /”  
Server: “Here is the response.”

**[HOST]**

Now the browser can finally ask for something.

The main language used for this conversation is HTTP.

HTTP stands for Hypertext Transfer Protocol.

In simple terms, it defines how a client—usually your browser—requests resources and how a server responds.

For example, the browser might send a GET request asking for the main page.

**[VISUAL]** Show a simplified request card:

GET /  
Host: example.com

**[NARRATION]**

The server receives the request.

But what exactly is a server?

A server is not necessarily a mysterious machine in a dark room.

It is a computer or software system that provides a service to other computers.

For a website, the server may return a file that already exists.

Or it may run an application, retrieve information from a database, and create a response specifically for this request.

And in many real websites, the request may pass through other systems first—such as a content delivery network, a reverse proxy, or a load balancer.

So the computer that first receives your request may not be the same machine that stores every piece of the website.

**[VISUAL]** Show a request moving through:
Browser → Edge/CDN or proxy (optional) → Application server → Database (if needed) → Response.

**[NARRATION]**

Eventually, the browser receives an HTTP response.

It includes a status code and other information, along with the requested resource when the request succeeds.

You may have seen one of these numbers before.

**[ON-SCREEN TEXT]**

- 200 — OK
- 301 — Redirect
- 403 — Forbidden
- 404 — Not Found
- 500 — Internal Server Error

**[HOST]**

A 404 error does not mean the entire internet is broken.

It usually means the server could not find the requested resource.

And a 500 error tells us that something went wrong on the server side.

These small numbers are messages that help different parts of the web understand what happened.

---

## 08:25 — The page arrives, but the work is not over

**[VISUAL]** The browser receives an HTML document. It opens like a file and reveals references to CSS, JavaScript, and images.

**[NARRATION]**

The browser has received the first response.

But a modern webpage often needs more than one file.

The HTML may refer to a stylesheet.

The stylesheet may refer to fonts and images.

The HTML may also refer to JavaScript files that make the page interactive.

So the browser reads the document and discovers that it needs more resources.

It sends additional requests.

And those resources may come from different servers or domains.

**[VISUAL]** Show a simple network of requests:
HTML → CSS  
HTML → JavaScript  
HTML → Image  
CSS → Font

**[HOST]**

Now the browser has to turn all of this information into something visible.

First, it parses the HTML and builds a structure of the page called the DOM—the Document Object Model.

Then it processes the CSS and works out how the elements should look.

The browser calculates where things belong on the screen.

This includes layout.

Then it paints the pixels and composites the different layers into the final image you see.

**[VISUAL]** Animate:
HTML → DOM tree  
CSS → Styles  
DOM + Styles → Layout → Paint → Screen

**[NARRATION]**

JavaScript can also run during this process.

It can change the page, respond to clicks, load more data, or update what you see.

And the browser may repeat parts of this work whenever the page changes.

**[HOST]**

So when you see a website appear, you are not looking at a picture that was simply sent to your phone.

You are looking at the result of a browser interpreting documents, applying styles, running code, and drawing the interface.

That is a lot of work for one press of Enter.

---

## 09:55 — What if the page loads instantly?

**[VISUAL]** Reload a page. Then show a second load appearing faster. A cache icon appears.

**[HOST]**

But you may have noticed something.

Sometimes a website loads much faster the second time.

Why?

Because your browser and other parts of the network can remember useful information.

This is called caching.

For example, a browser may keep a copy of an image, stylesheet, or other resource.

DNS information can also be cached.

So the next time you visit, the browser may not need to repeat every step in exactly the same way.

**[VISUAL]** First visit: many requests. Second visit: some resources come from cache.

**[NARRATION]**

Caching saves time and reduces unnecessary data transfers.

But it also explains why sometimes you may see an older version of a page, or why clearing the cache can help when a website behaves strangely.

The web is designed to reuse information when it makes sense.

---

## 10:40 — The bigger picture

**[VISUAL]** Return to the original phone. Pull the camera back to reveal a globe connected by network lines. Gradually remove the labels until only the phone and the website remain.

**[NARRATION]**

Let's go back to where we started.

One person opens a browser.

They type a name.

They press Enter.

And a website appears.

But behind that simple moment, many different systems have worked together.

DNS helps find an address.

Networks carry data.

Routers forward packets.

Protocols make communication possible.

TLS helps protect the connection.

HTTP carries requests and responses.

Servers provide resources.

And the browser turns those resources into the page on your screen.

**[HOST / ON CAMERA]**

And perhaps the most interesting part is this:

The internet is not a single place.

It is not one building, one company, or one giant computer.

It is a collection of connected networks, devices, standards, and services that can communicate with one another.

The web is one of the things we build on top of that infrastructure.

And every time you open a website, you are using that enormous system without having to think about it.

**[PAUSE]**

The next time a page loads, remember: your browser did not simply open a window.

It started a conversation with the rest of the world.

**[VISUAL]** Fade to the ETC logo.

**[ON-SCREEN TEXT]**

ETC  
Complex ideas. Clear explanations. Original stories.

**[HOST / VOICEOVER]**

If you enjoyed exploring what happens behind an ordinary click, subscribe to ETC.

In the next episode, we'll follow another mystery hiding in plain sight:

How does a few lines of code become a program that a computer can actually run?

See you there.

---

# PRODUCTION NOTES

## Required visuals

- A real browser demonstration: type a URL and load a page.
- A clean breakdown of a website into HTML, CSS, JavaScript, and assets.
- Domain name → DNS resolver → IP address animation.
- A simple network map with routers and packets.
- A TCP three-way handshake animation.
- A TLS/HTTPS visual showing an encrypted connection.
- A simplified HTTP request and response.
- An optional CDN/proxy/application/database diagram.
- DOM → styles → layout → paint animation.
- A caching comparison: first visit versus repeat visit.

## Practical demonstrations to record

1. Open browser developer tools and show the Network tab while loading a page.
2. Show the main document request and a few image, CSS, and JavaScript requests.
3. Show a response status such as 200 or 404 using a safe test page.
4. Show a page reload and explain that cached resources may be reused.

Do not expose private browsing data, personal accounts, cookies, authentication tokens, or private network details in screen recordings.

## Editing and pacing notes

- Let the opening question breathe. Do not rush the first 20 seconds.
- Use motion graphics only when they clarify a process.
- Keep on-screen labels short: one concept at a time.
- Avoid showing paragraphs of definitions.
- Use sound design sparingly: subtle movement for data flow, not constant dramatic effects.
- Return to the real browser demonstration between abstract explanations to keep the story grounded.
- Do not imply every website uses the exact same infrastructure or follows one identical connection path.
- The main script uses HTTPS over TCP as its teaching example, then briefly acknowledges HTTP/3 over QUIC.

## Accuracy notes for the editor

- DNS resolves domain names to records such as IP addresses; it does not carry the website content itself.
- DNS answers may be cached. A full root → TLD → authoritative lookup is not necessarily performed on every visit.
- IP packets are forwarded across networks; avoid claiming every packet always takes the same route.
- TCP is common, but HTTP/3 uses QUIC over UDP.
- HTTPS is HTTP over a secure transport using TLS; avoid saying the padlock proves a site is trustworthy.
- A server may serve static files or generate responses dynamically. A website may use CDNs, reverse proxies, load balancers, and databases, but not every site uses all of them.
- A browser may fetch multiple resources after receiving the HTML. Rendering involves parsing, style calculation, layout, paint, and compositing; do not portray it as one universal rigid sequence for every browser.
- Caching can occur at several layers, not just inside the browser.

## Research references

1. MDN Web Docs — How the web works  
   https://developer.mozilla.org/en-US/docs/Learn_web_development/Getting_started/Web_standards/How_the_web_works

2. MDN Web Docs — How browsers work  
   https://developer.mozilla.org/en-US/docs/Web/Performance/Guides/How_browsers_work

3. MDN Web Docs — Overview of HTTP  
   https://developer.mozilla.org/en-US/docs/Web/HTTP/Guides/Overview

4. Cloudflare Learning Center — What is DNS?  
   https://www.cloudflare.com/en-in/learning/dns/what-is-dns/

These references support the technical explanations. Before publication, verify any additional historical claims, protocol details, and screenshots against current primary documentation.

---

**ETC production principle:** Make the hidden process visible. Explain every difficult word. Never trade accuracy for simplicity.
