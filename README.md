<p align="center">
  <img alt="ReacTyper Demo GIF" src="demo.gif">
  <br />
  <b>A Preact component that types.</b>
  <br />
  Inspired by <a href="https://github.com/cngu/vue-typer">vue-typer</a>.
  Forked from <a href="https://github.com/Li357/reactyper">reactyper</a>.
  <p align="center">
    <img src="https://img.shields.io/npm/v/preactyper?style=flat-square" />
    <img src="https://img.shields.io/npm/dm/preactyper?style=flat-square" />
    <img src="https://img.shields.io/github/issues/ndom91/preactyper?style=flat-square" />
    <img src="https://img.shields.io/github/languages/code-size/ndom91/preactyper?style=flat-square" />
    <img src="https://img.shields.io/github/license/ndom91/preactyper?style=flat-square" />
  </p>
</p>



```js
import Typer from 'preactyper';

<Typer spool={['🎉 PreacTyper']} />
```

## Installation

#### Node

    $ npm i preactyper

or

    $ yarn add preactyper

Then import:

```js
import Typer from 'preactyper';
```

## Props

Each prop is listed in the format `<prop>: <type> = <default-value>`. **Note**: The typer is considered complete when it has run once through the whole spool, then an additional number of repeats through the spool, and has erased the last string if `eraseOnComplete` is true.

`spool: string[] = ['React Typer']`

- Array of strings to type
- Empty strings will be ignored, Unicode characters are supported

`repeats: number = Infinity`

- Number of additional times to the whole spool

`shuffle: boolean = false`

- Whether or not to shuffle the spool on every run
- Shuffles on first run

`initialAction: 'typing' | 'erasing' = 'typing'`

- Specifies initial action of the typer, whether to start typing or erasing

`eraseOnComplete: boolean = false`

- Whether or not to erase text on typer completion, see note above.

`eraseStyle: 'backspace' | 'select' | 'select-all' | 'clear' = 'backspace'`

- Style of erasing:
	- `backspace`: Each character is removed and classed with `erased`
	- `select`: Each character is selected and classed with `selected`
	- `select-all`: All characters are selected and classed with `selected`
	- `clear`: All characters are removed immediately and classed with `erased`

`caretAnimationStyle: 'solid' | 'blink' | 'smooth' = 'blink'`

- Style of the caret's animation:
	- `solid`: Caret is just solid
	- `blink`: Caret blinks
	- `smooth`: Caret smoothly moves between 0 and 100% opacity

`preTypeDelay: number = 70`

- Delay before the first type step in ms
- After this delay, the first character is typed immediately

`typeDelay: number = 70`

- Delay before every successive type step in ms

`preEraseDelay: number = 2000`
- Delay before the first erase step in ms
- After this delay, the first character is erased immediately

`eraseDelay: number = 250`

- Delay before every successive erase step in ms

## Events

`onType(typed: string)`

- Called after a character is typed, called in conjunction with `onTyped` for the last character
- `typed` : currently typed string

`onTyped(current: string)`

- Called after the whole word is typed
- `current`: string that finished typing

`onErase(erased: string)`

- Called after a character is erased, called in conjunction with `onErased` for last character
- `erased`: currently erased string

`onErased(current: string)`

- Called after the whole word is erased
- `current`: string that finished erasing in full

`onFinish()`

- Called after the typer finishes, i.e. when it runs `(repeats + 1) * spool.length` times

## Styles

The typer's styles are set to a relatively low specificity to allow overwriting them:

```
.preactyper {
  /* styles for entire typer span */
}
 
.preactyper-char {
  /* styles for any character of the typer */
}
 
.preactyper-char.typed {
  /* styles for a character that has been typed */
}
 
.preactyper-char.untyped {
  /* styles for a character that has not been typed */
}
 
.preactyper-char.erased {
  /* styles for a character that has been erased */
  /* see eraseStyle */
}
 
.preactyper-char.selected {
  /* styles for a character that has been selected */
  /* see eraseStyle */
}
 
.preactyper-caret {
  /* styles for the caret span */
}
 
.preactyper-caret.blink {
  /* animation for a smooth cursor */
}
 
.preactyper-caret.smooth {
  /* animation for a smooth caret */
}
```

## License


License [MIT](https://opensource.org/licenses/MIT)
