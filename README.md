# Yet Another Hacker News Reader - [🍠 *yahn*](https://yahn.vercel.app)

![demo](/public/img/demo.jpg)

I like browsing Hacker News, but I want a more *distraction-free* interface.

I also want to learn [Svelte](https://svelte.dev/).

So I built [_**yahn**_](https://yahn.vercel.app) to achieve both.

## Features
-  **Minimalist** design optimized for efficiency, functionality, and ease of use
- Human-oriented (a.k.a. won't burn your eyes at night) **dark-mode** design
- Available on **any OS**: iOS, Android, PC, macOS, Linux, etc.

## Tech stack
- [Svelte](https://svelte.dev): minimalist & optimized front-end compiler
- [Node.js](https://nodejs.org/): javascript backend
- [Tailwind.css](https://tailwindcss.com/): awesome CSS framework
- [Vercel](https://vercel.com): deployment PaaS 
- [Figma](https://figma.com): prototyping, UI & logo design

<p align="center"> Made with ❤️ by Vincent Wu.</p>


# Development
## Installation
To install the app you would first need `Node.js`, `npm` and `git`. Then you need to clone the repository:

	git clone https://github.com/Cveinnt/yahn.git

Next, navigate to the local repository

    cd yahn

And install all the dependencies:

	npm install


## Starting the development server
To run the development server you just need to use

	npm run dev

This should start the server at http://localhost:8080.

You can also start the production server with

	npm run start


## Building the app
To build the optimized JavaScript package you need to run

	npm run build
	
The output will be in the `public` directory ready to be served.
