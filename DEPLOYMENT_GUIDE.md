# Deployment and Distribution Guide

This guide explains how to make your Unity game more accessible to players.

## 🎮 Current Setup: GitHub Releases (Implemented)

The repository is now configured to automatically create downloadable releases. Here's how it works:

### Automatic Release Creation

A GitHub Actions workflow is set up to package your game. To create a new release:

1. Create a git tag with version number:
   ```bash
   git tag v1.0.0
   git push origin v1.0.0
   ```

2. The workflow will automatically:
   - Package the game into a ZIP file
   - Create a GitHub release
   - Upload the ZIP file as a downloadable asset
   - Add instructions for players

### Manual Release Creation

You can also create releases manually:

1. Go to your repository on GitHub
2. Click "Releases" in the right sidebar
3. Click "Draft a new release"
4. Create a tag (e.g., v1.0.0)
5. Add a title and description
6. Upload the game ZIP file manually
7. Click "Publish release"

## 🌐 Making Your Game Playable in Web Browsers

To make your game playable in browsers, you need to create a WebGL build in Unity:

### Creating a WebGL Build

1. **Open your Unity project**

2. **Switch to WebGL platform:**
   - Go to File → Build Settings
   - Select "WebGL" from the platform list
   - Click "Switch Platform"

3. **Configure WebGL settings:**
   - Go to Edit → Project Settings → Player
   - Under WebGL settings, configure:
     - Compression Format: Choose Gzip or Brotli
     - Memory Size: Set appropriate memory (default 256MB)
     - Exception Support: Choose "None" for smaller builds

4. **Build the game:**
   - File → Build Settings → Build
   - Choose a folder (e.g., "WebGL Build")
   - Wait for the build to complete

5. **Test locally:**
   - The build creates an `index.html` file
   - You need a local web server to test (Unity includes one)
   - Or use Python: `python -m http.server 8000`

### Hosting Your WebGL Build

#### Option 1: GitHub Pages (Free)

1. Create a new folder in your repository: `docs/game/`
2. Copy all WebGL build files to this folder
3. Go to repository Settings → Pages
4. Enable Pages and set source to `main` branch, `/docs` folder
5. Your game will be available at: `https://yourusername.github.io/Sinclair-Secrets-Game/game/`

**Note:** GitHub Pages has a 1GB soft limit. Your current build (~102MB) + WebGL build might exceed this.

#### Option 2: itch.io (Recommended for Unity Games)

[itch.io](https://itch.io) is a popular platform for indie games:

1. Create a free account at https://itch.io
2. Click "Upload New Project"
3. Fill in game details
4. For WebGL builds:
   - Set "Kind of project" to "HTML"
   - Upload your WebGL build as a ZIP
   - Check "This file will be played in the browser"
5. Set visibility (public/unlisted/private)
6. Click "Save & view page"

**Benefits:**
- No file size restrictions
- Built-in game discovery
- Analytics
- Payment options if you want to sell
- Comments and ratings
- Free hosting

#### Option 3: Netlify (Free tier available)

1. Sign up at https://netlify.com
2. Drag and drop your WebGL build folder
3. Get a free URL: `yoursite.netlify.app`

#### Option 4: GameJolt

Similar to itch.io, another gaming platform:
1. Create account at https://gamejolt.com
2. Upload your game
3. Set it as browser-playable or downloadable

## 📦 Creating a Better Download Experience

### Option 1: Use GitHub Releases (Already Implemented)

The repository now has automated releases! Just create a tag to trigger a new release.

### Option 2: Use a Download Page

The included `index.html` file provides a nice landing page with:
- Download button
- Game description
- System requirements
- Video link

To enable it:
1. Go to repository Settings → Pages
2. Enable Pages, source: `main` branch, root folder
3. Your page will be at: `https://yourusername.github.io/Sinclair-Secrets-Game/`

## 🚀 Recommended Workflow

1. **For Windows Downloads:**
   - Use GitHub Releases (already set up)
   - Players can download from Releases page
   - Or use the included landing page

2. **For Web Browser Play:**
   - Create a WebGL build in Unity
   - Host on itch.io (easiest and most feature-rich)
   - Alternative: Host on GitHub Pages if build size permits

3. **Best of Both Worlds:**
   - Keep Windows build on GitHub Releases
   - Put WebGL build on itch.io
   - Update your landing page to link to both options

## 📝 Tips for WebGL Builds

1. **Optimize for web:**
   - Reduce texture sizes
   - Use texture compression
   - Minimize audio file sizes
   - Reduce polygon counts if possible

2. **Test in different browsers:**
   - Chrome, Firefox, Edge, Safari
   - Some features may not work in all browsers

3. **Consider build size:**
   - Players need to download the build files
   - Smaller is better for web (aim for under 50MB if possible)
   - Use compression (Gzip or Brotli)

4. **Note about performance:**
   - WebGL builds may run slower than native
   - Some Unity features aren't supported in WebGL
   - First-person games usually work well

## 🔗 Additional Resources

- [Unity WebGL Documentation](https://docs.unity3d.com/Manual/webgl-building.html)
- [itch.io Creator Guide](https://itch.io/docs/creators/html5)
- [GitHub Pages Documentation](https://docs.github.com/en/pages)

## 💡 Quick Start: What You Should Do Next

1. **Create your first release:**
   ```bash
   git tag v1.0.0
   git push origin v1.0.0
   ```

2. **Enable GitHub Pages:**
   - Settings → Pages → Enable (main branch, root folder)

3. **Consider creating a WebGL build:**
   - Open Unity project
   - Build for WebGL
   - Host on itch.io or GitHub Pages

4. **Share your game:**
   - Share the Releases link or GitHub Pages URL
   - Post on game dev communities
   - Share on social media
