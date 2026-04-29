# Invoice Splitter - Render Hosted Version

This version is set up for internet hosting on Render as a single web service.

## What is included

- React/Vite frontend
- Node/Express backend
- PDF text extraction using `pdf-parse`
- Same-origin API route: `/api/extract`
- Render blueprint: `render.yaml`

## Recommended hosting: Render

Render supports Node web services and can run this app as one service. The Node server serves both:
- the built React app
- the PDF extraction API

Render’s docs describe deploying Node web services and static React apps, but for this app one combined Node service is easiest because PDF extraction needs a backend.

## Deploy steps

1. Create a GitHub account if you do not already have one.
2. Create a new private GitHub repository, e.g. `invoice-splitter`.
3. Upload all files from this folder into that repository.
4. Go to Render.
5. Choose **New +** then **Blueprint** or **Web Service**.
6. Connect the GitHub repository.
7. Use these settings if asked:

```text
Environment: Node
Build command: npm run build
Start command: npm start
```

8. Deploy.
9. Render will give you a live URL.

## Local test

```bash
npm run build
npm start
```

Then open:

```text
http://localhost:3001
```

## Important limitation

This extracts text from text-based PDFs. If a PDF is scanned/image-based, you will need OCR.

The recommended future upgrade is:
- Azure Document Intelligence
- Google Document AI
- AWS Textract
