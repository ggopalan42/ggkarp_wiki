# LLM Wiki Project Plan — v1

## Overview

This project implements Karpathy's LLM Wiki idea, built by GG and tuned to personal use cases.

- LinkedIn/X Post: https://x.com/karpathy/status/2039805659525644595
- LLM Wiki Idea: https://gist.github.com/karpathy/442a6bf555914893e9891c11519de94f

## Core Concept

Use an LLM to curate, link, and summarize various pieces of knowledge (articles, papers, books, images, etc.) using simple directory structures and markdown files. No fancy databases, RAGs, or graph structures.

Raw data (links, PDFs, images, etc.) is ingested and then indexed and linked by an LLM.

## Top-Level Domains

Data is organized into five top-level domains. There is **no cross-linking** between domains — they are completely separate and cross-linking would cause confusion. All markdowns, raw data, indexes, logs, etc. are separated accordingly.

| Domain | Description |
|---|---|
| `Personal` | Personal information: financial, taxes, books read, useful information, etc. |
| `Companies_worked_for` | Companies GG has worked for in the past |
| `Companies_interesting` | Interesting companies |
| `GenAI` | All things LLM and related technologies, including World Models |
| `Technical_general` | All general technical information |

## Status

This is the top-level plan. It will be refined in subsequent iterations using LLMs.
