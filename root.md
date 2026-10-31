block-app is a new operating system for creating apps that edit collaborative documents

**operating system?** yes, block-app runs on existing operating systems (web, mac, windows, linux, ios, android). block-app runs wasm apps and provides an execution interface. theoretically we could run on bare metal, support native apps, and provide that same interface through shared memory & a wait syscall. we won't ever do this though. if we ever make a block-app os, it will be based on linux because linux & libinput & mesa & others give us so much hardware support for free that it would be a waste of time to try and recreate and extremely expensive to try and test.

**block storage model:** block-app stores documents. documents have a type which stores an opaque `Vec<u8>` backed by a wasm blob that defines some operations on them:

- how they merge offline. given (lhs,base,rhs), compute a new merged version of the file.
- how you convert offline data to a new blob of online session data
- how they merge online. given (online session, operation), update the online session * matbe. OPEN QUESTION: it's a bit odd for a separate wasm blob to handle online sessions, because the main plugin blob probably needs to handle them too. and online sessions probably want a different in-memory view of the data than a compact offline version, which you can't really share across different wasm files. we need to decide a clean boundary here


