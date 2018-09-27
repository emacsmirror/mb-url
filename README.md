# mb-url - Multiple Backends for Emacs URL package

*Author:* ZHANG Weiyi <dochang@gmail.com><br>

[![MELPA](http://melpa.org/packages/mb-url-badge.svg)](http://melpa.org/#/mb-url)
[![MELPA Stable](http://stable.melpa.org/packages/mb-url-badge.svg)](http://stable.melpa.org/#/mb-url)
[![Build Status](https://travis-ci.org/dochang/mb-url.svg?branch=master)](https://travis-ci.org/dochang/mb-url)

Multiple Backends for URL package.

This package provides several backends for `url-retrieve` &
`url-retrieve-synchronously`, which replace the internal implementation.

The motivation of this package is I can't connect HTTPS url behind proxy
(Related bugs: [#11788][], [#12636][], [#18860][], [msg00756][], [#10][]).

[#11788]: http://debbugs.gnu.org/cgi/bugreport.cgi?bug=11788
[#12636]: http://debbugs.gnu.org/cgi/bugreport.cgi?bug=12636
[#18860]: http://debbugs.gnu.org/cgi/bugreport.cgi?bug=18860
[msg00756]: https://lists.gnu.org/archive/html/help-gnu-emacs/2015-08/msg00756.html
[#10]: http://debbugs.gnu.org/cgi/bugreport.cgi?bug=10

## Installation

`mb-url` is available on [MELPA] and [el-get].

[MELPA]: https://melpa.org/
[el-get]: https://github.com/dimitri/el-get

To install `mb-url` from git repository, clone the repo, then add the repo
dir into `load-path`.

`mb-url` depends on `cl-lib`;  The test code also depends on `s`.

NOTE: the test code requires GNU Emacs 24.4 and above because it uses the
new `nadvice` package.  `mb-url` may support GNU Emacs 24.3 and below but
it's not tested with those versions.

## Backends

Currently only support `url-http`.

### `url-http`

Install `mb-url-http-around-advice` to use `mb-url-http` backends.

```elisp
(advice-add 'url-http :around 'mb-url-http-around-advice)
```

All backend functions receive `(name url buffer default-sentinel)`, return a
process.

`mb-url-http-backend` indicates the current backend.  If the backend is
`nil`, which means no backend, `url-http` will be called.

E.g.,

```elisp
(setq mb-url-http-backend 'mb-url-http-curl)
```

#### [cURL][]

[cURL]: http://curl.haxx.se/

##### `mb-url-http-curl`

cURL backend for `url-http`.

##### `mb-url-http-curl-command`

Executable for cURL command.

#### [HTTPie][]

[HTTPie]: http://httpie.org/

##### `mb-url-http-httpie`

HTTPie backend for `url-http`.

##### `mb-url-http-httpie-command`

Executable for HTTPie command.

## License

GPLv3

## Acknowledgements

https://github.com/nicferrier/curl-url-retrieve


---
Converted from `mb-url.el` by [*el2markdown*](https://github.com/Lindydancer/el2markdown).
