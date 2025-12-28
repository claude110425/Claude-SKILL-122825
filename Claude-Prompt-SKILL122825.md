You will be generating a comprehensive SKILL.md document that contains multiple distinct skills (minimum 5, but generate more if the input warrants it) based on user-provided information. The user will provide either a description of desired functionality or actual code that you need to analyze.

Here is the input you need to analyze:

<input>
{{INPUT}}
</input>

Your task is to carefully analyze this input and generate a SKILL.md document with multiple well-defined skills. Each skill should be a distinct, focused capability that could be triggered independently.

Here is the format you must follow for each skill. Study this sample SKILL.md carefully:

<sample_format>
Skill 1: PDF to Markdown Transformer & Summarizer
pdf-markdown-analyzer

Description
Advanced PDF document processing that converts any PDF file into clean, structured markdown format with comprehensive summarization capabilities.

Capabilities
PDF Text Extraction: Full text extraction from multi-page PDF documents with layout preservation
Markdown Conversion: Intelligent conversion maintaining headers, lists, tables, and formatting
Image Handling: Extract and reference embedded images
Table Recognition: Convert PDF tables into markdown table format
Comprehensive Summary: Generate detailed 4000-5000 word analytical summaries
Structure Analysis: Identify and preserve document hierarchy
Metadata Extraction: Capture author, title, creation date, and document properties

Summary Features
Executive summary (200-300 words)
Detailed section-by-section analysis
Key findings and insights
Statistical data presentation
References and citations
Conclusion and recommendations

Output Format
# [Document Title]

## Metadata
- **Author**: [Name]
- **Date**: [Date]
- **Pages**: [Number]

## Executive Summary
[200-300 words overview]

## Comprehensive Analysis
[4000-5000 words detailed summary]

## Key Insights
- [Insight 1]
- [Insight 2]

## Conclusion
[Final analysis]

MANDATORY TRIGGERS
PDF, .pdf, pdf file, convert pdf, pdf to markdown, extract pdf, pdf analysis, document conversion, pdf summary

Supported Formats
PDF 1.0 - 2.0
Scanned PDFs (with OCR)
Multi-column layouts
Academic papers
Reports and whitepapers

---

Skill 2: Multi-Format Document Organizer & Keyword Highlighter
doc-organizer-coral

Description
Transform text, DOCX, and markdown files into beautifully organized markdown with coral-colored keyword highlighting and comprehensive summarization.

Capabilities
Format Support: TXT, DOCX, MD, RTF
Intelligent Organization: Auto-detect structure and reorganize content
Keyword Extraction: AI-powered keyword identification
Coral Color Highlighting: Apply <span style="color: coral;">keyword</span> to important terms
Semantic Analysis: Group related content intelligently
Hierarchical Structuring: Create logical header hierarchy
Cross-referencing: Link related sections
Summary Generation: 4000-5000 word comprehensive summary

Keyword Highlighting Criteria
Technical terms (15-20%)
Key concepts (20-25%)
Important names and entities (10-15%)
Action items and conclusions (10-15%)
Statistical data (5-10%)

Output Format
# <span style="color: coral;">Main Title</span>

## Table of Contents
[Auto-generated with coral keywords]

## Organized Content
Content with <span style="color: coral;">highlighted keywords</span>

## Comprehensive Summary (4000-5000 words)
[Detailed analysis with coral-highlighted key terms]

## Keyword Index
- <span style="color: coral;">Keyword 1</span>: Context
- <span style="color: coral;">Keyword 2</span>: Context

MANDATORY TRIGGERS
text file, docx, word document, .md, markdown file, organize, structure, keywords, highlight, coral, document analysis, text processing

Processing Pipeline
File parsing and format detection
Content extraction and cleaning
Structural analysis
Keyword identification (AI-powered)
Coral color application
Summary generation
Index creation
</sample_format>

Requirements for generating skills:

1. **Minimum 5 Skills**: Generate at least 5 distinct skills, but create more (6-10+) if the input contains rich functionality
2. **Unique Identifiers**: Each skill needs a unique kebab-case identifier (e.g., pdf-markdown-analyzer)
3. **Comprehensive Capabilities**: List 5-10+ specific capabilities per skill
4. **Output Format Section**: Include concrete examples of output structure, preferably with code/markdown examples
5. **MANDATORY TRIGGERS**: This section is critical - include 8-15 trigger words/phrases that would activate this skill
6. **Additional Sections**: Add relevant sections like "Supported Formats", "Processing Pipeline", "Features", "Security Features", etc.
7. **Code Examples**: Where relevant, include code snippets showing implementation details
8. **Detailed Descriptions**: Each capability should be explained, not just listed

Before generating the skills document, use the scratchpad to analyze the input:

<scratchpad>
- Identify the main functionalities or features in the input
- Group related capabilities into distinct skills
- Determine appropriate trigger words for each skill
- Plan the structure and unique aspects of each skill
- Ensure skills are complementary but non-overlapping
- Consider edge cases and advanced features
</scratchpad>

Now generate the complete SKILL.md document with all skills. Ensure each skill follows the format shown in the sample, with clear sections, detailed capabilities, output formats with examples, and comprehensive mandatory triggers.

Write your complete SKILL.md document inside <skills_document> tags.
