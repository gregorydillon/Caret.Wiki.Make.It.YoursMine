Never gonna happen.

## Here's why

Caret's job is to be a text editor. That's what it does, and I think it does it well. It emulates (quite closely) Sublime Text and other text editors, and quite consciously does _not_ emulate Eclipse/Visual Studio/JetBrains. It is not trying to be an all-in-one solution. It has very little UI--things like JSON settings files are a win for coders, because they're easy to figure out, but also a win for me as a developer, because I need to do little to no work on making them function well if the fundamental text editing is there.

So adding a huge (and it would be huge) system for handling Git, or SFTP, or Drive synchronization, with all the specialized UI and commands that would require, goes directly against what I'm working toward with Caret. It would also mean writing or integrating those systems, none of which I understand particularly well. And it would mean a great deal more work for me on updating components and debugging when things break, all of which I already do just for Ace and none of which is particularly profitable (by choice).

Instead, Caret will continue to work well within an ecosystem of dedicated software, as with the UNIX philosophy of small, chainable tools. Although it is not built-in, Caret already works very well with Git tools (either the native version or any Chrome App that can watch a directory) by virtue of simply being a well-behaved file editor. Likewise for SFTP: Caret supports SSHFS on systems that can use it, simply by opening the folder that it creates.

## Drive Support

Drive support is a special case, since there are existing APIs for saving files to Drive. Unfortunately, the API for managing these files is completely different from the API used in other parts of the system. Luckily, there's a workaround.

On Chromebooks (and on other computers with the native Drive app installed), Caret is perfectly capable of opening files off the Drive folder, and saving them there again. If you do not have a Google Drive folder on your Chrome OS device, search your settings for the setting that enables it. Once this is done, you can edit synchronized files to your heart's content--you won't need me to add special support for it.