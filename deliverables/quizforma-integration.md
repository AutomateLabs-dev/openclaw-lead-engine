# Quizforma Integration (Future Automation)
## Lead Qualification + Routing Automation

---

## Overview

**Current State:** Manual DM conversations for classification
**Future State:** Automated quiz qualifies leads, routes to appropriate tier
**Benefit:** Scale without linear headcount increase
**Timeline:** Phase 2 (after manual process is proven)

---

## Quiz Structure

### Quiz 1: Entry Qualification

**Question 1: What best describes you?**
- [ ] I'm exploring for personal use/side project
- [ ] I run a business and want to implement this
- [ ] I'm an agency/consultant with clients
- [ ] Just curious, not sure yet

**Branching:**
- Personal → Quiz 2A
- Business → Quiz 2B
- Agency → Quiz 2C
- Unclear → Manual follow-up

---

### Quiz 2A: Personal User Path

**Question 1: What's your main goal?**
- [ ] Learn AI tools
- [ ] Automate personal tasks
- [ ] Build something specific
- [ ] Not sure yet

**Question 2: Have you used AI tools before?**
- [ ] Yes, regularly
- [ ] A little bit
- [ ] Never

**Result:**
- Experienced → Direct to CourseSprout signup
- New → CourseSprout + onboarding offer

---

### Quiz 2B: Business Path

**Question 1: What type of business?**
- [ ] Agency/Marketing
- [ ] Coaching/Consulting
- [ ] E-commerce
- [ ] SaaS/Tech
- [ ] Other service business

**Question 2: Team size?**
- [ ] Just me
- [ ] 2-5 people
- [ ] 6-20 people
- [ ] 20+ people

**Question 3: What's your biggest pain point?**
- [ ] Not enough leads
- [ ] Poor conversion
- [ ] Content creation
- [ ] Operations/overwhelm
- [ ] Product delivery

**Question 4: Timeline?**
- [ ] ASAP (this month)
- [ ] Next 2-3 months
- [ ] This year
- [ ] Just exploring

**Result Calculation:**
- High urgency + clear pain point → Book call with Dave
- Medium urgency → Send case study + call booking
- Low urgency/just exploring → Add to nurture sequence

---

### Quiz 2C: Agency Path

**Question 1: How many clients do you serve?**
- [ ] 1-5
- [ ] 6-20
- [ ] 21-50
- [ ] 50+

**Question 2: What's your interest?**
- [ ] Use internally for delivery
- [ ] Offer as service to clients
- [ ] White-label platform
- [ ] Not sure yet

**Question 3: Monthly revenue?**
- [ ] Under $10K
- [ ] $10K-$50K
- [ ] $50K-$100K
- [ ] $100K+

**Result:**
- White-label interest + established → Partner call with Dave
- Internal use → Business path pricing
- Exploration → Agency nurture sequence

---

## Integration Points

### Facebook → Quiz

**Current Flow:**
Comment "openclaw" → Manual DM → Classification

**Future Flow:**
Comment "openclaw" → Auto-DM with quiz link → Complete quiz → Auto-route

**Auto-DM Message:**
```
Hey! Saw your comment 👍

To point you in the right direction, quick 2-minute quiz:

[Quizforma Link]

Takes 2 min — then I'll know exactly how to help.
```

---

## Quizforma → Actions

### If Personal + Experienced
- Redirect to: CourseSprout checkout
- Email: Welcome sequence
- Tag: DIY-Experienced

### If Personal + New
- Redirect to: CourseSprout checkout
- Email: Welcome + onboarding offer
- Tag: DIY-New

### If Business + High Intent
- Redirect: Calendly booking (Dave's calendar)
- Email: Pre-call prep
- Tag: Business-Hot
- Slack notification to Dave

### If Business + Medium Intent
- Redirect: Case study download
- Email: Nurture sequence + soft CTA
- Tag: Business-Warm

### If Agency + Qualified
- Redirect: Partner application form
- Email: Agency program info
- Tag: Agency-Partner
- Slack notification to Dave

---

## Scoring Logic

### Business Lead Score

| Factor | Points |
|--------|--------|
| Team size 6+ | +20 |
| Urgency: ASAP | +30 |
| Clear pain point | +20 |
| Revenue $50K+ | +20 |
| Timeline: This year | +10 |

**Score Ranges:**
- 80-100: Hot lead → Immediate call booking
- 50-79: Warm lead → Nurture + soft CTA
- 0-49: Cold lead → Long-term nurture

---

## Automation Rules

### Immediate Actions (No Delay)
- Hot business lead → Slack notification + Dave email
- Agency partner → Flag for manual review
- CourseSprout signup → Welcome email

### Delayed Actions
- 1 hour after quiz completion: Follow-up email if no action
- 24 hours: Nurture email with relevant content
- 7 days: Soft re-engagement

### Conditional Actions
- If started quiz but didn't finish: "Forgot to finish?" email
- If finished but didn't buy: Objection-handler sequence
- If bought DIY but no activity in 3 days: Onboarding offer

---

## Data Flow

```
Facebook Comment
    ↓
Auto-DM with Quiz Link
    ↓
Quizforma Completion
    ↓
Score Calculation
    ↓
Branch to Path
    ↓
Action (Booking/Signup/Nurture)
    ↓
CRM Update
    ↓
Notification (if hot lead)
```

---

## CRM Integration

**Fields to Capture:**
- Name
- Email
- Facebook profile
- Quiz completion date
- Category (Personal/Business/Agency)
- Score
- Path assigned
- Actions taken

**Sync:**
- Quizforma → CRM (Zapier or direct integration)
- CRM → Email platform
- CRM → Slack (for notifications)

---

## Benefits of Quiz Automation

### Scale
- Handle 100+ comments/day without linear headcount
- 24/7 qualification (no waiting for DM response)
- Consistent scoring and routing

### Quality
- Data-driven qualification (not gut feel)
- Complete information before human touch
- Pre-framed prospects (they understand tiers)

### Speed
- Instant routing (no 24-hour lag)
- Hot leads flagged immediately
- Self-serve option for ready buyers

---

## Implementation Plan

### Phase 1: Manual (Now)
- Prove scripts work
- Understand objections
- Define qualification criteria
- Build initial customer base

### Phase 2: Hybrid (Month 2-3)
- Quiz for initial classification
- Human takes over after quiz
- Refine scoring based on data

### Phase 3: Full Automation (Month 4+)
- Complete self-serve for DIY
- Automated nurture sequences
- Human only for business calls

---

## Quizforma Setup Requirements

**Quiz Builder:**
- Conditional logic
- Scoring system
- Result routing
- CRM integration

**Current Options:**
- Typeform (easy, expensive)
- Quizforma (designed for this)
- Custom build (more control, more time)

**Recommendation:** Start with Typeform/Quizforma for speed, migrate to custom if scale demands it.

---

## Success Metrics

**Quiz Performance:**
- Start rate: % who click quiz link
- Completion rate: % who finish
- Accuracy: % correctly classified
- Conversion: % who take next step

**Compare to Manual:**
- Response time (quiz: instant vs manual: hours)
- Classification accuracy
- Conversion rate
- Cost per lead (quiz: setup cost vs manual: ongoing time)

---

## When to Implement

**Wait if:**
- Manual process not yet proven
- Less than 50 leads processed
- Scripts still changing frequently

**Build when:**
- 5+ hours/day spent on DM management
- Classification criteria are stable
- Clear patterns in qualification
- Ready to scale volume

---

## Notes for Future Implementation

**Keep it simple initially:**
- 3-5 questions max
- Clear branching
- Fast load time
- Mobile-optimized

**Don't over-automate:**
- Business leads still get human touch
- Complex objections need conversation
- Relationship matters for high-ticket

**Measure everything:**
- Drop-off points in quiz
- Conversion by path
- Revenue by source
- Time saved vs manual
