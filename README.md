# Open Tracked Cookie Keeper

_Server tag template for Google Tag Manager (server container)._

Keeps a visitor's tracking cookies (Meta `_fbp` and `_fbc`, Google `_ga` and `FPID`, TikTok `_ttp` and others) alive in browsers that delete them early, such as Safari with ITP. It remembers them in your Open Tracked Data Store under a hash of an identifier you choose, and gives them back when the same visitor returns without them.

## How to use

1. Switch on **Data Store** and **Cookie Keeper** in your Open Tracked dashboard (Container, Power-Ups). Copy the Data Store address and token.
2. Add this tag to your server container and paste the address and token.
3. Set the event data key that holds a stable identifier of the visitor, such as a customer ID.
4. Choose the cookies to keep and how many days, then fire the tag on your events.

## Fields

| Field | Name | What it does |
|---|---|---|
| Data Store address | `apiUrl` | From the Data Store power-up in your Open Tracked dashboard, for example https://app.opentracked.io/api/ds/v1/123. |
| Data Store token | `token` | From the same page. |
| Event data key holding the visitor's identifier | `identifierKey` | A value that stays the same for the visitor for months: a customer ID, or an ID your site keeps. Without it nothing is done. |
| Cookies to keep (comma separated) | `cookieNames` | Any of: _fbp, _fbc, _ga, FPID, _gcl_aw, _gcl_dc, _ttp, ttclid, _os_vid, __kla_id, _scid, li_fat_id, _uetmsclkid, _uetvid, _epik, _pin_unauth. |
| Cookie domain | `domain` | auto uses your site's main domain, which is what every page of the site can read. |
| Keep for (days, at most 400) | `days` |  |

## Privacy

- The visitor is never stored under their identifier: the key is a SHA-256 hash of it.
- Only the cookies you list are read and written, and only from a fixed list of tracking cookies.
- Entries are deleted after the number of days you set (at most 400).

## Permissions

- **Reads event data**: Reads the identifier.
- **Sends HTTP requests**: Only to `https://app.opentracked.io/api/ds/` and `https://app.openserver.digital/api/ds/`.
- **Accesses template storage**: Keeps a short-lived copy of the answer.
- **Reads and sets cookies**: Only the listed tracking cookies.

## Notes

Requires an Open Tracked account. The Data Store must be switched on. Without a stable identifier in the event nothing is stored.

## About Open Tracked

[Open Tracked](https://opentracked.io) is a first-party tracking service: a tagging server on your own domain, an analytics pixel and a CRM. Documentation: https://docs.opentracked.io/google-tag-manager

## License

Apache License 2.0, see [LICENSE](LICENSE).
