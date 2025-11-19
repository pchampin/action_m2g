# action_m2g

An action to run [minutes_to_github](https://github.com/pchampin/minutes_to_gh) on github-hosted minutes.

## Example

```
name: Minutes 2 Github

on:
  push:
    branches:
      - main
    paths:
      - '**.html'

jobs:
  minutes_to_gh:
    runs-on: ubuntu-latest

    steps:
    - uses: pchampin/action_m2g@v1
      with:
        minutes-url-base: "https://jdoe.github.io/my_repo/minutes"
        minutes-repo-path: "minutes"
        m2g-token: ${{ secrets.M2G_TOKEN }}
        m2g-channel: pmwg
        m2g-group: wg/pm
        m2g-transcript: "true"
```

## Parameters

* `minutes-url-base`:
  + Base URL of the minutes (without trailing slash)
  + required
* `minutes-repo-path`:
  + Relative path of the minutes in the repository (without trailing or leading slash)
  + required
* `m2g-token`:
  + Github token usable by minutes_to_github
  + required
* `m2g-channel`:
  + IRC channel (without leading hash, e.g. `pmwg`)
  + required
* `m2g-group`:
  + W3C group (e.g. `wg/pm`)
  + optional (defaults to `wg/{m2g-channel}`)
* `m2g-transcript`:
  + indicates whether the comment on github should include a transcript of the minutes (should be `true` or `false`)
  + optional (defaults to `false`)
* `m2g-log-level`:
  + the verbosity of logging for m2g
  + optional (defaults to `info`)
* `m2g-extra-options`:
  + additional options to pass to m2g
  + optional

