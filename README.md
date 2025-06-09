# PreTeXt slides for MATH/COMP SCI 240

## Annotated vs blank

Use `component="a"` as an attribute on anything that you want in the instructor version of the slides but do not want to appear in the "blank" slides you will write on during class. Sometimes, it is cleanest to have two versions of something (or you need a placeholder in the blank slides), so you can put `component="b"` on whatever should appear in the blank slides.

## Building

Each chapter of the zyBook (as organized by default) has its own slide file, although occasionally, one chapter's slides ends with the first slides for the next chapter or starts with the last slides from the previous chapter. `project.ptx` has two separate build targets for each chapter. You can do `pretext build slides-2` to get the blank slides for writing on and posting for students for chapter 2. You use `pretext build slides-a-2` to get the annotated version. (Change 2 to another chapter value to get the slides for that chapter.)

## Viewing

You can use `pretext view slides-a-2` or `pretext view slides-2` to view the slides in a browser. Note that because this is HTML output, what you see may suggest that information is visible that gets cut off when doing the PDF. Thus, you need to conver to PDF and review that before considering your slides "final".

## Converting to PDF

Converting reveal.js slides to PDF requires an extra step. The best way to do this involves installing [Decktape](https://github.com/astefanutti/decktape). Note that Decktape also requires that you have Node.js and npm installed, which PreTeXt may not be setting up for you by default. If you are running PreTeXt in a Codespace on GitHub, you will be OK, but you will have to install Decktape by doing `npm install -g decktape`. If you are running PreTeXt on your own computer, you might have to figure out how to install Node.js and npm.

Once you have Decktape installed, you can use `decktape reveal http://localhost:8128/output/slides-2/slides.html filename-blank.pdf` to convert your slides to PDF. If you know that you only want slides 3 through 10, you can do `decktape --slides 3-10 reveal http://localhost:8128/output/slides-2/slides.html filename.pdf`. In either case, change `filename.pdf` to be what you want the output filename to be. Change the URL to match whatever you're looking at in your browser from `pretext view`, as the port (here, 8128) might be different. You will need to do this separately for both `slides-2` and `slides-a-2` (and will want to use different PDF files, of course).