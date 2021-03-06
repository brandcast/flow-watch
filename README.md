# flow-watch

A simple file watcher that clears the console and runs flow on each change.  Currently tested on OS X -- I don't know
if it works on Linux or Windows.  Works with `flow` on your path or `flow-bin` installed as a peer dependency.

## Usage

```
npm install --save-dev flow-watch
```

Add a script to your `package.json`:

```json
{
  "scripts": {
    "flow:watch": "flow-watch"
  }
}
```

## Configuration

`flow-watch` uses [`nodemon`](https://github.com/remy/nodemon) and accepts any command-line options that `nodemon` does.
If you provide no arguments, it uses the following defaults:
```
--ignore node_modules/ --watch *.js --watch *.jsx --watch *.js.flow --watch .flowconfig
```

By default, the watcher will clear the console between each change. If you wish to override this behavior, use the `FLOW_WATCH_NO_CLEAR_CONSOLE` env variable. If you choose that approach, you may also want to silent the `[nodemon]` messages in the console, which you can do with the `--quiet` flag (or `-q`). Putting it all together:

```json
{
  "scripts": {
    "flow:watch": "FLOW_WATCH_NO_CLEAR_CONSOLE=1 flow-watch -q"
  }
}
```
