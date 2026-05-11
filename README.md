# Subtitles to Text Converter

A simple and efficient tool to extract plain text from subtitle files by removing timestamps and formatting, leaving only the readable content.

## 📋 Description

This project converts `.srt` (SubRip) subtitle files into clean, readable text files. It automatically removes:
- Timestamp information (e.g., `00:00:00,000 --> 00:00:05,000`)
- Subtitle sequence numbers
- Extra blank lines

The result is a clean text file containing only the dialogue or content from the subtitle file, perfect for reading or processing textual content without subtitle metadata.

## ✨ Features

- ✅ Converts SRT subtitle format to plain text
- ✅ Removes timestamps and metadata
- ✅ Removes subtitle numbering
- ✅ Cleans up extra whitespace and blank lines
- ✅ Preserves the order and content of dialogue/captions
- ✅ UTF-8 encoding support
- ✅ Simple and fast processing

## 🛠️ Requirements

- Python 3.6 or higher
- No external dependencies required (uses only Python standard library)

## 📦 Installation

1. Clone this repository:
```bash
git clone https://github.com/mayankanand3007/subtitles-to-text.git
cd subtitles-to-text
```

2. No additional packages need to be installed (uses only Python built-ins)

## 🚀 Usage

### Option 1: Run as a Jupyter Notebook
1. Open `app.ipynb` in Jupyter Notebook or JupyterLab
2. Ensure your subtitle file is named `subtitles.srt` in the same directory
3. Run the notebook
4. The output will be saved as `text.txt`

### Option 2: Run as a Python Script
If you prefer to run this as a standalone Python script, you can extract the code from the notebook:

```python
import re

with open("subtitles.srt", "r", encoding="utf-8") as f:
    content = f.read()

# Remove timestamps
content = re.sub(r"\d{2}:\d{2}:\d{2},\d{3} --> .*", "", content)

# Remove subtitle numbers
content = re.sub(r"^\d+$", "", content, flags=re.MULTILINE)

# Remove extra blank lines
content = re.sub(r"\n\s*\n", "\n\n", content)

with open("text.txt", "w", encoding="utf-8") as f:
    f.write(content.strip())

print("Conversion complete! Output saved to text.txt")
```

## 📝 Example

### Input (subtitles.srt):
```
1
00:00:00,000 --> 00:00:05,000
Hello, welcome to this video.

2
00:00:05,500 --> 00:00:10,000
Today we'll learn about subtitles.

3
00:00:10,500 --> 00:00:15,000
Thanks for watching!
```

### Output (text.txt):
```
Hello, welcome to this video.

Today we'll learn about subtitles.

Thanks for watching!
```

## 📂 Project Structure

```
subtitles-to-text/
├── README.md                    # Project documentation
├── app.ipynb                    # Main Jupyter notebook
├── subtitles.srt               # Sample input subtitle file
├── text.txt                    # Generated output text file
├── powerbi.txt                 # Example output file
└── Power BI Expert.srt         # Example subtitle file
```

## 🔧 How It Works

The script uses Python's `re` module to perform three main regex operations:

1. **Remove timestamps**: Removes lines matching the pattern `HH:MM:SS,mmm --> ...`
2. **Remove sequence numbers**: Removes standalone numbers that typically appear before each subtitle
3. **Clean whitespace**: Consolidates multiple consecutive newlines into double newlines for readability

## 🎯 Use Cases

- Extract text content from video subtitles for analysis
- Convert subtitles to transcripts for documentation
- Process subtitle files for text mining or NLP tasks
- Create plain text versions of video dialogue
- Generate searchable text from subtitle content

## 📄 License

This project is open source and available under the MIT License. See LICENSE file for details (or add your preferred license).

## 🤝 Contributing

Contributions are welcome! If you have suggestions for improvements or find any issues, please feel free to:
1. Open an issue
2. Submit a pull request
3. Provide feedback

## 💡 Future Enhancements

Potential improvements for future versions:
- Support for multiple subtitle formats (VTT, ASS, etc.)
- Command-line interface with arguments
- Batch processing for multiple files
- Output formatting options
- Language-specific processing

## 📧 Contact

For questions or suggestions, please reach out through the GitHub repository issues section.

---

**Happy converting!** 🎬✨
