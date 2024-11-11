
# How to Install NPM on Windows

NPM (Node Package Manager) is a tool used to manage JavaScript libraries and tools in your project. To install NPM, you need to install Node.js, as NPM comes bundled with it.

---

## Step 1: Download Node.js
1. Visit the official Node.js website: [https://nodejs.org/](https://nodejs.org/).
2. Download the **LTS (Long-Term Support)** version for Windows. This version is recommended for most users because it’s stable and reliable.

---

## Step 2: Install Node.js
1. Open the downloaded installer (e.g., `node-vxx.x.x-x64.msi`).
2. Follow the installation wizard:
   - Accept the license agreement.
   - Choose the installation location (default is `C:\Program Files\Node.js`).
   - Leave all default settings unless you have specific requirements.
3. Complete the installation.

---

## Step 3: Verify Installation
1. Open **Command Prompt** or **PowerShell**.
2. Check the version of Node.js installed:
   ```bash
   node --version
   ```
   Example output:
   ```
   v18.16.0
   ```
3. Check the version of NPM installed:
   ```bash
   npm --version
   ```
   Example output:
   ```
   9.5.1
   ```

---

## Step 4: Update NPM (Optional)
The version of NPM bundled with Node.js might not be the latest. To update NPM to the latest version, run:
```bash
npm install -g npm
```

Verify the updated version:
```bash
npm --version
```

---

## Step 5: Test NPM
To test if NPM is working, install a sample package like `lodash`:
1. Create a new directory for testing:
   ```bash
   mkdir npm-test
   cd npm-test
   ```
2. Initialize a new NPM project:
   ```bash
   npm init -y
   ```
3. Install the `lodash` package:
   ```bash
   npm install lodash
   ```
4. Check that the `node_modules` folder and `package.json` file are created.

---

## Troubleshooting
1. **Command Not Found**:
   - Ensure Node.js is added to your PATH during installation. If not, reinstall Node.js and check the PATH option during setup.
2. **Permission Issues**:
   - Run the command prompt or PowerShell as an administrator.

---

## Summary
You’ve successfully installed NPM on Windows. With NPM, you can now manage JavaScript libraries, install tools like Laravel Mix, and compile frontend assets in your Laravel projects.

Happy coding! 🚀
