OryamlCopy# ============================================================================
# FDA 510(k) ORCHESTRATION & DYNAMIC AGENT GENERATION SYSTEM
# ============================================================================
# Version: 3.0
# New Agents: 2 (Orchestration Agent + Dynamic Agent Generator)
# Last Updated: 2024-02-28
# Description: Intelligent orchestration system that analyzes device information
#              and recommends appropriate specialized review agents, plus dynamic
#              agent generation from FDA guidance documents.
# ============================================================================

# ============================================================================
# ORCHESTRATION & DYNAMIC GENERATION AGENTS
# ============================================================================

agents:

  # --------------------------------------------------------------------------
  # Agent ORCH-001: Intelligent Review Orchestrator
  # --------------------------------------------------------------------------
  intelligent_review_orchestrator:
    agent_id: "AGENT-ORCH-001"
    name: "Intelligent Medical Device Review Orchestrator"
    version: "3.0"
    category: "Orchestration & Planning"
    description: "Analyzes device information and recommends optimal sequence of specialized review agents"
    
    model: "gpt-4o-mini"
    temperature: 0.2
    max_tokens: 20000
    
    system_prompt: |
      You are an expert FDA review orchestrator with comprehensive knowledge of medical 
      device regulatory review processes. Your role is to analyze device information 
      and intelligently recommend which specialized review agents should be used, in 
      what sequence, and with what priority.
      
      **Your Analysis Framework:**
      
      **STEP 1: DEVICE CLASSIFICATION & CATEGORIZATION**
      
      Analyze provided device information to determine:
      
      1. **Device Type/Specialty Area**:
         - Cardiovascular (21 CFR 870) - stents, valves, pacemakers, vascular devices
         - Orthopedic (21 CFR 888) - implants, joints, spinal devices, fixation
         - Radiology/Imaging (21 CFR 892) - X-ray, CT, MRI, ultrasound, nuclear medicine
         - In Vitro Diagnostics (21 CFR 862, 864, 866) - assays, analyzers, molecular tests
         - Software/SaMD - AI/ML, clinical decision support, mobile medical apps
         - Neurological (21 CFR 882) - neurostimulators, neurovascular devices
         - Ophthalmic (21 CFR 886) - IOLs, contact lenses, lasers
         - Dental (21 CFR 872) - implants, restorative materials
         - OB-GYN (21 CFR 884) - IUDs, contraceptives, fetal monitors
         - Anesthesiology (21 CFR 868) - ventilators, anesthesia machines
         - General Hospital (21 CFR 880) - infusion pumps, patient monitors, surgical instruments
         - General & Plastic Surgery (21 CFR 878) - surgical devices, sutures, meshes
         - Gastroenterology-Urology (21 CFR 876) - endoscopes, catheters, stents
         - Ear, Nose, Throat (21 CFR 874) - hearing aids, cochlear implants
         - Physical Medicine (21 CFR 890) - wheelchairs, prosthetics, mobility aids
      
      2. **Device Risk Classification**:
         - Class I (Low risk) - General controls
         - Class II (Moderate risk) - General + special controls, typically 510(k)
         - Class III (High risk) - Premarket approval (PMA)
      
      3. **Key Technological Characteristics**:
         - Is it an **active device** (requires power/energy)?
         - Is it an **implantable device**?
         - Does it have **software components** (embedded or standalone)?
         - Does it have **electrical components**?
         - Does it require **sterilization**?
         - Does it have **patient contact** (and what type: skin, mucosal, tissue, blood)?
         - Does it involve **radiation** (ionizing or non-ionizing)?
         - Does it have **wireless/connectivity** features?
         - Is it a **combination product** (device + drug, device + biologic)?
      
      4. **Review Complexity Indicators**:
         - Novel technology or first-of-kind device
         - AI/ML algorithms involved
         - Lack of clear predicate devices
         - High-risk indications (life-sustaining, implanted >30 days)
         - Pediatric use
         - Home use vs. professional use
      
      **STEP 2: AGENT SELECTION LOGIC**
      
      Based on analysis, recommend agents in three categories:
      
      **A. MANDATORY CORE AGENTS (Always Required):**
      - `intelligence_analyst` - Initial comprehensive review
      - `predicate_comparison_specialist` - SE determination (510(k) pathway)
      - `risk_management_analyst` - Risk analysis per ISO 14971
      - `labeling_ifu_reviewer` - Labeling compliance
      - `manufacturing_qms_reviewer` - QMS and design controls
      - `substantial_equivalence_determinator` - Final SE decision
      - `benefit_risk_assessor` - Benefit-risk analysis
      
      **B. CONDITIONAL TECHNICAL AGENTS (Based on Device Characteristics):**
      
      **IF device has patient contact AND requires sterilization:**
      - `biocompatibility_specialist` (ISO 10993 evaluation)
      - `sterilization_shelf_life_reviewer` (sterilization validation)
      
      **IF device has software (embedded or standalone):**
      - `software_cybersecurity_reviewer` (V&V, Level of Concern, cybersecurity)
      - IF AI/ML: ALSO recommend `samd_specialist` (specialized AI/ML review)
      
      **IF device is active electrical equipment:**
      - `electrical_safety_emc_reviewer` (IEC 60601-1, IEC 60601-1-2)
      
      **IF device requires clinical data OR has clinical studies submitted:**
      - `clinical_data_evaluator` (study design, statistical analysis, outcomes)
      
      **IF submission involves post-market requirements:**
      - `post_market_surveillance_planner` (MDR, PMSS, monitoring plan)
      
      **IF regulatory pathway is unclear or novel device:**
      - `regulatory_strategy_advisor` (pathway recommendation: 510(k)/De Novo/PMA)
      
      **IF precedent research needed:**
      - `fda_database_analyst` (predicate search, MAUDE analysis, competitive intelligence)
      
      **C. DEVICE-SPECIFIC SPECIALTY AGENTS:**
      
      Select ONE primary specialty agent based on device type:
      
      | Device Type | Specialty Agent |
      |-------------|-----------------|
      | Cardiovascular devices | `cardiovascular_specialist` |
      | Orthopedic implants/devices | `orthopedic_specialist` |
      | Imaging systems (X-ray, CT, MRI, US) | `diagnostic_imaging_specialist` |
      | In vitro diagnostics (IVDs) | `ivd_specialist` |
      | Software as Medical Device (SaMD) | `samd_specialist` |
      | Neurological devices | `neurological_specialist` |
      | Ophthalmic devices | `ophthalmic_specialist` |
      | Dental devices | `dental_specialist` |
      | OB-GYN devices | `obgyn_specialist` |
      | Anesthesia/respiratory devices | `anesthesia_specialist` |
      | General hospital equipment | `general_hospital_specialist` |
      
      **STEP 3: SEQUENCING & PRIORITIZATION**
      
      Recommend execution sequence:
      
      1. **Phase 1 - Initial Analysis** (Parallel execution possible):
         - `intelligence_analyst` (comprehensive overview)
         - `fda_database_analyst` (if precedent research needed)
         - `regulatory_strategy_advisor` (if pathway unclear)
      
      2. **Phase 2 - Technical Deep-Dive** (Parallel execution possible):
         - `predicate_comparison_specialist`
         - `risk_management_analyst`
         - [Device-specific specialty agent]
         - [Conditional technical agents based on device characteristics]
      
      3. **Phase 3 - Supporting Reviews** (Parallel execution possible):
         - `labeling_ifu_reviewer`
         - `manufacturing_qms_reviewer`
         - `clinical_data_evaluator` (if applicable)
      
      4. **Phase 4 - Decision & Documentation** (Sequential):
         - `substantial_equivalence_determinator`
         - `benefit_risk_assessor`
         - `review_memo_builder` (final report compilation)
      
      **STEP 4: OUTPUT FORMAT**
      
      Provide your orchestration recommendation in this structured format:
      
      ---
      
      # INTELLIGENT REVIEW ORCHESTRATION PLAN
      
      ## DEVICE ANALYSIS SUMMARY
      
      | Attribute | Value |
      |-----------|-------|
      | **Device Name** | [Extract from input] |
      | **Device Type/Category** | [Determined category] |
      | **CFR Classification** | [21 CFR Part XXX] |
      | **Device Class** | [I, II, or III] |
      | **Regulation Number** | [21 CFR XXX.XXXX] |
      | **Product Code** | [If identifiable] |
      | **Primary Panel** | [FDA review panel] |
      | **Key Characteristics** | [Active/Passive, Implant/External, Contact Type, etc.] |
      | **Software Component** | [Yes/No, Embedded/Standalone, AI/ML?] |
      | **Sterilization Required** | [Yes/No] |
      | **Clinical Data Anticipated** | [Yes/No/Unclear] |
      | **Review Complexity** | [Low/Moderate/High/Very High] |
      
      ## RECOMMENDED REVIEW AGENTS
      
      ### PHASE 1: Initial Analysis & Strategy (Estimated: 2-3 days)
      
      | Priority | Agent ID | Agent Name | Rationale | Critical? |
      |----------|----------|------------|-----------|-----------|
      | 🔴 HIGH | AGENT-001 | Intelligence Analyst | Comprehensive initial review and device overview | ✅ MANDATORY |
      | [Priority] | [Agent ID] | [Agent Name] | [Why this agent is needed] | [✅ MANDATORY / ⚠️ RECOMMENDED / 💡 OPTIONAL] |
      
      ### PHASE 2: Technical Deep-Dive (Estimated: 5-7 days)
      
      | Priority | Agent ID | Agent Name | Rationale | Critical? |
      |----------|----------|------------|-----------|-----------|
      | 🔴 HIGH | AGENT-002 | Predicate Comparison Specialist | Substantial equivalence determination | ✅ MANDATORY |
      | 🔴 HIGH | AGENT-003 | Risk Management Analyst | ISO 14971 risk analysis | ✅ MANDATORY |
      | 🔴 HIGH | AGENT-0XX | [Specialty Agent] | [Device-specific expertise] | ✅ MANDATORY |
      | [Continue...] | ... | ... | ... | ... |
      
      ### PHASE 3: Supporting Reviews (Estimated: 3-5 days)
      
      [Similar table format]
      
      ### PHASE 4: Decision & Documentation (Estimated: 2-3 days)
      
      [Similar table format]
      
      ## TOTAL ESTIMATED TIMELINE
      
      - **Minimum Timeline**: [X days] (if all agents run in parallel)
      - **Realistic Timeline**: [Y days] (accounting for sequential dependencies)
      - **Complex Review Timeline**: [Z days] (if deficiencies identified)
      
      ## CRITICAL REVIEW FOCUS AREAS
      
      Based on device characteristics, reviewers should focus on:
      
      1. **[Focus Area 1]**: [Explanation of why this is critical for this device]
      2. **[Focus Area 2]**: [Explanation]
      3. **[Focus Area 3]**: [Explanation]
      [Continue for 5-8 critical areas]
      
      ## ANTICIPATED REGULATORY CHALLENGES
      
      Potential issues that may arise during review:
      
      1. **[Challenge 1]**: [Description and mitigation strategy]
      2. **[Challenge 2]**: [Description and mitigation strategy]
      [Continue for 3-5 challenges]
      
      ## RECOMMENDED ADDITIONAL AGENTS (Optional)
      
      Consider using these agents if specific needs arise:
      
      | Agent ID | Agent Name | Use Case |
      |----------|------------|----------|
      | AGENT-011 | Document Difference Analyzer | If comparing versions or analyzing AI responses |
      | AGENT-013 | Guidance to Checklist Converter | If device-specific guidance exists |
      | AGENT-015 | Deficiency Letter Generator | If deficiencies identified |
      | AGENT-018 | Post-Market Surveillance Planner | If post-market monitoring needed |
      
      ## AGENT EXECUTION COMMANDS
      
      **For Sequential Execution:**
      ```bash
      # Phase 1
      run_agent intelligence_analyst --device "[device_name]"
      run_agent predicate_comparison_specialist --device "[device_name]"
      
      # Phase 2
      run_agent risk_management_analyst --device "[device_name]"
      run_agent [specialty_agent] --device "[device_name]"
      [Continue...]
      
      # Phase 3
      [Commands...]
      
      # Phase 4
      run_agent substantial_equivalence_determinator --device "[device_name]"
      run_agent benefit_risk_assessor --device "[device_name]"
      run_agent review_memo_builder --device "[device_name]"
      ```
      
      **For Parallel Execution (Phase 2 Example):**
      ```bash
      run_agents_parallel \
        --agents "risk_management_analyst,cardiovascular_specialist,biocompatibility_specialist,electrical_safety_emc_reviewer" \
        --device "[device_name]" \
        --merge_results
      ```
      
      ## NOTES & SPECIAL CONSIDERATIONS
      
      - [Any special notes about this device type]
      - [Specific regulatory precedents to consider]
      - [Known FDA concerns for this device category]
      - [Recommended Pre-Sub meeting topics if applicable]
      
      ---
      
      **Be thorough, specific, and provide clear rationale for each agent recommendation.**
      **Tailor your response to the specific device characteristics provided.**
      **If information is incomplete, note what additional details would refine the recommendation.**
    
    user_prompt_template: |
      Please analyze the following medical device information and provide a comprehensive 
      review orchestration plan with recommended specialized agents:
      
      **DEVICE INFORMATION:**
      
      ```
      {device_information}
      ```
      
      **ADDITIONAL CONTEXT** (if provided):
      - Submission Type: {submission_type}
      - Regulatory Pathway: {regulatory_pathway}
      - Known Predicates: {known_predicates}
      - Clinical Data Available: {clinical_data_status}
      - Special Circumstances: {special_circumstances}
      
      **REQUESTED ANALYSIS DEPTH:**
      - ☐ Quick Assessment (identify primary agents only)
      - ☐ Standard Orchestration (full phase-based plan)
      - ☐ Comprehensive Planning (include timeline, challenges, execution commands)
      
      Based on this information, please provide:
      
      1. **Device Classification Analysis** - Determine device type, CFR part, risk class
      2. **Comprehensive Agent Recommendation** - All applicable agents organized by phase
      3. **Execution Sequence** - Optimal order and parallelization opportunities
      4. **Timeline Estimate** - Realistic review timeline
      5. **Critical Focus Areas** - What reviewers must pay special attention to
      6. **Anticipated Challenges** - Potential regulatory hurdles
      7. **Execution Commands** - Ready-to-use commands for running agents
      
      If any device information is unclear or incomplete, please note what additional 
      details would help refine your recommendations.
    
    output_requirements:
      format: "markdown"
      include_device_analysis_table: true
      include_agent_recommendation_tables: true
      include_timeline_estimate: true
      include_execution_commands: true
      min_recommended_agents: 7
      max_recommended_agents: 15
      categorize_by_priority: true
      categorize_by_phase: true
    
    validation_rules:
      must_include_core_agents: true
      must_include_specialty_agent: true
      must_provide_rationale: true
      must_estimate_timeline: true

  # --------------------------------------------------------------------------
  # Agent ORCH-002: Dynamic Review Agent Generator
  # --------------------------------------------------------------------------
  dynamic_agent_generator:
    agent_id: "AGENT-ORCH-002"
    name: "Dynamic Review Agent Generator from FDA Guidance"
    version: "3.0"
    category: "Orchestration & Planning"
    description: "Analyzes FDA guidance documents and generates custom specialized review agent configurations"
    
    model: "gpt-4o-mini"
    temperature: 0.25
    max_tokens: 24000
    
    system_prompt: |
      You are an expert FDA guidance analyst and agent configuration specialist. Your 
      role is to analyze FDA guidance documents, special controls, standards, or review 
      protocols and automatically generate specialized review agent configurations that 
      can be added to the agents.yaml system.
      
      **Your Analysis Process:**
      
      **STEP 1: GUIDANCE DOCUMENT ANALYSIS**
      
      When provided with an FDA guidance document (text, markdown, or PDF extract), analyze:
      
      1. **Document Metadata**:
         - Guidance title
         - Document date (issue date, revision date)
         - Applicable device types/categories
         - FDA office/division
         - Scope and purpose
      
      2. **Key Review Elements**:
         - What are the main review topics covered?
         - What testing is recommended/required?
         - What performance criteria are specified?
         - What standards are referenced?
         - What clinical data is discussed?
         - What labeling requirements are specified?
         - What risk management considerations are highlighted?
      
      3. **Guidance Structure**:
         - Major sections and subsections
         - Recommendations vs. requirements ("should" vs. "must")
         - Decision trees or flowcharts
         - Examples or case studies
         - Appendices or checklists
      
      **STEP 2: AGENT DESIGN**
      
      Based on guidance analysis, design a specialized agent with:
      
      **A. Agent Identification:**
      - Unique agent_id (e.g., "AGENT-GUID-001", "AGENT-SPEC-XXX")
      - Descriptive name reflecting guidance scope
      - Version number
      - Category assignment
      
      **B. Agent Expertise Definition:**
      - What specialized knowledge does this agent have?
      - What specific review tasks does it perform?
      - What guidance documents does it reference?
      - What standards does it apply?
      
      **C. System Prompt Creation:**
      
      The system prompt must include:
      
      1. **Agent Role & Expertise**:
         ```
         You are a [specialized role] with expertise in FDA review of [device category]
         per [guidance document title and date]. You evaluate [specific aspects].
         ```
      
      2. **Guidance-Specific Review Framework**:
         - Extract key recommendations from guidance
         - Organize into logical review sections
         - Specify acceptance criteria from guidance
         - Reference specific guidance sections
      
      3. **Review Checklist Items** (extracted from guidance):
         - Convert guidance recommendations into specific review questions
         - Organize by guidance section or review topic
         - Include acceptance criteria
         - Note when items are "recommended" vs. "required"
      
      4. **Testing/Data Requirements**:
         - What performance testing is needed?
         - What test methods are specified?
         - What acceptance criteria apply?
         - What standards are referenced?
      
      5. **Output Structure**:
         - Specify tables, checklists, or analyses the agent should produce
         - Define completeness requirements
         - Specify format (markdown, tables, etc.)
      
      **D. User Prompt Template:**
      - Create template with appropriate placeholders
      - Include guidance-specific data inputs
      - Structure to elicit comprehensive review
      
      **E. Output Requirements:**
      - Specify deliverables
      - Define quality criteria
      - Set word counts or content minimums
      
      **STEP 3: YAML CONFIGURATION GENERATION**
      
      Generate complete, valid YAML agent configuration that can be directly inserted 
      into agents.yaml file.
      
      **STEP 4: USAGE DOCUMENTATION**
      
      Provide:
      - Agent description and use cases
      - When this agent should be invoked
      - What device types benefit from this agent
      - Integration with existing agent workflow
      - Example invocation commands
      
      **OUTPUT FORMAT:**
      
      Your output must be structured as follows:
      
      ---
      
      # DYNAMIC AGENT GENERATION REPORT
      
      ## GUIDANCE DOCUMENT ANALYSIS
      
      | Attribute | Value |
      |-----------|-------|
      | **Guidance Title** | [Full title] |
      | **Document Date** | [Issue date] |
      | **FDA Office/Division** | [CDRH division] |
      | **Applicable Devices** | [Device categories] |
      | **Scope** | [Brief description] |
      | **Document Type** | [Final Guidance / Draft / Special Controls / Standard] |
      
      ### Key Review Elements Identified
      
      1. **[Review Topic 1]**: [Description of what guidance says]
      2. **[Review Topic 2]**: [Description]
      3. **[Review Topic 3]**: [Description]
      [Continue for all major topics]
      
      ### Referenced Standards
      
      - [ISO/IEC/ASTM standard 1]
      - [Standard 2]
      - [Standard 3]
      
      ### Performance Criteria Specified
      
      | Parameter | Acceptance Criterion | Guidance Section |
      |-----------|---------------------|------------------|
      | [Parameter 1] | [Criterion] | [Section X] |
      | [Parameter 2] | [Criterion] | [Section Y] |
      
      ## GENERATED AGENT CONFIGURATION
      
      ### Agent Overview
      
      - **Agent ID**: [Generated ID]
      - **Agent Name**: [Descriptive name]
      - **Category**: [Device-Specific Expert / Specialized Analysis]
      - **Primary Function**: [What this agent does]
      - **Key Expertise Areas**: [List 3-5 areas]
      
      ### Complete YAML Configuration
      
      ```yaml
      # --------------------------------------------------------------------------
      # Agent [ID]: [Name]
      # --------------------------------------------------------------------------
      [agent_id]:
        agent_id: "[AGENT-ID]"
        name: "[Full Agent Name]"
        version: "1.0"
        category: "[Category]"
        description: "[Comprehensive description]"
        
        model: "gpt-4o-mini"
        temperature: 0.2
        max_tokens: 16000
        
        guidance_references:
          primary: "[Guidance title and date]"
          secondary:
            - "[Additional guidance 1]"
            - "[Additional guidance 2]"
        
        system_prompt: |
          [Complete system prompt with guidance-specific instructions]
          
          [Include all review framework, criteria, standards, etc.]
        
        user_prompt_template: |
          [Complete user prompt template with placeholders]
        
        output_requirements:
          format: "markdown"
          [Additional requirements]
        
        validation_rules:
          [Validation rules]
      ```
      
      ## AGENT USAGE DOCUMENTATION
      
      ### When to Use This Agent
      
      This agent should be invoked when:
      - [Use case 1]
      - [Use case 2]
      - [Use case 3]
      
      ### Applicable Device Types
      
      - [Device type 1]
      - [Device type 2]
      - [Device type 3]
      
      ### Integration with Review Workflow
      
      This agent fits into the review process as follows:
      
      1. **Phase**: [Phase 1/2/3/4]
      2. **Sequence**: [Before/After/Parallel with other agents]
      3. **Dependencies**: [What other agents should run first]
      4. **Outputs Used By**: [What downstream agents use this output]
      
      ### Example Invocation
      
      ```bash
      run_agent [agent_id] \
        --device "Device Name" \
        --submission_section "Section X" \
        --guidance_focus "[specific aspect]"
      ```
      
      ### Expected Output
      
      This agent will produce:
      - [Output 1 description]
      - [Output 2 description]
      - [Output 3 description]
      
      Typical output length: [X,XXX] words, [Y] tables, [Z] sections
      
      ## QUALITY ASSURANCE CHECKS
      
      ✅ **Validation Results:**
      - [ ] YAML syntax is valid
      - [ ] All required fields present
      - [ ] System prompt is comprehensive (>500 words)
      - [ ] User prompt template has appropriate placeholders
      - [ ] Output requirements are specific
      - [ ] Guidance references are complete
      - [ ] Agent integrates with existing workflow
      
      ## INSTALLATION INSTRUCTIONS
      
      To add this agent to your system:
      
      1. **Copy YAML configuration** from above
      2. **Insert into agents.yaml** under appropriate section:
         - Device-Specific Experts (Agents 21-31+)
         - OR Specialized Analysis (Agents 11-20)
      3. **Update workflow configurations** if this agent should be part of standard workflows
      4. **Test agent** with sample device information
      5. **Document in agent catalog** for future reference
      
      ## RECOMMENDATIONS FOR IMPROVEMENT
      
      Consider these enhancements:
      - [Enhancement 1]
      - [Enhancement 2]
      - [Enhancement 3]
      
      ---
      
      **Ensure all generated YAML is valid, complete, and ready for production use.**
      **Be comprehensive in extracting guidance requirements into agent logic.**
      **Make the agent specific enough to be useful, but flexible enough to handle variations.**
    
    user_prompt_template: |
      Please analyze the following FDA guidance document and generate a specialized 
      review agent configuration:
      
      **GUIDANCE DOCUMENT CONTENT:**
      
      ```
      {guidance_document_text}
      ```
      
      **ADDITIONAL CONTEXT** (if provided):
      - Document Title: {document_title}
      - Document Date: {document_date}
      - Target Device Types: {target_devices}
      - Specific Focus Area: {focus_area}
      - Integration Requirements: {integration_requirements}
      
      **GENERATION REQUIREMENTS:**
      - Agent Complexity Level: {complexity_level} [Basic/Standard/Comprehensive]
      - Include Detailed Checklist: {include_checklist} [Yes/No]
      - Reference Specific Standards: {reference_standards} [Yes/No]
      - Generate Test Requirements Matrix: {generate_test_matrix} [Yes/No]
      
      Please provide:
      
      1. **Comprehensive Guidance Analysis** - Extract all key review elements
      2. **Complete Agent YAML Configuration** - Production-ready configuration
      3. **Usage Documentation** - When and how to use this agent
      4. **Integration Guide** - How this fits into existing workflows
      5. **Example Outputs** - What this agent will produce
      6. **Quality Validation** - Confirm YAML validity and completeness
      
      The generated agent should be immediately usable in the FDA review agent system.
    
    output_requirements:
      format: "markdown"
      include_yaml_config: true
      yaml_must_be_valid: true
      include_usage_docs: true
      include_integration_guide: true
      min_system_prompt_words: 500
      include_validation_checklist: true
    
    validation_rules:
      verify_yaml_syntax: true
      verify_required_fields: true
      verify_completeness: true
      verify_guidance_references: true

  # --------------------------------------------------------------------------
  # Agent ORCH-003: Agent Performance Analyzer
  # --------------------------------------------------------------------------
  agent_performance_analyzer:
    agent_id: "AGENT-ORCH-003"
    name: "Agent Performance & Optimization Analyzer"
    version: "1.0"
    category: "Orchestration & Planning"
    description: "Analyzes agent outputs for quality, identifies gaps, and recommends workflow optimizations"
    
    model: "gpt-4o-mini"
    temperature: 0.25
    max_tokens: 16000
    
    system_prompt: |
      You are an agent performance analyst who evaluates the quality and completeness 
      of review agent outputs and recommends workflow optimizations.
      
      **Your Analysis Framework:**
      
      **1. OUTPUT QUALITY ASSESSMENT**
      - Completeness (all required sections present?)
      - Depth of analysis (superficial vs. thorough)
      - Regulatory accuracy (correct CFR/standard references?)
      - Actionability (clear recommendations?)
      - Format compliance (tables, word counts, structure)
      
      **2. GAP IDENTIFICATION**
      - What review areas were not adequately covered?
      - What additional agents should have been used?
      - What information is missing from the submission?
      
      **3. WORKFLOW OPTIMIZATION**
      - Which agents could run in parallel?
      - Which agents have dependencies?
      - What is the critical path?
      - How to reduce total review time?
      
      **4. RECOMMENDATIONS**
      - Additional agents to invoke
      - Re-run agents with better prompts
      - Request additional information from sponsor
      - Adjust agent parameters (temperature, max_tokens)
      
      Provide specific, actionable recommendations for improving review quality and efficiency.
    
    user_prompt_template: |
      Analyze the following agent outputs and provide optimization recommendations:
      
      **DEVICE**: {device_name}
      
      **AGENTS RUN**: {agents_executed}
      
      **AGENT OUTPUTS**:
      ```
      {agent_outputs}
      ```
      
      Please provide:
      1. Quality assessment for each agent output
      2. Gap analysis (what's missing?)
      3. Recommended additional agents
      4. Workflow optimization suggestions
      5. Overall review completeness score (0-100)
    
    output_requirements:
      format: "markdown"
      include_quality_scores: true
      include_gap_analysis: true
      include_recommendations: true

# ============================================================================
# WORKFLOW TEMPLATES FOR ORCHESTRATED REVIEWS
# ============================================================================

workflow_templates:

  # Orchestrated Complete Review
  orchestrated_complete_review:
    name: "AI-Orchestrated Complete 510(k) Review"
    description: "Intelligent orchestration determines optimal agent sequence"
    steps:
      - step: 1
        agent: intelligent_review_orchestrator
        inputs:
          - device_information
          - submission_type
          - regulatory_pathway
        outputs:
          - orchestration_plan
          - recommended_agents
          - execution_sequence
      
      - step: 2
        agent: dynamic_execution
        inputs:
          - orchestration_plan
          - agent_list_from_step_1
        description: "Execute recommended agents in optimal sequence"
        execution_mode: "adaptive" # Adjusts based on intermediate results
      
      - step: 3
        agent: agent_performance_analyzer
        inputs:
          - all_agent_outputs_from_step_2
        outputs:
          - quality_assessment
          - gap_analysis
          - optimization_recommendations
      
      - step: 4
        agent: review_memo_builder
        inputs:
          - all_agent_outputs_from_step_2
          - quality_assessment_from_step_3
        outputs:
          - final_review_memorandum

  # Custom Agent Generation Workflow
  custom_agent_generation:
    name: "Generate Custom Agent from FDA Guidance"
    description: "Create specialized agent from guidance document"
    steps:
      - step: 1
        agent: dynamic_agent_generator
        inputs:
          - guidance_document_text
          - document_title
          - target_devices
        outputs:
          - agent_yaml_configuration
          - usage_documentation
          - integration_guide
      
      - step: 2
        action: validate_yaml
        description: "Validate generated YAML configuration"
        validation_checks:
          - syntax_validity
          - required_fields
          - prompt_completeness
      
      - step: 3
        action: deploy_agent
        description: "Add agent to agents.yaml and register in system"
      
      - step: 4
        action: test_agent
        description: "Run test case with new agent"
        inputs:
          - sample_device_information
      
      - step: 5
        agent: agent_performance_analyzer
        description: "Evaluate new agent performance"
        inputs:
          - test_agent_output
        outputs:
          - performance_assessment
          - recommendations_for_improvement

# ============================================================================
# ORCHESTRATION RULES & LOGIC
# ============================================================================

orchestration_rules:
  
  # Device Type to Specialty Agent Mapping
  device_specialty_mapping:
    cardiovascular:
      keywords: ["stent", "valve", "pacemaker", "ICD", "defibrillator", "catheter", "vascular", "coronary", "cardiac"]
      cfr_part: "870"
      primary_agent: "cardiovascular_specialist"
      
    orthopedic:
      keywords: ["implant", "joint", "hip", "knee", "spine", "screw", "plate", "bone", "fixation", "prosthesis"]
      cfr_part: "888"
      primary_agent: "orthopedic_specialist"
      
    imaging:
      keywords: ["X-ray", "CT", "MRI", "ultrasound", "imaging", "scanner", "fluoroscopy", "mammography"]
      cfr_part: "892"
      primary_agent: "diagnostic_imaging_specialist"
      
    ivd:
      keywords: ["assay", "test", "diagnostic", "analyzer", "reagent", "kit", "in vitro", "specimen", "biomarker"]
      cfr_part: ["862", "864", "866"]
      primary_agent: "ivd_specialist"
      
    software:
      keywords: ["software", "algorithm", "AI", "machine learning", "app", "clinical decision support", "CAD"]
      cfr_part: "various"
      primary_agent: "samd_specialist"
      
    neurological:
      keywords: ["neurostimulator", "DBS", "spinal cord stimulator", "brain", "neural", "neurovascular"]
      cfr_part: "882"
      primary_agent: "neurological_specialist"
      
    ophthalmic:
      keywords: ["lens", "IOL", "contact", "eye", "cornea", "retina", "glaucoma", "ophthalmic", "vision"]
      cfr_part: "886"
      primary_agent: "ophthalmic_specialist"
      
    dental:
      keywords: ["dental", "tooth", "implant", "crown", "orthodontic", "composite", "cavity"]
      cfr_part: "872"
      primary_agent: "dental_specialist"
      
    obgyn:
      keywords: ["IUD", "contraceptive", "fetal", "obstetric", "gynecological", "uterine", "pregnancy"]
      cfr_part: "884"
      primary_agent: "obgyn_specialist"
      
    anesthesia:
      keywords: ["ventilator", "anesthesia", "airway", "respiratory", "breathing", "oxygen"]
      cfr_part: "868"
      primary_agent: "anesthesia_specialist"
      
    general_hospital:
      keywords: ["infusion pump", "monitor", "patient monitor", "surgical", "hospital bed", "exam table"]
      cfr_part: "880"
      primary_agent: "general_hospital_specialist"
  
  # Conditional Agent Triggers
  conditional_triggers:
    
    biocompatibility_required:
      conditions:
        - patient_contact: true
        - contact_duration: [">24 hours", "permanent"]
      required_agents:
        - biocompatibility_specialist
    
    sterilization_required:
      conditions:
        - sterilization: true
      required_agents:
        - sterilization_shelf_life_reviewer
    
    software_review_required:
      conditions:
        - has_software: true
      required_agents:
        - software_cybersecurity_reviewer
      additional_if:
        - condition: ai_ml_present
          agent: samd_specialist
    
    electrical_safety_required:
      conditions:
        - active_device: true
        - has_electrical_components: true
      required_agents:
        - electrical_safety_emc_reviewer
    
    clinical_data_required:
      conditions:
        - clinical_studies_present: true
      OR:
        - novel_device: true
        - no_predicate: true
        - high_risk: true
      required_agents:
        - clinical_data_evaluator
    
    regulatory_strategy_needed:
      conditions:
        - pathway_unclear: true
      OR:
        - novel_technology: true
        - no_clear_predicate: true
        - first_of_kind: true
      required_agents:
        - regulatory_strategy_advisor
        - fda_database_analyst

  # Agent Dependencies (what must run before what)
  agent_dependencies:
    
    predicate_comparison_specialist:
      requires_before:
        - intelligence_analyst (for device overview)
      OR:
        - fda_database_analyst (for predicate identification)
    
    substantial_equivalence_determinator:
      requires_before:
        - predicate_comparison_specialist
        - risk_management_analyst
        - device_specialty_agent
        - all_technical_agents
    
    benefit_risk_assessor:
      requires_before:
        - risk_management_analyst
        - clinical_data_evaluator (if applicable)
        - device_specialty_agent
    
    review_memo_builder:
      requires_before:
        - ALL_OTHER_AGENTS (final compilation)

  # Parallelization Opportunities
  parallel_execution_groups:
    
    phase_2_parallel_group:
      description: "Technical deep-dive agents that can run simultaneously"
      agents:
        - risk_management_analyst
        - device_specialty_agent
        - biocompatibility_specialist
        - software_cybersecurity_reviewer
        - electrical_safety_emc_reviewer
        - sterilization_shelf_life_reviewer
      prerequisites:
        - intelligence_analyst_complete
    
    phase_3_parallel_group:
      description: "Supporting review agents"
      agents:
        - labeling_ifu_reviewer
        - manufacturing_qms_reviewer
        - clinical_data_evaluator
      prerequisites:
        - phase_2_complete

# ============================================================================
# EXAMPLE USAGE SCENARIOS
# ============================================================================

example_scenarios:

  scenario_1_cardiovascular_stent:
    name: "Coronary Drug-Eluting Stent Review"
    device_info: |
      Device: CardioFlow DES
      Type: Drug-eluting coronary stent
      Material: CoCr alloy with biodegradable polymer coating
      Drug: Sirolimus
      Indications: Treatment of coronary artery disease
      Predicate: Previous-generation DES (K123456)
    
    orchestrator_output:
      recommended_agents:
        - intelligence_analyst
        - fda_database_analyst (for DES precedents)
        - predicate_comparison_specialist
        - cardiovascular_specialist (PRIMARY)
        - risk_management_analyst
        - biocompatibility_specialist (blood contact, drug elution)
        - sterilization_shelf_life_reviewer
        - clinical_data_evaluator (typically required for DES)
        - labeling_ifu_reviewer
        - manufacturing_qms_reviewer
        - substantial_equivalence_determinator
        - benefit_risk_assessor
        - review_memo_builder
      
      estimated_timeline: "12-15 days"
      critical_focus:
        - Drug elution kinetics and safety
        - Thrombosis rates (clinical data)
        - Late stent thrombosis monitoring
        - Polymer biocompatibility
        - Radial strength and recoil

  scenario_2_ai_diagnostic:
    name: "AI-Based Diabetic Retinopathy Detection Software"
    device_info: |
      Device: RetinaAI Pro
      Type: Standalone AI/ML software (SaMD)
      Function: Automated detection of diabetic retinopathy from fundus images
      Algorithm: Deep learning CNN
      Intended Use: Aid in diagnosis (adjunctive use)
      Setting: Primary care clinics
    
    orchestrator_output:
      recommended_agents:
        - intelligence_analyst
        - regulatory_strategy_advisor (De Novo vs 510(k))
        - fda_database_analyst (search for AI retinopathy predicates)
        - predicate_comparison_specialist
        - samd_specialist (PRIMARY)
        - software_cybersecurity_reviewer
        - ophthalmic_specialist (clinical context)
        - clinical_data_evaluator (reader studies required)
        - risk_management_analyst
        - labeling_ifu_reviewer
        - manufacturing_qms_reviewer
        - substantial_equivalence_determinator
        - benefit_risk_assessor
        - review_memo_builder
      
      estimated_timeline: "14-18 days"
      critical_focus:
        - Training dataset diversity and bias
        - Algorithm validation (sensitivity, specificity)
        - Reader study design (MRMC)
        - Cybersecurity (cloud-based processing?)
        - Algorithm change control (continuous learning?)
        - Intended user qualification
        - False negative risk (delayed treatment)

  scenario_3_ivd_covid_test:
    name: "Rapid COVID-19 Antigen Test"
    device_info: |
      Device: QuickCOVID Antigen Test
      Type: Lateral flow immunoassay
      Specimen: Nasal swab
      Setting: Point-of-care, OTC home use
      Detection: SARS-CoV-2 nucleocapsid protein
      Time to result: 15 minutes
    
    orchestrator_output:
      recommended_agents:
        - intelligence_analyst
        - fda_database_analyst (COVID test precedents)
        - predicate_comparison_specialist
        - ivd_specialist (PRIMARY)
        - risk_management_analyst
        - clinical_data_evaluator (clinical validation required)
        - labeling_ifu_reviewer (critical for OTC)
        - manufacturing_qms_reviewer
        - substantial_equivalence_determinator
        - benefit_risk_assessor
        - review_memo_builder
      
      estimated_timeline: "10-12 days"
      critical_focus:
        - Analytical sensitivity (LoD)
        - Clinical sensitivity/specificity
        - Asymptomatic vs symptomatic performance
        - User comprehension study (OTC use)
        - Shelf life stability
        - Specimen collection instructions
        - False negative risk communication

# ============================================================================
# END OF ORCHESTRATION AGENTS CONFIGURATION
# ============================================================================

20 COMPREHENSIVE FOLLOW-UP QUESTIONS
Strategic & Conceptual Questions

Multi-Pathway Orchestration: How should the orchestrator handle devices that could qualify for multiple regulatory pathways (e.g., both 510(k) Traditional and De Novo)? Should it recommend running parallel pathway analyses and comparing outcomes?
Learning & Adaptation: Should the orchestration system learn from past reviews to improve future agent recommendations? For example, if a cardiovascular stent consistently requires additional agents beyond the initial recommendation, should the system automatically include them in future stent reviews?
Confidence Scoring: Should the Intelligent Review Orchestrator provide confidence scores for its agent recommendations (e.g., "95% confident cardiovascular_specialist is needed, 60% confident clinical_data_evaluator is needed")? How would this help reviewers?
Human-in-the-Loop: At what decision points should the orchestration system pause and ask for human reviewer input before proceeding? Should it be after Phase 1, after each phase, or only when confidence is low?
Cost Optimization: Given different LLM costs (GPT-4o-mini vs. Claude vs. Gemini), should the orchestrator include cost-benefit analysis in its recommendations? For example, using cheaper models for straightforward reviews and premium models for complex/novel devices?

Agent Generation & Customization

Guidance Versioning: How should the Dynamic Agent Generator handle guidance documents that are later revised or superseded? Should it automatically flag when an agent is based on outdated guidance and recommend regeneration?
Hybrid Agents: Should the system support generating "hybrid agents" that combine multiple FDA guidances? For example, a single agent that covers both "Orthopedic Spinal Implant Guidance" and "Additive Manufacturing Guidance" for 3D-printed spinal devices?
Agent Specialization Depth: When generating agents from guidance, should there be options for different specialization levels? For example:

Broad agent: Covers entire guidance document generally
Deep agent: Focuses on one specific aspect (e.g., only clinical study requirements from the guidance)
Checklist agent: Generates primarily checklist-based reviews


Multi-Language Guidance: If provided with guidance documents in multiple languages (e.g., FDA English + Taiwan FDA Traditional Chinese), can the generator create bilingual agents? What challenges would this present?
Standards Integration: When an FDA guidance extensively references ISO/IEC standards (e.g., "follow ISO 14971 for risk management"), should the Dynamic Agent Generator attempt to incorporate the actual standard requirements, or just reference them? How deep should the integration go?

Workflow & Execution

Agent Chaining & Feedback Loops: Should certain agents be able to trigger re-execution of earlier agents based on their findings? For example, if substantial_equivalence_determinator finds a critical gap, should it automatically trigger predicate_comparison_specialist to search for alternative predicates?
Conditional Branching: How should the orchestration system handle scenarios where Phase 2 results indicate a completely different pathway is needed? For example:


Initial assessment: 510(k) pathway
After technical review: Novel technology, no true predicate → Switch to De Novo pathway
Should this trigger a complete re-orchestration?


Incremental Reviews: For devices with multiple AI Request (deficiency letter) rounds, should the orchestrator maintain "state" across review cycles and only run agents on changed/new information? Or always run complete review?
Parallel Execution Optimization: Given the parallel execution groups defined in orchestration_rules, what is the optimal strategy for load balancing when running multiple agents simultaneously? Should it consider:


Token usage per agent
Expected execution time
API rate limits
Cost constraints


Output Aggregation: When multiple agents analyze the same aspect (e.g., both cardiovascular_specialist and risk_management_analyst evaluate thrombosis risk), how should the review_memo_builder resolve conflicts or synthesize overlapping findings?

Quality & Validation

Agent Performance Metrics: What specific metrics should the agent_performance_analyzer use to evaluate agent output quality? Should it include:


Regulatory citation accuracy (% of CFR/standard references that are correct)
Completeness score (% of required review elements covered)
Consistency score (alignment with other agent outputs)
Actionability score (clarity of recommendations)
Deficiency prediction accuracy (how often did deficiencies identified match actual sponsor gaps)?


Ensemble Methods: For critical determinations (e.g., Substantial Equivalence decision), should the system run multiple agents or multiple runs of the same agent with different parameters, then use ensemble/voting methods to increase confidence? What's the trade-off between thoroughness and efficiency?
Validation Against Human Reviews: How should the system be validated against historical FDA reviews? Should there be a benchmark dataset of past 510(k) decisions with known outcomes to test orchestration accuracy?
Agent Drift Detection: Over time, if LLM models are updated (e.g., GPT-4o-mini → GPT-4.5-mini), agent outputs might change. Should there be automated testing to detect "agent drift" and ensure consistency over model updates?
False Positive/Negative Analysis: For the orchestrator's agent recommendations:


False Positive: Recommended an agent that wasn't needed (wasted resources)
False Negative: Didn't recommend an agent that should have been used (missed review element)

How should the system track these errors and continuously improve? Should there be a feedback mechanism where reviewers flag orchestration mistakes?

These questions cover strategic planning, technical implementation, quality assurance, workflow optimization, and continuous improvement for the orchestration and dynamic agent generation system. They are designed to help you think through edge cases, scalability, validation, and real-world operational considerations.
