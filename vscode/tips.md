


# Tips

- You can creat a file with path. For example, create a file as x/y/filename and create the file with path. You can use the [extension](#create-files--folders--on-the-go) for this purpose. 
  
- Switch between explore window and editor window: ctrl + shift+ E 
- Switch between editor window and terminal window: ctrl + j or ctrl + `
- Switch between opened files: 
  - ctrl + <number> : you need to know the tab number
  - ctrl + tab : provide you the list of opened files
- Open a file fro editing
  - ctrl + e
- Selete current line: ctrl + l
- Delete a line 
  - ctrl + k
- Go to the end of line: ctrl + end
- Go to the beginning of line: ctrl + home
- Move code snippet up or down
  - Linux: Alt + up/down
- Multiline editing
  - ctrl + atl + shift
- Side-by-side editing
  - ctrl + \
- Navigation history
  - Navigate entire history: Ctrl+Tab
  - Navigate back: Alt+Left
  - Navigate forward: Alt+Right
- Close the currently opened folder
  - Keyboard Shortcut: Ctrl+K F
- Copy line up / down
  - Keyboard Shortcut: Shift+Alt+Up or Shift+Alt+Down
- Move line up and down
  - Keyboard Shortcut: Alt+Up or Alt+Down
- Go to Symbol in Workspace
  - Keyboard Shortcut: Ctrl+T
- Create a file link in markdown file
  - Press shift and drag the file

## Create Files & Folders : On The Go

**How to use?**
- Keyboard Shortcut: ctrl+alt+N to create new files & ctrl+alt+shift+N to create new folders. (you can override these shortcuts).
- Press ctrl+shift+p to open command panel and type Create File or Create Folder.
- Right click on Explorer Window and click Create File or Create Folder.

**Feature**
- Create Files or Folder : Type /path/subpath/TestPath or /path/subpath/fileName.js
- Create Multiple files on the go : Type /path/subpath/file1 > file2 > file3 to create multiple file (file1, file2, file3) at a time in /path/subpath/ path.

## Paste Image
**How Paste Image woks**
1. Create a snapshot to the clipboard.
2. Paste on VSCode markdown file (Ctrl+Alt+v).
3. A link is pasted in markdown file like ![](img/YYYY-MM-DD-hh-mm-ss.png)
4. The image file is saved in the folder as YYYY-MM-DD-hh-mm-ss.png.

Use the following settings to save the images in file specific folder:
- ${projectRoot}/xyz/${currentFileNamewithoutExt}
- ${currentFileDir}/image

Links:
- https://www.janmeppe.com/blog/paste-image/
- https://marketplace.visualstudio.com/items?itemName=mushan.vscode-paste-image
- 