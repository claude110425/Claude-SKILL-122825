<scratchpad>
Let me analyze the provided code to understand what needs to be specified:

**Core Purpose Analysis:**
The code shows a GUDID (Global Unique Device Identification) agentic AI system built with Streamlit. However, the app_description asks for something completely different - an FDA medical device information search, PDF to markdown conversion, document summarization, and document comparison tool.

There's a significant mismatch between:
1. The code: A multi-agent orchestration system for GUDID with 10 specialized agents
2. The app_description: A simpler 4-step workflow for FDA device search, PDF processing, summarization, and comparison

I need to create a specification that addresses BOTH:
- The actual requirements from app_description (which is what the user wants)
- Potentially incorporating useful patterns from the provided code (multi-agent, LLM integration)

**Key Requirements from app_description:**
1. FDA device information search (510(k) number) → 3000-4000 word markdown summary with 5+ tables
2. PDF to markdown conversion (user selects pages, default first 10)
3. Document summarization (3000-4000 words, 20 entities in table with context)
4. Document comparison (identify 100 differences between two PDF versions in table)

**Technology Stack from Code:**
- Streamlit for UI
- Multiple LLM providers (OpenAI, Anthropic, Google Gemini)
- PyYAML for configuration
- Pandas for data handling
- Python type hints

**What I Need to Specify:**
Since the app_description is the actual requirement, I'll create a specification for THAT application, but incorporate the multi-LLM approach and orchestration patterns from the code.

The application needs:
1. FDA API integration (or web scraping)
2. PDF processing capabilities (PyPDF2, pdfplumber, or similar)
3. OCR capabilities for PDF to markdown
4. LLM integration for summarization
5. Document comparison logic
6. Markdown generation
7. Table generation capabilities
8. Multi-step workflow UI

Let me structure a comprehensive specification.
</scratchpad>

<specification>

# Technical Specification: FDA Medical Device Intelligence System

## 1. Executive Summary

### 1.1 Application Overview
The FDA Medical Device Intelligence System is a comprehensive document processing and analysis application designed to help medical device professionals research FDA-cleared devices, convert technical documents to markdown, generate detailed summaries, and identify differences between document versions.

### 1.2 Core Functionality
The application provides a 4-stage workflow:
1. **FDA Device Search & Analysis**: Search FDA 510(k) database by device name or number, generate comprehensive 3000-4000 word markdown reports with minimum 5 tables
2. **PDF to Markdown Conversion**: Extract and convert user-selected PDF pages (default: first 10 pages) into clean markdown format
3. **Document Summarization**: Generate detailed 3000-4000 word summaries with 20+ extracted entities in structured tables
4. **Document Comparison**: Analyze two versions of documents and identify 100+ differences with references and context

### 1.3 Target Users
- Regulatory affairs professionals
- Medical device manufacturers
- Quality assurance teams
- Technical writers
- Compliance officers

### 1.4 Key Features
- Multi-LLM support (OpenAI, Anthropic, Google Gemini)
- Intelligent agent orchestration
- Advanced PDF processing with OCR
- FDA database integration
- Structured markdown output with tables
- Side-by-side document comparison
- Export capabilities (markdown, JSON, CSV)

---

## 2. Technology Stack

### 2.1 Core Framework
- **Python**: 3.9+
- **Streamlit**: 1.28.0+ (Web application framework)
- **Type System**: Python typing module for type hints

### 2.2 LLM Integration
- **OpenAI API**: GPT-4, GPT-4-Turbo, GPT-3.5-Turbo
  - Library: `openai` 1.0.0+
- **Anthropic API**: Claude-3 (Opus, Sonnet, Haiku)
  - Library: `anthropic` 0.7.0+
- **Google Gemini API**: Gemini-Pro, Gemini-Pro-Vision
  - Library: `google-generativeai` 0.3.0+

### 2.3 PDF Processing
- **PyPDF2**: 3.0.0+ (PDF text extraction)
- **pdfplumber**: 0.10.0+ (Advanced PDF parsing, table extraction)
- **pdf2image**: 1.16.0+ (PDF to image conversion)
- **pytesseract**: 0.3.10+ (OCR capabilities)
- **Pillow**: 10.0.0+ (Image processing)

### 2.4 FDA Data Integration
- **requests**: 2.31.0+ (HTTP client for FDA API)
- **beautifulsoup4**: 4.12.0+ (Web scraping if needed)
- **lxml**: 4.9.0+ (XML/HTML parsing)

### 2.5 Data Processing
- **pandas**: 2.0.0+ (DataFrame operations, table generation)
- **numpy**: 1.24.0+ (Numerical operations)
- **PyYAML**: 6.0+ (Configuration management)

### 2.6 Text Processing
- **markdown**: 3.4.0+ (Markdown generation and parsing)
- **python-docx**: 0.8.11+ (DOCX export if needed)
- **tabulate**: 0.9.0+ (Table formatting)

### 2.7 Utilities
- **python-dotenv**: 1.0.0+ (Environment variable management)
- **tenacity**: 8.2.0+ (Retry logic for API calls)
- **difflib**: Built-in (Document comparison)

### 2.8 Development Tools
- **black**: Code formatting
- **pylint**: Code linting
- **pytest**: Testing framework

---

## 3. Data Models

### 3.1 Core Type Definitions

```python
from typing import Dict, List, Optional, Tuple, Any, Literal
from dataclasses import dataclass, field
from datetime import datetime
from enum import Enum

class WorkflowStage(Enum):
    """Application workflow stages"""
    FDA_SEARCH = "fda_search"
    PDF_TO_MARKDOWN = "pdf_to_markdown"
    DOCUMENT_SUMMARY = "document_summary"
    DOCUMENT_COMPARISON = "document_comparison"

class LLMProvider(Enum):
    """Supported LLM providers"""
    OPENAI = "openai"
    ANTHROPIC = "anthropic"
    GEMINI = "gemini"

class DocumentType(Enum):
    """Types of documents processed"""
    IFU = "instructions_for_use"
    TECHNICAL_SPEC = "technical_specification"
    CLINICAL_DATA = "clinical_data"
    LABEL = "label"
    SUMMARY_SAFETY = "summary_safety_effectiveness"
    OTHER = "other"

@dataclass
class LLMConfig:
    """Configuration for LLM providers"""
    provider: LLMProvider
    model: str
    api_key: str
    temperature: float = 0.7
    max_tokens: int = 4000
    timeout: int = 120

@dataclass
class FDADevice:
    """FDA device information model"""
    device_name: str
    fda_510k_number: Optional[str] = None
    product_code: Optional[str] = None
    device_class: Optional[str] = None
    regulation_number: Optional[str] = None
    submission_type: Optional[str] = None
    decision_date: Optional[datetime] = None
    decision: Optional[str] = None
    applicant: Optional[str] = None
    contact: Optional[str] = None
    predicate_devices: List[str] = field(default_factory=list)
    device_description: Optional[str] = None
    intended_use: Optional[str] = None
    indications_for_use: Optional[str] = None
    clearance_type: Optional[str] = None
    review_panel: Optional[str] = None
    advisory_committee: Optional[str] = None
    
    def to_dict(self) -> Dict[str, Any]:
        """Convert to dictionary for serialization"""
        return {
            'device_name': self.device_name,
            'fda_510k_number': self.fda_510k_number,
            'product_code': self.product_code,
            'device_class': self.device_class,
            'regulation_number': self.regulation_number,
            'submission_type': self.submission_type,
            'decision_date': self.decision_date.isoformat() if self.decision_date else None,
            'decision': self.decision,
            'applicant': self.applicant,
            'contact': self.contact,
            'predicate_devices': self.predicate_devices,
            'device_description': self.device_description,
            'intended_use': self.intended_use,
            'indications_for_use': self.indications_for_use,
            'clearance_type': self.clearance_type,
            'review_panel': self.review_panel,
            'advisory_committee': self.advisory_committee
        }

@dataclass
class FDASearchResult:
    """Results from FDA search with analysis"""
    device: FDADevice
    raw_data: Dict[str, Any]
    markdown_report: str
    tables: List[Dict[str, Any]]
    word_count: int
    generated_at: datetime
    search_query: str
    
@dataclass
class PDFPage:
    """Individual PDF page representation"""
    page_number: int
    text_content: str
    has_images: bool
    has_tables: bool
    image_data: Optional[bytes] = None
    tables: List[Dict[str, Any]] = field(default_factory=list)
    metadata: Dict[str, Any] = field(default_factory=dict)

@dataclass
class PDFDocument:
    """Complete PDF document model"""
    filename: str
    total_pages: int
    pages: List[PDFPage]
    metadata: Dict[str, Any]
    file_size_bytes: int
    uploaded_at: datetime
    file_hash: str  # For comparison purposes

@dataclass
class MarkdownConversion:
    """Result of PDF to Markdown conversion"""
    original_filename: str
    selected_pages: List[int]
    markdown_content: str
    extracted_tables: List[Dict[str, Any]]
    extracted_images: List[Dict[str, bytes]]
    conversion_metadata: Dict[str, Any]
    converted_at: datetime

@dataclass
class EntityExtraction:
    """Extracted entity with context"""
    entity_name: str
    entity_type: str  # device_name, measurement, standard, regulation, etc.
    context: str
    page_reference: Optional[int] = None
    confidence: Optional[float] = None
    comments: str = ""

@dataclass
class DocumentSummary:
    """Comprehensive document summary"""
    document_name: str
    executive_summary: str
    detailed_sections: List[Dict[str, str]]  # Section title: content
    entities: List[EntityExtraction]
    key_findings: List[str]
    technical_specifications: Dict[str, Any]
    regulatory_information: Dict[str, Any]
    markdown_output: str
    word_count: int
    entity_count: int
    generated_at: datetime

@dataclass
class DocumentDifference:
    """Single difference between documents"""
    difference_id: int
    category: str  # content, formatting, structure, technical, regulatory
    title: str
    description: str
    version1_content: str
    version2_content: str
    version1_pages: List[int]
    version2_pages: List[int]
    severity: str  # critical, major, minor, informational
    comments: str

@dataclass
class DocumentComparison:
    """Complete document comparison result"""
    document1_name: str
    document2_name: str
    differences: List[DocumentDifference]
    total_differences: int
    summary_statistics: Dict[str, int]
    markdown_report: str
    generated_at: datetime
    comparison_method: str

@dataclass
class SessionState:
    """Application session state"""
    current_stage: WorkflowStage
    fda_search_result: Optional[FDASearchResult] = None
    uploaded_pdf: Optional[PDFDocument] = None
    markdown_conversion: Optional[MarkdownConversion] = None
    document_summary: Optional[DocumentSummary] = None
    comparison_pdf1: Optional[PDFDocument] = None
    comparison_pdf2: Optional[PDFDocument] = None
    document_comparison: Optional[DocumentComparison] = None
    llm_config: Optional[LLMConfig] = None
    processing_history: List[Dict[str, Any]] = field(default_factory=list)
```

### 3.2 Configuration Schema

```yaml
# config.yaml structure
application:
  name: "FDA Medical Device Intelligence System"
  version: "1.0.0"
  max_upload_size_mb: 50
  supported_pdf_formats: [".pdf"]
  
llm_providers:
  openai:
    default_model: "gpt-4-turbo-preview"
    models:
      - "gpt-4-turbo-preview"
      - "gpt-4"
      - "gpt-3.5-turbo"
    max_tokens: 4096
    temperature: 0.7
    
  anthropic:
    default_model: "claude-3-opus-20240229"
    models:
      - "claude-3-opus-20240229"
      - "claude-3-sonnet-20240229"
      - "claude-3-haiku-20240307"
    max_tokens: 4096
    temperature: 0.7
    
  gemini:
    default_model: "gemini-pro"
    models:
      - "gemini-pro"
      - "gemini-pro-vision"
    max_tokens: 4096
    temperature: 0.7

fda_api:
  base_url: "https://api.fda.gov/device"
  endpoints:
    510k: "/510k.json"
    classification: "/classification.json"
    recall: "/recall.json"
    enforcement: "/enforcement.json"
  rate_limit: 240  # requests per minute
  timeout: 30

pdf_processing:
  ocr_enabled: true
  ocr_language: "eng"
  default_page_selection: 10
  table_detection: true
  image_extraction: true
  
markdown_generation:
  target_word_count:
    min: 3000
    max: 4000
  table_format: "github"  # github, grid, simple
  include_toc: true
  heading_levels: 3
  
document_comparison:
  target_differences: 100
  similarity_threshold: 0.85
  ignore_whitespace: true
  ignore_case: false
  
summary_generation:
  min_entities: 20
  entity_types:
    - "device_name"
    - "model_number"
    - "manufacturer"
    - "measurement"
    - "material"
    - "standard"
    - "regulation"
    - "indication"
    - "contraindication"
    - "warning"
```

---

## 4. UI/UX & Theming

### 4.1 Design System

#### 4.1.1 Color Palette
```python
COLOR_PALETTE = {
    # Primary Colors
    'primary_blue': '#1f77b4',
    'primary_dark': '#0d3d5c',
    'primary_light': '#4a9fd8',
    
    # Semantic Colors
    'success_green': '#28a745',
    'warning_orange': '#ffc107',
    'error_red': '#dc3545',
    'info_cyan': '#17a2b8',
    
    # Background Colors
    'bg_primary': '#ffffff',
    'bg_secondary': '#f0f2f6',
    'bg_tertiary': '#e8f4f8',
    'bg_card': '#fafbfc',
    
    # Text Colors
    'text_primary': '#262730',
    'text_secondary': '#666666',
    'text_muted': '#999999',
    
    # Border Colors
    'border_light': '#e0e0e0',
    'border_medium': '#cccccc',
    'border_dark': '#999999',
    
    # Stage-specific Colors
    'stage_1': '#667eea',  # FDA Search
    'stage_2': '#f093fb',  # PDF to Markdown
    'stage_3': '#4facfe',  # Summary
    'stage_4': '#fa709a',  # Comparison
}
```

#### 4.1.2 Typography
```css
/* Typography Scale */
--font-family-primary: -apple-system, BlinkMacSystemFont, 'Segoe UI', Roboto, 'Helvetica Neue', Arial, sans-serif;
--font-family-mono: 'SF Mono', Monaco, 'Cascadia Code', 'Roboto Mono', Consolas, monospace;

--font-size-xs: 0.75rem;    /* 12px */
--font-size-sm: 0.875rem;   /* 14px */
--font-size-base: 1rem;     /* 16px */
--font-size-lg: 1.125rem;   /* 18px */
--font-size-xl: 1.25rem;    /* 20px */
--font-size-2xl: 1.5rem;    /* 24px */
--font-size-3xl: 2rem;      /* 32px */
--font-size-4xl: 2.5rem;    /* 40px */

--font-weight-normal: 400;
--font-weight-medium: 500;
--font-weight-semibold: 600;
--font-weight-bold: 700;

--line-height-tight: 1.25;
--line-height-normal: 1.5;
--line-height-relaxed: 1.75;
```

#### 4.1.3 Spacing System
```python
SPACING = {
    'xs': '0.25rem',   # 4px
    'sm': '0.5rem',    # 8px
    'md': '1rem',      # 16px
    'lg': '1.5rem',    # 24px
    'xl': '2rem',      # 32px
    '2xl': '3rem',     # 48px
    '3xl': '4rem',     # 64px
}
```

### 4.2 Layout Structure

#### 4.2.1 Main Application Layout
```
┌─────────────────────────────────────────────────────────────┐
│                      Header / Title Bar                      │
│              FDA Medical Device Intelligence System          │
├────────────┬────────────────────────────────────────────────┤
│            │                                                 │
│  Sidebar   │              Main Content Area                  │
│            │                                                 │
│  - Config  │  ┌──────────────────────────────────────────┐ │
│  - Stage   │  │                                          │ │
│    Select  │  │        Workflow Stage Content            │ │
│  - LLM     │  │                                          │ │
│    Config  │  │    (Tabs for multi-step processes)       │ │
│  - Status  │  │                                          │ │
│  - Export  │  └──────────────────────────────────────────┘ │
│            │                                                 │
│            │              Progress / Status                  │
│            │                                                 │
└────────────┴────────────────────────────────────────────────┘
```

#### 4.2.2 Custom CSS Styling
```python
CUSTOM_CSS = """
<style>
/* Main Application Styles */
.main-header {
    font-size: 2.5rem;
    font-weight: 700;
    color: #1f77b4;
    text-align: center;
    padding: 1.5rem 0;
    background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
    -webkit-background-clip: text;
    -webkit-text-fill-color: transparent;
    margin-bottom: 1rem;
}

.stage-container {
    background-color: #fafbfc;
    border-radius: 0.75rem;
    padding: 2rem;
    margin: 1rem 0;
    box-shadow: 0 2px 8px rgba(0,0,0,0.1);
}

.stage-header {
    display: flex;
    align-items: center;
    gap: 1rem;
    margin-bottom: 1.5rem;
    padding-bottom: 1rem;
    border-bottom: 2px solid #e0e0e0;
}

.stage-icon {
    font-size: 2rem;
    width: 60px;
    height: 60px;
    display: flex;
    align-items: center;
    justify-content: center;
    border-radius: 50%;
    background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
    color: white;
}

.stage-title {
    font-size: 1.75rem;
    font-weight: 600;
    color: #262730;
}

/* Card Components */
.info-card {
    background-color: #e8f4f8;
    border-left: 4px solid #17a2b8;
    padding: 1rem 1.5rem;
    border-radius: 0.5rem;
    margin: 1rem 0;
}

.warning-card {
    background-color: #fff3cd;
    border-left: 4px solid #ffc107;
    padding: 1rem 1.5rem;
    border-radius: 0.5rem;
    margin: 1rem 0;
}

.success-card {
    background-color: #d4edda;
    border-left: 4px solid #28a745;
    padding: 1rem 1.5rem;
    border-radius: 0.5rem;
    margin: 1rem 0;
}

.error-card {
    background-color: #f8d7da;
    border-left: 4px solid #dc3545;
    padding: 1rem 1.5rem;
    border-radius: 0.5rem;
    margin: 1rem 0;
}

/* Metric Cards */
.metric-card {
    background: white;
    padding: 1.5rem;
    border-radius: 0.75rem;
    text-align: center;
    box-shadow: 0 2px 6px rgba(0,0,0,0.08);
    transition: transform 0.2s, box-shadow 0.2s;
}

.metric-card:hover {
    transform: translateY(-2px);
    box-shadow: 0 4px 12px rgba(0,0,0,0.12);
}

.metric-value {
    font-size: 2.5rem;
    font-weight: 700;
    color: #1f77b4;
    margin-bottom: 0.5rem;
}

.metric-label {
    font-size: 1rem;
    color: #666666;
    text-transform: uppercase;
    letter-spacing: 0.05em;
}

/* Progress Indicators */
.progress-bar {
    width: 100%;
    height: 8px;
    background-color: #e0e0e0;
    border-radius: 4px;
    overflow: hidden;
    margin: 1rem 0;
}

.progress-fill {
    height: 100%;
    background: linear-gradient(90deg, #667eea 0%, #764ba2 100%);
    transition: width 0.3s ease;
}

/* Table Styling */
.custom-table {
    width: 100%;
    border-collapse: collapse;
    margin: 1rem 0;
    background: white;
    border-radius: 0.5rem;
    overflow: hidden;
    box-shadow: 0 2px 6px rgba(0,0,0,0.08);
}

.custom-table thead {
    background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
    color: white;
}

.custom-table th {
    padding: 1rem;
    text-align: left;
    font-weight: 600;
    font-size: 0.875rem;
    text-transform: uppercase;
    letter-spacing: 0.05em;
}

.custom-table td {
    padding: 1rem;
    border-bottom: 1px solid #e0e0e0;
}

.custom-table tbody tr:hover {
    background-color: #f8f9fa;
}

.custom-table tbody tr:last-child td {
    border-bottom: none;
}

/* Button Styles */
.primary-button {
    background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
    color: white;
    border: none;
    padding: 0.75rem 2rem;
    border-radius: 0.5rem;
    font-weight: 600;
    cursor: pointer;
    transition: transform 0.2s, box-shadow 0.2s;
}

.primary-button:hover {
    transform: translateY(-2px);
    box-shadow: 0 4px 12px rgba(102, 126, 234, 0.4);
}

.secondary-button {
    background: white;
    color: #667eea;
    border: 2px solid #667eea;
    padding: 0.75rem 2rem;
    border-radius: 0.5rem;
    font-weight: 600;
    cursor: pointer;
    transition: all 0.2s;
}

.secondary-button:hover {
    background: #667eea;
    color: white;
}

/* Code Blocks */
.code-block {
    background-color: #282c34;
    color: #abb2bf;
    padding: 1.5rem;
    border-radius: 0.5rem;
    font-family: 'SF Mono', Monaco, monospace;
    font-size: 0.875rem;
    line-height: 1.6;
    overflow-x: auto;
}

/* Sidebar Styling */
.sidebar-section {
    background: white;
    padding: 1rem;
    border-radius: 0.5rem;
    margin-bottom: 1rem;
    box-shadow: 0 1px 3px rgba(0,0,0,0.05);
}

.sidebar-header {
    font-size: 1.125rem;
    font-weight: 600;
    color: #262730;
    margin-bottom: 0.75rem;
    padding-bottom: 0.5rem;
    border-bottom: 2px solid #e0e0e0;
}

/* Workflow Step Indicator */
.step-indicator {
    display: flex;
    justify-content: space-between;
    margin: 2rem 0;
    position: relative;
}

.step-indicator::before {
    content: '';
    position: absolute;
    top: 20px;
    left: 0;
    right: 0;
    height: 2px;
    background: #e0e0e0;
    z-index: 0;
}

.step {
    display: flex;
    flex-direction: column;
    align-items: center;
    position: relative;
    z-index: 1;
}

.step-circle {
    width: 40px;
    height: 40px;
    border-radius: 50%;
    background: white;
    border: 3px solid #e0e0e0;
    display: flex;
    align-items: center;
    justify-content: center;
    font-weight: 600;
    margin-bottom: 0.5rem;
    transition: all 0.3s;
}

.step-circle.active {
    background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
    border-color: #667eea;
    color: white;
}

.step-circle.completed {
    background: #28a745;
    border-color: #28a745;
    color: white;
}

.step-label {
    font-size: 0.75rem;
    color: #666666;
    text-align: center;
    max-width: 100px;
}

/* Markdown Preview */
.markdown-preview {
    background: white;
    padding: 2rem;
    border-radius: 0.5rem;
    border: 1px solid #e0e0e0;
    max-height: 600px;
    overflow-y: auto;
}

.markdown-preview h1 {
    color: #1f77b4;
    border-bottom: 2px solid #e0e0e0;
    padding-bottom: 0.5rem;
    margin-bottom: 1rem;
}

.markdown-preview h2 {
    color: #262730;
    margin-top: 1.5rem;
    margin-bottom: 0.75rem;
}

.markdown-preview table {
    border-collapse: collapse;
    width: 100%;
    margin: 1rem 0;
}

.markdown-preview th,
.markdown-preview td {
    border: 1px solid #e0e0e0;
    padding: 0.75rem;
    text-align: left;
}

.markdown-preview th {
    background-color: #f0f2f6;
    font-weight: 600;
}

/* Loading Spinner */
.spinner {
    border: 4px solid #f3f3f3;
    border-top: 4px solid #667eea;
    border-radius: 50%;
    width: 40px;
    height: 40px;
    animation: spin 1s linear infinite;
    margin: 2rem auto;
}

@keyframes spin {
    0% { transform: rotate(0deg); }
    100% { transform: rotate(360deg); }
}

/* Responsive Design */
@media (max-width: 768px) {
    .main-header {
        font-size: 1.75rem;
        padding: 1rem 0;
    }
    
    .stage-container {
        padding: 1rem;
    }
    
    .metric-card {
        margin-bottom: 1rem;
    }
    
    .step-indicator {
        flex-direction: column;
        align-items: flex-start;
    }
}

/* Scrollbar Styling */
::-webkit-scrollbar {
    width: 8px;
    height: 8px;
}

::-webkit-scrollbar-track {
    background: #f1f1f1;
    border-radius: 4px;
}

::-webkit-scrollbar-thumb {
    background: #667eea;
    border-radius: 4px;
}

::-webkit-scrollbar-thumb:hover {
    background: #764ba2;
}
</style>
"""
```

### 4.3 Component Visual Patterns

#### 4.3.1 Stage Selection Interface
- **Layout**: Horizontal card grid (2x2 on desktop, vertical stack on mobile)
- **Each Card Contains**:
  - Large icon (emoji or SVG)
  - Stage number and title
  - Brief description (2-3 lines)
  - Status indicator (not started / in progress / completed)
  - Action button ("Start" / "Continue" / "Review")

#### 4.3.2 File Upload Component
- **Visual**: Drag-and-drop zone with dashed border
- **States**:
  - Default: Light gray with upload icon
  - Hover: Blue border highlight
  - Dragging: Solid blue border
  - Success: Green border with checkmark
  - Error: Red border with error message
- **Info Display**: Filename, size, page count after upload

#### 4.3.3 Progress Indicators
- **Processing**: Animated progress bar with percentage
- **Stages**: Step-by-step indicator showing completed/current/pending
- **Status Messages**: Toast notifications for success/error states

#### 4.3.4 Data Tables
- **Style**: Striped rows, hover effects
- **Features**: Sortable columns, pagination for >50 rows
- **Actions**: Export buttons (CSV, JSON, copy to clipboard)

---

## 5. Component Specifications

### 5.1 Main Application Component

```python
# main_app.py

class MedicalDeviceIntelligenceApp:
    """Main application controller"""
    
    def __init__(self):
        """Initialize application"""
        self.config = self.load_configuration()
        self.session_state = self.initialize_session_state()
        self.fda_service = FDASearchService(self.config)
        self.pdf_service = PDFProcessingService(self.config)
        self.llm_service = LLMService(self.config)
        self.comparison_service = DocumentComparisonService()
        
    def run(self):
        """Main application entry point"""
        self.setup_page_config()
        self.inject_custom_css()
        self.render_header()
        
        # Main layout
        sidebar = self.render_sidebar()
        main_content = self.render_main_content()
        
        # Handle workflow routing
        current_stage = st.session_state.get('current_stage', WorkflowStage.FDA_SEARCH)
        self.route_to_stage(current_stage)
    
    def setup_page_config(self):
        """Configure Streamlit page settings"""
        st.set_page_config(
            page_title="FDA Medical Device Intelligence System",
            page_icon="🏥",
            layout="wide",
            initial_sidebar_state="expanded",
            menu_items={
                'Get Help': 'https://docs.example.com',
                'Report a bug': 'https://github.com/example/issues',
                'About': 'FDA Medical Device Intelligence System v1.0.0'
            }
        )
    
    def initialize_session_state(self) -> SessionState:
        """Initialize or retrieve session state"""
        if 'session' not in st.session_state:
            st.session_state.session = SessionState(
                current_stage=WorkflowStage.FDA_SEARCH
            )
        return st.session_state.session
    
    def route_to_stage(self, stage: WorkflowStage):
        """Route to appropriate workflow stage"""
        stage_components = {
            WorkflowStage.FDA_SEARCH: FDASearchComponent,
            WorkflowStage.PDF_TO_MARKDOWN: PDFToMarkdownComponent,
            WorkflowStage.DOCUMENT_SUMMARY: DocumentSummaryComponent,
            WorkflowStage.DOCUMENT_COMPARISON: DocumentComparisonComponent
        }
        
        component_class = stage_components.get(stage)
        if component_class:
            component = component_class(
                llm_service=self.llm_service,
                session_state=self.session_state
            )
            component.render()
        else:
            st.error(f"Unknown stage: {stage}")
```

### 5.2 Stage 1: FDA Search Component

```python
class FDASearchComponent:
    """
    Component for FDA 510(k) device search and analysis
    
    Features:
    - Search by device name or 510(k) number
    - Fetch data from FDA API
    - Generate comprehensive markdown report (3000-4000 words)
    - Create minimum 5 structured tables
    - Export results
    """
    
    def __init__(self, llm_service: LLMService, session_state: SessionState):
        self.llm_service = llm_service
        self.session_state = session_state
        self.fda_service = FDASearchService()
        
    def render(self):
        """Render FDA search interface"""
        st.markdown("## 🔍 Stage 1: FDA Device Search & Analysis")
        
        # Search input section
        col1, col2 = st.columns([3, 1])
        
        with col1:
            search_type = st.radio(
                "Search Type",
                options=["Device Name", "510(k) Number", "Product Code"],
                horizontal=True
            )
            
            if search_type == "Device Name":
                search_query = st.text_input(
                    "Enter Device Name",
                    placeholder="e.g., Cardiac Pacemaker"
                )
            elif search_type == "510(k) Number":
                search_query = st.text_input(
                    "Enter 510(k) Number",
                    placeholder="e.g., K123456"
                )
            else:
                search_query = st.text_input(
                    "Enter Product Code",
                    placeholder="e.g., DQA"
                )
        
        with col2:
            st.markdown("<br>", unsafe_allow_html=True)
            search_button = st.button("🔍 Search FDA Database", type="primary", use_container_width=True)
        
        # Advanced search options
        with st.expander("⚙️ Advanced Search Options"):
            col1, col2, col3 = st.columns(3)
            with col1:
                device_class = st.multiselect(
                    "Device Class",
                    options=["Class I", "Class II", "Class III"],
                    default=None
                )
            with col2:
                date_from = st.date_input("Decision Date From", value=None)
            with col3:
                date_to = st.date_input("Decision Date To", value=None)
            
            include_predicates = st.checkbox("Include Predicate Device Information", value=True)
            include_adverse_events = st.checkbox("Include Related Adverse Events", value=False)
        
        # Execute search
        if search_button and search_query:
            self.execute_fda_search(
                search_query=search_query,
                search_type=search_type,
                filters={
                    'device_class': device_class,
                    'date_from': date_from,
                    'date_to': date_to,
                    'include_predicates': include_predicates,
                    'include_adverse_events': include_adverse_events
                }
            )
        
        # Display results if available
        if self.session_state.fda_search_result:
            self.display_search_results()
    
    def execute_fda_search(self, search_query: str, search_type: str, filters: Dict):
        """Execute FDA database search"""
        with st.spinner("🔍 Searching FDA database..."):
            try:
                # Step 1: Search FDA database
                progress_bar = st.progress(0)
                status_text = st.empty()
                
                status_text.text("Querying FDA API...")
                progress_bar.progress(20)
                
                fda_data = self.fda_service.search(
                    query=search_query,
                    search_type=search_type,
                    filters=filters
                )
                
                if not fda_data:
                    st.error("No results found in FDA database")
                    return
                
                # Step 2: Parse and structure data
                status_text.text("Processing FDA data...")
                progress_bar.progress(40)
                
                device = self.fda_service.parse_device_data(fda_data)
                
                # Step 3: Generate comprehensive report using LLM
                status_text.text("Generating comprehensive report (3000-4000 words)...")
                progress_bar.progress(60)
                
                report_prompt = self.build_report_generation_prompt(device, filters)
                markdown_report = self.llm_service.generate_completion(
                    prompt=report_prompt,
                    max_tokens=4500,
                    temperature=0.7
                )
                
                # Step 4: Extract and format tables
                status_text.text("Creating structured tables...")
                progress_bar.progress(80)
                
                tables = self.extract_tables_from_report(markdown_report)
                
                # Validate report meets requirements
                word_count = len(markdown_report.split())
                if word_count < 3000:
                    # Request expansion
                    expansion_prompt = f"The following report is {word_count} words. Please expand it to 3000-4000 words with more detailed analysis:\n\n{markdown_report}"
                    markdown_report = self.llm_service.generate_completion(expansion_prompt, max_tokens=4500)
                    word_count = len(markdown_report.split())
                
                if len(tables) < 5:
                    # Generate additional tables
                    additional_tables = self.generate_additional_tables(device, 5 - len(tables))
                    tables.extend(additional_tables)
                
                # Step 5: Create result object
                result = FDASearchResult(
                    device=device,
                    raw_data=fda_data,
                    markdown_report=markdown_report,
                    tables=tables,
                    word_count=word_count,
                    generated_at=datetime.now(),
                    search_query=search_query
                )
                
                self.session_state.fda_search_result = result
                
                progress_bar.progress(100)
                status_text.text("✅ Report generated successfully!")
                time.sleep(1)
                status_text.empty()
                progress_bar.empty()
                
                st.success(f"✅ Generated {word_count:,} word report with {len(tables)} tables")
                st.rerun()
                
            except Exception as e:
                st.error(f"Error during FDA search: {str(e)}")
                logging.error(f"FDA search error: {e}", exc_info=True)
    
    def build_report_generation_prompt(self, device: FDADevice, filters: Dict) -> str:
        """Build prompt for LLM to generate comprehensive report"""
        prompt = f"""
Generate a comprehensive FDA 510(k) device analysis report in markdown format.

DEVICE INFORMATION:
- Device Name: {device.device_name}
- 510(k) Number: {device.fda_510k_number}
- Product Code: {device.product_code}
- Device Class: {device.device_class}
- Applicant: {device.applicant}
- Decision Date: {device.decision_date}
- Intended Use: {device.intended_use}

REQUIREMENTS:
1. Report must be 3000-4000 words
2. Must include AT LEAST 5 detailed tables
3. Use professional medical device regulatory language
4. Include comprehensive analysis

REQUIRED SECTIONS:
1. Executive Summary (300-400 words)
2. Device Overview
   - Device description
   - Classification and regulation
   - Intended use and indications
3. Regulatory Pathway Analysis
   - 510(k) submission details
   - Predicate device comparison
   - Substantial equivalence determination
4. Technical Specifications (include detailed table)
5. Clinical Evaluation
   - Clinical data summary
   - Performance testing
   - Safety considerations
6. Regulatory Compliance
   - Standards compliance (include table)
   - Labeling requirements
7. Market Analysis (include table)
8. Risk Assessment (include table)
9. Post-Market Surveillance
10. Conclusion and Recommendations

TABLE REQUIREMENTS (minimum 5):
1. Device Specifications Table
2. Predicate Device Comparison Table
3. Standards Compliance Table
4. Performance Testing Results Table
5. Risk Analysis Table
6. [Additional tables as appropriate]

Format all tables in markdown with clear headers and organized data.
Use proper markdown heading levels (##, ###).
Include citations where appropriate.
"""
        return prompt
    
    def display_search_results(self):
        """Display FDA search results"""
        result = self.session_state.fda_search_result
        
        st.markdown("---")
        st.markdown("## 📊 Search Results")
        
        # Summary metrics
        col1, col2, col3, col4 = st.columns(4)
        
        with col1:
            st.markdown(
                f'<div class="metric-card">'
                f'<div class="metric-value">{result.word_count:,}</div>'
                f'<div class="metric-label">Words</div>'
                f'</div>',
                unsafe_allow_html=True
            )
        
        with col2:
            st.markdown(
                f'<div class="metric-card">'
                f'<div class="metric-value">{len(result.tables)}</div>'
                f'<div class="metric-label">Tables</div>'
                f'</div>',
                unsafe_allow_html=True
            )
        
        with col3:
            st.markdown(
                f'<div class="metric-card">'
                f'<div class="metric-value">{result.device.device_class or "N/A"}</div>'
                f'<div class="metric-label">Device Class</div>'
                f'</div>',
                unsafe_allow_html=True
            )
        
        with col4:
            st.markdown(
                f'<div class="metric-card">'
                f'<div class="metric-value">{result.device.fda_510k_number or "N/A"}</div>'
                f'<div class="metric-label">510(k) Number</div>'
                f'</div>',
                unsafe_allow_html=True
            )
        
        # Tabs for different views
        tab1, tab2, tab3, tab4 = st.tabs(["📄 Full Report", "📊 Tables", "🔍 Device Details", "💾 Export"])
        
        with tab1:
            st.markdown("### Full Markdown Report")
            st.markdown(result.markdown_report)
        
        with tab2:
            st.markdown("### Extracted Tables")
            for i, table in enumerate(result.tables, 1):
                st.markdown(f"#### Table {i}: {table.get('title', 'Untitled')}")
                df = pd.DataFrame(table.get('data', []))
                st.dataframe(df, use_container_width=True)
        
        with tab3:
            st.markdown("### Device Details")
            device_data = result.device.to_dict()
            
            for key, value in device_data.items():
                if value:
                    st.markdown(f"**{key.replace('_', ' ').title()}:** {value}")
        
        with tab4:
            st.markdown("### Export Options")
            
            col1, col2, col3 = st.columns(3)
            
            with col1:
                # Export as Markdown
                markdown_bytes = result.markdown_report.encode('utf-8')
                st.download_button(
                    label="📄 Download Markdown",
                    data=markdown_bytes,
                    file_name=f"fda_report_{result.device.fda_510k_number}_{datetime.now().strftime('%Y%m%d')}.md",
                    mime="text/markdown"
                )
            
            with col2:
                # Export as JSON
                json_data = json.dumps({
                    'device': result.device.to_dict(),
                    'report': result.markdown_report,
                    'tables': result.tables,
                    'metadata': {
                        'word_count': result.word_count,
                        'generated_at': result.generated_at.isoformat(),
                        'search_query': result.search_query
                    }
                }, indent=2)
                st.download_button(
                    label="📋 Download JSON",
                    data=json_data.encode('utf-8'),
                    file_name=f"fda_data_{result.device.fda_510k_number}_{datetime.now().strftime('%Y%m%d')}.json",
                    mime="application/json"
                )
            
            with col3:
                # Export tables as CSV
                if result.tables:
                    combined_csv = self.create_combined_csv(result.tables)
                    st.download_button(
                        label="📊 Download Tables (CSV)",
                        data=combined_csv,
                        file_name=f"fda_tables_{result.device.fda_510k_number}_{datetime.now().strftime('%Y%m%d')}.csv",
                        mime="text/csv"
                    )
```

### 5.3 Stage 2: PDF to Markdown Component

```python
class PDFToMarkdownComponent:
    """
    Component for converting PDF pages to markdown
    
    Features:
    - PDF upload with validation
    - Page range selection (default: first 10 pages)
    - OCR for scanned documents
    - Table extraction
    - Image extraction and embedding
    - Clean markdown output
    """
    
    def __init__(self, llm_service: LLMService, session_state: SessionState):
        self.llm_service = llm_service
        self.session_state = session_state
        self.pdf_service = PDFProcessingService()
        
    def render(self):
        """Render PDF to Markdown conversion interface"""
        st.markdown("## 📄 Stage 2: PDF to Markdown Conversion")
        
        # File upload
        uploaded_file = st.file_uploader(
            "Upload PDF Document",
            type=['pdf'],
            help="Maximum file size: 50MB"
        )
        
        if uploaded_file:
            # Process uploaded PDF
            if 'current_pdf' not in st.session_state or st.session_state.current_pdf.filename != uploaded_file.name:
                with st.spinner("📖 Processing PDF..."):
                    pdf_document = self.pdf_service.process_uploaded_pdf(uploaded_file)
                    st.session_state.current_pdf = pdf_document
                    self.session_state.uploaded_pdf = pdf_document
            
            pdf_doc = st.session_state.current_pdf
            
            # Display PDF info
            st.markdown(f"""
            <div class="info-card">
                <strong>📄 {pdf_doc.filename}</strong><br>
                📑 Total Pages: {pdf_doc.total_pages}<br>
                💾 File Size: {pdf_doc.file_size_bytes / 1024 / 1024:.2f} MB<br>
                📅 Uploaded: {pdf_doc.uploaded_at.strftime('%Y-%m-%d %H:%M:%S')}
            </div>
            """, unsafe_allow_html=True)
            
            # Page selection
            st.markdown("### Select Pages to Convert")
            
            col1, col2 = st.columns([2, 1])
            
            with col1:
                selection_mode = st.radio(
                    "Selection Mode",
                    options=["Range", "Specific Pages", "All Pages"],
                    horizontal=True
                )
                
                if selection_mode == "Range":
                    col_start, col_end = st.columns(2)
                    with col_start:
                        start_page = st.number_input(
                            "Start Page",
                            min_value=1,
                            max_value=pdf_doc.total_pages,
                            value=1
                        )
                    with col_end:
                        end_page = st.number_input(
                            "End Page",
                            min_value=start_page,
                            max_value=pdf_doc.total_pages,
                            value=min(10, pdf_doc.total_pages)
                        )
                    selected_pages = list(range(start_page, end_page + 1))
                
                elif selection_mode == "Specific Pages":
                    pages_input = st.text_input(
                        "Enter page numbers (comma-separated)",
                        placeholder="e.g., 1,3,5-8,10",
                        help="You can use ranges like 5-8"
                    )
                    selected_pages = self.parse_page_input(pages_input, pdf_doc.total_pages)
                
                else:  # All Pages
                    selected_pages = list(range(1, pdf_doc.total_pages + 1))
                    st.info(f"All {pdf_doc.total_pages} pages will be converted")
            
            with col2:
                st.markdown("#### Conversion Options")
                enable_ocr = st.checkbox("Enable OCR", value=True, help="For scanned documents")
                extract_tables = st.checkbox("Extract Tables", value=True)
                extract_images = st.checkbox("Extract Images", value=False)
                clean_formatting = st.checkbox("Clean Formatting", value=True)
            
            # Preview selected pages
            if selected_pages:
                st.markdown(f"**Selected Pages:** {', '.join(map(str, selected_pages[:20]))}{' ...' if len(selected_pages) > 20 else ''} (Total: {len(selected_pages)})")
            
            # Convert button
            if st.button("🔄 Convert to Markdown", type="primary", disabled=not selected_pages):
                self.execute_pdf_conversion(
                    pdf_doc=pdf_doc,
                    selected_pages=selected_pages,
                    options={
                        'enable_ocr': enable_ocr,
                        'extract_tables': extract_tables,
                        'extract_images': extract_images,
                        'clean_formatting': clean_formatting
                    }
                )
            
            # Display conversion results
            if self.session_state.markdown_conversion:
                self.display_conversion_results()
    
    def execute_pdf_conversion(self, pdf_doc: PDFDocument, selected_pages: List[int], options: Dict):
        """Execute PDF to markdown conversion"""
        progress_bar = st.progress(0)
        status_text = st.empty()
        
        try:
            markdown_content = []
            extracted_tables = []
            extracted_images = []
            
            total_pages = len(selected_pages)
            
            for idx, page_num in enumerate(selected_pages):
                status_text.text(f"Converting page {page_num} of {total_pages}...")
                progress = int((idx / total_pages) * 80)
                progress_bar.progress(progress)
                
                page = pdf_doc.pages[page_num - 1]
                
                # Extract text
                if options['enable_ocr'] and not page.text_content.strip():
                    # Use OCR for scanned pages
                    page_text = self.pdf_service.ocr_page(page)
                else:
                    page_text = page.text_content
                
                # Convert to markdown
                markdown_text = self.convert_text_to_markdown(page_text, page_num)
                markdown_content.append(markdown_text)
                
                # Extract tables
                if options['extract_tables'] and page.has_tables:
                    for table in page.tables:
                        table['page'] = page_num
                        extracted_tables.append(table)
                        # Add table to markdown
                        markdown_table = self.format_table_as_markdown(table)
                        markdown_content.append(f"\n\n{markdown_table}\n\n")
                
                # Extract images
                if options['extract_images'] and page.has_images and page.image_data:
                    image_info = {
                        'page': page_num,
                        'data': page.image_data
                    }
                    extracted_images.append(image_info)
            
            # Combine all markdown
            status_text.text("Finalizing markdown...")
            progress_bar.progress(90)
            
            full_markdown = "\n\n".join(markdown_content)
            
            # Clean formatting if requested
            if options['clean_formatting']:
                full_markdown = self.clean_markdown_formatting(full_markdown)
            
            # Use LLM to enhance markdown structure
            status_text.text("Enhancing markdown structure...")
            enhanced_markdown = self.enhance_markdown_with_llm(full_markdown)
            
            # Create conversion result
            conversion = MarkdownConversion(
                original_filename=pdf_doc.filename,
                selected_pages=selected_pages,
                markdown_content=enhanced_markdown,
                extracted_tables=extracted_tables,
                extracted_images=extracted_images,
                conversion_metadata={
                    'ocr_enabled': options['enable_ocr'],
                    'tables_extracted': len(extracted_tables),
                    'images_extracted': len(extracted_images),
                    'total_pages_converted': len(selected_pages)
                },
                converted_at=datetime.now()
            )
            
            self.session_state.markdown_conversion = conversion
            
            progress_bar.progress(100)
            status_text.text("✅ Conversion complete!")
            time.sleep(1)
            status_text.empty()
            progress_bar.empty()
            
            st.success(f"✅ Successfully converted {len(selected_pages)} pages to markdown")
            st.rerun()
            
        except Exception as e:
            st.error(f"Error during conversion: {str(e)}")
            logging.error(f"PDF conversion error: {e}", exc_info=True)
    
    def convert_text_to_markdown(self, text: str, page_num: int) -> str:
        """Convert plain text to markdown with proper formatting"""
        # Add page marker
        markdown = f"## Page {page_num}\n\n"
        
        # Basic markdown conversion
        lines = text.split('\n')
        
        for line in lines:
            line = line.strip()
            if not line:
                continue
            
            # Detect headings (heuristic: all caps or very short lines)
            if len(line) < 50 and line.isupper():
                markdown += f"### {line}\n\n"
            else:
                markdown += f"{line}\n\n"
        
        return markdown
    
    def enhance_markdown_with_llm(self, markdown: str) -> str:
        """Use LLM to enhance markdown structure and formatting"""
        prompt = f"""
Improve the following markdown document by:
1. Adding proper heading hierarchy (##, ###, ####)
2. Identifying and formatting lists
3. Identifying and emphasizing key terms with **bold**
4. Improving paragraph structure
5. Adding appropriate line breaks
6. Maintaining all original content

Original markdown:
{markdown[:3000]}  # Limit for token management

Return only the improved markdown without explanations.
"""
        
        try:
            enhanced = self.llm_service.generate_completion(
                prompt=prompt,
                max_tokens=4000,
                temperature=0.3
            )
            return enhanced
        except:
            return markdown  # Return original if enhancement fails
    
    def display_conversion_results(self):
        """Display markdown conversion results"""
        conversion = self.session_state.markdown_conversion
        
        st.markdown("---")
        st.markdown("## ✅ Conversion Results")
        
        # Metrics
        col1, col2, col3, col4 = st.columns(4)
        
        with col1:
            st.metric("Pages Converted", len(conversion.selected_pages))
        with col2:
            st.metric("Tables Extracted", len(conversion.extracted_tables))
        with col3:
            st.metric("Images Extracted", len(conversion.extracted_images))
        with col4:
            st.metric("Word Count", len(conversion.markdown_content.split()))
        
        # Tabs
        tab1, tab2, tab3, tab4 = st.tabs(["📄 Markdown", "📊 Tables", "🖼️ Images", "💾 Export"])
        
        with tab1:
            st.markdown("### Converted Markdown")
            st.markdown(conversion.markdown_content)
        
        with tab2:
            if conversion.extracted_tables:
                st.markdown("### Extracted Tables")
                for i, table in enumerate(conversion.extracted_tables, 1):
                    st.markdown(f"#### Table {i} (Page {table['page']})")
                    df = pd.DataFrame(table.get('data', []))
                    st.dataframe(df, use_container_width=True)
            else:
                st.info("No tables extracted")
        
        with tab3:
            if conversion.extracted_images:
                st.markdown("### Extracted Images")
                cols = st.columns(3)
                for i, img in enumerate(conversion.extracted_images):
                    with cols[i % 3]:
                        st.image(img['data'], caption=f"Page {img['page']}")
            else:
                st.info("No images extracted")
        
        with tab4:
            st.markdown("### Export Options")
            
            col1, col2 = st.columns(2)
            
            with col1:
                st.download_button(
                    label="📄 Download Markdown",
                    data=conversion.markdown_content.encode('utf-8'),
                    file_name=f"{conversion.original_filename.replace('.pdf', '')}_converted.md",
                    mime="text/markdown"
                )
            
            with col2:
                if conversion.extracted_tables:
                    combined_csv = self.create_combined_csv(conversion.extracted_tables)
                    st.download_button(
                        label="📊 Download Tables (CSV)",
                        data=combined_csv,
                        file_name=f"{conversion.original_filename.replace('.pdf', '')}_tables.csv",
                        mime="text/csv"
                    )
```

### 5.4 Stage 3: Document Summary Component

```python
class DocumentSummaryComponent:
    """
    Component for generating comprehensive document summaries
    
    Features:
    - Generate 3000-4000 word summaries
    - Extract minimum 20 entities with context
    - Create structured tables
    - Identify key findings
    - Extract technical specifications
    """
    
    def __init__(self, llm_service: LLMService, session_state: SessionState):
        self.llm_service = llm_service
        self.session_state = session_state
        
    def render(self):
        """Render document summary interface"""
        st.markdown("## 📊 Stage 3: Document Summarization")
        
        # Check if markdown conversion is available
        if not self.session_state.markdown_conversion:
            st.warning("⚠️ Please complete Stage 2 (PDF to Markdown) first")
            return
        
        markdown_doc = self.session_state.markdown_conversion
        
        # Display source document info
        st.markdown(f"""
        <div class="info-card">
            <strong>📄 Source Document: {markdown_doc.original_filename}</strong><br>
            📑 Pages: {len(markdown_doc.selected_pages)}<br>
            📝 Word Count: {len(markdown_doc.markdown_content.split()):,}
        </div>
        """, unsafe_allow_html=True)
        
        # Summary options
        st.markdown("### Summary Configuration")
        
        col1, col2 = st.columns(2)
        
        with col1:
            target_word_count = st.slider(
                "Target Word Count",
                min_value=3000,
                max_value=5000,
                value=3500,
                step=100
            )
            
            min_entities = st.number_input(
                "Minimum Entities to Extract",
                min_value=20,
                max_value=100,
                value=20
            )
        
        with col2:
            focus_areas = st.multiselect(
                "Focus Areas",
                options=[
                    "Technical Specifications",
                    "Regulatory Information",
                    "Clinical Data",
                    "Safety Information",
                    "Performance Characteristics",
                    "Indications for Use",
                    "Contraindications",
                    "Warnings and Precautions"
                ],
                default=["Technical Specifications", "Regulatory Information"]
            )
            
            include_diagrams = st.checkbox("Analyze Diagrams/Figures", value=True)
        
        # Generate summary button
        if st.button("📊 Generate Summary", type="primary"):
            self.execute_summarization(
                markdown_doc=markdown_doc,
                target_word_count=target_word_count,
                min_entities=min_entities,
                focus_areas=focus_areas,
                include_diagrams=include_diagrams
            )
        
        # Display summary results
        if self.session_state.document_summary:
            self.display_summary_results()
    
    def execute_summarization(self, markdown_doc: MarkdownConversion, target_word_count: int,
                             min_entities: int, focus_areas: List[str], include_diagrams: bool):
        """Execute document summarization"""
        progress_bar = st.progress(0)
        status_text = st.empty()
        
        try:
            # Step 1: Extract entities
            status_text.text("🔍 Extracting entities...")
            progress_bar.progress(20)
            
            entities = self.extract_entities(markdown_doc.markdown_content, min_entities)
            
            # Step 2: Generate executive summary
            status_text.text("📝 Generating executive summary...")
            progress_bar.progress(40)
            
            executive_summary = self.generate_executive_summary(
                markdown_doc.markdown_content,
                focus_areas
            )
            
            # Step 3: Generate detailed sections
            status_text.text("📄 Generating detailed sections...")
            progress_bar.progress(60)
            
            detailed_sections = self.generate_detailed_sections(
                markdown_doc.markdown_content,
                focus_areas,
                target_word_count
            )
            
            # Step 4: Extract technical specifications
            status_text.text("🔧 Extracting technical specifications...")
            progress_bar.progress(75)
            
            technical_specs = self.extract_technical_specifications(markdown_doc.markdown_content)
            
            # Step 5: Identify key findings
            status_text.text("💡 Identifying key findings...")
            progress_bar.progress(85)
            
            key_findings = self.identify_key_findings(markdown_doc.markdown_content)
            
            # Step 6: Generate final markdown
            status_text.text("📊 Formatting final report...")
            progress_bar.progress(95)
            
            final_markdown = self.compile_summary_markdown(
                executive_summary=executive_summary,
                detailed_sections=detailed_sections,
                entities=entities,
                technical_specs=technical_specs,
                key_findings=key_findings,
                document_name=markdown_doc.original_filename
            )
            
            # Create summary object
            summary = DocumentSummary(
                document_name=markdown_doc.original_filename,
                executive_summary=executive_summary,
                detailed_sections=detailed_sections,
                entities=entities,
                key_findings=key_findings,
                technical_specifications=technical_specs,
                regulatory_information={},  # Extracted from sections
                markdown_output=final_markdown,
                word_count=len(final_markdown.split()),
                entity_count=len(entities),
                generated_at=datetime.now()
            )
            
            self.session_state.document_summary = summary
            
            progress_bar.progress(100)
            status_text.text("✅ Summary generated successfully!")
            time.sleep(1)
            status_text.empty()
            progress_bar.empty()
            
            st.success(f"✅ Generated {summary.word_count:,} word summary with {summary.entity_count} entities")
            st.rerun()
            
        except Exception as e:
            st.error(f"Error during summarization: {str(e)}")
            logging.error(f"Summarization error: {e}", exc_info=True)
    
    def extract_entities(self, content: str, min_count: int) -> List[EntityExtraction]:
        """Extract entities from document using LLM"""
        prompt = f"""
Analyze the following document and extract at least {min_count} key entities.

For each entity provide:
1. Entity name
2. Entity type (device_name, model_number, manufacturer, measurement, material, standard, regulation, indication, contraindication, warning)
3. Context (surrounding text that provides context)
4. Comments (any relevant notes)

Document excerpt:
{content[:4000]}

Return entities in JSON format:
[
  {{
    "entity_name": "...",
    "entity_type": "...",
    "context": "...",
    "comments": "..."
  }},
  ...
]
"""
        
        response = self.llm_service.generate_completion(prompt, max_tokens=3000)
        
        try:
            entities_data = json.loads(response)
            entities = []
            
            for entity_dict in entities_data:
                entity = EntityExtraction(
                    entity_name=entity_dict.get('entity_name', ''),
                    entity_type=entity_dict.get('entity_type', ''),
                    context=entity_dict.get('context', ''),
                    comments=entity_dict.get('comments', '')
                )
                entities.append(entity)
            
            # If not enough entities, request more
            while len(entities) < min_count:
                additional_prompt = f"Extract {min_count - len(entities)} more entities from the document, different from these: {[e.entity_name for e in entities]}"
                additional_response = self.llm_service.generate_completion(additional_prompt)
                additional_entities_data = json.loads(additional_response)
                
                for entity_dict in additional_entities_data:
                    entity = EntityExtraction(
                        entity_name=entity_dict.get('entity_name', ''),
                        entity_type=entity_dict.get('entity_type', ''),
                        context=entity_dict.get('context', ''),
                        comments=entity_dict.get('comments', '')
                    )
                    entities.append(entity)
            
            return entities[:min_count]  # Return exactly min_count entities
            
        except json.JSONDecodeError:
            # Fallback: parse text response
            return self.parse_entities_from_text(response, min_count)
    
    def generate_executive_summary(self, content: str, focus_areas: List[str]) -> str:
        """Generate executive summary"""
        prompt = f"""
Generate a comprehensive executive summary (300-500 words) for the following document.

Focus on these areas: {', '.join(focus_areas)}

Document:
{content[:3000]}

The summary should:
1. Provide high-level overview
2. Highlight key points
3. Mention critical specifications or requirements
4. Be written for technical and regulatory audiences
"""
        
        return self.llm_service.generate_completion(prompt, max_tokens=800)
    
    def generate_detailed_sections(self, content: str, focus_areas: List[str], 
                                   target_word_count: int) -> List[Dict[str, str]]:
        """Generate detailed sections for summary"""
        sections = []
        words_per_section = (target_word_count - 500) // len(focus_areas)  # Reserve 500 for exec summary
        
        for area in focus_areas:
            prompt = f"""
Write a detailed section about "{area}" based on this document ({words_per_section} words).

Document:
{content[:4000]}

Include specific details, data, and technical information relevant to {area}.
"""
            
            section_content = self.llm_service.generate_completion(prompt, max_tokens=int(words_per_section * 1.5))
            
            sections.append({
                'title': area,
                'content': section_content
            })
        
        return sections
    
    def compile_summary_markdown(self, executive_summary: str, detailed_sections: List[Dict[str, str]],
                                entities: List[EntityExtraction], technical_specs: Dict[str, Any],
                                key_findings: List[str], document_name: str) -> str:
        """Compile all components into final markdown summary"""
        markdown = f"""# Document Summary: {document_name}

*Generated: {datetime.now().strftime('%Y-%m-%d %H:%M:%S')}*

---

## Executive Summary

{executive_summary}

---

## Key Findings

"""
        
        for i, finding in enumerate(key_findings, 1):
            markdown += f"{i}. {finding}\n"
        
        markdown += "\n---\n\n"
        
        # Add detailed sections
        for section in detailed_sections:
            markdown += f"## {section['title']}\n\n{section['content']}\n\n---\n\n"
        
        # Add technical specifications table
        if technical_specs:
            markdown += "## Technical Specifications\n\n"
            markdown += "| Specification | Value | Notes |\n"
            markdown += "|---------------|-------|-------|\n"
            
            for spec, value in technical_specs.items():
                markdown += f"| {spec} | {value.get('value', 'N/A')} | {value.get('notes', '')} |\n"
            
            markdown += "\n---\n\n"
        
        # Add entities table
        markdown += "## Extracted Entities\n\n"
        markdown += "| # | Entity Name | Type | Context | Comments |\n"
        markdown += "|---|-------------|------|---------|----------|\n"
        
        for i, entity in enumerate(entities, 1):
            context_short = entity.context[:100] + "..." if len(entity.context) > 100 else entity.context
            markdown += f"| {i} | {entity.entity_name} | {entity.entity_type} | {context_short} | {entity.comments} |\n"
        
        return markdown
    
    def display_summary_results(self):
        """Display document summary results"""
        summary = self.session_state.document_summary
        
        st.markdown("---")
        st.markdown("## ✅ Summary Generated")
        
        # Metrics
        col1, col2, col3, col4 = st.columns(4)
        
        with col1:
            st.metric("Word Count", f"{summary.word_count:,}")
        with col2:
            st.metric("Entities Extracted", summary.entity_count)
        with col3:
            st.metric("Sections", len(summary.detailed_sections))
        with col4:
            st.metric("Key Findings", len(summary.key_findings))
        
        # Tabs
        tab1, tab2, tab3, tab4 = st.tabs(["📄 Full Summary", "🔍 Entities", "💡 Key Findings", "💾 Export"])
        
        with tab1:
            st.markdown(summary.markdown_output)
        
        with tab2:
            st.markdown("### Extracted Entities")
            
            # Entity type filter
            entity_types = list(set(e.entity_type for e in summary.entities))
            selected_type = st.selectbox("Filter by Type", ["All"] + entity_types)
            
            filtered_entities = summary.entities if selected_type == "All" else [
                e for e in summary.entities if e.entity_type == selected_type
            ]
            
            # Display as table
            entity_data = []
            for i, entity in enumerate(filtered_entities, 1):
                entity_data.append({
                    "#": i,
                    "Entity Name": entity.entity_name,
                    "Type": entity.entity_type,
                    "Context": entity.context[:100] + "...",
                    "Comments": entity.comments
                })
            
            df = pd.DataFrame(entity_data)
            st.dataframe(df, use_container_width=True)
        
        with tab3:
            st.markdown("### Key Findings")
            for i, finding in enumerate(summary.key_findings, 1):
                st.markdown(f"**{i}.** {finding}")
        
        with tab4:
            st.markdown("### Export Options")
            
            col1, col2 = st.columns(2)
            
            with col1:
                st.download_button(
                    label="📄 Download Summary (Markdown)",
                    data=summary.markdown_output.encode('utf-8'),
                    file_name=f"{summary.document_name}_summary_{datetime.now().strftime('%Y%m%d')}.md",
                    mime="text/markdown"
                )
            
            with col2:
                json_data = json.dumps({
                    'document_name': summary.document_name,
                    'executive_summary': summary.executive_summary,
                    'detailed_sections': summary.detailed_sections,
                    'entities': [vars(e) for e in summary.entities],
                    'key_findings': summary.key_findings,
                    'metadata': {
                        'word_count': summary.word_count,
                        'entity_count': summary.entity_count,
                        'generated_at': summary.generated_at.isoformat()
                    }
                }, indent=2)
                
                st.download_button(
                    label="📋 Download Data (JSON)",
                    data=json_data.encode('utf-8'),
                    file_name=f"{summary.document_name}_data_{datetime.now().strftime('%Y%m%d')}.json",
                    mime="application/json"
                )
```

### 5.5 Stage 4: Document Comparison Component

```python
class DocumentComparisonComponent:
    """
    Component for comparing two document versions
    
    Features:
    - Upload two PDF versions
    - Identify minimum 100 differences
    - Categorize differences
    - Provide page references
    - Generate comparison report
    """
    
    def __init__(self, llm_service: LLMService, session_state: SessionState):
        self.llm_service = llm_service
        self.session_state = session_state
        self.pdf_service = PDFProcessingService()
        self.comparison_service = DocumentComparisonService()
        
    def render(self):
        """Render document comparison interface"""
        st.markdown("## 🔄 Stage 4: Document Comparison")
        
        # Upload both documents
        col1, col2 = st.columns(2)
        
        with col1
