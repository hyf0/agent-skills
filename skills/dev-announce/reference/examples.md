# Examples

13 real tweet threads demonstrating the style. Grouped by feature type for quick lookup.

## New API Announcements

### Bun.cron

**Main:** In the next version of Bun / `Bun.cron(file, schedule, name)` schedules a function to be called on a recurring interval / _[Polished code screenshot]_

**Reply 1:** This uses your operating system's scheduler so it doesn't need to keep the process running to schedule a job, but each invocation is run as a separate process. This is useful for CLIs or long-running servers that perform regular but infrequent cleanup / _[Full API usage screenshot with comments]_

### Bun.JSONL.parseChunk

**Main:** In the next version of Bun / `Bun.JSONL.parseChunk` parses potentially incomplete line-delimited streaming JSON. This is useful when reading JSONL files or streams that may be too large to fit into memory / _[Code screenshot]_

**Reply 1:** We'll likely add a Bun.file(path).jsonl() later. But it's useful to have this as an underlying implementation decoupled from the specific use-case. / _[Code screenshot showing realistic streaming input with truncated data]_

### Built-in Markdown parser

**Main:** In the next version of Bun / Bun gets a built-in, native Markdown parser - a Zig port of the popular `md4c` library. / _[Code screenshot]_

**Reply 1:** We've also ported md4c's CommonMark and regression test suites. And we've added looked through the GitHub issues to port additional tests to address edgecases with Github-flavored markdown. / _[API screenshot + 792 pass / 0 fail test results]_

## Performance Improvements

### Event loop 2x faster

**Main:** In the next version of Bun / Bun's event loop loops 2x faster on macOS / _[Benchmark chart]_

**Reply 1:** Similar improvement on Linux, though the optimizations were different / _[Three-way comparison: New vs Prev vs Node on both macOS and Linux]_

### Bundler shims optimization

**Main:** In the next version of Bun / Bun's bundler shims/module wrappers are lower overhead, which in large TypeScript projects can reduce the total number of objects by 10% / _[Code snippet]_

**Reply 1:** This makes apps using Bun's bundler very slightly faster for two reasons: 1) faster property accesses for imports that point to what were commonjs modules 2) fewer objects for the GC to visit

**Reply 2:** _[Before/after table: Total objects -11%, Heap -4MB, GetterSetter -61%, Function -11%]_

### Path optimization (number-first, explanation in reply)

**Main:** In the next version of Rolldown / Up to 9% faster bundling by optimizing how file paths are handled internally. / _[Benchmark table]_

**Reply 1:** A bundler resolves thousands of paths per build, and it turns out most of them are already clean. We were allocating new path buffers every time regardless, even when there was nothing to normalize. Now we just reuse the original when it's already good, and rewrote the relative path computation to work directly on strings instead of walking path components one by one.

### Claude Code Bash tool

**Main:** In the next version of Claude Code / Claude Code's Bash tool runs faster and uses less memory. Claude writing 1 GB to stdout 10 times: Before: 115 seconds / After: 15 seconds (7x faster) / _[Benchmark chart]_

**Reply 1:** This will also impact Claude Agent SDK & Cowork.

**Reply 2:** _[Before/after RSS memory: ~4.76 GB -> ~709 MB]_

### Claude Code CPU reduction

**Main:** In the next version of Claude Code / Reduced CPU usage by (1) consolidating timers (2) slightly slowing timers when not focused / _[Benchmark chart]_

**Reply 1:** I still think 5% is way too high for when the spinners are shown. But we need to make more changes to get that to a reasonable %.

**Reply 2:** Unfortunately, there doesn't seem to be an OS-level API we can use for "is this visible at all" for CLIs that aren't the terminal itself. "blurred" here means did it send the terminal escape sequence for unfocus. You usually can still see it when it's blurred though / _[CPU usage table: Idle 0.7%->0.3%, Spinner ~17%->~5%]_

### Claude Code terminal bytes

**Main:** In the next version of Claude Code / Claude Code writes fewer bytes to the terminal, which reduces latency & improves memory usage a little / _[Benchmark chart]_

**Reply 1:** This was unrelated to CPU usage or memory usage improvements. / _[A/B comparison: -56.6% bytes on initial render, -56.1% on resize cycles]_

## Feature/Compatibility Announcements

### JSON5 support

**Main:** In the next version of Bun / Bun's JavaScript bundler & runtime get builtin JSON5 support, thanks to @dylanconway111. 7x faster parsing with `Bun.JSON5.parse` compared to the `json5` npm package. / _[Full benchmark: parse small 7x, parse large 9.5x, stringify small 3.7x, stringify large 5.8x]_

### ECMAScript Decorators

**Main:** In the next version of Bun / Bun gets bundler & runtime support for ECMAScript Decorators and accessors / _[Code screenshot]_

**Reply 1:** Previously, Bun only supported the deprecated TypeScript experimentalDecorators. Now it supports both variants of decorators. / _[Terminal: running + source code in one image]_

## CLI Features

### Parallel/sequential scripts

**Main:** In the next version of Bun / You can: `bun --parallel a.ts b.ts` / `bun --sequential seed app.ts` / `bun --parallel --filter='*' 'build:*'` / _[Video demo]_

**Reply 1:** You can run multiple files or package.json scripts in parallel or sequential across multiple workspace packages from the same command. Output is automatically prefixed. This also works with globs. / _[Cheat sheet: 8 usage variations with comments]_

## Bundled Features

### Standalone HTML

**Main:** In the next version of Bun / `bun build --compile --target=browser ./index.html` / Bundles & inlines all CSS and JS into a single standalone .html file - no external script or link tags. One file, zero dependencies. / _[Screenshot]_

**Reply 1:** Usecases: when you don't want a localhost server to open a .html file / so you don't have to think about relative paths when uploading throwaway .html files to s3 / when you want to workaround CORs restrictions with file:// URLs / when you want to iMessage a .html file

**Reply 2:** Since this runs bun's bundler and transpilers, this works with React, TypeScript TSX JSX etc as well as all the other features like TOML & YAML imports, ESM <> CJS interop etc / _[Before/after diff image]_
