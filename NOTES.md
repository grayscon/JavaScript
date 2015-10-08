# Setup

* We shouldn't need much for this project
* Make sure you have a text editor installed ideally Sublime Text or Atom
I'll be using Atom

# Audience
* We assume you know nothing about JavaScript and have never programmed before.
  People who do have programing experience may feel that this talk moves to slowly
* You should be simi-familar with html, but don't wory if your not it isn't the
  focus of this talk

# Download the Starter project
* Go to https://github.com/Freshmen15/JavaScript and click Download Zip in the lower right
* Unzip the folder anywhere, we don't care where.
* Navigate to the file and open the index.html file in your favorite text editor
* Open the index.html in your web browser of choice
* You should see a simple web page
* Open dev console, if you get stuck search for open dev console your browser

# Hello World!
* Add `console.log("Hello World!");` between the `<script type="text/javascript">` tag
and </script> tag
* You've just made the simplest script
* Reload the page in the browser and you will see in the dev console `Hello World!`
* [Commit](https://github.com/Freshmen15/JavaScript/commit/0bc178dfae5c72c0c0d9e9181c0401bb512ea22b)

# Two lines
* Add `console.log("Bye World!");` after `console.log("Hello World!");`
* Reload in the browser and notice that `Hello! World!` shows up above `Bye World`
* This is because the code is executed in the order it appears

# Functions: How Nice
* Get rid of `console.log("Bye World!");`
* Add `function handleChange() {` in front of Hello World!
* Add `}` after.
* You've just made a function
* A function is a way of wrapping up code so we can reuse it later
* Add handleChange(); at the end so that we'll actually call the function
* Reload in the browser, It's the exact same
* [Commit](https://github.com/Freshmen15/JavaScript/commit/e2273680cd31eba52af4debd79cd2bd2c68fa7a3)

# Useful functions, kind of
 * Right now our function always does the exact same thing, lets make it change
 * add a `value` between the parentheses in the function
 * replace `console.log("Hello World!");` with
 * console.log(value);
 * if we reload this we will get something about `undifined` we need to define what value is when we call the function. For now we can just replace
 `handleChange();` with `handleChange("Hello World!");`
