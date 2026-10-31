beui is a gui framework. Its goal is to be the best option for:

- web
- desktop (mac/windows/linux)
- mobile

How do you be the best?

- web
  - to be really good at web, you need partial hydration, islands, SSR-only, streaming, etc. if you are canvas-based, you can't do this. this fights with native.
- native
  - to be really good at native, you need to render to a canvas and handle a bunch of platform-specific stuff. this fights with web.
- mobile
  - idk

What works against us?

- rust, wasm sizes, wasm interop. Right now, you can't really be the best framework for web if you're using wasm.

Why make a new GUI framework?

- I want one codebase that works really well across iOS, android, native desktop, and web
- I want it to not be webtech

So what are the options?

- Flutter
- That's the only option, and it requires you to write Dart. Also, its web support isn't good enough.

What should it be like?

- unstyled/styled split built in, so if you want to make an app with its own style, you can use the unstyled layer and get all the functionality from there
- Provide good components. web gives you so little, if you're making an app you need to make your own copies of so many components or use a library that has done that
- Make it easy to make your own components. Stuff like focus handling should be easy to define.
- Fine-grained reactivity, like SolidJS
  - This comes with performance costs and benefits, it isn't necessarily the right choice. But it does let us be pretty efficient.
- Good spring / user-controlled animation support

Fun stuff

- by using typed components, we can easily use the same jsx syntax for different classes of node trees, like a terminal, or a 3d canvas, within a single node tree
- theoretically maybe we could make our styled layer pluggable. so then you could implement a whole new styled layer for a TUI, and then an app that only uses
  beui's styled layer could run on TUI without any changes. that would be hard to do well.
