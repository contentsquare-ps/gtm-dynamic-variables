# Contentsquare Dynamic Variables Tag for GTM

A Google Tag Manager community template (Web containers) that sends [Dynamic Variables](https://docs.contentsquare.com/en/web/dynamic-variables-tag/) to Contentsquare.

Dynamic Variables let you attach custom key/value data (for example a user tier, a cart value, or an A/B test variant) to a pageview so you can use it to segment and filter in Contentsquare.

## What it does

When the tag fires, it loops over the variables you configured and pushes each one onto the Contentsquare queue (`_uxa`) as:

```js
_uxa.push(["trackDynamicVariable", { key: key, value: value }]);
```

If the Contentsquare tag hasn't loaded yet, the push is queued on `window._uxa` and picked up once it does.

The tag then signals success to GTM.

## Configuration

The tag has a single field, a table of **Dynamic Variables**. Each row defines one variable:

| Column | Required | Description |
|--------|----------|-------------|
| Key | Yes | Name of the variable. Max 512 characters. Must be unique within the table. |
| Value | Yes | Value of the variable. Max 255 characters. GTM variables (for example `{{Page URL}}`) can be used. |
| Type | Yes | `String` or `Number`. |

With type `Number`, the value is converted to a number before it is sent. If it can't be converted (or converts to `0`), it is sent as a string instead. Valid numbers are in the range 0–4294967296.

## Usage

1. Make sure the Contentsquare tracking tag is installed on the site.
2. Add the template to your container (from the Community Template Gallery, or by importing `template.tpl`).
3. Create a new tag with this template and add one or more rows to the Dynamic Variables table.
4. Set a trigger for the tag, so that it fires at the moment the data is available.

### Recommendations and limits

- Define one variable per tag and create separate triggers for each action. If you need to send several variables on the same action, add more rows.
- Up to **40 unique variables per pageview** are recorded. If more are received, only the first 40 unique keys are kept.
- If the same key is sent twice, only the last value is recorded.

## Permissions

The template only needs access to the global `_uxa` (read, write, execute). It doesn't request any other permissions.

## Files

- `template.tpl`: the GTM template (import this into your container).
- `metadata.yaml`: Community Template Gallery metadata.

## Links

- [Contentsquare documentation: Dynamic Variables tag](https://docs.contentsquare.com/en/web/dynamic-variables-tag/)
- [Contentsquare](https://contentsquare.com/)

## License

See [LICENSE](LICENSE).
