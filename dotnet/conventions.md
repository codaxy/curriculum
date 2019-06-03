# .NET Coding Conventions

**This is a draft made from personal assembly of coding conventions. For wider audience, all points should be considered in proposal state. Also, the doc should be restructured, reworded (more strict language) and include DOs and DON'Ts.**
 
- Exception messages very rarely need to end with an exclamation point. Source: [english grammar](http://grammar.yourdictionary.com/punctuation/when/when-to-use-exclamation-marks.html), [SO](https://stackoverflow.com/questions/259887/what-style-do-you-use-for-exception-messages)

- Even though it’s very tempting to simply follow the rule of least privilege, you should resist the urge and prepend method and field and whatnot names with proper accessibility modifier (private, public, internal). Moreover, this should always be the first keyword (i.e. `private static` instead of `static private`). Source: [Some](https://github.com/openiddict) [great](https://github.com/aspnet-contrib/) [.NET](https://github.com/dotnet/corefx) [projects](https://github.com/jbogard/MediatR), VS code generator.

- There is almost never a reason to have two or more blank lines in a row. Avoid at all costs. Source: common sense.

- There is NEVER a reason to have a blank line between two closing braces (i.e. two `}`'s or two `)`'s or two `]`'s etc.). Source: common sense.

- You should ALWAYS put breathing space (a single empty line, see point 3 above) between adjacent methods within a class, between two classes within a namespace, between two namespaces within a file...you get the point. Additionally, you should treat code within a single method as a story consisting of paragraphs. You should separate these paragraphs by a single empty line. The last paragraph (the one that is followed by a `}`) does not have any extra blank lines; the `}` closes it perfectly. I will cringe from this empty line just as you might cringe from this written sentence: `Wow   ,   this thing really *is* opinionated   .`

- Useful comments are highly appreciated. Unfortunately, I don’t know how to write comments that are useful, so I usually skip them altogether. Bad habit. Commenting public methods is probably the easiest improvement. Unfortunately, I rarely do that, either. However, when you do write comments, please ALWAYS put a space between `//` and start of your comment. Also, *Sentence case* is encouraged. So, not `//this does some random stuff`, but: `// This does some random stuff`. Source: common sense. Also, [some](https://github.com/openiddict) [great](https://github.com/aspnet-contrib/) [.NET](https://github.com/dotnet/corefx) [projects](https://github.com/autofac/Autofac). **NOTE:** This does not apply to commented code, but to proper comments only. Commented code is a bad idea anyway, but if you really don’t want to delete the code and choose to comment it out, feel free use any style you want. 

- I might start prepending private fields with underscores (like `private Session _session`) at one point, even though I've never done it before. Source: [some](https://github.com/openiddict) [great](https://github.com/aspnet-contrib/) [.NET](https://github.com/dotnet/corefx) [projects](https://github.com/autofac/Autofac). 

- Always `string`, never `String`. Even in e.g. `string.Empty`, or `string.IsNullEmpty(text)`. Source: `Name can be simplified`, VS code generator. Also, [some](https://github.com/openiddict) [great](https://github.com/aspnet-contrib/) [.NET](https://github.com/dotnet/corefx) [projects](https://github.com/autofac/Autofac).
