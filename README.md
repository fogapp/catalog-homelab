# fog-catalog

Self-hosted apps packaged for [fog](https://github.com/fogapp/fog): the arr
stack, media servers, Immich, Paperless, Gitea and more. Every fog reads this
catalog out of the box, and its apps install directly. That trust comes from
fog listing this repository by URL; nothing in the repository grants it.

This is a `fog-catalog/1` catalog. The format is fog's
`docs/catalog-contract.md`.

```
catalog.yaml          name, what's featured, display order
apps/<id>/app.yaml    one app: spec, install options, listing, footprint
apps/<id>/*.svg|webp  its logo and screenshots
```

## Adding or changing an app

1. Add or edit `apps/<id>/app.yaml`, with its artwork beside it.
2. List it in `catalog.yaml`'s `order` where it belongs in its category, and
   in `featured` if a new fog should show it before anyone chooses.
3. Check it: with this repository and `fog-apps` checked out beside fog,
   `go test ./internal/catalog` in fog loads both catalogs and fails on any
   problem. That covers the spec, options, companions, artwork and
   footprint, plus tests specific to some apps, such as SABnzbd's init
   hooks.
4. Push. Fogs fetch the catalog every six hours, or straight away from
   Settings › App store › Fetch now.

Each release of fog also embeds a copy of this catalog as committed
(`scripts/catalog-seed.sh` in fog), which a fog reads until its first fetch.

## License

Copyright (c) 2026 Matthew Werner

The catalog (`catalog.yaml`, each app's `app.yaml`, and this README) is under
the MIT License; see [LICENSE](LICENSE). Copy it, adapt it, and publish
catalogs of your own from it.

The license doesn't cover the apps' logos, screenshots and names. They
belong to their own projects and are here only to identify them; each app
is under its own license, which its entry names (`license:`). The Fog name
and logo are trademarks under [TRADEMARKS.md](TRADEMARKS.md).

Issues are welcome; pull requests aren't accepted for now. See
[CONTRIBUTING.md](CONTRIBUTING.md).
