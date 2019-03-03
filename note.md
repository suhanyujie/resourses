# Roadmap Draft

> 源：https://hackmd.io/hetFa17jRem_aKBCukrjVg?view

- Feature Name: N/A
- Start Date: 2019-02-21
- RFC PR: 
- Rust Issue: N/A

# Summary
[summary]: #summary

This RFC proposes the *2019 Rust Roadmap*, in accordance with [RFC 1728]. The goal of the roadmap is to lay out a vision for where the Rust project should be in a year's time.

[RFC 1728]: https://github.com/rust-lang/rfcs/blob/26197104b7bb9a5a35db243d639aee6e46d35d75/text/1728-north-star.md

The proposal is based on the [2018 survey], our annual [call for blog posts], direct conversations with individual Rust users, and discussions at the 2019 Rust All Hands. Thanks to everyone who helped with this effort!

[2018 survey]: https://blog.rust-lang.org/2018/11/27/Rust-survey-2018.html
[call for blog posts]: https://readrust.net/rust-2019/

In short, 2019 will be a year of rejuvenation and maturation for the Rust project. We plan to *finish what we've started*, rather than make new grand plans. We will take stock of what we've done, and work on laying even more solid foundations for the future.
> [name=Mazdak Farrokhzad]
> > We plan to *finish what we've started*, rather than make new grand plans.
>
> I think it's fine to do this as a secondary priority; it's more that finishing should be the primary objective. The current wording makes that sound ~forbidden.

# Detailed description
[Detailed description]: #detailed-description

In 2018, the Rust team came together around a shared vision: Rust 2018, our first real edition. We not only decided to develop Rust 2018, but also the idea of editions themselves, all in one year. 2018 was also a fantastic year for production usage of Rust. Some of the largest names in tech have started relying on Rust as a key part of their stack. Smaller companies have started to build great things with our technology as well.

Doing this was both a herculean task and a great success. But it also created a lot of debt, both technical and organizational. When reading the Rust 2019 blog posts, and when having conversations with team members at the Rust All Hands, a general theme developed: 2019 should still be a year of shipping, but a certain kind of shipping. Words like confidence, maturity, practicality, productivity, sustainability, and stability were often used. This should be a year of reflection, one of polish, one of finishing plans that were started long ago.

In some ways, it's easier to describe what this year should *not* be, rather than what it should be. This should not be a year of dreaming up large new features, one of drastic change, or one that makes your old code feel obsolete. 

Here's some select quotations from a few Rust 2019 posts that really resonated with folks:

> Let’s finish what we started. As much as is possible and practical this year, let’s set aside new designs and ship what we’ve already designed. Let’s tackle challenges we haven’t had time to give our full attention.
>
> - Jonathan Turner, ["The fallow year"](https://www.jonathanturner.org/2018/12/the-fallow-year.html)

> I believe not only that the processes and institutions of Rust need to be shored up, but that special attention should be paid to people. Ultimately, people are what drives the language forward, whether it be through design, implementation, or outreach. If no people want to work on Rust, or are blocked from working on Rust, the language will stagnate. ...
> 
> This is not to say that there should not be any movement on improving features or process. Just that their effects and costs should be measured in people, as well as in technology.
>
> - Cessen, ["Rust 2019 - It's the Little Things"](https://blog.cessen.com/post/2018_12_12_rust_2019_its_the_little_things)

> In this post, I’ll refer to a highly simplified maturity life cycle with three stages: research, development, and polish. Different parts of the Rust ecosystem are at different levels of maturity. It’s important for effort to match the actual stage in the life cycle, ideally to push it to the next. For example, I consider the language to mostly be in the “polish” stage. Continuing to treat it as research would bring dependent types, virtual structs, etc., which would be interesting but disruptive. Conversely, we don’t know exactly what we want for GUI, so trying to drive that to a standardized solution too early will likely get us to a suboptimal place.
> 
> Many mature products have alternating releases focused on new features, then stabilization... 2018 has seen a lot of new features, so I think it’s time for a stabilization phase.
>  
> - Raph Levien, ["My thoughts on Rust 2019"](https://raphlinus.github.io/rust/2018/12/16/rust-2019.html)

> [name=Mazdak Farrokhzad] I don't agree with the language being in a polish stage, but so long as this life cycle thing is "cyclical", i.e. we will get back to R&D eventually, it's fine.

> If you’re familiar with the history of Rust you might be confused with a call to stabilization. After all, Rust 2015 (a.k.a 1.0) was all about stabilization and the team has actually done a pretty good job with achieving this goal. So what gives?
> 
> While Rust 2015 defined stabilization around language backward compatibility, it’s time for the language, the tooling, the ecosystem and the governance to stabilize. Each of these characterize stability in a different way.
> 
> - Ryan Levick, ["Rust 2019: Stabilization"](https://blog.ryanlevick.com/posts/rust-2019/)

> The Rust project has been growing like a startup for the last several years. This has some good aspect - “hockeystick curves” - but it has some very bad aspects as well. If this project is going to have a chance of sustaining itself in the long term, we need to get real about dealing with the organizational debt we have accumulated. I think we have serious problems at every level of our organization that need to be addressed, and I’m going to enumerate them from my personal perspective. 
> 
> - withoutboats, ["Organizational Debt"](https://boats.gitlab.io/blog/post/rust-2019/)

We don't have space to quote every single post; if you'd like to read them all, you can over at [Read Rust](https://readrust.net/rust-2019/). And of course, these themes are not *universally* shared among Rust developers, but there is a common theme in many of them: slow down, pay off debt, finish what we've started.

# By team
[By team]: #by-team

With this general theme in mind, here are the high-level plans from each of the teams for the upcoming year, in alphabetical order. These summaries are based on discussions had at the All Hands; each team may also post a more detailed individual roadmap. The summaries are meant to show plans in broad strokes and how they fit together for the project.

## Cargo

The [cargo team 2019 roadmap](https://gist.github.com/nrc/6f0fb3b66d3b043aace30217128f3af9) focuses on a few major themes:

- **Better support for cross compilation:**
    - Try to incorporate some of the innovations from tools like [Xargo](https://github.com/japaric/xargo), [cross](https://github.com/rust-embedded/cross), [Rustup](https://github.com/rust-lang/rustup.rs), and [WASM-Pack](https://github.com/rustwasm/wasm-pack) into cargo itself.
- **Focus on the cargo ecosystem by supporting plugins (custom commands):**
    - Custom commands enable faster experimentation, bringing new and flexible workflows to users sooner rather than later.
    - Make plugins more discoverable.
    - Provide library crates for parts of cargo to make it easier to create plugins.
- **Compile times:**
    - Investigate ways that cargo can help to reduce compilation time, including potentially distributing binaries for builds from crates.io.
- **Addressing technical debt:**
    - There are a number of parts of cargo that could use refactoring, and we plan to spend some time on that.
- **Finishing "almost complete" work:**
    - Work on [custom registries](https://github.com/rust-lang/cargo/issues/6589),
[offline mode](https://github.com/rust-lang/cargo/issues/4686), and 
[custom profiles](https://github.com/rust-lang/cargo/issues/2007) is nearly done, and we intend to see those items over the finish line.

## Community

The community team has decided to make "solidifying" the theme of the year. While it has a lot of ideas of what could be done, a lot of existing projects are useful and would be more so with more time and investment. Projects like RustBridge, event support, the YouTube channel and modernizing the community calendar will take priority.

Internationalization will also be a big subject over the next year. This both means making Rust more accessible to non-english speakers and growing our global reach. This will bring with it organizational changes to allow the team to grow out of its current locations. It's hard to contribute to the community team if you are in timezones incompatible with meetings in US/EU timezones and the community team wants to change that.
## Compiler

The compiler team has four main themes of work for this year:

- **Improve Raw Compile Times and code generation:**
    - Parallelize the compiler.
    - Introducing MIR Optimizations that can help make generated code run faster -- hopefully including rustc itself.
- **Improve RLS Infrastructure:**
    - Absorbing the [rust-analyzer project](https://github.com/rust-analyzer/rust-analyzer) into an "RLS 2.0" effort aiming to produce an end-to-end prototype supporting typed completions and fast incremental responsiveness.
- **Improve Compiler Accessibility:**
    - Extracting parts of the compiler into libraries (similar to Chalk or Polonius). These libraries should help to make the compiler's behavior better defined and easier to understand, but can also be shared between the "RLS 2.0" prototype and rustc itself.
- **Improve Team Structure:**
    - Introduce focused Working Groups which report regularly to the team (and to the community at large).
    - Create a [compiler-team repository](https://github.com/rust-lang/compiler-team) with information about all the ongoing projects and easy ways to help out.

## Crates.io

One of the newer teams, the Crates.io Team is going to be focused on growing itself, paying down technical debt in the codebase, and establishing themes for long-term priorities.

## Dev Tools

The Dev Tools team has a few core functions:

- liaising with the wider project
- providing a "commons" space for cross-cutting tools concerns
- discovering and filling needs that are not addressed by existing tooling
- helping smaller tool subteams make decisions

They'll be pursuing those goals this year.

Finally, the team is also looking to reshape its internal processes.

## Documentation

The documentation team is going to be completely reformulating itself, and possibly re-naming itself as the "learning team." They're working on an RFC to do so, and that will lay out the roadmap. Stay tuned!

## Language

The language team has four areas of interest this year:

- **Organizational:**
    - [Introduce working groups](http://smallcultfollowing.com/babysteps/blog/2019/02/22/rust-lang-team-working-groups/) with the goal of increasing transparency and lowering the barrier to get involved 
    - Create a [lang-team repository](https://github.com/rust-lang/lang-team/) to help track what is happening and how to get involved
- **Key ergonomic improvements:**
    - Async/await in particular is needed to help "unlock" Async I/O
- **Finish long-standing features:**
    - Rust has a number of in-progress features -- such as const generics, Generic Associated Types, and specialization -- that have been in development for some time. It's time to finish their designs and ship them.
- **Reference material and guidelines:**
    - Work with the documentation team on the Rust reference.
    - Produce "unsafe code guidelines" that describe what unsafe code can and cannot do.

## Library

The library team will be focusing on maintaining the standard library. The team will handle specialized tasks such as overseeing and reviewing ports of the standard library to new platforms, as well as typical bug fixes and performance improvements.

The team doesn't currently have the bandwidth to take on a large number of new features for the standard library, but is specifically planning to develop a plan of attack for custom allocators associated with instances of collections (e.g. `Vec<T, A: Alloc>`).

# Working Groups

In addition to the Rust teams, we also have a number of active **working groups** that report to the core team. These groups are tasked with exploring a particular domain and making recommendations to other Rust teams with decision-making power. This section contains the 2019 priorities for each of these working groups.

[2018 Roadmap RFC]: https://rust-lang.github.io/rfcs/2314-roadmap-2018.html

## Async Foundations and Async Ecosystem

The 2018 roadmap comissioned a "Networking Services" domain working group. Since then, that working group has [split into various parts](https://blog.yoshuawuyts.com/async-ecosystem-wg/). The "Async Foundations" effort, which is being led by the language design team, will focus on building the 'core building blocks' that belong to the language itself, such as the `Future` trait and `async`-`await` syntax. The "Async Ecosystem" working group, meanwhile, will focus on nurturing the budding ecosystem built on top of those layers. The plan for 2019 is to focus on the [Tide web framework], the [Romio reactor](https://docs.rs/romio/0.3.0-alpha.2/romio/), and the [juliex executor].

[Tide web framework]: https://docs.rs/tide/0.0.5/tide/
[Romio reactor]: https://docs.rs/romio/0.3.0-alpha.2/romio/
[juliex executor]: https://docs.rs/juliex/0.3.0-alpha.1/juliex/

## CLI apps

The CLI working group's [2019 roadmap](https://paper.dropbox.com/doc/0lRnShqsfMlfS6ylXrX9h) focuses on three main themes:

- the **design and maintenance of clap v3.0**
- working on the **testing crates**, such as [`assert_cli`](https://crates.io/crates/assert_cli), [`assert_fs`](https://crates.io/crates/assert_fs), and [`assert_cmd`](https://crates.io/crates/assert_cmd)
- improving the **organizational structure** of the WG through meetings, organization, and branding

## WebAssembly

The [2019 WebAssembly WG roadmap](https://github.com/rustwasm/rfcs/pull/7) adopts the overall theme of **practicality**. The intent is to focus on these areas:

- Grow our library ecosystem by collaborating on a modular toolkit.
- Bring multithreading to Rust-generated Wasm.
- Integrate best-in-class debugging support into our toolchain.
- Polish our toolchain and developer workflow, culminating in a 1.0 version of `wasm-pack`.
- Invest in monitoring, testing, and profiling infrastructure to keep our tools and libraries snappy, stable and production-ready.

## Embedded "bare metal" devices

The Embedded WG's [2019 Roadmap](https://paper.dropbox.com/doc/ZmUYvRp4PjX1jqq6LSxcZ) designates **productivity** as their theme for 2019. They plan to focus on three main points:

- **address practical problems**:
    - fix compiler bugs
    - polish tools
- **create documentation for intermediate level users:**
    - patterns and best practices
- work hand in hand with the community to **improve the ecosystem**

