be-host is a new operating system for creating apps that edit collaborative documents

**operating system?** yes, be-host runs on existing operating systems (web, mac, windows, linux, ios, android). be-host runs wasm apps and provides an execution interface. theoretically we could run on bare metal, support native apps, and provide that same interface through shared memory & a wait syscall. we won't ever do this though. if we ever make a be-host os, it will be based on linux because linux & libinput & mesa & others give us so much hardware support for free that it would be a waste of time to try and recreate and extremely expensive to try and test.

## document storage model

be-host stores documents. documents have a type which stores an opaque `Vec<u8>` backed by a wasm blob that defines some operations on them:

- how they merge offline. given (lhs,base,rhs), compute a new merged version of the file.
- how you convert offline data to a new blob of online session data
- how they merge online. given (online session, operation), update the online session \* maybe. OPEN QUESTION: it's a bit odd for a separate wasm blob to handle online sessions, because the main plugin blob probably needs to handle them too. and online sessions probably want a different in-memory view of the data than a compact offline version, which you can't really share across different wasm files. we need to decide a clean boundary here

this system should be flexible enough to support any collaboration model:

- CRDT
  - you use the same online and offline data model. OPEN QUESTION: how do you provide offline merges? ideally you shouldn't need to because you keep operations instead, so this might be an issue with our model
- OT
  - we provide an order for operations, so your app
- Git-like, for example ProseMirror iirc
- Hybrid (our model)

## Why would you build your app for be-host?

If you use our entire stack, here's what your app gets for free:

- easy undo & redo
- persistent data storage on a server, so it is easy for your users to make a file on their computer and open it on their phone
- sharing & live collaboration, so it
- permissions
- version control. revision history and a full jj-like vcs available
- e2e encrypted data, so our servers never see data users make with your app
- offline-first, so for individuals using your app they can keep a copy of their files on all their devices and edit them while offline
- teams

You don't have to use our whole stack though, you can:

- use your own server to run backend calculations: we should support this by auto-sharing the document with the service provider
- using your own entire data storage: the document is just an identifier and the whole UI goes through your server
- using your own gui library: we should support web apps, wasm apps support any gui framework that can run on wasm, and we should support native apps, and even web and native apps that run outside of be-host's own ui.

What you lose:



## platforms

we want t


**terms**:

- **be-host**: temporary name for the app host
- **app**: an app built for be-host
- **document**: a piece of data stored by the app host, currently called a "block" in the code
- **format**: a type for stored data, currently called a "block type" in the code



