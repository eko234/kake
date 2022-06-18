# Kake

Make you makefile more useful in kakoune,

## Usage
`kake-mode`:
enter `kake-mode`, which will map keys acording to the first Makefile
found while walking back to the root dir

`kake-info`:
show the mappings avaiable for `kake-mode` along
with their documentation, which is taken from the first comment
block on top of the target in a scratch buffer

my recommendation is to map `<leader-m>` to enter `kake-mode`, when in this mode
you will get the info of each target

## Configuration
by changing the option `kake_how`, you can define if it does `automatic` mapping
based on the makefile targets, or if you want to look for a `.kake` file right
besides the first found makefile where you would manually map the targets
e.g.:

```
# .kake
run -> r p
test -> t
```
here run will automatically prompt when pressing r in `kake-mode`, while test will
run instantly

you can also set `kake_how` to `inline`, this way when parsing your makefile, `kake`
will try to look for a `<target> -> <key> <flag>*` pattern on the first comment block
on top of the target to decide how it should
work, when using `auto` though, the default is to always prompt so you can
set the variables, you can redefine this setting `kake_auto_prompt_always` to false,
also, `inline` will default to `auto` in case it doesn't find something resembling a kake
configuration line in the comments, if the target key is already taken that target
wont be loaded, kake will asume that since you selected `inline`, you are aware of what
you want, being inline just a more convenient way to configure things in comparison to
having a `.kake` file, you can set the option `kake_inline_strict` to true to make `inline` only load
targets that have the kake config line and discard the ones that don't.
