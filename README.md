
create the 

# ajimaru QR Order + POS

A lightweight static restaurant ordering demo built with HTML5, Bootstrap 5, and vanilla JavaScript.

## Views

| View | File |
|---|---|
| Customer ordering | `index.html?table=<1-40>` (e.g. `index.html?table=3`) |
| Single-table QR sign | `table1-40-qr.html` |
| QR sheet, tables 1-40 | `tables-1-to-40-qr.html` |
| Kitchen Display System | `kitchen.html` |
| Register / POS (checkout) | `register.html` |

## Run

Customers scan the table's QR code, which opens the Customer view with that table number.

To try it locally, open the files directly in a browser or serve the folder with any static server. For the smoothest multi-tab behavior, use a local server:

    python -m http.server 8080

Then open `http://localhost:8080/index.html?table=3`.

Open Kitchen and Register in separate tabs. Orders and status changes sync through `BroadcastChannel` and `localStorage`. This is a front-end demo store, not a production multi-device backend.

## Data model

`data/schema.json` defines menu items, orders, and payments as JSON Schema. The example menu (including item photos) lives in `js/data.js`. In production, replace `js/store.js` with API calls and server-side persistence and authentication.

## Demo flow

1. **Customer:** open a URL with a table number, add menu items, and send the order. A kitchen ticket prints and the order appears in Register (checkout).
2. **Kitchen:** start cooking, then mark the ticket ready.
3. **Customer:** the status banner updates to *Preparing*, then *Served*.
4. **Register:** select the table, apply a discount, choose a payment method, close the table, and print the receipt.
