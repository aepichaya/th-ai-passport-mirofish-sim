# 04_public_opinion_signals.md

> Seed material สำหรับใช้กับ MiroFish simulation  
> Project: AI Pass TH / TH-AI Passport  
> Generated: 2026-06-11  
> Coverage window: 2025-11-17 ถึง 2026-06-11  
> Method: qualitative signal extraction from public news, government statements, expert commentary, political debate, and visible social/media framing.  
> Limitation: ไม่ใช่ social listening เชิงสถิติแบบ scrape ทุกโพสต์ แต่เป็นชุดสัญญาณเชิงคุณภาพจากแหล่งข่าวสาธารณะล่าสุดสำหรับใช้เป็น simulation seed.

---

## 1. Executive Summary

กระแสสาธารณะของโครงการ TH-AI Passport อยู่ในภาวะ **high-attention / low-trust / high-polarization** กล่าวคือ ประชาชนและสื่อให้ความสนใจสูง เพราะโครงการมีทั้งงบประมาณขนาดใหญ่ ประเด็น AI ที่กำลังเป็นกระแส และคำมั่นว่าจะให้ประชาชน 5 ล้านคนเข้าถึง AI ระดับ Pro เป็นเวลา 1 ปี แต่ความไว้วางใจต่อโครงการยังเปราะบาง เนื่องจากมีคำถามต่อความคุ้มค่า ความโปร่งใสของ TOR / e-bidding ความสัมพันธ์ของผู้ชนะประมูล ความเหมาะสมของการใช้งบซื้อบริการ AI จากต่างประเทศ และความสามารถในการทำให้คนทั่วไปใช้งานจริงหลังได้รับสิทธิ์

ภาพรวม sentiment ณ 2026-06-11:

- **Supportive but conditional**: เห็นด้วยกับเป้าหมายการเพิ่ม AI literacy และลด digital divide แต่ต้องการรายละเอียด KPI, data governance, token allocation, และผลลัพธ์เชิงเศรษฐกิจ
- **Skeptical / critical**: ตั้งคำถามเรื่องงบ 1.6 พันล้านบาท, TOR, ระยะเวลาประมูล, ผู้รับจ้าง, ราคากลาง, เงื่อนไขการเบิกจ่าย และการพึ่งพา vendor ต่างประเทศ
- **Constructive expert intervention**: กลุ่มผู้ประกอบการ/ผู้เชี่ยวชาญ AI ไม่ได้ปฏิเสธเป้าหมายโครงการทั้งหมด แต่เสนอให้ปรับเป็นระบบที่ช่วย ecosystem ไทย เช่น API access, Thai LLM, token transparency, infrastructure, และการใช้งานจริงตามกลุ่มเป้าหมาย
- **Government defensive-reframing**: ภาครัฐพยายาม reframe จาก “แจก AI ฟรี” เป็น “ลงทุนเพื่ออนาคต / Learn to Earn / AI adoption 5 ล้านคน / ใช้งานจริงจ่ายจริง / โปร่งใสทุกขั้นตอน”

---

## 2. Core Public Opinion Signals

### Signal 01: “งบ 1.6 พันล้าน” กลายเป็น framing หลักของกระแส

**Signal type:** Budget skepticism  
**Sentiment:** Negative / suspicious  
**Intensity:** High  
**Primary agents:** general public, opposition politicians, tech community, media  
**Trigger phrase examples:**

- “1.6 พันล้านคุ้มจริงหรือ?”
- “แจก AI ฟรี 5 ล้านสิทธิ์”
- “ละลายงบหรือไม่”
- “คนไทยได้อะไร”

**Observation:**  
แม้รัฐพยายามอธิบายว่าต้นทุนเฉลี่ยประมาณ 324 บาทต่อคนต่อปี หรือประมาณ 27 บาทต่อเดือน แต่ public framing ที่สื่อใช้บ่อยยังเริ่มต้นจาก “โครงการ 1.6 พันล้าน” ทำให้ emotional entry point ของประชาชนจำนวนมากคือ “เงินก้อนใหญ่” มากกว่า “ต้นทุนต่อหัวต่ำ”

**MiroFish implication:**  
Budget frame จะเป็น narrative ที่ติดง่ายที่สุดในกลุ่มประชาชนทั่วไปและสื่อการเมือง หากไม่มี KPI เชิงผลลัพธ์ที่จับต้องได้ public sentiment จะเคลื่อนจาก curiosity ไปสู่ suspicion ได้เร็ว

**Simulation variables:**

```yaml
budget_skepticism:
  base_intensity: 0.80
  escalation_triggers:
    - no_public_dashboard
    - unclear_cost_per_active_user
    - low_registration_quality
    - political_attack_repetition
  deescalation_triggers:
    - transparent_cost_breakdown
    - active_user_dashboard
    - pay_as_used_contract_terms
    - independent_audit
```

---

### Signal 02: ความโปร่งใสด้าน TOR และ e-bidding เป็นจุดเสี่ยงสูงสุดของ trust

**Signal type:** Procurement trust risk  
**Sentiment:** Negative / investigative  
**Intensity:** Very High  
**Primary agents:** opposition politicians, journalists, civic tech groups, tech practitioners  
**Key public questions:**

- ทำไมโครงการวงเงินสูงจึงเปิดให้ยื่นข้อเสนอในระยะเวลาสั้น
- TOR มีเงื่อนไขที่เอื้อผู้เล่นบางรายหรือไม่
- ผู้ชนะประมูลมีศักยภาพเพียงพอกับมูลค่างานหรือไม่
- ทำไมราคาผู้เสนอแต่ละรายใกล้กันมาก
- การจัดซื้อรวมบริการ AI, training, PR และ platform ไว้ในสัญญาเดียวทำให้ตรวจสอบยากหรือไม่

**Observation:**  
สัญญาณจากสื่อและการเมืองระบุว่าข้อกังวลไม่ได้อยู่แค่ “ควรให้คนไทยใช้ AI หรือไม่” แต่ย้ายไปที่ “กระบวนการจัดซื้อจัดจ้างน่าเชื่อถือแค่ไหน” ซึ่งเป็น narrative ที่ทำลาย trust ได้แรงกว่า debate เชิงนโยบายทั่วไป

**MiroFish implication:**  
เมื่อ procurement trust risk ขึ้นเป็น dominant narrative ต่อให้โครงการมีประโยชน์จริง ก็อาจถูกตีความผ่านกรอบ “เอื้อทุน / ล็อกสเปก / เงินทอน” ก่อนเสมอ

**Simulation variables:**

```yaml
procurement_trust_risk:
  base_intensity: 0.90
  keywords:
    - TOR
    - e-bidding
    - ล็อกสเปก
    - ฮั้วประมูล
    - ผู้ชนะประมูล
    - ราคากลาง
    - เงินทอน
  escalation_triggers:
    - new_document_leak
    - unclear_bidder_qualification
    - no_independent_review
    - hostile_parliament_session
  deescalation_triggers:
    - full_contract_disclosure
    - third_party_procurement_audit
    - public_q_and_a_with_documents
```

---

### Signal 03: รัฐบาลพยายาม reframe เป็น “AI literacy / Learn to Earn / ลดเหลื่อมล้ำ”

**Signal type:** Government benefit narrative  
**Sentiment:** Supportive / defensive  
**Intensity:** Medium-High  
**Primary agents:** MDES, government communicators, pro-government media  
**Narrative pillars:**

- ไทยมี AI adoption ต่ำกว่าหลายประเทศในอาเซียน
- โครงการจะช่วยให้คนไทย 5 ล้านคนเข้าถึง AI Pro
- ต้นทุนเฉลี่ยต่อคนต่ำเมื่อเทียบกับราคาบริการ AI Pro ทั่วไป
- โครงการไม่ใช่แค่แจก AI ฟรี แต่มี training, bootcamp, test, campaign และ Learn to Earn
- ข้อมูลผู้ใช้และ prompt จะไม่ถูกนำไป train และจะจัดเก็บในประเทศไทยแบบ anonymized

**Observation:**  
ข้อความรัฐพยายามเปลี่ยนโจทย์จาก “subscription subsidy” ไปเป็น “national AI capability program” แต่การ reframe ยังชนกับคำถามเรื่อง procurement และ outcome measurement

**MiroFish implication:**  
Narrative ฝั่งรัฐมีโอกาสชนะเฉพาะเมื่อเชื่อมกับ proof points ที่เห็นได้จริง เช่น dashboard, cohort training, use case by occupation, active usage, and income/productivity evidence

**Simulation variables:**

```yaml
government_reframe_strength:
  base_intensity: 0.62
  message_pillars:
    - ai_literacy
    - learn_to_earn
    - digital_inclusion
    - global_competitiveness
    - cost_per_person
  weaknesses:
    - trust_gap
    - lack_of_outcome_kpi
    - procurement_suspicion
```

---

### Signal 04: Tech community ไม่ได้คัดค้าน AI adoption แต่คัดค้าน design และ governance

**Signal type:** Expert constructive criticism  
**Sentiment:** Skeptical but constructive  
**Intensity:** High  
**Primary agents:** AI practitioners, developers, AI entrepreneurs, startup ecosystem  
**Core critique themes:**

- ต้องมี token strategy ไม่ใช่แจกสิทธิ์แบบ generic
- ต้องแยกกลุ่มผู้ใช้ตาม use case และระดับงาน
- ควรเปิด API ให้นักพัฒนาใช้สร้างนวัตกรรม
- ควรสนับสนุน Thai LLM / local AI ecosystem
- ต้องรายงานการใช้ token อย่างโปร่งใส
- ต้องมี infrastructure ภายในประเทศเพื่อไม่ให้เงินไหลออกไปซื้อบริการต่างชาติอย่างเดียว

**Observation:**  
เสียงจากกลุ่มผู้เชี่ยวชาญมีลักษณะ “คัดค้านวิธีทำมากกว่าเป้าหมาย” ซึ่งเป็นกลุ่มสำคัญใน simulation เพราะสามารถเปลี่ยนจาก critic เป็น validator ได้ หากรัฐปรับ governance และเปิดข้อมูลเชิงเทคนิค

**MiroFish implication:**  
Tech experts คือ swing agents ที่สำคัญ ถ้ารัฐตอบ technical detail ได้ดี กระแสอาจเปลี่ยนจาก scandal framing เป็น policy improvement framing

**Simulation variables:**

```yaml
tech_community_alignment:
  base_alignment: 0.35
  can_shift_to_support_if:
    - api_access_for_developers
    - thai_llm_inclusion
    - token_usage_dashboard
    - open_technical_spec
    - security_architecture_disclosure
  can_shift_to_opposition_if:
    - vague_technical_answers
    - vendor_lock_in_signals
    - privacy_uncertainty
    - no_local_ecosystem_budget
```

---

### Signal 05: “ใช้งานจริงเท่าไร” เป็นคำถาม outcome สำคัญที่สุด

**Signal type:** Adoption and retention concern  
**Sentiment:** Skeptical / pragmatic  
**Intensity:** High  
**Primary agents:** general public, economists, SME groups, educators, journalists  
**Key questions:**

- ผู้ได้รับสิทธิ์ 5 ล้านคนจะใช้งานจริงกี่คน
- ใช้งานต่อเนื่องกี่เดือน
- คนที่ไม่เคยใช้ AI จะเริ่มอย่างไร
- โครงการมี onboarding / template / workflow ตามอาชีพหรือไม่
- วัด productivity, income uplift, cost saving หรือ learning outcome อย่างไร
- หาก active usage ต่ำ จะมีระบบลดค่าใช้จ่ายหรือ reclaim งบหรือไม่

**Observation:**  
รัฐชี้ว่ามีกิจกรรม training, test, bootcamp, contest และการใช้งานผ่าน platform แต่ public skepticism ยังมุ่งไปที่ความเสี่ยง “สมัครเพราะฟรี แล้วไม่ใช้ต่อ” หรือ “ใช้เฉพาะกลุ่มที่ใช้ AI เป็นอยู่แล้ว”

**MiroFish implication:**  
Retention KPI จะเป็นตัวตัดสินว่ากระแสหลังเปิดใช้จริงจะเป็น positive proof หรือ negative backlash

**Simulation variables:**

```yaml
adoption_risk:
  registration_spike_probability: 0.80
  retention_drop_risk: 0.70
  high_value_user_segments:
    - students
    - teachers
    - freelancers
    - SME owners
    - office workers
    - developers
  low_retention_triggers:
    - weak_onboarding
    - confusing_token_limits
    - no_job_specific_use_cases
    - slow_platform
    - limited_model_access
```

---

### Signal 06: Privacy และ data governance ถูกใช้เป็น trust test

**Signal type:** Data protection concern  
**Sentiment:** Concerned / conditional  
**Intensity:** Medium  
**Primary agents:** tech community, privacy advocates, educated users, media  
**Key questions:**

- Prompt และ user data ถูกเก็บที่ไหน
- ใครเป็น data controller / processor
- เจ้าของโมเดล AI ต่างประเทศเข้าถึงข้อมูลอะไรบ้าง
- “Anonymous” ทำอย่างไร และ audit ได้หรือไม่
- การ verify ผ่าน Thai ID ผูกกับ usage logs หรือไม่
- มี Data Processing Agreement และ Privacy Impact Assessment หรือไม่

**Observation:**  
รัฐสื่อสารว่าผู้ให้บริการ AI จะไม่สามารถนำข้อมูลผู้ใช้ไป train ต่อ ข้อมูล User และ Prompt จะจัดเก็บบน cloud ในประเทศไทย และเข้าถึงเฉพาะในรูปแบบ anonymous แต่คำอธิบายนี้ยังต้องการ technical/legal artifact เพื่อสร้างความเชื่อมั่นในกลุ่มผู้เชี่ยวชาญ

**MiroFish implication:**  
Privacy concern ยังไม่ใช่ dominant mass narrative เท่ากับงบ/TOR แต่เป็น trigger ที่สามารถขยายแรงมากหากเกิดข่าวข้อมูลรั่วหรือมีการอธิบายผิดพลาด

**Simulation variables:**

```yaml
privacy_trust:
  base_concern: 0.55
  escalation_triggers:
    - unclear_thai_id_linkage
    - unclear_model_provider_data_flow
    - data_breach_news
    - no_dpa_or_pia_disclosure
  deescalation_triggers:
    - data_flow_diagram
    - privacy_impact_assessment
    - third_party_security_audit
    - plain_language_privacy_policy
```

---

### Signal 07: เวทีรับฟัง 11 มิ.ย. 2569 เป็น trust-recovery attempt แต่ยังไม่ปิดประเด็น

**Signal type:** Trust recovery event  
**Sentiment:** Mixed  
**Intensity:** Medium-High  
**Primary agents:** MDES, experts, opposition, media  
**Observation:**  
วันที่ 11 มิ.ย. 2569 กระทรวงดีอีเปิด TH-AI Passport Forum เพื่อรับฟังความคิดเห็นจากนักวิชาการ ผู้เชี่ยวชาญ ภาคธุรกิจ และประชาชนทั่วไป พร้อมย้ำว่าโครงการดำเนินตามขั้นตอน และยังอยู่ในช่วงบริหารสัญญาที่สามารถนำข้อเสนอไปปรับปรุงได้

**Positive effect:**  
ช่วยให้รัฐดู “เปิดรับฟัง” และเปิดพื้นที่ให้คำถามเข้าสู่กระบวนการ

**Negative risk:**  
หากเวทีถูกมองว่าเป็นการสื่อสารทางเดียวหรือไม่เปิดเอกสารสำคัญ กระแสจะกลายเป็น “ฟอกขาว” หรือ “ซื้อเวลา”

**MiroFish implication:**  
Forum เป็น inflection point ระยะสั้น แต่ผลต่อ trust ขึ้นกับ post-forum action มากกว่าตัวเวทีเอง

**Simulation variables:**

```yaml
forum_effect:
  initial_trust_gain: 0.10
  decay_rate_if_no_followup: 0.70
  required_followup:
    - publish_forum_minutes
    - publish_q_and_a
    - publish_contract_summary
    - publish_kpi_dashboard_plan
    - publish_change_log_after_feedback
```

---

### Signal 08: “ใช้งานจริงเท่าไร จ่ายเท่านั้น” เป็น narrative ใหม่ที่ลดแรงต้านได้

**Signal type:** Contract value-control narrative  
**Sentiment:** Potentially positive  
**Intensity:** Medium  
**Primary agents:** MDES, public finance observers, journalists  
**Observation:**  
กระทรวงสื่อสารว่าการบริหารสัญญาจะยึดหลัก “ใช้งานจริงเท่าไร จ่ายเท่านั้น” ซึ่งเป็นข้อความสำคัญเพราะตอบข้อกังวลเรื่องจ่ายเต็มงบแม้ผู้ใช้จริงต่ำ อย่างไรก็ตาม ต้องมีรายละเอียดกลไกคำนวณ จ่ายตามอะไร active user, token usage, capacity reservation, monthly cap, SLA หรือ outcome

**MiroFish implication:**  
หากมีเอกสารสัญญารองรับ narrative นี้จะลด budget backlash ได้มาก แต่ถ้าไม่มีหลักฐานจะกลายเป็นคำพูดที่ถูกท้าทายซ้ำ

**Simulation variables:**

```yaml
pay_as_used_claim:
  trust_gain_if_documented: 0.25
  trust_loss_if_undocumented: 0.20
  required_evidence:
    - payment_milestone_terms
    - usage_metering_method
    - audit_rights
    - unused_capacity_refund_or_rollover
```

---

### Signal 09: Media amplification กระจายทั้งข่าว บทวิเคราะห์ รายการ และวิดีโอ

**Signal type:** Media amplification  
**Sentiment:** Mixed, leaning critical  
**Intensity:** High  
**Primary channels:**

- Thai PBS: explainer + expert criticism + procurement timeline
- Thairath: parliamentary conflict, forum coverage, government clarification
- Thansettakij: budget/procurement concern and bidder questions
- Dailynews / Spacebar: AIEAT constructive recommendations
- YouTube news/talk shows: framing เช่น “คุ้มจริงหรือ”, “วิจารณ์ยับ”, “ไปต่อหรือพอแค่นี้”

**Observation:**  
กระแสไม่ได้อยู่เฉพาะ social media แต่ถูกยกขึ้นเป็น agenda ของสื่อหลักและรายการวิเคราะห์การเมือง/เศรษฐกิจแล้ว ทำให้กระแสมี shelf-life มากกว่า viral post ปกติ

**MiroFish implication:**  
Media agents ควรมีบทบาท “amplifier” ที่ทำให้ประเด็นเล็กกลายเป็นประเด็นระดับชาติ โดยเฉพาะเมื่อมีนักการเมืองหรือผู้เชี่ยวชาญให้คำพูดใหม่

**Simulation variables:**

```yaml
media_amplification:
  base_strength: 0.75
  strong_triggers:
    - parliamentary_exchange
    - new_expert_statement
    - procurement_document_dispute
    - public_forum_conflict
    - influencer_thread
  decay_condition:
    - no_new_information_for_7_days
```

---

### Signal 10: Local AI ecosystem narrative เป็น white-space ของฝั่งวิจารณ์เชิงสร้างสรรค์

**Signal type:** Policy alternative narrative  
**Sentiment:** Constructive / strategic  
**Intensity:** Medium-High  
**Primary agents:** AI entrepreneurs, local tech ecosystem, universities, developers  
**Core argument:**  
แทนที่จะใช้งบส่วนใหญ่เพื่อซื้อ access จากต่างประเทศ โครงการควรมีส่วนที่สร้าง capability ภายในประเทศ เช่น Thai LLM, GPU/AI server, developer credit, API ecosystem, startup sandbox, SME workflow packs และ public benchmark

**Observation:**  
Narrative นี้มีพลังเพราะไม่ใช่การปฏิเสธ AI แต่เสนอว่า “AI budget should build Thailand’s AI capacity, not only rent foreign AI access.”

**MiroFish implication:**  
ถ้ารัฐเพิ่ม local ecosystem component กระแส expert criticism อาจ soft landing ได้

**Simulation variables:**

```yaml
local_ecosystem_demand:
  base_intensity: 0.65
  groups:
    - ai_startups
    - thai_llm_researchers
    - universities
    - developer_communities
    - sme_platforms
  policy_actions_that_reduce_criticism:
    - thai_llm_support
    - developer_api_credit
    - local_ai_infrastructure_fund
    - public_model_benchmark
```

---

## 3. Stakeholder Sentiment Matrix

| Stakeholder | Current sentiment | Trust level | Main concern | What could shift them positive |
|---|---:|---:|---|---|
| MDES / Government | Supportive / defensive | High self-confidence | Public trust gap | Document disclosure, dashboard, measurable outcomes |
| Opposition politicians | Critical | Very low | TOR, bidder, budget, political linkage | Independent audit, full contract transparency |
| AI practitioners / developers | Skeptical constructive | Low-medium | Technical design, token, privacy, vendor lock-in | API, Thai LLM, open spec, transparent token usage |
| AI entrepreneurs / AIEAT-like groups | Constructive critical | Medium | Local ecosystem not prioritized | Developer access, local model support, infrastructure |
| General public | Curious but suspicious | Medium-low | Tax spending, free benefit, ease of use | Clear signup flow, visible real use cases, success stories |
| Students / teachers | Potentially supportive | Medium | Access, ease of learning, plagiarism concern | Free access + guided learning path + templates |
| SME owners | Pragmatic | Medium | Usefulness for real business | SME playbooks, marketing/accounting workflows, mentors |
| Journalists | Investigative | Low-medium | Documents, conflicts, accountability | Public data room, direct Q&A, independent verification |
| AI vendors | Supportive but cautious | Medium-high | Brand risk, government backlash | Clear scope, privacy guarantees, public success metrics |

---

## 4. Timeline of Public Opinion Triggers

| Date | Event / Trigger | Signal effect |
|---|---|---|
| 2025-11-17 | เผยแพร่แผนจัดซื้อจัดจ้าง | Later used as transparency defense by government |
| 2025-12-15 ถึง 2025-12-22 | เปิดรับฟังความคิดเห็นร่าง TOR | Later debated whether public consultation was sufficient |
| 2025-12-24 ถึง 2026-01-26 | ประกาศเชิญชวนผู้ยื่นข้อเสนอ | “34 days” becomes criticism anchor |
| 2026-01-27 | เปิดเสนอราคา | Bid process becomes later controversy |
| 2026-05-08 | Media scrutiny expands around budget/procurement | Budget skepticism becomes public agenda |
| 2026-05-28 | Parliamentary questioning; MDES issues transparency defense | Political conflict raises awareness |
| 2026-06-01 | Korn Chatikavanij raises 5 questions in media | Economic/value-for-money frame expands |
| 2026-06-03 | AIEAT proposes 8 recommendations | Expert community moves to constructive policy alternative |
| 2026-06-08 | Senate live question; MDES responds | “เงินทอน / ป.ป.ช. / โปร่งใส” narrative intensifies |
| 2026-06-10 | Thai PBS publishes explainers and expert roundup | Mainstream issue consolidation |
| 2026-06-11 | TH-AI Passport Forum | Trust recovery attempt and new scrutiny point |

---

## 5. Dominant Narratives for Simulation

### Narrative A: “ลงทุนเพื่ออนาคต คนไทยไม่ตกขบวน AI”

- **Source agents:** Government, supportive educators, some SME users
- **Emotional frame:** Hope, opportunity, national competitiveness
- **Core claim:** Thailand needs mass AI access now
- **Vulnerability:** Needs proof of real adoption and productivity gain

### Narrative B: “แจก AI ฟรีด้วยงบ 1.6 พันล้าน คุ้มจริงหรือ”

- **Source agents:** Media, taxpayers, opposition, general public
- **Emotional frame:** Suspicion, fiscal caution
- **Core claim:** Big budget must show concrete ROI
- **Vulnerability:** Can be countered by cost-per-active-user and pay-as-used evidence

### Narrative C: “TOR / ประมูล / ผู้ชนะ มีพิรุธหรือไม่”

- **Source agents:** Opposition, investigative journalists, civic tech community
- **Emotional frame:** Distrust, anti-corruption
- **Core claim:** Procurement process may favor specific groups
- **Vulnerability:** Only deescalates with document-level transparency and audit

### Narrative D: “เป้าหมายดี แต่วิธีทำไม่สร้าง ecosystem ไทย”

- **Source agents:** AI entrepreneurs, developers, researchers
- **Emotional frame:** Strategic concern
- **Core claim:** Budget should build Thai AI capacity, not only buy access
- **Vulnerability:** Can be integrated into redesigned project scope

### Narrative E: “ข้อมูลปลอดภัยจริงหรือ”

- **Source agents:** Privacy advocates, developers, educated users
- **Emotional frame:** Risk awareness
- **Core claim:** Thai ID + prompt logs + foreign AI vendors must be governed carefully
- **Vulnerability:** Requires technical architecture, privacy policy, data flow, audit

---

## 6. Recommended MiroFish Agent Seeds

### Agent 01: Government Policy Communicator

```yaml
role: Government Policy Communicator
stance: strongly_supportive
motivation:
  - defend project legitimacy
  - emphasize national AI adoption
  - reframe as Learn to Earn
typical_posts:
  - "โครงการนี้ไม่ใช่แจก AI ฟรี แต่เป็นการลงทุนเพื่ออนาคต"
  - "ต้นทุนเฉลี่ยเพียง 27 บาทต่อเดือนต่อคน"
  - "ทุกขั้นตอนเป็นไปตามกฎหมายและ e-bidding"
risk:
  - sounds defensive if no documents are provided
```

### Agent 02: Opposition Tech-Savvy Politician

```yaml
role: Opposition Tech-Savvy Politician
stance: highly_critical
motivation:
  - expose procurement irregularity
  - question budget allocation
  - demand independent audit
typical_posts:
  - "ทำไมโครงการระดับ 1.6 พันล้านเปิดให้ยื่นข้อเสนอแค่ 34 วัน"
  - "TOR เอื้อรายใดรายหนึ่งหรือไม่"
  - "ประชาชนต้องได้เห็นสัญญาและ KPI"
influence:
  - high media amplification
```

### Agent 03: AI Startup Founder

```yaml
role: AI Startup Founder
stance: skeptical_constructive
motivation:
  - make project useful for Thai AI ecosystem
  - demand API and developer access
  - support Thai LLM
typical_posts:
  - "เป้าหมายดี แต่ควรเปิด API ให้คนไทยสร้างผลิตภัณฑ์ต่อ"
  - "ต้องมี token dashboard และสนับสนุน Thai LLM"
  - "งบ AI ควรสร้าง capability ในประเทศ"
influence:
  - high among developers and tech media
```

### Agent 04: SME Owner

```yaml
role: SME Owner
stance: pragmatic_curious
motivation:
  - reduce marketing/admin cost
  - get free tool if easy to use
concerns:
  - doesn't know how to use AI for business
  - afraid of confusing registration
typical_posts:
  - "ถ้าเอามาช่วยทำโพสต์ขายของ ทำบัญชี หรือสรุปยอดขายได้ก็น่าสนใจ"
  - "แต่ต้องมีตัวอย่างใช้งานจริง ไม่ใช่สมัครแล้วงง"
```

### Agent 05: Student / Early Adopter

```yaml
role: Student Early Adopter
stance: excited_but_low_trust
motivation:
  - free pro AI access
  - study, portfolio, coding, content creation
concerns:
  - eligibility
  - model limits
  - Thai ID privacy
typical_posts:
  - "ถ้าได้ ChatGPT/Gemini/Claude Pro ฟรีก็น่าสน"
  - "ลงทะเบียนเมื่อไหร่ ใช้โมเดลไหนได้จริง"
```

### Agent 06: General Taxpayer

```yaml
role: General Taxpayer
stance: suspicious
motivation:
  - wants public money used well
typical_posts:
  - "เงินภาษี 1.6 พันล้าน ใช้แล้วได้อะไร"
  - "คนใช้จริงกี่คน หรือสมัครทิ้ง"
  - "ควรเอาเงินไปทำเรื่องจำเป็นกว่านี้ไหม"
```

### Agent 07: Privacy Advocate

```yaml
role: Privacy Advocate
stance: concerned
motivation:
  - ensure user data and prompt logs are protected
typical_posts:
  - "Thai ID กับ prompt history แยกกันอย่างไร"
  - "Anonymous แปลว่าอะไรในเชิงเทคนิค"
  - "ต้องเปิด Data Flow Diagram และ DPA"
```

### Agent 08: Investigative Journalist

```yaml
role: Investigative Journalist
stance: skeptical
motivation:
  - follow documents and inconsistencies
typical_posts:
  - "เปิดไทม์ไลน์จัดซื้อจัดจ้าง TH-AI Passport"
  - "ส่องราคากลาง ผู้ชนะประมูล และเงื่อนไข TOR"
  - "รัฐบอกโปร่งใส แต่เอกสารเปิดพอหรือไม่"
```

---

## 7. Early Warning Indicators

| Indicator | Meaning | Simulation effect |
|---|---|---|
| รัฐเปิด dashboard เฉพาะยอดลงทะเบียน แต่ไม่มี active usage | Vanity metric risk | Trust decreases after launch |
| มีคำว่า “ฟอกขาว” / “ล็อกสเปก” / “เงินทอน” เพิ่มขึ้นใน social | Corruption frame intensifies | Negative narrative accelerates |
| ผู้เชี่ยวชาญ AI ออกบทความยาววิจารณ์ technical design | Expert opposition strengthens | Tech community shifts negative |
| รัฐเปิด technical architecture และ contract summary | Trust recovery begins | Critical agents soften |
| มี success story SME/teacher/student ที่ตรวจสอบได้ | Outcome narrative emerges | General public sentiment improves |
| ระบบลงทะเบียนล่มหรือ token limit ไม่ชัด | Launch failure | Media backlash spike |
| มี third-party audit หรือ public data room | Procurement issue deescalates | Political attack loses some force |
| ไม่มี follow-up หลัง Forum | Listening event perceived as PR | Forum benefit decays rapidly |

---

## 8. Recommended Simulation Scenarios

### Scenario 1: Best Case — “National AI Literacy Program”

**Trigger path:**

1. MDES publishes contract summary, KPI dashboard plan, privacy architecture, and procurement Q&A
2. Project redesigned into cohorts: students, teachers, SMEs, freelancers, government staff
3. AIEAT-like recommendations partly adopted: token dashboard, Thai LLM, API sandbox
4. Early use cases generate real stories: SME saves time, teacher creates lesson plan, student builds portfolio
5. Media shifts from procurement scandal to implementation watch

**Expected public sentiment:** cautiously positive  
**Trust score movement:** 45 → 62  
**Main risk remains:** procurement skepticism among opposition

---

### Scenario 2: Base Case — “High Registration, Medium Trust, Uneven Usage”

**Trigger path:**

1. Government continues project with some additional explanations
2. Registration opens and gets strong interest due to free AI access
3. Usage concentrates among students, freelancers, tech workers, and urban knowledge workers
4. General public finds onboarding confusing
5. Critics keep asking for active usage and procurement transparency

**Expected public sentiment:** mixed  
**Trust score movement:** 45 → 48  
**Main risk remains:** retention and cost-per-active-user

---

### Scenario 3: Worst Case — “Procurement Scandal Frame Dominates”

**Trigger path:**

1. No meaningful disclosure beyond repeated statements of transparency
2. New documents or political claims revive TOR / bidder issues
3. Forum perceived as PR or whitewashing
4. Registration or platform launch has UX/performance problems
5. Active usage is low or no dashboard is published

**Expected public sentiment:** negative  
**Trust score movement:** 45 → 28  
**Main risk remains:** project becomes remembered as “1.6B AI subscription controversy”

---

## 9. Suggested Quantitative Parameters for MiroFish

```yaml
initial_conditions:
  public_attention: 0.82
  public_trust: 0.45
  polarization: 0.72
  procurement_suspicion: 0.88
  ai_opportunity_interest: 0.68
  privacy_concern: 0.55
  expert_alignment: 0.35
  government_message_reach: 0.70
  media_amplification: 0.75

narrative_weights:
  budget_skepticism: 0.25
  procurement_transparency: 0.30
  ai_literacy_opportunity: 0.16
  adoption_retention: 0.14
  local_ai_ecosystem: 0.09
  privacy_data_governance: 0.06

agent_influence_weights:
  opposition_politicians: 0.18
  investigative_media: 0.17
  ai_experts: 0.16
  government_officials: 0.15
  general_public: 0.12
  tech_influencers: 0.10
  sme_and_students: 0.07
  vendors: 0.05
```

---

## 10. Source Index

1. MDES official clarification, 2026-05-28  
   Title: รมว.ดีอี แจง TH-AI Passport โปร่งใสทุกขั้นตอน...  
   URL: https://www.mdes.go.th/news/detail/11066-%E0%B8%A3%E0%B8%A1%E0%B8%A7-%E0%B8%94%E0%B8%B5%E0%B8%AD%E0%B8%B5-%E0%B9%81%E0%B8%88%E0%B8%87-TH-AI-Passport-%E0%B9%82%E0%B8%9B%E0%B8%A3%E0%B9%88%E0%B8%87%E0%B9%83%E0%B8%AA%E0%B8%97%E0%B8%B8%E0%B8%81%E0%B8%82%E0%B8%B1%E0%B9%89%E0%B8%99%E0%B8%95%E0%B8%AD%E0%B8%99-%E0%B8%A2%E0%B9%89%E0%B8%B3%E0%B9%83%E0%B8%8A%E0%B9%89%E0%B8%87%E0%B8%9A%E0%B8%84%E0%B8%B8%E0%B9%89%E0%B8%A1%E0%B8%84%E0%B9%88%B2-%E0%B8%A5%E0%B8%87%E0%B8%97%E0%B8%B8%E0%B8%99%E0%B9%80%E0%B8%9E%E0%B8%B7%E0%B9%88%E0%B8%AD%E0%B8%AD%E0%B8%99%E0%B8%B2%E0%B8%84%E0%B8%95-1-6-%E0%B8%9E%E0%B8%B1%E0%B8%99%E0%B8%A5%E0%B9%89%E0%B8%B2%E0%B8%99-%E0%B8%A2%E0%B8%81%E0%B8%A3%E0%B8%B0%E0%B8%94%E0%B8%B1%E0%B8%9A%E0%B8%84%E0%B8%99%E0%B9%84%E0%B8%97%E0%B8%A2-5-%E0%B8%A5%E0%B9%89%E0%B8%B2%E0%B8%99%E0%B8%84%E0%B8%99-%E0%B9%80%E0%B8%82%E0%B9%89%E0%B8%B2%E0%B8%96%E0%B8%B6%E0%B8%87-AI-%E0%B8%81%E0%B9%88%E0%B8%AD%E0%B8%99%E0%B8%95%E0%B8%81%E0%B8%82%E0%B8%9A%E0%B8%A7%E0%B8%99%E0%B9%82%E0%B8%A5%E0%B8%81

2. Thai PBS explainer, 2026-06-10  
   Title: TH-AI Passport คืออะไร กางไทม์ไลน์จัดซื้อจัดจ้างวงเงินกว่า 1.6 พันล้าน  
   URL: https://www.thaipbs.or.th/news/content/506890

3. Thai PBS expert roundup, 2026-06-10  
   Title: หลากคำถาม TH-AI Passport จากผู้เชี่ยวชาญ AI คุ้ม-ไม่คุ้ม คนไทยได้อะไร  
   URL: https://www.thaipbs.or.th/news/content/506898

4. Thansettakij scrutiny report, 2026-05-08  
   Title: ตั้งคำถามงบ 1.62 พันล้าน “TH-AI Passport” หลังเปิดโครงการแจก AI ฟรี 5 ล้านสิทธิ์  
   URL: https://www.thansettakij.com/economy/658588

5. Thairath forum report, 2026-06-11  
   Title: ดีอีเปิดเวทีรับฟัง-แลกเปลี่ยน TH-AI Passport “ไชยชนก” ยันทุกอย่างเป็นไปตามขั้นตอน  
   URL: https://www.thairath.co.th/news/politic/2938835

6. MGR Online forum/procurement clarification, 2026-06-11  
   Title: ปลัดดีอีแจงปม TH-AI Passport ย้ำโปร่งใสทุกขั้นตอน...  
   URL: https://mgronline.com/infographic/detail/9690000055460

7. Dailynews / AIEAT recommendations, 2026-06-03  
   Title: “AIEAT” แนะ 8 ข้อเสนอทางออกทำ “TH-AI Passport” ให้เกิดประโยชน์สูงสุด  
   URL: https://www.dailynews.co.th/news/5915819/

8. InfoQuest overview, 2026-05-29  
   Title: ZoomIn: รู้จัก TH-AI Passport แจกสิทธิใช้ Pro ฟรี 5 ล้านคน ใครได้บ้าง?  
   URL: https://www.infoquest.co.th/2026/597192

---

## 11. Notes for Simulation Prompt

Use this file as qualitative signal input, not as final truth. The model should treat each signal as public perception or media-framed concern. Some allegations are disputed by government. Simulation must distinguish between:

- factual project claims
- government explanations
- public concerns
- political allegations
- expert recommendations
- unresolved questions

Recommended simulation instruction:

```text
When simulating public opinion, do not assume allegations are true. Model them as claims, suspicions, or narratives that affect trust. Separate verified facts from contested interpretations. Track how transparency actions, document disclosure, platform launch quality, and measurable usage outcomes change stakeholder trust over time.
```
