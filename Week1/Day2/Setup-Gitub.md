# How to Download and Set Up STS and GitHub Copilot

**STS** (Spring Tools Suite) is an Eclipse-based IDE for building Spring and Spring Boot applications. This guide covers installing it, creating a first project, and adding GitHub Copilot.

---

## 1. Prerequisites

| Requirement | Details |
|---|---|
| JDK | JDK 17 or newer (21 recommended). Check with `java -version`. |
| OS | Windows 10/11, macOS (Intel or Apple Silicon), or Linux |
| Disk / RAM | ~1 GB disk, 4 GB RAM minimum (8 GB recommended) |
| GitHub account | Needed for Copilot, with an active Copilot plan (Free, Pro, Business or Enterprise) |

### Install a JDK (if you don't have one)
- Download from [Adoptium Temurin](https://adoptium.net) or [Oracle JDK](https://www.oracle.com/java/technologies/downloads/).
- Run the installer, then confirm in a terminal:
  ```bash
  java -version
  javac -version
  ```
- Set `JAVA_HOME` if the IDE can't find the JDK.

---

## 2. Download STS

1. Go to the official page: **https://spring.io/tools**
2. Pick the build for your OS:
   - Windows: `.zip` or self-extracting `.jar`
   - macOS: `.dmg` (choose Intel x86_64 or Apple Silicon aarch64)
   - Linux: `.tar.gz`
3. Save the file to a normal folder such as Downloads.

> Download only from spring.io. Third-party mirrors can be outdated or tampered with.

---

## 3. Install STS

### Windows
1. Extract the zip to a short path, e.g. `C:\sts`. Avoid long paths and folders with spaces.
2. Open the extracted folder and run `SpringToolSuite4.exe`.

### macOS
1. Open the `.dmg` and drag **SpringToolSuite4** into **Applications**.
2. First launch: right-click the app, choose **Open**, then confirm (Gatekeeper warning).

### Linux
```bash
tar -xzf spring-tool-suite-4-*.tar.gz -C ~/
cd ~/sts-*
./SpringToolSuite4
```

---

## 4. First Launch

1. When asked for a **workspace**, choose or create a folder (e.g. `~/sts-workspace`). Tick *Use this as the default* if you like.
2. Wait for the Welcome screen to load, then close it.
3. Confirm the JDK: **Window > Preferences > Java > Installed JREs** (on macOS: **Spring Tool Suite 4 > Settings**). Add or select your JDK 17+ and tick it as default.

### Optional: increase memory
Edit `SpringToolSuite4.ini` (on macOS: right-click the app > *Show Package Contents* > `Contents/Eclipse/`) and adjust:
```
-Xms512m
-Xmx2048m
```

---

## 5. Create a Test Spring Boot Project

1. **File > New > Spring Starter Project**
2. Fill in name, Maven or Gradle, Java version, and package.
3. Click **Next**, add dependencies (e.g. *Spring Web*), then **Finish**.
4. Wait for dependencies to download (progress bar bottom right).
5. Right-click the project > **Run As > Spring Boot App**.
6. Open http://localhost:8080 to confirm it runs.

---

## 6. Set Up GitHub Copilot in STS

STS is built on Eclipse, so you use the official **GitHub Copilot for Eclipse** plugin.

### 6.1 Check requirements
- A Copilot-enabled GitHub account. Free plan: https://github.com/features/copilot
- A recent STS 4 build (based on Eclipse 2024-09 or newer is recommended).

### 6.2 Install the plugin
1. In STS, open **Help > Eclipse Marketplace...**
2. Search for **GitHub Copilot**.
3. Click **Install** on *GitHub Copilot* (publisher: GitHub).
4. Accept the license, confirm the trust prompt, and click **Finish**.
5. When prompted, **Restart** STS.

If the Marketplace is missing or the search fails, use **Help > Install New Software...** and add the update site URL listed on the plugin's Marketplace page or in the GitHub Copilot docs.

### 6.3 Sign in to GitHub
1. After restart, click the **Copilot icon** in the bottom status bar (or use the **GitHub Copilot** menu).
2. Choose **Sign in to GitHub**.
3. A device code appears. Click **Copy and Open**, then paste the code in the browser page at https://github.com/login/device.
4. Click **Authorize GitHub Copilot Plugin**.
5. Return to STS. The status icon should show you're signed in.

### 6.4 Use Copilot
- **Inline suggestions:** Start typing in a `.java` file. Grey ghost text appears.
  - `Tab` accepts a suggestion
  - `Esc` dismisses it
- **Comment prompts:** Write a comment like `// method to reverse a string` and press Enter to get a suggestion.
- **Chat:** Open **Window > Show View > Other > GitHub Copilot > Chat** (or use the Copilot menu). Ask questions, explain code, generate tests, or fix errors.
- **Select code + right-click > Copilot** for options such as *Explain*, *Fix*, or *Generate Tests*.

### 6.5 Settings
Open **Window > Preferences > GitHub Copilot** to:
- Enable or disable completions per language
- Configure proxy settings (needed on some corporate networks)
- Adjust chat and completion behavior

---

## 7. Troubleshooting

| Problem | Fix |
|---|---|
| STS won't start | Check JDK 17+ is installed and `JAVA_HOME` is set. Try the `-vm` option in `SpringToolSuite4.ini` pointing at your JDK. |
| macOS says app is damaged or from an unidentified developer | Right-click > **Open**. Or run `xattr -cr /Applications/SpringToolSuite4.app`. |
| Copilot not in Marketplace | Update STS via **Help > Check for Updates**, or install via **Install New Software** with the update site. |
| Sign-in loops or fails | Make sure your account has Copilot access. Check https://github.com/settings/copilot. Try signing out and in again. |
| No suggestions appear | Confirm you're signed in, the file type is enabled in Preferences, and the file isn't excluded by your org policy. |
| Behind a corporate proxy | Set the proxy in **Window > Preferences > General > Network Connections**, and in the Copilot preferences. |
| Project errors after import | Right-click project > **Maven > Update Project** (Alt+F5), or **Gradle > Refresh Gradle Project**. |

---

## 8. Quick Checklist

- [ ] JDK 17+ installed and verified
- [ ] STS downloaded from spring.io/tools
- [ ] STS extracted/installed and launched
- [ ] Workspace and JDK configured
- [ ] Test Spring Boot project runs
- [ ] GitHub Copilot plugin installed and STS restarted
- [ ] Signed in to GitHub and getting suggestions

---

*Note: menu names and plugin details can change between STS and Copilot releases. If something looks different, check https://spring.io/tools and the GitHub Copilot documentation.*
