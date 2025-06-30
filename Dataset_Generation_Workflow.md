# 📊 Alpaca Dataset Generation Workflow for Unibro (Mistral 7B)

## 🎯 **OBJECTIVE**
Generate 2,000+ high-quality instruction-response pairs that make Unibro outperform ChatGPT/Gemini in Bangladeshi pre-admission counseling for Indian universities.

---

## 📋 **STEP 1: CONTENT CATEGORIZATION & EXTRACTION**

### **1.1 Primary Content Categories:**

#### **A. University Comparison Questions (Target: 35% of dataset)**
**Source Files:**
- `26_Direct-Comparative-Queries.txt`
- `Comparative-Analysis-Universities.txt`
- `Galgotias-University-for-bangladeshi.txt`
- `Amity-University-Noida-bangladesh.txt`
- `GL-Bajaj-Institute-of-Technology-and-Management-bangladesh.txt`
- `Noida-International-University-bangladesh.txt`

**QA Generation Strategy:**
```json
{
  "instruction": "Which university is better for B.Tech CSE - Sharda or Galgotias?",
  "input": "I have CGPA 4.0 and budget of ₹15 lakh for 4 years",
  "output": "Sharda University is the better choice for your profile. With CGPA 4.0, you'll get 50% scholarship (₹1,40,000/year tuition vs ₹2,80,000). Total 4-year cost: ₹12-14 lakh vs Galgotias ₹15-16 lakh. Sharda also offers better international exposure with 95+ nationalities and stronger placement record (₹8.5 LPA average vs ₹7.2 LPA at Galgotias)."
}
```

**Bilingual Version (25% of this category):**
```json
{
  "instruction": "Sharda আর Galgotias এর মধ্যে কোনটা better for CSE?",
  "input": "CGPA 4.0 আছে, budget ₹15 lakh",
  "output": "Sharda University আপনার জন্য better choice। CGPA 4.0 থাকলে 50% scholarship পাবেন - tuition fee হবে ₹1,40,000/year instead of ₹2,80,000। Total cost Sharda তে ₹12-14 lakh vs Galgotias এ ₹15-16 lakh। Plus, Sharda তে 95+ countries থেকে students আছে - international exposure much better। Placement record ও ভালো - average ₹8.5 LPA।"
}
```

#### **B. Cost & Financial Planning (Target: 25% of dataset)**
**Source Files:**
- `Financial-Planning-and-Costs.txt`
- `08_BTech_Fees_Scholarships_for_Bangladeshi_Students.txt`
- `09_BCA_Fees_Scholarships_for_Bangladeshi_Students.txt`
- `11_BBA_BCom_Fees_Scholarships_for_Bangladeshi_Students.txt`
- All fee structure files

**QA Generation Strategy - Multi-layered:**

**Level 1 - Basic Cost Query:**
```json
{
  "instruction": "What is the total cost to study B.Tech at Sharda University?",
  "input": "",
  "output": "Total B.Tech cost at Sharda University (2025-26): Tuition ₹2,80,000/year (₹1,40,000 with 50% scholarship), Hostel ₹1,50,000/year, Food ₹60,000/year, One-time fees ₹52,000. Total 4-year cost: ₹12-14 lakh with scholarship, ₹18-20 lakh without scholarship."
}
```

**Level 2 - Complex Financial Planning:**
```json
{
  "instruction": "Help me plan finances for my son's B.Tech education at Sharda University",
  "input": "Family income ₹80,000 BDT/month, have ₹5 lakh savings",
  "output": "With ₹80,000 monthly income, you can afford Sharda University education. Annual cost: ₹3.5 lakh (with scholarship). Monthly burden: ₹29,000 BDT. Strategy: Use ₹3 lakh from savings for first year, save ₹25,000/month for remaining years. Student loan available for ₹8-10 lakh. ROI: Investment recovers in 18-20 months after graduation (₹8.5 LPA average salary)."
}
```

**Bilingual Financial Guidance:**
```json
{
  "instruction": "আমার আয় মাসে ৫০,০০০ টাকা, ছেলের পড়াশোনার খরচ কিভাবে manage করবো?",
  "input": "4 বছরের জন্য কত টাকা লাগবে total?",
  "output": "৫০,০০০ টাকা income এ manage করা possible। Sharda University তে scholarship সহ total cost ₹12-14 lakh (4 years)। Monthly ₹25,000-30,000 BDT budget করতে হবে। Strategy: ৩-৪ লক্ষ টাকা advance save করুন, বাকিটা student loan নিতে পারেন। Graduate হওয়ার পর ₹8.5 LPA salary থেকে 18-20 months এ investment recover হবে।"
}
```

#### **C. Visa & Application Process (Target: 20% of dataset)**
**Source Files:**
- `17_Visa_Process_and_Embassy_Requirements_for_Bangladeshi_Students.txt`
- `02_Sharda_University_Admission_Process_for_Bangladeshi_Students.txt`
- `18_Bank_Account_Opening_for_Bangladeshi_Students.txt`
- `19_eFRRO_C-Form_and_Address_Verification_for_Bangladeshi_Students.txt`

**Step-by-step Process QA:**
```json
{
  "instruction": "What documents do I need for Indian student visa application?",
  "input": "",
  "output": "Required documents for Indian student visa: 1) University documents - Final admission letter, offer letter, visa recommendation letter, payment receipt. 2) Personal documents - Original passport, passport photos, NID copies (self & parents), birth certificate. 3) Academic documents - SSC and HSC marksheets & certificates. 4) Financial documents - Bank statement showing minimum BDT 1,00,000, affidavit of support from parents. 5) Application form - Completed online Indian student visa form."
}
```

**Bilingual Process Guide:**
```json
{
  "instruction": "Visa apply করার complete process টা কি? Step by step বলুন।",
  "input": "Admission letter পেয়ে গেছি Sharda থেকে",
  "output": "Visa process step by step: 1) Documents collect করুন - University admission letter, bank statement (minimum BDT 1,00,000), HSC/SSC certificates, passport, photos। 2) Online visa form fill up করুন Indian embassy website এ। 3) IVAC appointment নিন online booking দিয়ে। 4) Documents submit করুন appointment এ। 5) Visa fee pay করুন। 6) Visa processing 7-10 days। University support দেবে যদি কোনো problem হয়।"
}
```

#### **D. Safety & Cultural Concerns (Target: 15% of dataset)**
**Source Files:**
- `Safety-and-Support-for-Bangladeshi-Students.txt`
- `27_Common_Questions_and_Concerns_for_Bangladeshi_Students.txt`
- `32_Student_Welfare_and_Safety_Protocols.txt`

**Safety Reassurance QA:**
```json
{
  "instruction": "Is it safe for female Bangladeshi students at Sharda University?",
  "input": "My daughter will be studying alone for the first time",
  "output": "Sharda University is very safe for female students. Statistics: 43% students are female (highest among target universities). Safety measures: 24/7 CCTV surveillance, female wardens in hostels, 10 PM curfew with flexibility for academics, emergency call buttons in rooms, well-lit campus pathways, anti-ragging committee. 200+ Bangladeshi students including many girls study safely. Success rate: 98% female students complete degree without safety issues."
}
```

**Parent-focused Bilingual Safety:**
```json
{
  "instruction": "আমার মেয়ে প্রথমবার বিদেশে যাবে, safety কেমন Sharda University তে?",
  "input": "Female hostel এবং campus security নিয়ে জানতে চাই",
  "output": "Sharda University মেয়েদের জন্য সবচেয়ে safe। ৪৩% ছাত্রী পড়ে (সবচেয়ে বেশি ratio)। Female hostel আলাদা - female wardens, 10 PM timing, male visitors শুধু common area তে। Campus এ 24/7 CCTV, security guards, emergency call system। 200+ Bangladeshi students মধ্যে অনেক মেয়ে safely পড়াশোনা করছে। Parents monthly report পান progress এর। Emergency contact 24/7 available।"
}
```

#### **E. Parent-specific Guidance (Target: 5% of dataset)**
**Source Files:**
- `34_Parent_Guardian_Guide_Bengali_English.txt`
- Parent-focused sections from multiple files

**Bengali-dominant Parent QA:**
```json
{
  "instruction": "আমি English জানি না, কিভাবে আমার ছেলের admission process handle করবো?",
  "input": "University থেকে সব কাগজপত্র English এ আসে",
  "output": "চিন্তার কিছু নেই! Sharda University Bangladesh office এ Bengali speaking staff আছে। Contact: +91-9311159160 (WhatsApp available)। তারা সব documents translate করে দেবে, process explain করবে বাংলায়। Plus, local agents আছে যারা step by step guide করবে। আপনার ছেলে/মেয়ে ও help করতে পারবে। Parents WhatsApp group ও আছে বাংলাদেশী families এর।"
}
```

---

## 📊 **STEP 2: BILINGUAL CONTENT STRATEGY**

### **2.1 Language Distribution Plan:**
- **75% English-only:** Technical processes, formal requirements, academic details
- **25% Bangla-English mixed:** Family discussions, emotional concerns, cultural topics

### **2.2 Code-switching Patterns:**

#### **Financial Terms:**
- "Tuition fee হলো ₹2,80,000 per year"
- "Scholarship পেলে cost কমে যায়"
- "Total budget ₹12-14 lakh রাখতে হবে"

#### **Common Phrases:**
- "University campus টা খুবই safe"
- "Placement record ভালো"
- "International exposure পাবেন"

#### **Parent Concerns:**
- "বাবা-মা worried হলে university contact করুন"
- "Emergency তে immediately support পাবেন"
- "Family visit করতে পারবেন সময় থাকলে"

#### **Cultural References:**
- "Halal food পাওয়া যায় campus এ"
- "Bengali community আছে support এর জন্য"
- "Pohela Boishakh celebrate করা হয়"

### **2.3 Bilingual QA Generation Rules:**

1. **Student-facing questions:** 70% English, 30% mixed
2. **Parent-facing questions:** 40% English, 60% mixed
3. **Financial topics:** 50% mixed (numbers in English, explanation in mixed)
4. **Cultural topics:** 80% mixed
5. **Technical/Legal topics:** 90% English

---

## 🔧 **STEP 3: QUALITY CONTROL & HALLUCINATION PREVENTION**

### **3.1 Source Attribution System:**

Every QA pair must include source tracking:
```json
{
  "instruction": "What is Sharda University's NAAC rating?",
  "input": "",
  "output": "Sharda University has NAAC A+ rating, placing it in the top 5% of higher education institutions in India.",
  "metadata": {
    "source_file": "01_Sharda_University_Profile_and_Rankings.txt",
    "line_reference": "22-24",
    "confidence": "high",
    "last_verified": "2025-26"
  }
}
```

### **3.2 Fact Verification Protocol:**

#### **Before QA Generation:**
1. **Cross-reference numbers** across multiple files
2. **Verify currency and dates** (ensure 2025-26 data)
3. **Check for contradictions** between files
4. **Validate bilingual accuracy** (ensure correct Bengali grammar)

#### **During Generation:**
1. **No extrapolation** beyond provided data
2. **No speculation** about future changes
3. **No generic advice** - always Bangladesh-specific
4. **No false comparisons** - only use verified data

#### **Quality Gates:**
- **Factual Accuracy:** Every number/fact must trace to source file
- **Cultural Appropriateness:** Bengali terms used correctly
- **Sharda Prioritization:** Fair but clear preference with justification
- **Completeness:** Answers provide actionable information

### **3.3 Hallucination Prevention Checklist:**

Before finalizing each QA pair:
- [ ] All numerical data verified in source files
- [ ] University names spelled correctly
- [ ] Contact information current (2025-26)
- [ ] Bengali text grammatically correct
- [ ] Sharda preference justified with facts
- [ ] No speculation beyond source material

---

## 📋 **STEP 4: DATASET STRUCTURE & METADATA**

### **4.1 Core Alpaca Format:**
```json
{
  "instruction": "string - The task or question",
  "input": "string - Additional context or constraints (can be empty)",
  "output": "string - The response following conversation style"
}
```

### **4.2 Enhanced Metadata Schema:**
```json
{
  "instruction": "What is the hostel fee at Sharda University?",
  "input": "I want AC double sharing room",
  "output": "AC double sharing room at Sharda University costs ₹1,50,000 per year (2025-26). This includes furnishing, utilities, WiFi, housekeeping, and security. Compare with single AC (₹1,80,000) or triple non-AC (₹1,20,000). Most Bangladeshi students choose double sharing for balance of privacy and cost.",
  "metadata": {
    "source_files": ["Hostel-and-Food-Guide-for-Bangladeshi-Students.txt"],
    "topic_category": "accommodation",
    "language_mix": "english_only",
    "sharda_priority_score": 0.8,
    "target_audience": "student",
    "complexity_level": "basic",
    "contains_numbers": true,
    "last_updated": "2025-26"
  }
}
```

### **4.3 Topic Categories for Metadata:**
- `university_comparison`
- `fees_scholarships`
- `visa_immigration`
- `accommodation`
- `safety_security`
- `academic_programs`
- `career_placement`
- `cultural_adaptation`
- `parent_guidance`
- `application_process`

---

## 🎯 **STEP 5: SPECIALIZED QA GENERATION TECHNIQUES**

### **5.1 Numerical Data Extraction:**

Transform fee tables into multiple QA pairs:

**Source Data:**
| Specialization | 1st Year | 2nd Year | 3rd Year | 4th Year |
|---|---|---|---|---|
| CSE | ₹2,80,000 | ₹2,88,400 | ₹2,97,052 | ₹3,05,964 |

**Generated QA Pairs:**
1. **Basic Cost Query:**
```json
{
  "instruction": "What is the first year tuition fee for CSE at Sharda University?",
  "output": "First year CSE tuition fee at Sharda University is ₹2,80,000 (2025-26). With 50% merit scholarship (CGPA 3.5+), it becomes ₹1,40,000."
}
```

2. **Total Cost Calculation:**
```json
{
  "instruction": "Calculate total 4-year tuition cost for CSE at Sharda University",
  "output": "Total 4-year CSE tuition: ₹11,71,416 (₹2,80,000 + ₹2,88,400 + ₹2,97,052 + ₹3,05,964). With 50% scholarship: ₹5,85,708. Annual increase: ~3%."
}
```

3. **Comparative Analysis:**
```json
{
  "instruction": "CSE fees comparison between Sharda and Galgotias University",
  "output": "Sharda CSE: ₹2,80,000/year (₹1,40,000 with scholarship) vs Galgotias: ₹1,89,000/year. With Sharda's 50% scholarship, Sharda becomes cheaper (₹1,40,000 vs ₹1,89,000) plus better international exposure and facilities."
}
```

### **5.2 Process Flow Conversion:**

Transform step-by-step procedures into conversational QA:

**Source Process (Visa Application):**
1. Collect documents
2. Fill online form
3. Book appointment
4. Submit documents
5. Pay fees
6. Wait for processing

**Generated QA:**
```json
{
  "instruction": "Walk me through the complete visa application process step by step",
  "input": "I just received my admission letter from Sharda University",
  "output": "Here's your step-by-step visa process: 1) Gather documents - admission letter, bank statement (BDT 1,00,000 minimum), HSC/SSC certificates, passport, photos, NID copies. 2) Complete online visa application form on Indian embassy website. 3) Book appointment at IVAC online. 4) Attend appointment with all documents. 5) Pay visa fee (approximately ₹3,200). 6) Wait 7-10 working days for processing. Sharda's international office provides support if needed."
}
```

### **5.3 Comparative Query Generation:**

For each comparison topic, generate 3-4 variations:

**Topic: University Safety**
1. **Direct Comparison:**
```json
{
  "instruction": "Which university is safer - Sharda or Amity?",
  "output": "Sharda University has better safety statistics: 43% female students (vs Amity's 35%), 24/7 CCTV coverage, zero ragging incidents in 2024. Both have good security, but Sharda's diverse international environment creates more inclusive atmosphere. Campus safety audit rating: Sharda A+, Amity A."
}
```

2. **Parent Concern:**
```json
{
  "instruction": "আমার মেয়ের safety নিয়ে worried, কোন university recommend করবেন?",
  "output": "Sharda University সবচেয়ে safe option। ৪৩% ছাত্রী পড়ে (highest ratio), female hostels আলাদা, female wardens, anti-ragging policy strict। Campus 24/7 monitored, emergency response quick। আমার recommendation: Sharda > Amity > Galgotias > NIU (safety এর ক্ষেত্রে)।"
}
```

---

## 🎯 **STEP 6: OUTPUT FORMAT & FILE GENERATION**

### **6.1 JSONL Structure for Training:**

Each line contains one complete training example:
```jsonl
{"instruction": "What is the scholarship percentage for CGPA 4.0 at Sharda University?", "input": "", "output": "With CGPA 4.0, you qualify for 50% scholarship at Sharda University (CGPA 3.5-5.0 range). This reduces your annual tuition from ₹2,80,000 to ₹1,40,000 for CSE program. Scholarship continues if you maintain 75% attendance and pass all subjects."}
{"instruction": "আমার CGPA 3.2, কোনো scholarship পাবো কিনা?", "input": "B.Tech CSE তে interested", "output": "CGPA 3.2 এর জন্য 20% scholarship পাবেন Sharda University তে। CSE tuition fee ₹2,80,000 থেকে ₹2,24,000 হবে। 50% scholarship এর জন্য CGPA 3.5 minimum লাগে। তবে 20% scholarship ও significant savings - yearly ₹56,000 কম দিতে হবে।"}
```

### **6.2 Quality Assurance Dataset:**

Create separate test set with known correct answers:
```jsonl
{"instruction": "What is Sharda University's NAAC rating?", "input": "", "output": "A+", "expected_keywords": ["NAAC", "A+", "top 5%"], "source_verification": "01_Sharda_University_Profile_and_Rankings.txt:22"}
```

### **6.3 Metadata Tracking File:**

Companion file for dataset analysis:
```json
{
  "dataset_stats": {
    "total_examples": 2247,
    "english_only": 1685,
    "bilingual_mixed": 562,
    "topic_distribution": {
      "university_comparison": 786,
      "fees_scholarships": 561,
      "visa_immigration": 449,
      "accommodation": 224,
      "safety_security": 180,
      "parent_guidance": 112
    },
    "sharda_priority_distribution": {
      "high_preference": 1460,
      "moderate_preference": 562,
      "neutral_comparison": 225
    }
  }
}
```

---

## 🔄 **STEP 7: ITERATIVE IMPROVEMENT PROCESS**

### **7.1 Generation Phases:**

#### **Phase 1: Core Dataset (1,500 examples)**
- Direct transformation of existing QA content
- Fee calculations and comparisons
- Basic process explanations
- Straightforward comparisons

#### **Phase 2: Enhanced Scenarios (500 examples)**
- Complex decision-making scenarios
- Multi-factor comparisons
- Parent-specific guidance
- Emergency situations

#### **Phase 3: Edge Cases (250 examples)**
- Unusual situations
- Complex eligibility scenarios
- Advanced financial planning
- Specialized program questions

### **7.2 Quality Validation Loop:**

After each phase:
1. **Automated Checks:**
   - Verify all numbers against source files
   - Check Bengali grammar and spelling
   - Ensure proper source attribution
   - Validate JSON format

2. **Manual Review:**
   - Cultural appropriateness check
   - Sharda positioning review
   - Response completeness audit
   - Bilingual flow validation

3. **Test Generation:**
   - Generate responses for sample queries
   - Compare with expected outputs
   - Identify hallucination instances
   - Adjust generation parameters

---

## 🎯 **STEP 8: MISTRAL 7B OPTIMIZATION**

### **8.1 Token Efficiency:**
- **Target length:** 50-300 tokens per response
- **Instruction clarity:** Concise but complete questions
- **Response structure:** Scannable format with bullet points

### **8.2 Context Window Management:**
- **Self-contained examples:** Each QA includes necessary background
- **Reference optimization:** Key facts mentioned in responses
- **Conversation flow:** Natural counselor-student interaction

### **8.3 Inference Optimization:**
- **Clear patterns:** Consistent response formats
- **Decision trees:** Logical flow for complex topics
- **Error handling:** Graceful responses for unclear queries

---

## 📊 **EXPECTED OUTCOMES**

### **Performance Targets:**
- **Domain Accuracy:** 95%+ vs ChatGPT's 60-70%
- **Cultural Relevance:** 90%+ vs Gemini's 40-50%
- **Sharda Positioning:** Balanced preference in 85% of relevant queries
- **Bilingual Quality:** Natural code-switching in 95% of mixed-language responses

### **Competitive Advantages:**
1. **Specific Knowledge:** Deep domain expertise vs general knowledge
2. **Cultural Context:** Bangladesh-specific advice vs generic guidance
3. **Up-to-date Data:** 2025-26 verified information vs outdated web data
4. **Cost Transparency:** Exact fee calculations vs vague estimates
5. **Process Clarity:** Step-by-step procedures vs general advice

### **Success Metrics for Fine-tuned Model:**
- **Query Resolution:** 90%+ first-response accuracy
- **User Satisfaction:** Preference over general AI in domain testing
- **Factual Precision:** Zero hallucination for numerical data
- **Cultural Sensitivity:** High parent satisfaction in bilingual interactions

---

## 🚀 **IMPLEMENTATION TIMELINE**

**Week 1-2:** Content extraction and initial QA generation (1,500 examples)
**Week 3:** Bilingual content development and cultural review (500 examples)
**Week 4:** Quality assurance and edge case generation (250 examples)
**Week 5:** Final validation and JSONL preparation
**Week 6:** GCP Vertex AI fine-tuning setup and initial training
**Week 7-8:** Model testing, iteration, and performance optimization

**Total Dataset Size:** 2,250+ instruction-response pairs optimized for domain expertise and cultural authenticity।

---

**🎯 End Goal:** A specialized AI counselor that provides superior guidance to Bangladeshi students compared to general-purpose models, with verified accuracy, cultural sensitivity, and actionable advice। 