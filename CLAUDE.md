# ioBroker.vw-connect (owner's fork)

Fork of TA2k/ioBroker.vw-connect (MIT, keep the attribution), based on upstream 0.10.1. Owner's car: VW ID.4, data via the
EU Data Act portal (15-min data request). Used by ioBroker.energie (car SOC) and the SmartView car tile.

## Changes in this fork (0.10.2-beta.0)

- `lib/euDataAct.js`: VW moved the portal to `eu-data-act.vwgroup-datahub.com` (Nov 2026). The OIDC redirect_uri on the old
  host still works, but the callback ends on the new host and sets `access_token` there -> "Login did not complete (ended at
  https://eu-data-act.vwgroup-datahub.com/de/en/user.html)". `PORTAL_ORIGINS` (old + new), `loginCompletionRedirect` accepts
  both, `this.base` = origin the login ended on, used for all portal API calls. Unit test in test/unit/euDataActLogin.test.js.
  Not yet confirmed on the owner's ioBroker.

## Conventions

- Code and comments in English, like upstream. Bump `version` in package.json and io-package.json + news.
- Install: `iobroker url https://github.com/andreaslampl/ioBroker.vw-connect`.
- `npx mocha test/unit --exit` before committing.
- Keep changes small so they can go upstream as a pull request; back to upstream once it has the fix.
