<p align="center"><img src ="https://plextogether.com/img/new/logo-long-dark.png" /></p>

Plex Together is a tool to sync [Plex](http://plex.tv) content across multiple players in multiple locations. 

Utilising [Vue.js](https://vuejs.org/) and Webpack, Plex Together has been rewritten and brought to the browser. While we run a live version available at [plextogether.com](http://app.plextogether.com), the project can be built and deployed completely seperate from plextogether.com. We also provide a handful of public Plex Together Server instances that everyone is free to use. 

[Live version](http://app.plextogether.com)


## How it works
Plex Together aims to keep multiple viewing sessions in sync regardless of whether the clients are in the same room or across the globe. To do this Plex Together utilizes a middle-man server to communicate between each of Plex Together clients. Users choose their Plex client, decide on a Plex Together Server and Room name and join up. Your friends/family can do the same. Whoever joins the room first will become the host. 

The host has complete control over a room. Commands they send to their client will be sent through to other people in the room (Play, Pause, Seek etc). If the host starts playing something different, Plex Together will search all of your available Plex Media Servers for an equiavalent copy, even if it is not from the same Plex Media Server as the Host.  

## Features
* Syncing between Plex Clients over the Internet
* Settings to tune Plex Together to your environment
	* Client Polling Interval - Sets how frequently Plex Together will poll the client for new information. 
	* Sync Flexability - Sets the acceptable distance away from the host in milliseconds.
	* Sync method:
		* Clean seek - Seeks straight to where the host is.
		* Skip ahead - Seeks 10 seconds ahead, pauses and then resumes 10 seconds later.
* Autoplay content 
	* Plex Together will automatically search all of your available Plex Media Servers for content that is similar to the Host.
* Metadata fetching from Plex Media Server
* Chat to others in your room
* Password locked rooms
* Movies and TV Shows (Music not supported)
## FAQ
* _I have to login to Plex.tv on the site, how come?_
	* Plex Together uses your Plex account to fetch details about your Plex Clients and Media Servers to use within the app. While having to enter your username and password is not optimal it is the only real option until Plex implements a public OAUTH scheme.
	* (Update) Pin login method is currently in the dev branch
* _Won't you have access to my username, password and Plex account?_
	* All of your details are stored client side (in your browser). Absolutely none of your **confidential** data is sent to our server. You can verify this by inspecting the Network tab within Chrome developer tools or if you would like you can deploy Plex Together yourself - read the 'Building and deploying' section below.
* _What is sent then?_
	* When you've connected to a Plex Together room, a few details are sent back and forth to the Plex Together Server to enable syncing. The data sent contains the following:
		* Plex Username
		* Plex User Thumbnail URL
		* Content playing title (Eg. Lord of the Rings: The Fellowship of the Ring)
		* Current timestamp (Eg. 00:35:02)
		* Maximum timestamp (Eg. 03:48:18)
		* Playerstate (Eg. paused, stopped, playing)
		* Client response time (Ping time between you and your Plex Client)
* _What about the public server provided by Plex Together? Is my data safe?_
	* We log absolutely nothing to disk. Data is kept within the room instance until you leave or the server restarts. We have enabled SSL on our public servers but if privacy is a concern for you we strongly suggest running your own server. For more details read the 'Building and Deploying' section below.

* _Speaking of SSL, why isn't the site served over HTTPS?_
 	* While we would love to run the Plex Together application over HTTPS, doing so forces modern browsers in to blocking all HTTP connections. This effectively stops all communication with Plex Clients which are all HTTP. 
## Screenshots

Head to the [website](http://plextogether.com/screenshots)

## Supported Plex Clients
Theoretically, all Plex Clients that implement the Plex Client Protocol will work. As some clients have this implemented slightly differently, compability with Plex Together may vary. If you have access to one of the untested clients please let us know so we can update our list below.

Some low powered clients may be hard to achieve a perfect sync with (for example: Raspberry Pi clients).
### Supported

#### Computer
* Plex Media Player 
* Plex Home Theater
* OpenPHT

#### Streaming Devices
* Apple TV
* Rasplex
* Roku

#### Mobile
* iOS (iPhone & iPad)
* Android

### Tested and Unsupported
* Plex Web Player (Chrome/Safari)
	* Relies on a local Plex Media Server to proxy commands. May work if you have a local PMS instance but issues may arise. 
	
### Untested 

#### Computer
* Windows 10 App 
* Kodi

#### Streaming Devices
* Amazon Fire TV  
* Android TV
* Chromecast
* TiVo

#### TVs and Consoles		
* Xbox One
* Xbox 360
* PS3
* PS4
* Nvidia Shield
* Smart TV

#### Mobile
* Windows Phone

## Contributing
Please use the Issue tracker here on Github for Issues & Feature requests. We'll gladly merge Pull requests if you're keen to get hands on with the development. 


## Building and deploying

### Building the app:

* Make sure you have Node v6+ installed
 
	*  ``git clone https://github.com/samcm/plextogether``
	*  ``cd plextogether``
	*  ``npm install``
	*  ``npm run build``
* When complete, copy the contents of dist/ to the root of your web server.

### Running the server:

* Make sure you have Node v6+ installed
 
	*  ``git clone https://github.com/samcm/plextogether``
	*  ``cd plextogether``	
	*  ``cd server``
	*  ``npm install``
	*  ``node server.js``
* The server will now be listening on all interfaces on port 8089. Note: you may have to port forward if you are behind a router.

## Developing

You need:

* Node v6+
 
	*  ``git clone https://github.com/samcm/plextogether``
	*  ``cd plextogether``
	*  ``npm install``
	*  ``npm run dev``
* Once Webpack has finished compiling, navigate to http://localhost:8080 in your web browser. 
	* Hot reload is enabled
	* Suggested to install [Vue.js Devtools](https://chrome.google.com/webstore/detail/vuejs-devtools/nhdogjmejiglipccpnnnanhbledajbpd?hl=en)


## Issues
If you run in to any issues:
* Raise an Issue here on Github. Try to be as detailed as possible by including details such as:
	* Operating System
		* Web Browser name and version
	* Plex Media Server details
		* Version
		* Operating System
		* Location (Local/Remote)
	* Plex Client details
		* Name
		* Version
		* Network connection (Wired/Wifi)
		* Platform

* Join the [Discord Server](https://discord.gg/Cp9RPSJ) and raise your issue.


## Contributors
[samcm](https://twitter.com/durksau) - Developer

[pureMidi](https://twitter.com/midnitegc) - User Interface

[Brandz](https://twitter.com/homebrandz) - Design

[TheGrimmChester](https://github.com/TheGrimmChester) - Developer/Tester

kg6jay - Tester

## Contact
[Discord Server](https://discord.gg/Cp9RPSJ)

Twitter:
[Plex Together](https://twitter.com/plextogether)

## License

Plex Together is licensed under MIT License. See the ``LICENSE.txt`` file.
Plex Together is in no way affiliated with Plex Inc.