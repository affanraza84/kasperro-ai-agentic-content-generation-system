# Agentic Content Generation System

Next.js + TypeScript app that orchestrates modular agents to transform a constrained product dataset into machine-readable JSON pages (FAQ, product, comparison). Tailwind is used for a lightweight UI that visualizes the pipeline outputs.

## Architecture
- **Parser Agent** (`lib/agents/parserAgent.ts`): normalizes the raw product input into an internal `Product` contract.
- **Question Agent** (`lib/agents/questionAgent.ts`): generates 15 categorized user questions from the product model.
- **Comparison Agent** (`lib/agents/comparisonAgent.ts`): injects a fictional Product B for contrast.
- **Content Logic Blocks** (`lib/agents/contentBlocks.ts`): reusable pure functions (hero creation, highlights, value messaging, comparison diffing, FAQ slicing).
- **Templates** (`lib/templates/*.ts`): structured page definitions (FAQ, product description, comparison) that consume logic blocks.
- **Page Builder Agent** (`lib/agents/pageBuilderAgent.ts`): assembles pages from templates and upstream agents.
- **Pipeline Orchestrator** (`lib/pipeline.ts`): deterministic flow wiring all agents together.

## Running
```
npm install
npm run dev
```

## Generating JSON artifacts
```
npm run generate
```
Outputs are written to `output/faq.json`, `output/product_page.json`, `output/comparison_page.json`, and `output/questions.json`.

