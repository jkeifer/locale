# Locale Extension Specification

- **Title:** Locale
- **Identifier:** <https://stac-extensions.github.io/template/v1.0.0/schema.json>
- **Field Name Prefix:** locale
- **Scope:** Item, Collection
- **Extension [Maturity Classification](https://github.com/radiantearth/stac-spec/tree/master/extensions/README.md#extension-maturity):** Proposal
- **Owner**: @jkeifer

This document explains the Locale Extension to the [SpatioTemporal Asset Catalog](https://github.com/radiantearth/stac-spec) (STAC) specification. Allows specifying properties specific to the local area represented in the item or collection.

- Examples:
  - [Item example](examples/item.json): Shows the basic usage of the extension in a STAC Item
  - [Collection example](examples/collection.json): Shows the basic usage of the extension in a STAC Collection
- [JSON Schema](json-schema/schema.json)
- [Changelog](./CHANGELOG.md)

## Fields

The fields in the table below can be used in these parts of STAC documents:
- [ ] Catalogs
- [x] Collections
- [x] Item Properties (incl. Summaries in Collections)
- [x] Assets (for both Collections and Items, incl. Item Asset Definitions in Collections)
- [ ] Links

| Field Name                | Type    | Description                                            |
| ------------------------- | ------- | ------------------------------------------------------ |
| locale:datetime           | string  | `datetime` in the local timezone.                      |
| locale:start_datetime     | string  | `start_datetime` in the local timezone.                |
| locale:end_datetime       | string  | `end_datetime` in the local timezone.                  |
| locale:tz_offset          | float   | Local timezone offset at `datetime`.                   |
| locale:solar_zenith       | float   | Sun angle relative to the horizon at `datetime`.       |
| locale:start_solar_zenith | float   | Sun angle relative to the horizon at `start_datetime`. |
| locale:end_solar_zenith   | float   | Sun angle relative to the horizon at `end_datetime`.   |

All timestamps MUST be formatted according to RFC 3339, section 5.6.

The timestamps have different meaning depending on where they are used.
If those fields are available in the Item properties, it's referencing to the timestamps valid for of the metadata.
Having those fields in the Item assets refers to the timestamps valid for the actual data linked to in the Asset Object.

All values are assumed to be derived from the item's centroid unless otherwise documented.

## Contributing

All contributions are subject to the
[STAC Specification Code of Conduct](https://github.com/radiantearth/stac-spec/blob/master/CODE_OF_CONDUCT.md).
For contributions, please follow the
[STAC specification contributing guide](https://github.com/radiantearth/stac-spec/blob/master/CONTRIBUTING.md) Instructions
for running tests are copied here for convenience.

### Running tests

The same checks that run as checks on PR's are part of the repository and can be run locally to verify that changes are valid. 
To run tests locally, you'll need `npm`, which is a standard part of any [node.js installation](https://nodejs.org/en/download/).

First you'll need to install everything with npm once. Just navigate to the root of this repository and on 
your command line run:
```bash
npm install
```

Then to check markdown formatting and test the examples against the JSON schema, you can run:
```bash
npm test
```

This will spit out the same texts that you see online, and you can then go and fix your markdown or examples.

If the tests reveal formatting problems with the examples, you can fix them with:
```bash
npm run format-examples
```
