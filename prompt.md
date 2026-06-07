คำสั่งงาน (Prompt) — สร้างเวอร์ชัน Vanilla HTML + Tailwind

อ่านกติกาการแข่งขัน CARC Maze Explorer และสร้างตัวอย่างแอปจำลองสนาม (static, vanilla HTML + JavaScript) โดยใช้ Tailwind CSS (CDN หรือ build) ให้มีลักษณะ compact และ responsive — ดูดีทั้งบนเดสก์ท็อปและมือถือ

ข้อกำหนดหลัก:
- แผนที่สุ่ม 7×7 (ROWS=7, COLS=7) สร้างจากผนัง/ขอบ (walls model: vertical/horizontal) — ห้ามใช้การสุ่มแบบ "ปิดช่อง" ให้เป็นการเปิด/ปิดผนังระหว่างเซลล์
- จุดเริ่มต้น: มุมล่างซ้าย (row=6,col=0)
- ไม่ให้เกิดช่องว่างเส้นประ (no dashed visual gaps) เว้นแต่เป็นตัวเลือกแสดงผล

UI และฟีเจอร์:
- ปุ่ม `Start` / `Stop` (toggle) และปุ่ม `Randomize Map`
- ตัวเลือก `Algorithm` ก่อนเริ่ม (options: DFS, Wall Follower, Left-hand, Right-hand, Random Walk, A*)
- ตัวแสดงโค้ดด้านข้าง (Code viewer) ที่สลับภาษาได้: ไทย (คำอธิบาย), Python (pseudo) และ `SPIKE` (ตัวอย่างโค้ดเป็น SPIKE Python v3 ตามเอกสาร)
- ปุ่ม `Copy` เพื่อคัดลอกโค้ด (สำเนาเฉพาะโค้ด ไม่เอาเลขบรรทัด)
- แสดงสถานะ: เวลา (timer), Visited count, Score, Restarts, Sensor readings (Front/Left/Right)
- ไอคอนหุ่นยนต์ SVG ที่มี: indicator ด้านหน้า, ล้อซ้าย/ขวาชัดเจน, จุดของเซ็นเซอร์ทั้ง 3 ชัดเจน

การจำลองและกติกา:
- ระบบสเต็ป: ฟังก์ชัน `stepOnce()` เรียกตาม interval ที่สามารถปรับได้ (slider หรือ input)
- เซ็นเซอร์จำลอง 3 ตัว: front, left, right — ให้คืนค่าระยะเป็นจำนวนเซลล์จนถึงผนัง
- ระบบการคำนวณ reachable cells (BFS) และปรับแผนที่จนได้เป้าหมาย reachable = 48 (TARGET_REACHABLE = 48)
- สูตรคะแนนตามกติกา CARC: `score = round(visited * 100 / 48) - restarts * 3` (จับให้ไม่เป็นค่าติดลบ)
- ห้ามมี layout shift เมื่อผนังเปลี่ยน — ให้สำรองพื้นที่ขอบ (reserve border widths)

โค้ด SPIKE (ข้อกำหนด):
- ตัวอย่างโค้ด `spike` ต้องเป็น SPIKE Python v3 (อ้างอิง: https://tuftsceeo.github.io/SPIKEPythonDocs/SPIKE3.html)
- ให้รวมตัวอย่างต่อไปนี้ในโฟลเดอร์ `spike_examples/`: `wall_follower.py`, `random_walk.py`, `left_hand.py`, `right_hand.py`, `dfs_scaffold.py`, `astar_follow.py` (Hub-side follow routine)

ผลลัพธ์ที่ต้องส่งมอบ (Static Vanilla app):
- โฟลเดอร์ `vanilla/` ที่มีอย่างน้อย: `index.html`, `app.js`, `styles` (ใช้ Tailwind CDN หรือ build), `README.md`
- โค้ด JavaScript ที่ทำงานได้ (สุ่มแผนที่, จำลองการเคลื่อนที่ ตามอัลกอริทึมที่เลือก, สรุปคะแนน/เวลา)
- ตัวอย่างไฟล์ SPIKE ใน `spike_examples/` (ตามข้อกำหนด SPIKE3)
- คำแนะนำสั้น ๆ ใน `README.md` เกี่ยวกับการรัน (เปิด `index.html` ด้วยเว็บเซิร์ฟเวอร์หรือไฟล์) และการปรับพอร์ต/พารามิเตอร์สำหรับฮาร์ดแวร์จริง

เพิ่มเติม:
- ให้โค้ดเรียบง่าย, มีคอมเมนต์สั้น ๆ อธิบายส่วนสำคัญ และสามารถนำไปต่อยอดเป็น Vite React เวอร์ชันได้โดยง่าย
- หากต้องการผมจะช่วย scaffold ไฟล์ `vanilla/` ให้ทันที (index.html + app.js + ตัวอย่างสไตล์ Tailwind)

อ้างอิง API SPIKE3: https://tuftsceeo.github.io/SPIKEPythonDocs/SPIKE3.html

