beui is a gui framework. Its goal is to be the best option for:

- web
- desktop (mac/windows/linux)
- mobile

How do you be the best?

- web

What works against us?

- rust, wasm sizes, wasm interop. Right now, you can't really be the best framework for web if you're using wasm.

Why make a new GUI framework?

- I want one codebase that works really well across iOS, android, native desktop, and web
- I want it to not be webtech

So what are the options?

- Flutter
- That's the only option, and it requires you to write Dart. Also, its web support isn't good enough.

What should it be like?

- unstyled/styled split built in
- Provide good components. web gives you so little, if you're making an app you need to make your own copies of so many components or use a library that has done that
- Make it easy to make your own components. Stuff like focus handling should be easy to define.
- Fine-grained reactivity, like SolidJS
  - This comes with performance costs and benefits, it isn't necessarily the right choice. But it does let us be pretty efficient.
