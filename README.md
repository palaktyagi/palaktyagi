# FactSage  
AI-powered fact-checking platform that analyzes claims using OCR, Gemini AI, and real-time Google Search grounding. FactSage enables fast, transparent verification with structured evidence, confidence scoring, and visual explanations.

---

## Overview

FactSage is designed to help users quickly determine whether a statement is true, false, mixed, or uncertain. It processes text or images, extracts meaningful claims, retrieves fresh web sources, and uses Gemini AI to analyze evidence and produce an interpretable verdict.  
The platform emphasizes transparency by showing supporting and contradicting sources, confidence scores, and an interactive graph illustrating how each piece of evidence contributes to the final decision.

---

## Features

### AI-Powered Verification  
- Automated claim detection and cleanup  
- Gemini 1.5 Flash model with search grounding  
- Structured, confidence-weighted verdicts  
- Detailed reasoning summaries  

### Evidence Collection  
- Fetches 5–10 reputable sources in real time  
- Categorizes sources as supporting or refuting  
- Extracts headlines, links, and contextual snippets  
- Ranks evidence by confidence and relevance  

### Knowledge Graph Visualization  
- Visual representation of claim → evidence → verdict  
- Node–edge based flow for easy interpretation  
- Helpful for understanding multi-step reasoning  

### OCR Processing  
- Extracts text from images, screenshots, or documents  
- Normalizes, cleans, and parses extracted text into claims  

### Modern Developer Stack  
- Fully typed with TypeScript  
- Clean architecture using Next.js App Router  
- Modular verification pipeline  
- Reusable UI components with shadcn/ui  

---

## Quick Start

### Prerequisites
- Node.js 18+  
- npm or yarn  
- Gemini API Key from Google AI Studio  

### Installation

```bash
git clone https://github.com/kashishdesai01/CMPE-280-FactSage.git
cd CMPE-280-FactSage
npm install
```

### Environment Configuration

```bash
cp .env.example .env.local
```

Edit `.env.local`:

```
GEMINI_API_KEY=your_api_key_here
NEXT_PUBLIC_API_BASE=http://localhost:3000
```

### Running the Development Server

```bash
npm run dev
```

Access the app at:

```
http://localhost:3000
```

---

## Claim Verification

FactSage exposes a simple API that processes text and returns a structured evaluation with evidence, reasoning, and graph data.

### Example Request

```json
{
  "text": "Intel reported a $4.1B profit in Q3 2024."
}
```

### Example Response

```json
{
  "authenticity_score": 0.92,
  "verdict": "true",
  "category": "tech",
  "evidence": [
    {
      "url": "https://cnbc.com/2024/intel-earnings",
      "title": "Intel Reports Strong Q3 Results",
      "snippet": "Intel announced a Q3 profit of $4.1 billion...",
      "stance": "supporting",
      "confidence": 0.88
    }
  ],
  "explanation": "Multiple reputable sources confirm the claim.",
      "graph": {
        "nodes": [...],
        "edges": [...]
      }
}
```

---

## Screenshots

_Add screenshots here (homepage, OCR upload, verification results, graph view)._  
If you provide them, they can be formatted into this section.

---

## Tech Stack

| Technology | Purpose |
|-----------|----------|
| Next.js 14 | Framework & App Router |
| TypeScript | Type safety |
| Gemini 1.5 Flash | AI verification |
| Google Search API | Evidence gathering |
| Tesseract.js | OCR extraction |
| Tailwind CSS | Styling |
| shadcn/ui | Component library |
| React Flow | Graph visualization |

---

## Project Structure

```
CMPE-280-FactSage/
├── app/
│   ├── api/
│   │   └── verify-claim/
│   │       └── route.ts           # Claim verification API endpoint
│   ├── page.tsx                   # Main application page
│   └── layout.tsx                 # Root layout
│
├── components/
│   ├── input-panel.tsx
│   ├── verification-panel.tsx
│   ├── evidence-panel.tsx
│   ├── results-history-panel.tsx
│   └── knowledge-graph.tsx
│
├── lib/
│   ├── claim-extractor.ts         # OCR + claim parsing logic
│   ├── gemini-verifier.ts         # AI verification pipeline
│   ├── types.ts                   # Shared TypeScript types
│   └── utils.ts
│
├── public/
├── .env.local
├── package.json
└── README.md
```

---

## API Endpoints

### POST `/api/verify-claim`

Runs the full fact-checking pipeline including extraction, search, evidence scoring, and verdict generation.

#### Request Body

```json
{
  "text": "Your claim here"
}
```

#### Response Includes
- `authenticity_score` — numerical confidence value  
- `verdict` — true, false, mixed, uncertain  
- `category` — topic classification  
- `evidence[]` — list of supporting/refuting sources  
- `graph` — knowledge graph nodes and edges  
- `explanation` — summary of Gemini’s reasoning  

---

## API Limits

### Gemini Free Tier
- Approximately 15 requests per minute  
- Around 1,500 requests per day  
- Works well for development and testing  

### Paid Tier
- Approximately $1 per 1,000 verifications  
- Suitable for production workloads  
