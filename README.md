# Html_Source_Code_Editor_Titan
A minimalist HTML compression tool with live editing and preview live file.

 Titan HTML Editor

A minimalist HTML compression tool with live editing and preview capabilities using the modern gzip streaming API. Edit, compress, and preview HTML files in real-time with an intuitive drag-and-drop interface.

## Features

- **Live HTML Editing**: Real-time code editor with syntax highlighting
- **Gzip Compression**: Compress HTML using the native CompressionStream API
- **Live Preview**: Instant preview of your HTML changes in an isolated iframe
- **Drag-and-Drop**: Simply drag HTML files into the editor to load them
- **File Processing**: Save compressed or uncompressed HTML files
- **Compression Stats**: View original vs compressed file sizes
- **Base64 Encoding**: Export compressed data as Base64 for easy sharing
- **Zero Dependencies**: Pure vanilla JavaScript with no external libraries
- **Responsive Design**: Works seamlessly on desktop and mobile devices

## Installation

### Option 1: Direct Usage

1. Clone the repository:
```bash
git clone https://github.com/yourusername/titan-html-editor.git
cd titan-html-editor
```

2. Open `index.html` in your web browser:
```bash
# On macOS
open index.html

# On Linux
xdg-open index.html

# On Windows
start index.html
```

No build process or installation required!

### Option 2: Local Server (Recommended)

For best results, serve the files using a local web server:

```bash
# Using Python 3
python -m http.server 8000

# Using Node.js (with npx)
npx serve

# Using PHP
php -S localhost:8000
```

Then navigate to `http://localhost:8000` in your browser.

## Usage

### Basic Editing

1. **Type or Paste HTML**: Use the editor panel to write or paste your HTML code
2. **Live Preview**: See changes instantly in the preview pane
3. **Compress**: Click the "Compress" button to gzip your HTML
4. **Download**: Save the compressed or original file to your device

### Drag-and-Drop

1. Drag any HTML file onto the editor area
2. The file content will be loaded automatically
3. Edit and compress as needed

### Compression Workflow

1. Load or write your HTML content
2. Click "Compress with Gzip" to compress the content
3. View compression statistics (original size vs compressed size)
4. Download the compressed `.gz` file or Base64 encoded output
5. Use "Decompress" to restore the original HTML

### Keyboard Shortcuts

- `Ctrl/Cmd + S`: Save current HTML file
- `Ctrl/Cmd + O`: Open file dialog
- `Ctrl/Cmd + K`: Compress HTML
- `Ctrl/Cmd + L`: Clear editor

### API Usage Example

```javascript
// Compress HTML using CompressionStream API
async function compressHTML(htmlString) {
  const blob = new Blob([htmlString], { type: 'text/html' });
  const stream = blob.stream();
  const compressedStream = stream.pipeThrough(
    new CompressionStream('gzip')
  );
  const compressedBlob = await new Response(compressedStream).blob();
  return compressedBlob;
}

// Decompress gzipped HTML
async function decompressHTML(compressedBlob) {
  const stream = compressedBlob.stream();
  const decompressedStream = stream.pipeThrough(
    new DecompressionStream('gzip')
  );
  const decompressedBlob = await new Response(decompressedStream).blob();
  return await decompressedBlob.text();
}
⬇ README.md
