# Compare two CSV exports — free n8n workflow (demo)

Loupe & Lettres — créé avec l'aide de l'IA (created with AI assistance). This repository was published by an AI assistant for the Loupe & Lettres brand.

A free, MIT-licensed n8n workflow that compares two CSV exports on one exact key column (an order ID, an invoice number...) before the result feeds the next step of a workflow. It reports keys missing on either side, changed fields, repeated keys and invalid numeric values. It runs manually, reads text only, adds no node that sends or stores data and needs no account, credential, API or AI model.

## Try it in 2 minutes

1. Import `compare-csv-exports.json` into a fresh n8n workflow.
2. Execute it manually and open the output of `Compare exports`.
3. Compare it with `expected/orders.json` (written by hand from `fixtures/orders-a.csv` and `fixtures/orders-b.csv`): 4 matched keys (1 identical, 3 changed), `SHOP-104` missing in B, `SHOP-105` missing in A, one repeated key on each side, one invalid number.

## Use your own files

Replace the object returned by the `Example inputs` Code node: `key` (key column name), `csvA` and `csvB` (the complete CSV texts, not file names), `delimiter` (default `,`) and optionally `numericFields` (columns compared as plain decimals, so `10` equals `10.00`).

## Rules, stated plainly

- Keys are matched exactly after trimming spaces; case matters. Only the first row of a repeated key is compared; every repeat is listed.
- An invalid file (missing key column, empty key, wrong row width, unclosed quote, duplicate header) stops the run with a message naming the file and the row. No partial result is returned.
- Limits: 1,000,000 characters and 10,000 data rows per file.
- A difference is a review hint, not proof of an error. Not accounting or tax advice.
- Tested by command-line import and execution in n8n 2.14.2. Not tested: interface import, n8n Cloud, other n8n versions, real exports from any system.
- Your n8n instance may keep inputs and outputs in its execution history; keep your first run fictional.

## More

- Product page (free, pay-what-you-want): https://loupeetlettres.gumroad.com/l/oefple
- Paid pack of administrative n8n workflows for freelancers (French): https://loupeetlettres.gumroad.com/l/ynqrgw

MIT license (see `LICENSE.txt`). No endorsement by n8n is claimed.
