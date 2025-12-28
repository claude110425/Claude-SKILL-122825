# USER GUIDE: FDA 510(k) Agentic Reviewer
## Complete Beginner's Instructions for All Platforms

---

# Table of Contents

1. [Platform Setup Instructions](#platform-setup-instructions)
   - Claude Console (Web)
   - ChatGPT
   - Google AI Studio (Gemini)
   - Perplexity
   - Grok (X.AI)

2. [Five Detailed Step-by-Step Examples](#five-detailed-examples)
   - Example 1: Generate Complete 510(k) Review Report
   - Example 2: Compare Two Document Versions
   - Example 3: Extract Action Items & Create Task List
   - Example 4: Convert FDA Guidance to Review Checklist
   - Example 5: Enhance Messy Notes with All Magic Tools

3. [Troubleshooting Guide](#troubleshooting-guide)

4. [Tips for Best Results](#tips-for-best-results)

---

# Platform Setup Instructions

## 1. Claude Console (Web) - claude.ai

### Initial Setup

**Step 1: Access Claude**
1. Open your web browser
2. Go to: https://claude.ai
3. Sign in with your account (Google, email, etc.)
4. You'll see the main chat interface

**Step 2: Create a New Project (Recommended)**
1. Click "Projects" in the left sidebar
2. Click "+ New Project"
3. Name it: "FDA 510k Reviewer"
4. Click "Create Project"

**Step 3: Upload the SKILL.md File**
1. Inside your project, click "Add Content"
2. Click "Upload files"
3. Select the `SKILL.md` file from your computer
4. Wait for upload to complete (green checkmark)
5. The file will appear in "Project Knowledge"

**Step 4: Start a New Conversation**
1. Click "Start new chat" (or press Ctrl+N / Cmd+N)
2. You're now ready to use the skills!

### Visual Guide for Claude:
```
┌─────────────────────────────────────────────────────────────┐
│  Claude.ai Interface                                        │
├─────────────────────────────────────────────────────────────┤
│                                                             │
│  [≡] Projects                    [+ New Chat]               │
│   └─ FDA 510k Reviewer ←────────────────────────────────┐  │
│      └─ Project Knowledge                                │  │
│         └─ 📄 SKILL.md (uploaded) ←──────────────────────┤  │
│                                                          │  │
│  ┌───────────────────────────────────────────────────┐  │  │
│  │ Chat Area                                         │  │  │
│  │                                                   │  │  │
│  │ Your prompts and Claude's responses appear here  │  │  │
│  │                                                   │  │  │
│  └───────────────────────────────────────────────────┘  │  │
│                                                          │  │
│  [Type your message here...               ] [Send ↑]    │  │
│                                                          │  │
└──────────────────────────────────────────────────────────┘  │
```

---

## 2. ChatGPT (OpenAI) - chat.openai.com

### Initial Setup

**Step 1: Access ChatGPT**
1. Go to: https://chat.openai.com
2. Sign in with your OpenAI account
3. You'll see the main chat interface

**Step 2: Create a Custom GPT (Optional but Recommended)**
1. Click your profile icon (bottom left)
2. Select "My GPTs"
3. Click "Create a GPT"
4. In "Configure" tab:
   - Name: "FDA 510(k) Reviewer"
   - Description: "Expert regulatory reviewer for medical devices"
5. In "Instructions" box, paste the **entire SKILL.md content**
6. Under "Knowledge", upload any reference documents
7. Click "Save" → "Only me" (or share as needed)

**Step 3: Alternative - Use in Regular Chat**
If you don't create a custom GPT:
1. Start a new chat
2. Click the 📎 (paperclip) icon
3. Upload the `SKILL.md` file
4. Type: "I've uploaded your instruction manual. Please acknowledge that you understand all 11 skills."

### Visual Guide for ChatGPT:
```
┌─────────────────────────────────────────────────────────────┐
│  ChatGPT Interface                                          │
├─────────────────────────────────────────────────────────────┤
│                                                             │
│  [☰] Menu                        [+ New Chat]              │
│   └─ My GPTs                                               │
│      └─ FDA 510k Reviewer ←─────────────────────────────┐  │
│                                                          │  │
│  ┌───────────────────────────────────────────────────┐  │  │
│  │ 💬 Chat Area                                      │  │  │
│  │                                                   │  │  │
│  │ Your messages and GPT responses                  │  │  │
│  │                                                   │  │  │
│  └───────────────────────────────────────────────────┘  │  │
│                                                          │  │
│  [📎 Attach] [Type message...              ] [Send ➤]   │  │
│                                                          │  │
└──────────────────────────────────────────────────────────┘  │
```

---

## 3. Google AI Studio (Gemini) - aistudio.google.com

### Initial Setup

**Step 1: Access Google AI Studio**
1. Go to: https://aistudio.google.com
2. Sign in with your Google account
3. Accept terms if first time

**Step 2: Create a New Prompt**
1. Click "Create new prompt"
2. Select "Freeform prompt"

**Step 3: Set Up System Instructions**
1. In the top area, you'll see "System instructions" section
2. Click to expand it
3. Paste the **System Prompt Section** from SKILL.md
   - Copy the "system_prompt" content from any agent in SKILL.md
   - Example: Copy the intelligence_analyst system prompt

**Step 4: Upload Reference Materials**
1. On the right side, find "Attach files" option
2. Click and upload your documents
3. Or paste text directly into the chat

### Visual Guide for Google AI Studio:
```
┌─────────────────────────────────────────────────────────────┐
│  Google AI Studio                                           │
├─────────────────────────────────────────────────────────────┤
│                                                             │
│  Model: Gemini 2.0 Flash ▼        [+ New prompt]          │
│                                                             │
│  ┌─────────────────────────────────────────────────────┐  │
│  │ System instructions (Optional)                       │  │
│  │ Paste system prompt from SKILL.md here ↓           │  │
│  │ [                                                  ] │  │
│  └─────────────────────────────────────────────────────┘  │
│                                                             │
│  ┌─────────────────────────────────────────────────────┐  │
│  │ User prompt                                          │  │
│  │ Type your request here                              │  │
│  │ [                                                  ] │  │
│  └─────────────────────────────────────────────────────┘  │
│                                                             │
│  [📎 Attach files]                    [Run ▶]             │
│                                                             │
└─────────────────────────────────────────────────────────────┘
```

---

## 4. Perplexity - perplexity.ai

### Initial Setup

**Step 1: Access Perplexity**
1. Go to: https://www.perplexity.ai
2. Sign in (optional, but recommended for history)

**Step 2: Set Context**
Since Perplexity doesn't have persistent file upload:
1. Start your prompt with context-setting
2. Include relevant excerpts from SKILL.md in your prompt

**Example Prompt Structure:**
```
Context: I'm using an FDA 510(k) review system with 11 specialized skills:
1. Multi-model LLM integration
2. 510(k) report generation
[... list relevant skills ...]

Task: [Your specific request]

Instructions: [Copy relevant instructions from SKILL.md]

Content: [Paste your document or information]
```

---

## 5. Grok (X.AI) - x.com

### Initial Setup

**Step 1: Access Grok**
1. Go to: https://x.com (Twitter/X)
2. Sign in to your X account
3. Look for Grok icon (usually bottom right or in sidebar)
4. Click to open Grok chat

**Step 2: Set Up Context**
1. Start a new conversation
2. Paste system instructions from SKILL.md
3. Give specific task instructions

**Note:** Grok is integrated with X (Twitter), so it may have access to real-time information. Be mindful of data privacy.

---

# Five Detailed Examples

---

## Example 1: Generate Complete 510(k) Review Report

### Scenario
You have basic information about a new continuous glucose monitor (CGM) and need to generate a comprehensive 510(k) review report with tables, analysis, and recommendations.

---

### Platform: Claude Console

#### Step-by-Step Instructions

**Step 1: Prepare Your Input Information**

Create a text document with this information:
```
Device Name: AcuGluco Pro CGM
Manufacturer: MedTech Innovations Inc.
510(k) Number: K242567
Product Code: NBW
Classification: Class II

Device Description:
The AcuGluco Pro is a continuous glucose monitoring system for adults 
with Type 2 diabetes. The system consists of:
- A disposable sensor (14-day wear time)
- A reusable transmitter (Bluetooth 5.0)
- A smartphone application (iOS and Android)

Key Features:
- Factory calibrated (no fingerstick calibration needed)
- Real-time glucose readings every 5 minutes
- Customizable high/low glucose alerts
- Trend arrows and graphs
- Data sharing with healthcare providers

Predicate Device: FreeStyle Libre 2 (K193899)

Indications for Use:
The AcuGluco Pro CGM is indicated for continuous glucose monitoring 
in adults aged 18 years and older with diabetes mellitus. The system 
is intended to replace fingerstick blood glucose testing for diabetes 
treatment decisions.

Testing Summary:
- Bench testing: Accuracy, precision, interference studies
- Biocompatibility: ISO 10993-1 testing for prolonged skin contact
- Clinical study: 120 subjects, accuracy within ±15% of YSI reference
- Electrical safety: IEC 60601-1 compliance
- EMC testing: IEC 60601-1-2 for wireless devices
- Software verification & validation: Level of Concern - Moderate
```

**Step 2: Open Claude and Start Your Request**

In Claude console, type this exact prompt:

```
I need to use Skill 2: Intelligent 510(k) Report Generator.

Please generate a comprehensive FDA 510(k) review intelligence report 
for the following device. The report must include:
- Minimum 5 comprehensive markdown tables
- 3000-4000 word detailed analysis
- All standard FDA review sections
- Substantial equivalence assessment

Device Information:

[Paste your device information from Step 1 here]

Please proceed with generating the complete report following FDA review 
memo format.
```

**Step 3: Send and Wait for Response**

1. Click "Send" or press Enter
2. Claude will process for 30-60 seconds
3. You'll see a comprehensive report being generated in real-time

**Step 4: Review the Output**

You should receive a report with these sections:

✅ **1. Executive Summary**
- Key findings
- Recommendation (SE/NSE)
- Critical issues (if any)

✅ **2. Device Overview Table**
```markdown
| Attribute | Details |
|-----------|---------|
| Device Name | AcuGluco Pro CGM |
| Manufacturer | MedTech Innovations Inc. |
| ... | ... |
```

✅ **3. Indications for Use Table**
✅ **4. Technological Characteristics Comparison Table**
✅ **5. Performance Testing Summary Table**
✅ **6. Risk Management Matrix Table**
✅ **7-10. Detailed narrative sections**

**Step 5: Export and Use the Report**

To save the report:

**Method A: Copy All**
1. Click the "Copy" button that appears at the top of Claude's response
2. Paste into Microsoft Word or Google Docs
3. Save as .docx or .pdf

**Method B: Download as Markdown**
1. Copy the entire response
2. Paste into a text editor (Notepad, VS Code, etc.)
3. Save with `.md` extension (e.g., "K242567_Review_Report.md")
4. Use a markdown viewer or converter

**Method C: Claude's Built-in Export**
1. Click the three dots (⋯) at the top right of the response
2. Select "Copy as Markdown"
3. Paste into your preferred document

---

### Expected Output Preview

```markdown
# FDA 510(k) REVIEW MEMORANDUM

## Administrative Information

| Field | Details |
|-------|---------|
| 510(k) Number | K242567 |
| Received Date | [Insert Date] |
| Device Trade Name | AcuGluco Pro CGM |
| Manufacturer | MedTech Innovations Inc. |
| Review Division | Division of Chemistry and Toxicology Devices |
| Product Code | NBW |
| Regulation Number | 21 CFR 862.1355 |
| Classification | Class II |
| Review Type | Traditional 510(k) |
| Reviewer | [Insert Name] |
| Lead Reviewer | [Insert Name] |

---

## EXECUTIVE SUMMARY

The AcuGluco Pro Continuous Glucose Monitor (CGM) is a Class II medical 
device submitted under 510(k) number K242567 by MedTech Innovations Inc. 
The device is indicated for continuous monitoring of interstitial glucose 
levels in adults aged 18 years and older with diabetes mellitus...

[3,000+ words continue...]

---

## Device Overview

| Attribute | Subject Device | Predicate Device |
|-----------|----------------|------------------|
| Trade Name | AcuGluco Pro CGM | FreeStyle Libre 2 |
| Manufacturer | MedTech Innovations | Abbott Diabetes Care |
| 510(k) Number | K242567 | K193899 |
| Product Code | NBW | NBW |
...

[Report continues with all sections and tables...]
```

---

### Common Issues and Solutions

**Issue 1: Report is too short (less than 3000 words)**

**Solution:**
```
The report you generated is only [X] words. Please expand it to meet 
the minimum 3000-word requirement. Add more detail to these sections:
- Performance Testing (expand each test type)
- Risk Management (detail each risk and mitigation)
- Technological Characteristics (expand comparison)
- Clinical Study (add more statistical details)
```

**Issue 2: Missing tables**

**Solution:**
```
The report is missing some required tables. Please add:
- [Specific table name, e.g., "Risk Management Matrix"]

Use this format:
| Risk | Severity | Probability | Mitigation | Residual Risk |
|------|----------|-------------|------------|---------------|
```

**Issue 3: Want to regenerate with different focus**

**Solution:**
```
Please regenerate the report with additional emphasis on:
- Software verification and validation (expand this section significantly)
- Clinical study statistical analysis
- Cybersecurity considerations

Keep all other sections, but enhance these areas.
```

---

### Verification Checklist

After receiving your report, verify:

- [ ] Report is 3,000-4,000 words *(Use word counter in Word/Docs)*
- [ ] Contains minimum 5 comprehensive tables
- [ ] Includes Executive Summary
- [ ] Includes Device Overview section with table
- [ ] Includes Indications for Use comparison
- [ ] Includes Technological Characteristics comparison table
- [ ] Includes Performance Testing summary table
- [ ] Includes Risk Management matrix
- [ ] Includes Standards Compliance section
- [ ] Includes Labeling Review section
- [ ] Includes Clear Recommendation (SE or NSE)
- [ ] Uses proper FDA regulatory language
- [ ] References appropriate CFR regulations
- [ ] Markdown formatting is correct (headings, tables, bullets)

---

## Example 2: Compare Two Document Versions (Find 100+ Differences)

### Scenario
The sponsor submitted a revised version of their 510(k) submission after receiving an Additional Information (AI) request. You need to identify all changes between Version 1 and Version 2 to assess if the sponsor adequately addressed FDA's questions.

---

### Platform: ChatGPT

#### Step-by-Step Instructions

**Step 1: Prepare Your Two Document Versions**

**Version 1 (Original Submission) - Save as text:**
```
INDICATIONS FOR USE

The AcuGluco Pro CGM is indicated for continuous glucose monitoring 
in adults with diabetes mellitus.

DEVICE DESCRIPTION

The AcuGluco Pro consists of a sensor, transmitter, and mobile app.

Sensor specifications:
- Wear time: 10 days
- Measurement range: 40-400 mg/dL
- Warm-up time: 60 minutes

PERFORMANCE TESTING

Bench Testing:
Accuracy testing was performed using YSI reference analyzer.
Results showed accuracy within ±15 mg/dL.

Clinical Study:
A clinical study with 80 subjects was conducted.
Results demonstrated acceptable accuracy.

RISK MANAGEMENT

Risks were identified and mitigated per ISO 14971.

Major risks include:
- Skin irritation
- Inaccurate readings

Mitigations include biocompatibility testing and calibration.
```

**Version 2 (Revised After AI Request) - Save as text:**
```
INDICATIONS FOR USE

The AcuGluco Pro CGM is indicated for continuous glucose monitoring 
in adults aged 18 years and older with diabetes mellitus. The device 
is intended to replace fingerstick blood glucose testing for diabetes 
treatment decisions.

DEVICE DESCRIPTION

The AcuGluco Pro Continuous Glucose Monitoring System consists of 
three components:
1. Disposable Sensor
2. Reusable Transmitter
3. Mobile Application (iOS and Android)

Sensor specifications:
- Wear time: 14 days
- Measurement range: 40-400 mg/dL
- Accuracy: ±15% or ±15 mg/dL
- Warm-up time: 60 minutes
- Sensor size: 5mm diameter x 35mm length
- Insertion depth: 5mm subcutaneous
- Sample type: Interstitial fluid
- Detection method: Electrochemical (glucose oxidase)

Transmitter specifications:
- Wireless: Bluetooth 5.0
- Range: 20 feet
- Battery: Rechargeable lithium-ion, 90-day life
- Water resistance: IP68 (submersible 3 feet, 30 minutes)
- Dimensions: 25mm x 25mm x 10mm
- Weight: 5 grams

PERFORMANCE TESTING

Bench Testing:
Accuracy testing was performed using the YSI 2300 STAT Plus Glucose 
Analyzer as the reference method per ISO 15197:2013 Section 6.3. 
A total of 200 sensors were tested across the claimed measurement range.

Results:
- Overall accuracy: 98.5% of readings within ±15% or ±15 mg/dL
- Glucose <100 mg/dL: 99.2% within ±15 mg/dL
- Glucose ≥100 mg/dL: 98.1% within ±15%
- MARD (Mean Absolute Relative Difference): 8.7%

Additional bench testing included:
- Precision testing: CV <5% across range
- Linearity: R² = 0.995
- Interference testing: No clinically significant interference from 
  acetaminophen (up to 20 mg/dL), ascorbic acid, salicylic acid
- Temperature stability: Performance maintained 15-40°C
- Electromagnetic interference: Per IEC 60601-1-2:2014

Clinical Study:
A prospective, single-arm clinical study was conducted at 4 U.S. sites 
with 120 adult subjects (age 18-75 years) with Type 1 or Type 2 diabetes.

Study Design:
- Duration: 14 days per subject
- YSI reference measurements: Every 15 minutes during in-clinic sessions
- Total paired points analyzed: 14,850

Results:
- Primary endpoint: 98.3% of CGM readings within ±15% or ±15 mg/dL 
  of YSI reference (met acceptance criterion of ≥95%)
- MARD: 8.5%
- Clinical accuracy per ISO 15197:2013 Clarke Error Grid:
  * Zone A (clinically accurate): 96.8%
  * Zone B (clinically acceptable): 3.1%
  * Zones C, D, E: 0.1%

No serious adverse events related to device use were reported.

Biocompatibility Testing:
Performed per ISO 10993-1:2018 for prolonged contact (>24h, ≤30 days) 
with intact skin.

Tests conducted:
- Cytotoxicity (ISO 10993-5): Pass
- Sensitization (ISO 10993-10, GPMT): Pass
- Irritation (ISO 10993-10, Primary Skin Irritation): Pass
- Systemic toxicity (ISO 10993-11): Pass
- Material-mediated pyrogenicity (ISO 10993-11): Pass

All tests were conducted at ISO 17025 accredited laboratories.
Test reports provided in Section 8 of submission.

RISK MANAGEMENT

Risk analysis was performed per ISO 14971:2019. A comprehensive 
Failure Modes and Effects Analysis (FMEA) was conducted.

Risk Management File includes:
- Hazard identification worksheets
- Risk estimation matrices
- Risk evaluation
- Risk control measures
- Residual risk evaluation
- Risk/benefit analysis
- Production and post-production information plan

Major risks identified and controlled:

1. Risk: Skin irritation or allergic reaction from adhesive or sensor
   - Pre-mitigation risk: Medium (Severity: Moderate, Probability: Occasional)
   - Mitigation: 
     * Medical-grade hypoallergenic acrylic adhesive
     * Biocompatibility testing per ISO 10993-10
     * Clear instructions on site rotation and skin preparation
     * Warnings in labeling for known adhesive sensitivities
   - Residual risk: Low (Severity: Minor, Probability: Remote)

2. Risk: Inaccurate glucose readings leading to incorrect treatment
   - Pre-mitigation risk: High (Severity: Critical, Probability: Occasional)
   - Mitigation:
     * Factory calibration (no user calibration required)
     * Extensive accuracy testing (bench + clinical)
     * Real-time quality checks in sensor algorithm
     * Labeling includes warnings to confirm with fingerstick before treatment
     * Alert fatigue mitigation through smart notification algorithms
   - Residual risk: Low (Severity: Moderate, Probability: Remote)

3. Risk: Wireless interference affecting device operation
   - Pre-mitigation risk: Medium
   - Mitigation:
     * IEC 60601-1-2:2014 EMC testing (immunity and emissions)
     * Wireless coexistence testing
     * Labeling warnings about potential interference sources
   - Residual risk: Low

4. Risk: Data security breach or unauthorized access
   - Pre-mitigation risk: Medium
   - Mitigation:
     * AES-256 encryption for data transmission
     * User authentication (PIN or biometric)
     * Secure cloud storage (HIPAA compliant)
     * Cybersecurity risk assessment per FDA 2014 guidance
   - Residual risk: Low

All residual risks are acceptable per benefit-risk analysis documented 
in Risk Management File Section 12.
```

---

**Step 2: Access ChatGPT**

1. Go to chat.openai.com
2. Start a new chat
3. If you created a custom GPT, select "FDA 510(k) Reviewer"

---

**Step 3: Upload or Paste Documents**

Type this prompt:

```
I need to use Skill 3: Dual-Version Document Comparator.

I have two versions of a 510(k) submission and need you to identify 
a MINIMUM of 100 meaningful differences between them.

Please create a comprehensive comparison table with these columns:
- ID (001, 002, ...)
- Title (brief description)
- Change Type (Addition/Deletion/Modification/Relocation)
- Before (Version 1 text)
- After (Version 2 text)
- Regulatory Significance (HIGH/MEDIUM/LOW)
- Review Impact (how this affects the review)

After the table, provide:
1. Summary statistics (total differences, breakdown by type)
2. List of HIGH significance changes requiring reviewer attention
3. Assessment of whether AI request was adequately addressed

Here are the two versions:

===== VERSION 1 (ORIGINAL) =====
[Paste Version 1 text here]

===== VERSION 2 (REVISED) =====
[Paste Version 2 text here]

Please proceed with comprehensive comparison.
```

---

**Step 4: Review the Output**

You'll receive a detailed comparison table like this:

```markdown
# Document Comparison Report
**Comparison Date**: February 28, 2024
**Version 1**: Original 510(k) Submission
**Version 2**: Revised Submission (Post-AI)
**Total Differences Identified**: 127

---

## Comprehensive Difference Table

| ID | Title | Change Type | Before (V1) | After (V2) | Regulatory Significance | Review Impact |
|----|-------|-------------|-------------|------------|------------------------|---------------|
| 001 | Age specification added to indications | **Modification** | "adults with diabetes mellitus" | "adults aged 18 years and older with diabetes mellitus" | 🔴 **HIGH** | Clarifies patient population, critical for safety assessment |
| 002 | Treatment decision claim added | **Addition** | [Not present] | "The device is intended to replace fingerstick blood glucose testing for diabetes treatment decisions" | 🔴 **HIGH** | Major expansion of intended use, requires robust clinical data |
| 003 | Component list detailed | **Modification** | "sensor, transmitter, and mobile app" | "1. Disposable Sensor\n2. Reusable Transmitter\n3. Mobile Application (iOS and Android)" | 🟡 **MEDIUM** | Improved clarity, better technical description |
| 004 | Sensor wear time increased | **Modification** | "10 days" | "14 days" | 🔴 **HIGH** | Extended wear time affects biocompatibility requirements and shelf-life validation |
| 005 | Accuracy specification added | **Addition** | [Not present] | "Accuracy: ±15% or ±15 mg/dL" | 🔴 **HIGH** | Critical performance specification, essential for SE determination |
| 006 | Sensor dimensions added | **Addition** | [Not specified] | "5mm diameter x 35mm length" | 🟢 **LOW** | Administrative detail, helpful for completeness |
| 007 | Insertion depth specified | **Addition** | [Not specified] | "Insertion depth: 5mm subcutaneous" | 🟡 **MEDIUM** | Important safety information, affects risk assessment |
| 008 | Sample type clarified | **Addition** | [Not specified] | "Sample type: Interstitial fluid" | 🟡 **MEDIUM** | Important technical detail distinguishing CGM from blood glucose meters |
| 009 | Detection method specified | **Addition** | [Not specified] | "Detection method: Electrochemical (glucose oxidase)" | 🟡 **MEDIUM** | Technical detail important for predicate comparison |
| 010 | Transmitter wireless spec added | **Addition** | [Not specified] | "Wireless: Bluetooth 5.0" | 🟡 **MEDIUM** | Relevant for EMC testing requirements |

[... continues for 127 differences ...]

---

## Summary Statistics

**Total Differences**: 127

**By Change Type**:
- **Additions**: 87 (68.5%)
- **Modifications**: 32 (25.2%)
- **Deletions**: 3 (2.4%)
- **Relocations**: 5 (3.9%)

**By Regulatory Significance**:
- 🔴 **HIGH**: 38 differences (29.9%)
- 🟡 **MEDIUM**: 54 differences (42.5%)
- 🟢 **LOW**: 35 differences (27.6%)

**By Document Section**:
- Indications for Use: 8 changes (6 HIGH, 2 MEDIUM)
- Device Description: 31 changes (12 HIGH, 15 MEDIUM, 4 LOW)
- Performance Testing: 45 changes (15 HIGH, 25 MEDIUM, 5 LOW)
- Risk Management: 28 changes (5 HIGH, 18 MEDIUM, 5 LOW)
- Biocompatibility: 15 changes (0 HIGH, 10 MEDIUM, 5 LOW)

---

## HIGH Significance Changes Requiring Reviewer Attention

### 1. Indications for Use Expansion (IDs: 001, 002)
**Critical Finding**: The revised submission significantly expands the indications:
- **Added**: Age specification (18 years and older)
- **Added**: Claim to "replace fingerstick blood glucose testing for diabetes treatment decisions"

**Reviewer Action Required**:
✅ Verify clinical study included subjects aged 18+ only
✅ Assess if clinical data supports non-adjunctive claim (replacement claim)
✅ Compare to predicate's indications - if predicate is adjunctive only, this may constitute NSE

**AI Request Status**: ⚠️ This was likely the subject of the AI request. Appears adequately addressed with clinical data expansion.

---

### 2. Sensor Wear Time Extension (ID: 004)
**Critical Finding**: Wear time increased from 10 to 14 days

**Reviewer Action Required**:
✅ Verify biocompatibility testing appropriate for 14-day prolonged contact
✅ Review shelf-life/stability testing for 14-day claim
✅ Assess clinical study duration (must include 14-day wear data)

**AI Request Status**: ✅ Likely addressed - biocompatibility testing section significantly expanded with 14-day contact testing

---

[Additional HIGH significance changes detailed...]

---

## Assessment: AI Request Response Adequacy

**Overall Assessment**: ✅ **AI REQUEST APPEARS ADEQUATELY ADDRESSED**

**Evidence**:
1. ✅ **Performance Testing**: Dramatically expanded from vague "acceptable accuracy" to detailed:
   - Specific test methods (YSI 2300, ISO 15197:2013)
   - Quantitative results (98.5% accuracy, MARD 8.7%)
   - Sample sizes (200 sensors bench tested, 120 subjects clinical study)
   
2. ✅ **Clinical Study**: Added comprehensive study design and results:
   - Study sites, subject count, duration
   - Statistical analysis (14,850 paired points)
   - Primary endpoint met (98.3% within ±15% acceptance)
   - Safety outcomes (no serious AEs)
   
3. ✅ **Risk Management**: Transformed from superficial to comprehensive:
   - Detailed FMEA per ISO 14971:2019
   - Four major risks with pre/post-mitigation severity
   - Specific mitigations and residual risk assessments
   - Risk Management File structure documented

4. ✅ **Biocompatibility**: Changed from "testing was done" to:
   - Specific ISO 10993 parts tested
   - Test results (all Pass)
   - ISO 17025 accredited lab confirmation
   - Section reference for test reports

5. ✅ **Technical Specifications**: All previously missing specs now provided:
   - Sensor dimensions, insertion depth, sample type
   - Transmitter wireless specs (Bluetooth 5.0)
   - Battery specifications
   - Water resistance rating

**Deficiencies Resolved**: Estimated 8-12 original deficiencies
**New Questions Raised**: 2-3 minor questions (see below)

**Remaining Minor Questions**:
1. ⚠️ Software V&V documentation - still not detailed in submission text (may be in separate section)
2. ⚠️ Labeling - no labeling excerpts or IFU discussion in provided text
3. ⚠️ Predicate comparison table - not included in excerpts

**Recommendation**: 
- ✅ Sponsor has substantially addressed AI request deficiencies
- ⏸️ Verify above remaining items before final SE determination
- 🟢 **Proceed with detailed technical review** - AI response appears adequate

---

## Reviewer Checklist for Follow-Up

- [ ] Verify clinical study report matches summary (detailed stats, subject demographics)
- [ ] Review actual Risk Management File for completeness
- [ ] Confirm biocompatibility test reports in Section 8
- [ ] Check predicate comparison table completeness
- [ ] Review labeling (IFU) for adequate warnings on treatment decisions
- [ ] Verify software documentation (Level of Concern: Moderate requires V&V)
- [ ] Assess if non-adjunctive claim is supported vs. predicate's adjunctive claim

---

**End of Comparison Report**
```

---

**Step 5: Extract Key Insights for Review Memo**

From the comparison, you can quickly:

1. **Identify what changed** (127 differences documented)
2. **Prioritize review focus** (38 HIGH significance items)
3. **Assess AI adequacy** (AI request appears addressed)
4. **Create follow-up questions** (3 remaining minor items)
5. **Update review timeline** (sponsor responded adequately, can proceed)

---

**Step 6: Export and Use**

**For Review Documentation:**
```
Copy the "HIGH Significance Changes" section and paste into your 
review memo under "Response to Additional Information Request"
```

**For Team Discussion:**
```
Copy the Summary Statistics and Assessment sections for team meeting
```

**For Sponsor Communication:**
```
Copy the "Remaining Minor Questions" if you need to send a follow-up 
email or phone call discussion points
```

---

### Common Issues and Solutions

**Issue 1: Fewer than 100 differences found**

**Solution:**
```
You identified only [X] differences, but I need at least 100. Please 
re-analyze with higher sensitivity to detect:
- Minor wording changes that could affect interpretation
- Punctuation or formatting changes that alter meaning
- Additions of specifications or numbers
- Changes in verb tense or modality (e.g., "should" to "shall")
- Reorganization of content
- Changes in units or precision (e.g., "10mg/dL" to "10.0 mg/dL")
```

**Issue 2: Missing regulatory significance assessment**

**Solution:**
```
Please add the "Regulatory Significance" column to your table with 
assessments of HIGH/MEDIUM/LOW for each difference. Use these criteria:

HIGH: Changes to indications, safety claims, performance specs, 
identified risks, or test methods

MEDIUM: Changes to design details, technical specifications, or 
testing details that could affect review

LOW: Administrative, formatting, or clarification changes with no 
regulatory impact
```

**Issue 3: Want to filter only HIGH significance changes**

**Solution:**
```
Please create a separate summary table showing ONLY the HIGH 
significance differences (filtered from your original table). Include 
all columns, and add a "Recommended Reviewer Action" column describing 
what the reviewer should verify or assess for each HIGH item.
```

---

## Example 3: Extract Action Items & Create Task List

### Scenario
After a team review meeting, you have meeting minutes with embedded action items, questions, and follow-up tasks. You need to extract all actionable items and create a prioritized, trackable task list with checkboxes.

---

### Platform: Claude Console

#### Step-by-Step Instructions

**Step 1: Prepare Your Meeting Notes**

Example meeting minutes:
```
510(k) REVIEW TEAM MEETING MINUTES
Date: February 28, 2024
Device: AcuGluco Pro CGM (K242567)
Attendees: Dr. Smith (Lead), Dr. Johnson (Biocomp), Dr. Williams (Software), 
           Dr. Brown (Clinical), Dr. Davis (Electrical)

DISCUSSION SUMMARY:

Dr. Smith opened the meeting reviewing the overall submission status. The device 
is a CGM for Type 2 diabetes, similar to FreeStyle Libre 2 predicate.

INDICATIONS FOR USE:
Dr. Smith noted that the indications claim "replace fingerstick testing for 
treatment decisions." This is broader than the predicate which is adjunctive only.
QUESTION: Has the sponsor provided adequate clinical data to support non-adjunctive use?
Dr. Brown will need to carefully review the clinical study to verify the 98.3% 
accuracy claim and assess if this meets the bar for non-adjunctive use.

Dr. Smith: "We should compare this to the Special Controls guidance for iCGM 
devices to see if accuracy meets iCGM criteria."

DEVICE DESCRIPTION:
Device has three components: sensor, transmitter, app. Wear time is 14 days.
Dr. Johnson raised concern about 14-day wear - need to verify biocompatibility 
testing is for prolonged contact (>24h, <30days) not limited contact.
The submission references ISO 10993-1 testing in Section 8 but the summary 
table in Section 5 is incomplete. Someone needs to cross-check that all 
required tests from ISO 10993-1 Table A.1 were actually performed.

PERFORMANCE TESTING:
Bench testing appears comprehensive. Clinical study had 120 subjects across 
4 sites with 14,850 paired YSI reference points.

Dr. Brown: "I need to review the actual clinical study report, not just the 
summary. Need to verify:
- Subject demographics match intended population
- Study protocol was appropriate
- Statistical analysis is sound
- Adverse events were adequately documented
- YSI reference measurements were done correctly"

Dr. Williams noted software is Level of Concern: Moderate. The software V&V 
documentation is in Section 7 (500 pages). This will be time-consuming.
We should prioritize the software review since it's a moderate LoC and includes 
the glucose algorithm which is critical to device safety.

Dr. Davis: "For electrical safety and EMC, the submission references IEC 60601-1 
and IEC 60601-1-2 testing. I'll review the test reports but we should verify:
1. Tests were done at accredited lab
2. Correct edition/version of standards was used (we want 60601-1-2:2014, 4th edition)
3. Wireless coexistence testing was done for Bluetooth
4. Device passed all tests"

RISK MANAGEMENT:
Risk management file appears complete with FMEA. Dr. Smith: "The four major 
risks identified are reasonable - skin irritation, inaccurate readings, wireless 
interference, and data security."

However, I noticed the data security risk mitigation mentions "AES-256 encryption" 
and "user authentication" but there's no detailed cybersecurity documentation 
referenced. We need to verify:
- Cybersecurity risk assessment was performed per 2014 FDA guidance
- Threat modeling was done
- Security controls are adequate
- Software Bill of Materials (SBOM) is provided
- Vulnerability management plan exists

Dr. Williams: "I can review cybersecurity as part of my software review."

LABELING:
No one has reviewed labeling yet. The IFU is in Section 11 (150 pages).
Need someone to check:
- Indications statement matches exactly what we're clearing
- Warnings are adequate (especially for treatment decision use)
- MRI incompatibility warning is prominent
- Instructions are clear and complete
- Contraindications are appropriate

Dr. Smith: "Dr. Brown, can you take labeling review in addition to clinical?"
Dr. Brown: "Yes, I can do that, but it'll take extra time."

PREDICATE COMPARISON:
The predicate comparison table is in Section 3. Dr. Smith: "I started reviewing 
this but didn't finish. The table lists FreeStyle Libre 2 (K193899) as predicate.
Need to verify:
- All technological characteristics are compared
- Any differences are explained
- Performance testing addresses any differences
- If characteristics are different, sponsor demonstrated equivalence"

Dr. Johnson: "I can take the predicate comparison review."

TIMELINE & NEXT STEPS:
We received this submission 45 days ago. We're targeting a 90-day review cycle, 
so we have 45 days remaining. Based on today's discussion, we have significant 
review work ahead.

Priority items that could delay clearance:
1. Non-adjunctive indications claim (clinical data adequacy)
2. Software V&V review (500 pages, moderate LoC)
3. Cybersecurity documentation completeness

Dr. Smith: "Let's set intermediate deadlines:
- Complete all initial technical reviews: March 15 (2 weeks)
- Team meeting to discuss findings: March 18
- Draft review memo: March 25
- Final decision: April 5"

If we identify deficiencies, we'll issue an AI request by March 22 to stay 
on schedule.

OUTSTANDING QUESTIONS NEEDING SPONSOR CLARIFICATION:
1. Is there any pediatric use data or plans for future pediatric indication?
2. What is the claimed shelf life and is it supported by stability data?
3. Has the device been tested with acetaminophen interference? (I saw this 
   mentioned but wasn't sure if it was comprehensive)

Dr. Smith will draft these questions and send to sponsor for clarification 
via email by March 1.

ACTION ITEM ASSIGNMENTS:
- Dr. Brown: Clinical study detailed review + Labeling review (Due: March 15)
- Dr. Williams: Software V&V review + Cybersecurity assessment (Due: March 15)
- Dr. Johnson: Biocompatibility verification + Predicate comparison (Due: March 15)
- Dr. Davis: Electrical safety/EMC review (Due: March 12)
- Dr. Smith: Overall coordination, draft questions to sponsor, prepare for team 
  meeting March 18

MEETING ADJOURNED: 11:45 AM
```

---

**Step 2: Open Claude and Trigger Magic Tool 3**

Type this prompt:

```
I need to use Magic Tool 3: Action Item Extraction & Task List Generator.

Please extract ALL action items from the following meeting minutes and create 
a comprehensive, prioritized task list with:
- Unique IDs for each item
- Priority levels (HIGH/MEDIUM/LOW)
- Detailed descriptions
- Assignees
- Due dates
- Status tracking
- Checkboxes

Also identify implicit action items from questions and concerns raised.

Here are the meeting minutes:

[Paste your meeting minutes from Step 1 here]

Please proceed with comprehensive action item extraction.
```

---

**Step 3: Review the Generated Task List**

You'll receive output like this:

```markdown
# Action Item List
**Document Source**: 510(k) Review Team Meeting Minutes - AcuGluco Pro CGM
**Meeting Date**: February 28, 2024
**Extraction Date**: February 28, 2024
**Total Action Items Identified**: 24

---

## High Priority Action Items (9)

### ITEM-001: Review Clinical Study Report for Non-Adjunctive Use Support
- **Priority**: 🔴 HIGH
- **Category**: Clinical Performance
- **Description**: Conduct detailed review of the full clinical study report 
  to verify if the 98.3% accuracy claim and study design adequately support 
  the non-adjunctive indication ("replace fingerstick testing for treatment 
  decisions"). This is broader than the predicate device (FreeStyle Libre 2) 
  which is adjunctive only. Verify subject demographics, protocol appropriateness, 
  statistical soundness, adverse event documentation, and YSI reference methodology.
- **Assignee**: Dr. Brown
- **Estimated Effort**: 8-12 hours
- **Due Date**: March 15, 2024
- **Status**: ⏳ Not Started
- **Dependencies**: Clinical study report must be located in submission
- **Checkbox**: - [ ] Complete detailed clinical study report review

**Notes**: This is critical for SE determination. If clinical data is insufficient 
for non-adjunctive claim, this could result in NSE or AI request.

---

### ITEM-002: Verify Clinical Data Meets iCGM Special Controls Criteria
- **Priority**: 🔴 HIGH
- **Category**: Regulatory Classification
- **Description**: Compare the device's accuracy performance (98.3% within 
  ±15% or ±15 mg/dL) against FDA's Special Controls guidance for integrated 
  Continuous Glucose Monitoring Systems (iCGM) to determine if device meets 
  iCGM criteria. This assessment will inform whether non-adjunctive use is 
  appropriate.
- **Assignee**: Dr. Smith
- **Estimated Effort**: 2 hours
- **Due Date**: March 8, 2024
- **Status**: ⏳ Not Started
- **Dependencies**: None (guidance document is publicly available)
- **Checkbox**: - [ ] Compare accuracy to iCGM special controls criteria

**Notes**: Dr. Smith mentioned this during indications discussion. iCGM special 
controls may provide regulatory precedent for non-adjunctive use approval.

---

### ITEM-003: Review 500-Page Software V&V Documentation
- **Priority**: 🔴 HIGH
- **Category**: Software
- **Description**: Conduct comprehensive review of software verification and 
  validation documentation (Section 7, 500 pages). Device has Level of Concern: 
  Moderate, and software includes critical glucose algorithm. Review must verify 
  adequate software development lifecycle compliance per FDA Software Guidance 
  (2005), including requirements traceability, unit testing, integration testing, 
  system testing, and risk-based testing.
- **Assignee**: Dr. Williams
- **Estimated Effort**: 16-20 hours (due to volume)
- **Due Date**: March 15, 2024
- **Status**: ⏳ Not Started
- **Dependencies**: None
- **Checkbox**: - [ ] Complete software V&V review

**Notes**: Dr. Williams noted this is time-consuming but critical. Prioritize 
this review given moderate LoC and safety-critical algorithm.

---

### ITEM-004: Assess Cybersecurity Documentation Completeness
- **Priority**: 🔴 HIGH
- **Category**: Cybersecurity
- **Description**: Verify cybersecurity risk assessment per FDA 2014 guidance 
  "Content of Premarket Submissions for Management of Cybersecurity in Medical 
  Devices." Assessment must confirm: (1) Threat modeling was performed, 
  (2) Security controls (AES-256 encryption, user authentication) are adequately 
  documented, (3) Software Bill of Materials (SBOM) is provided, (4) Vulnerability 
  management plan exists. Risk management mentions encryption and authentication 
  but detailed cybersecurity documentation is not referenced.
- **Assignee**: Dr. Williams
- **Estimated Effort**: 4-6 hours
- **Due Date**: March 15, 2024
- **Status**: ⏳ Not Started
- **Dependencies**: Cybersecurity documentation must be located in submission
- **Checkbox**: - [ ] Review and verify cybersecurity documentation

**Notes**: Dr. Smith raised concern that risk mitigation mentions security 
controls but no detailed cybersecurity section is referenced. This could be 
a deficiency if documentation is missing.

---

### ITEM-005: Verify Biocompatibility Testing for 14-Day Prolonged Contact
- **Priority**: 🔴 HIGH
- **Category**: Biocompatibility
- **Description**: Confirm that biocompatibility testing was conducted per 
  ISO 10993-1:2018 for prolonged contact (>24hr, ≤30 days) with intact skin, 
  appropriate for the device's 14-day wear time. Cross-check summary table 
  in Section 5 against detailed test reports in Section 8 to verify all required 
  tests from ISO 10993-1 Table A.1 were actually performed. Dr. Johnson noted 
  the summary table appears incomplete.
- **Assignee**: Dr. Johnson
- **Estimated Effort**: 3-4 hours
- **Due Date**: March 15, 2024
- **Status**: ⏳ Not Started
- **Dependencies**: Section 8 test reports must be reviewed
- **Checkbox**: - [ ] Verify ISO 10993-1 test battery completeness

**Notes**: Extended wear time from 10 to 14 days requires confirming appropriate 
contact duration category for biocompatibility testing.

---

### ITEM-006: Review Electrical Safety and EMC Test Reports
- **Priority**: 🔴 HIGH
- **Category**: Electrical Safety / EMC
- **Description**: Review test reports for IEC 60601-1 (electrical safety) 
  and IEC 60601-1-2 (electromagnetic compatibility). Verify: (1) Tests were 
  conducted at accredited laboratories, (2) Correct editions used (60601-1-2:2014, 
  4th edition preferred), (3) Wireless coexistence testing was performed for 
  Bluetooth 5.0, (4) Device passed all required tests with no deviations or 
  failures.
- **Assignee**: Dr. Davis
- **Estimated Effort**: 4-5 hours
- **Due Date**: March 12, 2024
- **Status**: ⏳ Not Started
- **Dependencies**: Test reports must be located in submission
- **Checkbox**: - [ ] Review IEC 60601-1 and 60601-1-2 test reports

**Notes**: Dr. Davis will handle this review. Earlier due date (March 12) 
provides buffer time.

---

### ITEM-007: Complete Predicate Device Comparison Table Review
- **Priority**: 🔴 HIGH
- **Category**: Substantial Equivalence
- **Description**: Review predicate comparison table (Section 3) comparing 
  subject device (AcuGluco Pro) to predicate (FreeStyle Libre 2, K193899). 
  Verify: (1) All technological characteristics are compared, (2) Any differences 
  are adequately explained, (3) Performance testing addresses identified differences, 
  (4) Sponsor has demonstrated equivalence despite any differences. Dr. Smith 
  started this review but did not complete it.
- **Assignee**: Dr. Johnson
- **Estimated Effort**: 3-4 hours
- **Due Date**: March 15, 2024
- **Status**: ⏳ In Progress (Dr. Smith started)
- **Dependencies**: None
- **Checkbox**: - [ ] Complete predicate comparison table review

**Notes**: Dr. Johnson will complete this review. Incomplete predicate comparison 
is a common deficiency leading to AI requests.

---

### ITEM-008: Review Labeling (Instructions for Use)
- **Priority**: 🔴 HIGH
- **Category**: Labeling
- **Description**: Conduct comprehensive review of Instructions for Use (IFU) 
  in Section 11 (150 pages). Verify: (1) Indications for Use statement matches 
  exactly what is being cleared, (2) Warnings are adequate (especially for 
  treatment decision use without confirmatory fingerstick), (3) MRI incompatibility 
  warning is prominent and clear, (4) Instructions are complete and easy to follow, 
  (5) Contraindications are appropriate, (6) All required labeling elements 
  per 21 CFR 801 are present.
- **Assignee**: Dr. Brown
- **Estimated Effort**: 5-6 hours
- **Due Date**: March 15, 2024
- **Status**: ⏳ Not Started
- **Dependencies**: None
- **Checkbox**: - [ ] Complete IFU/labeling review

**Notes**: Dr. Brown will handle both clinical and labeling reviews. Labeling 
is critical for non-adjunctive use claim - warnings must be adequate.

---

### ITEM-009: Draft and Send Clarification Questions to Sponsor
- **Priority**: 🔴 HIGH
- **Category**: Sponsor Communication
- **Description**: Draft email with three clarification questions identified 
  during meeting: (1) Is there any pediatric use data or plans for future 
  pediatric indication? (2) What is the claimed shelf life and is it supported 
  by stability testing data? (3) Has the device been tested comprehensively 
  for acetaminophen interference? Send email to sponsor requesting responses.
- **Assignee**: Dr. Smith
- **Estimated Effort**: 1 hour
- **Due Date**: March 1, 2024 (URGENT - 2 days away)
- **Status**: ⏳ Not Started
- **Dependencies**: None
- **Checkbox**: - [ ] Draft and send clarification questions to sponsor

**Notes**: Early due date to allow sponsor time to respond before March 15 
review completion deadline.

---

## Medium Priority Action Items (10)

### ITEM-010: Verify Adequate Adverse Event Documentation in Clinical Study
- **Priority**: 🟡 MEDIUM
- **Category**: Clinical Safety
- **Description**: As part of clinical study review (ITEM-001), specifically 
  verify that adverse events during the 120-subject study were adequately 
  documented, categorized by severity and relatedness, and that all serious 
  adverse events (SAEs) were reported. Confirm no SAEs were device-related.
- **Assignee**: Dr. Brown
- **Estimated Effort**: 2 hours (included in clinical review time)
- **Due Date**: March 15, 2024
- **Status**: ⏳ Not Started
- **Dependencies**: ITEM-001 (clinical study review)
- **Checkbox**: - [ ] Verify AE documentation adequacy

---

### ITEM-011: Confirm YSI Reference Measurements Were Conducted Properly
- **Priority**: 🟡 MEDIUM
- **Category**: Clinical Performance
- **Description**: Verify that YSI 2300 reference glucose measurements in the 
  clinical study were performed according to manufacturer instructions and 
  appropriate quality control procedures. Confirm YSI operator training was 
  documented and YSI calibration/maintenance records are available.
- **Assignee**: Dr. Brown
- **Estimated Effort**: 1 hour (included in clinical review time)
- **Due Date**: March 15, 2024
- **Status**: ⏳ Not Started
- **Dependencies**: ITEM-001 (clinical study review)
- **Checkbox**: - [ ] Verify YSI reference methodology

---

### ITEM-012: Assess Statistical Analysis Methodology in Clinical Study
- **Priority**: 🟡 MEDIUM
- **Category**: Clinical Performance
- **Description**: Review the statistical analysis section of the clinical 
  study report to verify appropriate sample size calculation, endpoint selection, 
  statistical tests (e.g., for accuracy assessment), and handling of missing data. 
  Confirm that 14,850 paired data points provide adequate statistical power.
- **Assignee**: Dr. Brown
- **Estimated Effort**: 2 hours (included in clinical review time)
- **Due Date**: March 15, 2024
- **Status**: ⏳ Not Started
- **Dependencies**: ITEM-001 (clinical study review)
- **Checkbox**: - [ ] Review clinical statistical analysis

---

### ITEM-013: Verify Subject Demographics Match Intended Population
- **Priority**: 🟡 MEDIUM
- **Category**: Clinical Performance
- **Description**: Confirm that the 120 clinical study subjects' demographics 
  (age, diabetes type, glucose control level, etc.) are representative of the 
  intended use population (adults 18+ with diabetes mellitus). Assess if any 
  subgroups are underrepresented.
- **Assignee**: Dr. Brown
- **Estimated Effort**: 1 hour (included in clinical review time)
- **Due Date**: March 15, 2024
- **Status**: ⏳ Not Started
- **Dependencies**: ITEM-001 (clinical study review)
- **Checkbox**: - [ ] Verify subject demographics representativeness

---

### ITEM-014: Confirm Accredited Laboratory for Electrical/EMC Testing
- **Priority**: 🟡 MEDIUM
- **Category**: Electrical Safety / EMC
- **Description**: Verify that IEC 60601-1 and IEC 60601-1-2 testing was 
  conducted at an ISO/IEC 17025 accredited testing laboratory. Confirm lab 
  accreditation certificates or statements are included in test reports.
- **Assignee**: Dr. Davis
- **Estimated Effort**: 30 minutes (included in EMC review time)
- **Due Date**: March 12, 2024
- **Status**: ⏳ Not Started
- **Dependencies**: ITEM-006 (EMC test report review)
- **Checkbox**: - [ ] Verify accredited lab for electrical/EMC testing

---

### ITEM-015: Verify Correct Edition of IEC 60601-1-2 Standard Used
- **Priority**: 🟡 MEDIUM
- **Category**: EMC
- **Description**: Confirm that testing was performed to IEC 60601-1-2:2014 
  (4th edition) rather than older 3rd edition (2007). The 4th edition includes 
  updated immunity levels and risk management requirements.
- **Assignee**: Dr. Davis
- **Estimated Effort**: 15 minutes (included in EMC review time)
- **Due Date**: March 12, 2024
- **Status**: ⏳ Not Started
- **Dependencies**: ITEM-006 (EMC test report review)
- **Checkbox**: - [ ] Verify IEC 60601-1-2 edition is 2014 (4th ed.)

---

### ITEM-016: Assess Adequacy of Warnings for Non-Adjunctive Use
- **Priority**: 🟡 MEDIUM
- **Category**: Labeling
- **Description**: Specifically assess if IFU warnings adequately inform users 
  about limitations and appropriate use for treatment decisions without confirmatory 
  fingerstick testing. Verify warnings cover situations where CGM may be inaccurate 
  (e.g., rapid glucose changes, sensor warm-up period, end of sensor life).
- **Assignee**: Dr. Brown
- **Estimated Effort**: 1 hour (included in labeling review time)
- **Due Date**: March 15, 2024
- **Status**: ⏳ Not Started
- **Dependencies**: ITEM-008 (labeling review)
- **Checkbox**: - [ ] Assess non-adjunctive use warnings adequacy

---

### ITEM-017: Verify MRI Incompatibility Warning Prominence
- **Priority**: 🟡 MEDIUM
- **Category**: Labeling
- **Description**: Confirm that Instructions for Use contain a clear, prominent 
  warning about MRI incompatibility and the need to remove the device before 
  MRI procedures. Verify warning uses appropriate signal word (e.g., WARNING 
  or CAUTION) and is placed in a highly visible location.
- **Assignee**: Dr. Brown
- **Estimated Effort**: 30 minutes (included in labeling review time)
- **Due Date**: March 15, 2024
- **Status**: ⏳ Not Started
- **Dependencies**: ITEM-008 (labeling review)
- **Checkbox**: - [ ] Verify MRI warning prominence in IFU

---

### ITEM-018: Review Risk Management File Structure and Completeness
- **Priority**: 🟡 MEDIUM
- **Category**: Risk Management
- **Description**: Review the Risk Management File structure to verify it includes 
  all required elements per ISO 14971:2019: hazard identification, risk estimation, 
  risk evaluation, risk control, residual risk evaluation, benefit-risk analysis, 
  and production/post-production information plan. Verify FMEA methodology is 
  appropriate.
- **Assignee**: Dr. Smith
- **Estimated Effort**: 2-3 hours
- **Due Date**: March 15, 2024
- **Status**: ⏳ Not Started
- **Dependencies**: None
- **Checkbox**: - [ ] Review Risk Management File completeness

---

### ITEM-019: Cross-Check Biocompatibility Summary vs. Detailed Reports
- **Priority**: 🟡 MEDIUM
- **Category**: Biocompatibility
- **Description**: Compare the biocompatibility testing summary table (Section 5) 
  against detailed test reports (Section 8) to identify any discrepancies. 
  Dr. Johnson noted the summary table appears incomplete. Verify all tests 
  listed in summary have corresponding detailed reports.
- **Assignee**: Dr. Johnson
- **Estimated Effort**: 1 hour (included in biocomp review time)
- **Due Date**: March 15, 2024
- **Status**: ⏳ Not Started
- **Dependencies**: ITEM-005 (biocompatibility verification)
- **Checkbox**: - [ ] Cross-check biocomp summary vs. detailed reports

---

## Low Priority Action Items (5)

### ITEM-020: Schedule March 18 Team Review Meeting
- **Priority**: 🟢 LOW
- **Category**: Administrative
- **Description**: Send calendar invitation for team review meeting on March 18 
  to discuss all technical review findings. Include all meeting attendees from 
  today (Dr. Smith, Dr. Johnson, Dr. Williams, Dr. Brown, Dr. Davis). Reserve 
  conference room or video conference link.
- **Assignee**: Dr. Smith
- **Estimated Effort**: 15 minutes
- **Due Date**: March 1, 2024
- **Status**: ⏳ Not Started
- **Dependencies**: None
- **Checkbox**: - [ ] Schedule March 18 team review meeting

---

### ITEM-021: Update Internal Tracking System with Review Timeline
- **Priority**: 🟢 LOW
- **Category**: Administrative
- **Description**: Update the division's 510(k) tracking database/spreadsheet 
  with key milestones for K242567: Received (45 days ago), Technical Review 
  Target (March 15), Team Meeting (March 18), Draft Memo (March 25), Final 
  Decision (April 5). Update status to "In Technical Review."
- **Assignee**: Dr. Smith (or administrative assistant)
- **Estimated Effort**: 10 minutes
- **Due Date**: March 5, 2024
- **Status**: ⏳ Not Started
- **Dependencies**: None
- **Checkbox**: - [ ] Update tracking system with milestones

---

### ITEM-022: Prepare Draft Agenda for March 18 Team Meeting
- **Priority**: 🟢 LOW
- **Category**: Administrative
- **Description**: Prepare agenda for March 18 team review meeting. Include: 
  (1) Review findings presentation (each reviewer presents their area), 
  (2) Discussion of deficiencies or concerns, (3) Decision on AI request vs. 
  clearance, (4) Assignment of memo drafting responsibilities, (5) Timeline 
  for final decision.
- **Assignee**: Dr. Smith
- **Estimated Effort**: 30 minutes
- **Due Date**: March 15, 2024
- **Status**: ⏳ Not Started
- **Dependencies**: None
- **Checkbox**: - [ ] Prepare March 18 meeting agenda

---

### ITEM-023: Gather Predicate Device Clearance Letter (K193899)
- **Priority**: 🟢 LOW
- **Category**: Reference Materials
- **Description**: Retrieve FDA clearance letter and summary for predicate 
  device FreeStyle Libre 2 (K193899) from FDA database for reference during 
  predicate comparison review. This will help verify indications and technological 
  characteristics claims.
- **Assignee**: Dr. Johnson (or administrative assistant)
- **Estimated Effort**: 10 minutes
- **Due Date**: March 8, 2024
- **Status**: ⏳ Not Started
- **Dependencies**: None
- **Checkbox**: - [ ] Retrieve predicate K193899 clearance letter

---

### ITEM-024: Archive Today's Meeting Minutes in Document System
- **Priority**: 🟢 LOW
- **Category**: Administrative
- **Description**: Save and archive today's meeting minutes (February 28, 2024) 
  in the division's document management system under K242567 folder. Ensure 
  proper naming convention and access permissions.
- **Assignee**: Dr. Smith (or administrative assistant)
- **Estimated Effort**: 5 minutes
- **Due Date**: March 1, 2024
- **Status**: ⏳ Not Started
- **Dependencies**: None
- **Checkbox**: - [ ] Archive meeting minutes

---

## Action Item Summary Table

| ID | Action | Priority | Assignee | Due Date | Status | Est. Hours |
|----|--------|----------|----------|----------|--------|------------|
| 001 | Review Clinical Study for Non-Adjunctive Use | 🔴 HIGH | Dr. Brown | 03/15 | ⏳ Not Started | 8-12 |
| 002 | Compare Accuracy to iCGM Criteria | 🔴 HIGH | Dr. Smith | 03/08 | ⏳ Not Started | 2 |
| 003 | Review Software V&V (500 pages) | 🔴 HIGH | Dr. Williams | 03/15 | ⏳ Not Started | 16-20 |
| 004 | Assess Cybersecurity Documentation | 🔴 HIGH | Dr. Williams | 03/15 | ⏳ Not Started | 4-6 |
| 005 | Verify Biocompatibility for 14-Day Wear | 🔴 HIGH | Dr. Johnson | 03/15 | ⏳ Not Started | 3-4 |
| 006 | Review Electrical Safety/EMC Reports | 🔴 HIGH | Dr. Davis | 03/12 | ⏳ Not Started | 4-5 |
| 007 | Complete Predicate Comparison Review | 🔴 HIGH | Dr. Johnson | 03/15 | ⏸️ In Progress | 3-4 |
| 008 | Review IFU/Labeling (150 pages) | 🔴 HIGH | Dr. Brown | 03/15 | ⏳ Not Started | 5-6 |
| 009 | Draft/Send Questions to Sponsor | 🔴 HIGH | Dr. Smith | 03/01 | ⏳ Not Started | 1 |
| 010 | Verify AE Documentation | 🟡 MEDIUM | Dr. Brown | 03/15 | ⏳ Not Started | 2 |
| 011 | Confirm YSI Reference Methodology | 🟡 MEDIUM | Dr. Brown | 03/15 | ⏳ Not Started | 1 |
| 012 | Review Statistical Analysis | 🟡 MEDIUM | Dr. Brown | 03/15 | ⏳ Not Started | 2 |
| 013 | Verify Subject Demographics | 🟡 MEDIUM | Dr. Brown | 03/15 | ⏳ Not Started | 1 |
| 014 | Confirm Accredited Lab for EMC | 🟡 MEDIUM | Dr. Davis | 03/12 | ⏳ Not Started | 0.5 |
| 015 | Verify IEC 60601-1-2 Edition | 🟡 MEDIUM | Dr. Davis | 03/12 | ⏳ Not Started | 0.25 |
| 016 | Assess Non-Adjunctive Warnings | 🟡 MEDIUM | Dr. Brown | 03/15 | ⏳ Not Started | 1 |
| 017 | Verify MRI Warning Prominence | 🟡 MEDIUM | Dr. Brown | 03/15 | ⏳ Not Started | 0.5 |
| 018 | Review Risk Management File | 🟡 MEDIUM | Dr. Smith | 03/15 | ⏳ Not Started | 2-3 |
| 019 | Cross-Check Biocomp Summary | 🟡 MEDIUM | Dr. Johnson | 03/15 | ⏳ Not Started | 1 |
| 020 | Schedule March 18 Meeting | 🟢 LOW | Dr. Smith | 03/01 | ⏳ Not Started | 0.25 |
| 021 | Update Tracking System | 🟢 LOW | Dr. Smith | 03/05 | ⏳ Not Started | 0.17 |
| 022 | Prepare Meeting Agenda | 🟢 LOW | Dr. Smith | 03/15 | ⏳ Not Started | 0.5 |
| 023 | Retrieve Predicate Clearance Letter | 🟢 LOW | Dr. Johnson | 03/08 | ⏳ Not Started | 0.17 |
| 024 | Archive Meeting Minutes | 🟢 LOW | Dr. Smith | 03/01 | ⏳ Not Started | 0.08 |

**Total Action Items**: 24  
**Total Estimated Hours**: 59-75 hours

---

## Workload Distribution

| Reviewer | # of Actions | Est. Total Hours | Key Responsibilities |
|----------|--------------|------------------|----------------------|
| Dr. Brown | 8 | 20.5-29.5 | Clinical study, Labeling |
| Dr. Williams | 2 | 20-26 | Software V&V, Cybersecurity |
| Dr. Johnson | 4 | 7.17-9.17 | Biocompatibility, Predicate comparison |
| Dr. Davis | 3 | 4.75-5.75 | Electrical safety, EMC |
| Dr. Smith | 7 | 6.08-9.08 | Coordination, Risk management, iCGM assessment |

**Note**: Dr. Brown and Dr. Williams have the heaviest workloads. Consider 
providing support or extending deadlines if needed.

---

## Quick Copy Checklist (All Items with Checkboxes)

### HIGH Priority (Due by March 15 or earlier)
- [ ] ITEM-001: Review Clinical Study for Non-Adjunctive Use (Dr. Brown, 03/15)
- [ ] ITEM-002: Compare Accuracy to iCGM Criteria (Dr. Smith, 03/08)
- [ ] ITEM-003: Review Software V&V 500 pages (Dr. Williams, 03/15)
- [ ] ITEM-004: Assess Cybersecurity Documentation (Dr. Williams, 03/15)
- [ ] ITEM-005: Verify Biocompatibility 14-Day Wear (Dr. Johnson, 03/15)
- [ ] ITEM-006: Review Electrical Safety/EMC Reports (Dr. Davis, 03/12)
- [ ] ITEM-007: Complete Predicate Comparison (Dr. Johnson, 03/15)
- [ ] ITEM-008: Review IFU/Labeling 150 pages (Dr. Brown, 03/15)
- [ ] ITEM-009: Draft/Send Questions to Sponsor (Dr. Smith, 03/01) ⚠️ URGENT

### MEDIUM Priority (Due by March 15)
- [ ] ITEM-010: Verify AE Documentation (Dr. Brown, 03/15)
- [ ] ITEM-011: Confirm YSI Reference Methodology (Dr. Brown, 03/15)
- [ ] ITEM-012: Review Statistical Analysis (Dr. Brown, 03/15)
- [ ] ITEM-013: Verify Subject Demographics (Dr. Brown, 03/15)
- [ ] ITEM-014: Confirm Accredited Lab (Dr. Davis, 03/12)
- [ ] ITEM-015: Verify IEC 60601-1-2 Edition (Dr. Davis, 03/12)
- [ ] ITEM-016: Assess Non-Adjunctive Warnings (Dr. Brown, 03/15)
- [ ] ITEM-017: Verify MRI Warning Prominence (Dr. Brown, 03/15)
- [ ] ITEM-018: Review Risk Management File (Dr. Smith, 03/15)
- [ ] ITEM-019: Cross-Check Biocomp Summary (Dr. Johnson, 03/15)

### LOW Priority (Administrative)
- [ ] ITEM-020: Schedule March 18 Meeting (Dr. Smith, 03/01)
- [ ] ITEM-021: Update Tracking System (Dr. Smith, 03/05)
- [ ] ITEM-022: Prepare Meeting Agenda (Dr. Smith, 03/15)
- [ ] ITEM-023: Retrieve Predicate Letter (Dr. Johnson, 03/08)
- [ ] ITEM-024: Archive Meeting Minutes (Dr. Smith, 03/01)

---

## Timeline Visualization

```
TODAY (Feb 28)
     |
     v
Mar 1 ─► URGENT: Send sponsor questions (ITEM-009)
     |    URGENT: Schedule meeting (ITEM-020)
     |    Archive minutes (ITEM-024)
     |
Mar 5 ─► Update tracking system (ITEM-021)
     |
Mar 8 ─► iCGM comparison complete (ITEM-002)
     |    Retrieve predicate letter (ITEM-023)
     |
Mar 12 ─► Electrical/EMC review complete (ITEM-006, 014, 015)
     |
Mar 15 ─► ALL technical reviews complete (ITEMS 001, 003-005, 007-013, 016-019, 022)
     |
Mar 18 ─► TEAM REVIEW MEETING
     |     ↓
     |   Discuss findings
     |   Decide: AI request vs. Clearance
     |   Assign memo drafting
     |
Mar 22 ─► Issue AI request if needed (stay on schedule)
     |
Mar 25 ─► Draft review memo complete
     |
Apr 5  ─► FINAL DECISION (90-day target)
```

---

**End of Action Item List**
```

---

**Step 4: Export and Use the Task List**

**For Project Management:**
1. Copy the "Summary Table" section
2. Paste into Excel, Google Sheets, or project management tool (Asana, Trello, Monday)
3. Track progress as items are completed

**For Team Distribution:**
1. Copy the relevant section for each team member
   - Example: Send Dr. Brown items 001, 008, 010-013, 016-017
2. Email or share via collaboration tool

**For Personal To-Do:**
1. Copy the "Quick Copy Checklist" section
2. Paste into your personal task app (Todoist, Notion, Apple Reminders)
3. Check off items as you complete them

**For Meeting Preparation:**
1. Copy the "Timeline Visualization" section
2. Include in meeting agenda or presentation slides
3. Use to communicate project status to leadership

---

### Common Issues and Solutions

**Issue 1: Want to add custom fields (like "Review Section" or "Document Location")**

**Solution:**
```
Please add these additional columns to the action item table:
- Review Section (e.g., "Section 7 - Software", "Section 11 - IFU")
- Document Location (page numbers or section references)
- Deficiency Risk (likelihood this could lead to AI request: High/Med/Low)

Regenerate the summary table with these additional columns.
```

**Issue 2: Need to export to specific project management tool format**

**Solution:**
```
Please reformat the action item list as a CSV (comma-separated values) file 
suitable for importing into [Tool Name, e.g., "Microsoft Project"]. 

Use this format:
ID,Task Name,Priority,Assignee,Start Date,Due Date,Duration (days),Notes

Provide the output in a code block so I can copy it directly.
```

**Issue 3: Want to filter by assignee**

**Solution:**
```
Please create separate action item lists for each assignee:
1. Dr. Brown's Action Items (with subtotals)
2. Dr. Williams's Action Items
3. Dr. Johnson's Action Items
4. Dr. Davis's Action Items
5. Dr. Smith's Action Items

For each person, show: Total items, Total hours, Earliest due date
```

**Issue 4: Missed some implicit action items**

**Solution:**
```
I think there are additional implicit action items you may have missed. 
Please re-analyze the meeting minutes specifically looking for:

1. Concerns or questions raised without explicit action assignments
   Example: "I'm concerned about X" → Action: Investigate X

2. Statements indicating something needs verification
   Example: "The submission says Y, but I'm not sure" → Action: Verify Y

3. Comparisons mentioned
   Example: "We should compare to guidance Z" → Action: Compare to guidance Z

4. Follow-up needed after a task
   Example: If Task A reveals issues → Action: Address issues from Task A

Please generate additional action items for these implicit tasks.
```

---

(Due to length constraints, I'll provide Examples 4 and 5 in a follow-up response. Would you like me to continue with Examples 4 & 5, or would you prefer the Troubleshooting Guide and Tips for Best Results sections next?)
