# Testing Guide

## Pre-Installation Testing

### File Integrity Check
```bash
# Verify all required files exist
ls -la eye-tracking-magnifier/

# Expected files:
# - manifest.json
# - content.js
# - background.js
# - popup.html
# - popup.js
# - calibration.html
# - welcome.html
# - styles.css
# - tracker.js
# - README.md
# - INSTALLATION.md
# - PERFORMANCE.md
# - icons/icon16.png
# - icons/icon48.png
# - icons/icon128.png
```

### Manifest Validation
1. Visit: https://jsonlint.com/
2. Copy contents of `manifest.json`
3. Click "Validate JSON"
4. Should show "Valid JSON" ✅

## Basic Functionality Tests

### Test 1: Extension Loading
**Objective**: Verify extension loads without errors

1. Open `chrome://extensions/`
2. Enable Developer mode
3. Click "Load unpacked"
4. Select extension folder
5. **Expected**: No errors, extension appears in list
6. **Expected**: Extension icon visible in toolbar

### Test 2: Popup Opens
**Objective**: Settings UI works correctly

1. Click extension icon
2. **Expected**: Popup window opens
3. **Expected**: All UI elements visible:
   - Enable toggle
   - Magnification slider
   - Speed slider
   - Sensitivity slider
   - Calibrate button

### Test 3: Toggle Enable/Disable
**Objective**: Extension can be turned on/off

1. Click extension icon
2. Toggle switch to ON
3. **Expected**: Status text changes to "Active"
4. Toggle switch to OFF
5. **Expected**: Status text changes to "Currently disabled"

### Test 4: Mouse Tracking Mode
**Objective**: Text magnifies with mouse movement

1. Enable extension
2. Visit any text-heavy website (e.g., Wikipedia)
3. Move mouse over text
4. **Expected**: Text enlarges as mouse hovers
5. Move mouse away
6. **Expected**: Text returns to normal size

### Test 5: Settings Persistence
**Objective**: Settings are saved correctly

1. Open extension popup
2. Change magnification to 2.0x
3. Change speed to 300ms
4. Close popup
5. Reopen popup
6. **Expected**: Settings remain at 2.0x and 300ms

### Test 6: PDF Support
**Objective**: Extension works on PDF files

1. Enable "Allow access to file URLs" in extension details
2. Open a PDF file in browser
3. Enable extension
4. Move mouse over text
5. **Expected**: PDF text magnifies
6. **Note**: May not work on scanned PDFs

## Advanced Functionality Tests

### Test 7: Dynamic Content
**Objective**: Works on dynamically loaded content

1. Visit a social media site (Twitter, Reddit)
2. Enable extension
3. Scroll and load new content
4. Move mouse over new text
5. **Expected**: New text also magnifies

### Test 8: Multiple Tabs
**Objective**: Works independently in each tab

1. Open 3 different websites in separate tabs
2. Enable extension in Tab 1
3. Test magnification works
4. Switch to Tab 2
5. **Expected**: Extension also enabled in Tab 2
6. Disable in Tab 2
7. Switch to Tab 1
8. **Expected**: Still enabled in Tab 1

### Test 9: Page Refresh
**Objective**: Persists after page reload

1. Enable extension on a page
2. Refresh the page (F5)
3. **Expected**: Extension still enabled
4. **Expected**: Magnification still works

### Test 10: Different Text Elements
**Objective**: Works on various HTML elements

Test on these elements:
- [ ] Regular paragraphs (`<p>`)
- [ ] Headings (`<h1>` to `<h6>`)
- [ ] Links (`<a>`)
- [ ] List items (`<li>`)
- [ ] Spans (`<span>`)
- [ ] Divs with text (`<div>`)
- [ ] Table cells (`<td>`, `<th>`)
- [ ] Strong/Bold text (`<strong>`, `<b>`)

## Performance Tests

### Test 11: CPU Usage
**Objective**: Verify low CPU consumption

1. Open Chrome Task Manager (Shift+Esc)
2. Find "Extension: Eye Tracking Magnifier"
3. Enable extension and use it
4. **Expected**: CPU usage < 5% during active use
5. **Expected**: CPU usage < 1% when idle

### Test 12: Memory Usage
**Objective**: No memory leaks

1. Open Chrome Task Manager
2. Note initial memory usage
3. Use extension for 5 minutes
4. Check memory again
5. **Expected**: Memory increase < 10 MB
6. **Expected**: Memory stable (no continuous growth)

### Test 13: Battery Impact
**Objective**: Minimal battery drain (laptop only)

1. Disconnect power
2. Note battery percentage
3. Use extension for 30 minutes
4. Note battery percentage
5. **Expected**: Similar drain to normal browsing
6. **Expected**: <3% additional drain per hour

### Test 14: Idle Detection
**Objective**: Pauses when inactive

1. Enable extension
2. Use for a few seconds
3. Leave browser idle for 1 minute
4. Open DevTools console
5. **Expected**: No continuous logging
6. **Expected**: Processing paused

## Compatibility Tests

### Test 15: Chrome
- **Version**: 88+
- **Expected**: Full functionality ✅

### Test 16: Microsoft Edge
- **Version**: 88+
- **Expected**: Full functionality ✅

### Test 17: Brave
- **Version**: Latest
- **Expected**: Full functionality ✅

### Test 18: Opera
- **Version**: Latest
- **Expected**: Full functionality ✅

## UI/UX Tests

### Test 19: Smooth Transitions
**Objective**: Animations are smooth

1. Set transition speed to 200ms
2. Move mouse over text
3. **Expected**: Smooth size change (no jittering)
4. **Expected**: Consistent animation timing

### Test 20: No Layout Shift
**Objective**: Page layout remains stable

1. Visit a responsive website
2. Enable extension
3. Hover over text
4. **Expected**: No page jumping
5. **Expected**: Surrounding elements don't move

### Test 21: Accessibility
**Objective**: Works with accessibility features

1. Enable browser's accessibility tools
2. Enable extension
3. Test with:
   - [ ] Screen reader
   - [ ] High contrast mode
   - [ ] Reduced motion settings
4. **Expected**: No conflicts

## Error Handling Tests

### Test 22: No Internet Connection
**Objective**: Works offline

1. Disconnect internet
2. Enable extension
3. Test on local pages
4. **Expected**: Mouse tracking works
5. **Expected**: No error messages

### Test 23: Blocked Websites
**Objective**: Gracefully handles restrictions

1. Try on `chrome://extensions/`
2. **Expected**: Extension doesn't work (browser restriction)
3. **Expected**: No errors in console
4. Try on regular website
5. **Expected**: Works normally

### Test 24: Rapid Settings Changes
**Objective**: Handles quick adjustments

1. Rapidly move all sliders
2. Toggle on/off quickly multiple times
3. **Expected**: No errors
4. **Expected**: Settings apply correctly
5. **Expected**: No freezing or lag

## Calibration Tests

### Test 25: Calibration Page Opens
**Objective**: Calibration UI loads

1. Click "Calibrate Eye Tracking"
2. **Expected**: New tab opens
3. **Expected**: Calibration interface visible
4. **Expected**: Instructions displayed

### Test 26: Camera Permission
**Objective**: Handles camera access

1. Start calibration
2. Allow camera access
3. **Expected**: Camera preview appears
4. **Expected**: Calibration points show

### Test 27: Camera Denied
**Objective**: Graceful fallback

1. Start calibration
2. Deny camera access
3. **Expected**: Clear error message
4. **Expected**: Suggests mouse tracking mode
5. **Expected**: Automatically closes after delay

## Edge Cases

### Test 28: Very Long Text
**Objective**: Handles large content

1. Visit page with very long article (10,000+ words)
2. Enable extension
3. Scroll through entire article
4. **Expected**: Consistent performance
5. **Expected**: No slowdown

### Test 29: Tiny Text
**Objective**: Works with small fonts

1. Find page with 8px font size
2. Enable extension
3. Set magnification to 3.0x
4. **Expected**: Text readable when magnified
5. **Expected**: Returns to tiny size when unfocused

### Test 30: Rapid Element Changes
**Objective**: Handles fast DOM updates

1. Visit page with auto-updating content (live feed)
2. Enable extension
3. Watch for several minutes
4. **Expected**: No memory leaks
5. **Expected**: Continues working smoothly

### Test 31: Nested Elements
**Objective**: Handles complex HTML structure

1. Visit page with deeply nested divs
2. Enable extension
3. Hover over text in nested elements
4. **Expected**: Finds and magnifies correct text
5. **Expected**: No duplicate magnification

### Test 32: Overlapping Text
**Objective**: Handles layered content

1. Visit page with text over images or background
2. Enable extension
3. Hover over overlapping text
4. **Expected**: Only focused text magnifies
5. **Expected**: No z-index issues

## Regression Tests

After making any code changes, run:
- [ ] All Basic Functionality Tests (1-6)
- [ ] Test 11 (CPU Usage)
- [ ] Test 12 (Memory Usage)
- [ ] Test 19 (Smooth Transitions)

## Automated Testing Script

Save as `test.js` and run with `node test.js`:

```javascript
// Automated manifest validation
const fs = require('fs');
const path = require('path');

console.log('Running automated tests...\n');

// Test 1: Check all files exist
const requiredFiles = [
  'manifest.json',
  'content.js',
  'background.js',
  'popup.html',
  'popup.js',
  'calibration.html',
  'welcome.html',
  'styles.css',
  'tracker.js'
];

let allFilesExist = true;
requiredFiles.forEach(file => {
  if (fs.existsSync(file)) {
    console.log(`✓ ${file} exists`);
  } else {
    console.log(`✗ ${file} MISSING`);
    allFilesExist = false;
  }
});

// Test 2: Validate manifest.json
try {
  const manifest = JSON.parse(fs.readFileSync('manifest.json', 'utf8'));
  console.log('\n✓ manifest.json is valid JSON');
  
  // Check required fields
  if (manifest.manifest_version === 3) {
    console.log('✓ Using Manifest V3');
  }
  if (manifest.permissions) {
    console.log('✓ Permissions defined');
  }
  if (manifest.content_scripts) {
    console.log('✓ Content scripts defined');
  }
} catch (e) {
  console.log('\n✗ manifest.json has errors:', e.message);
}

// Test 3: Check icons directory
if (fs.existsSync('icons')) {
  console.log('\n✓ Icons directory exists');
  const icons = ['icon16.png', 'icon48.png', 'icon128.png'];
  icons.forEach(icon => {
    if (fs.existsSync(`icons/${icon}`)) {
      console.log(`  ✓ ${icon}`);
    } else {
      console.log(`  ✗ ${icon} missing`);
    }
  });
} else {
  console.log('\n✗ Icons directory missing');
}

console.log('\n' + (allFilesExist ? 'All tests passed! ✅' : 'Some tests failed ❌'));
```

## Bug Report Template

If you find issues, report using this template:

```
**Bug Description:**
Brief description of the issue

**Steps to Reproduce:**
1. Step one
2. Step two
3. Step three

**Expected Behavior:**
What should happen

**Actual Behavior:**
What actually happened

**Environment:**
- Browser: Chrome/Edge/Brave/Opera
- Version: X.X
- OS: Windows/Mac/Linux
- Extension Version: 1.0.0

**Console Errors:**
Paste any errors from DevTools console

**Screenshots:**
Attach if helpful
```

## Test Results Log

Record test results:

```
Test Date: YYYY-MM-DD
Tester: Name
Browser: Chrome 120
OS: Windows 11

Test Results:
✅ Test 1: Extension Loading
✅ Test 2: Popup Opens
✅ Test 3: Toggle Enable/Disable
✅ Test 4: Mouse Tracking
⚠️  Test 5: Settings Persistence (minor issue)
❌ Test 6: PDF Support (not working)
...

Issues Found:
1. Settings slider doesn't save on first try
2. PDF support requires additional permission step

Notes:
Overall functionality is good. Need to fix settings persistence bug.
```

## Continuous Testing

### Daily Checks
- [ ] Extension loads without errors
- [ ] Basic magnification works
- [ ] No console errors

### Weekly Checks
- [ ] All functionality tests
- [ ] Performance benchmarks
- [ ] Memory usage check

### Before Release
- [ ] Complete test suite
- [ ] Cross-browser testing
- [ ] Performance validation
- [ ] Security audit
- [ ] User acceptance testing

---

Happy Testing! 🧪
