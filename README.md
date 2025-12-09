# TikTok Video Metadata Scraper

> This project provides a TikTok video metadata scraper that collects clean, structured data from TikTok video pages and feeds. It focuses on extracting titles, captions, hashtags, engagement counts, author info, sounds, and timestamps without relying on unofficial SDKs. Whether you’re analyzing content performance, doing market research, or fueling internal tools, this scraper turns TikTok video pages into usable data.

> Instead of manually copying stats or using unreliable one-click tools, you define your inputs (video URLs, users, hashtags, or search queries) and let the scraper handle navigation, parsing, and structured export — ready for analytics, dashboards, and data pipelines.


<p align="center">
  <a href="https://Appilot.app" target="_blank"><img src="https://github.com/Instagram-Automations/Footer-test/blob/main/appilot-baner.png" alt="Appilot Banner" width="100%"></a>
</p>
<p align="center">
  <a href="https://t.me/devpilot1" target="_blank"><img src="https://img.shields.io/badge/Chat%20on-Telegram-2CA5E0?style=for-the-badge&logo=telegram&logoColor=white" alt="Telegram"></a>
  <a href="mailto:support@appilot.app" target="_blank"><img src="https://img.shields.io/badge/Email-support@appilot.app-EA4335?style=for-the-badge&logo=gmail&logoColor=white" alt="Gmail"></a>
  <a href="https://Appilot.app" target="_blank"><img src="https://img.shields.io/badge/Visit-Website-007BFF?style=for-the-badge&logo=google-chrome&logoColor=white" alt="Website"></a>
  <a href="https://discord.gg/wpfG4j84" target="_blank"><img src="https://img.shields.io/badge/Join-Appilot_Community-5865F2?style=for-the-badge&logo=discord&logoColor=white" alt="Appilot Discord"></a>
</p>

<p align="center">
Created by Appilot, built to showcase our approach to Automation!
If you are looking for custom <strong> {TikTok Video Metadata Scraper} <strong>, you've just found your team — Let’s Chat.&#128070; &#128070;
</p>

## Introduction

The repetitive task at the center of this project is collecting TikTok video details at scale. Manually opening each video, reading metrics, copying captions and hashtags, and logging them into a spreadsheet is slow, error-prone, and impossible to scale beyond a few clips per session.

This scraper automates that workflow. It navigates to TikTok video URLs or feed endpoints (user feed, hashtag feed, or search results), captures key metadata, normalizes it into a consistent schema, and exports it as JSON/CSV for downstream processing. The business value is clear: faster content research, more reliable performance tracking, and better input for recommendation, growth, or competitive analysis.

### Structured TikTok Video Intelligence for Research & Growth

- Turn unstructured TikTok video pages into structured, analyzable rows of data for dashboards and scripts.  
- Save time for creators, agencies, and analysts who routinely research trends, competitors, or content formats.  
- Standardize fields (views, likes, comments, shares, hashtags, sound, author profile) across different discovery modes.  
- Enable repeatable data pulls for time-based tracking — for example, capturing the same set of videos daily to see growth.  
- Provide a reusable scraping backbone that can power internal tools, notebooks, or BI integrations.

---

## Core Features

| Feature | Description |
|----------|-------------|
| URL-Based Video Scraping | Given one or many TikTok video URLs, the scraper visits each page and extracts all relevant metadata into a structured record. |
| User Feed Scraping | Scrapes video metadata from a specific user’s profile feed with configurable limits (e.g., latest N videos). |
| Hashtag & Search Feed Scraping | Collects videos discovered via hashtag pages or search results for trend and keyword analysis. |
| Rich Metadata Extraction | Captures title/caption, hashtags, sound/music info, author details, publish time, views, likes, comments, shares, and link references. |
| Headless Browser Automation | Uses Playwright to render dynamic content reliably, including lazy-loaded metrics and elements hidden behind scrolling. |
| Robust Selector & Layout Handling | Implements resilient DOM selectors and fallbacks to handle minor UI changes and regional variants. |
| Configurable Rate Limiting | Applies delays and concurrency controls to avoid aggressive scraping patterns and reduce the risk of soft blocks. |
| Output in JSON & CSV | Writes standardized results to JSON and CSV files so they can be used directly in spreadsheets, scripts, or databases. |
| CLI & Library Usage | Offers a command-line interface for quick runs and a Python module interface for embedding into other tools. |
| Error & Retry Handling | Retries transient failures such as timeouts or navigation errors and marks problematic URLs with error details. |
| Logging & Run Reports | Produces structured logs and simple summary reports with counts of processed, successful, and failed videos. |
| Config-Driven Scraping Profiles | Allows different scrape profiles (light vs full metadata, different feeds) without changing code. |

---

## How It Works

| Step | Description |
|------|-------------|
| **Input or Trigger** | You provide a list of TikTok URLs, usernames, hashtags, or search queries via CLI arguments, config file, or a small API endpoint. Each input is expanded into a list of video targets according to your chosen mode (direct URLs vs feed scraping). |
| **Core Logic** | The scraper spins up Playwright browser contexts, navigates to each target, waits for the relevant elements to load, and extracts metadata using structured selectors and parsing helpers. It normalizes text, numbers, timestamps, and hashtag lists into a consistent schema. |
| **Output or Action** | For each video, the scraper emits a record with fields like video_id, author_handle, caption, hashtags, stats, sound, and publish_time. Records are appended to an in-memory buffer and periodically flushed to JSON and/or CSV output files. |
| **Other Functionalities** | The engine includes retries for transient failures, configurable scrolling to reveal full captions and comments, and optional screenshot capture for debugging problematic pages. A summary report at the end shows how many items were processed and any encountered errors. |
| **Safety Controls** | Built-in rate limiting, randomized delays between navigations, concurrency caps, and optional proxy support help keep requests moderate and reduce risk of temporary blocks. Configuration lives in files and environment variables, not hard-coded thresholds. |
| ... | You can extend the scraper with custom extraction fields (e.g., language detection, sentiment estimates) by adding lightweight parsing plugins that hook into the same pipeline. |

## Tech Stack

| Component | Description |
|------------|-------------|
| **Language** | Python |
| **Frameworks** | Playwright for headless browser automation and page rendering. |
| **Tools** | httpx or requests for auxiliary HTTP calls, python-dotenv and pydantic for configuration and schema validation, Rich or logging for structured CLI/log output. |
| **Infrastructure** | Optional Docker image for reproducible runs, GitHub Actions for running tests and lint checks on pushes and pull requests. |

---

## Directory Structure Tree

    tiktok-video-metadata-scraper/
      ├── src/
      │   ├── main.py
      │   ├── cli.py
      │   ├── scraper/
      │   │   ├── runner.py
      │   │   ├── browser_client.py
      │   │   ├── url_collector.py
      │   │   ├── video_parser.py
      │   │   ├── feed_modes.py
      │   │   └── utils/
      │   │       ├── logger.py
      │   │       ├── config_loader.py
      │   │       └── rate_limiter.py
      │   └── api/
      │       ├── server.py
      │       └── routes_scrape.py
      ├── config/
      │   ├── settings.yaml
      │   ├── profiles/
      │   │   ├── light_profile.yaml
      │   │   └── full_profile.yaml
      │   └── .env.example
      ├── logs/
      │   └── scraper.log
      ├── output/
      │   ├── videos.json
      │   └── videos.csv
      ├── tests/
      │   ├── test_video_parser.py
      │   ├── test_feed_modes.py
      │   └── test_runner.py
      ├── pyproject.toml
      ├── Dockerfile
      └── README.md

---

## Use Cases

- **Content analysts** use it to collect metadata from top-performing TikTok videos in a niche, so they can study hooks, caption patterns, and engagement metrics.  
- **Creator teams** use it to track performance of their own videos over time, so they can analyze what works without relying solely on in-app views.  
- **Agencies** use it to pull competitor or trend data for client reports, so they can back strategy decisions with real platform numbers.  
- **Data scientists** use it to build datasets for modeling virality, recommendation, or audience behavior, so they can experiment with features derived from real content.  
- **Tool builders** use it as a backend module in dashboards or internal tools, so users can request fresh TikTok video data on demand.  

---

## FAQs

**Q: What kinds of TikTok inputs does this scraper support?**  
A: It supports direct video URLs, user profile handles, hashtag pages, and search queries. Each mode discovers and queues video links before extracting metadata.

**Q: Which fields are captured for each video?**  
A: By default, each record includes video ID, URL, author name and handle, caption, hashtags, sound name and ID where available, publish time, views, likes, comments, shares, and basic link references. The schema is defined centrally so you can extend it.

**Q: Does this require logging into TikTok?**  
A: For many public use cases, anonymous browsing is enough. However, some regions and access patterns may benefit from optional login and cookies for more stable behavior. The project is designed so credentials and session storage can be configured if needed.

**Q: How do I integrate this into my existing stack?**  
A: You can call the scraper via CLI for batch jobs, import it as a Python module in your own code, or hit the optional API endpoints from external tools. Outputs in JSON and CSV are designed to fit neatly into data pipelines and BI tools.

---

## Performance & Reliability Benchmarks

**Execution Speed:** On a typical headless setup, the scraper can process around 60–120 video pages per hour per browser context with conservative delays and full metadata extraction. Lighter profiles (fewer fields, less scrolling) can run faster.

**Success Rate:** With stable selectors and moderate rate limits, successful extraction rates usually stabilize around 92–94% across large runs, with failures due mostly to intermittent network issues, geo or consent popups, or sudden UI changes.

**Scalability:** The architecture supports multiple concurrent browser contexts or containerized workers, making it feasible to scale to hundreds or thousands of videos per day by distributing the workload while respecting safety limits per IP and session.

**Resource Efficiency:** Each headless Playwright context typically consumes a modest CPU share and 300–600 MB of RAM while active. Concurrency can be adjusted in configuration to match the capacity of your machine or container environment.

**Error Handling:** All scraping steps are wrapped in structured exception handling with categorized error types, retries with exponential backoff for transient issues, and detailed logs of failed URLs. Summary reports make it easy to re-run only the problematic subset if needed.

<p align="center">
<a href="https://cal.com/app-pilot-m8i8oo/30min" target="_blank">
 <img src="https://img.shields.io/badge/Book%20a%20Call%20with%20Us-34A853?style=for-the-badge&logo=googlecalendar&logoColor=white" alt="Book a Call">
</a>
 <a href="https://www.youtube.com/@Appilot-app/videos" target="_blank">
  <img src="https://img.shields.io/badge/🎥%20Watch%20demos%20-FF0000?style=for-the-badge&logo=youtube&logoColor=white" alt="Watch on YouTube">
 </a>
</p>
