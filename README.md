# Metasys UI Custom Symbol Builder

A web-based tool for creating properly formatted custom symbol packages for Johnson Controls Metasys UI.

## Features

### Two Processing Modes

**1. Individual Symbols** - Manual symbol creation with full control
- Add symbols one by one
- Choose animation type (5-state, binary, or static)
- Upload specific images for each state
- Set custom point binding names
- Optional thumbnail upload (auto-generated if not provided)

**2. Batch Processing** - Automatic package generation from folder structure
- Process entire folders of symbols at once
- Auto-detects symbol types based on file naming
- Uses folder names as symbol names
- Supports regional organization
- Automatic thumbnail generation

## Getting Started

1. Save the HTML file locally
2. Open in a modern web browser (Chrome, Firefox, Edge)
3. Choose your processing mode

## File Naming Conventions (Batch Mode)

### 5-State Animation
- `frame_0.png` - 0% state
- `frame_1.png` - 25% state  
- `frame_2.png` - 50% state
- `frame_3.png` - 75% state
- `frame_4.png` - 100% state

### Binary Animation
- `state_off.png` - Off state
- `state_on.png` or `state_on.gif` - On state (supports animated GIFs)

### Static Symbol
- Any single image file

## Folder Structure Examples

### Without Regions
```
MySymbols/
├── WaterTankLarge/
│   └── frame_0.png through frame_4.png
├── ExhaustFan/
│   ├── state_off.png
│   └── state_on.gif
└── CompanyLogo/
    └── logo.png
```

### With Regions
```
MySymbols/
├── Asia/
│   └── WaterTankLarge/
│       └── frame_0.png through frame_4.png
├── Europe/
│   └── ExhaustFan/
│       ├── state_off.png
│       └── state_on.gif
```

## Output

The tool generates a ZIP file containing:
- `customSymbolLibrary.json` - Symbol configuration
- `csAnimations.js` - Animation logic (if needed)
- Symbol HTML files with embedded base64 images
- Thumbnails (280x280 PNG, auto-generated)
- Proper folder structure for Metasys UI import

## Technical Details

- Images are embedded as base64 in HTML files
- SVG dimensions match source image dimensions
- Thumbnails maintain aspect ratio on 280x280 canvas
- Point names default to symbol names (batch mode)
- Supports PNG, JPG, and GIF formats

## Requirements

- Modern web browser with JavaScript enabled
- No installation needed - runs entirely in browser
- No server or backend required

## Import to Metasys UI

1. Generate package using this tool
2. In Metasys UI, navigate to Graphics Manager
3. Select Tools → Import Custom Symbols
4. Upload the generated ZIP file
5. Refresh browser (Ctrl+F5) after import

## Browser Compatibility

- Chrome (recommended)
- Firefox
- Edge
- Safari (folder selection may vary)

## Notes

- Large images will create large HTML files due to base64 encoding
- Batch processing requires consistent file naming
- The favicon error when opening locally is normal and harmless
