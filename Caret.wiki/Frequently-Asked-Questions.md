Frequently Asked Questions
==========================

### Does Caret support Google Drive/SFTP/Dropbox/other remote storage providers?

Indirectly, yes. Caret is capable of saving to anything that looks like a local filesystem, which includes the Google Drive directory on Chromebooks and on computers with the Drive client installed. It will also save to any other folder that maps to a remote resource. But it will not save to these remote locations directly, and I don't have any intention of adding this feature.

### Can Caret add support for language X?

If Ace supports it, Caret can as well. By default, to keep the package size down, not all languages are shipped, but they can be added pretty easily. File an issue (including the file extensions that should be associated with that syntax) and I'll get it added.

### Does Caret support plugins?

Yes! You can send Caret commands through the standard Chrome app messaging system. A list of commands is available [here](https://github.com/thomaswilburn/Caret/wiki/Commands). You can also send messages from Caret to external applications from a keystroke or menu item: look at the External API settings file for more information.

### Can Caret open files from the command line?

Not as far as I know. This is a limitation of Chrome apps, but I believe the Chromium team is working on a solution.

### Feature X is broken in vim emulation mode. Can you fix it?

Vim mode is completely unsupported in Caret: it was enabled as an opt-in feature because it's built into Ace, so it required me to do very little to turn it on. However, I wrote Caret specifically because I didn't want to learn vim on my Chromebook, and I do not use the emulation mode, _ever_, which means that I will neither find nor fix any bugs that exist in it. Use at your own risk.

### I'd like to help make Caret better. How can I get started?

Great question! Help is always appreciated. If you're a technical type, clone the repo and take a look at contributing.txt to answer any questions you might have about style. If you're not a coder, you can still help out: file bugs, help write documentation, work on the UI design, and answer questions!