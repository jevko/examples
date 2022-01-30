# Visual Studio Code settings

An excerpt from [Visual Studio Code JSON configuration](https://code.visualstudio.com/docs/getstarted/settings#_default-settings) encoded in Jevko:

```
editor.quickSuggestions [
  other [true]
  comments [false]
  strings [false]
]
terminal.integrated.wordSeparators [ ()`[`]{}',"``─‘’]
terminal.integrated.scrollback [1000]
remote.extensionKind [
  pub.name [[ui]]
]
git.checkoutType [[local] [remote] [tags]]
git.defaultCloneDirectory [null]
```

JSON equivalent:

```
{
  "editor.quickSuggestions": {
    "other": true,
    "comments": false,
    "strings": false
  },
  "terminal.integrated.wordSeparators": " ()[]{}',\"`─‘’",
  "terminal.integrated.scrollback": 1000,
  "remote.extensionKind": {
    "pub.name": ["ui"]
  },
  "git.checkoutType": ["local", "remote", "tags"],
  "git.defaultCloneDirectory": null
}
```
