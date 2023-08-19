[![Crates.io][crates-badge]][crates-url]
[![Docs.rs][docs-badge]][docs-url]
[![MIT License][license-mit-badge]][license-mit-url]
[![Apache 2.0 License][license-apache-badge]][license-apache-url]
[![Build Status][actions-badge]][actions-url]

[crates-badge]: https://img.shields.io/crates/v/browserjs.svg
[crates-url]: https://crates.io/crates/browserjs
[docs-badge]: https://img.shields.io/docsrs/browserjs/latest
[docs-url]: https://docs.rs/browserjs/latest/browserjs/index.html
[license-mit-badge]: https://img.shields.io/badge/license-MIT-blue.svg
[license-mit-url]: https://github.com/plabayo/browserjs/blob/main/LICENSE-MIT
[license-apache-badge]: https://img.shields.io/badge/license-APACHE-blue.svg
[license-apache-url]: https://github.com/plabayo/browserjs/blob/main/LICENSE-APACHE
[actions-badge]: https://github.com/plabayo/browserjs/workflows/CI/badge.svg
[actions-url]: https://github.com/plabayo/browserjs/actions?query=workflow%3ACI+branch%main

> browserjs is early work in progress, use at your own risk.
>
> Not everything that exists is documented and not everything that is documented is implemented.

This is an experimental project and no [minimal Rust version (MSRV)](https://rust-lang.github.io/rfcs/2495-min-rust-version.html) is defined or promised for the time being. Once this project is usuable (at your own risk) in production we will define one.

## Wishlist

Dream API:

```python
from browserjs import Browser

browser = Browser(('chrome', '115'))

browser.set_dom("""<!DOCTYPE html>
<html lang="en">
  <head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Hello World! Site Title</title>
  </head>
  <body>
    <h1>Hello World!</h1>
  </body>
</html>""")

page_title = browser.eval_js("""document.title""")
assert(page_title == "Hello World! Site Title")

page_title = browser.eval_js("""document.write("foo"), document.title""")
assert(page_title == "")

ua = browser.eval_js("""navigator.userAgent""")
assert(ua == 'Mozilla/5.0 (Macintosh; Intel Mac OS X 10_15_7) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/115.0.0.0 Safari/537.36')
```

It is not a goal to make an actual "fake" browser.
As such if you have a DOM containing javascript,
it will never be loaded automatically, unless you
make it evaluate the embedded js.

Some features are also enabled only when
you configure it with your own logic. E.g. making
XHR requests is supported only if you specify the logic for
it, these will be blocked by default.

TODOS:

* integrate V8 Engine
* make small Rust Hello Eval lib with it,
  that already uses Rust functionality
* make a python wrapper
  * not sure PyO3 will work here nicely given the native bindings to the v8 engine... We'll see

## Contributing

:balloon: Thanks for your help improving the project! We are so happy to have
you! We have a [contributing guide][contributing] to help you get involved in the
`browserjs` project.

Should you want to contribure this project but you do not yet know how to program in Rust, you could start learning Rust with as goal to contribute as soon as possible to `browserjs` by using "[the Rust 101 Learning Guide](https://rust-lang.guide/)" as your study companion. Glen can also be hired as a mentor or teacher to give you paid 1-on-1 lessons and other similar consultancy services. You can find his contact details at <https://www.glendc.com/>.

## License

This project is dual-licensed under both the [MIT license][mit-license] and [Apache 2.0 License][apache-license].

### Contribution

Unless you explicitly state otherwise, any contribution intentionally submitted
for inclusion in `browserjs` by you, shall be licensed as both [MIT][mit-license] and [Apache 2.0][apache-license],
without any additional terms or conditions.

## Sponsors

browserjs is **completely free, open-source software** which needs lots of effort and time to develop and maintain.

Support this project by becoming a [sponsor](https://github.com/sponsors/plabayo).

Sponsors help us continue to maintain and improve `browserjs`, as well as other
Free and Open Source (FOSS) technology. It also helps us to create
educational content such as <https://github.com/plabayo/learn-rust-101>,
and other open source libraries such as <https://github.com/plabayo/tower-async>.

Sponsors receive perks and depending on your regular contribution it also
allows you to rely on us for support and consulting.

If you plan to use browserjs for your commercial resell or package activities you
need to be a sponsor for a high enough tier to allow you to use it
for these purposes despite it having a Business License (BSL).

## FAQ

### Q: Help this library doesn't work!

This is an experimental project, use at your own risk.
For now this is purely for our own purposes,
and if it works for you, great.

That said, feel free to reach out via GitHub or email
to see how this might benefit you or how you might be able to
[contribute](#contributing).
