# .NET Coding Conventions

We are using [CoreFX Style Guidelines](https://github.com/dotnet/corefx/blob/368fdfd86ee3a3bf1bca2a6c339ee590f3d6505d/Documentation/coding-guidelines/coding-style.md) as a baseline for our own C# code. In this document, we will outline differences and some important points.

- Proper indentation is **a must**. Also, code needs to be readable and tidy. Any pull request that violates either indentation rules or basic readability will be rejected without further consideration.
 
- Exception messages very rarely (if ever) need to end with an exclamation point. Rationale: [english grammar](http://grammar.yourdictionary.com/punctuation/when/when-to-use-exclamation-marks.html), [SO](https://stackoverflow.com/questions/259887/what-style-do-you-use-for-exception-messages)

- Developers should **avoid** relying on the rule of least privilege for implicit access modifiers (`private`, `public`, `protected`, `internal`) and always specify them **explicitly**. Moreover, this should always be the first keyword (i.e. `private static` instead of `static private`). Rationale: [some](https://github.com/openiddict) [great](https://github.com/aspnet-contrib/) [.NET](https://github.com/dotnet/corefx) [projects](https://github.com/jbogard/MediatR), VS code generator defaults.

- There is almost never a reason to have two or more consecutive blank lines.

- There is **never** a reason to have a blank line between two closing braces (i.e. two `}`'s or two `)`'s or two `]`'s etc.).

- You should **always** put breathing space (a single empty line, see point above) between adjacent methods within a class, between two classes within a namespace, between two namespaces within a file (but if you do have multiple namespaces within the same file, you should seriously reconsider that). Additionally, you should treat code within a single method as a story consisting of paragraphs. You should separate these paragraphs by a single empty line. The last paragraph (the one that is followed by a `}`) does not have any extra blank lines; that final `}` closes it perfectly.

- Useful comments are highly appreciated, but we understand it's not easy to write concise comments that don't get in the way of code readability. In any case, when you do write single-line comments, always put a space between `//` and the beginning of your comment. Also, *Sentence case* is highly encouraged. So, not `//this does some random stuff`, but: `// This does some random stuff`. Rationale: [some](https://github.com/openiddict) [great](https://github.com/aspnet-contrib/) [.NET](https://github.com/dotnet/corefx) [projects](https://github.com/autofac/Autofac). 

- Previous point does not apply to commented code, but to proper comments only. Commented code is usually a **bad idea**, but if you have a really good reason not to delete the old code, feel free use any commenting style you want.

- Always `string`, never `String`. Even in e.g. `string.Empty`, or `string.IsNullOrEmpty(text)`. Rationale: `Name can be simplified`, VS code generator defaults. Also, [some](https://github.com/openiddict) [great](https://github.com/aspnet-contrib/) [.NET](https://github.com/dotnet/corefx) [projects](https://github.com/autofac/Autofac).

- Contrary to CoreFX guidelines, Codaxy does *not* use underscores to prepend private fields (e.g. `private readonly ISession _session`), or `s_`, `t_`, and similar prefixes for static fields, thread-static fields, etc. However, due to the popularity of this style ([some](https://github.com/openiddict) [great](https://github.com/aspnet-contrib/) [.NET](https://github.com/dotnet/corefx) [projects](https://github.com/autofac/Autofac)), we do not forbid it for new projects. If you do decide to use it, make sure you're consistent throughout the **entire project** and avoid using `this.` unless absolutely necessary, as the guideline says.

- We use `var` much more freely than CoreFX team recommends, but following that recommendation is encouraged.

- We don't usually tidy up our imports (remove unused and sort alphabetically) and don't really care about it at the moment. Just make sure they're on top of the file, outside the namespace.

