# rescript-zed

ReScript support for the [Zed](https://zed.dev) editor.

This extension plugs in the following projects:

- [tree-sitter-rescript](https://github.com/rescript-lang/tree-sitter-rescript)
  parser
- [@rescript/language-server](https://www.npmjs.com/package/@rescript/language-server)
  LSP

## Installing the language server

The stable server is the default language server used by this extension. It uses
the pre-v2 versions of `@rescript/language-server`, and the extension installs
and updates that package automatically.

Use `settings.version` when you need to pin a specific npm version. If it is
omitted, Zed installs the latest published stable version.

> [!NOTE]
> The experimental server is the v2 language server published to npm under the
> `dev` tag. Pin the package to the current `dev` version. See the version
> history on
> [npm](https://www.npmjs.com/package/@rescript/language-server?activeTab=versions).

> [!TIP]
> You can install the language server globally with
> `npm i -g @rescript/language-server@dev` and set the binary path.
>
> ```json
> {
>   "lsp": {
>     "rescript-language-server": {
>       "binary": {
>         "path": "rescript-language-server"
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
      // Server configuration for pre-v2 should be passed through initialization_options
      "initialization_options": {
        "extensionConfiguration": {
          "askToStartBuild": false,
        },
      },
      "settings": {
        "version": "1.71.0-next-441959d.0",
        // Server configuration for v2 should be passed through settings.rescript
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

`initialization_options` are passed to the language server (pre-v2) when it is started.
They can be used to configure the language server. See
[extensionConfiguration](https://github.com/rescript-lang/rescript-vscode/blob/441959d1feeaaffc1a589687758b1fbe1f649e72/server/src/config.ts#L5-L29)

## Developing

See [CONTRIBUTING.md](CONTRIBUTING.md) for instructions on how to develop this
extension locally.

## Acknowledgements

This project was originally created by [humaans](https://github.com/humaans/).
We're grateful for their initial work in bringing ReScript support to Zed.
