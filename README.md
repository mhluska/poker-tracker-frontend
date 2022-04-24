## Poker Tracker

Frontend for a Google Sheet that I use to track my poker sessions. To better
understand how React works under the hood, I built my own basic React-like
library to power this.

Motivation: I used to type session data into a note on my phone and then
transfer it to the sheet later on my laptop. This was error-prone and got tiring
quickly.

### Develop

```sh
nvm use $(cat .nvmrc)
npm install
npm start
```

### Deploy

```sh
npm run build
npm run deploy
```

### Features

#### Start Session

Creates a poker session with the current time prefilled. Asks for the casino
name, stake and max buyin. Max buyin is prefilled if entered previously. The URL
is updated and session data is stored in localStorage so the page can be
refreshed.

#### Rebuy

Asks for the amount to rebuy. Has a button for rebuying the maximum
automatically.

#### End Session

Asks for cash out amount and prefills the end time with the current time. Asks
for an admin password which can be saved for reuse later. A request is sent to a
backend service which adds a row to the sheet after authenticating.

### Todo

- Avoid calling the `createVirtualElement()` functions until reconcile happens.
  In other words, `VirtualElement.children` should actually be an array of
  functions that returns the child elements when called. A function component
  should return `{ type: string, props: object, children: Function[] }`
- Nest `children` under `props`
- Treat text nodes as just another virtual element
- Use event binding instead of global `handleInput`
- Auto render on appState change
- Dropdown for selecting casinos
- Rerender on route change
- Input focus
- Add assets (og:image, favicon.icom, icon.svg, site.webmanifest, icon.png)
- Add opt-in notifications for when the session should be ended (x hours later)