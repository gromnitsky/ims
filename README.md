# Interactive Make Shell

The simplest possible wrapper around GNU Make for playing w/ it
internal functions like `$(patsubst)` interactively as if in some kind
of REPL environment.

## Requirements

* Ruby 2.0+
* GNU Make
* rlwrap

## Usage

To run, type

	$ rlwrap -S 'ims> ' ./ims

<kbd>.</kbd> (+ <kbd>Return</kbd>) prints the help screen.

## Examples

~~~
ims> src := foo/a.coffee foo/b.coffee bar/index.html
ims> . $(patsubst %.coffee, build/%.js, $(src))
 build/foo/a.js  build/foo/b.js bar/index.html
ims> . $(filter %.html, $(src))
bar/index.html
ims>
~~~

~~~
ims> me:; @printenv USER
ims> .t me
alex
ims>
~~~

~~~
ims> . $(sort $(wildcard /*))
/bin /boot /dev /etc /home /lib /lost+found /media /mnt /opt /proc /root /run /sbin /srv /sys /tmp /usr /var
~~~

## Bugs

It's not possible to enter a multiline expression.

## License

MIT.
