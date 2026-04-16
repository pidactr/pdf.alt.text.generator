# PDF Alt Text Generator

A browser-based accessibility tool that adds alt text to images in PDF documents.

## How It Works

1. Upload a PDF file
2. The tool automatically converts it to Word format behind the scenes
3. Claude AI generates alt text descriptions for each image and graphic
4. Review and edit each description, approve the ones you want
5. Download your accessible PDF — conversion back happens automatically

## Live Tool

https://pidactr.github.io/pdf.alt.text.generator

## Tech Stack

| Service | Role |
|---|---|
| GitHub Pages | Hosts the tool publicly |
| Cloudflare Worker | API proxy — holds encrypted credentials, handles Adobe conversions |
| Anthropic API | Claude AI analyzes images and generates alt text descriptions |
| Adobe PDF Services API | Converts PDF to Word and back |

## Security

- Password gate built into the tool
- All API keys stored as encrypted Cloudflare secrets — never in source code
- Cloudflare Worker locked to pidactr.github.io origin only

## Admin Notes

- To change the password: edit `index.html`, find `TOOL_PASSWORD`, update the value, commit
- To rotate the Anthropic API key: Cloudflare Worker → Settings → Variables and Secrets
- To rotate Adobe credentials: same location — update `ADOBE_CLIENT_ID` and `ADOBE_CLIENT_SECRET`
- Cost: ~$0.005 per image (Anthropic) + 2 Adobe transactions per document (500 free/month)
