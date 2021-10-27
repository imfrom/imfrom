---
title: "Configuring Kakoune Kakrc"
date: 2017-12-06T03:22:08-04:00
draft: true
---


<!--# Configuring Kakoune Kakrc {#configuring-kakoune-kakrc .post-title}

[Dec 6, 2017]{.post-date}
-->

Configuring the [kakoune text editor](https://github.com/mawww/kakoune)
initialization file has been nothing short of a chore, as it requires
the path environment to be correctly set, before any changes on the
`kakrc` take ahold of the settings.

As the tutorial suggests, see [Configuration and
autoloading](https://github.com/mawww/kakoune#configuration-autoloading),
if it is launched with the `-n` switch, kakoune will source the
`../share/kak/kakrc`, but on a unrelated issue but nonetheless relevant
about the correct location for the initialization file, the developer
clearly stated that:

> The kakrc file in share is Kakounes init script, it is not intended to
> be user edited. It is actually that script that will load your user
> configuration in \~/.config/kak/kakrc.

![](/images/dont-use-share-kakrc.png)

See [clang completion
\#1102](https://github.com/mawww/kakoune/issues/1102)

Thus, it is necessary to set the environment first on any Unix system.
The command `setenv` is used for the **csh** shell, whereas in **bash**,
this is accomplished through the `export` command.

To find out whether for example, `XDG_CONFIG_HOME` was set, is necessary
to invoke on the terminal:

     printenv XDG_CONFIG_HOME

which if it does not return a value, the environment has not been set
yet.

To set the environment across sessions, note it accordingly on your
`bashrc` file with the `export` command:

     export XDG_CONFIG_HOME=$HOME/.config

create a directory **kak** under that environment, and further create
your init file **kakrc**

Most of the available settings will be available without further
modifications. That is, some of the commands that are loaded by not
using a `kakrc` file, will not have to be further tweaked with.

     colorscheme <tab completion> <name of theme>

can be identified without a problem.

There are, however, a handful of those that would have to be further
tweaked with, in order to load the **kakrc** init file correctly.

Take for example, `autowrap-enable`, which normally applies soft wrap
manipulation to the lines.

According to the developer,

> autowrapping is provided by the autowrap.kak script (which should be
> loaded by default), enable it for a buffer with the autowrap-enable
> command, that you probably want to put in a hook (for example if you
> want to always enable autowrap, add hook global WinCreate .\* %{
> autowrap-enable } in your kakrc. the autowrap_column option controls
> the column on which to autowrap.

See [Noob questions](https://github.com/mawww/kakoune/issues/419)

![](/images/autowrap-kakrc.png)

Further customizations to map certain keys are also necessary.

For example, to map the `\` backslash key to say the `;` semicolon.,
it's imperative to precede the \**\** key with the `%` percent sign and
further enclose the `\` backslash key within curly brackets `{}`, so the
final code would be something like:

     map buffer insert %{\} ';' 

of course, if the settings are desirable to be loaded globally, then

     map global insert %{\} ';'

needs to be specified accordingly on the initialization file.

See for example this issue: [can't map to
backslash](https://github.com/mawww/kakoune/issues/419), which touched
upon the problem, and further linked
<https://github.com/mawww/kakoune/issues/1049> and
<https://github.com/mawww/kakoune/issues/1221>

It's certainly two-fold that by specifying:

     map buffer insert ';' \ 

the behavior to have the `\` inserted, is easily accomplished, as shown
on the example above, but the same is not true, by having the same
characters inversed within the strings, that would yield the correct
results.

for example whereas

     map buffer insert ';' \ 

is correct, a simple `map buffer insert '\' ;`

throws an error with the message
`parse error: unterminated string '...'`

It's therefore necessary to have:

     map buffer insert %{;} \

the same is true if one were to `map buffer insert '\' %{;}`

one of the methods that would work across buffers, is to have such
characters enclosed within curly brackets and further preceded by the
`%` sign

     map buffer insert %{\} %{;} 

and

     map buffer insert %{;} %{\} 
:::
:::
:::

