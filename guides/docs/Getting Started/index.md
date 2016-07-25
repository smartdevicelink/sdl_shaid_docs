# Installing

#### Node.js & Git

MAIDS is entirely written in javascript and uses Node.js.

Install [Node.js](https://nodejs.org/en/) and [Git](https://git-scm.com/).

## Reference Documentation
You can find the latest reference documentation in the [SDL MAIDS](/docs/sdl-maids/master/overview) section.

## Setup SDL Server

Download or clone the <a href="https://github.com/smartdevicelink/sdl_maids" target="_blank">SDL MAIDS git repository</a>.
```
git clone https://github.com/smartdevicelink/sdl_maids.git
```

Once cloned, navigate to the repository's root directory and use npm to install the server's dependencies.
```
cd sdl_maids && npm install
```

Start the server using npm.
```
npm start
```

Finally, navigate to <a href="http://localhost:3000" target="_blank">localhost:3000</a> in your browser.
