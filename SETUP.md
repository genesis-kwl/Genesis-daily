# Genesis Daily — GitHub Pages Setup

## One-time setup (requires gh CLI or GitHub web)

### Option A: Using gh CLI
```bash
brew install gh
gh auth login
gh repo create genesis-daily --public --source=/Users/genesis/CoreAOS/genesis-daily --remote=origin --push
```

### Option B: Manual (GitHub web)
1. Go to https://github.com/new
2. Create repo named `genesis-daily` (public)
3. Copy the repo URL
4. Run:
```bash
cd ~/CoreAOS/genesis-daily
git remote add origin https://github.com/YOUR_USERNAME/genesis-daily.git
git push -u origin main
```

### Enable GitHub Pages
1. Go to repo Settings > Pages
2. Source: Deploy from a branch
3. Branch: main, folder: / (root)
4. Save

### Update the URL
After setup, update `GITHUB_PAGES_URL` in `~/CoreAOS/tools/morning_news.py` with your actual URL:
```
https://YOUR_USERNAME.github.io/genesis-daily/
```

## Daily operation
The `morning_news.py` script handles everything automatically:
- Fetches news from RSS feeds + Hacker News API
- Fetches crypto prices from CoinGecko
- Generates the HTML page
- Commits and pushes to GitHub Pages
- Sends a Telegram summary with the GitHub Pages link
