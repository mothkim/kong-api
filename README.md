# มาลองเล่น kong api gateway กันซ๊ะหน่อย ใช้เป็น Version : Kong Open–Source (Community) 

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

![image](https://github.com/Arctica-th/kong/assets/105619969/81d82ac4-f8c2-41aa-9a45-d32e0e63dbe1)


8. login ลอกมาจากไฟล์ kus.js ได้เลย

![image](https://github.com/Arctica-th/kong/assets/105619969/94b7eadc-e529-4385-84b5-0296778ab881)

9. ในหน้านี้ให้เราใส่รายละเอียดของ kong gateway ก่อนถึงจะเข้าสู่หน้าหลักได้

![image](https://github.com/Arctica-th/kong/assets/105619969/73fb7f8d-c80a-4393-b25a-c4a260e01c65)

ที่นี่เราจะมาลอง configure Kong กันหน่อยเพื่อทดสอบการใช้งาน kong เบื้องค้น

### ทดสอบการทำ api gateway ###
1. Run nginx ที่เป็น docker container ไว้สำหรับทดสอบ

```
docker run -d -p 8090:80 --name nginx nginx:latest
```
> ก็คือ รัน nginx container โดยเปิด port:8090 ของเครื่องไปที่ port:80 ของ container

2. ทดสอบเปิด web browser ของ nginx ก่อน
```
http://localhost:8090/
```
เปิดได้ละ
![image](https://github.com/Arctica-th/kong/assets/105619969/7701b669-4370-411e-b4ee-c0b2b19c5098)

3. สร้าง service
<img width="722" alt="image" src="https://github.com/Arctica-th/kong/assets/105619969/519db14e-f37b-4ddc-b13d-585eb7b16dc8">

กรอกข้อมูลของ service ที่เราจะไปต่อ ในที่นี่ก็คือ nginx พระเอกของเรา

<img width="447" alt="image" src="https://github.com/Arctica-th/kong/assets/105619969/2ff4f06f-a375-4329-a265-cb176cccbb46">

เสร็จแล้วก็กด <img width="377" alt="image" src="https://github.com/Arctica-th/kong/assets/105619969/8c64584a-4f30-48eb-8994-9f56ce30cc94">

4. สร้าง route โดนการกดเข้าไปใน service nginx ที่พึ่งสร้างเมื่อกี๊ แล้วเลือก route ในนี้ จากนั้นกด ADD ROUTE

<img width="1008" alt="image" src="https://github.com/Arctica-th/kong/assets/105619969/bd9301c3-340a-43df-a3d9-cbf4b36eb05c">

![image](https://github.com/Arctica-th/kong/assets/105619969/cfcf181c-cff4-469d-aaee-bddb3a03ff00)

5. หลังจากที่ configure service กับ route เรียบร้อยแล้วเราก็มาลอง เข้า web browser nginx ผ่าน kong api gateway กัน ว่าแล้วก็เริ่มกันเลยเปิดเข้าไปที่ URL:http://IP-Address-kong/mynginx

> IP-Address-kong = IP Address ของเครื่อง kong
> /mynginx = configure route ในกำหนดใน kong

ผลลัพธ์ คือ เราควรจะต้องโผล่ไปที่ nginx ที่ start เป็น container ไว้ ถ้าไปได้ แปลว่าที่ configure นั้นถูกต้อง แต่ถ้าไม่ให้ย้อนกลับไปดู configure ดีๆ

---
### มาลองทำ Basic Authen เพื่อกำหนดขอบเขตของคนที่มีสิทธิ์เข้ามาใช้งาน API นี้ได้กัน ##

ขั้นตอนนี้จะมีสิ่งที่ต้องเตรียมหลักๆ อยู่
1. consumer เปรียบเสมือน user ถ้าใครเคยใช้ kafka มา consumer จะหมายถึงผู้บริโภค หรือมองง่ายๆ ก็มองไปว่าเป็นขารับนั่นแหละ
2. Plugin Basic auth ก็คือ plugin ที่ไว้สำหรับ authen เพื่อกำหนดสิทธิ์ให้เฉพาะมีสิทธิ์เท่านั้น ที่จะสามารถ ใช้งาน API ได้ ซึ่ง Basic authen จะค่อนข้างง่ายในการทดสอบเพราะว่าใช้แค่ username/password ธรรมดา

### งั้นมาเริ่มกันเลย สร้าง consumer ก่อน ###
1. สร้าง consumer

ไปที่เมนู consumer แล้วกดสร้าง

![image](https://github.com/Arctica-th/kong/assets/105619969/af49a697-34cb-4064-b892-762afb11e819)

ใส่ข้อมูลของ consumer ตามที่ต้องการแล้วกด submit

![image](https://github.com/Arctica-th/kong/assets/105619969/36f9b46d-bfbd-4307-ae3d-d960d75a8fe5)

พอสร้างเสร็จแล้ว ก็ลองเข้าไปดูใน consumer หน้าตาก็จะเป็นแบบรูปด้านล่าง

![image](https://github.com/Arctica-th/kong/assets/105619969/88253011-edc0-4196-81af-f8727fa23bc0)

2. หลังจากสร้าง consumer เสร็จแล้ว ก็มา Add Plugin Basic auth ต่อ

กรอก username / password ที่ต้องการ แล้วกด submit

![image](https://github.com/Arctica-th/kong/assets/105619969/fc9706a1-4343-42c8-a2b5-e9e497a2784d)

เสร็จแล้ว จะได้หน้าตาแบบนี้

![image](https://github.com/Arctica-th/kong/assets/105619969/06e69995-f77b-4940-9158-363a7d5264b5)

จากนั้นไปยัง service ที่เราต้องการจะใส่่ Basic auth เลือกเมนู Plugin ด้านซ้ายมือ และกด ADD PLUGIN

![image](https://github.com/Arctica-th/kong/assets/105619969/f80271d5-8d6e-4f17-b367-14de23cdf179)

หลังจากกด ADD PLUGIN ไปแล้วจะมีหน้าต่างเด้งขึ้นมาให้เลือก plugin ให้กด ADD ที่ Basic Auth ได้เลย

![image](https://github.com/Arctica-th/kong/assets/105619969/d384d5f4-a721-4e36-a7e0-022d5cab337b)

จะมีหน้าต่างเด้งอีกครั้ง เป็นรูปด้านล่าง แต่ไม่เป็นไรกด ADD PLUGIN ได้เลย เย้!!!

![image](https://github.com/Arctica-th/kong/assets/105619969/12ab1c20-8392-4b86-b58a-007c943feb10)

Add Plugin เสร็จแล้วให้ไปดูเมนู "Eligible consumers" ซึ่งอันนี้จะแสดง consumer ที่มีสิทธิ์มาเรียก API นี้ได้

![image](https://github.com/Arctica-th/kong/assets/105619969/e8f09897-e8cb-4072-8108-43428ca02942)

ที่นี่ลองไปเปิด web browser ไปที่ service nginx ผ่าน kong api gatewaty กันใหม่อีกครั้ง URL:http://IP-Address-kong/mynginx
เราก็จะเจอกับหน้า authen ทันที เหอะๆ

![image](https://github.com/Arctica-th/kong/assets/105619969/295ee737-a219-413b-a2ac-6ee2622bf3ba)

---

### ALC Plugin ###

![image](https://github.com/Arctica-th/kong/assets/105619969/46148ec6-b577-4147-8d53-e14f59782d14)

ที่นี่มาลองใช้งาน Plugin อีกตัวที่เข้ามาควรจัดการ การเข้าถึงของ consumer อีกที นั่นก็คือ ACL Plugin

1. สร้าง consumer มาเพิ่มก่อน เพื่อให้เป็นคนที่ถูกเลือกให้ผิดหวัง

![image](https://github.com/Arctica-th/kong/assets/105619969/f2858151-241e-428c-a0fc-231a5610ef5e)

2. กำหนด group ให้กับ consumer กันก่อน ส่วนการเข้าไปกำหนด group ให้กับ consumer ก็ให้เข้าไปใน consumer นั้นๆ แล้วเลือกเมนู groups เสร็จแล้วก็กดปุ่ม ![image](https://github.com/Arctica-th/kong/assets/105619969/c2651ea9-ddb4-42c5-b185-cacbea46903c)

กำหนด consumer 'cs-1' ให้เป็น group1

![image](https://github.com/Arctica-th/kong/assets/105619969/c04e0633-76b2-4dc0-9e9a-47c09ac0b960)

กำหนด consumer 'cs-2' ให้เป็น group2

![image](https://github.com/Arctica-th/kong/assets/105619969/137f20a7-c032-4889-9357-1462061f2738)


3. Configure service เพิ่มโดยการ Add Plugin ACL เข้าไป และใส่ group ของ consumer แรก

![image](https://github.com/Arctica-th/kong/assets/105619969/b0e29512-3520-44f2-bbb4-a8984af46640)

หลังจากกด ADD PLUGIN

![image](https://github.com/Arctica-th/kong/assets/105619969/509d7006-1712-41c6-b5b5-2ec0eb1f2300)

4. เปิด web browser แปป เสร็จแล้วลองเปิดขึ้นมาใหม่ แต่เดี๋ยวก่อน นี่แหละ มาลองทีละอัน อันแรกลอง username/password ของ consumer-1 ก่อน

![image](https://github.com/Arctica-th/kong/assets/105619969/4e84ae86-1f34-40f6-b095-c2b4151d2375)

![image](https://github.com/Arctica-th/kong/assets/105619969/f5f9bdc7-69ec-4a9d-a46c-0643fcd9595a)

เห็นไหม เข้าได้ใช่ไหม งั้นเราไปดูคนที่ถูกเลือกให้ผิดหวังกัน เปิด tab ใหม่ขึ้นมาแล้วกรอก link เดิมเลย ที่นี่ลองใส่ username/password ของ consumer-2 ดู

![image](https://github.com/Arctica-th/kong/assets/105619969/aa5d0481-9251-4dd7-bdb3-ae089c64b563)

![image](https://github.com/Arctica-th/kong/assets/105619969/961082a0-aef3-4471-be5e-614fe75cacd6)

เรียบร้อย เข้าไม่ได้ใช่ไหมละ ก็เพราะเป็นคน... ไม่มีสิทธิ์... จะคิดดดดดดดดด เข้ามาก็ Deny ซิคร้าบบบ

ที่นี่เราก็สามารถจัดการ API โดยที่ไม่ต้องไปบอกให้ฝั่ง application ต้องแก้ไขเลย ก็แค่จัดการผ่าน kong api gateway ตรงนี้ แถบยังสามารถกำหนดสิทธิ์การเข้าถึงได้ด้วย ว่าจะอนุญาติให้ใครเข้ามาใช้งาน api ได้บ้าง

>ฝากไว้ให้ซี๊ด ในการใช้งาน plugin ACL ของตัว kong community หนึ่งสิ่งที่เจอและทำให้เสียเวลาไปพอตัวเลยก็คือ เมื่อทำการ configure ACL แล้วต้องการดูว่ามี consumer ไหนบ้างที่สามารถเข้าถึง service นี้ได้บ้าง ที่ Eligible consumers ปรากฏว่า ไม่มี list แสดงให้เห็น แต่่ใช่ มันทำงานได้ เพราะพึ่งลองทดสอบไปเมื่อกี๊ นั่นแหละครับ เป็นสิ่งที่ทำให้อยากต่อ user ที่ใช้งาน และกับคนที่พึ่งเริ่มต้นใช้งานอย่างเราๆ ต้องมาเจ็ฐปวดและเสียเวลาไปกับขั้นตอนนี้ แต่ก็นะใช้ของฟรีครับ ทำใจ อยากใช้ที่ Stable ก็คงต้องไปเสียเงิน ใครเขาทำงานเพื่อการกุศลกัน
