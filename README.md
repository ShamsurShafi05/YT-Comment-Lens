# 🔍 YT-Comment-Lens

> A powerful browser extension that analyzes and summarizes YouTube comments using AI, helping you understand audience sentiment at a glance.

<img width="959" height="476" alt="YT-Comment-Lens-7" src="https://github.com/user-attachments/assets/38a3ca20-4466-48bc-8579-a0fddb35f6cd" />
<img width="958" height="473" alt="YT-Comment-Lens-9" src="https://github.com/user-attachments/assets/caa05418-7216-42e9-b497-d44b6d2802fc" />


## ✨ Features

- **📊 Comment Analysis** - Automatically analyze YouTube comment sections with AI-powered insights
- **💭 Sentiment Detection** - Understand the overall mood and tone of the audience (positive/neutral/negative breakdown)
- **📈 Key Insights Extraction** - Identify trending topics, top comments, common complaints, and engaging threads
- **🚨 Toxic Comment Detection** - Flags negative or harmful comments with severity levels
- **⚠️ Issues & Complaints Tab** - Surfaces error reports and viewer grievances in one place
- **🔥 Best Thread Finder** - Highlights the most engaging comment thread and its replies
- **🖱️ Hover Preview** - Hover over any video thumbnail for a quick comment stats preview
- **🖱️ Right-click Context Menu** - Right-click any video to analyze it or select it for comparison
- **📊 Multi-Video Comparison** - Select multiple videos from search results to compare their comment sentiment side by side
- **⚡ Lightweight & Fast** - Minimal performance impact on your browsing experience

## 🚀 Quick Start

### Prerequisites

- Chrome browser (version 88 or higher)
- YouTube Data API v3 key
- Groq API key (free tier available; multiple keys supported for rate-limit fallback)

### Installation

1. **Download the latest release**
   - Go to the [Releases page](https://github.com/yourusername/yt-comment-lens/releases)
   - Download the latest `.zip` file
   - Extract the contents to a folder on your computer

2. **Load the extension in Chrome**
   - Open `chrome://extensions/`
   - Enable "Developer mode" (toggle in top right)
   - Click "Load unpacked"
   - Select the extracted folder

### Configuration

After installing the extension:

1. Click the YT Comment Lens icon in your Chrome toolbar
2. Enter your **YouTube Data API v3 key**
3. Add one or more **Groq API keys** (keys rotate automatically when a rate limit is hit; the currently active key is shown with a green badge)
4. Set the number of **comments to fetch per video** (default: 60)
5. Click **"Save Settings"**

Your API keys are stored locally in your browser and never sent anywhere except to the respective API services.

### Getting API Keys

**YouTube Data API v3 (Required):**
1. Visit [console.cloud.google.com](https://console.cloud.google.com/)
2. Create a new project (or select an existing one)
3. Enable the **YouTube Data API v3**
4. Go to "Credentials" → "Create Credentials" → "API Key"
5. Copy your API key

**Groq API (Required for AI analysis):**
1. Visit [console.groq.com](https://console.groq.com/)
2. Sign up or log in
3. Navigate to "API Keys" and create a new key
4. Copy keys starting with `gsk_...`

💡 **Tip:** Add multiple Groq API keys — the extension automatically rotates to the next key when a rate limit is hit, ensuring uninterrupted analysis.

## 📖 Usage

### Analyzing a Single Video

1. Navigate to any YouTube video page
2. Click the YT Comment Lens icon in your Chrome toolbar
3. Click **"Analyze Comments"**
4. Wait a few seconds while the AI analyzes the comments
5. Browse the results across tabs

### Analyzing from Search Results

- **Hover** over any video thumbnail to see a quick comment stats preview
- **Right-click** any video for options:
  - **Analyze this video** — opens the full analysis panel
  - **Select for comparison** — adds the video to a comparison selection
- **Select multiple videos** using the checkboxes, then click **"Analyze Selected"** in the floating bar to compare them side by side

### Analysis Tabs

| Tab | What you'll see |
|-----|-----------------|
| **Overview** | Quality score, total comments analyzed, toxic count, sentiment breakdown (positive/neutral/negative %), overall summary, and top themes |
| **Top** | Best comments ranked by likes and replies, each labeled (supportive, insightful, etc.) with an AI-generated summary |
| **Toxic** | Negative or harmful comments flagged with a severity level (low/medium/high) and a brief explanation |
| **Issues** | Complaints, bug reports, and viewer grievances, each tagged as "issue" with a summary |
| **Thread** | The most engaging comment thread, including its top replies |

### Multi-Video Panel

When hovering over a video in search results, a compact preview card appears showing:
- Number of comments analyzed
- Quality score
- Toxic count and complaint count
- Positivity bar (positive / neutral / negative %)
- A short summary of the overall sentiment

## 🛠️ Development

### Project Structure

```
yt-comment-lens/
├── src/
│   ├── popup/          # Extension popup UI
│   ├── content/        # Content scripts for YouTube
│   ├── background/     # Service worker scripts
│   └── utils/          # Shared utilities
├── public/             # Static assets
├── dist/               # Built extension (gitignored)
└── manifest.json       # Extension manifest
```

### Available Scripts

```bash
npm run dev          # Start development server with hot reload
npm run build        # Build for production
npm run test         # Run test suite
npm run lint         # Lint code with ESLint
```

### Contributing

Contributions are welcome! Please follow these steps:

1. Fork the repository
2. Create a feature branch (`git checkout -b feature/amazing-feature`)
3. Commit your changes (`git commit -m 'Add amazing feature'`)
4. Push to the branch (`git push origin feature/amazing-feature`)
5. Open a Pull Request

## 🔒 Security & Privacy

- **Local Storage Only** — Your API keys are stored securely in your browser's local storage
- **No Data Storage** — Comments are analyzed in real-time and never stored on any server
- **Direct API Calls** — Keys are sent only directly to YouTube's API and Groq's API
- **No Tracking** — No user data or analytics are collected
- **Open Source** — Full transparency; review the code yourself

⚠️ **Security Tips:**
- Never share your API keys with anyone
- Each user must obtain and configure their own API keys
- Regularly rotate your API keys for security
- Review your API provider's usage dashboard periodically

## 🐛 Troubleshooting

**Extension not loading:**
- Ensure Developer Mode is enabled in Chrome (`chrome://extensions/`)
- Try removing and re-adding the extension
- Check the browser console for error messages

**API errors or "Invalid API Key":**
- Verify your YouTube Data API v3 key is correct and the API is enabled in your Google Cloud project
- Verify your Groq key starts with `gsk_` and is active in your Groq console
- Ensure there are no extra spaces before or after any key
- Check that you have remaining quota on both services

**"Failed to analyze comments":**
- Check your internet connection
- Ensure both the YouTube API and Groq API are not experiencing downtime
- If you hit a Groq rate limit, add another Groq API key — the extension will rotate automatically
- Try refreshing the YouTube page and analyzing again

**No comments detected:**
- Refresh the YouTube page after installing the extension
- Scroll down to load comments first, then analyze
- Some videos may have comments disabled by the creator

**Hover preview or right-click menu not appearing:**
- Refresh the YouTube page
- Ensure the extension is enabled in `chrome://extensions/`

## 🙏 Acknowledgments

- Powered by the [Groq API](https://console.groq.com/) for fast AI inference
- Uses the [YouTube Data API v3](https://developers.google.com/youtube/v3) for comment retrieval
- Inspired by the need for better comment section navigation

## 📞 Support

- 📧 **Email:** m.s.shafi2001@gmail.com
