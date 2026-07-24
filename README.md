# rescript-zed

ReScript support for the [Zed](https://zed.dev) editor.

This extension plugs in the following projects:

- [tree-sitter-rescript](https://github.com/rescript-lang/tree-sitter-rescript)
  parser
- [@rescript/language-server](https://www.npmjs.com/package/@rescript/language-server)
  LSP

## Language Server

The stable server is used by default. It is provided by the
`@rescript/language-server` package, which the extension installs and updates
automatically.

Use `settings.version` to pin a specific npm version. If it is omitted, Zed
installs the latest published stable version.

> [!TIP] To test the experimental language server (ReScript v13), use the
> `rescript lsp` subcommand included with the compiler. Set the binary path and
> arguments as follows:
>
> ```json
> {
>   "lsp": {
>     "rescript-language-server": {
>       "binary": {
>         "path": "node_modules/.bin/rescript",
>         "arguments": ["lsp", "--stdio"]
>       }
>     }
>   }
> }
> ```

### Settings

```jsonc
{
  "lsp": {
    "rescript-language-server": {
      // Pass stable language server configuration through initialization_options
      // See https://github.com/rescript-lang/rescript-vscode/blob/441959d1feeaaffc1a589687758b1fbe1f649e72/server/src/config.ts#L5-L29
      "initialization_options": {
        "extensionConfiguration": {
          "askToStartBuild": false,
        },
      },
      "settings": {
        "version": "1.71.0-next-441959d.0",
        // Pass experimental language server configuration through settings.rescript
        "rescript": {
          "hover": {
            "supportMarkdownLinks": true,
          },
        },
      },
    },
  },
}
```

## Developing

See [CONTRIBUTING.md](CONTRIBUTING.md) for instructions on how to develop this
extension locally.

## Acknowledgements

This project was originally created by [humaans](https://github.com/humaans/).
We're grateful for their initial work in bringing ReScript support to Zed.
