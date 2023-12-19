
# 1 Step

Clone Scratch GUI - Develop Branch 

```
git clone https://github.com/LLK/scratch-gui](https://github.com/LLK/scratch-gui
```

```
cd scratch-gui
npm install
npm start
```


# 2 For Using Other Scratch Packages

- Scratch VM
- Scratch Renderer
- Scratch Blocks
- Scratch Translation

## Clone the specific Repo

- Scratch VM (git clone [https://github.com/LLK/scratch-vm](https://github.com/LLK/scratch-vm))
- Scratch Renderer (git clone [https://github.com/LLK/scratch-render](https://github.com/LLK/scratch-render))
- Scratch Blocks (git clone [https://github.com/LLK/scratch-blocks](https://github.com/LLK/scratch-blocks))
- Scratch Translation (git clone https://github.com/scratchfoundation/scratch-l10n)

- cd scratch-vm
- cd scratch-render
- cd scratch-blocks

```
npm install
npm link
```

# scratch-vm and scratch-render

Run npm run watch. This will start another dev server which makes changes to the dependency trigger the automatic reload of scratch-gui.

# scratch-blocks 

This one is a little tougher. Every time you make a change to the code in scratch-blocks, you need to manually run the npm run prepublish command to rebuild scratch-blocks. (Make sure you run the command from the scratch-blocks directory!) Then, from the scratch-gui directory, stop and restart the dev server (ctrl+c to stop it if it's running, then npm start to restart it).


# Back to Scratch Gui Folder

- npm link scratch-vm  
- npm link scratch-render  
- npm link scratch-blocks




