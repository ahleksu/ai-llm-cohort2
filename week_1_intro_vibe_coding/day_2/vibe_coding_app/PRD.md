# 🧠 Product Requirements Document (PRD) – Vibe Coding App

## 💬 EMPATHIZE

### Users
- **Primary Users:** HR recruiters, hiring managers, and talent acquisition officers
- **Secondary Users:** Candidate applicants (indirect interaction through AI screening)

### User Needs
- Reduce manual resume screening time from hours to minutes
- Ensure objective, consistent, and bias-free candidate evaluations
- Provide standardized shortlists with transparent ranking criteria
- Enable faster turnaround for high-volume hiring cycles
- Maintain candidate experience quality during automated screening

### Pain Points
- **Manual bias:** Unconscious biases affect shortlisting decisions
- **Inconsistent scoring:** Different recruiters apply different standards
- **Time-intensive screening:** Reading 50+ resumes manually takes hours
- **Context switching:** Jumping between resume formats and tracking systems
- **Lost candidates:** Qualified candidates overlooked due to fatigue or volume
- **No audit trail:** Difficult to explain why candidates were rejected

### User Research Insights
> "I spend 3-4 hours daily just reading resumes for a single role. By the 30th resume, I lose focus and might miss great candidates."  
> — *HR Manager, interviewed during discovery phase*

> "We need consistency. Different recruiters score the same candidate differently, which creates internal conflicts."  
> — *Talent Acquisition Lead*

---

## 🎯 DEFINE

### Problem Statement
> **"HR teams struggle to efficiently identify qualified candidates due to repetitive manual screening, subjective evaluation criteria, and time constraints, resulting in inconsistent hiring outcomes and delayed time-to-hire metrics."**

### Target Audience
- **Enterprise HR Departments** (50-500 employees)
- **Recruitment Agencies** handling multiple clients
- **Startups** with limited HR capacity but high hiring needs

### Success Metrics

| Metric | Baseline | Target | Timeline |
|--------|----------|--------|----------|
| Time per candidate screening | 10-15 minutes | 2-3 minutes | 3 months |
| Consistency score (inter-rater reliability) | 65% | 90%+ | 6 months |
| HR satisfaction rating | N/A | 4.5/5 | Launch + 1 month |
| Candidate NPS (Net Promoter Score) | N/A | 70+ | Launch + 3 months |
| Cost per hire reduction | Baseline | -25% | 6 months |

### Core Value Proposition
**"Screen smarter, hire faster. AI-powered resume screening that eliminates bias, ensures consistency, and cuts screening time by 80%."**

---

## 💡 IDEATE

### Brainstorming Sessions Summary

#### Potential Solutions Explored
1. **Conversational AI Interviewer**
   - Simulates initial phone screening through text-based dialogue
   - Evaluates communication skills, motivation, and culture fit
   - Provides "vibe score" based on interaction quality

2. **Sentiment & Communication Tone Scoring**
   - Analyzes resume language for professionalism, confidence, clarity
   - Detects communication patterns matching company culture
   - Flags red flags (gaps, inconsistencies, overselling)

3. **Auto-Summarized Candidate Profile Card**
   - Generates "Vibe Summary" — a one-page candidate snapshot
   - Highlights key strengths, relevant experience, and match percentage
   - Includes AI-generated recommendation (Strong Fit / Consider / Pass)

4. **Top Candidate Shortlist Export**
   - Auto-ranks candidates by composite score
   - Exports top 10-15 candidates to HR dashboard
   - Includes interview question suggestions per candidate

5. **Bias Detection & Mitigation**
   - Flags potential bias triggers in job descriptions
   - Blinds candidate demographic data during screening
   - Tracks diversity metrics in shortlist outcomes

#### Selected Solution for MVP
**Hybrid Approach:** Conversational AI screening + Auto-summarized profile cards + Shortlist export

**Rationale:**
- Balances automation with human judgment
- Maintains candidate experience quality
- Provides explainable AI decisions
- Allows HR to focus on final interviews, not initial screening

---

## 🧪 PROTOTYPE

### Platform Architecture
- **Backend:** Python (Flask/FastAPI) hosted on Replit for rapid prototyping
- **Frontend:** v0.dev (Vercel) — minimalist, empathetic UI design
- **AI Engine:** OpenAI GPT-4 API for resume analysis and conversational screening
- **Data Storage:** Local JSON files for MVP, PostgreSQL for production

### User Flow

```
┌─────────────────────────────────────────────────────────────────┐
│  STEP 1: HR INPUTS JOB DETAILS                                  │
│  - Job title, required skills, experience level                 │
│  - Company culture keywords (optional)                           │
│  - Screening priorities (skills vs. experience vs. culture fit) │
└─────────────────────────────────────────────────────────────────┘
                              ↓
┌─────────────────────────────────────────────────────────────────┐
│  STEP 2: UPLOAD CANDIDATE RESUMES                               │
│  - Drag & drop PDF/DOCX resumes                                 │
│  - Batch upload (up to 50 resumes)                              │
│  - System validates and parses resume data                      │
└─────────────────────────────────────────────────────────────────┘
                              ↓
┌─────────────────────────────────────────────────────────────────┐
│  STEP 3: AI CHATBOT SCREENS CANDIDATES                          │
│  - Simulates initial screening questions                        │
│  - Evaluates resume content against job requirements            │
│  - Generates "Vibe Score" (0-100) based on:                     │
│    • Skills match (40%)                                          │
│    • Experience relevance (30%)                                  │
│    • Communication quality (20%)                                 │
│    • Culture fit indicators (10%)                                │
└─────────────────────────────────────────────────────────────────┘
                              ↓
┌─────────────────────────────────────────────────────────────────┐
│  STEP 4: VIEW RANKED CANDIDATES                                 │
│  - Sortable list by Vibe Score                                  │
│  - Candidate summary cards with key highlights                  │
│  - Export top candidates to CSV/PDF                             │
│  - Share shortlist with hiring manager                          │
└─────────────────────────────────────────────────────────────────┘
```

### Demo Dataset
- **Mock Resumes:** 30 fictional candidate profiles spanning various industries
- **Test Job Descriptions:** 5 sample roles (Software Engineer, Marketing Manager, Data Analyst, HR Coordinator, Sales Executive)
- **Conversation Samples:** Pre-scripted AI screening dialogues for testing

### Prototype Tools
- **Python Libraries:** `PyPDF2`, `docx2txt`, `openai`, `flask`
- **Frontend Framework:** v0.dev components with Tailwind CSS
- **Version Control:** Git + GitHub for iteration tracking
- **Testing:** Manual UAT with 5 HR staff members

---

## 🔬 TEST

### Testing Strategy

#### Phase 1: Internal Testing (Week 1-2)
- **Testers:** 3 HR staff members from original requester team
- **Focus:** Functionality, accuracy, usability

#### Phase 2: Expanded Testing (Week 3-4)
- **Testers:** 10 HR professionals across different departments
- **Focus:** Edge cases, bias detection, performance under load

### Feedback Summary

#### ✅ Positive Feedback
| Theme | Count | Representative Quote |
|-------|-------|---------------------|
| **Empathetic UI** | 8/10 | "The interface felt human, not robotic. I appreciated the conversational tone." |
| **Time Savings** | 10/10 | "I screened 40 resumes in under 2 hours. This would normally take me a full day." |
| **Accurate Summaries** | 7/10 | "The AI-generated summaries captured the key points I would have noted manually." |
| **Reduced Bias** | 6/10 | "I felt more objective because I wasn't seeing names or photos first." |

#### ⚠️ Areas for Improvement
| Issue | Count | Recommendation |
|-------|-------|----------------|
| **Scoring Transparency** | 9/10 | Users want to understand *why* a score was assigned. Add score breakdown feature. |
| **Overly Formal Tone** | 5/10 | Some found the AI too corporate. Add tone customization options. |
| **False Positives** | 4/10 | AI occasionally ranked irrelevant candidates high. Improve skills matching algorithm. |
| **No Feedback Loop** | 7/10 | Users couldn't correct AI mistakes. Add "Train AI" feature for edge cases. |

### Iteration Plan
1. **Priority 1:** Add scoring transparency dashboard showing weight distribution
2. **Priority 2:** Implement tone customization (Formal / Conversational / Casual)
3. **Priority 3:** Introduce feedback mechanism for HR to flag incorrect rankings
4. **Priority 4:** A/B test different vibe score formulas

---

## 📘 EPIC

> **As an HR recruiter**, I want an AI assistant that automates the initial resume screening process so I can focus my time on interviewing only the most qualified candidates, reducing time-to-hire and improving hiring quality.

---

## 📋 USER STORIES

| ID | User Story | Acceptance Criteria | Priority | Story Points |
|----|------------|---------------------|----------|--------------|
| **US-01** | As an HR officer, I want to input job requirements to customize candidate screening criteria. | • System captures job title, required skills (min 3), experience level (0-20 years), and optional culture keywords<br>• Validation prevents submission without mandatory fields<br>• Settings persist for reuse across similar roles | **HIGH** | 5 |
| **US-02** | As an HR officer, I want to upload resumes in bulk for AI analysis. | • System accepts .pdf and .docx formats<br>• Supports batch upload (5-50 resumes)<br>• Displays upload progress and parsing status<br>• Flags corrupted or unreadable files | **HIGH** | 8 |
| **US-03** | As an HR officer, I want to view candidate vibe scores and AI-generated summaries. | • Ranked list displays all candidates sorted by score (default: high to low)<br>• Each candidate card shows: Name, Vibe Score, Top 3 Skills, Experience Years, AI Summary (50-100 words)<br>• Sortable by Name, Score, or Upload Date | **HIGH** | 8 |
| **US-04** | As an HR officer, I want to understand how vibe scores are calculated. | • Clicking score reveals breakdown: Skills Match (%), Experience Relevance (%), Communication Quality (%), Culture Fit (%)<br>• Tooltips explain each scoring dimension<br>• Option to adjust weighting preferences | **MEDIUM** | 5 |
| **US-05** | As an HR officer, I want to export the top candidate shortlist. | • "Export Top 10" button generates CSV/PDF report<br>• Report includes candidate name, score, summary, and contact info<br>• Option to customize export count (top 5, 10, 15, or all) | **MEDIUM** | 3 |
| **US-06** | As a candidate, I want the AI screening to feel natural and respectful. | • AI chatbot uses conversational language (avoids jargon)<br>• Responses acknowledge candidate effort<br>• Error messages are empathetic, not blaming<br>• Processing time < 30 seconds per resume | **MEDIUM** | 5 |
| **US-07** | As an HR manager, I want to track screening analytics over time. | • Dashboard shows: Total resumes screened, Average score, Top skills identified, Time saved<br>• Filterable by date range and job role<br>• Exportable analytics report | **LOW** | 8 |
| **US-08** | As an HR officer, I want to flag and correct AI mistakes. | • "Report Issue" button on candidate cards<br>• HR can override scores or flag false positives<br>• Feedback trains AI model for future improvements | **LOW** | 8 |

---

## 🧱 TECHNICAL REQUIREMENTS

### Backend Stack
- **Language:** Python 3.10+
- **Framework:** Flask (MVP) → FastAPI (production for async performance)
- **AI Integration:** OpenAI GPT-4 API (fallback: GPT-3.5-turbo for cost optimization)
- **Resume Parsing:** `PyPDF2` (PDF), `python-docx` (DOCX), `pdfplumber` (complex layouts)
- **Hosting:** Replit (prototype) → AWS Lambda / Google Cloud Run (production)

### Frontend Stack
- **Framework:** v0.dev (Vercel) — React-based minimalist UI
- **Styling:** Tailwind CSS for responsive design
- **Components:** Shadcn UI for accessible, consistent elements
- **Deployment:** Vercel for instant deployment and CDN

### Data Handling
- **MVP:** Local JSON files (`candidates.json`, `jobs.json`, `scores.json`)
- **Production:** PostgreSQL for relational data, AWS S3 for resume file storage
- **Security:** Resume files deleted after 30 days, GDPR-compliant data handling

### API Architecture
```
POST /api/jobs           → Create new job screening request
POST /api/upload         → Upload resumes for screening
GET  /api/candidates/:id → Retrieve candidate details
POST /api/screen         → Trigger AI screening process
GET  /api/results/:jobId → Get ranked candidate list
POST /api/feedback       → Submit HR feedback on AI decisions
```

### Performance Requirements
- **Resume Processing Time:** < 15 seconds per resume
- **Concurrent Users:** Support 20 HR users simultaneously (MVP), 100+ (production)
- **Uptime SLA:** 99.5% (MVP), 99.9% (production)
- **Data Privacy:** SOC 2 Type II compliance for production

---

## 🚀 NEXT STEPS

### Immediate (Next Sprint)
1. ✅ **Integrate sentiment analysis model** for "Vibe Scoring" refinement
2. ✅ **Add scoring transparency feature** (breakdown modal)
3. ✅ **Implement tone customization** (3 preset modes)

### Short-Term (1-3 Months)
4. 📊 **Build analytics dashboard** for HR managers
5. 🔄 **Add feedback loop mechanism** for AI training
6. 🎨 **Improve UI empathy** based on user testing insights
7. 🔒 **Implement role-based access control** (Recruiter vs. Manager permissions)

### Long-Term (3-6 Months)
8. 🌍 **Multi-language support** for global hiring
9. 🤖 **Train custom ML model** on company-specific hiring patterns
10. 📱 **Mobile app version** for on-the-go screening
11. 🔗 **Integrate with ATS systems** (Greenhouse, Lever, Workday)

---

## 📊 RISK ASSESSMENT

| Risk | Impact | Probability | Mitigation Strategy |
|------|--------|-------------|---------------------|
| AI produces biased results | HIGH | MEDIUM | Implement bias detection, diverse training data, regular audits |
| GDPR/privacy violations | HIGH | LOW | Legal review, data encryption, auto-deletion policies |
| API cost overruns | MEDIUM | HIGH | Implement rate limiting, use GPT-3.5 for non-critical tasks, cache results |
| User adoption resistance | MEDIUM | MEDIUM | Pilot with friendly teams, emphasize time savings, provide training |
| False negatives (missing good candidates) | MEDIUM | MEDIUM | Tunable sensitivity settings, HR override options, continuous model improvement |

---

## ✅ DEFINITION OF DONE

This PRD is considered complete when:
- [x] All Design Thinking stages documented (Empathize, Define, Ideate, Prototype, Test)
- [x] EPIC and User Stories defined with acceptance criteria
- [x] Technical requirements specified for MVP and production
- [x] Success metrics and KPIs established
- [x] Risk mitigation strategies outlined
- [x] Next steps roadmap created

---

**Document Version:** 1.0  
**Last Updated:** October 19, 2025  
**Owner:** PSI AI Academy Scholar (HR Vibe Coding Project)  
**Stakeholders:** HR Department, Talent Acquisition Team, Engineering Team
