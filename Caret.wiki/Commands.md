Caret is powered by a command architecture: menus, keyboard events, and plugins respond to command/argument messages for almost all user-facing operations (and many internal operations, as well). This page lists all the known commands and their effects, should you want to customize your menus or keyboard mappings.

Commands consist of two parts, the command string and an (optional) argument. Command strings are themselves split into two parts: the namespace and the verb, separated by a colon. Arguments are not required for all commands, but allow some commands to operate in different ways or with some variation. Browsing through the menu and keyboard settings should show numerous examples of these commands in action, and they are also often attached to Caret's DOM elements by way of `command` and `argument` attributes.

### App commands
- `app:minimize` - Hide the Caret window.
- `app:maximize` - Maximize the Caret window (_not_ fullscreen mode).
- `app:restart` - Restart Caret and reload its background page.
- `app:debug` - If dev tools are open, pause JavaScript execution and enter the debugger.
- `app:exit` - Close the Caret window.
- `app:about` - Display the "About Caret" dialog.
- `app:check-for-updates` - query the update server for the latest version. If there is a newer version, Caret will display a notification and prompt you to restart.

### Editor commands
- `ace:command` - Triggers Ace commands through its `execCommand` method. The argument is the Ace command you want to fire. See Ace docs/source for more information.
- `ace:togglemacro` - Turns Ace's macro recording on or off, and displays its state in the statusbar.
- `editor:insert` - Calls Ace's `insert()` method with the text specified in the argument.
- `editor:default-zoom` - Resets the zoom to its default size.
- `editor:adjust-zoom` - Moves the font size up or down by the number of pixels passed into the argument.
- `editor:theme` - Change the editor's theme to the value specified by the argument.
- `sublime:expand-to-line`
- `sublime:expand-to-paragraph`
- `sublime:expand-to-matching`
- `sublime:tabs-to-spaces`
- `sublime:spaces-to-tabs`
- `editor:word-count` - Shows the character/word/line counts for the current document in the status bar.
- `editor:print` - Opens a print dialog for the current tab. Printed documents will use the current editor theme, which may not be what you want if you're trying to save ink.
- `ace:trim-whitespace` - Trims whitespace from the end of each line. 
- `editor:insert` - Insert the text specified in the argument at the current cursor location. Useful for writing plugins.

### Session commands (tab management)
- `session:new-file` - Opens a new tab. If an argument is provided, it will be used as the starting content. If not, it'll be empty.
- `session:open-file` - Opens a new tab from a file.
- `session:save-file` - Saves the file. If the file is new, will ask where to save.
- `session:save-file-as` - Like `session:save-file` but always asks for a destination.
- `session:revert-file` - Reload the tab's contents from disk.
- `session:check-file` - Test to see if the file has been modified since it was last loaded.
- `session:open-settings-file` - Open one of the JSON settings "files" from sync storage. The argument should specify the file name.
- `session:open-settings-defaults` - Open the default form of the settings JSON.
- `session:open-dragdrop` - Internal use only. Opens a file from a mouse drag-and-drop.
- `session:open-launch` - Internal use only. Opens files from the Files app.
- `session:insert-from-file` - Opens a file dialog, then inserts the selected file's contents at the cursor location.
- `session:raise-tab` - Bring the tab at the index specified by the argument to the foreground. Will also fire `session:check-file`.
- `session:close-tab` - Close the current tab. Will ask to save if the contents have been modified.
- `session:change-tab` - Jumps to the last used tab (Sublime's default Ctrl-Tab behavior). Not usually called through commands. If the Ctrl key is held, you can keep stepping back through the tab stack.
- `session:change-tab-linear` - Moves forward or back by the specified number of tabs (Chrome's Ctrl-Tab behavior).
- `session:render` - Internal use only. Used to trigger a re-render of the tab elements.
- `session:syntax` - Set the current tab's syntax to the mode specified by the argument (do not include the `ace/mode/` prefix).

### Project commands
- `project:add-dir` - Open the "Add directory" window.
- `project:remove-all` - Strip all directories from the current project.
- `project:generate` - Trigger the "Save Project File" action.
- `project:open-file` - Open a file in the project, specifying the file's display path in the argument.
- `project:refresh-dir` - Reload the directory listing in the project navigator panel.
- `project:open` - Ask the user for the location of a project file and load it.
- `project:edit` - Open the current project file in a new tab and watch it for changes.
- `project:clear` - Unset the current project from memory.

### Other UI
- `app:show-prompt` - Show the "command prompt" for manually entering Caret commands.
- `app:hide-prompt` - Hide the command prompt.
- `palette:open` - Show the command/go-to palette. You can specify a mode as the argument: `command`, `line`, `reference`, and `search` are valid options.
- `status:set` - Display a message in the status bar.
- `status:clear` - Remove any message in the status bar.
- `status:toast` - Display a message in the status bar, then remove it automatically. Recommended over `status:set` and `status:clear`, and useful for posting information from plugins.

### API/Plugin commands (still in beta)
- `api:execute` - Looks in the External Commands JSON file and fires off a command matching the ID provided in the argument. See the JSON file for how these commands should be structured. You can use this to send messages to other Chrome apps and extensions, assuming they can accept messages from Caret.
- Other applications can send messages to Caret's ID with the following format:
```javascript
{
  command: "commandName",
  argument: "optional"
}
```
This format should look familiar if you've edited the keys.json or menus.json files at all.

### Internal commands (module-to-module communication)
- `init:startup` - Fired when Caret starts up, once all settings are loaded for the first time.
- `init:restart` - Fired when settings files change or are reloaded, so that modules can reinitialize to the new values.
- `init:complete` - Fired when all retained files have been loaded during initial startup, so that launch commands can be safely run.
- `settings:change-local` - Notify the settings module that a virtual settings file has been changed and needs to be reloaded from storage.
- `settings:delete-local` - Erase any custom settings JSON for the file specified in the command argument.