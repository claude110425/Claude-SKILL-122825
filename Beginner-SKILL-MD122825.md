COMPREHENSIVE BEGINNER'S GUIDE TO USING SKILLS
How to Activate and Use Skills in Claude Console and Other Platforms

Table of Contents

Understanding Skills and Triggers
Platform-Specific Setup Instructions
Five Detailed Examples with Step-by-Step Instructions
Troubleshooting Guide
Best Practices and Tips


Understanding Skills and Triggers
What Are Skills?
Skills are specialized capabilities that Claude can perform. Each skill in the SKILL.md document has:

A unique identifier (e.g., fda-device-research-reporter)
A description of what it does
Capabilities (specific functions)
MANDATORY TRIGGERS (keywords that activate the skill)

How Do Triggers Work?
When you include trigger words in your message, Claude automatically recognizes which skill you want to use. For example:

Typing "FDA 510(k)" triggers the FDA Medical Device Intelligence skill
Typing "convert pdf to markdown" triggers the PDF Conversion skill
Typing "compare two versions" triggers the Document Comparison skill

Important: You Don't Need to Mention the Skill Name
❌ Don't say: "Use the fda-device-research-reporter skill to..."
✅ Do say: "Search FDA database for [device name] K123456"
The trigger words automatically activate the right skill!

Platform-Specific Setup Instructions
Option 1: Claude.ai Web Console (Recommended for Beginners)
Step 1: Access Claude

Go to https://claude.ai
Sign in with your account
Start a new conversation (click "+" or "New Chat")

Step 2: Provide Context (Optional but Recommended)
Copy and paste this at the start of your conversation:
CopyI'll be asking you to perform specialized tasks including:
- FDA medical device research and reporting
- PDF to markdown conversion
- Document analysis and entity extraction
- Version comparison between documents

Please use the appropriate specialized skills based on my requests.
Step 3: Upload Files (if needed)

Click the 📎 (paperclip) icon
Select your PDF or document files
Wait for upload confirmation
Proceed with your request

Step 4: Make Your Request
Use the trigger words from the skill you want to activate (see examples below)

Option 2: Claude for Sheets/Docs
Google Sheets Setup

Install Claude for Sheets extension
Open a new or existing spreadsheet
Use the Claude formula: =CLAUDE("your prompt with triggers")

Example:
Copy=CLAUDE("Search FDA 510(k) for device K123456 and create a report with 5 tables")
Google Docs Setup

Install Claude for Docs add-on
Open your document
Go to Extensions → Claude → Start
Type your request with triggers in the sidebar


Option 3: API Integration (Advanced)
pythonCopyimport anthropic

client = anthropic.Anthropic(api_key="your-api-key")

message = client.messages.create(
    model="claude-3-5-sonnet-20241022",
    max_tokens=4096,
    messages=[{
        "role": "user",
        "content": "Search FDA database for [device] K123456 and create comprehensive report"
    }]
)

print(message.content)

Five Detailed Examples with Step-by-Step Instructions

EXAMPLE 1: FDA Medical Device Research Report
Scenario
You need to research an FDA-cleared medical device and create a comprehensive report with tables.
Skill Activated
FDA Medical Device Intelligence & Report Generator (fda-device-research-reporter)
Step-by-Step Instructions
Step 1: Prepare Your Information
Gather one or more of the following:

Device name: "Acme Cardiac Monitor"
510(k) number: "K193456" (if you have it)
Manufacturer name: "Acme Medical Corp"

Step 2: Open Claude Console

Go to https://claude.ai
Click "New Chat"
Give your chat a name: "FDA Device Research - Cardiac Monitor"

Step 3: Craft Your Prompt
Copy this template and fill in your details:
CopyI need an FDA medical device intelligence report for the following device:

Device Name: Acme Cardiac Monitor
510(k) Number: K193456
Manufacturer: Acme Medical Corporation

Please search the FDA database and create a comprehensive markdown report with:
- 3,000-4,000 words
- At least 5 detailed tables
- Device classification and regulatory pathway
- Predicate device analysis
- Post-market surveillance data
- Competitive analysis
Step 4: Review Key Triggers Used
✅ "FDA" - Primary trigger
✅ "510(k)" - Specific database trigger
✅ "medical device" - Domain trigger
✅ "comprehensive report" - Output format trigger
✅ "tables" - Table generation trigger
Step 5: Submit and Wait

Paste your prompt
Press Enter or click Send
Wait 30-60 seconds for research and generation
Claude will search FDA databases and compile information

Step 6: Review the Output
You should receive a document with this structure:
markdownCopy# FDA Medical Device Intelligence Report
## Acme Cardiac Monitor - 510(k) K193456

## Executive Summary
[300-400 words]

## 1. Device Identification and Classification
**Table 1: Device Identification**
[Complete table]

## 2. Regulatory Pathway Analysis
**Table 2: Timeline**
[Complete table]

[... continues with 5+ tables total]
Step 7: Request Modifications (if needed)
If you need changes:
CopyThank you! Can you please:
1. Add more detail to the post-market surveillance section
2. Include additional predicate devices in Table 3
3. Add a table comparing technical specifications
Step 8: Export Your Report

Click the three dots (•••) next to the response
Select "Copy" to copy the markdown
Paste into your preferred markdown editor (Typora, Obsidian, VS Code)
Or paste into Google Docs/Word (formatting will be preserved)


EXAMPLE 2: Convert Specific PDF Pages to Markdown
Scenario
You have a 50-page technical manual, but you only need pages 1-10 and pages 25-30 converted to markdown.
Skill Activated
Selective PDF to Markdown Converter (pdf-page-selector-converter)
Step-by-Step Instructions
Step 1: Prepare Your PDF

Locate your PDF file on your computer
Note which pages you want converted
Have the file ready to upload

Step 2: Open Claude and Upload File

Go to https://claude.ai
Start new chat: "PDF Conversion - Technical Manual"
Click the 📎 paperclip icon
Select your PDF file
Wait for "Upload complete" confirmation

Step 3: Specify Pages to Convert
Option A: Specific Page Ranges
CopyPlease convert the following pages from the uploaded PDF to markdown:
- Pages 1-10 (Introduction and Overview)
- Pages 25-30 (Technical Specifications)

Maintain all formatting, tables, and structure.
Option B: Default First 10 Pages
CopyPlease convert this PDF to markdown. Use the default first 10 pages.
Option C: Multiple Specific Pages
CopyPlease convert these specific pages to markdown: 1, 5, 10, 15, 20, 25
Step 4: Review Triggers Used
✅ "convert" - Action trigger
✅ "PDF to markdown" - Primary skill trigger
✅ "pages" - Page selection trigger
✅ "formatting" - Quality requirement trigger
Step 5: Claude Processes Your Request
Claude will:

Analyze the PDF structure
Extract text from specified pages
Identify headers, lists, tables
Convert to clean markdown
Add page break markers

Step 6: Review the Output
You'll receive:
markdownCopy# Converted Document: Technical_Manual.pdf

## Conversion Metadata
- **Source PDF**: Technical_Manual.pdf
- **Total Pages in PDF**: 50
- **Pages Converted**: 1-10, 25-30
- **Conversion Date**: 2024-01-15 14:30:00

---

## Page 1

# Technical Manual
## Model XR-2000

Introduction text with **bold** and *italic* formatting preserved...

---

## Page 2

### Section 1.1: Overview

Content continues...

| Feature | Specification |
|---------|--------------|
| Weight  | 2.5 kg       |
| Power   | 120V AC      |

---

[Continues for all requested pages]

## Conversion Notes
- Tables: 8 tables detected and converted
- Images: 3 images extracted
- Formatting confidence: High
Step 7: Handle Images (if present)
If Claude mentions extracted images:
CopyI see there are 3 images in the conversion. Can you:
1. List all image locations (which pages)
2. Describe what each image shows
3. Suggest descriptive alt-text for each
Step 8: Request Different Pages
If you need additional pages:
CopyThank you! Now please also convert pages 35-40 from the same PDF.
Step 9: Save Your Markdown

Copy the entire markdown output
Save to a .md file
Open in markdown editor
Images will need to be manually re-inserted if needed


EXAMPLE 3: Comprehensive Document Summary with 20 Entities
Scenario
You have a research paper or regulatory document that you need thoroughly analyzed with key entities extracted.
Skill Activated
Deep Document Analyzer & Entity Extractor (document-entity-intelligence)
Step-by-Step Instructions
Step 1: Prepare Your Document
Supported formats:

PDF (most common)
DOCX (Word documents)
TXT (plain text)
MD (markdown files)

Step 2: Upload Document

Open Claude.ai
New chat: "Document Analysis - Research Paper"
Upload your file using 📎 icon
Confirm upload successful

Step 3: Request Comprehensive Analysis
Template Prompt:
CopyPlease analyze this document and provide:

1. A comprehensive summary (3,000-4,000 words) covering:
   - Background and context
   - Main arguments and findings
   - Methodology (if applicable)
   - Implications and impact
   - Critical evaluation

2. Extract and analyze the 20 most important entities with:
   - Entity name and category
   - Contextual quotes (50-100 words each)
   - Page/section references
   - Frequency of mention
   - Significance assessment
   - Detailed commentary (100-150 words each)

Present entities in a comprehensive table format.
Step 4: Review Triggers Used
✅ "comprehensive summary" - Long-form analysis trigger
✅ "3,000-4,000 words" - Word count trigger
✅ "extract entities" - Entity extraction trigger
✅ "20 most important entities" - Quantity specification
✅ "contextual" - Context requirement trigger
✅ "table format" - Output format trigger
Step 5: Wait for Processing

Small documents (< 10 pages): 30-45 seconds
Medium documents (10-50 pages): 1-2 minutes
Large documents (50+ pages): 2-4 minutes

Step 6: Review Summary Structure
You'll receive a document like this:
markdownCopy# Comprehensive Document Analysis: [Document Title]

## Document Overview
**Source**: research_paper.pdf
**Type**: Academic Research Paper
**Length**: 35 pages, ~12,000 words
**Analysis Date**: 2024-01-15

---

## Executive Summary (400-500 words)
[High-level overview of the entire document]

---

## Section 1: Background and Context (500-600 words)
[Detailed context analysis]

### Historical Context
[Background information]

### Document Purpose
[Why document was created]

---

## Section 2: Main Content Analysis (800-1000 words)

### Theme 1: [Primary Theme]
[250-300 words analysis]

### Theme 2: [Secondary Theme]
[250-300 words analysis]

---

[Continues through all sections]

**Total Word Count**: 3,547 words
Step 7: Review Entity Table
The entity table will look like this:
markdownCopy## Extracted Entities: Comprehensive Analysis

| # | Entity Name | Category | Context (Quote/Reference) | Page/Section | Frequency | Significance | Commentary |
|---|-------------|----------|---------------------------|--------------|-----------|--------------|------------|
| 1 | CRISPR-Cas9 | Technology | "The CRISPR-Cas9 gene editing system represents a breakthrough in molecular biology, enabling precise modifications to DNA sequences with unprecedented accuracy and efficiency..." | p. 5, 12, 18, 23 | 45 occurrences | Critical | CRISPR-Cas9 is the central technology discussed in this paper. The authors present novel modifications to the standard protocol that improve editing efficiency by 35%. This represents the core innovation of the research. The entity connects to entities #3 (Dr. Smith - principal investigator), #7 (target genes), and #15 (off-target effects). Understanding this technology is essential to grasping the paper's contribution to the field. |
| 2 | Dr. Jennifer Smith | Person | "Dr. Smith's laboratory at Stanford University has pioneered several advances in gene editing technology..." | p. 2, 15, 28 | 12 occurrences | High | Principal investigator and corresponding author. Her previous work (entity #18) established the foundation for this research. Key opinion leader in gene editing field with 15+ years experience. |

[... continues for all 20 entities]
Step 8: Request Clarifications
If you need more detail:
CopyThank you for the analysis! Can you please:
1. Expand the commentary for entity #5 - I need more detail on its significance
2. Add entity relationships - which entities are most closely connected?
3. Provide a visual relationship map showing how the top 10 entities connect
Step 9: Ask Follow-Up Questions
CopyBased on your entity analysis, what are the 3 most critical concepts I should understand from this document?
Step 10: Export and Use

Copy markdown output
Save as document_analysis.md
Use entity table as quick reference guide
Share with colleagues or include in your own reports


EXAMPLE 4: Compare Two Document Versions and Find 100 Differences
Scenario
You have two versions of a regulatory submission document and need to identify all changes between them.
Skill Activated
Document Version Comparator & Difference Analyzer (doc-diff-version-comparator)
Step-by-Step Instructions
Step 1: Prepare Both Documents

Version 1 (older): Device_Submission_v1.pdf
Version 2 (newer): Device_Submission_v2.pdf

Label files clearly so you know which is which!
Step 2: Upload Both Files

Open Claude.ai
New chat: "Document Comparison - Submission v1 vs v2"
Click 📎 to upload first document
Wait for confirmation
Click 📎 again to upload second document
Confirm both files are uploaded

Step 3: Craft Your Comparison Request
CopyI have uploaded two versions of the same regulatory document:
- Version 1 (older): Device_Submission_v1.pdf
- Version 2 (newer): Device_Submission_v2.pdf

Please compare these two versions and identify the 100 most significant differences.

For each difference, provide:
1. Change number and descriptive title
2. Difference type (content addition/deletion/modification, structural change, data change, etc.)
3. Version 1 content (what it said before)
4. Version 2 content (what it says now)
5. Page reference in Version 1
6. Page reference in Version 2
7. Impact assessment (Critical/Major/Minor)
8. Detailed commentary (100-200 words explaining why this change matters)

Present all differences in a comprehensive table, then provide:
- Statistical summary of changes
- Analysis by document section
- Top 10 critical changes
- Overall change pattern analysis
Step 4: Review Triggers Used
✅ "compare" - Primary comparison trigger
✅ "two versions" - Version comparison trigger
✅ "differences" - Difference detection trigger
✅ "100 most significant" - Quantity specification
✅ "table" - Output format trigger
✅ "document comparison" - Skill activation trigger
Step 5: Processing Time
Document comparison takes longer:

Small documents (< 20 pages each): 1-2 minutes
Medium documents (20-50 pages each): 2-4 minutes
Large documents (50+ pages each): 4-8 minutes

Claude will show "Claude is thinking..." during processing.
Step 6: Review the Output Structure
markdownCopy# Document Version Comparison Analysis

## Comparison Overview
- **Document Title**: Medical Device Regulatory Submission
- **Version 1**: Device_Submission_v1.pdf (uploaded 2023-06-15)
- **Version 2**: Device_Submission_v2.pdf (uploaded 2024-01-10)
- **Analysis Date**: 2024-01-15
- **Total Differences Detected**: 247
- **Significant Differences Reported**: 100

---

## Statistical Summary

### Change Breakdown by Category
| Category | Count | Percentage |
|----------|-------|------------|
| Content Changes | 42 | 42% |
| Data/Table Changes | 28 | 28% |
| Structural Changes | 15 | 15% |
| Technical Specifications | 10 | 10% |
| Regulatory Updates | 5 | 5% |
| **Total** | **100** | **100%** |

### Change Impact Assessment
- **Critical Changes**: 15 (High impact on regulatory approval)
- **Major Changes**: 45 (Significant modifications)
- **Minor Changes**: 40 (Small updates)

---

## Comprehensive Difference Table (100 Differences)

| # | Change Title | Type | V1 Content | V2 Content | V1 Page | V2 Page | Impact | Comments |
|---|--------------|------|------------|------------|---------|---------|--------|----------|
| 1 | Device Classification Upgraded | Regulatory | "The device is classified as Class II under 21 CFR 870.2300" | "The device is classified as Class III under 21 CFR 870.2400 requiring PMA approval" | p. 3 | p. 3 | Critical | This is the most significant change in the document. The upgrade from Class II to Class III dramatically alters the regulatory pathway. Instead of 510(k) clearance, the device now requires Premarket Approval (PMA), which demands: extensive clinical trials, manufacturing inspections, and significantly longer review times (typically 180+ days vs 90 days). This impacts development timeline by 12-18 months and increases costs by $1-3M. Companies must reassess clinical trial protocols, manufacturing controls, and market strategy. |
| 2 | Clinical Trial Sample Size Increased | Data Modification | "Enrollment target: n=50 subjects" | "Enrollment target: n=150 subjects with 12-month follow-up" | p. 15 | p. 16 | Critical | Tripling the sample size and adding extended follow-up significantly strengthens the clinical evidence base but adds substantial cost and time. This change likely responds to FDA feedback requesting more robust safety data. Impact: 9-12 additional months in clinical phase, ~$500K-$1M additional trial costs. |
| 3 | Intended Use Statement Modified | Content Modification | "Intended for diagnostic monitoring in hospital settings" | "Intended for diagnostic and therapeutic monitoring in hospital and ambulatory settings" | p. 5 | p. 5 | Major | Expanded scope from diagnostic-only to diagnostic plus therapeutic, and added ambulatory use. This broadens market opportunity but requires additional validation data for home/ambulatory use scenarios. May trigger different regulatory standards for home healthcare devices. |

[... continues for all 100 differences]
Step 7: Navigate to Critical Changes
Scroll to the "Critical Changes Summary" section:
markdownCopy## Critical Changes Summary (Top 10)

1. **Difference #1**: Device Classification Upgraded - Class II to Class III
   - *Why Critical*: Changes entire regulatory strategy from 510(k) to PMA

2. **Difference #2**: Clinical Trial Sample Size Tripled
   - *Why Critical*: Major impact on timeline and budget

3. **Difference #8**: Sterilization Method Changed
   - *Why Critical*: Requires new validation studies and biocompatibility testing

[... continues for top 10]
Step 8: Review Section-by-Section Analysis
markdownCopy## Detailed Change Analysis by Section

### Section 1: Device Description (Page 1-10)
**Changes Detected**: 12
**Impact**: Major

The device description section underwent significant revision, primarily to accommodate the expanded indications for use and the classification upgrade. Notable changes include:

1. Addition of new technical specifications (Differences #5, #7, #9)
2. Enhanced safety feature descriptions (Difference #12)
3. Updated materials list to reflect biocompatibility requirements (Difference #15)

**Key Changes**:
- Difference #1: Classification upgrade
- Difference #5: Power supply specifications updated
- Difference #7: Added wireless communication capabilities
Step 9: Request Focused Analysis
If you need deeper analysis on specific changes:
CopyCan you provide more detail on:
1. All changes related to clinical trial design (differences #2, #23, #45)
2. The regulatory implications of changes #1, #8, and #12
3. A timeline impact assessment based on all Critical changes
Step 10: Export and Share
CopyCan you export the comparison in these formats:
1. Summary PDF (executive overview only)
2. Full markdown with all 100 differences
3. CSV file of the difference table for import into Excel
Step 11: Track Changes for Document Management
Use the output to:

Create a formal change log document
Brief stakeholders on key modifications
Update project timelines based on critical changes
Identify areas needing additional documentation


EXAMPLE 5: Combined Workflow - FDA Research → PDF Analysis → Version Comparison
Scenario
You're preparing a regulatory submission and need to:

Research a predicate device from FDA database
Convert your technical specification PDF to markdown
Compare your submission draft v1 vs v2
Create a comprehensive analysis with entities

This demonstrates using multiple skills in sequence.
Skills Activated (in order)

FDA Medical Device Intelligence (fda-device-research-reporter)
Selective PDF to Markdown Converter (pdf-page-selector-converter)
Document Version Comparator (doc-diff-version-comparator)
Deep Document Analyzer (document-entity-intelligence)

Step-by-Step Instructions
PHASE 1: FDA Predicate Device Research
Step 1.1: Start Research Task
Open Claude and start with:
CopyI'm preparing a 510(k) submission for a new cardiac monitor. I need to research the predicate device:

Device Name: CardioSense Pro
510(k) Number: K183456
Manufacturer: MedTech Solutions Inc

Please create a comprehensive FDA intelligence report with:
- 3,000-4,000 words
- At least 5 tables including device classification, regulatory timeline, predicate comparison, technical specs, and post-market data
- Analysis of substantial equivalence claims
- Competitive landscape
Step 1.2: Review FDA Report
Wait 30-60 seconds for the comprehensive report with 5+ tables.
Step 1.3: Save FDA Research
CopyThank you! Please save this as a markdown file I can reference. 
Also, can you extract just the technical specifications table so I can use it for my comparison?
Copy and save the response to: Predicate_Research_K183456.md

PHASE 2: Convert Your Technical Specifications
Step 2.1: Upload Your Specs PDF
CopyNow I need to convert my technical specification document to markdown.
[Upload: My_Device_Technical_Specs.pdf]

Please convert pages 1-15 (full technical section) to markdown, maintaining all tables and formatting.
Step 2.2: Review Conversion
Claude converts the PDF with this structure:

Device overview
Technical specifications tables
Performance data
Safety features

Step 2.3: Request Comparison Format
CopyCan you format the technical specifications from my device to match the table structure you created for the predicate device? This will make side-by-side comparison easier.
Step 2.4: Save Converted Specs
Save to: My_Device_Specs_Markdown.md

PHASE 3: Compare Submission Versions
Step 3.1: Upload Both Submission Drafts
CopyI have two versions of my 510(k) submission document that need comparison:
[Upload: 510k_Submission_Draft_v1.pdf]
[Upload: 510k_Submission_Draft_v2.pdf]

Please identify the 100 most significant differences between these versions, with full analysis table including:
- Change titles
- Type of change
- Content from both versions
- Page references
- Impact assessment
- Detailed commentary on implications
Step 3.2: Wait for Comprehensive Comparison
Processing time: 2-4 minutes for full document comparison
Step 3.3: Review Critical Changes First
Focus on the "Critical Changes Summary" section to understand the most important modifications.
Step 3.4: Request Regulatory Impact Assessment
CopyBased on the differences you identified, please provide:
1. Which changes might trigger additional FDA questions?
2. Which changes strengthen the substantial equivalence argument?
3. Which changes require updated validation data?
4. Overall assessment: Is v2 stronger or weaker for regulatory approval?
Step 3.5: Save Comparison Report
Save to: Submission_Comparison_v1_v2.md

PHASE 4: Comprehensive Document Analysis
Step 4.1: Analyze Final Version
CopyNow please provide a comprehensive analysis of the Version 2 submission (the newer version):

1. Create a 3,000-4,000 word comprehensive summary covering:
   - Regulatory strategy
   - Device description and specifications
   - Substantial equivalence rationale
   - Clinical evidence summary
   - Risk analysis
   - Quality system overview

2. Extract 20 key entities including:
   - Device features and technologies
   - Predicate devices referenced
   - Regulatory standards cited
   - Key personnel/companies
   - Testing methodologies
   - Clinical endpoints

Present entities in detailed table with context, page references, and commentary.
Step 4.2: Review Comprehensive Analysis
You'll receive:

3,500 word structured summary
20-entity table with detailed commentary
Cross-references between entities
Entity relationship mapping

Step 4.3: Request Strategic Recommendations
CopyBased on your comprehensive analysis and the entity extraction, please provide:
1. Top 5 strengths of this submission
2. Top 3 areas that need strengthening
3. Potential FDA questions and suggested responses
4. Comparison to predicate device - is substantial equivalence clearly demonstrated?
Step 4.4: Save Final Analysis
Save to: Final_Submission_Analysis.md

PHASE 5: Create Master Summary Document
Step 5.1: Request Integrated Summary
CopyPlease create a master executive summary document (1,500-2,000 words) that integrates:
1. Key findings from the predicate device research
2. Critical changes between submission v1 and v2
3. Top 10 entities from the final submission analysis
4. Strategic recommendations for submission success

Format as an executive briefing for management.
Step 5.2: Review Executive Briefing
You'll receive a concise, high-level document suitable for stakeholders.
Step 5.3: Request Presentation Slides Outline
CopyCan you convert this executive summary into a PowerPoint slide outline with:
- Title slide
- Project overview (1 slide)
- Predicate device comparison (1 slide with table)
- Key submission changes v1→v2 (1 slide)
- Critical entities and concepts (1 slide)
- Recommendations (1 slide)
- Next steps (1 slide)

Provide text and table content for each slide.

PHASE 6: Final Organization and Export
Step 6.1: Create Document Package
Organize all outputs:
CopyProject_Folder/
├── 1_Predicate_Research/
│   └── Predicate_Research_K183456.md
├── 2_Technical_Specs/
│   ├── My_Device_Specs_Markdown.md
│   └── Predicate_Comparison_Table.md
├── 3_Version_Comparison/
│   └── Submission_Comparison_v1_v2.md
├── 4_Final_Analysis/
│   ├── Final_Submission_Analysis.md
│   └── Entity_Table.md
└── 5_Executive_Summary/
    ├── Executive_Briefing.md
    └── Presentation_Outline.md
Step 6.2: Request Document Checklist
CopyBased on all the analysis, please create a submission readiness checklist showing:
- ✅ Completed items
- ⚠️ Items needing attention
- ❌ Missing items
- 📅 Timeline for addressing gaps
Step 6.3: Export Everything

Copy each markdown output to separate files
Convert to PDF if needed for distribution
Import tables into Excel for further manipulation
Share with team members


Time Investment for Full Workflow

Phase 1 (FDA Research): 1-2 minutes
Phase 2 (PDF Conversion): 1 minute
Phase 3 (Version Comparison): 3-4 minutes
Phase 4 (Comprehensive Analysis): 2-3 minutes
Phase 5 (Master Summary): 1-2 minutes
Phase 6 (Organization): 5-10 minutes (manual)

Total Active Time: ~10-15 minutes
Total Elapsed Time: ~30-40 minutes (including review)
Benefits of Combined Workflow
✅ Consistent analysis framework across all documents
✅ Comprehensive understanding of regulatory landscape
✅ Clear documentation of changes and rationale
✅ Stakeholder-ready outputs at multiple levels of detail
✅ Traceable decision-making process
✅ Time savings of 15-20 hours vs. manual analysis

Troubleshooting Guide
Common Issues and Solutions
Issue 1: Skill Not Activating
Problem: Claude doesn't seem to be using the specialized skill.
Solution:
CopyI need FDA regulatory intelligence for device K123456. 
Please search the FDA 510(k) database and create a comprehensive report with at least 5 tables in markdown format, 3000-4000 words.
Why it works: Uses multiple trigger words: "FDA," "510(k)," "database," "comprehensive report," "tables," "3000-4000 words"

Issue 2: Word Count Not Matching Target
Problem: Summary is only 1,500 words instead of 3,000-4,000.
Solution:
CopyThe summary is too short. Please expand it to meet the 3,000-4,000 word requirement by:
1. Adding more detail to each section
2. Expanding the analysis with examples
3. Including more context for key points
4. Adding transitional content between sections

Target: 3,500 words minimum.

Issue 3: Missing Tables
Problem: Report has only 2 tables, but you need at least 5.
Solution:
CopyPlease add 3 more tables to this report:
1. Table comparing device specifications
2. Table of post-market surveillance data
3. Table of competitive devices in the market

Each table should have at least 4-5 columns and 5+ rows.

Issue 4: PDF Upload Not Working
Problem: PDF file won't upload or appears corrupted.
Solutions:

Check file size: Maximum 32 MB on Claude.ai

If too large, use PDF compression tool


Check file format: Ensure it's a real PDF, not renamed file
Try OCR: If scanned PDF, pre-process with OCR software
Split large files: Break into smaller sections
Alternative: Copy text directly from PDF and paste as text


Issue 5: Entity Count Wrong
Problem: Only 10 entities extracted instead of 20.
Solution:
CopyPlease extract 10 more entities (total of 20) from the document. Focus on:
- Key concepts and methodologies
- Important dates and events
- Technical terms and standards
- Regulatory references
- Secondary people and organizations

Add these to the existing entity table with the same level of detail.

Issue 6: Version Comparison Incomplete
Problem: Only showing 30 differences instead of 100.
Solution:
CopyPlease continue the comparison to identify 70 more differences (total 100). 
Look for:
- Formatting changes
- Minor wording modifications
- Table data updates
- Reference and citation changes
- Section reorganization
- Header and subheader changes

Add these to the existing comparison table.

Issue 7: Not Sure Which Skill to Use
Problem: You have multiple tasks and don't know which skill applies.
Solution: Describe what you want to achieve, not the skill name:
CopyI need to:
1. Research an FDA-cleared device and get detailed information → Use FDA triggers
2. Convert part of a PDF to text → Use PDF conversion triggers
3. Find all changes between two documents → Use comparison triggers
4. Get a detailed summary with key concepts → Use entity extraction triggers

Just describe the task and the triggers will activate the right skill!

Issue 8: Tables Not Formatting Correctly
Problem: Markdown tables appear broken or misaligned.
Solution:
CopyThe tables are not displaying correctly. Please:
1. Ensure all table rows have the same number of columns
2. Use proper markdown table syntax with | separators
3. Include the header separator row with dashes
4. Test table in a markdown previewer

Regenerate the tables with proper formatting.

Issue 9: Context Too Large Error
Problem: Document too large for single analysis.
Solution:
CopyLet's break this into parts:
1. First, analyze pages 1-20 and extract 10 entities
2. Then analyze pages 21-40 and extract 10 more entities
3. Finally, combine into one comprehensive analysis

Start with pages 1-20.

Issue 10: Need to Combine Multiple Outputs
Problem: You have analysis from 3 different conversations.
Solution: Start a new conversation and say:
CopyI have three separate analyses that need to be combined:

[Paste Analysis 1]

[Paste Analysis 2]

[Paste Analysis 3]

Please synthesize these into one comprehensive document with:
- Integrated executive summary
- Combined entity tables (de-duplicated)
- Cross-references between documents
- Master conclusion

Best Practices and Tips
1. Be Specific with Trigger Words
❌ Vague: "Analyze this document"
✅ Specific: "Create a 3,500-word comprehensive summary with 20 extracted entities in table format"
2. Provide Context Upfront
CopyI'm a regulatory affairs specialist preparing a 510(k) submission for a Class II cardiac monitoring device. I need to research predicate devices and compare technical specifications.

[Then make your specific request]
3. Use Structured Requests
CopyPlease analyze this document and provide:
1. [First requirement with details]
2. [Second requirement with details]
3. [Third requirement with details]

Format: [Specify format]
Length: [Specify length]
4. Iterate and Refine
Don't expect perfection on first try:

Request initial output
Review carefully
Ask for specific improvements
Iterate 2-3 times for best results

5. Save Important Outputs Immediately
Copy markdown to files right away:

Conversations can be lost
Outputs might be regenerated differently
Build a library of reusable content

6. Use Consistent File Naming
CopyProjectName_DocumentType_Version_Date.md

Examples:
- CardiacMonitor_FDA_Research_K183456_20240115.md
- CardiacMonitor_Submission_v1_v2_Comparison_20240115.md
- CardiacMonitor_Technical_Specs_Converted_20240115.md
7. Create Template Prompts
Save your best-performing prompts:
FDA Research Template:
CopySearch FDA database for:
- Device: [NAME]
- 510(k): [NUMBER]
- Manufacturer: [COMPANY]

Create comprehensive report (3,000-4,000 words) with minimum 5 tables covering classification, timeline, predicates, specifications, and post-market data.
8. Leverage Follow-Up Questions
After initial output:
CopyBased on this analysis:
1. What are the top 3 regulatory risks?
2. Which entities are most critical to understand?
3. What additional information should I gather?
9. Request Multiple Formats
CopyPlease provide this information in three formats:
1. Full detailed report (markdown)
2. Executive summary (1 page)
3. Bullet-point checklist (actionable items)
10. Document Your Process
Keep a log of what you requested and received:
Copy# Analysis Log - Cardiac Monitor Project

## 2024-01-15
- Completed FDA predicate research (K183456)
- Converted technical specs pages 1-15
- Generated entity analysis with 20 entities
- Files saved: [list files]

## 2024-01-16
- Compared submission v1 vs v2
- Identified 100 differences
- Created executive summary
- Next: Address critical changes flagged

Quick Reference Card
Essential Trigger Phrases
What You WantSay ThisFDA Device Report"FDA 510(k) K123456 comprehensive report with 5 tables"PDF Conversion"Convert PDF pages 1-10 to markdown"Document Summary"3,500-word comprehensive summary with 20 entities"Version Comparison"Compare two versions and identify 100 differences"Create Tables"Create markdown table with [specifications]"
Word Count Triggers

"3000 words"
"4000 words"
"3,000-4,000 words"
"approximately 3,500 words"

Table Triggers

"at least 5 tables"
"minimum 5 tables"
"create tables for..."
"table format"
"tabular presentation"

Analysis Depth Triggers

"comprehensive"
"detailed"
"in-depth"
"thorough analysis"
"exhaustive review"


Getting Help
If Skills Aren't Working

Check your prompt: Are you using trigger words?
Be more specific: Add details about what you need
Provide examples: Show Claude what output format you want
Start new conversation: Sometimes helps reset context

If Output Quality Is Low

Request improvements: "Please expand section 3 with more detail"
Provide feedback: "The entity commentary needs to be longer"
Ask clarifying questions: "Why did you categorize entity #5 as a concept instead of a technology?"

If You're Unsure What's Possible
CopyI have [describe your documents/task]. 
What analysis capabilities do you have that could help me with:
- Understanding regulatory requirements
- Comparing document versions
- Extracting key information
- Creating summary reports

Conclusion
You now have comprehensive instructions for:
✅ Activating skills using trigger words
✅ 5 detailed real-world examples
✅ Troubleshooting common issues
✅ Best practices for optimal results
Remember: You don't need to memorize skill names or technical details. Just:

Describe what you want
Use relevant trigger words
Be specific about format and length
Iterate to improve results

Start with Example 1 (FDA Research) if you're completely new, then progress to more complex workflows as you gain confidence!Add to Conversation
