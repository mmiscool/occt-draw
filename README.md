WASM build of OpenCASCADE draw from build published at this link https://github.com/gkv311/occt-draw

Minimalist example for interfacing with the draw module provided in index.html

All the xterm.js stuff from the code provide here https://github.com/gkv311/occt-draw has been stripped out. 

```
    createDRAWEXE().then(async (theModule) => {
            await DRAWEXE.termEvaluateCommand( "ploadall");
            const result = await DRAWEXE.termEvaluateCommand( "help box");
            alert(result.result ? result.result : result.errors);
    });

```