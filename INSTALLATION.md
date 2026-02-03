# Installation & Setup Guide

## Quick Start (5 minutes)

### Step 1: Prepare the Extension

1. Extract/download all files to a folder called `eye-tracking-magnifier`
2. The folder should contain:
   - manifest.json
   - content.js
   - background.js
   - popup.html
   - popup.js
   - calibration.html
   - welcome.html
   - styles.css
   - tracker.js
   - README.md
   - icons/ (folder)

### Step 2: Create Icons (Optional)

You can use any 16x16, 48x48, and 128x128 PNG images as icons, or create simple ones:

**Option A: Use Online Tool**
1. Go to https://favicon.io/favicon-generator/
2. Create three sizes: 16x16, 48x48, 128x128
3. Save them in the `icons/` folder

**Option B: Use Placeholder**
Create simple colored squares in any image editor and save as:
- `icons/icon16.png` (16x16 pixels)
- `icons/icon48.png` (48x48 pixels)
- `icons/icon128.png` (128x128 pixels)

**Option C: Use ImageMagick (Linux/Mac)**
```bash
cd icons/
./create_icons.sh
```

### Step 3: Load Extension in Browser

#### Google Chrome / Microsoft Edge / Brave
1. Open browser and navigate to: `chrome://extensions/`
2. Enable "Developer mode" (toggle switch in top-right)
3. Click "Load unpacked"
4. Select the `eye-tracking-magnifier` folder
5. Extension loaded! ✅

#### Opera
1. Navigate to: `opera://extensions/`
2. Enable "Developer mode"
3. Click "Load unpacked"
4. Select the extension folder

### Step 4: Configure Permissions

1. After loading, click "Details" on the extension
2. Enable these permissions:
   - ✅ "Allow access to file URLs" (for PDFs)
   - ✅ "Allow in Incognito" (optional)

### Step 5: First Use

1. Click the extension icon in your browser toolbar
2. Toggle the switch to "ON"
3. Choose one of two modes:
   - **Mouse Tracking**: Works immediately, no setup
   - **Eye Tracking**: Click "Calibrate" for hands-free reading

## Advanced Configuration

### Adding Real Eye Tracking (Optional)

The extension includes a placeholder for WebGazer.js. To enable full eye tracking:

**Method 1: Download WebGazer.js**
1. Visit: https://webgazer.cs.brown.edu/
2. Download `webgazer.js`
3. Rename to `tracker.js`
4. Replace the placeholder file
5. Reload extension

**Method 2: Use CDN (Already Configured)**
The extension will attempt to load WebGazer from CDN automatically.

### Browser-Specific Setup

#### Chrome
No additional setup needed - works out of the box!

#### Firefox (Converting to Firefox Add-on)
1. Rename `manifest.json` to `manifest-chrome.json`
2. Create new `manifest.json` with:
```json
{
  "manifest_version": 2,
  "browser_specific_settings": {
    "gecko": {
      "id": "eye-tracker@example.com"
    }
  }
  // ... rest of manifest
}
```
3. Install via `about:debugging`

#### Safari (Requires Conversion)
Use Apple's converter: https://developer.apple.com/documentation/safariservices/safari_web_extensions

### Keyboard Shortcut Setup

1. Go to `chrome://extensions/shortcuts`
2. Find "Eye Tracking Magnifier"
3. Set shortcut (e.g., `Ctrl+Shift+E` or `Cmd+Shift+E`)
4. Use keyboard to toggle extension on/off

## Testing the Extension

### Test Checklist

- [ ] Extension loads without errors
- [ ] Icon appears in toolbar
- [ ] Popup opens with settings
- [ ] Toggle switch works
- [ ] Mouse tracking magnifies text
- [ ] Magnification level slider works
- [ ] Speed slider works
- [ ] Settings are saved
- [ ] Works on regular web pages
- [ ] Works on PDF files
- [ ] Calibration page opens

### Test on Different Content

1. **Text-heavy website**: Try Wikipedia or news sites
2. **PDF Document**: Open a PDF and test magnification
3. **Dynamic content**: Try social media feeds
4. **Different fonts**: Test various websites

### Performance Testing

Monitor these in Chrome DevTools (F12):
- **CPU Usage**: Should be minimal when idle
- **Memory**: Should not increase over time
- **Network**: No external requests (except WebGazer CDN)
- **Console**: No error messages

## Troubleshooting Installation

### "Manifest file is missing or unreadable"
- Ensure `manifest.json` exists
- Check for JSON syntax errors
- Validate at: https://jsonlint.com/

### "Failed to load extension"
- Check all required files are present
- Ensure file paths in manifest match actual files
- Reload extension from extensions page

### Icons Not Showing
- Verify icon files exist in `icons/` folder
- Check file names match manifest.json exactly
- Try using different icon images

### Extension Not Working on Some Sites
- Check if site is blocked (chrome:// pages, browser settings)
- Verify "Allow access to file URLs" is enabled for PDFs
- Some sites may have Content Security Policy restrictions

### Performance Issues
- Disable other extensions temporarily
- Check Chrome Task Manager (Shift+Esc)
- Lower magnification level
- Increase transition speed

## Updating the Extension

1. Make changes to files
2. Go to `chrome://extensions/`
3. Click reload button (circular arrow) on extension card
4. Test changes

## Distribution

### Create Package File

1. Go to `chrome://extensions/`
2. Click "Pack extension"
3. Select extension directory
4. (Optional) Select private key if updating
5. Share generated `.crx` file

### Chrome Web Store Publishing

1. Create developer account: https://chrome.google.com/webstore/devconsole
2. Pay one-time $5 fee
3. Prepare store listing:
   - Screenshots (1280x800 or 640x400)
   - Promotional images
   - Description
   - Privacy policy
4. Upload extension ZIP
5. Submit for review

### Alternative Distribution

- Share folder via GitHub/GitLab
- Provide installation instructions
- Users load unpacked in developer mode

## Security Best Practices

### Before Publishing

1. Review all permissions
2. Test on multiple browsers
3. Validate manifest.json
4. Scan for security issues
5. Test with different content types
6. Verify privacy compliance

### Code Review

Check for:
- No hardcoded credentials
- No external data collection
- Proper error handling
- Input validation
- XSS prevention

## Support & Maintenance

### Keeping Extension Updated

1. Monitor browser extension API changes
2. Test with new browser versions
3. Update WebGazer.js periodically
4. Review user feedback
5. Fix reported bugs promptly

### User Support

Provide:
- Clear README documentation
- FAQ section
- Contact information
- Bug reporting process
- Feature request channel

## Next Steps

After installation:
1. ✅ Test basic functionality
2. ✅ Calibrate eye tracking
3. ✅ Customize settings
4. ✅ Set keyboard shortcut
5. ✅ Test on various websites
6. ✅ Share with others!

---

## Quick Reference

**Enable Extension**: Click icon → Toggle ON  
**Settings**: Click icon → Adjust sliders  
**Calibrate**: Click icon → Calibrate button  
**Keyboard Shortcut**: chrome://extensions/shortcuts  
**Reload Extension**: chrome://extensions/ → Reload  
**View Console**: F12 → Console tab  

Happy reading! 👁️📖
