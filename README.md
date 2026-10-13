# starline-opener-assets

Data files read at runtime by the Starline Case Opener (a single-file Lua script for Starline / CS2).
The script fetches them through `raw.githubusercontent.com`; nothing here is code.

## case_opener/v1

A slim catalogue index: the CS2 weapon cases and the skins they drop (knives and gloves with their phases).

| file | content |
| - | - |
| `index.txt` | `#slc-index 1`, then per kind: kind, gen, parts, count, sha256 (12 hex), bytes |
| `<kind>.<gen>.<i>.idx` | tab-separated lines, at most 64 KB per part |

`gen` comes from the content hash and is part of the file names, so a cached answer never mixes two versions.
Built by `tools/make_opener_index.py` from item data of the [ByMykel CSGO-API](https://github.com/ByMykel/CSGO-API).
Item images are not stored here; the script loads Valve's official images from the Steam CDN.
