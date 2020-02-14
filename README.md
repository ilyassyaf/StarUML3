Recently StarUML was updated from 2.0 to 3.0. The original crack method, how to modify the license verification function
can not be used. The installation location has changed and the LicenseManagerDomain.js file was found.
What should I do? The old driver told everyone to solve the problem.

StarUML is written in nodejs. Specifically, it is written on the front frame of Electron.
All starUML source code in the new version is packaged by the roasting tool.

# Enter the directory (Windows)

C:\Program Files\StarUML\resources

# Install the roasting tool

```bash
npm install -g asar
```

# Unpack StarUML

```bash
asar extract app.asar app
```
# Edit the license file

```bash
app\src\engine\license-manager.js
```

### Modify the code
Line 125

```js
  checkLicenseValidity () {
    this.validate (). then (() => {
      setStatus (this, true)
    }, () => {
    // ===> Change false to true
      setStatus (this, true)
      // ===> Comment Dialog
      // UnregisteredDialog.showDialog ()
    })
  }
```

# Repack StarUML

```bash
  asar pack app app.asar
```
 
# Run StarUML
 
Source: https://blog.csdn.net/sam_shan/article/details/80585240
