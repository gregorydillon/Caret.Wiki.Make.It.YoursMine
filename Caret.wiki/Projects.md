To create a project, start by clicking Project > Add Directory, and pick a directory you'd like to show in the left-hand panel. You can now use this to navigate through the file in that directory--clicking a file will open it up in a new tab. If the file is already open, Caret will switch to that tab. You can clear your current directory by choosing Project > Remove All Directories.

It's possible to work like this, and for quick directory choices it may even make a lot of sense. But if you'd like to persist your project (i.e., to re-open directories after Caret is closed), or use custom project settings, you'll need to generate a project file. Choose Project > Save Project from the menu and decide where to save your file. Once you've created a project file, you can switch between them by choosing Open Project from the same menu.

Project files are just JSON, so they're easy to edit. They look roughly like this:

```json
{
  "folders": [
    { "path": "../../something", "retained": "43j2klfdu9432klfudsia:something" }
  ],
  "settings": {
    "indentation": 4
  }
}
```

If you've used Sublime project files, this should look pretty familiar. The "folders" property tells Caret which directories to open, and anything in "settings" will override your current user preferences, which is helpful when working on projects with different code styles. Please keep in mind that the folders property should not be changed manually, because Caret needs the correct file retained ID in order to re-open them on startup. If you want to change the folder, do so through the project menu only.

You can quickly open the project file through the menu, under Project > Edit Current Project File. Caret will watch any project file opened this way, and reload the changes when you save it, so this is a great way to test out project-specific configuration settings.

Finally, if you want to stop using a project file and go back to just regular Caret operation, choose Project > Clear Project from the menu. This will not delete your project file, but it will hide the navigation panel and unset any project-specific settings you were using.

## Additional Cautionary Notes

One of the frustrating things about the way files are retained on Chrome is that these project files are not strictly portable, because each machine will generate a unique retention ID for your project folders. As a result, it's not a good idea to check your project files into source control, unless you only work on one machine. 

That said, you can transfer a project file from place to place in order to load settings for a given project, and Caret will ignore any directories that it finds. Just be aware that saving the project file out again will overwrite the old folders--they're not merged, although that may be a smart thing to do in the future.