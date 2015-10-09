# JavaScript
A website to teach the basics of JavaScript for use in website to those with absolutely no experience

# Notes

# Setup

* We shouldn't need much for this project
* Make sure you have a text editor installed ideally Sublime Text or Atom
I'll be using Atom

# Audience
* We assume you know nothing about JavaScript and have never programmed before.
  People who do have programing experience may feel that this talk moves to slowly
* You should be simi-familar with html, but don't wory if your not it isn't the
  focus of this talk

# Steps

## Download the Starter project
* Go to https://github.com/Freshmen15/JavaScript and click Download Zip in the lower right
* Unzip the folder anywhere, we don't care where.
* Navigate to the file and open the index.html file in your favorite text editor
* Open the index.html in your web browser of choice
* You should see a simple web page
* Open dev console, if you get stuck search for open dev console your browser

## Hello World!
* Add `console.log("Hello World!");` between the `<script type="text/javascript">` tag
and </script> tag
* You've just made the simplest script
* Reload the page in the browser and you will see in the dev console `Hello World!`
* [Commit](https://github.com/Freshmen15/JavaScript/commit/0bc178dfae5c72c0c0d9e9181c0401bb512ea22b)

## Two lines
* Add `console.log("Bye World!");` after `console.log("Hello World!");`
* Reload in the browser and notice that `Hello! World!` shows up above `Bye World`
* This is because the code is executed in the order it appears

## Functions: How Nice
* Get rid of `console.log("Bye World!");`
* Add `function handleChange() {` in front of Hello World!
* Add `}` after.
* You've just made a function
* A function is a way of wrapping up code so we can reuse it later
* Add handleChange(); at the end so that we'll actually call the function
* Reload in the browser, It's the exact same
* [Commit](https://github.com/Freshmen15/JavaScript/commit/e2273680cd31eba52af4debd79cd2bd2c68fa7a3)

## Useful functions, kind of
* Right now our function always does the exact same thing, lets make it change
* add a `value` between the parentheses in the function
* replace `console.log("Hello World!");` with
* console.log(value);
* if we reload this we will get something about `undifined` we need to define what value is when we call the function. For now we can just replace
 `handleChange();` with `handleChange("Hello World!");`
* The quotes mean that the thing inside is a string (a list of characters) rather than something we should run
* [Commit](https://github.com/Freshmen15/JavaScript/commit/4a00d6ca031e49061a825ca4d71eaa95bcca6960)

## That's odd
* Our website always does the same thing. It's kind of boring. Lets fix that.
* Remove `handleChange("Hello World!");`
* Add `onchange="handleChange(this)` to make it look like `input type="test" onchange="handleChange(this)"/>`
* Run the program, put something in the text box then press enter.
* You should see something like `<input type="test" onchange="handleChange(this)"/>` in the dev console.
* This is because we are printing the entire element
* [Commit](https://github.com/Freshmen15/JavaScript/commit/769fc1a7314b35a69d31f6ad601f2333e6f0e6f2)

## Better
* We can get what was typed with value.value, but this looks bad
* Change the function prototype to match function `handleChange(value)` by replacing `value` with `input` we can use any name but input will work well
* Replace `console.log(value);` with `console.log(input.value);`

## WE ONLY WANT HELLO WORLD!
* Right now our wonderful code can be used for things other than printing hello world. We will be putting a stop to this
* Lets wrap the our `console.log` statement in an if statement
* Add `if (input.value == "Hello World!") {` in front of the `console.log`
* add `}` after to end the if statement
* Now run it and your notice it only prints something out if you type Hello World exactly
* [Commit](https://github.com/Freshmen15/JavaScript/commit/0fc20666a8a82ce8b8e5349559f6bb453b944d97)

## Clear the field
* We kind of don't want to have to get rid of our the text in the input ourselves.
* Thankfully we have a great way to do this.
* Just add `input.value = "";` to the end of our function.
* [Commit](https://github.com/Freshmen15/JavaScript/commit/8f568e6a9f056c1bc09ca2c0da1e3f21f0b8f9c7)

## Say when we enter the wrong thing
* Right now we don't have it say anything when when we mess up and enter the wrong thing.
* Add
      else {
         console.log("Don't say that");
      }

    After the if statement
* [Commit](https://github.com/Freshmen15/JavaScript/commit/622c557bfa04f9d0ee5c8cf7405da91aef282b09)
## Count how wrong they are
* A bit complicated start by adding `var howWrong=0` to the start of the script to tell the browser we want to keep track of this
* Add `howWrong=0` so that it gets run if the user enters `Hello World!`
* add at the end of the else `howWrong = howWrong + 1;`
* Change `console.log("Don't say that");` to `console.log("You were wrong " + howWrong + " times");`
* Now when you enter things it will tell you how many times you were wrong

## Tell them what's up after a while
* This isn't all that fun at the moment, lets give them a hint after a while
* Replace `console.log("You were wrong " + howWrong + " times");` with:
      if (howWrong < 3) {
        console.log("Don't say that");
      } else {
        console.log("Psst say Hello World!");
      }
* [Commit](https://github.com/Freshmen15/JavaScript/commit/95d2935ccd1883d81ca9ff2595e946b3444df0e9)

## Lets actually implement the the goal
* We'd like to maintain a list of games so lets start out by letting us add games to the list
* Remove everything in the `handleChange` function except `input.value = "";`
* Add `var games = document.getElementById("games");`
  * This gets the html element with the id `games`
* Add `games.innerHTML = games.innerHTML + "<li>" + input.value + "</li>";`
  * This says to set the html inside the tags to be what ever it currently is plus a new line
* That's it
* [Commit](https://github.com/Freshmen15/JavaScript/commit/322a2640e0f8139642648d0b6ff536fef7c2c9fd)

## We should be able to get rid of games
* We want to be able to remove games so lets to do that by adding a listener to to each line item to call another bit of code we have to tell it to call function and delete that element
* When we add a new game replace `"<li>" + input.value + "</li>";` with `"<li onClick='removeGame(this)'>" + input.value + "</li>";`
* Add a `removeGame` function to allow us to remove a game like so:
      function removeGame(game) {
        var games = document.getElementById("games");
        games.removeChild(game);
      }
* Now when we click on games they are removed

## Let us delete default stuff
* Right now we can't remove the default games. Lets fix that by adding an onClick listener to each of them like so:
      <ul id="games">
        <li onClick='removeGame(this)'>Chess</li>
        <li onClick='removeGame(this)'>Tic Tac Toe</li>
      </ul>
