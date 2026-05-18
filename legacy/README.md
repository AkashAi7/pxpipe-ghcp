# legacy/

Reference implementations kept around as a parity oracle during the
TypeScript port. Not part of the published npm package.

## python/

The original working Python proxy (commit `5212f71`) plus its companion
scripts:

| file                 | role                                                     |
| -------------------- | -------------------------------------------------------- |
| `proxy.py`           | the proxy itself — `python3 proxy.py` to run             |
| `gen_atlas.py`       | pre-bakes Menlo glyph atlas (originally for the Zig CLI) |
| `diff_render.py`     | byte-compare PNGs from two renderers                     |
| `diff_transform.py`  | byte-compare transformed request bodies                  |
| `visual_compare.py`  | side-by-side PNG diff viewer                             |
| `install.js`         | old postinstall (verified Python + Pillow)               |
| `cli.js`             | old npm `bin` shim that spawned `proxy.py`               |

### Running the legacy proxy

```bash
cd legacy/python
python3 proxy.py --port 47821
```

Requires Python 3.8+ and `Pillow` + `httpx` (`pip install Pillow httpx`).

### Why it's still here

Until the TypeScript port reaches output parity (byte-for-byte
transformed requests, visually identical PNGs), this is the reference
implementation we diff against. Once parity is verified end-to-end,
the entire `legacy/` directory will be removed in a single commit.
