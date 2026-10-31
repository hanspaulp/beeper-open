# beeper-open

One static page that opens a WhatsApp chat in Beeper Desktop:
`https://hanspaulp.github.io/beeper-open/#channel=whatsapp&chat=<chat id>`.

The GTM cockpit (saunabox-hermes `garden/gtm-cockpit`) links its WhatsApp buttons here. A Garden widget
opens only https links on a site other than sauna.garden, so the cockpit cannot hand the browser a
`beeper://` link itself.

- The chat id travels after the `#`, so it never reaches GitHub's servers.
- Only a WhatsApp chat id of the two shapes Beeper uses is accepted: `!<id>:beeper.local` (the +39
  account) and `!<id>:<suffix>.local-whatsapp.localhost` (the +1 number's local bridge, which Beeper
  finds only with `accountID=local-whatsapp_<suffix>`). Anything else shows "This is not a Beeper chat link."
- The page sends the browser to `beeper://select-thread/bridge-whatsapp/<chat id>[?accountID=...]`;
  the browser asks once whether to open Beeper Desktop. A link on the page does the same if the
  automatic hand-off is blocked.

The rule is the same as `beeperUrl` in the cockpit's `server.js`; change both together.
