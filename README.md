<p align="center">
  <img width="200" src="https://open-wc.org/hero.png"></img>
</p>

## Web components Workshop

[![Built with open-wc recommendations](https://img.shields.io/badge/built%20with-open--wc-blue.svg)](https://github.com/open-wc)

## Prerequisites
We're going to learn a bit about how to build and deploy Lit based web components using vercel and open-wc. To participate, do the following:

- Get a github.com account - install https://desktop.github.com or have git installed on machine
- Get a vercel.com account - and connect it to your github.com account
- Install VSCode - https://code.visualstudio.com/
- Install Chrome or Firefox (Safari is less ideal for console debugging)
- Install the following VSCode extensions - `lit-html` and `lit-plugin`
- Install the latest LTS version of Node (20.9.0 as of writing) - https://nodejs.org/

This repo was made using Open-wc tooling. You can learn more about open-wc and how it can help you build Lit based web components at https://open-wc.org/ or run `npm init @open-wc` after installing node/npm in order to build a new web component based application like the one in this workshop!

## Workshop tasks
- Let's check out Lit.dev and a component example to understand what we'll be working on
  - Full component - https://lit.dev/playground/#sample=examples/full-component
- Create a new repo using this one as the template. Name your repo `wc-workshop`.
- Clone this code locally on your machine
- Open the code in VSCode, and open a terminal in VSCode at the project root
- Run `npm install` to install dependencies
- Run `npm run start` to begin working on the code. You now have a live running web development environment where changes to the code in the repo will automatically reload the website.

### Optimal working setup
- Open VSCode in a 50% wide window
- Open live updating environment in browser
- Right click anywhere on website running in browser and hit Inspect
- Keep the console data open below your site running so you can see errors as they happen
- Edit code in VSCode and hit Save (Control + S) to see update in browser

## Background on my work and worldview
- With the right tools, you can build anything - https://www.youtube.com/watch?v=G5yEgFIxzl0
- HAXTheWeb Youtube channel - https://www.youtube.com/@haxtheweb

## Play with my work to understand why this is relevant
Web components are used by companies big and small and are the future of the web. I would argue that they will eat the web as we knew it but that's a story for a different time. For now, let's play
- https://hax.psu.edu (production) - HAXcms + Microsoft Login = micro-site factory
- https://hax.cloud (experimental)
- https://haxapi.vercel.app/?path=/story/about-getting-started--using-penn-state-cdn use our assets anywhere
- https://github.com/elmsln/haxcms - platform that hax.psu is running if you want to self host later on

## What you have when you get started with this repo
- Open-wc boilerplate + vercel API structure + my modifications
- A search box that when typing you see image result data from NASA image search API

### What we'll build on top of this
- Modifying the data to output a listing of images instead of text names
- Let's create a new component called `nasa-image` in a file called `src/nasa-image.js`
```js
import { LitElement, html, css } from "lit";

export class NasaImage extends LitElement {

  constructor() {
    super();
  }

  static get properties() {
    return {

    };
  }

  static get styles() {
    return [css``];
  }

  render() {
    return html`
    <div>

    </div>
    `;
  }
  static get tag() {
    return "nasa-image";
  }
}
customElements.define(NasaImage.tag, NasaImage);
```
- Let's reference this new tag for use in our `wc-workshop` app
- Let's add support for image source via a property
- Let's add support for alt data
- Let's add support for a visible title
- Let's do some minor CSS styling
- Let's add CSS variables for height / width
- Let's add support for lazy loading the image (Google search)

### JSON output
- Now let's look through the JSON Response from NASA to see how we can wire this all up
- https://images-api.nasa.gov/search?q=apollo%2011&media_type=image as an example
- Where's the 'image' we'll render?
- How would we obtain "alt" data?
- What are some fields we can add on our `nasa-image` element to match the API?

### Meme's we love them, especially when we didn't make them
Let's wire our data up to someone else's (mine) tag: meme-maker
- Read docs on how to use and install https://haxapi.vercel.app/?path=/story/media-memes--basic-meme
- Install the element
- Implement the element

### Bringing in a carousel from Shoelace
Let's wire up a different library called shoelace. https://shoelace.style/components/carousel to put nasa results into a carousel
- install the element library `npm install @shoelace-style/shoelace`
- and add support into our workshop app
```js
import "@shoelace-style/shoelace/dist/components/carousel/carousel.js";
import "@shoelace-style/shoelace/dist/components/carousel-item/carousel-item.js";
```
- Read the docs for carousel and see if you can figure out how to wire it into the template to modify the work we've done!

## I want more
https://github.com/elmsln/lrnwebcomponents is a massive monorepo of elements that the HAX team has been working on for years to transform education, publishing and the web. I am always looking for students to do independent study work to learn how to build advanced web components by contributing to our efforts. One brick at a time we will build a better world.

## Tooling configs

For most of the tools, the configuration is in the `package.json` to reduce the amount of files in your project.

If you customize the configuration a lot, you can consider moving them to individual files.

## Scripts

- `start` runs your app for development, reloading on file changes
- `start:build` runs your app after it has been built using the build command
- `build` builds your app and outputs it in your `dist` directory
- `test` runs your test suite with Web Test Runner
- `lint` runs the linter for your project
- `format` fixes linting and formatting errors
