## About ##

Bashets is an alternative widget system for Awesome window manager allowing you to simply use your shellscript's output as a source for Awesome widget's content.

When some other projects are trying to reinvent the wheel in Lua, the aim of this solution is to enable users to quickly create powerful widgets using existing shellscripts they are used to use. That's why the coverage of such custom widgets is limited only by user's fantasy.

Note: Bashets is currently only compatible with awesome-git, not with the stable version. If you want to use it on stable, please modify the util.get\_widget\_meta function to work with old-fashion widgets and email a patch to ahmad200512 <[at](at.md)> yandex.ru.

## Latest version ##

Latest version is [0.6.2](http://bashets.googlecode.com/files/bashets.lua) for Awesome-git.

There is an AUR package for Arch Linux: http://aur.archlinux.org/packages.php?ID=30612

  * Example [userscripts](http://code.google.com/p/bashets/source/browse/userscripts) could also be downloaded.

See https://gitorious.org/bashets/pages/Brief_Introduction for configuration details.
Sorry, but I support actual documentation only for gitorious.

## Example ##

  * I have a shellscript `mpdstatus.sh` with an output like this:

> `❚❚|Threshold - The Art of Reason|0:03/10:21`

  * I add following lines to my `rc.lua`:

> `mpdw = widget({ type = "textbox", name = "mpdw"})`

> `bashets.register("mpdstatus.sh", {widget=mpdw, format=' | <span color="black" face="Monospace">$1</span>  $2 : $3', update_time=1, separator='|'})`

> and..

  * Now I have small "media player" on my wibox.

> Also there is a support for widgets with a "long pause" before they produce any output implemented through the register\_async function. For example, here is a volume level widget:

> `vlw = widget({type="textbox",name="vlw"})`

> `bashets.register("vollevel.sh Master", {widget=vlw, format=' <span color="black">V:</span> $1%', update_time=2, file_update_time=1, async=true})`


It is simple and powerful, right?

Also there is support for dbus events listening, for external (not timed) script execution, for callbacks, and more to come.

And there is support for non-text widgets: graphs, progressbars, imageboxes.