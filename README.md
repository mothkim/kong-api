# มาลองเล่น kong api gateway กันซ๊ะหน่อย ใช้เป็น Version : Kong Open–Source (Community) #

เริ่มจากอันดับแรกเลย มารู้จักก่อนว่า API คืออะไร API ย่อมาจาก “Application Program Interface” ลองดูรูปนี้ก่อน

![image](https://github.com/Arctica-th/kong/assets/105619969/08b2f82f-c318-44f7-a55d-3abf01b61afa)

การทำงานคือ API ทำหน้าที่เป็นส่วนที่ทำงานประมวลผลตามที่ถูกออกแบบมา ก็ลอง จำลอง ภาพด้านบนนี้ว่าคือการที่ Client ส่ง request มาที่ API ==> API ก็จะไปหยิบข้อมูลจาก Database เพื่อมาตอบให้กับ Client ตาม request ที่ได้รับมาและเป็นไปตามการทำงานของ API เอ๊ะ!!! เป็นไปตามการทำงานของ API ทำไมหน่ะเหรอ ก็เพราะว่า API ถูกสร้างมาเพื่อทำงานตามที่โปรแกรมไว้ และมีเงื่อนไขการรับข้อมูล ว่าต้องการอะไรบ้างแล้วถึงจะ reponse ผลลัพธ์กลับไปให้คนที่ request เข้ามา โดยปกติ ก็จะต้องระบุว่าเป็น method อะไร, parameter ต้องส่งอะไรมาบ้าง, format แบบไหน เป็นต้น
---

### KONG Gateway ###
![image](https://github.com/Arctica-th/kong/assets/105619969/bb039901-67dd-4619-9982-951ee9ae4029)

ที่นี่มาเจอคนๆ นี้หน่อย KONG The API Gateway!!!!

<img src="https://github.com/Arctica-th/kong/assets/105619969/b030c159-a184-43ba-9b87-25ead42ffebc" alt="drawing" width="500"/>

Kong คืออะไรล่ะ ดียังไง ทำไมต้องใช้ จะดีกว่าไหมถ้าฝั่ง Back-end ไม่ต้องเสียเวลาในการเขียนบ NodeJS เพื่อเรียก Microservice ในการทำ API Gateway ด้วย “KONG” ซึ่งเป็น Open Source ที่ทำหน้าที่บริหารจัดการ API (Application Programming Interface) หรือที่เรียกกันว่า API Gateway ที่สามารถ Scale ได้ง่ายและมีความปลอดภัยสูง KONG ทำงานเป็นตัวกลางในการสื่อสารระหว่าง Clients กับ Microservice ต่างๆ ช่วยบริหารจัดการ Functionality ทั้งหมดเลยไม่ว่าจะเป็น Caching, Monitoring, Authentication หรือแม้กระทั้ง Rate-limiting ซึ่งจะเหมาะและตอบโจทย์ของ Modernise Application และก็สามารถ Scale ได้ทุกครั้งขึ้นอยู่กับการใช้งาน ทำให้ผู้ใช้งานสามารถโฟกัส Product และ Service ใหม่ได้โดยไม่ต้องกังวลเรื่องของการจัดการ API

ซึ่ง Kong มีทั้งแบบที่เสียเงินและฟรี

แบบฟรี Kong Open-Source (Community)
เรามาเริ่มที่ตัว Open-Source หรือที่หลายคนเรียกว่า Community กันก่อนเลยดีกว่า ตัวนี้คือ API Gateway แบบทั่วไป ไม่เสียค่าใช้จ่าย ซึ่งทำหน้าที่เป็นตัวกลางเชื่อมต่อและสื่อสารระหว่างแอปพลิเคชัน สามารถนำ Free Plugins มาติดตั้งเพิ่มเติมเพื่อให้เหมาะสมกับการใช้งานได้

แบบเสียเงิน Kong Enterprise
มาต่อกันที่ฝั่ง Enterprise กันบ้าง เปรียบเทียบให้เห็นภาพชัดๆ เลยก็คือ Kong Enterprise เป็นบริการที่เสียค่าใช้จ่ายเพื่ออัพเกรดฟีเจอร์ให้แอดวานซ์ขึ้นไปอีกขั้น ด้วยคุณสมบัติที่มากกว่า Kong Open-Source นั่นเองตัวอย่างเช่น GUI ที่เอาไว้ควบคุมการใช้งานต่างๆ มาพร้อมระบบป้องกันความปลอดภัย รองรับการขยายของ Application ในกรณีที่มี Workload สูง เสี่ยงต่อการเกิดปัญหานั่นเอง
แม้ว่า Kong Enterprise จะมาพร้อมคุณสมบัติที่ตอบโจทย์การใช้งานรอบด้านขนาดนี้ แต่รู้หรือไม่ว่า ค่าใช้จ่ายในการใช้บริการนั้นเป็นมิตรกับผู้ใช้งาน ซึ่งมาในรูปแบบของ Pay-as-you-go Pricing Model และที่มากไปกว่านั้น Kong Enterprise ยังมีทีมผู้เชี่ยวชาญหลังบ้านที่คอยให้ความช่วยเหลือในกรณีเกิดปัญหาการใช้งานอีกด้วย

ลองมาเทียบข้อมูลทั้ง Kong Open-Source และ Enterprise กันหน่อย

Kong Open-Source (Community)
1. Microservice  API Gateway : สามารถที่จะใช้ API เพื่อเป็นตัวกลางของการสื่อสารแอปพลิเคชันต่างๆ
2. Open Source Plugins : สามารถที่จะนำ Third Party เข้ามา Integrate กับ Kong ได้
3. Community Support : ทาง Kong มีแหล่งรวบรวมข้อมูล หรือนักพัฒนาที่จะคอยช่วยเหลือและให้คำตอบตลอดเวลาในกรณีที่เราติดปัญหาต่างๆ ไม่ว่าจะเป็นการติดตั้งหรือการใช้งาน

Kong Enterprise
1. Kong Admin GUI : มีหน้ากากที่เอาไว้บริหารจัดการ API
2. Kong Security : รองรับในส่วนของการทำ AAA (Authentication, Authorisation, Auditing)
3. Kong Dev Portal : สามารถที่จะติดตั้งหรือบริหารจัดการ Service ต่างๆ ได้
4. Kong Analytics : ทำการ Monitor API traffic ได้โดยข้อมูลที่ได้รับจะเป็นแบบ Real-Time
5. Kong Scalability : สามารถที่จะขยายออกหรือหดเข้าได้ทุกเมื่อขึ้นอยู่กับการใช้งานและ Traffic ต่างๆ

ร่ายยาวเลย ถึงเวลามาลองเล่นกันละ มาเริ่มจากใน git repo ของเราในนี้มีอยู่ 2 ไฟล์
1.docker-compose.yaml => ไฟล์ docker-compose สำหรับ start kong + konga(UI) และก็มี database ด้วยนะ มี postgresql สำหรับใช้งานกับ kong , mongoDB สำหรับใช้งานกับ konga
2.kus.js => เป็นไฟล์ที่ใส่รายระเอียดของ User : admin ซึ่งจะเพิ่ม User อื่นอีกก็ได้

อันดับแรกเลย เครื่องที่เราจะใช้ทดสอบจะต้องมี docker และสามารถใช้งาน docker-compose , docker compose ได้ด้วย
![image](https://github.com/Arctica-th/kong/assets/105619969/8429d1b7-08e3-47af-9916-2b5ac0349e48)
![image](https://github.com/Arctica-th/kong/assets/105619969/bbd2fb6e-195c-459f-aae0-512985c1ce2f)

```
docker --version
docker-compose version
```

output

![image](https://github.com/Arctica-th/kong/assets/105619969/1678a858-740e-4432-a79d-584bd4b9ae0c)


มาเริ่มเลย
1. git clone https://github.com/Arctica-th/kong.git
2. cd kong
3. มาดูไฟล์ kus.js กันหน่อย ก็นั่นแหละ username / password ก็ในรายละเอียดไฟล์นี้เลย
```
module.exports = [
    {
        "username": "admin",
        "email": "admin@domain.com",
        "firstName": "Admin",
        "lastName": "Admin",
        "node_id": "http://kong:8001",
        "admin": true,
        "active": true,
        "password": "admin1234"
    }
];
```
4. start kong ขึ้นมา ปลุกชีพ
```
docker-compose up -d
```
![image](https://github.com/Arctica-th/kong/assets/105619969/e7796e6a-7291-47ed-a96f-94522de890be)

![image](https://github.com/Arctica-th/kong/assets/105619969/925c2d15-e7f4-4153-9b8f-00f363809871)

5. Check status kong container กันหน่อย
```
docker ps -a
```

6. เรียบร้อย kong container healthy ละ
7. เปิด web browser ขึ้นมา แล้วลองเข้า Konga ดู
```
http://localhost:1337
```
8. login ลอกมาจากไฟล์ kus.js ได้เลย
9. ในหน้านี้ให้เราใส่รายละเอียดของ kong gateway ก่อนถึงจะเข้าสู่หน้าหลักได้

ที่นี่เราจะมาลอง configure Kong กันหน่อยเพื่อทดสอบการใช้งาน kong เบื้องค้น
