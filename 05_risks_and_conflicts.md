# 05_risks_and_conflicts.md

> Seed material สำหรับใช้กับ MiroFish simulation  
> Project: AI Pass TH / TH-AI Passport  
> Generated: 2026-06-11  
> Coverage window: 2025-11-17 ถึง 2026-06-11  
> Related file: `04_public_opinion_signals.md`  
> Method: risk and conflict extraction from public news, government statements, expert commentary, visible political/media framing, and public-opinion signals.  
> Limitation: เอกสารนี้เป็น risk model สำหรับ simulation ไม่ใช่ข้อสรุปทางกฎหมายหรือการตรวจสอบข้อเท็จจริงขั้นสุดท้าย ประเด็นที่เป็นข้อสงสัย/ข้อกล่าวหาให้ถือเป็น **perceived risk / narrative risk** จนกว่าจะมีหลักฐานตรวจสอบอย่างเป็นทางการ

---

## 1. Executive Risk Posture

โครงการ TH-AI Passport อยู่ในสถานะ **high-policy-potential / high-trust-risk / high-execution-risk**

โครงการมีเป้าหมายเชิงนโยบายที่สังคมจำนวนมากยอมรับได้ คือการเพิ่ม AI literacy ลดความเหลื่อมล้ำในการเข้าถึง AI และยกระดับแรงงานไทย แต่ความเสี่ยงหลักไม่ได้อยู่ที่ “AI มีประโยชน์หรือไม่” แต่อยู่ที่คำถามว่า **รัฐออกแบบ ใช้งบ จัดซื้อ วัดผล และบริหารความเชื่อมั่นได้ดีพอหรือไม่**

แกนความเสี่ยงสูงสุดมี 5 ด้าน:

1. **Procurement Trust Risk** — ความเชื่อมั่นต่อ TOR, e-bidding, ราคากลาง, ผู้ชนะประมูล และความโปร่งใสของสัญญา
2. **Outcome Risk** — ความเสี่ยงที่โครงการวัดผลได้แค่จำนวนสิทธิ์/ผู้ลงทะเบียน แต่ไม่เกิด actual AI adoption หรือ productivity uplift
3. **Product Expectation Risk** — ความเข้าใจคลาดเคลื่อนระหว่าง “AI Pro app experience” กับ “model/API/platform access”
4. **Data Governance Risk** — ความเสี่ยงด้านข้อมูลส่วนบุคคล prompt data, anonymization, data localization, consent, และการนำข้อมูลไปต่อยอด ThaiLLM
5. **Ecosystem Conflict Risk** — ความขัดแย้งระหว่างการซื้อบริการจากผู้ให้บริการรายใหญ่/ต่างชาติ กับการสนับสนุน local AI ecosystem ของไทย

---

## 2. Risk Scoring Method

ใช้สำหรับกำหนดค่า simulation ใน MiroFish

```yaml
risk_score_method:
  likelihood:
    1: unlikely
    2: possible
    3: likely
    4: very_likely
    5: almost_certain
  impact:
    1: low_noise
    2: operational_irritation
    3: public_criticism
    4: policy_damage
    5: project_legitimacy_crisis
  velocity:
    slow: develops_over_weeks_or_months
    medium: develops_over_days
    fast: develops_within_24_to_72_hours
  detectability:
    low: weak_signal_hard_to_detect
    medium: visible_in_media_or_expert_comments
    high: visible_in_mainstream_news_or_parliament
  risk_score_formula: likelihood * impact
```

---

## 3. Master Risk Register

### R01 — Procurement Trust Collapse

**Category:** Governance / procurement  
**Likelihood:** 4  
**Impact:** 5  
**Velocity:** fast  
**Risk score:** 20  
**Current posture:** Critical

**Description:**  
ความเสี่ยงที่กระแสสาธารณะตีความโครงการผ่านกรอบ “ล็อกสเปก / ฮั้วประมูล / เอื้อเอกชน / ไม่โปร่งใส” แม้ภาครัฐยืนยันว่าดำเนินการตามกฎหมายและผ่าน e-bidding แล้วก็ตาม

**Conflict core:**  
รัฐมองว่าใช้กระบวนการจัดซื้อจัดจ้างตามกฎหมายแล้ว แต่สื่อ ฝ่ายค้าน และกลุ่มผู้เชี่ยวชาญบางส่วนต้องการเห็นข้อมูลเชิงลึกมากกว่า statement เช่น TOR ฉบับเต็ม เกณฑ์ประเมิน สัญญา ราคากลาง รายละเอียดผู้เสนอราคา และเหตุผลเชิงเทคนิคในการเลือกผู้ชนะ

**Early warning indicators:**

- ข่าวหรือโพสต์ใหม่ที่ใช้คำว่า “ล็อกสเปก”, “ฮั้ว”, “ผู้ชนะประมูล”, “ราคากลาง”, “TOR”
- เอกสารจัดซื้อจัดจ้างถูกแชร์เป็น screenshot พร้อมการตีความเชิงลบ
- ฝ่ายค้านนำประเด็นเข้าสภาหรือแถลงข่าวซ้ำ
- ผู้เชี่ยวชาญสาย procurement / civic tech เข้ามาขยายประเด็น

**Escalation triggers:**

```yaml
triggers:
  - new_procurement_document_leak
  - bidder_relationship_story
  - unclear_tor_requirement
  - parliamentary_question_session
  - no_public_contract_disclosure
```

**Mitigation triggers:**

```yaml
mitigation:
  - publish_full_tor_and_contract
  - publish_scoring_criteria
  - independent_procurement_audit
  - public_q_and_a_with_documents
  - machine_readable_procurement_timeline
```

**MiroFish agent sensitivity:**

```yaml
agent_sensitivity:
  opposition_politician: 0.95
  investigative_journalist: 0.90
  civic_tech_group: 0.85
  ai_practitioner: 0.65
  general_public: 0.55
  government_spokesperson: -0.80
```

---

### R02 — Value-for-Money Backlash

**Category:** Budget / public finance  
**Likelihood:** 5  
**Impact:** 4  
**Velocity:** fast  
**Risk score:** 20  
**Current posture:** Critical

**Description:**  
งบประมาณระดับ 1.6 พันล้านบาททำให้โครงการถูก frame เป็น “เงินก้อนใหญ่” ก่อนที่ประชาชนจะรับรู้รายละเอียดต้นทุนต่อหัวหรือประโยชน์ระยะยาว ความเสี่ยงคือสังคมตัดสินโครงการจาก headline budget มากกว่า economic outcome

**Conflict core:**  
รัฐสื่อสารว่าต้นทุนเฉลี่ยต่อคนต่อปีต่ำและคุ้มค่าเมื่อเทียบกับราคา AI Pro ในตลาด ขณะที่ฝ่ายวิจารณ์ถามว่าความคุ้มค่าต้องวัดจาก active usage, productivity, income uplift, cost saving, skill completion และผลลัพธ์ทางเศรษฐกิจ ไม่ใช่จำนวนสิทธิ์ที่แจก

**Early warning indicators:**

- คำถาม “ใช้เงินจริงเท่าไรต่อ active user?”
- มีการคำนวณ cost per login, cost per active month, cost per trained user ในโซเชียล
- สื่อเปรียบเทียบงบนี้กับทางเลือกอื่น เช่น สนับสนุน startup ไทย, ซื้อ GPU, สร้าง Thai AI infrastructure

**Simulation variable:**

```yaml
value_for_money_backlash:
  baseline_intensity: 0.85
  rises_when:
    - reported_metric_is_registration_only
    - no_active_usage_dashboard
    - training_completion_low
    - contract_cost_fixed_despite_low_usage
  falls_when:
    - cost_per_active_user_disclosed
    - outcome_kpi_disclosed
    - pay_as_used_terms_confirmed
    - independent_cost_benchmark_released
```

---

### R03 — Registration Success but Adoption Failure

**Category:** Product adoption / behavior  
**Likelihood:** 4  
**Impact:** 5  
**Velocity:** medium  
**Risk score:** 20  
**Current posture:** Critical

**Description:**  
โครงการอาจมีผู้ลงทะเบียนสูงในช่วงแรกเพราะเป็นสิทธิ์ฟรี แต่ active usage และ retention อาจลดลงอย่างรวดเร็ว หากผู้ใช้ไม่มี onboarding, learning path, use case ตามอาชีพ, template, workflow หรือ coaching

**Conflict core:**  
รัฐต้องการเพิ่มจำนวนผู้ใช้ AI ระดับประเทศ ส่วนฝ่ายวิจารณ์ถามว่า “เข้าถึง” ไม่เท่ากับ “ใช้จริง” และ “ใช้จริง” ไม่เท่ากับ “สร้างผลลัพธ์ทางเศรษฐกิจ”

**Early warning indicators:**

- ข่าวรายงานยอดสมัครสูง แต่ไม่มี MAU/WAU/DAU
- ผู้ใช้แชร์ว่าได้สิทธิ์แต่ไม่รู้จะใช้ทำอะไร
- กลุ่ม non-tech users เลิกใช้หลังทดลองไม่กี่ครั้ง
- สื่อถามหาตัวเลข retention หลัง 30/90/180 วัน

**Simulation variable:**

```yaml
adoption_failure_risk:
  registration_spike_probability: 0.80
  day_30_retention_risk: 0.65
  day_90_retention_risk: 0.75
  high_adoption_segments:
    - students
    - teachers
    - office_workers
    - freelancers
    - creators
    - smes_with_marketing_needs
  low_adoption_segments:
    - low_digital_literacy_public
    - users_without_clear_workflow
    - users_with_language_barrier
```

---

### R04 — AI Pro Expectation Mismatch

**Category:** Product clarity / communication  
**Likelihood:** 4  
**Impact:** 4  
**Velocity:** fast  
**Risk score:** 16  
**Current posture:** High

**Description:**  
ประชาชนอาจเข้าใจว่าโครงการให้ประสบการณ์เหมือนซื้อ ChatGPT Plus, Gemini Advanced, Claude Pro หรือ AI app ระดับ premium เต็มรูปแบบ แต่สิ่งที่ได้รับจริงอาจเป็น model access, API-layer service, token-based platform, หรือ curated interface ที่ไม่ได้มีฟีเจอร์ระดับ app ทั้งหมด

**Conflict core:**  
ถ้าภาษาโครงการใช้คำว่า “AI Pro / Premium” แต่ user experience ไม่ตรงกับสิ่งที่ตลาดเข้าใจ จะเกิด backlash ว่า “ไม่ใช่ Pro จริง” หรือ “โฆษณาเกินจริง”

**Early warning indicators:**

- ผู้เชี่ยวชาญอธิบายความต่างระหว่าง AI model, API, platform และ app
- ผู้ใช้ถามว่าได้ Deep Research, Canvas, Custom GPTs, file workspace, agent features หรือไม่
- มี viral post เปรียบเทียบ feature list ระหว่างสิทธิ์โครงการกับ subscription โดยตรง

**Simulation variable:**

```yaml
expectation_mismatch:
  baseline_intensity: 0.70
  rises_when:
    - official_message_uses_ai_pro_without_feature_matrix
    - user_experience_lacks_expected_app_features
    - influencers_post_feature_gap
  falls_when:
    - publish_feature_matrix_by_model
    - explain_api_vs_app_clearly
    - provide_use_case_templates_that_work
```

---

### R05 — Data Privacy and Prompt Governance Concern

**Category:** Privacy / PDPA / security  
**Likelihood:** 4  
**Impact:** 5  
**Velocity:** medium  
**Risk score:** 20  
**Current posture:** Critical

**Description:**  
โครงการเกี่ยวข้องกับ ID verification, user data, prompt data, cloud storage, anonymization, model providers, และอาจมีการนำข้อมูลที่ปกปิดตัวตนไปต่อยอด ThaiLLM ความเสี่ยงคือประชาชนและผู้เชี่ยวชาญไม่มั่นใจว่า data flow, consent, retention, deletion, access control และ audit ถูกออกแบบรัดกุมเพียงพอ

**Conflict core:**  
รัฐยืนยันว่าข้อมูลผู้ใช้และ prompt จะไม่ถูกนำไป train โดยผู้ให้บริการ AI และจะจัดเก็บในประเทศไทยในรูปแบบ anonymous แต่ผู้เชี่ยวชาญต้องการรายละเอียดเชิงเทคนิคและกฎหมาย เช่น data processing agreement, anonymization method, retention period, audit log, subprocessors, และสิทธิ์ผู้ใช้ในการลบข้อมูล

**Early warning indicators:**

- คำถามเรื่อง “prompt คนไทยถูกเก็บไหม”
- ประเด็น “verify ID แล้วข้อมูลไปไหน”
- ผู้ใช้กังวลเรื่องข้อมูลบริษัท/งาน/เอกสารราชการที่อัปโหลดเข้า AI
- นักกฎหมายหรือผู้เชี่ยวชาญ PDPA เข้ามาวิจารณ์

**Simulation variable:**

```yaml
privacy_concern:
  baseline_intensity: 0.75
  sensitive_topics:
    - id_verification
    - prompt_storage
    - anonymous_data
    - thai_llm_reuse
    - cloud_location
    - foreign_model_provider
  mitigation:
    - publish_data_flow_diagram
    - publish_pdpa_assessment
    - publish_retention_policy
    - opt_out_for_data_reuse
    - independent_security_audit
```

---

### R06 — Data Localization vs Frontier Model Capability Conflict

**Category:** Technical architecture / service quality  
**Likelihood:** 3  
**Impact:** 4  
**Velocity:** medium  
**Risk score:** 12  
**Current posture:** High

**Description:**  
หากโครงการกำหนดให้ข้อมูลอยู่ภายในประเทศ แต่ต้องการให้ประชาชนเข้าถึง frontier models หรือ app-level features ที่โดยธรรมชาติประมวลผลบน infrastructure ต่างประเทศ อาจเกิดความขัดแย้งระหว่าง policy promise, technical reality, และ user experience

**Conflict core:**  
ประชาชนคาดหวัง “ความสามารถระดับโลก” ขณะที่การควบคุมข้อมูลในประเทศอาจทำให้ต้องใช้ proxy, API, hosted model, regional infrastructure หรือ hybrid model ซึ่งอาจจำกัดฟีเจอร์ ความเร็ว คุณภาพ และความชัดเจนเรื่องข้อมูล

**Early warning indicators:**

- ผู้เชี่ยวชาญถามว่า data localization ทำงานกับ ChatGPT / Gemini / Claude อย่างไร
- ระบบมี latency สูงหรือฟีเจอร์ไม่ครบ
- เอกสาร technical architecture ไม่ชัดเจน

**Simulation variable:**

```yaml
data_localization_conflict:
  baseline_intensity: 0.55
  rises_when:
    - no_architecture_disclosure
    - quality_gap_vs_commercial_apps
    - privacy_promise_too_broad
  falls_when:
    - technical_architecture_published
    - model_by_model_data_policy_disclosed
    - local_gateway_audited
```

---

### R07 — Foreign Vendor Capture / Platform Lock-in Narrative

**Category:** Industrial policy / digital sovereignty  
**Likelihood:** 4  
**Impact:** 4  
**Velocity:** medium  
**Risk score:** 16  
**Current posture:** High

**Description:**  
โครงการอาจถูกตีความว่าใช้งบภาครัฐสร้างฐานลูกค้าให้ Big Tech หรือผู้ให้บริการต่างชาติ มากกว่าสร้างความสามารถ AI ของประเทศเอง

**Conflict core:**  
รัฐมองว่าการใช้บริการผู้ให้บริการระดับโลกช่วยให้คนไทยเข้าถึงเทคโนโลยีเร็วที่สุด ส่วนผู้เชี่ยวชาญและ startup ไทยบางส่วนมองว่างบขนาดนี้ควรสร้างโครงสร้างพื้นฐาน ทักษะงาน และธุรกิจ AI ภายในประเทศควบคู่กัน

**Early warning indicators:**

- คำว่า “สร้างฐานลูกค้าให้ Big Tech” ถูกแชร์ซ้ำ
- ผู้ประกอบการไทยออกมาเรียกร้อง local AI allocation
- มีการเปรียบเทียบว่า 1.6 พันล้านสามารถซื้อ GPU/สร้างงาน AI ไทยได้มากเพียงใด

**Simulation variable:**

```yaml
vendor_capture_narrative:
  baseline_intensity: 0.68
  rises_when:
    - foreign_platform_brand_dominates_campaign
    - no_local_vendor_quota
    - no_open_api_for_thai_developers
  falls_when:
    - thai_ai_vendor_program
    - thai_llm_budget_line
    - local_startup_participation
    - open_innovation_grants
```

---

### R08 — Local AI Ecosystem Alienation

**Category:** Ecosystem / innovation policy  
**Likelihood:** 4  
**Impact:** 3  
**Velocity:** medium  
**Risk score:** 12  
**Current posture:** High

**Description:**  
ผู้ประกอบการ AI ไทยอาจรู้สึกว่าโครงการไม่ได้กระจายโอกาสให้ ecosystem ภายในประเทศเพียงพอ ส่งผลให้กลุ่มที่ควรเป็น ally กลายเป็น critic

**Conflict core:**  
รัฐต้องการ scale เร็ว ส่วน startup ไทยต้องการให้เงินรัฐช่วยสร้าง capability ระยะยาว เช่น infrastructure, dataset, Thai LLM, API credits, sandbox, procurement access และ real user distribution

**Early warning indicators:**

- startup ไทยรวมตัวออกแถลงการณ์
- นักพัฒนาเรียกร้อง API access หรือ local model benchmark
- สื่อเทคเริ่ม frame ว่าโครงการไม่สร้างอุตสาหกรรม AI ไทย

**Simulation variable:**

```yaml
local_ecosystem_alienation:
  baseline_intensity: 0.60
  allies_can_be_created_by:
    - local_ai_challenge
    - startup_api_marketplace
    - thai_llm_integration
    - procurement_subcontract_transparency
    - credits_for_thai_tools
```

---

### R09 — Training / Bootcamp Becomes Symbolic Rather than Transformative

**Category:** Learning design / program delivery  
**Likelihood:** 4  
**Impact:** 4  
**Velocity:** slow  
**Risk score:** 16  
**Current posture:** High

**Description:**  
แม้โครงการมี training, test, bootcamp, contest และกิจกรรมส่งเสริมการเรียนรู้ แต่ความเสี่ยงคือกิจกรรมเหล่านี้กลายเป็น output เชิงกิจกรรม ไม่ใช่ transformation เชิงทักษะหรืออาชีพ

**Conflict core:**  
รัฐอาจรายงานจำนวนคนเข้าอบรมหรือจำนวนกิจกรรม ขณะที่สังคมต้องการเห็นว่าผู้เรียนนำ AI ไปใช้ทำงานจริง สร้างรายได้ ลดเวลา ลดต้นทุน หรือสร้างผลงานได้อย่างไร

**Early warning indicators:**

- รายงานเฉพาะจำนวน bootcamp / จำนวนผู้เข้าร่วม
- ไม่มี pre/post skill assessment ที่น่าเชื่อถือ
- ไม่มี occupational workflow เช่น ครู, SME, นักศึกษา, เกษตรกร, ฟรีแลนซ์
- ผู้เรียนจบอบรมแต่ใช้ AI ต่อไม่ได้

**Simulation variable:**

```yaml
training_symbolism_risk:
  baseline_intensity: 0.65
  falls_when:
    - role_based_curriculum
    - pre_post_assessment
    - portfolio_output
    - mentor_follow_up
    - public_case_studies
```

---

### R10 — Digital Divide Reproduction

**Category:** Equity / inclusion  
**Likelihood:** 4  
**Impact:** 3  
**Velocity:** slow  
**Risk score:** 12  
**Current posture:** Medium-High

**Description:**  
โครงการตั้งเป้าลดความเหลื่อมล้ำ แต่ผู้ที่ได้ประโยชน์สูงสุดอาจเป็นกลุ่มที่มี digital literacy อยู่แล้ว เช่น นักศึกษาเมืองใหญ่ knowledge workers, creators, freelancers และ developers ขณะที่กลุ่มเป้าหมายที่เปราะบางอาจใช้จริงได้น้อย

**Conflict core:**  
การแจกสิทธิ์ไม่เพียงพอ หากไม่มี assistive onboarding, local language workflow, community helper, public access points, device/internet support และ content ตามบริบทชีวิตจริง

**Early warning indicators:**

- ผู้ใช้ต่างจังหวัด/ผู้สูงอายุ/แรงงานนอกระบบรายงานว่าใช้ยาก
- สัดส่วน active users กระจุกในเมืองใหญ่หรือกลุ่มการศึกษาสูง
- ผู้ที่มีบัญชี AI อยู่แล้วได้ประโยชน์ซ้ำซ้อน

**Simulation variable:**

```yaml
digital_divide_reproduction:
  baseline_intensity: 0.55
  rises_when:
    - no_segmented_onboarding
    - urban_user_dominance
    - english_or_tech_heavy_interface
  falls_when:
    - community_center_support
    - thai_language_templates
    - occupation_based_guides
    - assisted_signup_and_training
```

---

### R11 — Political Escalation and Scandal Framing

**Category:** Politics / media  
**Likelihood:** 5  
**Impact:** 4  
**Velocity:** fast  
**Risk score:** 20  
**Current posture:** Critical

**Description:**  
โครงการมีองค์ประกอบที่เหมาะกับ political escalation: งบสูง, เทคโนโลยีซับซ้อน, ความคาดหวังประชาชนสูง, กระบวนการจัดซื้อ, และผู้รับจ้างเอกชน เมื่อประเด็นเข้าสู่สนามการเมือง โครงการอาจถูกตีความผ่านกรอบ scandal มากกว่า policy design

**Conflict core:**  
ฝ่ายการเมืองจะใช้จุดอ่อนเรื่องความโปร่งใสและความคุ้มค่าเพื่อโจมตีความชอบธรรมของโครงการ ขณะที่รัฐจะตอบด้วยกรอบกฎหมาย กระบวนการราชการ และประโยชน์เชิงนโยบาย

**Early warning indicators:**

- กระทู้สด/อภิปรายในสภา
- แฮชแท็กเชิงโจมตี
- สื่อทำ timeline “ความเอ๊ะ” หรือ “ข้อสงสัยรอบด้าน”
- คำอธิบายรัฐถูกตีความว่าเป็นการ “ฟอกขาว” หรือ “แก้ตัว”

**Simulation variable:**

```yaml
political_escalation:
  baseline_probability: 0.85
  escalation_velocity: fast
  peak_conditions:
    - procurement_document_ambiguity
    - weak_public_forum_response
    - contract_rigidity_message
    - viral_expert_critique
```

---

### R12 — Public Forum Backfire

**Category:** Stakeholder engagement / communication  
**Likelihood:** 3  
**Impact:** 4  
**Velocity:** fast  
**Risk score:** 12  
**Current posture:** High

**Description:**  
การเปิดเวทีรับฟังความคิดเห็นสามารถลดแรงต้านได้ แต่ก็มีความเสี่ยงกลายเป็น backfire หากผู้เข้าร่วมรู้สึกว่าเวทีเป็นพิธีกรรมหลังจากโครงการเดินหน้าไปแล้ว หรือข้อเสนอไม่สามารถเปลี่ยนแปลงสาระสำคัญได้

**Conflict core:**  
รัฐต้องการแสดงความเปิดกว้าง ขณะที่ผู้วิจารณ์ต้องการเห็นผลของการรับฟังต่อสัญญา TOR การวัดผล การเปิดข้อมูล และ governance จริง

**Early warning indicators:**

- ผู้เข้าร่วม forum ระบุว่าไม่ได้รับคำตอบเรื่องสำคัญ
- สื่อพาดหัวว่า “ฟังแต่ไม่แก้”
- รัฐย้ำว่า “เซ็นสัญญาแล้วแก้ไม่ได้” โดยไม่มีทางออกเชิง governance
- ข้อเสนอภาคประชาชนไม่ถูก publish เป็น action list

**Simulation variable:**

```yaml
public_forum_backfire:
  baseline_probability: 0.50
  mitigation:
    - publish_forum_minutes
    - publish_action_items
    - publish_accepted_rejected_proposals
    - assign_owner_and_deadline
    - open_follow_up_forum
```

---

### R13 — Centralized Identity + AI Usage Database Concern

**Category:** Security / identity / civil trust  
**Likelihood:** 3  
**Impact:** 5  
**Velocity:** medium  
**Risk score:** 15  
**Current posture:** High

**Description:**  
การ verify ID เพื่อยืนยันสิทธิ์ของคนไทยอาจถูกสาธารณะตั้งคำถามว่าเชื่อมโยงกับประวัติการใช้ AI, prompt, เอกสาร, หรือข้อมูลอ่อนไหวหรือไม่ แม้รัฐยืนยันว่าไม่มีการเปิดเผยข้อมูลส่วนบุคคลแก่เจ้าของโมเดล

**Conflict core:**  
ระบบต้องพิสูจน์ว่า identity layer แยกจาก usage/prompt layer อย่างเข้มงวด และไม่มีการสร้าง profiling รายบุคคลโดยไม่จำเป็น

**Early warning indicators:**

- โพสต์ถามว่า “รัฐจะรู้ไหมว่าเราถาม AI เรื่องอะไร”
- นักกฎหมาย PDPA ถามหา DPIA / data protection impact assessment
- องค์กรเอกชนห้ามพนักงานใช้สิทธิ์โครงการกับข้อมูลงาน

**Simulation variable:**

```yaml
identity_usage_database_concern:
  baseline_intensity: 0.58
  rises_when:
    - no_data_separation_diagram
    - unclear_identity_provider
    - unclear_retention_policy
  falls_when:
    - privacy_by_design_disclosure
    - independent_pdpa_review
    - user_data_deletion_control
```

---

### R14 — ThaiLLM Data Reuse Consent Conflict

**Category:** Data reuse / national AI  
**Likelihood:** 3  
**Impact:** 4  
**Velocity:** medium  
**Risk score:** 12  
**Current posture:** High

**Description:**  
หากข้อมูลการใช้งาน AI ที่ปกปิดตัวตนแล้วถูกนำไปต่อยอด ThaiLLM หรือ National AI จะเกิดคำถามเรื่อง consent, anonymization quality, re-identification risk, data ownership และสิทธิ์ของผู้ใช้

**Conflict core:**  
การสร้าง ThaiLLM เป็นเป้าหมายเชิงยุทธศาสตร์ที่มีคุณค่า แต่ต้องแยกชัดระหว่าง “ข้อมูลสถิติการใช้งาน”, “prompt data”, “feedback data”, “output data” และ “personal/work data”

**Early warning indicators:**

- นักวิชาการถามว่า anonymized data เพียงพอหรือไม่
- ผู้ใช้ถามว่าจะ opt out ได้ไหม
- สื่อถามว่า prompt ของประชาชนกลายเป็น dataset ของรัฐหรือไม่

**Simulation variable:**

```yaml
thai_llm_reuse_conflict:
  baseline_intensity: 0.52
  mitigation:
    - opt_in_data_reuse
    - dataset_governance_board
    - published_data_taxonomy
    - no_prompt_reuse_without_consent
    - privacy_preserving_aggregation
```

---

### R15 — Multi-Model Operational Complexity

**Category:** Operations / technical delivery  
**Likelihood:** 4  
**Impact:** 3  
**Velocity:** medium  
**Risk score:** 12  
**Current posture:** Medium-High

**Description:**  
โครงการที่ระบุผู้ให้บริการหลายราย หลายโมเดล และผู้ใช้จำนวนมาก มีความซับซ้อนด้าน routing, token allocation, capacity, availability, latency, model selection, abuse prevention, billing reconciliation และ support

**Conflict core:**  
ผู้ใช้คาดหวังว่า “ใช้ AI ได้ง่ายเหมือนแอปทั่วไป” แต่ระบบหลังบ้านที่รวมหลายโมเดลและหลายผู้ให้บริการอาจทำให้ UX ซับซ้อนหรือไม่เสถียร

**Early warning indicators:**

- ระบบล่มช่วงเปิดใช้งาน
- สิทธิ์ใช้ได้บางโมเดล บางเวลาหรือ latency สูง
- ผู้ใช้ไม่เข้าใจ token/capacity allocation
- support backlog สูง

**Simulation variable:**

```yaml
multi_model_operational_complexity:
  baseline_risk: 0.60
  rises_when:
    - launch_big_bang_5m_users
    - no_staged_rollout
    - unclear_model_routing
    - weak_support_system
  falls_when:
    - phased_rollout
    - transparent_service_status
    - simple_user_interface
    - clear_quota_policy
```

---

### R16 — Abuse, Misuse, and Academic Integrity Risk

**Category:** Responsible AI / education / misuse  
**Likelihood:** 4  
**Impact:** 3  
**Velocity:** medium  
**Risk score:** 12  
**Current posture:** Medium-High

**Description:**  
การให้คนจำนวนมากเข้าถึง AI ระดับสูงอาจเพิ่มความเสี่ยงด้าน misinformation, plagiarism, fraud, spam, deepfake content, phishing assistance, และการใช้ในบริบทการศึกษาโดยไม่มี governance

**Conflict core:**  
โครงการต้องสมดุลระหว่างการ democratize AI กับ responsible use policy, safeguards, education และ monitoring โดยไม่ละเมิด privacy

**Early warning indicators:**

- โรงเรียน/มหาวิทยาลัยรายงาน plagiarism เพิ่มขึ้น
- มีข่าวใช้ AI จากโครงการทำ scam content
- สื่อถามว่าโครงการมี guardrails หรือไม่

**Simulation variable:**

```yaml
ai_misuse_risk:
  baseline_intensity: 0.45
  high_risk_contexts:
    - education_assignments
    - scam_content
    - impersonation
    - confidential_work_documents
  mitigation:
    - responsible_ai_curriculum
    - safety_policy
    - reporting_channel
    - educator_guidelines
```

---

### R17 — Communication Overclaim Risk

**Category:** Public communication / expectation management  
**Likelihood:** 4  
**Impact:** 4  
**Velocity:** fast  
**Risk score:** 16  
**Current posture:** High

**Description:**  
หากรัฐสื่อสารเกินกว่าสิ่งที่ระบบส่งมอบได้จริง เช่น “Pro เทียบเท่าทุกบริการ”, “สร้างรายได้ทันที”, “ข้อมูลปลอดภัย 100%”, หรือ “เพิ่ม GDP” โดยไม่มี evidence จะทำให้เกิด backlash เมื่อผู้ใช้พบข้อจำกัดจริง

**Conflict core:**  
ข้อความสื่อสารที่ดีสำหรับการเมืองอาจไม่แม่นพอสำหรับผู้เชี่ยวชาญและผู้ใช้จริง เมื่อถูก fact-check จะกลายเป็น trust damage

**Early warning indicators:**

- มี infographic โครงการที่ถูก tech community ตรวจผิด
- official statement ใช้คำ broad promise โดยไม่มีรายละเอียด
- ผู้ใช้จริงโพสต์ว่า “ไม่ได้เหมือนที่โฆษณา”

**Simulation variable:**

```yaml
communication_overclaim:
  baseline_intensity: 0.65
  mitigation:
    - clear_feature_matrix
    - honest_limitations
    - user_terms_explained
    - kpi_grounded_messages
```

---

### R18 — Post-12-Month Cliff and Dependency

**Category:** Sustainability / user dependency  
**Likelihood:** 4  
**Impact:** 3  
**Velocity:** slow  
**Risk score:** 12  
**Current posture:** Medium-High

**Description:**  
หลังสิทธิ์ 12 เดือนหมดลง ผู้ใช้ที่เริ่มพึ่งพา AI อาจต้องจ่ายเงินเอง ย้ายแพลตฟอร์ม หรือหยุดใช้ ทำให้เกิดคำถามว่าโครงการสร้าง capability ระยะยาวหรือสร้าง dependency ระยะสั้น

**Conflict core:**  
รัฐมองว่า 12 เดือนเป็นช่วงทดลองและสร้างทักษะ แต่ฝ่ายวิจารณ์มองว่าเป็นการสร้าง customer funnel ให้ vendor

**Early warning indicators:**

- ผู้ใช้ถามว่า “ครบ 1 ปีแล้วทำอย่างไรต่อ”
- vendor เสนอ paid upgrade หลังหมดสิทธิ์
- ไม่มี plan ต่อเนื่องสำหรับคนรายได้น้อยหรือสถานศึกษา

**Simulation variable:**

```yaml
post_12_month_cliff:
  baseline_risk: 0.62
  mitigation:
    - exit_plan
    - open_skill_portability
    - local_ai_alternatives
    - discounted_continuation_for_priority_groups
    - public_digital_centers_access
```

---

### R19 — Audit and Accountability Gap

**Category:** Accountability / performance governance  
**Likelihood:** 4  
**Impact:** 5  
**Velocity:** medium  
**Risk score:** 20  
**Current posture:** Critical

**Description:**  
หากไม่มีระบบ audit และ accountability ที่ชัดเจน โครงการจะถูกวิจารณ์ต่อเนื่องแม้เปิดใช้งานแล้ว เพราะสังคมไม่รู้ว่าใครรับผิดชอบ KPI ใด ใช้งบเท่าไร ใช้จริงเท่าไร และผลลัพธ์เป็นอย่างไร

**Conflict core:**  
รัฐอาจรายงานผลตาม deliverable ในสัญญา แต่ประชาชนต้องการ performance governance แบบ public dashboard และ independent verification

**Early warning indicators:**

- รายงานผลเป็น PDF เป็นครั้งคราว ไม่ใช่ dashboard
- ไม่มี baseline / target / actual แบบเปรียบเทียบ
- ไม่มีหน่วยงานภายนอกตรวจวัด outcome
- สื่อถามหา “หลักฐานว่าประชาชนได้ประโยชน์จริง”

**Simulation variable:**

```yaml
accountability_gap:
  baseline_intensity: 0.78
  minimum_public_dashboard:
    - registered_users
    - monthly_active_users
    - retention_30_90_180_days
    - token_or_usage_consumption
    - training_completion
    - use_case_completion
    - cost_per_active_user
    - privacy_incidents
    - support_resolution_time
```

---

### R20 — Contract Rigidity vs Public Feedback Conflict

**Category:** Contract management / governance  
**Likelihood:** 3  
**Impact:** 4  
**Velocity:** medium  
**Risk score:** 12  
**Current posture:** High

**Description:**  
เมื่อมีการลงนามสัญญาแล้ว การปรับรายละเอียดตามข้อเสนอจากเวทีรับฟังความคิดเห็นอาจทำได้จำกัด ความเสี่ยงคือสาธารณะมองว่าการรับฟังเกิดขึ้นหลัง decision point สำคัญ ทำให้ความชอบธรรมของ participation ลดลง

**Conflict core:**  
ภาครัฐต้องรักษากรอบกฎหมายและสัญญา ขณะที่ public stakeholders ต้องการให้ feedback ส่งผลต่อระบบจริง

**Early warning indicators:**

- คำถามว่า “ฟังความเห็นแล้วแก้อะไรได้บ้าง”
- ข้อเสนอสำคัญไม่ถูกนำไป action
- รัฐตอบด้วยข้อจำกัดทางสัญญาโดยไม่มี governance workaround

**Simulation variable:**

```yaml
contract_rigidity_conflict:
  baseline_intensity: 0.55
  mitigation:
    - publish_changeable_vs_fixed_scope
    - add_governance_layer_without_contract_change
    - add_public_kpi_dashboard
    - create_independent_oversight_committee
```

---

## 4. Conflict Map

### C01 — Government vs Opposition / Investigative Media

**Conflict theme:** Legitimacy of procurement and budget use

```yaml
conflict:
  government_position:
    - project_follows_law
    - e_bidding_is_open_and_fair
    - budget_per_user_is_low
    - project_is_investment_for_future
  opposition_media_position:
    - full_disclosure_required
    - tor_and_scoring_need_scrutiny
    - budget_requires_outcome_kpi
    - public_forum_may_be_too_late
  likely_escalation:
    - repeated_parliament_questions
    - timeline_reconstruction
    - document_based_storytelling
    - scandal_frame
  deescalation_condition:
    - publish_documents
    - allow_independent_audit
    - answer_with_evidence_not_slogan
```

---

### C02 — Government vs Tech Experts

**Conflict theme:** Policy goal is accepted, design execution is questioned

```yaml
conflict:
  government_position:
    - need_fast_national_ai_adoption
    - use_global_tech_to_scale_quickly
    - learn_to_earn_and_training_will_create_value
  tech_expert_position:
    - define_ai_model_vs_ai_app_vs_platform
    - disclose_token_and_feature_matrix
    - include_api_access_and_local_ecosystem
    - measure_actual_ai_adoption_not_access
  likely_escalation:
    - viral_technical_threads
    - feature_gap_analysis
    - privacy_architecture_questions
  deescalation_condition:
    - technical_whitepaper
    - public_architecture_diagram
    - expert_advisory_board
    - open_kpi_dashboard
```

---

### C03 — Foreign AI Vendors vs Local AI Startups

**Conflict theme:** Fast access vs national capability building

```yaml
conflict:
  foreign_vendor_advantage:
    - mature_models
    - large_scale_capacity
    - brand_recognition
    - ready_training_material
  local_startup_concern:
    - public_budget_flows_outward
    - thai_ai_industry_not_strengthened
    - local_products_excluded_from_distribution
    - user_data_and_behavior_benefit_big_platforms
  likely_escalation:
    - startup_founders_comment_publicly
    - digital_sovereignty_narrative
    - comparison_with_gpu_or_ai_infrastructure_budget
  deescalation_condition:
    - allocate_budget_to_thai_ai_tools
    - thai_ai_marketplace
    - local_model_benchmark
    - open_innovation_grants
```

---

### C04 — Public Benefit Narrative vs Public Trust Deficit

**Conflict theme:** Good policy idea cannot overcome weak trust alone

```yaml
conflict:
  benefit_narrative:
    - reduce_ai_access_inequality
    - improve_work_productivity
    - give_people_tools_for_income
    - keep_thailand_from_falling_behind
  trust_deficit:
    - large_budget_suspicion
    - procurement_opacity
    - fear_of_unused_subscription
    - uncertainty_about_data
  likely_escalation:
    - jokes_and_memes_about_waste
    - skepticism_after_launch
    - cost_per_active_user_discussion
  deescalation_condition:
    - visible_success_cases
    - user_outcome_stories_with_data
    - monthly_public_dashboard
```

---

### C05 — Privacy Promise vs Technical Verification

**Conflict theme:** Statement-level assurance vs auditable architecture

```yaml
conflict:
  official_assurance:
    - prompt_not_used_to_train_provider_models
    - data_stored_in_thailand
    - anonymous_access
    - id_verification_only_for_rights
  verification_demand:
    - data_flow_diagram
    - dpia_or_pdpa_review
    - deletion_rights
    - subprocessors_list
    - anonymization_method
  likely_escalation:
    - pdpa_expert_threads
    - enterprise_usage_warning
    - questions_about_thai_llm_reuse
  deescalation_condition:
    - privacy_whitepaper
    - audit_report
    - opt_out_controls
    - public_incident_reporting
```

---

### C06 — Mass User UX vs Technical Backend Complexity

**Conflict theme:** Consumer simplicity vs multi-model allocation system

```yaml
conflict:
  user_expectation:
    - simple_login
    - clear_model_choices
    - stable_speed
    - pro_like_features
    - no_confusing_quota
  backend_reality:
    - multiple_models
    - token_allocation
    - reserve_capacity
    - gpu_tpu_cloud_or_hybrid_model
    - provider_specific_limitations
  likely_escalation:
    - launch_day_outage
    - quota_confusion
    - perceived_low_quality_model
    - comparison_with_paid_apps
  deescalation_condition:
    - phased_rollout
    - clear_service_status
    - plain_language_quota_explanation
    - default_recommended_workflows
```

---

## 5. MiroFish Simulation Scenario Seeds

### Scenario A — “Transparency Recovery”

**Trigger:** รัฐเปิด TOR, สัญญา, scoring criteria, dashboard, data flow diagram และตั้ง independent audit committee

**Expected behavior:**

```yaml
scenario_transparency_recovery:
  government_trust: +0.25
  procurement_suspicion: -0.35
  tech_expert_alignment: +0.30
  opposition_attack_strength: -0.15
  public_confusion: -0.20
  remaining_risk:
    - actual_usage_outcome
    - model_feature_quality
    - local_ecosystem_support
```

**Narrative shift:**  
จาก “โครงการน่าสงสัย” → “โครงการยังต้องพิสูจน์ผลลัพธ์ แต่ตรวจสอบได้มากขึ้น”

---

### Scenario B — “High Registration, Low Retention”

**Trigger:** ยอดสมัครสูงในเดือนแรก แต่ MAU/retention/use-case completion ต่ำ และไม่มี dashboard เชิงคุณภาพ

**Expected behavior:**

```yaml
scenario_high_registration_low_retention:
  registration_metric: high
  active_usage: medium_low
  media_sentiment: skeptical
  budget_backlash: +0.30
  adoption_risk: +0.45
  government_reframe_strength: -0.20
```

**Narrative shift:**  
จาก “คนไทยแห่ใช้ AI” → “สมัครเพราะฟรี แต่ใช้จริงน้อย”

---

### Scenario C — “Feature Gap Backlash”

**Trigger:** ผู้ใช้พบว่าสิทธิ์ที่ได้ไม่เทียบเท่าประสบการณ์ AI app Pro ที่คาดหวัง หรือมี quota/feature limitation ที่ไม่ได้สื่อสารชัด

**Expected behavior:**

```yaml
scenario_feature_gap_backlash:
  user_disappointment: +0.45
  tech_critique_amplification: +0.40
  meme_risk: +0.30
  value_for_money_backlash: +0.25
  procurement_suspicion: +0.10
```

**Narrative shift:**  
จาก “ได้ AI Pro ฟรี” → “ไม่ได้ Pro แบบที่คิด”

---

### Scenario D — “Privacy Shock”

**Trigger:** มีข่าวหรือความเข้าใจว่า prompt/user data ถูกจัดเก็บ ใช้ต่อยอด หรือเชื่อมโยงกับ identity โดยไม่ชัดเจน

**Expected behavior:**

```yaml
scenario_privacy_shock:
  public_trust: -0.40
  privacy_concern: +0.60
  enterprise_usage: -0.35
  education_usage: -0.20
  media_attention: +0.35
```

**Narrative shift:**  
จาก “รัฐให้ใช้ AI ฟรี” → “รัฐเก็บข้อมูลการใช้ AI ของประชาชนหรือไม่”

---

### Scenario E — “Local Ecosystem Pivot”

**Trigger:** รัฐเพิ่ม program สนับสนุน AI startup ไทย, Thai LLM, API marketplace, local tools, dataset governance และ developer credits

**Expected behavior:**

```yaml
scenario_local_ecosystem_pivot:
  local_startup_alignment: +0.45
  tech_expert_alignment: +0.30
  vendor_capture_narrative: -0.30
  long_term_policy_credibility: +0.35
  remaining_risk:
    - procurement_trust
    - actual_user_adoption
```

**Narrative shift:**  
จาก “ซื้อของต่างชาติ” → “ใช้ global AI เพื่อเร่ง adoption และสร้าง ecosystem ไทยควบคู่กัน”

---

## 6. Recommended Agent Conflict Parameters

```yaml
agents:
  government_mdes:
    trust_defensiveness: 0.80
    transparency_threshold: 0.55
    policy_benefit_confidence: 0.90
    sensitivity_to_political_attack: 0.75

  opposition_politician:
    procurement_focus: 0.95
    budget_attack_likelihood: 0.90
    responsiveness_to_new_documents: 0.95
    willingness_to_accept_dashboard: 0.35

  investigative_journalist:
    timeline_reconstruction: 0.90
    procurement_document_interest: 0.95
    expert_quote_amplification: 0.80
    scandal_frame_probability: 0.70

  ai_practitioner:
    supports_ai_literacy_goal: 0.75
    demands_technical_clarity: 0.90
    concern_about_model_vs_app_gap: 0.85
    concern_about_privacy_architecture: 0.80

  local_ai_startup_founder:
    supports_ai_adoption: 0.70
    concern_about_foreign_vendor_capture: 0.90
    demand_for_local_ecosystem_budget: 0.85
    possible_shift_to_support_if_included: 0.70

  general_public:
    interest_in_free_ai: 0.75
    budget_skepticism: 0.65
    privacy_concern: 0.45
    need_for_simple_onboarding: 0.85
    retention_without_use_case: 0.30

  student_user:
    adoption_probability: 0.80
    academic_integrity_risk: 0.60
    price_sensitivity: 0.85
    learning_path_need: 0.65

  sme_owner:
    adoption_probability_if_templates_exist: 0.75
    adoption_probability_without_templates: 0.25
    value_focus: 0.90
    support_if_cost_saving_visible: 0.85
```

---

## 7. Early Warning Indicator Dashboard

```yaml
early_warning_dashboard:
  procurement:
    - tor_keywords_trending
    - bidder_relationship_posts
    - parliament_questions
    - procurement_document_screenshots

  budget:
    - cost_per_active_user_discussion
    - low_usage_vs_budget_headlines
    - comparison_with_alternative_budget_uses

  adoption:
    - registration_without_mau
    - low_training_completion
    - low_30_day_retention
    - user_confusion_posts

  product:
    - ai_pro_feature_gap_threads
    - model_vs_app_explainer_posts
    - quota_confusion
    - launch_day_system_status_complaints

  privacy:
    - prompt_storage_questions
    - id_verification_concerns
    - pdpa_expert_comments
    - thai_llm_data_reuse_questions

  ecosystem:
    - thai_startup_criticism
    - big_tech_capture_narrative
    - local_ai_budget_demands
```

---

## 8. Conflict-Resolution Actions for Simulation

ให้ MiroFish จำลองผลของ policy interventions ต่อ sentiment

```yaml
interventions:
  publish_procurement_pack:
    includes:
      - tor
      - contract
      - scoring_criteria
      - bidder_summary
      - cost_breakdown
    expected_effect:
      procurement_trust_risk: -0.30
      political_escalation: -0.15
      tech_expert_alignment: +0.15

  publish_ai_passport_dashboard:
    includes:
      - registered_users
      - monthly_active_users
      - retention
      - model_usage
      - training_completion
      - cost_per_active_user
      - support_metrics
    expected_effect:
      value_for_money_backlash: -0.25
      adoption_failure_risk: -0.20
      accountability_gap: -0.35

  publish_privacy_and_architecture_whitepaper:
    includes:
      - data_flow_diagram
      - pdpa_assessment
      - storage_location
      - anonymization_method
      - retention_period
      - opt_out_controls
      - model_provider_data_policy
    expected_effect:
      privacy_concern: -0.35
      data_localization_conflict: -0.25
      expert_trust: +0.25

  launch_role_based_ai_workflows:
    target_groups:
      - students
      - teachers
      - sme_owners
      - freelancers
      - office_workers
      - farmers
      - civil_servants
    expected_effect:
      adoption_failure_risk: -0.30
      training_symbolism_risk: -0.25
      digital_divide_reproduction: -0.20

  include_local_ai_ecosystem:
    includes:
      - thai_ai_tool_marketplace
      - developer_api_credits
      - local_startup_grants
      - thai_llm_benchmark
      - public_sector_use_case_challenges
    expected_effect:
      vendor_capture_narrative: -0.35
      local_ecosystem_alienation: -0.40
      tech_expert_alignment: +0.25
```

---

## 9. Recommended Simulation Questions

ใช้เป็น prompt เสริมใน MiroFish

```text
Simulate how the TH-AI Passport project risks evolve over 90 days after public debate peaks.

Focus on these conflict lines:
1. Government transparency claims vs public demand for procurement evidence
2. AI literacy policy goal vs skepticism over actual AI adoption
3. AI Pro expectation vs actual model/platform capability
4. Privacy assurance vs need for auditable data governance
5. Global vendor access vs local Thai AI ecosystem development
6. Public forum participation vs contract rigidity

For each simulation round, track:
- public trust
- procurement suspicion
- budget backlash
- tech expert alignment
- local startup alignment
- privacy concern
- actual adoption confidence
- media amplification
- political escalation

Generate risk events, agent reactions, narrative shifts, and recommended de-escalation actions.
```

---

## 10. Source Index for Simulation Context

> Sources are included for traceability of public signals and risk framing. This file does not claim that every public allegation is true; allegations are modeled as narrative risks.

1. Thai PBS, “TH-AI Passport คืออะไร กางไทม์ไลน์จัดซื้อจัดจ้างวงเงินกว่า 1.6 พันล้าน”, 2026-06-10  
   URL: https://www.thaipbs.or.th/news/content/506890

2. กรมประชาสัมพันธ์, “รมว.ดีอี แจง TH-AI Passport โปร่งใสทุกขั้นตอน ย้ำใช้งบคุ้มค่า...”, 2026-05-28  
   URL: https://www.prd.go.th/th/content/category/detail/id/39/iid/507369

3. ฐานเศรษฐกิจ, “เสียงสะท้อนวงการเทค TH-AI Passport แจก AI ฟรี 5 ล้านสิทธิ์ คุ้มงบ 1.6 พันล้านหรือไม่”, 2026  
   URL: https://www.thansettakij.com/technology/ai/660310

4. แนวหน้า, “ดีอี ลุยต่อ TH-AI Passport เปิดเวทีใหญ่ 11 มิถุนายน ไชยชนก ถกทุกฝ่าย”, 2026-06-09  
   URL: https://www.naewna.com/politic/969658

5. Ministry of Digital Economy and Society / MDES public statements on TH-AI Passport transparency, AI adoption, data governance, and Learn to Earn framing  
   URL: https://www.mdes.go.th/

---

## 11. Final Risk Summary

```yaml
final_risk_summary:
  overall_risk_level: high
  highest_risk_domains:
    - procurement_trust
    - value_for_money
    - adoption_retention
    - privacy_governance
    - accountability_gap
  most_important_conflict:
    - policy_benefit_vs_public_trust
  best_deescalation_path:
    - disclose_documents
    - publish_dashboard
    - clarify_product_features
    - publish_privacy_architecture
    - include_local_ai_ecosystem
  worst_escalation_path:
    - no_contract_disclosure
    - high_registration_only_metrics
    - user_feature_gap_backlash
    - privacy_confusion
    - political_scandal_framing
```
