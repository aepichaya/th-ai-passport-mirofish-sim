# TH-AI Passport Public Opinion Simulation

ชุดข้อมูลและรายงานจำลองกระแสสังคมของโครงการ **TH-AI Passport / AI Pass TH** ด้วยเครื่องมือ **MiroFish** ซึ่งเป็นระบบ AI multi-agent simulation สำหรับจำลองปฏิกิริยาของผู้มีส่วนเกี่ยวข้องหลายกลุ่ม และวิเคราะห์ว่า public opinion อาจพัฒนาไปทางใดในอนาคต

โครงการนี้จัดทำขึ้นเพื่อทดลองใช้ AI simulation ในการวิเคราะห์ประเด็นสาธารณะ โดยเน้นเรื่องความเชื่อมั่นของประชาชน ความโปร่งใส ความคุ้มค่าของงบประมาณ การใช้งานจริงของประชาชน ความเป็นส่วนตัวของข้อมูล และความสามารถด้าน AI ของประเทศในระยะยาว

> Repository นี้จัดทำเพื่อการวิจัย การเรียนรู้ การวิเคราะห์เชิงสถานการณ์ และการอภิปรายสาธารณะเท่านั้น
> ผลลัพธ์จาก simulation ไม่ใช่คำทำนายที่ยืนยันว่าจะเกิดขึ้นจริง ไม่ใช่ข้อกล่าวหา และไม่ใช่รายงานทางการ

---

## ที่มาของโครงการ

**TH-AI Passport / AI Pass TH** เป็นโครงการที่เกี่ยวข้องกับการเปิดให้ประชาชนเข้าถึงเครื่องมือ AI และการยกระดับทักษะด้าน AI ในประเทศไทย ซึ่งได้รับความสนใจและถูกพูดถึงอย่างกว้างขวางในสังคม

ประเด็นที่ถูกพูดถึงประกอบด้วย

* การเพิ่มการเข้าถึง AI ของประชาชน
* การพัฒนาทักษะดิจิทัลและ AI
* การลด digital divide
* ความคุ้มค่าของงบประมาณ
* ความโปร่งใสของการจัดซื้อจัดจ้าง
* ความปลอดภัยและความเป็นส่วนตัวของข้อมูล
* การพึ่งพาโมเดลและโครงสร้างพื้นฐานจากต่างประเทศ
* การใช้งานจริงหลังจากประชาชนได้รับสิทธิ์
* ผลลัพธ์ระยะยาวต่อแรงงาน นักเรียน นักศึกษา SME และผู้ประกอบการ

Repository นี้นำประเด็นเหล่านี้มาจัดเป็น seed material สำหรับใช้จำลองสถานการณ์ด้วย MiroFish

---

## โครงสร้างไฟล์ใน Repository

```text
.
├── 01_project_summary.md
├── 02_timeline_and_facts.md
├── 03_stakeholders.md
├── 04_public_opinion_signals.md
├── 05_risks_and_conflicts.md
├── 06_simulation_requirement.md
├── reports/
│   ├── simulation_report_01.md
│   └── simulation_report_02.md
└── README.md
```

---

## คำอธิบายไฟล์

### 01_project_summary.md

สรุปภาพรวมของโครงการ TH-AI Passport / AI Pass TH ได้แก่ เป้าหมายของโครงการ ประโยชน์ที่คาดหวัง ประเด็นที่สังคมให้ความสนใจ และบริบทเชิงนโยบาย

### 02_timeline_and_facts.md

รวบรวม timeline ของเหตุการณ์สำคัญ เช่น การประกาศนโยบาย ข่าวจากหน่วยงานรัฐ รายงานข่าว ความเห็นสาธารณะ และ trigger ที่ทำให้เกิดกระแสถกเถียง

### 03_stakeholders.md

แผนที่ผู้มีส่วนเกี่ยวข้องที่ใช้เป็นฐานในการสร้าง agent สำหรับ simulation เช่น

* รัฐบาล / กระทรวงดิจิทัลฯ
* ประชาชนทั่วไป
* นักเรียน นักศึกษา
* ครู
* SME
* ฟรีแลนซ์
* Developer / AI Practitioner
* สื่อมวลชน
* ภาคประชาสังคม
* นักการเมืองฝ่ายค้าน
* Vendor / ผู้ให้บริการ AI

### 04_public_opinion_signals.md

ไฟล์รวบรวมสัญญาณกระแสสังคม เช่น narrative ที่กำลังเกิดขึ้น คำถามของประชาชน ความเห็นจากกลุ่มเทคโนโลยี ประเด็นจากสื่อ และข้อกังวลที่อาจขยายตัวเป็นกระแสใหญ่

ไฟล์นี้ใช้เพื่อช่วยให้ simulation เข้าใจทิศทางของ public opinion

### 05_risks_and_conflicts.md

ไฟล์วิเคราะห์ความเสี่ยงและความขัดแย้งหลักของโครงการ เช่น

* ความโปร่งใสของการจัดซื้อ
* ความคุ้มค่าของงบประมาณ
* ความเป็นส่วนตัวของข้อมูล
* Data governance
* AI sovereignty
* Vendor lock-in
* การลงทะเบียนสูงแต่ใช้งานต่อจริงต่ำ
* ระบบ onboarding ไม่เพียงพอ
* การขยายประเด็นโดยสื่อและการเมือง
* ความเชื่อมั่นของประชาชนลดลง

### 06_simulation_requirement.md

ไฟล์ prompt หลักสำหรับใช้สั่ง MiroFish ให้จำลองสถานการณ์ โดยกำหนดเป้าหมายของ simulation กลุ่ม agent ที่เกี่ยวข้อง คำถามหลักที่ต้องการวิเคราะห์ และรูปแบบรายงานที่ต้องการ

### reports/

โฟลเดอร์เก็บรายงานที่ generate จาก MiroFish

รายงานเหล่านี้เป็น scenario-based report หรือรายงานเชิงสถานการณ์สมมุติ ไม่ใช่ข้อเท็จจริง ไม่ใช่คำทำนายแบบฟันธง และไม่ใช่ข้อสรุปทางกฎหมายหรือทางการเมือง

---

## วัตถุประสงค์ของ Simulation

คำถามหลักของ simulation คือ

> กระแสสังคมต่อโครงการ TH-AI Passport จะพัฒนาไปทางไหน หากโครงการเดินหน้าต่อภายใต้ระดับความโปร่งใส ความน่าเชื่อถือ คุณภาพการใช้งาน และการสนับสนุนผู้ใช้ที่แตกต่างกัน

หัวข้อที่ simulation ให้ความสำคัญ ได้แก่

* ความเชื่อมั่นของประชาชน
* ความคุ้มค่าของงบประมาณในสายตาสังคม
* ความโปร่งใสของการจัดซื้อจัดจ้าง
* พฤติกรรมการใช้งาน AI ของประชาชน
* คุณภาพของ onboarding
* ความเป็นส่วนตัวของข้อมูล
* ข้อวิจารณ์จากกลุ่ม Developer / AI Practitioner
* การขยายประเด็นโดยสื่อ
* การตีความเชิงการเมือง
* Retention หลังจากประชาชนลงทะเบียน
* แนวทางฟื้นความเชื่อมั่น
* ความสามารถด้าน AI ของประเทศในระยะยาว

---

## สมมุติฐานหลัก

Simulation นี้ตั้งอยู่บนสมมุติฐานว่า

> TH-AI Passport จะไม่ได้สำเร็จหรือ失败จากจำนวนคนลงทะเบียนเพียงอย่างเดียว
> โครงการจะสำเร็จหากสามารถกลายเป็นระบบสร้างทักษะ AI และ productivity ให้คนไทยได้จริง
> แต่จะล้มเหลวในเชิง perception หากถูกมองว่าเป็นเพียงการแจกสิทธิ์ AI subscription ขนาดใหญ่โดยไม่มีผลลัพธ์ที่วัดได้

---

## Key Findings จาก Simulation

จากการรัน simulation พบ pattern สำคัญหลายข้อ

### 1. เป้าหมายของโครงการมีศักยภาพสูง

แนวคิดการทำให้ประชาชนเข้าถึง AI เป็นแนวคิดที่มีคุณค่า หากดำเนินการได้ดี สามารถช่วยเรื่อง

* AI literacy
* Productivity ของแรงงาน
* ความสามารถในการแข่งขันของ SME
* การศึกษา
* งานฟรีแลนซ์และ creator economy
* Digital transformation ของประเทศ

### 2. ประเด็นที่สังคมกังวลไม่ใช่ตัว AI

แบบจำลองสะท้อนว่า ประชาชนจำนวนมากสนใจ AI และพร้อมทดลองใช้

ประเด็นหลักไม่ได้อยู่ที่ว่า AI มีประโยชน์หรือไม่ แต่อยู่ที่ว่าโครงการนี้โปร่งใส ใช้งานได้จริง วัดผลได้ และน่าเชื่อถือพอหรือไม่

### 3. การลงทะเบียนไม่เท่ากับการใช้งานจริง

จำนวนผู้ลงทะเบียนอาจช่วยสร้างภาพความสำเร็จช่วงเปิดตัว แต่ความสำเร็จระยะยาวต้องวัดจาก active usage และ real-world outcome

ตัวชี้วัดที่สำคัญ เช่น

* Monthly active users
* Retention หลัง 30 / 90 / 180 วัน
* จำนวนผู้เรียนจบ learning path
* จำนวน use case ที่ทำสำเร็จ
* เวลาทำงานที่ลดลง
* ต้นทุนของ SME ที่ลดลง
* รายได้ที่เพิ่มขึ้น
* ความพึงพอใจของผู้ใช้

### 4. Onboarding เป็นปัจจัยชี้ชะตา

การให้สิทธิ์ AI Pro เพียงอย่างเดียวไม่ได้ทำให้ productivity เพิ่มขึ้นโดยอัตโนมัติ

โครงการต้องมีระบบสนับสนุน เช่น

* Template ภาษาไทย
* Workflow เฉพาะอาชีพ
* Use case library
* คู่มือสำหรับผู้เริ่มต้น
* Workshop
* Community support
* Helpdesk หรือ coaching
* ระบบ certificate หรือ learning milestone

### 5. ความโปร่งใสเป็นเงื่อนไขของความเชื่อมั่น

Simulation แสดงซ้ำว่า หากข้อมูลการจัดซื้อ ข้อมูลการใช้ข้อมูลส่วนบุคคล และโครงสร้างเทคนิคยังไม่ชัด ความเชื่อมั่นของประชาชนจะลดลง

ประเด็นที่ต้องการความชัดเจน ได้แก่

* TOR
* กระบวนการจัดซื้อจัดจ้าง
* เกณฑ์คัดเลือก vendor
* โครงสร้างราคา
* Data governance
* นโยบายการเก็บ prompt
* นโยบายการใช้โมเดล
* Auditability
* Cybersecurity
* Public KPI dashboard

### 6. AI Sovereignty เป็นประเด็นอ่อนไหว

ถ้าโครงการพึ่งพาโมเดลต่างประเทศ cloud ต่างประเทศ หรือ platform ภายนอกเป็นหลัก สังคมอาจตั้งคำถามเรื่องอธิปไตยทางเทคโนโลยี

คำถามสำคัญคือ

> ประเทศไทยกำลังสร้างความสามารถด้าน AI ระยะยาว หรือเพียงเช่าสิทธิ์ใช้เครื่องมือ AI ชั่วคราว

---

## Prompt ที่ใช้กับ MiroFish

```text
Simulate the public opinion trajectory of Thailand’s TH-AI Passport / AI Pass TH project over the next 90 days.

The simulation should model interactions among government officials, general citizens, students, SME owners, developers, AI practitioners, opposition politicians, journalists, civil society groups, and AI vendors.

Focus on:
- public trust
- perceived value for money
- procurement transparency
- AI adoption behavior
- onboarding quality
- privacy and data governance concerns
- technical criticism from AI/developer communities
- media amplification
- political framing
- possible recovery strategies

Generate three scenarios:
1. Best case: the project becomes a national AI literacy program
2. Base case: high registration but medium retention
3. Worst case: the project is framed as wasteful public spending

For each scenario, identify:
- key trigger events
- stakeholder reactions
- dominant narratives
- weak signals
- risk escalation path
- recommended government response
- measurable KPIs
```

---

## ค่าที่แนะนำสำหรับการรัน Simulation

สำหรับการรันครั้งแรก

```text
Simulation length: 30–90 days
Rounds: 20–40
Agent groups: 6–8
Agent count: 30–80
Focus: public opinion, policy risk, adoption behavior
```

สำหรับการรันแบบละเอียด

```text
Simulation length: 180–365 days
Rounds: 80–150
Agent count: 150–500
Scenario branches:
- รัฐเปิด transparency dashboard
- รายละเอียดการจัดซื้อยังไม่ชัด
- ระบบเปิดตัวแล้วใช้งานยาก
- Tech influencer ออกมาสนับสนุน
- ฝ่ายค้านยกระดับการตรวจสอบงบประมาณ
- ประชาชนลงทะเบียนจำนวนมากแต่ใช้งานต่อจริงน้อย
```

---

## ตัวอย่าง Stakeholder Agents

### Government / MDES

แรงจูงใจ

* ผลักดัน national AI adoption
* สร้าง policy success
* ลดความเหลื่อมล้ำด้านดิจิทัล
* วางภาพประเทศไทยว่าเป็นประเทศที่พร้อมใช้ AI

ความเสี่ยง

* ถูกวิจารณ์หากผลลัพธ์ไม่ชัด
* ถูกตรวจสอบเรื่องงบประมาณและความโปร่งใส

### General Public

แรงจูงใจ

* อยากทดลองใช้ AI
* อยากเข้าถึงเครื่องมือที่ปกติอาจมีค่าใช้จ่ายสูง
* อยากนำ AI ไปใช้กับงาน การเรียน หรือรายได้

ความเสี่ยง

* สมัครแล้วเลิกใช้เร็ว
* ไม่รู้ว่าจะนำ AI ไปใช้กับชีวิตจริงอย่างไร

### Developers / AI Practitioners

แรงจูงใจ

* ตรวจสอบ technical architecture
* ประเมินคุณภาพของโมเดล
* ตรวจสอบ data privacy และ governance
* ผลักดัน open standard และ local capability

ความเสี่ยง

* วิจารณ์หนักหากคำตอบเชิงเทคนิคไม่ชัด
* ตั้งคำถามเรื่อง vendor lock-in และการจัดการข้อมูล

### Media / Civil Society / Opposition

แรงจูงใจ

* ตรวจสอบการใช้งบประมาณรัฐ
* เรียกร้องความโปร่งใส
* ตรวจสอบผลลัพธ์และประโยชน์สาธารณะ

ความเสี่ยง

* ประเด็นอาจขยายเป็น controversy ทางการเมือง
* Narrative อาจเปลี่ยนจาก AI literacy เป็นการใช้งบไม่คุ้มค่า

### AI Vendors / Platform Providers

แรงจูงใจ

* ขยายฐานผู้ใช้
* ได้ distribution ระดับประเทศ
* เข้าไปเป็นส่วนหนึ่งของ AI ecosystem ไทย

ความเสี่ยง

* แบรนด์เสียหายหากประสบการณ์ใช้งานไม่ดี
* ถูกโยงกับข้อถกเถียงเรื่อง procurement

---

## วิธีใช้งาน Repository นี้

### 1. Clone หรือ Download Repository

```bash
git clone https://github.com/YOUR_USERNAME/YOUR_REPOSITORY_NAME.git
cd YOUR_REPOSITORY_NAME
```

### 2. ติดตั้ง MiroFish

ทำตามขั้นตอนจาก repository ต้นทางของ MiroFish

```bash
git clone https://github.com/666ghj/MiroFish.git
cd MiroFish
cp .env.example .env
docker compose up -d
```

จากนั้นเปิดใช้งานที่

```text
Frontend: http://localhost:3000
Backend: http://localhost:5001
```

### 3. Upload ไฟล์ Markdown

สร้าง project ใหม่ใน MiroFish แล้ว upload ไฟล์ต่อไปนี้

```text
01_project_summary.md
02_timeline_and_facts.md
03_stakeholders.md
04_public_opinion_signals.md
05_risks_and_conflicts.md
06_simulation_requirement.md
```

### 4. Build Graph

ใช้ MiroFish สร้าง knowledge graph จากไฟล์ที่ upload

### 5. Run Simulation

เริ่มจาก simulation ขนาดเล็กก่อน

ค่าที่แนะนำ

```text
20–40 rounds
30–80 agents
30–90 simulated days
```

### 6. Generate Report

หลังจาก simulation เสร็จ ให้ generate report และเปรียบเทียบผลลัพธ์จากแต่ละ scenario

---

## แนวทางการอ่านผลลัพธ์

ผลลัพธ์จาก simulation ควรถูกอ่านในฐานะ

* Scenario exploration
* Public opinion stress test
* Policy risk mapping
* Stakeholder reaction model
* Narrative forecasting experiment

ผลลัพธ์จาก simulation ไม่ควรถูกอ่านในฐานะ

* คำทำนายที่ยืนยันว่าจะเกิดขึ้นจริง
* การสืบสวนที่พิสูจน์แล้ว
* ข้อสรุปทางกฎหมาย
* รายงานทางการของรัฐ
* ข้อกล่าวหาต่อบุคคลหรือองค์กรใด

---

## ข้อจำกัดของโครงการ

1. ผลลัพธ์ขึ้นอยู่กับคุณภาพของ seed files
2. Public opinion signals เป็นข้อมูลเชิงคุณภาพ ไม่ใช่ social listening dataset ที่ครอบคลุมทุกโพสต์
3. พฤติกรรมของ agent เป็นพฤติกรรมจำลอง ไม่ใช่พฤติกรรมมนุษย์จริง
4. กระแสสื่อและการเมืองเปลี่ยนแปลงได้เร็ว
5. Simulation ไม่สามารถพิสูจน์ข้อกล่าวหาใด ๆ ได้
6. ผลลัพธ์ควรถูกตรวจสอบเทียบกับแหล่งข้อมูลทางการ ข่าว และเอกสารสาธารณะ

---

## Ethical Note

Repository นี้พูดถึงนโยบายสาธารณะ งบประมาณรัฐ เทคโนโลยี AI และความเสี่ยงเชิง governance

ประเด็นที่มีความอ่อนไหวควรถูกมองเป็น narrative, concern หรือ simulation variable จนกว่าจะมีข้อมูลยืนยันจากแหล่งที่ตรวจสอบได้

เป้าหมายของ repository นี้คือสนับสนุนการพูดคุยเรื่อง AI policy, transparency และ national digital capability อย่างมีเหตุผลมากขึ้น

---

## Disclaimer

Repository นี้เป็นงานวิเคราะห์สถานการณ์โดยอิสระ

ไม่ได้มีความเกี่ยวข้องกับหน่วยงานรัฐ พรรคการเมือง ผู้ให้บริการ AI หรือสื่อใด ๆ

เนื้อหาและรายงาน simulation จัดทำขึ้นเพื่อการวิจัย การศึกษา และการอภิปรายสาธารณะเท่านั้น
