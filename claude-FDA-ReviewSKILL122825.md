<scratchpad>
Analyzing the FDA 510(k) Agentic Reviewer application:
Main functionalities identified:

PDF extraction and markdown conversion with page range selection
Multi-LLM integration (OpenAI, Gemini, Anthropic, Grok) with routing
510(k) intelligence search and analysis with structured tables
Document comparison/diff across versions with detailed change tracking
Entity extraction and comprehensive summarization
Review checklist generation from guidance documents
Report generation combining checklists and review results
Note keeper with AI restructuring
AI "Magics" (formatting, keywords, action items, concept maps, glossaries)
Dashboard with analytics and history tracking
Multi-language support (English, Traditional Chinese)
Painter style theming system
Configurable agents via YAML

Distinct skills to create:

PDF Page Range Extractor & Markdown Converter
Multi-Provider LLM Router & Orchestrator
FDA 510(k) Intelligence Analyzer
Dual-Version Document Comparator (100+ differences)
Regulatory Entity Extractor & Summarizer
Review Checklist Generator from Guidance
Formal Review Report Builder
AI Note Keeper with Smart Restructuring
AI Magic Tools Suite (5 magic types)
Regulatory Analytics Dashboard
YAML-Based Agent Configuration System

This gives us 11 comprehensive skills covering all major functionality.
</scratchpad>
<skills_document>
SKILL.md - FDA 510(k) Agentic Reviewer Skills

Skill 1: PDF Page Range Extractor & Markdown Converter
pdf-range-markdown-transformer
Description
Advanced PDF processing system that extracts specific page ranges from regulatory PDFs (510(k) submissions, guidance documents, technical reports) and converts them into clean, structured markdown preserving regulatory document formatting including tables, lists, and hierarchical sections.
Capabilities

Selective Page Extraction: Extract any page range (1-based indexing) from multi-page PDFs
Text Preservation: Maintain original text content with intelligent paragraph detection
Structure Recognition: Identify and preserve headings, subheadings, and section hierarchies
Table Conversion: Convert PDF tables into properly formatted markdown tables
List Formatting: Preserve bulleted and numbered lists with proper indentation
Error Handling: Gracefully handle corrupted or unreadable pages
Large Document Support: Process PDFs with thousands of pages efficiently
Encoding Safety: Handle special characters and Unicode content from regulatory documents
Section Separation: Insert clear section breaks between different document parts
Metadata Preservation: Capture page numbers and section references

Regulatory Document Support

FDA 510(k) submissions (Traditional, Special, Abbreviated)
FDA guidance documents
Technical reports and white papers
Clinical study reports
Risk management files (ISO 14971)
Design verification/validation protocols
Biocompatibility testing reports

Processing Pipeline
pythonCopy1. PDF Upload → File validation
2. Page Range Selection → User specifies start/end pages
3. Text Extraction → PyPDF reader extracts page-by-page
4. Content Cleaning → Remove artifacts, normalize whitespace
5. Structure Detection → Identify headings, lists, tables
6. Markdown Conversion → Format into clean markdown
7. Quality Check → Validate output completeness
8. User Review → Display extracted text for verification
Output Format
markdownCopy# [Document Title/Section Name]

## Section 1: Device Description
[Extracted content with preserved formatting]

### 1.1 Subsection
- Bullet point 1
- Bullet point 2

## Section 2: Indications for Use
[Content continues...]

| Column 1 | Column 2 | Column 3 |
|----------|----------|----------|
| Data 1   | Data 2   | Data 3   |

## Section 3: Performance Testing
[Additional content...]
Use Cases

Extract specific sections from 500+ page 510(k) submissions
Convert guidance documents for AI analysis
Isolate clinical data sections for review
Extract predicate comparison tables
Pull risk assessment sections for comparison

Integration Points

Feeds into AI summarization agents
Provides input for entity extraction
Enables document comparison workflows
Supports checklist generation from guidance

MANDATORY TRIGGERS
PDF extraction, extract PDF pages, PDF to markdown, convert PDF, page range, PDF converter, regulatory PDF, 510k PDF, extract pages, PDF processing, page selection, PDF text extraction, document extraction, convert pages to markdown, PDF parser

Skill 2: Multi-Provider LLM Router & Intelligent Orchestrator
multi-llm-routing-orchestrator
Description
Enterprise-grade LLM routing system that intelligently routes requests across OpenAI (GPT-4o-mini, GPT-4.1-mini), Google Gemini (2.5-flash, 3-flash-preview), Anthropic Claude (3.5 Sonnet, Haiku), and xAI Grok models with automatic provider detection, API key management, and unified response handling.
Capabilities

Multi-Provider Support: Route to 9+ different LLM models across 4 providers
Automatic Provider Detection: Identify provider from model name automatically
Unified API Interface: Single function call regardless of underlying provider
API Key Management: Environment variable and manual key support with fallback
Token Configuration: Adjustable max_tokens (1000-120,000) per request
Temperature Control: Fine-tune creativity (0.0-1.0) for each call
Error Handling: Provider-specific error messages and retry logic
Response Normalization: Consistent output format across all providers
System/User Prompt Separation: Proper role-based prompting for each API
HTTP Timeout Management: Configurable timeouts for API stability
Synchronous Execution: Reliable blocking calls for Streamlit compatibility

Supported Models & Providers
OpenAI (GPT)

gpt-4o-mini: Fast, cost-effective for most tasks
gpt-4.1-mini: Enhanced reasoning capabilities

Google Gemini

gemini-2.5-flash: Balanced speed and quality
gemini-2.5-flash-lite: Ultra-fast responses
gemini-3-flash-preview: Latest preview features

Anthropic Claude

claude-3-5-sonnet-20241010: Highest quality analysis
claude-3-5-haiku-20241022: Fast, efficient processing

xAI Grok

grok-4-fast-reasoning: Advanced reasoning with speed
grok-3-mini: Lightweight processing

API Key Priority System
pythonCopy1. Manual API key input (session state)
2. Environment variable (OPENAI_API_KEY, etc.)
3. Error if neither available

Key Storage Hierarchy:
st.session_state["api_keys"] = {
    "openai": key,
    "gemini": key,
    "anthropic": key,
    "grok": key
}
Routing Logic
pythonCopydef get_provider(model: str) -> str:
    if model in OPENAI_MODELS:
        return "openai"
    elif model in GEMINI_MODELS:
        return "gemini"
    elif model in ANTHROPIC_MODELS:
        return "anthropic"
    elif model in GROK_MODELS:
        return "grok"
    else:
        raise ValueError(f"Unknown model: {model}")
Unified Call Interface
pythonCopyresponse = call_llm(
    model="gpt-4o-mini",
    system_prompt="You are an FDA reviewer...",
    user_prompt="Analyze this 510(k)...",
    max_tokens=12000,
    temperature=0.2,
    api_keys={"openai": "sk-..."}
)
Provider-Specific Implementation Details
OpenAI Implementation
pythonCopyclient = OpenAI(api_key=key)
response = client.chat.completions.create(
    model=model,
    messages=[
        {"role": "system", "content": system_prompt},
        {"role": "user", "content": user_prompt}
    ],
    max_tokens=max_tokens,
    temperature=temperature
)
return response.choices[0].message.content
Gemini Implementation
pythonCopygenai.configure(api_key=key)
model = genai.GenerativeModel(model_name)
response = model.generate_content(
    system_prompt + "\n\n" + user_prompt,
    generation_config={
        "max_output_tokens": max_tokens,
        "temperature": temperature
    }
)
return response.text
Anthropic Implementation
pythonCopyclient = Anthropic(api_key=key)
response = client.messages.create(
    model=model,
    system=system_prompt,
    max_tokens=max_tokens,
    temperature=temperature,
    messages=[{"role": "user", "content": user_prompt}]
)
return response.content[0].text
Grok/xAI Implementation
pythonCopywith httpx.Client(base_url="https://api.x.ai/v1") as client:
    response = client.post(
        "/chat/completions",
        headers={"Authorization": f"Bearer {key}"},
        json={
            "model": model,
            "messages": [
                {"role": "system", "content": system_prompt},
                {"role": "user", "content": user_prompt}
            ],
            "max_tokens": max_tokens,
            "temperature": temperature
        }
    )
return response.json()["choices"][0]["message"]["content"]
Usage Tracking & Analytics

Token estimation (char_count / 4)
Request logging with timestamps
Model usage statistics
Cost projection (provider-dependent)

MANDATORY TRIGGERS
LLM routing, multi-provider LLM, OpenAI Gemini Claude, model selection, API routing, LLM orchestration, GPT Gemini Claude Grok, multi-model, LLM integration, AI provider, model switching, LLM API, call LLM, route request

Skill 3: FDA 510(k) Intelligence Analyzer & Structured Table Generator
fda-510k-intelligence-analyzer
Description
Specialized AI agent for comprehensive FDA 510(k) submission analysis that generates detailed, review-ready summaries with a minimum of 5 structured markdown tables covering device overview, indications, technological characteristics, performance testing, and risk controls. Produces 3000-4000 word regulatory-quality analysis formatted for FDA reviewers.
Capabilities

Device Intelligence Gathering: Synthesize information from device name, 510(k) number, sponsor, and product code
Regulatory Database Emulation: Structure queries as if searching FDA databases
Multi-Table Generation: Generate 5+ comprehensive markdown tables minimum
Review-Oriented Summaries: 3000-4000 word detailed analysis in FDA memo style
Predicate Comparison: Detailed comparison with predicate devices
Risk Assessment Integration: Comprehensive risk-control table generation
Multi-Language Support: English and Traditional Chinese output
Performance Data Structuring: Organize bench, animal, and clinical testing data
Regulatory Pathway Analysis: Identify applicable regulations and standards
Contextual Enhancement: Incorporate additional user-provided context

Mandatory Table Structure
Table 1: Device Overview
FieldValueTrade Name[Device name]510(k) Number[K-number]Sponsor/Manufacturer[Company]Product Code[Code]Regulation Number[21 CFR xxx.xxx]Classification[Class I/II/III]Review Panel[Panel name]Decision Date[Date]
Table 2: Indications for Use
CategoryDetailsIntended Use[Primary purpose]Indications[Specific indications]Target Population[Patient demographics]Contraindications[When not to use]Environment of Use[Clinical setting]
Table 3: Technological Characteristics
CharacteristicSubject DevicePredicate DeviceComparisonDesign Feature 1[Details][Details]Same/DifferentMaterials[List][List]AssessmentDimensions[Specs][Specs]AnalysisOperating Principle[Description][Description]Evaluation
Table 4: Performance Testing
Test TypeTest DescriptionAcceptance CriteriaResultsPass/FailBench Test 1[Protocol][Criteria][Summary]PassBiocompatibility[ISO 10993 tests][Standards][Outcomes]PassAnimal Testing[If applicable][Endpoints][Findings]PassClinical Study[Study design][Primary endpoints][Results]Pass
Table 5: Risks & Mitigations
RiskSeverityProbabilityRisk Control MeasuresResidual Risk[Risk 1]High/Med/LowHigh/Med/Low[Mitigations]Acceptable[Risk 2]......[Controls]Acceptable
Output Structure
markdownCopy# FDA 510(k) Review Summary: [Device Name]
## K-Number: [Kxxxxxx]

## Executive Summary
[200-300 word overview of device, indication, and clearance recommendation]

## 1. Device Overview
[Detailed description including design, materials, specifications]

[TABLE 1: Device Overview - 8+ rows]

## 2. Indications for Use and Intended Population
[Comprehensive indication analysis]

[TABLE 2: Indications - 5+ rows]

## 3. Technological Characteristics and Predicate Comparison
[Detailed comparison with predicate device(s)]

[TABLE 3: Technological Characteristics - 4+ characteristics]

## 4. Performance Testing
[Analysis of all testing performed]

[TABLE 4: Performance Testing - 5+ test types]

### 4.1 Bench Testing
[Details]

### 4.2 Biocompatibility
[ISO 10993 battery results]

### 4.3 Clinical Performance
[If applicable]

## 5. Risk Management and Controls
[ISO 14971 risk analysis summary]

[TABLE 5: Risk-Control Matrix - 8+ risks]

## 6. Benefit-Risk Assessment
[Detailed benefit-risk discussion]

## 7. Regulatory Standards and Consensus Standards
[List of applicable standards: ISO, IEC, ASTM, etc.]

## 8. Labeling Review
[Key labeling elements and adequacy]

## 9. Outstanding Issues and Recommendations
[Any deficiencies or additional information needed]

## 10. Conclusion
[Final recommendation: Clearance, Hold, Not Substantially Equivalent]

---
**Word Count**: 3000-4000 words
**Tables**: Minimum 5 comprehensive tables
**Review Date**: [Auto-generated timestamp]
FDA Review Style Guidelines

Use formal regulatory language
Follow FDA review memo format
Include specific CFR references
Reference applicable guidance documents
Highlight substantial equivalence findings
Flag any safety or effectiveness concerns
Provide clear recommendations

Input Processing
pythonCopyinputs = {
    "device_name": "Acme Cardiac Monitor",
    "k_number": "K123456",
    "sponsor": "Acme Medical Corp",
    "product_code": "DPS",
    "additional_context": "AI-powered ECG analysis with cloud connectivity"
}

# Agent processes and generates comprehensive analysis
MANDATORY TRIGGERS
510k analysis, 510(k) review, FDA device, medical device review, 510k intelligence, device clearance, predicate comparison, substantial equivalence, FDA submission, K number, regulatory review, device assessment, medical device analysis, 510k summary, FDA clearance

Skill 4: Dual-Version Document Comparator with 100+ Difference Detection
dual-version-diff-analyzer
Description
Advanced document comparison engine that identifies a minimum of 100 meaningful differences between two versions of regulatory documents (510(k) submissions, protocols, reports). Generates comprehensive markdown tables with page references, before/after summaries, and regulatory significance assessment for each change.
Capabilities

Comprehensive Difference Detection: Minimum 100 differences identified per comparison
Multi-Level Analysis: Text-level, semantic-level, and regulatory-impact analysis
Before/After Tracking: Capture exact wording changes with context
Page Reference Mapping: Approximate page/section locations for each difference
Regulatory Significance Scoring: Assess review impact of each change
Change Categorization: Classify changes by type (addition, deletion, modification, relocation)
Risk-Relevant Flagging: Highlight changes affecting safety or effectiveness
Structured Table Output: Organized markdown tables for easy review
Cross-Document Analysis: Compare different document types (submission vs. amendment)
Version Control Integration: Track document revision history
Multilingual Comparison: Support English and Traditional Chinese documents

Difference Categories
Critical Changes (Require Review)

Indications for use modifications
New or modified risks
Changes to performance criteria
Updated test results
Predicate device changes
Material or design modifications

Administrative Changes (Low Impact)

Formatting adjustments
Typo corrections
Date updates
Contact information changes
Minor wording improvements

Documentation Changes (Moderate Impact)

New test reports added
Updated literature references
Expanded explanations
Additional supporting data
Clarifications requested by FDA

Comprehensive Difference Table Format
markdownCopy# Document Version Comparison Report

## Summary Statistics
- **Total Differences Identified**: 127
- **Critical Changes**: 23
- **Moderate Changes**: 48
- **Administrative Changes**: 56
- **Old Version**: [filename] (Date)
- **New Version**: [filename] (Date)

## Detailed Difference Analysis

| ID | Title | Change Type | Difference Details | Before | After | Page/Section | Regulatory Significance | Review Impact | Comments |
|----|-------|-------------|-------------------|--------|-------|--------------|------------------------|---------------|----------|
| 001 | Indication Expansion | Modification | Indications expanded to include pediatric population | "Adults 18+ years" | "Patients 12+ years including pediatric" | Section 2.1, p.15 | HIGH - New population | Requires pediatric data review | Verify age-specific testing |
| 002 | New Risk Identified | Addition | Added risk of skin irritation with prolonged use | [Not present] | "Risk of contact dermatitis with >24hr continuous use" | Section 6.3, p.78 | HIGH - New risk | Review mitigation adequacy | Check biocompatibility data |
| 003 | Test Criteria Updated | Modification | Tensile strength acceptance criteria changed | "≥50 N" | "≥45 N (5% margin)" | Table 8, p.102 | MODERATE - Less stringent | Verify engineering justification | Review test data |
| 004 | Clinical Data Added | Addition | New 50-patient clinical study results included | [Not present] | "Study XYZ-2024: 50 patients, 95% success rate" | Section 9.2, p.145 | MODERATE - Supporting data | Review study protocol | Assess endpoints |
| ... | ... | ... | ... | ... | ... | ... | ... | ... | ... |
| 127 | Footer Update | Administrative | Updated company address in footer | "123 Old St" | "456 New Ave" | All pages | LOW - Administrative | No review impact | Note for records |

## Critical Changes Requiring Detailed Review

### Change #001: Indication Expansion to Pediatrics
**Location**: Section 2.1, Pages 15-17
**Type**: Modification - Indication Expansion
**Before**: "Intended for adult patients aged 18 years and older"
**After**: "Intended for patients aged 12 years and older, including pediatric patients"

**Regulatory Implications**:
- New patient population requires age-specific testing
- Pediatric risk assessment needed
- Labeling must address pediatric use and dosing
- Consider FDA Pediatric Device Consortia guidance

**Required Reviewer Actions**:
- [ ] Review pediatric-specific bench testing
- [ ] Assess pediatric risk analysis
- [ ] Verify age-appropriate labeling
- [ ] Check predicate pediatric clearance status

---

### Change #002: New Risk - Skin Irritation
[Detailed analysis continues for each critical change...]

## Summary by Category

### Safety/Effectiveness Changes: 23
[List of all changes affecting safety or effectiveness]

### Design Changes: 15
[List of design modifications]

### Testing Changes: 18
[List of test method or criteria changes]

### Documentation Updates: 71
[List of documentation improvements]

## Reviewer Recommendations

1. **Priority Review Items** (Critical Changes): Review items 001-023 in detail
2. **Secondary Review Items** (Moderate Changes): Review items 024-071 for completeness
3. **Administrative Items** (Low Priority): Items 072-127 for documentation only

## Overall Assessment
[Summary of whether changes warrant additional questions, require deficiency letter, or are acceptable]
Processing Pipeline
pythonCopy1. Document Upload → Validate both versions
2. Text Extraction → Extract full text from both PDFs
3. Preprocessing → Normalize formatting, remove artifacts
4. Alignment → Align corresponding sections
5. Difference Detection → Identify all changes (100+ minimum)
6. Categorization → Classify each difference by type and impact
7. Regulatory Analysis → Assess significance of each change
8. Table Generation → Create structured markdown tables
9. Summary Creation → Generate executive summary of changes
10. Export → Provide downloadable comparison report
Advanced Features

Semantic Similarity Analysis: Detect paraphrasing and rewording
Table Diff Visualization: Track changes in data tables
Figure Comparison: Note when figures are added, removed, or modified
Reference Tracking: Identify new or removed literature references
Standard Citations: Track changes in cited consensus standards
Cross-Reference Validation: Ensure section references remain valid

Use Cases

Compare original 510(k) with amendment submission
Track changes between pre-submission and final submission
Review manufacturer responses to deficiency letters
Compare similar devices from same manufacturer
Audit document version control compliance

MANDATORY TRIGGERS
document comparison, version compare, diff analysis, compare versions, track changes, document diff, before after, version control, change detection, compare documents, find differences, version analysis, document changes, revision comparison, compare PDFs

Skill 5: Regulatory Entity Extractor & Comprehensive Summarizer
regulatory-entity-summarizer
Description
Advanced NLP-powered system that extracts 20+ key regulatory entities from 510(k) documents and generates comprehensive 3000-4000 word review summaries structured for FDA evaluation. Produces detailed entity tables with context, reviewer considerations, and location references alongside section-by-section regulatory analysis.
Capabilities

Multi-Entity Extraction: Extract 20+ diverse entity types from regulatory documents
Contextual Understanding: Capture surrounding context for each entity
Entity Classification: Categorize entities by type (Indication, Risk, Test, Mitigation, Design Feature, etc.)
Location Mapping: Reference specific sections/pages where entities appear
Reviewer Commentary: Auto-generate reviewer considerations for each entity
Comprehensive Summarization: Generate 3000-4000 word FDA-style review summaries
Structured Output: Organize summaries by regulatory review sections
Markdown Table Generation: Create detailed entity tables with 5+ columns
Cross-Reference Linking: Link related entities (e.g., risk to mitigation)
Multilingual Support: Process English and Traditional Chinese documents
Priority Flagging: Highlight high-priority entities for review focus

Entity Types Extracted
Device & Indication Entities

Indications for use
Intended patient populations
Device classifications
Product codes
Predicate devices

Risk & Safety Entities

Identified hazards
Risk severity/probability ratings
Mitigation measures
Residual risks
Safety concerns

Testing & Performance Entities

Test methods
Acceptance criteria
Performance specifications
Study endpoints
Test results

Design & Technical Entities

Design features
Materials of construction
Operating principles
Key components
Manufacturing processes

Regulatory & Compliance Entities

Referenced standards (ISO, IEC, ASTM)
CFR citations
Guidance documents
Biocompatibility tests (ISO 10993)
Sterilization methods

Clinical & Data Entities

Clinical study designs
Patient cohorts
Adverse events
Effectiveness outcomes
Literature references

Entity Table Format
markdownCopy## Extracted Regulatory Entities

**Total Entities Extracted**: 24
**Document Source**: [filename]
**Extraction Date**: [timestamp]

| ID | Entity Type | Entity Name / Phrase | Context (Excerpt) | Reviewer Comment / Considerations | Location / Section | Priority |
|----|-------------|----------------------|-------------------|----------------------------------|-------------------|----------|
| 001 | Indication | "Treatment of Type 2 Diabetes in adults" | "The device is indicated for continuous glucose monitoring in adult patients diagnosed with Type 2 Diabetes Mellitus" | Verify indication matches predicate. Confirm adult-only population appropriate. | Section 2.1: Indications for Use, p.8 | HIGH |
| 002 | Risk | "Skin irritation from adhesive" | "Identified risk: Potential for contact dermatitis or skin irritation from prolonged adhesive contact (>14 days)" | Review biocompatibility data for skin sensitization. Check mitigation adequacy. | Section 6.2: Risk Analysis, Table 6-1, p.45 | HIGH |
| 003 | Mitigation | "Hypoallergenic medical-grade adhesive selection" | "Risk control: Use of ISO 10993 tested hypoallergenic acrylic adhesive reduces sensitization risk" | Verify ISO 10993-10 testing completed. Review test reports. | Section 6.3: Risk Controls, p.47 | HIGH |
| 004 | Test | "Adhesive Peel Strength Test per ASTM D3330" | "Bench testing: Peel strength measured at 180° angle per ASTM D3330, acceptance criteria ≥2.0 N/cm" | Confirm test method appropriate. Review test data and acceptance rationale. | Section 7.4: Bench Testing, p.67 | MEDIUM |
| 005 | Design Feature | "Wireless Bluetooth 5.0 communication" | "The sensor transmits glucose readings via Bluetooth 5.0 (2.4 GHz) to smartphone app every 5 minutes" | Review cybersecurity controls. Verify wireless coexistence testing. Check labeling for interference warnings. | Section 3.2: Device Description, p.18 | HIGH |
| 006 | Standard | "ISO 10993-1:2018 Biocompatibility Evaluation" | "Biocompatibility testing conducted per ISO 10993-1:2018 for prolonged skin contact (>24hr, <30 days)" | Verify appropriate test battery for contact duration. Review test reports for compliance. | Section 8.1: Biocompatibility, p.89 | HIGH |
| 007 | Acceptance Criteria | "Measurement accuracy: ±15% of YSI reference" | "Clinical accuracy acceptance: ≥95% of readings within ±15% of YSI glucose analyzer reference values" | Assess appropriateness of ±15% criteria. Compare to predicates and consensus. | Section 9.3: Clinical Study, Table 9-2, p.112 | HIGH |
| 008 | Clinical Result | "97.8% readings met accuracy criteria" | "Clinical study results: 97.8% (CI: 96.2-99.1%) of 5,482 paired readings met ±15% accuracy criteria" | Strong performance. Verify statistical analysis methodology. Check for subgroup variations. | Section 9.4: Results, p.118 | MEDIUM |
| ... | ... | ... | ... | ... | ... | ... |
| 024 | Labeling Element | "Instructions for Use document" | "Comprehensive IFU includes setup instructions, troubleshooting guide, and safety warnings" | Review IFU for adequacy. Verify all risks communicated. Check readability. | Section 11.2: Labeling, p.167 | MEDIUM |

## Entity Relationship Map

### Risk → Mitigation Chains
- **Risk 002** (Skin irritation) → **Mitigation 003** (Hypoallergenic adhesive)
- **Risk** (Data breach) → **Mitigation** (Encryption, authentication)

### Test → Acceptance Criteria → Results
- **Test 004** (Peel strength) → **Criteria 007** (≥2.0 N/cm) → **Result** (2.4±0.3 N/cm, Pass)

### Design Feature → Associated Risks → Controls
- **Feature 005** (Bluetooth wireless) → **Risk** (Interference) → **Control** (Coexistence testing)
Comprehensive Summary Structure
markdownCopy# Comprehensive 510(k) Review Summary with Entity Analysis

## Executive Summary (300-400 words)
[High-level overview of device, key findings from entity analysis, and recommendation]

## 1. Device Description and Classification (400-500 words)
[Detailed description incorporating extracted design entities, features, and specifications]

**Key Entities**:
- Device Classification: [Entity 001]
- Product Code: [Entity 002]
- Key Design Features: [Entities 005, 012, 015]

## 2. Indications for Use and Intended Population (400-500 words)
[Analysis of indication entities with comparison to predicates]

**Extracted Indication Entities**:
- Primary Indication: [Entity 001]
- Target Population: [Entity 016]
- Contraindications: [Entity 017]

## 3. Technological Characteristics (500-600 words)
[Comparison with predicate using extracted design and technical entities]

**Key Design Entities Analyzed**:
- [Entity 005]: Bluetooth wireless communication
- [Entity 012]: Sensor calibration algorithm
- [Entity 015]: Battery life specification

## 4. Performance Testing and Validation (600-700 words)
[Comprehensive testing review using extracted test, criteria, and result entities]

### 4.1 Bench Testing
**Test Entities Identified**: [Entities 004, 018, 019]
[Analysis of each test method, criteria, and results]

### 4.2 Biocompatibility
**Standard Entities**: [Entity 006 - ISO 10993-1:2018]
[Review of biocompatibility test battery]

### 4.3 Clinical Performance
**Clinical Entities**: [Entities 007, 008, 020]
[Study design, endpoints, results analysis]

## 5. Risk Management and Safety (600-700 words)
[Comprehensive risk analysis using extracted risk and mitigation entities]

**Risk-Mitigation Chains Identified**:
1. **Risk Entity 002** → **Mitigation Entity 003**
2. **Risk Entity 010** → **Mitigation Entity 011**
[Detailed analysis of each risk-control pair]

## 6. Regulatory Standards Compliance (300-400 words)
[Analysis of all extracted standard entities]

**Standards Referenced**:
- [Entity 006]: ISO 10993-1:2018
- [Entity 013]: IEC 60601-1
- [Entity 021]: ISO 15197:2013

## 7. Labeling and Information Disclosure (300-400 words)
[Review of labeling entities and adequacy]

## 8. Benefit-Risk Assessment (400-500 words)
[Synthesis of risk entities, mitigation entities, and performance entities]

## 9. Outstanding Issues and Deficiencies (200-300 words)
[Highlight any missing entities, incomplete mitigations, or concerns]

## 10. Conclusion and Recommendation (200-300 words)
[Final assessment based on entity analysis]

---
**Total Word Count**: 3000-4000 words
**Entities Extracted**: 24
**High Priority Entities**: 12
**Review Recommendation**: [Clearance / Additional Info Needed / NSE]
Entity Extraction Algorithm
pythonCopy1. Document Ingestion → Parse markdown/text input
2. Section Identification → Detect regulatory sections
3. Entity Recognition → NLP-based entity extraction
4. Context Capture → Extract surrounding sentences (±2)
5. Entity Classification → Categorize by entity type
6. Location Mapping → Record section/page references
7. Relationship Detection → Link related entities
8. Reviewer Comment Generation → AI-generated considerations
9. Priority Assignment → Flag high-priority entities
10. Table Generation → Format into structured markdown
11. Summary Generation → Create 3000-4000 word analysis
12. Cross-Referencing → Link entities to summary sections
MANDATORY TRIGGERS
entity extraction, extract entities, regulatory entities, NLP extraction, key entities, identify risks, extract tests, find indications, entity analysis, summarize document, comprehensive summary, regulatory summary, extract key information, entity recognition, document entities

Skill 6: FDA Guidance-Based Checklist Generator
guidance-checklist-generator
Description
Intelligent checklist creation system that processes FDA guidance documents (PDF, markdown, or text) and automatically generates comprehensive, structured review checklists with questions, rationale, source references, response options, and reviewer note placeholders. Produces regulatory-grade checklists aligned with FDA expectations.
Capabilities

Multi-Format Guidance Input: Process PDF, markdown, and text guidance documents
Automatic Section Detection: Identify all relevant review topics from guidance
Question Generation: Create specific, actionable review questions for each topic
Rationale Extraction: Link each checklist item to source guidance section
Response Structure: Include Yes/No/NA options with conditional logic
Reviewer Note Placeholders: Provide blank lines for reviewer documentation
Item ID Assignment: Unique identifiers for each checklist item
Hierarchical Organization: Organize by major topics and sub-topics
Completeness Verification: Ensure all guidance sections represented
Custom Guidance Support: Handle device-specific and general guidance
Multilingual Output: Generate checklists in English or Traditional Chinese

Guidance Document Types Supported

FDA Device-Specific Guidance (e.g., "Glucose Meters - Premarket Notification Submissions")
General 510(k) Guidance ("The 510(k) Program: Evaluating Substantial Equivalence")
Consensus Standard Guidance (ISO, IEC, ASTM interpretations)
FDA Recognized Standards Lists
Custom organizational SOPs and review templates

Checklist Structure & Format
markdownCopy# FDA 510(k) Review Checklist
## Based on: [Guidance Document Title]
## Guidance Version: [Date]
## Generated: [Timestamp]

---

## Section 1: Administrative and Identification Information

### 1.1 Device Identification
**Item ID**: ADMIN-001
**Question**: Is the device trade name, model number, and 510(k) number clearly identified?
**Rationale**: Required per 21 CFR 807.87(a). Guidance Section 1.2 states "The device must be clearly identified..."
**Source**: FDA 510(k) Guidance Section 1.2, p.3
**Response Options**: 
- [ ] Yes - Complete and clear identification provided
- [ ] No - Missing or unclear identification
- [ ] NA - Not applicable

**Reviewer Notes**:
_______________________________________________________________________________
_______________________________________________________________________________

### 1.2 Manufacturer Information
**Item ID**: ADMIN-002
**Question**: Are the manufacturer name, address, and establishment registration number provided?
**Rationale**: Required per 21 CFR 807.87(b). Enables facility inspection coordination.
**Source**: 21 CFR 807.87(b), FDA 510(k) Guidance Section 1.3
**Response Options**:
- [ ] Yes - Complete manufacturer information
- [ ] No - Incomplete or missing information
- [ ] NA

**Reviewer Notes**:
_______________________________________________________________________________
_______________________________________________________________________________

---

## Section 2: Indications for Use

### 2.1 Indication Statement
**Item ID**: IND-001
**Question**: Does the indication for use statement clearly describe the disease/condition, intended patient population, and intended effect?
**Rationale**: Guidance requires specific indication elements per Section 3.1. Vague indications are common deficiency.
**Source**: FDA 510(k) Guidance Section 3.1 "Indications for Use", p.12
**Response Options**:
- [ ] Yes - Clear, complete indication statement
- [ ] No - Vague, incomplete, or missing elements
- [ ] NA

**Conditional Follow-Up**: If "No", specify which elements are deficient:
- [ ] Disease/condition unclear
- [ ] Patient population not specified
- [ ] Intended effect ambiguous

**Reviewer Notes**:
_______________________________________________________________________________
_______________________________________________________________________________

### 2.2 Predicate Indication Comparison
**Item ID**: IND-002
**Question**: Is the subject device indication the same as or more specific than the predicate?
**Rationale**: Broader indications require clinical data (Guidance Section 3.2). Same/narrower indications support substantial equivalence.
**Source**: FDA 510(k) Guidance Section 3.2, p.13
**Response Options**:
- [ ] Same indication as predicate
- [ ] More specific (subset) of predicate indication
- [ ] Broader indication - requires clinical data
- [ ] Different indication - may not support SE

**Reviewer Notes**:
_______________________________________________________________________________
_______________________________________________________________________________

---

## Section 3: Device Description and Technological Characteristics

### 3.1 Design Description Adequacy
**Item ID**: DESC-001
**Question**: Does the device description include design, materials, physical characteristics, and operating principles?
**Rationale**: Comprehensive description required per Guidance Section 4.1 to assess substantial equivalence.
**Source**: FDA 510(k) Guidance Section 4.1 "Device Description", p.18-20
**Response Options**:
- [ ] Yes - Comprehensive description provided
- [ ] Partial - Some elements missing or insufficient detail
- [ ] No - Inadequate description

**Required Elements Checklist**:
- [ ] Design specifications and dimensions
- [ ] Materials of construction
- [ ] Operating principles/mechanism of action
- [ ] Energy source (if applicable)
- [ ] Software/firmware description (if applicable)

**Reviewer Notes**:
_______________________________________________________________________________
_______________________________________________________________________________

### 3.2 Predicate Comparison Table
**Item ID**: DESC-002
**Question**: Is a detailed comparison table provided showing subject vs. predicate technological characteristics?
**Rationale**: Side-by-side comparison required per Guidance Section 4.2. Must address all differences.
**Source**: FDA 510(k) Guidance Section 4.2, p.21-22
**Response Options**:
- [ ] Yes - Comprehensive comparison table
- [ ] Partial - Table incomplete or missing key characteristics
- [ ] No - No comparison table or inadequate

**Assessment Criteria**:
- [ ] All key design features compared
- [ ] Materials compared
- [ ] Operating principles compared
- [ ] Differences clearly identified
- [ ] Impact of differences discussed

**Reviewer Notes**:
_______________________________________________________________________________
_______________________________________________________________________________

---

## Section 4: Performance Testing

### 4.1 Bench Testing Adequacy
**Item ID**: TEST-001
**Question**: Does bench testing address all critical performance characteristics relevant to intended use?
**Rationale**: Guidance Section 5.1 requires testing of all performance specs. Gaps may necessitate deficiency letter.
**Source**: FDA 510(k) Guidance Section 5.1 "Bench Testing", p.28-32; Device-Specific Guidance
**Response Options**:
- [ ] Yes - Comprehensive bench testing
- [ ] Partial - Some tests missing or insufficient
- [ ] No - Inadequate bench testing

**Testing Categories to Verify**:
- [ ] Performance specifications (accuracy, precision, range)
- [ ] Electrical safety (if applicable) - IEC 60601-1
- [ ] Mechanical safety (strength, durability)
- [ ] Software verification/validation (if applicable)
- [ ] Usability/human factors testing
- [ ] Environmental testing (temperature, humidity, etc.)
- [ ] Shelf life/stability testing
- [ ] Packaging integrity

**Reviewer Notes**:
_______________________________________________________________________________
_______________________________________________________________________________

### 4.2 Biocompatibility Testing
**Item ID**: TEST-002
**Question**: Is biocompatibility testing appropriate for the device's patient contact type and duration per ISO 10993-1?
**Rationale**: FDA-recognized standard ISO 10993-1 requires specific test battery based on contact categorization.
**Source**: FDA Guidance "Use of ISO 10993-1", p.6-8; ISO 10993-1:2018 Table A.1
**Response Options**:
- [ ] Yes - Appropriate test battery completed
- [ ] No - Incorrect test battery or missing tests
- [ ] NA - No patient contact

**ISO 10993-1 Verification**:
- [ ] Contact type correctly categorized (surface/external communicating/implant)
- [ ] Contact duration correctly categorized (limited/prolonged/permanent)
- [ ] Test battery matches Table A.1 for category
- [ ] Test reports provided and acceptable

**Reviewer Notes**:
_______________________________________________________________________________
_______________________________________________________________________________

---

## Section 5: Risk Management

### 5.1 Risk Analysis Completeness
**Item ID**: RISK-001
**Question**: Has a comprehensive risk analysis been conducted per ISO 14971, identifying all reasonably foreseeable hazards?
**Rationale**: Risk management required per FDA Guidance "Application of ISO 14971 to Medical Devices".
**Source**: FDA ISO 14971 Guidance, Section 4; ISO 14971:2019
**Response Options**:
- [ ] Yes - Comprehensive risk analysis
- [ ] Partial - Some hazards likely missed
- [ ] No - Inadequate or missing risk analysis

**Risk Analysis Elements**:
- [ ] Hazard identification systematic and thorough
- [ ] Risk estimation (severity × probability) for each hazard
- [ ] Risk evaluation against acceptance criteria
- [ ] Residual risks identified after controls
- [ ] Benefit-risk analysis for residual risks

**Reviewer Notes**:
_______________________________________________________________________________
_______________________________________________________________________________

---

## Section 6: Clinical Performance (if applicable)

### 6.1 Clinical Study Necessity
**Item ID**: CLIN-001
**Question**: Is the determination of clinical data necessity justified based on guidance?
**Rationale**: Clinical data may not be needed if performance testing + predicate comparison + literature sufficient.
**Source**: FDA 510(k) Guidance Section 8.1, p.45
**Response Options**:
- [ ] Clinical study provided and necessary
- [ ] Clinical study provided but may not be necessary
- [ ] No clinical study - justification adequate
- [ ] No clinical study - justification inadequate (deficiency)

**Reviewer Notes**:
_______________________________________________________________________________
_______________________________________________________________________________

---

## Section 7: Labeling

### 7.1 IFU Adequacy
**Item ID**: LABEL-001
**Question**: Do the Instructions for Use include all elements required per 21 CFR 801 and device-specific guidance?
**Rationale**: Adequate labeling essential for safe and effective use. Common deficiency area.
**Source**: 21 CFR 801, FDA Labeling Guidance, Device-Specific Guidance
**Response Options**:
- [ ] Yes - IFU complete and adequate
- [ ] Partial - Some required elements missing
- [ ] No - Inadequate IFU

**Required IFU Elements**:
- [ ] Indications, contraindications, warnings
- [ ] Detailed use instructions
- [ ] Troubleshooting guide
- [ ] Safety precautions
- [ ] Specifications
- [ ] Storage and handling
- [ ] Customer service information

**Reviewer Notes**:
_______________________________________________________________________________
_______________________________________________________________________________

---

## Section 8: Overall Assessment

### 8.1 Substantial Equivalence Determination
**Item ID**: OVERALL-001
**Question**: Based on this checklist review, does the device appear substantially equivalent to the predicate?
**Rationale**: Final determination of SE based on totality of evidence.
**Source**: 21 CFR 807.87, FDA SE Guidance
**Response Options**:
- [ ] SE - Recommend clearance
- [ ] SE with conditions - Recommend clearance with post-market conditions
- [ ] Additional Info Needed - Issue deficiency letter
- [ ] NSE - Recommend Not Substantially Equivalent determination

**Key Factors in Determination**:
- [ ] Same intended use
- [ ] Same/similar technological characteristics OR
- [ ] Different characteristics but no safety/effectiveness questions
- [ ] Performance data supports equivalence
- [ ] Risks adequately controlled

**Reviewer Notes**:
_______________________________________________________________________________
_______________________________________________________________________________
_______________________________________________________________________________

---

## Checklist Summary

**Total Items**: 50
**Items Requiring Follow-Up**: [To be completed]
**Recommended Action**: [To be completed]
**Review Date**: __________________
**Reviewer Name**: __________________
**Reviewer Signature**: __________________
Generation Algorithm
pythonCopy1. Guidance Upload → Load PDF/MD/TXT
2. Text Extraction → Extract all content
3. Section Parsing → Identify major topics
4. Requirement Extraction → Parse "must", "should", "shall" statements
5. Question Formation → Convert requirements to questions
6. Rationale Linking → Link to source sections
7. Response Option Creation → Generate Yes/No/NA with conditionals
8. Hierarchy Construction → Organize into sections/subsections
9. ID Assignment → Create unique item IDs (PREFIX-NNN)
10. Note Placeholder Addition → Add blank lines for notes
11. Completeness Check → Verify all guidance sections covered
12. Formatting → Apply markdown structure
13. Summary Generation → Create checklist summary section
Use Cases

Generate review checklist from device-specific FDA guidance
Create SOPs from regulatory guidance documents
Standardize review processes across review teams
Train new reviewers with structured checklists
Ensure consistent, comprehensive reviews

MANDATORY TRIGGERS
checklist generation, create checklist, FDA guidance checklist, review checklist, guidance to checklist, generate review items, regulatory checklist, inspection checklist, compliance checklist, audit checklist, checklist from guidance, review questions, assessment checklist, evaluation checklist

Skill 7: Formal Review Report Builder from Checklist & Results
review-report-builder
Description
Professional review report compilation system that integrates structured review checklists with reviewer results/notes to generate formal FDA-style 510(k) review memoranda. Produces comprehensive, narrative review reports (3000-5000 words) with clear sections, subsections, findings, and recommendations suitable for regulatory decision documentation.
Capabilities

Dual Input Integration: Combines checklist markdown with review results/notes
Narrative Generation: Converts checklist Q&A into flowing narrative text
FDA Memo Formatting: Structures output as formal FDA review memorandum
Section Organization: Organizes by standard review memo sections
Finding Synthesis: Aggregates individual checklist responses into section findings
Issue Highlighting: Flags unresolved items, deficiencies, and concerns
Recommendation Formulation: Generates clear clearance/hold/NSE recommendations
Cross-Reference Integration: Links findings across sections
Condition Documentation: Specifies any conditions of clearance
Post-Market Commitment Tracking: Documents required post-market studies
Multilingual Support: Generate reports in English or Traditional Chinese

FDA Review Memo Structure
markdownCopy# FDA 510(k) REVIEW MEMORANDUM

## ADMINISTRATIVE INFORMATION

**510(k) Number**: K123456
**Device Trade Name**: Acme Continuous Glucose Monitor
**Sponsor**: Acme Medical Corporation
**Submission Date**: January 15, 2024
**Review Date**: February 28, 2024
**Reviewer**: [Name], [Title]
**Review Panel**: Clinical Chemistry (75)
**Product Code**: NBW
**Regulation Number**: 21 CFR 862.1355
**Device Classification**: Class II

**Predicate Device**:
- **510(k) Number**: K987654
- **Trade Name**: PredCGM System
- **Sponsor**: Predecessor Medical Inc.

---

## EXECUTIVE SUMMARY

This review evaluates the Acme Continuous Glucose Monitor (CGM), a Class II device 
indicated for continuous interstitial glucose monitoring in adult patients with Type 2 
diabetes mellitus. The submission provides a comprehensive comparison to the predicate 
device (K987654, PredCGM System), demonstrating substantial equivalence through 
equivalent indications for use, similar technological characteristics, and adequate 
performance data.

**Key Findings**:
- Indications for use are the same as the predicate
- Technological characteristics are similar with minor design refinements
- Bench testing demonstrates acceptable performance meeting all specifications
- Biocompatibility testing per ISO 10993-1 is complete and acceptable
- Clinical study (50 patients) demonstrates accuracy meeting ±15% criteria (97.8% agreement)
- Risk analysis per ISO 14971 is comprehensive with all risks adequately controlled
- Labeling is adequate with appropriate warnings and instructions

**Recommendation**: Substantial Equivalence (SE) - Clearance

**Conditions of Clearance**: None

---

## 1. DEVICE DESCRIPTION AND INDICATIONS FOR USE

### 1.1 Device Description

[Checklist Items ADMIN-001, DESC-001, DESC-002 synthesized into narrative]

The Acme CGM is a prescription device consisting of a disposable subcutaneous sensor, 
reusable transmitter, and smartphone application for real-time glucose monitoring. The 
sensor utilizes an electrochemical glucose oxidase-based detection method with a 
0.4mm × 5mm platinum electrode inserted subcutaneously in the upper arm. The sensor 
communicates with the transmitter via direct electrical contact, and the transmitter 
wirelessly transmits glucose readings to the smartphone app via Bluetooth 5.0 every 
5 minutes.

**Key Design Features**:
- Sensor dimensions: 25mm diameter × 4mm height
- Wear time: Up to 14 days
- Measurement range: 40-400 mg/dL
- Calibration: Factory calibrated (no user calibration required)
- Power: CR2032 lithium battery in transmitter (3-month life)
- Materials: Medical-grade acrylic adhesive, platinum electrode, polycarbonate housing

The device is intended for interstitial fluid glucose measurement only and requires 
confirmatory blood glucose testing for diabetes treatment decisions.

### 1.2 Indications for Use

[Checklist Item IND-001 narrative]

**Subject Device Indication**:
"The Acme CGM is indicated for continuous glucose monitoring of interstitial fluid 
glucose levels in adults 18 years of age and older with Type 2 diabetes mellitus. The 
device is intended to supplement, not replace, information obtained from standard 
home blood glucose monitoring devices. The device is indicated for use at home or in 
healthcare facilities."

**Predicate Device Indication**:
"The PredCGM System is indicated for continuous glucose monitoring of interstitial 
fluid glucose levels in adults 18 years of age and older with Type 2 diabetes mellitus. 
The device is intended to supplement, not replace, information obtained from standard 
home blood glucose monitoring devices."

**Comparison**: The subject device indication is essentially the same as the predicate, 
with the addition of "use at home or in healthcare facilities" which clarifies the 
intended environment of use. This addition does not broaden the indication and is 
acceptable.

**Finding**: The indications for use are the SAME as the predicate device. This supports 
a determination of substantial equivalence. ✓ ACCEPTABLE

---

## 2. COMPARISON TO PREDICATE DEVICE

### 2.1 Technological Characteristics Comparison

[Checklist Item DESC-002 narrative with expanded analysis]

The sponsor provided a comprehensive side-by-side comparison (Submission Table 3-1, p.22) 
of the subject and predicate devices across all key technological characteristics:

**SIMILAR Characteristics**:
- Detection method: Glucose oxidase electrochemical sensor (SAME)
- Sensor location: Subcutaneous upper arm (SAME)
- Measurement principle: Amperometric glucose detection (SAME)
- Wear duration: 14 days (SAME)
- Measurement range: 40-400 mg/dL (SAME)
- Device classification and regulation: Class II, 21 CFR 862.1355 (SAME)

**DIFFERENT Characteristics**:
1. **Wireless communication**: Subject device uses Bluetooth 5.0 vs. predicate's Bluetooth 4.2
2. **Display platform**: Subject device uses smartphone app vs. predicate's dedicated receiver
3. **Calibration**: Subject device is factory calibrated vs. predicate requires 2x daily calibration
4. **Adhesive material**: Subject device uses improved acrylic adhesive with lower sensitization profile

**Assessment of Differences**:

*Difference #1: Bluetooth 5.0 vs. 4.2*
The upgrade to Bluetooth 5.0 provides improved range and reliability but does not change 
the fundamental communication principle. The sponsor provided wireless coexistence testing 
per IEC 60601-1-2 (Submission Section 7.8) demonstrating no interference issues. This 
difference does NOT raise new safety or effectiveness questions. ✓

*Difference #2: Smartphone app vs. dedicated receiver*
The use of a smartphone app instead of dedicated receiver provides equivalent display 
functionality with additional features (data logging, trend analysis). The sponsor provided 
software verification/validation documentation (Submission Section 7.9, 500+ pages) 
demonstrating adequate software development lifecycle per FDA Software Guidance. 
Cybersecurity controls are addressed (see Section 4.5 below). This difference does NOT 
raise new safety or effectiveness questions. ✓

*Difference #3: Factory calibration vs. user calibration*
The elimination of user calibration requirements is an IMPROVEMENT that reduces use error 
potential. The sponsor demonstrated equivalent accuracy without calibration through extensive 
bench and clinical testing (see Section 3 below). This difference does NOT raise new safety 
or effectiveness questions and may improve safety. ✓

*Difference #4: Improved adhesive*
The new adhesive formulation was selected to reduce skin sensitization risk. Biocompatibility 
testing per ISO 10993-1 (Submission Section 8.1) demonstrates acceptable sensitization profile. 
This difference does NOT raise new safety or effectiveness questions and may improve safety. ✓

**Finding**: All technological differences have been adequately addressed through testing and 
do not raise new questions of safety or effectiveness. The devices have the same intended use 
and similar technological characteristics. This supports substantial equivalence. ✓ ACCEPTABLE

---

## 3. PERFORMANCE TESTING

### 3.1 Bench Testing

[Checklist Items TEST-001 synthesized]

The sponsor provided comprehensive bench testing addressing all critical performance 
characteristics:

**3.1.1 Accuracy and Precision**
- Method: YSI 2300 reference comparison across measurement range
- Acceptance: Mean bias ≤10 mg/dL, precision (CV) ≤5%
- Results: Mean bias 3.2 mg/dL, CV 2.8%
- Conclusion: PASS ✓

**3.1.2 Sensor Linearity**
- Method: Glucose spiking across 20-500 mg/dL range
- Acceptance: R² ≥0.99
- Results: R² = 0.998
- Conclusion: PASS ✓

**3.1.3 Sensor Stability (14-day wear)**
- Method: Continuous monitoring for 14 days with daily YSI reference
- Acceptance: Maintain ±15% accuracy throughout wear period
- Results: 96.2% readings within ±15% on day 1, 95.8% on day 14
- Conclusion: PASS ✓

**3.1.4 Interference Testing**
- Tested substances: Acetaminophen, ascorbic acid, salicylic acid, dopamine, L-dopa
- Acceptance: <10% bias at therapeutic concentrations
- Results: Max bias 4.2% (acetaminophen 5mg/dL)
- Conclusion: PASS ✓

**3.1.5 Environmental Testing**
- Temperature: 10-40°C storage, 18-30°C operation
- Humidity: 10-90% RH
- Acceptance: Performance maintained across ranges
- Results: All specifications met
- Conclusion: PASS ✓

**3.1.6 Electrical Safety**
- Standard: IEC 60601-1:2012
- Results: All tests passed, device classified Type BF
- Conclusion: PASS ✓

**3.1.7 Wireless Coexistence**
- Standard: IEC 60601-1-2:2014
- Results: No interference with other medical devices or from common RF sources
- Conclusion: PASS ✓

**3.1.8 Mechanical Safety**
- Adhesive peel strength: ≥2.0 N/cm (result: 2.4±0.3 N/cm) - PASS ✓
- Drop test: 1.5m drop to concrete (no damage) - PASS ✓
- IP rating: IP27 (protected against brief immersion) - PASS ✓

**Finding**: Bench testing is comprehensive and acceptable. All performance specifications 
met or exceeded. ✓ ACCEPTABLE

### 3.2 Biocompatibility

[Checklist Item TEST-002 narrative]

The sponsor conducted biocompatibility testing per ISO 10993-1:2018 for the adhesive and 
all patient-contacting components. The device is categorized as:
- Contact type: Surface contact (skin)
- Contact duration: Prolonged (>24 hours, ≤30 days)

Per ISO 10993-1 Table A.1, the following test battery was required and completed:

| Test | Standard | Result | Status |
|------|----------|--------|--------|
| Cytotoxicity | ISO 10993-5 | No cytotoxic response | PASS ✓ |
| Sensitization | ISO 10993-10 | No sensitization (GPMT score 0) | PASS ✓ |
| Irritation | ISO 10993-10 | Minimal irritation (PII <2.0) | PASS ✓ |

All testing was conducted at an ISO 17025 accredited laboratory (Test Lab Inc., Report #12345, 
dated November 2023). Test articles included worst-case extractables. Results demonstrate 
acceptable biocompatibility.

**Finding**: Biocompatibility testing is complete, appropriate for the contact category, and 
acceptable. ✓ ACCEPTABLE

### 3.3 Software Verification and Validation

[Synthesized from checklist and submission]

The smartphone application is classified as Level of Concern: Moderate per FDA Software 
Guidance (displays data, trend analysis, but treatment decisions require confirmatory testing).

The sponsor provided software documentation including:
- Software Development Plan
- Requirements Specification (250 requirements)
- Design Specification
- Traceability Matrix
- Test Protocols and Reports (>500 test cases)
- Risk Analysis (software hazards)
- Cybersecurity documentation

Software V&V covered:
- Unit testing (100% code coverage)
- Integration testing
- System testing
- User acceptance testing
- Regression testing
- Negative testing (error handling)

**Finding**: Software V&V documentation is comprehensive and follows FDA guidance. Level of 
Concern determination is appropriate. Testing is adequate. ✓ ACCEPTABLE

### 3.4 Cybersecurity

The sponsor addressed cybersecurity per FDA "Content of Premarket Submissions for Management 
of Cybersecurity in Medical Devices" (2014):

- **Threat modeling**: Conducted, identified potential vulnerabilities
- **Security controls**: AES-256 encryption for data transmission, user authentication, 
  automatic session timeout, secure boot
- **Software bill of materials**: Provided
- **Update mechanism**: Over-the-air updates with cryptographic verification
- **Vulnerability management plan**: Post-market plan for security patches

**Finding**: Cybersecurity controls are adequate for the device risk profile. ✓ ACCEPTABLE

### 3.5 Clinical Performance

[Checklist Items CLIN-001 and clinical performance synthesis]

The sponsor conducted a prospective clinical study to demonstrate accuracy:

**Study Design**:
- N = 50 adult patients with Type 2 diabetes
- 3 clinical sites
- 14-day wear period per sensor (2 sensors per subject = 28 days total per subject)
- YSI 2300 reference measurements every 15 minutes during 3 in-clinic sessions per subject
- Total paired points: 5,482

**Primary Endpoint**: ≥95% of CGM readings within ±15% of YSI reference for glucose ≥100 mg/dL 
or ±15 mg/dL for glucose <100 mg/dL

**Results**:
- Overall accuracy: 97.8% (CI: 96.2-99.1%) of readings within acceptance criteria
- MARD (Mean Absolute Relative Difference): 8.2%
- By glucose range:
  - <70 mg/dL: 96.1% within criteria
  - 70-180 mg/dL: 98.2% within criteria
  - >180 mg/dL: 97.4% within criteria
- No significant drift over 14-day wear (Day 1: 98.0%, Day 14: 97.5%)

**Safety**:
- 3 device-related adverse events:
  - 2 mild skin irritation (resolved with topical treatment)
  - 1 sensor insertion pain (resolved spontaneously)
- No serious adverse events

**Finding**: Clinical study demonstrates acceptable accuracy meeting the ±15% criteria with 
strong performance (97.8%). Study design, execution, and statistical analysis are adequate. 
Safety profile is acceptable. ✓ ACCEPTABLE

---

## 4. RISK MANAGEMENT

[Checklist Item RISK-001 expanded]

The sponsor provided a comprehensive risk management file per ISO 14971:2019 (Submission 
Section 6, 120 pages). The risk analysis process included:

1. **Hazard Identification**: Systematic evaluation identifying 23 potential hazards across 
   categories: mechanical, electrical, biological, software, use error, environmental

2. **Risk Estimation**: Each hazard evaluated for severity (negligible/minor/serious/critical) 
   and probability (rare/unlikely/possible/probable/frequent)

3. **Risk Evaluation**: Risks assessed against acceptance criteria (must be ≤Medium before 
   controls, ≤Low after controls)

4. **Risk Control**: Multiple risk controls implemented per hazard (design, protective measures, 
   information for safety)

5. **Residual Risk Evaluation**: All residual risks acceptable (Low or Negligible)

**Key Risks and Controls**:

| Hazard | Initial Risk | Risk Controls | Residual Risk |
|--------|--------------|---------------|---------------|
| Skin irritation from adhesive | Medium | ISO 10993 tested hypoallergenic adhesive; IFU warnings | Low ✓ |
| Inaccurate glucose readings | High | Factory calibration; accuracy testing; IFU limitation statements | Low ✓ |
| Sensor insertion injury | Low | Blunt-tip needle; insertion training; IFU instructions | Negligible ✓ |
| Data security breach | Medium | Encryption; authentication; secure communications | Low ✓ |
| Wireless interference | Medium | IEC 60601-1-2 testing; IFU warnings re: interference | Low ✓ |
| Sensor breakage/retention | Low | Material selection; tensile testing; IFU removal instructions | Negligible ✓ |

**Benefit-Risk Analysis**:
The sponsor provided a benefit-risk analysis concluding that the benefits (improved glucose 
monitoring, reduced fingersticks, trend awareness) outweigh the residual risks for the intended 
patient population. This reviewer concurs.

**Finding**: Risk management is comprehensive and acceptable. All risks have been identified, 
adequately controlled, and residual risks are acceptable. Benefit-risk balance is favorable. 
✓ ACCEPTABLE

---

## 5. LABELING

[Checklist Item LABEL-001 expanded]

The sponsor provided draft labeling including:
- Instructions for Use (IFU) - 35 pages
- Quick Start Guide
- On-screen app help text
- Packaging labels

**IFU Review**:

The IFU includes all required elements per 21 CFR 801:
- ✓ Device description and components
- ✓ Indications for use
- ✓ Contraindications (pregnancy not validated, age <18)
- ✓ Warnings (including hypoglycemia/hyperglycemia symptoms, confirmatory testing requirement)
- ✓ Precautions (MRI incompatibility, interference sources)
- ✓ Detailed insertion instructions with illustrations
- ✓ Sensor removal instructions
- ✓ App pairing and setup
- ✓ Troubleshooting guide
- ✓ Specifications
- ✓ Storage and handling
- ✓ Symbols glossary
- ✓ Customer service contact

**Key Warnings Adequacy**:
- "This device is intended to supplement, not replace, blood glucose information obtained 
  with a standard blood glucose meter. Always confirm glucose readings with a blood glucose 
  meter before making diabetes treatment decisions." - ADEQUATE ✓
- "Do not use the device during MRI, CT, or diathermy procedures." - ADEQUATE ✓
- "Inaccurate readings may occur in the presence of high-dose acetaminophen..." - ADEQUATE ✓

**Finding**: Labeling is comprehensive, clear, and adequate. All required warnings and 
precautions are present. ✓ ACCEPTABLE

---

## 6. OUTSTANDING ISSUES AND DEFICIENCIES

Based on this review, there are NO outstanding issues or deficiencies requiring additional 
information. All checklist items have been satisfactorily addressed.

- Device identification: Complete ✓
- Indications: Same as predicate ✓
- Technological comparison: Comprehensive, differences addressed ✓
- Bench testing: Complete and acceptable ✓
- Biocompatibility: Appropriate battery, all tests passed ✓
- Software: Adequate V&V for Level of Concern ✓
- Cybersecurity: Adequate controls ✓
- Clinical study: Demonstrates accuracy, adequate design ✓
- Risk management: Comprehensive per ISO 14971 ✓
- Labeling: Complete with appropriate warnings ✓

---

## 7. CONCLUSIONS AND RECOMMENDATIONS

### 7.1 Substantial Equivalence Determination

The Acme Continuous Glucose Monitor (K123456) is substantially equivalent to the predicate 
device (K987654, PredCGM System) based on the following:

**Same Intended Use**: Both devices are indicated for continuous glucose monitoring in adults 
with Type 2 diabetes.

**Similar Technological Characteristics**: The devices share the same fundamental glucose 
sensing technology (glucose oxidase electrochemical sensor) with similar design, materials, 
and performance specifications.

**Differences Do Not Raise New Questions**: The technological differences (Bluetooth 5.0, 
smartphone app, factory calibration, improved adhesive) have been adequately addressed through 
testing and do not raise new questions of safety or effectiveness. In fact, some differences 
(factory calibration, improved adhesive) may improve safety by reducing use errors and skin 
reactions.

**Performance Data Adequate**: Bench testing demonstrates the device meets all performance 
specifications. Clinical testing demonstrates acceptable accuracy (97.8% of readings within 
±15% criteria, MARD 8.2%). Risk management is comprehensive with all residual risks acceptable.

### 7.2 Recommendation

**SUBSTANTIAL EQUIVALENCE (SE) - CLEARANCE RECOMMENDED**

This device may be marketed subject to the general controls and special controls of 21 CFR 
862.1355.

### 7.3 Conditions of Clearance

**NONE**

No post-market studies or special conditions are required.

### 7.4 Post-Market Recommendations (Optional)

While not required as conditions of clearance, FDA may wish to monitor:
- Post-market adverse event reports related to adhesive reactions
- Software adverse events and cybersecurity incidents
- Real-world accuracy performance through post-market surveillance

---

**Reviewer**: ____________________________  **Date**: ______________
**Team Leader**: ____________________________  **Date**: ______________
**Division Director**: ____________________________  **Date**: ______________

---

## APPENDIX: CHECKLIST ITEM SUMMARY

| Item ID | Question | Response | Page |
|---------|----------|----------|------|
| ADMIN-001 | Device identification clear? | Yes ✓ | 8 |
| ADMIN-002 | Manufacturer info complete? | Yes ✓ | 8 |
| IND-001 | Indication statement clear? | Yes ✓ | 9 |
| IND-002 | Indication vs predicate? | Same ✓ | 9 |
| DESC-001 | Description adequate? | Yes ✓ | 10-11 |
| DESC-002 | Comparison table provided? | Yes ✓ | 11-12 |
| TEST-001 | Bench testing adequate? | Yes ✓ | 13-14 |
| TEST-002 | Biocompatibility appropriate? | Yes ✓ | 14-15 |
| RISK-001 | Risk analysis complete? | Yes ✓ | 16 |
| LABEL-001 | IFU adequate? | Yes ✓ | 17 |
| OVERALL-001 | SE determination? | SE - Clearance ✓ | 18 |

**Total Checklist Items**: 50
**Items Marked Acceptable**: 50
**Items Requiring Follow-Up**: 0
**Deficiencies**: 0

---

**Report Word Count**: 4,237 words
**Report Generation Date**: February 28, 2024
**Report Version**: Final v1.0
Report Generation Algorithm
pythonCopy1. Input Validation → Verify checklist + review results provided
2. Parse Checklist → Extract all items, IDs, sections
3. Parse Review Results → Extract responses, notes, findings
4. Match Items to Results → Link each checklist item to reviewer response
5. Aggregate by Section → Group related items into review sections
6. Narrative Generation → Convert Q&A into flowing paragraphs
7. Finding Synthesis → Create section findings from multiple items
8. Issue Identification → Flag any "No" responses or concerns
9. Cross-Reference → Link related findings across sections
10. Recommendation Formulation → Generate SE/Hold/NSE recommendation
11. Executive Summary → Create high-level summary
12. Formatting → Apply FDA memo structure
13. Quality Check → Verify completeness, word count 3000-5000
14. Export → Generate downloadable markdown/PDF
MANDATORY TRIGGERS
review report, FDA memo, review memorandum, 510k report, generate report, review documentation, formal report, clearance memo, SE determination, review summary, decision memo, regulatory report, assessment report, evaluation report, final report

Skill 8: AI Note Keeper with Intelligent Restructuring
ai-note-keeper-restructuring
Description
Smart note management system that transforms raw, unstructured reviewer notes (text fragments, bullet points, stream-of-consciousness) into well-organized, professional markdown documents with clear sections, complete sentences, highlighted key points, action items, and follow-up questions. Perfect for converting meeting notes, review session notes, and quick jottings into polished documentation.
Capabilities

Fragment-to-Sentence Conversion: Transform bullet fragments into complete, readable sentences
Intelligent Section Detection: Auto-identify major topics and create logical sections
Hierarchical Organization: Create multi-level heading structure (H1, H2, H3, H4)
Key Point Highlighting: Identify and emphasize critical findings or decisions
Action Item Extraction: Detect and format action items with checkboxes
Question Identification: Extract open questions and follow-up items
Chronological Ordering: Maintain or reorganize by logical flow
Duplicate Removal: Identify and consolidate redundant notes
Context Enhancement: Add clarifying text where notes are cryptic
Cross-Reference Creation: Link related note sections
Metadata Addition: Add timestamps, note source, version info
Multilingual Support: Process English and Traditional Chinese notes

Input Note Types Supported

Meeting notes (stakeholder meetings, team huddles, teleconferences)
Review session notes (510(k) document review, protocol review)
Phone call notes (sponsor calls, FDA internal discussions)
Stream-of-consciousness brainstorming
Bullet-point quick captures
Handwritten note transcriptions (post-OCR)
Voice-to-text transcriptions
Email thread summaries

Restructuring Examples
Input (Raw Notes):
Copydevice - cgm, acme medical
k number? need to find
indication T2DM adults only
similar to predicate (pred123)

risks:
- skin irritation
- inaccurate readings
- wireless issues maybe?

testing:
bench - done, looks ok
bio - iso 10993, reports in section 8
clinical - 50 pts, 98% accuracy (good!)

Q: calibration needed? A: factory calib, no user calib (improvement!)

labeling - check warnings, MRI incompatibility

TODO:
[ ] review software section (big, 500 pgs)
[ ] verify wireless testing per 60601-1-2
[ ] check predicate comparison table completeness

Follow up with sponsor re: pediatric use? not in indication but might ask

DECISION: looks like SE, pending software review
Output (Restructured Markdown):
markdownCopy# 510(k) Review Session Notes: Acme CGM
**Date**: February 15, 2024
**Reviewer**: [Name]
**510(k) Number**: [To be confirmed]
**Device**: Acme Continuous Glucose Monitor

---

## 1. Device Overview

The subject device is a continuous glucose monitor (CGM) manufactured by Acme Medical. 
The 510(k) number needs to be confirmed and documented. The device is indicated for 
continuous glucose monitoring in **adults with Type 2 diabetes only** (pediatric use not included).

**Predicate Device**: The device is being compared to predicate K-pred123. The devices appear 
to have similar technological characteristics.

---

## 2. Risk Management Observations

The sponsor has identified several key risks in the risk management file:

- **Skin Irritation**: Risk of contact dermatitis or allergic reaction from the adhesive. 
  Mitigations and biocompatibility testing need to be verified.
  
- **Inaccurate Glucose Readings**: Risk of incorrect glucose values leading to improper 
  treatment decisions. Performance testing and labeling warnings are critical.
  
- **Wireless Communication Issues**: Potential for signal interference or dropout. Need to 
  verify IEC 60601-1-2 testing (see action items below).

---

## 3. Performance Testing Summary

### 3.1 Bench Testing
Bench testing appears to have been completed and the results look acceptable. Further detailed 
review of test protocols and acceptance criteria is needed.

### 3.2 Biocompatibility Testing
Biocompatibility testing was conducted per ISO 10993-1. Test reports are located in Section 8 
of the submission. Need to verify the appropriate test battery was selected based on contact 
type and duration.

### 3.3 Clinical Performance
A clinical study was conducted with 50 patients. **Excellent accuracy performance**: 98% of 
readings met the acceptance criteria. This is well above the typical ≥95% threshold and 
supports substantial equivalence.

---

## 4. Key Design Feature: Factory Calibration

**Important finding**: Unlike the predicate device, the subject device uses **factory 
calibration** and does NOT require user calibration. This is a design **improvement** that:
- Reduces potential for use error
- Eliminates calibration-related inaccuracies
- Simplifies user experience

This difference should be highlighted as a benefit in the review and does not raise safety 
concerns.

---

## 5. Labeling Review

Labeling needs to be reviewed with particular attention to:
- ✓ Adequate warnings about MRI incompatibility (device must be removed during MRI procedures)
- ✓ Warnings about the need for confirmatory blood glucose testing
- ✓ Interference warnings for wireless communication

---

## 6. Outstanding Items and Action Items

### 6.1 Action Items (Priority Review Needed)

- [ ] **HIGH PRIORITY**: Review software documentation section (noted as ~500 pages). 
      Verify software V&V is adequate for the Level of Concern. Check for FDA software 
      guidance compliance.
      
- [ ] Verify wireless testing per IEC 60601-1-2:2014 was completed. Review test reports 
      for electromagnetic compatibility and wireless coexistence.
      
- [ ] Check predicate comparison table for completeness. Ensure all technological 
      characteristics are addressed and all differences are explained.

### 6.2 Follow-Up Questions

**Question for Sponsor**: Has the device been tested for pediatric use, or is there potential 
for future pediatric indication expansion? 

*Rationale*: The current indication is adults only, but pediatric diabetes management is an 
important clinical need. If pediatric use is contemplated in the future, it may be worth 
discussing now to avoid significant additional testing later.

---

## 7. Preliminary Assessment

Based on the review to date, the device appears to demonstrate **substantial equivalence (SE)** 
to the predicate device:
- Same intended use (CGM for Type 2 diabetes)
- Similar technological characteristics (electrochemical glucose sensing)
- Differences (factory calibration, wireless communication) do not raise new safety questions
- Strong clinical performance (98% accuracy)

**Pending Items**: Final SE determination is contingent on acceptable software review (see 
action item above). If software V&V is adequate, recommend clearance.

---

## 8. Next Steps

1. Complete detailed software section review
2. Verify wireless and biocompatibility testing adequacy
3. Confirm predicate comparison completeness
4. Consider sending question to sponsor re: pediatric use plans
5. Prepare draft review memo if software review is satisfactory

---

**Notes Version**: Draft v1.0
**Status**: Under Review
**Target Completion**: February 28, 2024
Restructuring Features
Sentence Completion:

"device - cgm, acme medical" → "The subject device is a continuous glucose monitor (CGM)
manufactured by Acme Medical."

Section Organization:

Groups related fragments (all risk items together, all testing items together)
Creates logical section hierarchy

Action Item Formatting:

Converts informal TODOs into formal action items with checkboxes
Adds priority levels and rationale

Key Point Emphasis:

"98% accuracy (good!)" → "Excellent accuracy performance: 98%..."
Highlights important findings with bold text

Question Clarification:

"Follow up with sponsor re: pediatric use?" → Formatted as "Follow-Up Questions" section
with full question and rationale

Context Addition:

"calibration needed? A: factory calib" → Expanded into full paragraph explaining the
significance of factory calibration as a design improvement

Use Cases

Convert real-time review session notes into professional documentation
Transform voice-to-text meeting transcriptions into organized minutes
Restructure brainstorming sessions into actionable plans
Consolidate daily review notes into weekly summaries
Prepare informal notes for sharing with team or management
Create audit trails from quick review jottings

Processing Algorithm
pythonCopy1. Note Ingestion → Parse raw text input
2. Fragment Detection → Identify incomplete sentences
3. Sentence Completion → Convert fragments to sentences using AI
4. Topic Clustering → Group related notes by topic
5. Section Identification → Determine major sections
6. Hierarchy Creation → Assign heading levels (H1-H4)
7. Action Item Extraction → Identify TODO, follow-up, check items
8. Question Detection → Find interrogatives and open items
9. Key Point Identification → Detect important findings (!, **, DECISION)
10. Duplicate Consolidation → Merge redundant notes
11. Cross-Reference Linking → Connect related sections
12. Context Enhancement → Add clarifying text where needed
13. Metadata Addition → Add date, version, status
14. Formatting Application → Apply markdown structure
15. Quality Check → Verify readability and completeness
MANDATORY TRIGGERS
note keeper, organize notes, restructure notes, note taking, meeting notes, review notes, note organization, clean up notes, format notes, note management, smart notes, AI notes, note assistant, improve notes, note transformation

Skill 9: AI Magic Tools Suite - Five Regulatory Document Enhancement Tools
ai-magic-tools-suite
Description
Comprehensive suite of five specialized AI "Magic" tools designed to enhance regulatory documents and notes with specific transformations: formatting beautification, keyword highlighting with custom colors, action item extraction, concept map generation, and glossary creation. Each Magic tool applies targeted AI processing to add value and structure to existing content.
Magic Tool Overview
| Magic Name | Function | Primary Output |
|----------
