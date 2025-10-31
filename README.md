# Diagram Studio

A lightweight, offline-first diagramming application for creating organizational charts and process flow diagrams. No installation, no internet connection, no external dependencies - just open and start diagramming.

![License](https://img.shields.io/badge/license-MIT-blue.svg)
![Version](https://img.shields.io/badge/version-1.0.0-green.svg)

## 🎯 Features

### Core Functionality
- **Infinite Canvas** with pan (Space + drag) and zoom (Ctrl/Cmd + scroll)
- **Org Chart Tools** - Executive, Manager, and IC role cards with "Add Direct Report" button
- **Process Flow Tools** - Start/End, Process, Decision, Data I/O, Connector, and Swimlane shapes
- **Smart Connectors** - Orthogonal routing with arrowheads
- **Drag & Drop** - Shape palette with visual previews

### Editing & Manipulation
- **Multi-Select** - Select multiple objects with Ctrl/Cmd + click or marquee selection
- **Resize & Move** - Drag handles to resize, drag shapes to reposition
- **Text Editing** - Double-click any shape to edit text inline
- **Undo/Redo** - 100-step history (Ctrl/Cmd + Z / Shift + Ctrl/Cmd + Z)
- **Keyboard Shortcuts** - Arrow keys to nudge, Del to delete, Ctrl/Cmd + D to duplicate
- **Context Menu** - Right-click for quick actions

### Organization & Layout
- **Auto-Layout** - "Tidy Tree" button for automatic org chart arrangement
- **Layer Control** - Bring to front, send to back
- **Lock/Unlock** - Prevent accidental edits
- **Grid & Snap** - Toggle-able grid with snap-to-grid behavior

### Persistence & Export
- **Auto-Save** - Saves to browser LocalStorage every 5 seconds
- **Export PNG** - High-quality 2x resolution export
- **Export SVG** - Vector format for infinite scalability
- **Save/Load JSON** - Manual backup and restore
- **Reusable Assets** - Save custom shapes for reuse across sessions

### Accessibility
- **High Contrast Mode** - Toggle for better visibility
- **Keyboard Navigation** - Full keyboard support
- **Respects Motion Preferences** - Honors `prefers-reduced-motion`

### Navigation
- **Mini-Map** - Bottom-right overview with draggable viewport indicator
- **Inspector Panel** - Edit properties of selected objects
- **Shape Library** - Organized tabs for Org, Process, and Saved assets

## 🚀 Quick Start

1. **Download** `index.html`
2. **Double-click** to open in your browser (Chrome, Edge, or Firefox)
3. **Start creating** - Drag shapes from the left sidebar onto the canvas

That's it! No installation, no setup, no internet required.

## 📋 Requirements

- Modern web browser:
  - Chrome 90+
  - Edge 90+
  - Firefox 88+
  - Safari 14+ (may have minor issues)
- JavaScript enabled
- LocalStorage enabled (for auto-save feature)

## 🎓 How to Use

### Creating Shapes
1. Click a tab in the left sidebar (Org or Process)
2. Drag a shape onto the canvas
3. Double-click to edit text

### Connecting Shapes
1. Click the "Connect" button in the toolbar
2. Click the first shape (starting point)
3. Click the second shape (ending point)
4. Connection is created automatically

### Building Org Charts
1. Drag an "Executive" shape onto the canvas
2. Select it
3. Click the blue "+" button below the shape
4. A connected child node is created automatically
5. Use "Tidy Tree" button to auto-arrange

### Keyboard Shortcuts

| Action | Shortcut |
|--------|----------|
| Undo | `Ctrl/Cmd + Z` |
| Redo | `Ctrl/Cmd + Shift + Z` |
| Delete | `Del` or `Backspace` |
| Duplicate | `Ctrl/Cmd + D` |
| Select All | `Ctrl/Cmd + A` |
| Group | `Ctrl/Cmd + G` |
| Nudge 1px | `Arrow Keys` |
| Nudge 10px | `Shift + Arrow Keys` |
| Pan Canvas | `Space + Drag` |
| Zoom | `Ctrl/Cmd + Mouse Wheel` |

### Exporting Your Work

**PNG Export:**
- Click "PNG" button in toolbar
- High-quality 2x resolution
- Transparent background option

**SVG Export:**
- Click "SVG" button in toolbar
- Vector format (scales infinitely)
- Editable in other vector tools

**JSON Backup:**
- Click "Save" button to download JSON
- Click "Load" button to restore from JSON
- Full fidelity - preserves all data

## 🏗️ Architecture

### Technology Stack
- **HTML5** - Structure and semantic markup
- **CSS3** - Styling with CSS Grid and Flexbox
- **Vanilla JavaScript** - No frameworks or libraries
- **SVG** - Vector graphics rendering
- **Canvas API** - PNG export functionality

### Design Patterns
- **Single-Page Application (SPA)** - Everything in one HTML file
- **State Management** - Centralized state object
- **Event-Driven Architecture** - Responds to user interactions
- **Immediate Mode Rendering** - Full re-render on state changes
- **Command Pattern** - Undo/redo with history stack

### File Structure
```
diagram-studio/
├── index.html          # Complete application (HTML + CSS + JS)
├── README.md          # This file
├── LICENSE            # MIT License
└── .gitignore         # Git ignore rules
```

### Data Model
```javascript
{
  "version": 1,
  "page": {
    "grid": 16,
    "snap": true
  },
  "nodes": [
    {
      "id": "n_1",
      "type": "org.manager",
      "x": 100,
      "y": 100,
      "w": 160,
      "h": 90,
      "style": { "fill": "#3b82f6", "stroke": "#2563eb" },
      "fields": { "role": "Manager", "name": "John Doe", "dept": "Engineering" }
    }
  ],
  "edges": [
    {
      "id": "e_1",
      "from": { "nodeId": "n_1" },
      "to": { "nodeId": "n_2" },
      "routing": "orthogonal"
    }
  ]
}
```

## 🔧 Customization

### Adding New Shapes
Edit the `NODE_TEMPLATES` object in the JavaScript section:

```javascript
const NODE_TEMPLATES = {
  org: {
    yourNewShape: {
      name: 'Your Shape',
      desc: 'Description',
      w: 150,
      h: 80,
      style: {
        fill: '#yourcolor',
        stroke: '#yourborder',
        strokeWidth: 2,
        textColor: '#ffffff'
      },
      fields: {
        label: 'Your Label'
      }
    }
  }
};
```

### Changing Colors
Modify CSS variables at the top of the `<style>` section:

```css
:root {
  --bg-primary: #f5f5f7;
  --accent-blue: #0071e3;
  /* ... etc */
}
```

### Adjusting Grid Size
Change the `GRID_SIZE` constant in JavaScript:

```javascript
const GRID_SIZE = 16; // Change to your preferred size
```

## 🐛 Troubleshooting

**App doesn't load:**
- Ensure JavaScript is enabled
- Try a different browser
- Check browser console for errors

**Auto-save not working:**
- Check if LocalStorage is enabled
- Clear browser cache and try again
- Some private browsing modes disable LocalStorage

**Export not working:**
- Ensure pop-ups are not blocked
- Try a different browser
- Check file permissions in your downloads folder

**Slow performance:**
- Reduce number of shapes (recommended: <500 nodes)
- Disable grid if not needed
- Clear browser cache

## 🤝 Contributing

Contributions are welcome! Here's how you can help:

1. Fork the repository
2. Create a feature branch (`git checkout -b feature/amazing-feature`)
3. Commit your changes (`git commit -m 'Add amazing feature'`)
4. Push to the branch (`git push origin feature/amazing-feature`)
5. Open a Pull Request

### Development Guidelines
- Keep everything in a single HTML file
- No external dependencies
- Comment complex logic
- Test in Chrome, Firefox, and Edge
- Maintain offline-first functionality

## 📝 License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

## 🙏 Acknowledgments

- Inspired by Microsoft Visio, Lucidchart, and Draw.io
- Built for users who need a simple, offline diagramming tool
- No telemetry, no tracking, no data collection

## 📧 Contact

Have questions or suggestions? Open an issue on GitHub!

## 🗺️ Roadmap

Future enhancements under consideration:

- [ ] Multiple pages/tabs
- [ ] Presentation mode (hide UI)
- [ ] CSV import for org charts
- [ ] More shape types
- [ ] Custom color palettes
- [ ] Shape search
- [ ] Keyboard shortcuts customization
- [ ] Touch/mobile support improvements

## 📊 Version History

### Version 1.0.0 (2024)
- Initial release
- Org chart support
- Process flow support
- Export to PNG/SVG
- Auto-save functionality
- Undo/redo
- Mini-map
- High contrast mode

---

**Made with ❤️ for people who need a simple, offline diagramming tool**
