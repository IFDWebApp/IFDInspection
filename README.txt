วิธีทำให้ติดตั้งเป็นแอปบน Android / iOS (PWA)
================================================
เหตุผล: Apps Script ไม่ให้ใส่ manifest/service worker ในหน้าของมันเอง
จึงใช้ "หน้าห่อ" (ไฟล์ในโฟลเดอร์นี้) โฮสต์บน HTTPS แล้วฝังแอปจริงไว้ข้างใน

1) แก้ pwa/index.html บรรทัด EXEC_URL ให้เป็น URL Web app (…/exec) ของคุณ
   (Deploy → Web app → Who has access: Anyone / Anyone with Google account)
2) อัปโหลดทั้งโฟลเดอร์ pwa ขึ้นโฮสต์ HTTPS ฟรี เช่น
   - GitHub Pages: สร้าง repo → อัปโหลดไฟล์ทั้งหมดไว้ที่ root → Settings → Pages → Deploy from branch (main /root)
   - Netlify / Cloudflare Pages: ลากโฟลเดอร์ไปวาง
3) เปิด URL ของหน้าห่อบนมือถือ
   - Android (Chrome): เมนู ⋮ → "ติดตั้งแอป" / "เพิ่มลงในหน้าจอหลัก"
   - iPhone/iPad (Safari เท่านั้น): ปุ่มแชร์ → "เพิ่มลงในหน้าจอหลัก"
4) เปิดจากไอคอนจะเต็มจอ ไม่มีแถบ address bar

หมายเหตุ
- อัปเดตโค้ด Apps Script (New version) ผู้ใช้ได้ของใหม่ทันที ไม่ต้องติดตั้งใหม่
- ต้องใช้งานออนไลน์ (ข้อมูลอยู่บน Google Sheets)
- ถ้าบัญชี Google ของผู้ใช้ล็อกอินหลายบัญชี/เบราว์เซอร์บล็อก third-party cookies
  ให้ตั้ง Web app เป็น Anyone (ไม่ต้องล็อกอิน Google) ซึ่งระบบนี้ใช้รหัสพนักงาน+PIN อยู่แล้ว

เชื่อมกับปุ่มในแอป (ตั้งค่าผู้ใช้ → ติดตั้งแอปบนมือถือ)
-------------------------------------------------------
เปิด Index.html (ของ Apps Script) ค้นหา  var PWA_URL = '';
แล้วใส่ลิงก์ GitHub Pages ของคุณ เช่น  var PWA_URL = 'https://ชื่อ.github.io/ifdpm/';
จากนั้น Save → Deploy → New version
ผู้ใช้กดปุ่มในแอป (ที่เปิดผ่าน Google Sites เดิม) → เปิดหน้าติดตั้ง (?install=1)
 - Android: กด "ติดตั้งแอปเลย" แล้วยืนยัน
 - iPhone: แสดงขั้นตอน แชร์ → เพิ่มลงในหน้าจอหลัก (iOS ไม่อนุญาตให้ติดตั้งอัตโนมัติ)
