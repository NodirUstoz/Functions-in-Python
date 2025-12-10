# Python dasturlash tilida FUNKSIYALAR (Functions) mavzusi

---

## 1) Kirish — Funksiya nima va nega kerak?

### Funksiya nima?

**Funksiya** — bu ma'lum bir vazifani bajaruvchi, bir marta yozib, keyin xohlagancha qayta ishlatish mumkin bo'lgan kod blokidir.

Oddiy qilib aytganda: **funksiya — bu dastur ichidagi kichik dastur**.

### Hayotiy analogiya

**1-misol: Choy damlash**
```
Siz har safar choy ichmoqchi bo'lganingizda:
1. Choynak oling
2. Suv quying
3. Qaynatib oling
4. Choy bargini soling
5. Bir oz kutib turing
```

Agar siz kuniga 5 marta choy ichsangiz, bu jarayonni 5 marta takrorlab yozish kerak bo'lardi. Lekin "choy_damla()" degan funksiya yaratib qo'ysangiz, faqat chaqirasiz va tayyor!

**2-misol: Robot**

Uy ishlarini bajadigan robotingiz bor deylik:
- `tozala()` — uyni tozalaydi
- `taom_pishir()` — taom pishiradi
- `kir_yuv()` — kir yuvadi

Har safar sizga biror ish kerak bo'lganda, siz robotga buyruq berasiz (funksiyani chaqirasiz).

**3-misol: Fabrika**

Fabrikada mahsulot ishlab chiqarish uchun:
- Xom ashyo kiritiladi (parametrlar)
- Ishlov beriladi (funksiya tanasi)
- Tayyor mahsulot chiqariladi (return qiymati)

### 🤔 Nima uchun funksiyalar paydo bo'lgan?

Dasturchilar dastlab shuni tushunishdi:

1. **Bir xil kod ko'p marta takrorlanadi** — bu vaqt isrofi
2. **Xatoliklarni tuzatish qiyin** — 100 joyda xato bo'lsa, 100 joyni tuzatish kerak
3. **Kodni tushunish murakkab** — 1000 qatorlik kod o'qib chiqish mushkul

**Yechim: FUNKSIYALAR!**

### DRY — "Don't Repeat Yourself" printsipi

```python
# ❌ NOTO'G'RI — kodning takrorlanishi
ism = "Ali"
print("Assalomu alaykum, " + ism)
print("Xush kelibsiz!")
print("-" * 30)

ism = "Vali"
print("Assalomu alaykum, " + ism)
print("Xush kelibsiz!")
print("-" * 30)

ism = "Hasan"
print("Assalomu alaykum, " + ism)
print("Xush kelibsiz!")
print("-" * 30)
```

```python
# ✅ TO'G'RI — funksiya ishlatish
def salomlash(ism):
    """Foydalanuvchini salomlash funksiyasi"""
    print("Assalomu alaykum, " + ism)
    print("Xush kelibsiz!")
    print("-" * 30)

# Endi faqat chaqiramiz
salomlash("Ali")
salomlash("Vali")
salomlash("Hasan")
```

### Funksiyalarning afzalliklari

| # | Afzallik | Tushuntirish | Misol |
|---|----------|--------------|-------|
| 1 | **Qayta foydalanish** | Bir marta yoz, ko'p marta ishla | `hisoblash()` funksiyasini har joyda ishlatish |
| 2 | **Kodning tushunarli bo'lishi** | Kod o'qilishi oson | `malumot_tekshir()` nomi o'zi hamma narsani tushuntiradi |
| 3 | **Xatolarni tuzatish oson** | Faqat bir joyni tuzatish kifoya | Funksiyani tuzatsangiz, u ishlatilgan barcha joylarda tuzatiladi |
| 4 | **Modulizatsiya** | Katta dasturni kichik qismlarga bo'lish | Dasturni 50 ta funksiyaga bo'lish |
| 5 | **Sinash (Testing) oson** | Har bir funksiyani alohida sinash | `test_hisobla()` funksiyasi yozish |
| 6 | **Hamkorlik** | Bir necha dasturchi bitta loyihada ishlaydi | Ali `frontend()` funksiyalarini, Vali `backend()` funksiyalarini yozadi |
| 7 | **Vaqt tejash** | Bir marta yozasiz, doim ishlatasiz | 1000 qator kodni 10 ta funksiyaga qisqartirish |
| 8 | **Xavfsizlik** | Funksiya o'z ichidagi o'zgaruvchilarni yashiradi | Local scope tufayli xavfsizlik |

---

## 2) Funksiyaning sintaksisi — to'liq tushuntirish

### To'liq sintaksis

```python
def funksiya_nomi(parametr1, parametr2, parametr3):
    """
    Bu yerda funksiya haqida izoh yoziladi (docstring).
    Bu majburiy emas, lekin juda foydali!
    """
    # Funksiya tanasi (body) — bu yerda kodlar yoziladi
    natija = parametr1 + parametr2 + parametr3
    return natija  # Natijani qaytarish
```

### Har bir element batafsil tushuntirish

#### 1️⃣ `def` — kalit so'z

- **def** — "define" so'zining qisqartmasi
- Pythonga "men funksiya yaratyapman" deb xabar beradi
- Har doim funksiya boshida yoziladi
- Kichik harflarda bo'ladi

```python
def    # ✅ To'g'ri
DEF    # ❌ Noto'g'ri
Def    # ❌ Noto'g'ri
```

#### 2️⃣ Funksiya nomi

**Nomlash qoidalari:**

```python
# ✅ TO'G'RI nomlar
def hisoblash():
    pass

def malumot_olish():
    pass

def narx_hisobla_2024():
    pass

def _ichki_funksiya():  # Ichki funksiya uchun
    pass

# ❌ NOTO'G'RI nomlar
def 1_funksiya():  # Raqam bilan boshlanmaydi
    pass

def narx-hisobla():  # Defis ishlatilmaydi
    pass

def narx hisobla():  # Bo'sh joy bo'lmaydi
    pass

def if():  # Kalit so'zlar ishlatilmaydi
    pass
```

**Best practices:**

- Lotin harflari, raqamlar, pastki chiziq (_) ishlatiladi
- Kichik harflarda yoziladi
- So'zlar orasida pastki chiziq qo'yiladi (snake_case)
- Nom funksiyaning vazifasini bildirishi kerak
- Fe'l bilan boshlash yaxshi: `hisoblash`, `olish`, `yuborish`

#### 3️⃣ Qavslar `()`

```python
def salom():  # Bo'sh qavslar — parametrsiz funksiya
    print("Salom!")

def qoshish(a, b):  # Qavs ichida parametrlar
    return a + b
```

#### 4️⃣ Parametrlar

```python
def funksiya(parametr1, parametr2, parametr3):
    # parametrlar — funksiyaga beriladigan ma'lumotlar
    pass
```

**Parametr va argument farqi:**
- **Parametr** — funksiya e'lon qilinayotganda yoziladigan o'zgaruvchilar
- **Argument** — funksiya chaqirilayotganda beriladigan qiymatlar

```python
def salomlash(ism):  # "ism" — parametr
    print("Salom, " + ism)

salomlash("Ali")  # "Ali" — argument
```

#### 5️⃣ Ikki nuqta `:`

```python
def funksiya():  # : belgisi majburiy
    pass

def funksiya()   # ❌ Xato — : yo'q
    pass
```

**Vazifasi:** Funksiya sarlavhasi tugaganini va funksiya tanasi boshlanishini bildiradi.

#### 6️⃣ Funksiya tanasi (body)

```python
def hisoblash(a, b):
    # Bu joylar — funksiya tanasi
    natija = a + b
    print("Natija:", natija)
    return natija
```

**Qoidalar:**
- Funksiya tanasi **4 ta bo'sh joy** (yoki 1 tab) chekinitiriladi
- Bu joyda barcha kodlar yoziladi
- Kamida bitta qator bo'lishi kerak (bo'sh funksiya uchun `pass` yoziladi)

#### 7️⃣ Chekinish (Indentation)

```python
# ✅ TO'G'RI
def salom():
    print("Salom!")  # 4 ta bo'sh joy
    print("Dunyo!")  # 4 ta bo'sh joy

# ❌ NOTO'G'RI
def salom():
print("Salom!")  # Xato — chekinish yo'q
```

Python'da **chekinish (indentation)** — bu sintaksisning bir qismi. Boshqa tillarda `{}` ishlatilsa, Python'da bo'sh joylar ishlatiladi.

#### 8️⃣ `return`

```python
def qoshish(a, b):
    natija = a + b
    return natija  # Natijani qaytaradi
```

**Vazifasi:**
- Funksiya natijasini qaytaradi
- Funksiyani to'xtatadi
- `return` dan keyingi kodlar ishlamaydi

```python
def test():
    print("1")
    return "Tugadi"
    print("2")  # Bu qator HECH QACHON ishlamaydi!

print(test())  # Faqat "1" va "Tugadi" chiqadi
```

---

### To'liq sintaksis

```python
def talabaYoshi(tug_yil):  # def — funksiya, talabaYoshi — nom, tug_yil — parametr
    """
    Talabaning yoshini hisoblaydigan funksiya.
    
    Parametr:
        tug_yil (int): Talabaning tug'ilgan yili
    
    Qaytaradi:
        int: Talabaning yoshi
    """
    joriy_yil = 2024  # Joriy yilni o'zgaruvchiga saqlaymiz
    yosh = joriy_yil - tug_yil  # Yoshni hisoblaymiz
    return yosh  # Natijani qaytaramiz

# Funksiyani chaqirish
natija = talabaYoshi(2005)  # talabaYoshi funksiyasini chaqiramiz, 2005 — argument
print("Talaba yoshi:", natija)  # Natijani chiqaramiz
```

**Qatorma-qator tushuntirish:**

1. `def talabaYoshi(tug_yil):` — "talabaYoshi" nomli funksiya yaratdik, u bitta parametr qabul qiladi
2. `"""..."""` — Docstring, funksiya haqida ma'lumot
3. `joriy_yil = 2024` — Local o'zgaruvchi, funksiya ichida ishlaydi
4. `yosh = joriy_yil - tug_yil` — Yoshni hisoblash formulasi
5. `return yosh` — Natijani qaytarish, funksiya tugaydi
6. `natija = talabaYoshi(2005)` — Funksiyani chaqirish, natijani `natija` o'zgaruvchisiga saqlash
7. `print(...)` — Natijani ekranga chiqarish

**Expected output:**
```
Talaba yoshi: 19
```

---

## 3) Boshlang'ich funksiyalar — 5 ta sodda misol

### Misol 1: Salomlashish funksiyasi

```python
def salom():  # Parametrsiz funksiya
    """Oddiy salomlashish funksiyasi"""
    print("Assalomu alaykum!")  # Ekranga matn chiqaradi
    print("Xush kelibsiz!")

# Funksiyani chaqirish
salom()  # Funksiyani ishga tushiramiz
salom()  # Yana bir marta chaqiramiz
```

**Qatorma-qator tushuntirish:**
- **1-qator:** `def salom():` — "salom" nomli funksiya yaratdik, parametrlari yo'q (bo'sh qavslar)
- **3-qator:** `print("Assalomu alaykum!")` — Ekranga "Assalomu alaykum!" matnini chiqaradi
- **4-qator:** `print("Xush kelibsiz!")` — Ekranga "Xush kelibsiz!" matnini chiqaradi
- **7-qator:** `salom()` — Funksiyani birinchi marta chaqiramiz
- **8-qator:** `salom()` — Funksiyani ikkinchi marta chaqiramiz

**Expected output:**
```
Assalomu alaykum!
Xush kelibsiz!
Assalomu alaykum!
Xush kelibsiz!
```

**Keng tarqalgan xatolar:**

```python
# ❌ XATO 1: Qavslarni unutish
salom  # Bu funksiyani CHAQIRMAYDI, faqat funksiya obyektini ko'rsatadi

# ❌ XATO 2: Funksiyani e'lon qilmasdan chaqirish
salom()  # NameError — funksiya hali yaratilmagan

def salom():
    print("Salom")

# ❌ XATO 3: Chekinishni unutish
def salom():
print("Salom")  # IndentationError
```

---

### Misol 2: Ikkita sonni qo'shish

```python
def qoshish(son1, son2):  # Ikki parametrli funksiya
    """Ikki sonni qo'shadigan funksiya"""
    natija = son1 + son2  # Qo'shish amali
    return natija  # Natijani qaytarish

# Funksiyani chaqirish
javob = qoshish(10, 20)  # 10 va 20 ni qo'shadi
print("Natija:", javob)  # Natijani chiqaradi

# Boshqa qiymatlar bilan
javob2 = qoshish(100, 250)
print("Natija:", javob2)

# Bevosita chiqarish ham mumkin
print("Natija:", qoshish(5, 7))
```

**Qatorma-qator tushuntirish:**
- **1-qator:** `def qoshish(son1, son2):` — "qoshish" funksiyasi, ikki parametr: son1 va son2
- **3-qator:** `natija = son1 + son2` — son1 va son2 ni qo'shib, natija o'zgaruvchisiga saqlaymiz
- **4-qator:** `return natija` — Natijani qaytaramiz
- **7-qator:** `javob = qoshish(10, 20)` — Funksiyaga 10 va 20 beramiz, natijani javob o'zgaruvchisiga saqlaymiz
- **8-qator:** `print("Natija:", javob)` — javob o'zgaruvchisini ekranga chiqaramiz
- **14-qator:** `print("Natija:", qoshish(5, 7))` — Funksiyani bevosita print ichida chaqiramiz

**Expected output:**
```
Natija: 30
Natija: 350
Natija: 12
```

**Keng tarqalgan xatolar:**

```python
# ❌ XATO 1: return ni unutish
def qoshish(son1, son2):
    natija = son1 + son2
    # return yo'q

javob = qoshish(5, 10)
print(javob)  # None — natija qaytarilmagan

# ❌ XATO 2: Parametrlar sonini to'g'ri bermaslik
qoshish(5)  # TypeError — 2 ta parametr kerak, 1 ta berilgan
qoshish(5, 10, 15)  # TypeError — 2 ta parametr kerak, 3 ta berilgan

# ❌ XATO 3: Argumentlar turini adashtirish
qoshish("salom", "dunyo")  # "salomdunyo" — to'g'ri, lekin kutilmagan natija
```

---

### Misol 3: Ismni formatlash

```python
def ism_formatlash(ism, familiya):  # Ikki parametr
    """Ism va familiyani formatlaydi"""
    to_liq_ism = ism + " " + familiya  # Birlashtiramiz
    to_liq_ism = to_liq_ism.title()  # Har bir so'zning birinchi harfini katta qilamiz
    return to_liq_ism  # Natijani qaytaramiz

# Chaqirish
talaba = ism_formatlash("ali", "valiyev")
print(talaba)

# Boshqa misol
print(ism_formatlash("vali", "aliyev"))
print(ism_formatlash("HASAN", "HUSANOV"))
```

**Qatorma-qator tushuntirish:**
- **1-qator:** `def ism_formatlash(ism, familiya):` — Funksiya yaratamiz, 2 parametr
- **3-qator:** `to_liq_ism = ism + " " + familiya` — Ism va familiyani bo'sh joy bilan birlashtiramiz
- **4-qator:** `to_liq_ism = to_liq_ism.title()` — `.title()` metodi har bir so'zning birinchi harfini katta qiladi
- **5-qator:** `return to_liq_ism` — Natijani qaytaramiz
- **8-qator:** `talaba = ism_formatlash("ali", "valiyev")` — Funksiyani chaqiramiz, natijani saqlaimiz

**Expected output:**
```
Ali Valiyev
Vali Aliyev
Hasan Husanov
```

**Keng tarqalgan xatolar:**

```python
# ❌ XATO 1: Parametrlar tartibini adashtirish
def ism_formatlash(ism, familiya):
    return ism + " " + familiya

print(ism_formatlash("Valiyev", "Ali"))  # Noto'g'ri: "Valiyev Ali"

# ❌ XATO 2: String metodlarini noto'g'ri ishlatish
def ism_formatlash(ism, familiya):
    return ism.title + " " + familiya.title  # ❌ Qavslar yo'q
    # To'g'risi: ism.title() va familiya.title()

# ❌ XATO 3: Return qatoridan keyin kod yozish
def ism_formatlash(ism, familiya):
    return ism + " " + familiya
    print("Bu kod hech qachon ishlamaydi!")  # Dead code
```

---

### Misol 4: Kvadratini topish

```python
def kvadrat(son):  # Bitta parametr
    """Berilgan sonning kvadratini hisoblayd"""
    natija = son * son  # yoki son ** 2
    return natija

# Turli xil sonlarning kvadrati
print(kvadrat(5))     # 25
print(kvadrat(10))    # 100
print(kvadrat(2.5))   # 6.25
print(kvadrat(-3))    # 9

# O'zgaruvchida saqlash
raqam = 7
kvadrati = kvadrat(raqam)
print(f"{raqam} ning kvadrati: {kvadrati}")
```

**Qatorma-qator tushuntirish:**
- **1-qator:** `def kvadrat(son):` — Funksiya, bitta "son" parametri
- **3-qator:** `natija = son * son` — Sonni o'ziga ko'paytiramiz (kvadrat)
- **4-qator:** `return natija` — Natijani qaytaramiz
- **7-qator:** `print(kvadrat(5))` — 5 ning kvadratini hisoblaymiz va chiqaramiz
- **13-qator:** `kvadrati = kvadrat(raqam)` — Funksiya natijasini o'zgaruvchiga saqlaymiz

**Expected output:**
```
25
100
6.25
9
7 ning kvadrati: 49
```

**Keng tarqalgan xatolar:**

```python
# ❌ XATO 1: Mantiqiy xato
def kvadrat(son):
    return son * 2  # Bu kvadrat emas, 2 ga ko'paytirish!

# ❌ XATO 2: Natijani saqlamasdan ishlatish
def kvadrat(son):
    son * son  # return yo'q!
    
print(kvadrat(5))  # None

# ❌ XATO 3: Global o'zgaruvchini o'zgartirish
raqam = 10

def kvadrat(son):
    raqam = son * son  # Bu yangi local o'zgaruvchi
    return raqam

natija = kvadrat(5)
print(raqam)  # Hali ham 10, o'zgarmagan!
```

---

### Misol 5: Juft yoki toqligini aniqlash

```python
def juft_toq(son):  # Bitta parametr
    """Sonning juft yoki toq ekanini aniqlaydi"""
    if son % 2 == 0:  # Agar 2 ga qoldiqsiz bo'linsa
        return "Juft"  # "Juft" qaytaramiz
    else:  # Aks holda
        return "Toq"  # "Toq" qaytaramiz

# Turli sonlarni tekshirish
print(f"10 soni: {juft_toq(10)}")
print(f"7 soni: {juft_toq(7)}")
print(f"0 soni: {juft_toq(0)}")
print(f"-4 soni: {juft_toq(-4)}")

# Sikl bilan ishlatish
for i in range(1, 6):
    print(f"{i} - {juft_toq(i)}")
```

**Qatorma-qator tushuntirish:**
- **1-qator:** `def juft_toq(son):` — Funksiya yaratamiz
- **3-qator:** `if son % 2 == 0:` — `%` (modul) operatori qoldiqni beradi, agar qoldiq 0 bo'lsa — juft
- **4-qator:** `return "Juft"` — Agar shart to'g'ri bo'lsa, "Juft" qaytaramiz va funksiya tugaydi
- **5-qator:** `else:` — Agar shart noto'g'ri bo'lsa
- **6-qator:** `return "Toq"` — "Toq" qaytaramiz
- **9-qator:** `print(f"10 soni: {juft_toq(10)}")` — f-string formatida chiqaramiz

**Expected output:**
```
10 soni: Juft
7 soni: Toq
0 soni: Juft
-4 soni: Juft
1 - Toq
2 - Juft
3 - Toq
4 - Juft
5 - Toq
```

**Keng tarqalgan xatolar:**

```python
# ❌ XATO 1: Bir nechta return ni noto'g'ri ishlatish
def juft_toq(son):
    return "Juft"  # Har doim "Juft" qaytaradi!
    if son % 2 == 0:
        return "Juft"
    else:
        return "Toq"

# ❌ XATO 2: print va return ni adashtirish
def juft_toq(son):
    if son % 2 == 0:
        print("Juft")  # Print qiladi, lekin qaytarmaydi!
    else:
        print("Toq")

natija = juft_toq(10)
print(natija)  # None — funksiya hech narsa qaytarmagan

# ❌ XATO 3: Mantiqiy xato
def juft_toq(son):
    if son % 2 == 1:  # Faqat musbat toq sonlar uchun ishlaydi
        return "Toq"
    else:
        return "Juft"

print(juft_toq(-3))  # "Juft" — noto'g'ri! -3 toq son
```

---

## 4) Parametrlar va Argumentlar — to'liq tushuntirish

### Asosiy tushunchalar

**Parameter (Parametr)** — funksiya ta'rifida ko'rsatiladigan o'zgaruvchi:
```python
def salom(ism):  # "ism" — parametr
    print("Salom,", ism)
```

**Argument (Argument)** — funksiya chaqirilganda beriladigan qiymat:
```python
salom("Ali")  # "Ali" — argument
```

---

### 1️⃣ Oddiy parametrlar

```python
def talaba_malumoti(ism, yosh, fakultet):  # 3 ta parametr
    """Talaba haqida ma'lumot beradi"""
    print(f"Ism: {ism}")
    print(f"Yosh: {yosh}")
    print(f"Fakultet: {fakultet}")
    print("-" * 30)

# Chaqirish
talaba_malumoti("Ali", 20, "Informatika")
talaba_malumoti("Madina", 19, "Matematika")
```

**Expected output:**
```
Ism: Ali
Yosh: 20
Fakultet: Informatika
------------------------------
Ism: Madina
Yosh: 19
Fakultet: Matematika
------------------------------
```

---

### 2️⃣ Pozitsion argumentlar (Positional arguments)

Argumentlar **tartibi muhim**!

```python
def ayirish(a, b):  # Tartib: birinchi a, keyin b
    """a dan b ni ayiradi"""
    return a - b

print(ayirish(10, 3))   # 10 - 3 = 7
print(ayirish(3, 10))   # 3 - 10 = -7 (farq bor!)

# Bo'linish misoli
def bolish(surat, maxraj):
    """Surat ni maxraj ga bo'ladi"""
    return surat / maxraj

print(bolish(10, 2))   # 10 / 2 = 5.0
print(bolish(2, 10))   # 2 / 10 = 0.2 (juda farq qiladi!)
```

**Expected output:**
```
7
-7
5.0
0.2
```

**Qatorma-qator:**
- Pozitsion argumentlarda **tartib muhim**
- Birinchi argument — birinchi parametrga
- Ikkinchi argument — ikkinchi parametrga
- Va hokazo...

---

### 3️⃣ Kalit so'zli argumentlar (Keyword arguments)

Argumentlarni **nom bilan** beramiz, tartib muhim emas!

```python
def talaba_info(ism, yosh, kurs):
    """Talaba ma'lumotini ko'rsatadi"""
    print(f"{ism} - {yosh} yoshda, {kurs}-kurs")

# Keyword arguments — tartib muhim emas
talaba_info(ism="Ali", yosh=20, kurs=2)
talaba_info(yosh=19, kurs=1, ism="Madina")  # Boshqa tartibda, lekin to'g'ri!
talaba_info(kurs=3, ism="Vali", yosh=21)    # Yana boshqa tartib

# Aralashtirish ham mumkin (lekin pozitsion birinchi bo'lishi kerak)
talaba_info("Hasan", yosh=20, kurs=2)  # ✅ To'g'ri
# talaba_info(ism="Hasan", 20, 2)  # ❌ Xato — pozitsion keyword dan keyin bo'lmaydi
```

**Expected output:**
```
Ali - 20 yoshda, 2-kurs
Madina - 19 yoshda, 1-kurs
Vali - 21 yoshda, 3-kurs
Hasan - 20 yoshda, 2-kurs
```

**Afzalliklari:**
- Kod tushunarli
- Xatolarni kamaytiradi
- Tartib muhim emas
- O'qish oson

---

### 4️⃣ Default qiymatli parametrlar

Ba'zi parametrlarga **standart qiymat** beramiz:

```python
def salomlash(ism, til="O'zbek"):  # "til" default qiymatga ega
    """Turli tillarda salomlashadi"""
    if til == "O'zbek":
        print(f"Assalomu alaykum, {ism}!")
    elif til == "Ingliz":
        print(f"Hello, {ism}!")
    elif til == "Rus":
        print(f"Privet, {ism}!")
    else:
        print(f"Salom, {ism}!")

# Default qiymat ishlatiladi
salomlash("Ali")  # til="O'zbek" (default)

# O'z qiymatimizni beramiz
salomlash("John", "Ingliz")
salomlash("Ivan", "Rus")
salomlash("Akbar", "Tojik")
```

**Expected output:**
```
Assalomu alaykum, Ali!
Hello, John!
Privet, Ivan!
Salom, Akbar!
```

**Qoidalar:**
```python
# ✅ TO'G'RI — default parametrlar oxirida
def funksiya(a, b, c=10, d=20):
    pass

# ❌ NOTO'G'RI — default parametr boshida yoki o'rtada
def funksiya(a=10, b, c):  # SyntaxError
    pass
```

**Muhim misol — mutable default argument xavfi:**

```python
# ❌ XATO — ro'yxatni default qiymat qilish XAVFLI!
def qoshish(element, royxat=[]):  # Bu MUAMMO!
    royxat.append(element)
    return royxat

print(qoshish(1))  # [1]
print(qoshish(2))  # [1, 2] — Kutilmagan! [2] bo'lishi kerak edi!
print(qoshish(3))  # [1, 2, 3] — Xato davom etmoqda!

# ✅ TO'G'RI yechim — None ishlatish
def qoshish_tgri(element, royxat=None):
    if royxat is None:  # Agar ro'yxat berilmagan bo'lsa
        royxat = []  # Yangi ro'yxat yaratamiz
    royxat.append(element)
    return royxat

print(qoshish_tgri(1))  # [1]
print(qoshish_tgri(2))  # [2] — To'g'ri!
print(qoshish_tgri(3))  # [3] — To'g'ri!
```

---

### 5️⃣ *args — Cheksiz pozitsion argumentlar

`*args` yordamida **istalgan miqdorda** pozitsion argument qabul qilish mumkin:

```python
def yigindi(*sonlar):  # *args — tuple qaytaradi
    """Barcha sonlarning yig'indisini hisoblayd"""
    print(f"Sonlar: {sonlar}")  # Tuple ko'rinishida
    print(f"Turi: {type(sonlar)}")
    
    jami = 0
    for son in sonlar:  # Tuple ustida sikl
        jami += son
    return jami

# Turli miqdorda argumentlar
print(yigindi(1, 2, 3))           # 3 ta argument
print(yigindi(10, 20, 30, 40))    # 4 ta argument
print(yigindi(5))                  # 1 ta argument
print(yigindi(1, 2, 3, 4, 5, 6, 7, 8, 9, 10))  # 10 ta argument
```

**Expected output:**
```
Sonlar: (1, 2, 3)
Turi: <class 'tuple'>
6
Sonlar: (10, 20, 30, 40)
Turi: <class 'tuple'>
100
Sonlar: (5,)
Turi: <class 'tuple'>
5
Sonlar: (1, 2, 3, 4, 5, 6, 7, 8, 9, 10)
Turi: <class 'tuple'>
55
```

**Qatorma-qator tushuntirish:**
- `*sonlar` — barcha pozitsion argumentlarni **tuple** ga yig'adi
- `sonlar` o'zgaruvchisi ichida tuple mavjud
- Tuple ustida sikl ishlatib, elementlarni bitta-bitta olish mumkin

**Ikkinchi misol:**

```python
def malumot(ism, *oquvlar):  # Birinchi parametr oddiy, qolganlari *args
    """Talabaning barcha o'quv fanlarini ko'rsatadi"""
    print(f"Talaba: {ism}")
    print("O'quv fanlari:")
    for fan in oquvlar:
        print(f"  - {fan}")

malumot("Ali", "Matematika", "Fizika", "Informatika")
malumot("Madina", "Ona tili", "Ingliz tili")
```

**Expected output:**
```
Talaba: Ali
O'quv fanlari:
  - Matematika
  - Fizika
  - Informatika
Talaba: Madina
O'quv fanlari:
  - Ona tili
  - Ingliz tili
```

---

### 6️⃣ **kwargs — Cheksiz kalit so'zli argumentlar

`**kwargs` yordamida **istalgan miqdorda** keyword argument qabul qilish mumkin:

```python
def talaba(**malumotlar):  # **kwargs — dictionary qaytaradi
    """Talaba haqida barcha ma'lumotlarni ko'rsatadi"""
    print(f"Ma'lumotlar: {malumotlar}")
    print(f"Turi: {type(malumotlar)}")
    print("\nTalaba to'liq ma'lumoti:")
    
    for kalit, qiymat in malumotlar.items():  # Dictionary ustida sikl
        print(f"  {kalit}: {qiymat}")

# Turli xil keyword argumentlar
talaba(ism="Ali", yosh=20, fakultet="IT", kurs=2)
print("\n" + "="*40 + "\n")
talaba(ism="Madina", yosh=19, manzil="Toshkent", telefon="+998901234567")
```

**Expected output:**
```
Ma'lumotlar: {'ism': 'Ali', 'yosh': 20, 'fakultet': 'IT', 'kurs': 2}
Turi: <class 'dict'>

Talaba to'liq ma'lumoti:
  ism: Ali
  yosh: 20
  fakultet: IT
  kurs: 2

========================================

Ma'lumotlar: {'ism': 'Madina', 'yosh': 19, 'manzil': 'Toshkent', 'telefon': '+998901234567'}
Turi: <class 'dict'>

Talaba to'liq ma'lumoti:
  ism: Madina
  yosh: 19
  manzil: Toshkent
  telefon: +998901234567
```

**Qatorma-qator tushuntirish:**
- `**malumotlar` — barcha keyword argumentlarni **dictionary** ga yig'adi
- Key — parametr nomi, Value — argument qiymati
- `.items()` metodi bilan key va value larni ajratib olamiz

---

### 7️⃣ *args va **kwargs ni birga ishlatish

Barcha argumentlar turlarini bitta funksiyada ishlatish mumkin:

```python
def universal(majburiy, default="standart", *args, **kwargs):
    """Barcha argument turlarini qabul qiladi"""
    print(f"Majburiy parametr: {majburiy}")
    print(f"Default parametr: {default}")
    print(f"Args (tuple): {args}")
    print(f"Kwargs (dict): {kwargs}")
    print("-" * 50)

# Turli xil chaqirish usullari
universal("Salom")
universal("Hello", "Custom")
universal("Hi", "Test", 1, 2, 3)
universal("Privet", "Rus", 10, 20, ism="Ali", yosh=20)
```

**Expected output:**
```
Majburiy parametr: Salom
Default parametr: standart
Args (tuple): ()
Kwargs (dict): {}
--------------------------------------------------
Majburiy parametr: Hello
Default parametr: Custom
Args (tuple): ()
Kwargs (dict): {}
--------------------------------------------------
Majburiy parametr: Hi
Default parametr: Test
Args (tuple): (1, 2, 3)
Kwargs (dict): {}
--------------------------------------------------
Majburiy parametr: Privet
Default parametr: Rus
Args (tuple): (10, 20)
Kwargs (dict): {'ism': 'Ali', 'yosh': 20}
--------------------------------------------------
```

**Muhim qoida — parametrlar tartibi:**
```python
def funksiya(
    oddiy_param,           # 1. Oddiy parametrlar
    default_param=10,      # 2. Default parametrlar
    *args,                 # 3. *args
    **kwargs               # 4. **kwargs
):
    pass
```

---

## 5) return — chuqur tushuntirish

### return nima?

`return` — funksiyaning natijasini qaytarish va funksiyani to'xtatish uchun ishlatiladi.

### 🔍 return qanday ishlaydi?

```python
def kvadrat(son):
    print("Hisoblash boshlandi")  # Birinchi bu ishlayd
    natija = son ** 2
    print("Hisoblash tugadi")      # Keyin bu ishlaydi
    return natija                  # Natija qaytariladi va funksiya tugaydi
    print("Bu qator hech qachon ishlamaydi!")  # Dead code

javob = kvadrat(5)
print("Javob:", javob)
```

**Expected output:**
```
Hisoblash boshlandi
Hisoblash tugadi
Javob: 25
```

---

### ❌ return bo'lmasa nima bo'ladi?

Agar funksiyada `return` bo'lmasa, funksiya **None** qaytaradi:

```python
def salom(ism):
    print(f"Salom, {ism}!")
    # return yo'q

natija = salom("Ali")
print("Natija:", natija)  # None
print("Turi:", type(natija))  # <class 'NoneType'>
```

**Expected output:**
```
Salom, Ali!
Natija: None
Turi: <class 'NoneType'>
```

**None** — bu Python'da "hech narsa yo'q" ni bildiradi.

---

### print va return farqi

| # | `print` | `return` |
|---|---------|----------|
| **1. Vazifa** | Ekranga chiqaradi | Qiymat qaytaradi |
| **2. Natija** | Hech narsa qaytarmaydi (None) | Funksiya natijasini qaytaradi |
| **3. Funksiya davomi** | Funksiya davom etadi | Funksiya to'xtaydi |
| **4. Qayta ishlatish** | Natijani saqlab bo'lmaydi | Natijani o'zgaruvchida saqlash mumkin |
| **5. Matematik amallar** | Natija ustida amal bajarib bo'lmaydi | Natija ustida amal bajarish mumkin |
| **6. Funksiya ichida nechta?** | Ko'p marta ishlatish mumkin | Bir marta (birinchi return ishlaydi) |
| **7. Qachon ishlatiladi?** | Axborot ko'rsatish uchun | Natija qaytarish uchun |
| **8. Funksiyalarni zanjirlash** | Mumkin emas | Mumkin (bir funksiyaning natijasini boshqasiga berish) |

**Misollar:**

```python
# 1. print — faqat ekranga chiqaradi
def qoshish_print(a, b):
    print(a + b)  # Ekranga chiqaradi
    # return yo'q

natija1 = qoshish_print(5, 3)  # Ekranga: 8
print("Natija:", natija1)      # None

# 2. return — qiymat qaytaradi
def qoshish_return(a, b):
    return a + b  # Qiymat qaytaradi

natija2 = qoshish_return(5, 3)
print("Natija:", natija2)  # 8

# 3. Farqni ko'rsatish
def test_print(x):
    print(x * 2)

def test_return(x):
    return x * 2

# print bilan
a = test_print(10)  # Ekranga: 20
print(a + 5)  # TypeError — None + 5 bo'lmaydi!

# return bilan
b = test_return(10)
print(b + 5)  # 25 — to'g'ri ishladi
```

---

### 🔢 Bir nechta return ishlatish

Funksiyada bir nechta `return` bo'lishi mumkin, lekin **faqat birinchisi** ishlaydi:

```python
def bahoni_aniqlash(ball):
    """Ballga ko'ra bahoni aniqlaydi"""
    if ball >= 90:
        return "A'lo"  # Agar bu ishlasa, funksiya to'xtaydi
    elif ball >= 80:
        return "Yaxshi"  # Yoki bu
    elif ball >= 70:
        return "Qoniqarli"  # Yoki bu
    else:
        return "Qoniqarsiz"  # Yoki bu
    
    print("Bu qator hech qachon ishlamaydi!")

print(bahoni_aniqlash(95))  # A'lo
print(bahoni_aniqlash(75))  # Qoniqarli
print(bahoni_aniqlash(65))  # Qoniqarsiz
```

**Expected output:**
```
A'lo
Qoniqarli
Qoniqarsiz
```

---

### 🔴 return dan keyingi kod ishlaydimi?

**YO'Q!** return dan keyingi barcha kodlar **dead code** (o'lik kod) hisoblanadi:

```python
def test():
    print("1 - Bu ishlaydi")
    print("2 - Bu ham ishlaydi")
    return "Tugadi"
    print("3 - Bu HECH QACHON ishlamaydi!")
    print("4 - Bu ham ishlamaydi!")
    return "Bu return ham hech qachon ishlamaydi"

natija = test()
print("Natija:", natija)
```

**Expected output:**
```
1 - Bu ishlaydi
2 - Bu ham ishlaydi
Natija: Tugadi
```

---

### return qayerda bo'lishi kerak?

`return` funksiyaning **istalgan joyida** bo'lishi mumkin, lekin odatda **oxirida**:

```python
def tub_son_tekshir(son):
    """Sonning tub yoki tub emasligini aniqlaydi"""
    
    # 1 dan kichik sonlar tub emas
    if son < 2:
        return False  # Darhol to'xtatamiz
    
    # 2 tub son
    if son == 2:
        return True  # Darhol to'xtatamiz
    
    # Juft sonlar (2 dan tashqari) tub emas
    if son % 2 == 0:
        return False  # Darhol to'xtatamiz
    
    # 3 dan boshlab toq bo'luvchilarni tekshiramiz
    for i in range(3, int(son**0.5) + 1, 2):
        if son % i == 0:
            return False  # Bo'luvchi topildi — tub emas
    
    # Hech qanday bo'luvchi topilmadi — tub son
    return True

print(tub_son_tekshir(17))  # True
print(tub_son_tekshir(20))  # False
```

---

### Bir nechta qiymatni qaytarish

Python'da **tuple** yordamida bir nechta qiymat qaytarish mumkin:

```python
def bolish_va_qoldiq(a, b):
    """Bo'lish va qoldiqni qaytaradi"""
    bolinma = a // b  # Butun qismi
    qoldiq = a % b    # Qoldiq
    return bolinma, qoldiq  # Ikki qiymat — tuple bo'lib qaytadi

# Tuple qaytaradi
natija = bolish_va_qoldiq(17, 5)
print(natija)  # (3, 2)
print(type(natija))  # <class 'tuple'>

# Yoki qiymatlarni alohida o'zgaruvchilarga ajratamiz
b, q = bolish_va_qoldiq(17, 5)
print(f"Bo'linma: {b}, Qoldiq: {q}")
```

**Expected output:**
```
(3, 2)
<class 'tuple'>
Bo'linma: 3, Qoldiq: 2
```

---

## 6) Funksiyalardan funksiyani chaqirish

### Funksiya ichida boshqa funksiya chaqirish

```python
def salom():
    """Salomlashadi"""
    print("Salom!")

def xayrlash():
    """Xayrlashadi"""
    print("Xayr!")

def uchrashuv():
    """To'liq uchrashuvni boshqaradi"""
    salom()  # Birinchi funksiya
    print("Qanday ahvolingiz?")
    print("Yaxshi, rahmat!")
    xayrlash()  # Ikkinchi funksiya

# Chaqirish
uchrashuv()
```

**Expected output:**
```
Salom!
Qanday ahvolingiz?
Yaxshi, rahmat!
Xayr!
```

**Qatorma-qator:**
- `uchrashuv()` funksiyasi chaqiriladi
- `uchrashuv()` ichida `salom()` chaqiriladi
- `salom()` bajariladi va tugaydi
- `uchrashuv()` davom etadi
- `xayrlash()` chaqiriladi
- `xayrlash()` bajariladi va tugaydi
- `uchrashuv()` tugaydi

---

### 🔗 3 bosqichli funksiya zanjiri

```python
def harf_baho(ball):
    """Ballni harf bahoga o'giradi"""
    if ball >= 90:
        return "A"
    elif ball >= 80:
        return "B"
    elif ball >= 70:
        return "C"
    else:
        return "F"

def baho_tavsifi(harf):
    """Harf bahoning tavsifini beradi"""
    if harf == "A":
        return "A'lo"
    elif harf == "B":
        return "Yaxshi"
    elif harf == "C":
        return "Qoniqarli"
    else:
        return "Qoniqarsiz"

def toliq_natija(ball):
    """To'liq natijani ko'rsatadi"""
    harf = harf_baho(ball)  # Birinchi funksiya
    tavsif = baho_tavsifi(harf)  # Ikkinchi funksiya
    return f"Ball: {ball}, Baho: {harf}, Tavsif: {tavsif}"

# Zanjirli chaqirish
print(toliq_natija(95))
print(toliq_natija(82))
print(toliq_natija(65))
```

**Expected output:**
```
Ball: 95, Baho: A, Tavsif: A'lo
Ball: 82, Baho: B, Tavsif: Yaxshi
Ball: 65, Baho: F, Tavsif: Qoniqarsiz
```

**Zanjirlash tartibi:**
```
toliq_natija(95)
    → harf_baho(95)
        → return "A"
    → baho_tavsifi("A")
        → return "A'lo"
    → return "Ball: 95, Baho: A, Tavsif: A'lo"
```

---

### 📚 Call Stack (Chaqiruvlar to'plami)

**Call Stack** — bu funksiyalar chaqirilish tartibini saqlovchi xotira strukturasi.

```python
def A():
    print("A boshlandi")
    B()  # B ni chaqiradi
    print("A tugadi")

def B():
    print("  B boshlandi")
    C()  # C ni chaqiradi
    print("  B tugadi")

def C():
    print("    C ishlamoqda")

A()  # Boshlanish nuqtasi
```

**Expected output:**
```
A boshlandi
  B boshlandi
    C ishlamoqda
  B tugadi
A tugadi
```

**Call Stack visualizatsiyasi:**

```
1. A() chaqiriladi
   Stack: [A]

2. A() ichida B() chaqiriladi
   Stack: [A, B]

3. B() ichida C() chaqiriladi
   Stack: [A, B, C]

4. C() tugaydi va stackdan chiqadi
   Stack: [A, B]

5. B() tugaydi va stackdan chiqadi
   Stack: [A]

6. A() tugaydi va stackdan chiqadi
   Stack: []
```

**Chizma:**
```
             ┌───────┐
             │   C   │  ← Eng yuqori (oxirgi chaqirilgan)
             ├───────┤
             │   B   │
             ├───────┤
             │   A   │  ← Eng past (birinchi chaqirilgan)
             └───────┘
               Stack
```

---

## 7) Local va Global o'zgaruvchilar

### 🌍 Global scope (Global doira)

**Global o'zgaruvchi** — dasturning asosiy qismida (funksiyalardan tashqarida) e'lon qilingan o'zgaruvchi:

```python
ism = "Ali"  # Global o'zgaruvchi

def salom():
    print("Salom, " + ism)  # Global o'zgaruvchini o'qish mumkin

salom()  # Salom, Ali
print(ism)  # Ali
```

---

### 🏠 Local scope (Local doira)

**Local o'zgaruvchi** — funksiya ichida e'lon qilingan o'zgaruvchi:

```python
def test():
    yosh = 20  # Local o'zgaruvchi
    print("Ichkarida:", yosh)

test()  # Ichkarida: 20
# print(yosh)  # ❌ NameError — yosh faqat funksiya ichida mavjud
```

---

### 🔄 Global va local o'zgaruvchilarni birga ishlatish

```python
ism = "Ali"  # Global

def test():
    yosh = 20  # Local
    print(f"Ism: {ism}")  # Global o'zgaruvchini o'qish
    print(f"Yosh: {yosh}")  # Local o'zgaruvchini o'qish

test()
print(f"Tashqarida ism: {ism}")  # Global o'zgaruvchi mavjud
# print(f"Tashqarida yosh: {yosh}")  # ❌ Xato — local o'zgaruvchi yo'q
```

**Expected output:**
```
Ism: Ali
Yosh: 20
Tashqarida ism: Ali
```

---

### ⚠️ Shadowing (Soyalash)

Agar funksiya ichida global o'zgaruvchi bilan bir xil nomli local o'zgaruvchi yaratilsa:

```python
son = 100  # Global

def test():
    son = 50  # Yangi LOCAL o'zgaruvchi (global emas!)
    print("Ichkarida:", son)  # 50

test()
print("Tashqarida:", son)  # 100 — global o'zgarmagan!
```

**Expected output:**
```
Ichkarida: 50
Tashqarida: 100
```

**Tushuntirish:**
- Funksiya ichidagi `son = 50` — bu **yangi local** o'zgaruvchi
- Global `son` o'zgarmaydi
- Funksiya ichida local `son` ishlatiladi

---

### 🌐 `global` kalit so'zi

Agar funksiya ichida global o'zgaruvchini **o'zgartirish** kerak bo'lsa, `global` kalit so'zini ishlatish kerak:

```python
hisob = 0  # Global o'zgaruvchi

def oshir():
    global hisob  # Global o'zgaruvchini o'zgartiraman deb e'lon qilamiz
    hisob += 1  # Endi global o'zgaruvchini o'zgartiramiz
    print("Ichkarida:", hisob)

print("Boshlash:", hisob)  # 0
oshir()  # 1
oshir()  # 2
oshir()  # 3
print("Yakuniy:", hisob)  # 3 — global o'zgaruvchi o'zgardi!
```

**Expected output:**
```
Boshlash: 0
Ichkarida: 1
Ichkarida: 2
Ichkarida: 3
Yakuniy: 3
```

---

### ❌ global kalit so'zisiz xato

```python
hisob = 0

def oshir():
    hisob += 1  # ❌ UnboundLocalError
    # Python chalkashib qoladi: hisob local mi yoki global mi?

oshir()
```

**Xato sababi:**
- Python `hisob += 1` ni ko'rganda, `hisob` ni local o'zgaruvchi deb o'ylaydi
- Lekin `hisob` hali yaratilmagan
- Xato chiqadi: "local variable 'hisob' referenced before assignment"

---

### 🛡️ Xavfsizlik bo'yicha eslatmalar

1. **Global o'zgaruvchilarni kam ishlatish** — kod chalkashadi
2. **Funksiyalar o'z local o'zgaruvchilariga ega bo'lishi kerak** — mustaqillik
3. **Global o'zgaruvchilarni o'zgartirish xavfli** — kutilmagan xatolar
4. **Parametrlar orqali ma'lumot uzatish yaxshiroq** — aniqroq

```python
# ❌ YOMON — global o'zgaruvchiga bog'liq
hisob = 0

def oshir():
    global hisob
    hisob += 1
    return hisob

# ✅ YAXSHI — parametr orqali ma'lumot uzatish
def oshir(hisob):
    return hisob + 1

hisob = 0
hisob = oshir(hisob)  # Aniq va xavfsiz
```

---

## 8) Lambda funksiyalar — to'liq dars

### 📖 Lambda nima?

**Lambda** — bu **bir qatorli, nomsiz (anonim) funksiya**.

**Sintaksis:**
```python
lambda parametrlar: ifoda
```

**Oddiy funksiya:**
```python
def kvadrat(x):
    return x ** 2

print(kvadrat(5))  # 25
```

**Lambda bilan:**
```python
kvadrat = lambda x: x ** 2
print(kvadrat(5))  # 25
```

---

### 🔍 Lambda sintaksisini tushunish

```python
# Lambda strukturasi:
kvadrat = lambda x: x ** 2
#         │     │  │
#         │     │  └─ Ifoda (natija)
#         │     └─ Parametr
#         └─ Lambda kalit so'zi
```

**Qatorma-qator:**
- `lambda` — lambda funksiya yaratish uchun kalit so'z
- `x` — parametr (bir yoki bir nechta bo'lishi mumkin)
- `:` — parametr va ifodani ajratuvchi
- `x ** 2` — natija (ifoda)
- `return` yo'q — avtomatik qaytariladi

---

### 📝 Oddiy misollar

**1-misol: Sonni ikkilash**

```python
# Oddiy funksiya
def ikkilash(x):
    return x * 2

# Lambda
ikkilash = lambda x: x * 2

print(ikkilash(5))   # 10
print(ikkilash(100)) # 200
```

**2-misol: Ikki sonni qo'shish**

```python
# Lambda bir nechta parametr bilan
qoshish = lambda a, b: a + b

print(qoshish(10, 20))  # 30
print(qoshish(5, 7))    # 12
```

**3-misol: Shartli operator bilan**

```python
# Maksimumni topish
maksimum = lambda a, b: a if a > b else b

print(maksimum(10, 20))  # 20
print(maksimum(50, 30))  # 50
```

---

### 🔧 Lambda + filter()

`filter()` — ro'yxatdan shartga mos elementlarni saralaydi.

```python
sonlar = [1, 2, 3, 4, 5, 6, 7, 8, 9, 10]

# Juft sonlarni filterlash
juftlar = list(filter(lambda x: x % 2 == 0, sonlar))
print("Juft sonlar:", juftlar)

# 5 dan katta sonlar
kattalar = list(filter(lambda x: x > 5, sonlar))
print("5 dan kattalar:", kattalar)

# Toq sonlar
toqlar = list(filter(lambda x: x % 2 != 0, sonlar))
print("Toq sonlar:", toqlar)
```

**Expected output:**
```
Juft sonlar: [2, 4, 6, 8, 10]
5 dan kattalar: [6, 7, 8, 9, 10]
Toq sonlar: [1, 3, 5, 7, 9]
```

**Qatorma-qator tushuntirish:**
- `filter(funksiya, ro'yxat)` — ro'yxatdagi har bir elementni funksiyadan o'tkazadi
- Agar funksiya `True` qaytarsa — element saqlanadi
- Agar funksiya `False` qaytarsa — element o'chiriladi
- `list()` — natijani ro'yxatga aylantiradi

---

### 🗺️ Lambda + map()

`map()` — ro'yxatdagi har bir elementga funksiya qo'llaydi.

```python
sonlar = [1, 2, 3, 4, 5]

# Har bir sonni kvadratga ko'tarish
kvadratlar = list(map(lambda x: x ** 2, sonlar))
print("Kvadratlar:", kvadratlar)

# Har bir sonni 10 ga ko'paytirish
kopaytma = list(map(lambda x: x * 10, sonlar))
print("10 ga ko'paytma:", kopaytma)

# Har bir sonni stringga aylantirish
stringlar = list(map(lambda x: str(x), sonlar))
print("Stringlar:", stringlar)
print("Turi:", type(stringlar[0]))
```

**Expected output:**
```
Kvadratlar: [1, 4, 9, 16, 25]
10 ga ko'paytma: [10, 20, 30, 40, 50]
Stringlar: ['1', '2', '3', '4', '5']
Turi: <class 'str'>
```

**Ikki ro'yxat ustida map:**

```python
sonlar1 = [1, 2, 3, 4, 5]
sonlar2 = [10, 20, 30, 40, 50]

# Ikkala ro'yxatni qo'shish
yigindi = list(map(lambda x, y: x + y, sonlar1, sonlar2))
print("Yig'indi:", yigindi)

# Ko'paytirish
kopaytma = list(map(lambda x, y: x * y, sonlar1, sonlar2))
print("Ko'paytma:", kopaytma)
```

**Expected output:**
```
Yig'indi: [11, 22, 33, 44, 55]
Ko'paytma: [10, 40, 90, 160, 250]
```

---

### 📊 Lambda + sorted()

`sorted()` — ro'yxatni tartiblaydi, lambda bilan maxsus tartib qo'yish mumkin.

```python
talabalar = [
    {"ism": "Ali", "yosh": 20, "ball": 85},
    {"ism": "Vali", "yosh": 19, "ball": 92},
    {"ism": "Madina", "yosh": 21, "ball": 78},
    {"ism": "Hasan", "yosh": 20, "ball": 95}
]

# Yosh bo'yicha tartiblash
yosh_tartib = sorted(talabalar, key=lambda t: t["yosh"])
print("Yosh bo'yicha:")
for t in yosh_tartib:
    print(f"  {t['ism']} - {t['yosh']} yosh")

print()

# Ball bo'yicha tartiblash (kamayish tartibida)
ball_tartib = sorted(talabalar, key=lambda t: t["ball"], reverse=True)
print("Ball bo'yicha (yuqoridan pastga):")
for t in ball_tartib:
    print(f"  {t['ism']} - {t['ball']} ball")
```

**Expected output:**
```
Yosh bo'yicha:
  Vali - 19 yosh
  Ali - 20 yosh
  Hasan - 20 yosh
  Madina - 21 yosh

Ball bo'yicha (yuqoridan pastga):
  Hasan - 95 ball
  Vali - 92 ball
  Ali - 85 ball
  Madina - 78 ball
```

---

### Murakkab misol — Lambda bilan ma'lumot tahlili

```python
mahsulotlar = [
    {"nom": "Telefon", "narx": 500, "soni": 10, "chegirma": 0.1},
    {"nom": "Noutbuk", "narx": 1000, "soni": 5, "chegirma": 0.15},
    {"nom": "Planshet", "narx": 300, "soni": 15, "chegirma": 0.05},
    {"nom": "Monitor", "narx": 200, "soni": 20, "chegirma": 0.2}
]

# 1. Narxi 400 dan yuqori mahsulotlarni filterlash
qimmat = list(filter(lambda m: m["narx"] > 400, mahsulotlar))
print("Narxi 400$ dan yuqori:")
for m in qimmat:
    print(f"  {m['nom']} - ${m['narx']}")

print()

# 2. Har bir mahsulot uchun umumiy qiymatni hisoblash (narx * soni)
umumiy = list(map(lambda m: {
    "nom": m["nom"],
    "umumiy_qiymat": m["narx"] * m["soni"]
}, mahsulotlar))

print("Umumiy qiymatlar:")
for m in umumiy:
    print(f"  {m['nom']} - ${m['umumiy_qiymat']}")

print()

# 3. Chegirma qo'llangandan keyingi narx
chegirmali = list(map(lambda m: {
    "nom": m["nom"],
    "asl_narx": m["narx"],
    "chegirmali_narx": m["narx"] * (1 - m["chegirma"])
}, mahsulotlar))

print("Chegirmadan keyingi narxlar:")
for m in chegirmali:
    print(f"  {m['nom']}: ${m['asl_narx']} → ${m['chegirmali_narx']:.2f}")

print()

# 4. Eng qimmat mahsulotni topish
eng_qimmat = max(mahsulotlar, key=lambda m: m["narx"])
print(f"Eng qimmat: {eng_qimmat['nom']} - ${eng_qimmat['narx']}")

# 5. Eng ko'p sotilgan mahsulot (soni bo'yicha)
eng_kop = max(mahsulotlar, key=lambda m: m["soni"])
print(f"Eng ko'p sotilgan: {eng_kop['nom']} - {eng_kop['soni']} dona")
```

**Expected output:**
```
Narxi 400$ dan yuqori:
  Telefon - $500
  Noutbuk - $1000

Umumiy qiymatlar:
  Telefon - $5000
  Noutbuk - $5000
  Planshet - $4500
  Monitor - $4000

Chegirmadan keyingi narxlar:
  Telefon: $500 → $450.00
  Noutbuk: $1000 → $850.00
  Planshet: $300 → $285.00
  Monitor: $200 → $160.00

Eng qimmat: Noutbuk - $1000
Eng ko'p sotilgan: Monitor - 20 dona
```

---

## 9) Rekursiya (Recursion) — chuqur tushuntirish

### 📖 Rekursiya nima?

**Rekursiya** — funksiyaning o'zini chaqirishidir.

**Hayotiy misol: Oynadagi aks sado**

Agar ikki parallel oyna orasida tursangiz, oynadagi aks sado cheksiz ko'payadi. Har bir aks sado — oldingi aks sadoning aksidir.

```
Siz → Oyna 1 → Oyna 2 → Oyna 1 → Oyna 2 → ...
```

### Rekursiyaning 2 qismi

Har bir rekursiv funksiyada **2 ta muhim qism** bo'lishi kerak:

1. **Base case (Asosiy holat)** — rekursiya to'xtash sharti
2. **Recursive case (Rekursiv holat)** — funksiyaning o'zini chaqirish

```python
def rekursiv_funksiya(n):
    if n == 0:  # BASE CASE — to'xtash sharti
        return
    
    print(n)
    rekursiv_funksiya(n - 1)  # RECURSIVE CASE — o'zini chaqirish
```

---

### 🔢 Misol 1: Faktorial (n!)

**Faktorial** — barcha sonlarni ko'paytirish:
```
5! = 5 × 4 × 3 × 2 × 1 = 120
```

**Rekursiv yechim:**

```python
def faktorial(n):
    """Faktorialni rekursiv usulda hisoblaydi"""
    
    # BASE CASE — to'xtash sharti
    if n == 0 or n == 1:
        return 1  # 0! = 1, 1! = 1
    
    # RECURSIVE CASE — o'zini chaqirish
    return n * faktorial(n - 1)

# Sinovlar
print(f"5! = {faktorial(5)}")   # 120
print(f"10! = {faktorial(10)}") # 3628800
print(f"0! = {faktorial(0)}")   # 1
```

**Expected output:**
```
5! = 120
10! = 3628800
0! = 1
```

**Qatorma-qator tahlil (5! uchun):**

```
faktorial(5)
    → 5 * faktorial(4)
        → 4 * faktorial(3)
            → 3 * faktorial(2)
                → 2 * faktorial(1)
                    → 1 (BASE CASE)
                → 2 * 1 = 2
            → 3 * 2 = 6
        → 4 * 6 = 24
    → 5 * 24 = 120
```

**Call Stack:**

```
Step 1: faktorial(5) chaqirildi
Stack: [faktorial(5)]

Step 2: faktorial(4) chaqirildi
Stack: [faktorial(5), faktorial(4)]

Step 3: faktorial(3) chaqirildi
Stack: [faktorial(5), faktorial(4), faktorial(3)]

Step 4: faktorial(2) chaqirildi
Stack: [faktorial(5), faktorial(4), faktorial(3), faktorial(2)]

Step 5: faktorial(1) chaqirildi
Stack: [faktorial(5), faktorial(4), faktorial(3), faktorial(2), faktorial(1)]

Step 6: faktorial(1) = 1 qaytardi (BASE CASE)
Stack: [faktorial(5), faktorial(4), faktorial(3), faktorial(2)]

Step 7: faktorial(2) = 2 * 1 = 2
Stack: [faktorial(5), faktorial(4), faktorial(3)]

Step 8: faktorial(3) = 3 * 2 = 6
Stack: [faktorial(5), faktorial(4)]

Step 9: faktorial(4) = 4 * 6 = 24
Stack: [faktorial(5)]

Step 10: faktorial(5) = 5 * 24 = 120
Stack: []
```

---

### 🐰 Misol 2: Fibonacci ketma-ketligi

**Fibonacci** — har bir son oldingi ikki sonning yig'indisi:
```
0, 1, 1, 2, 3, 5, 8, 13, 21, ...
```

```python
def fibonacci(n):
    """n-chi Fibonacci sonini topadi"""
    
    # BASE CASES
    if n == 0:
        return 0  # fib(0) = 0
    if n == 1:
        return 1  # fib(1) = 1
    
    # RECURSIVE CASE
    return fibonacci(n - 1) + fibonacci(n - 2)

# Sinovlar
for i in range(10):
    print(f"fib({i}) = {fibonacci(i)}")
```

**Expected output:**
```
fib(0) = 0
fib(1) = 1
fib(2) = 1
fib(3) = 2
fib(4) = 3
fib(5) = 5
fib(6) = 8
fib(7) = 13
fib(8) = 21
fib(9) = 34
```

**Rekursiya daraxti (fibonacci(5) uchun):**

```
                    fib(5)
                   /      \
              fib(4)      fib(3)
             /    \       /    \
        fib(3)  fib(2) fib(2) fib(1)
       /   \    /   \   /   \
   fib(2) fib(1) fib(1) fib(0) fib(1) fib(0)
   /   \
fib(1) fib(0)
```

**Hisoblash jarayoni:**
```
fib(5) = fib(4) + fib(3)
       = (fib(3) + fib(2)) + (fib(2) + fib(1))
       = ((fib(2) + fib(1)) + (fib(1) + fib(0))) + ((fib(1) + fib(0)) + 1)
       = (((1 + 0) + 1) + (1 + 0)) + ((1 + 0) + 1)
       = (1 + 1 + 1) + (1 + 1)
       = 3 + 2
       = 5
```

---

### ➕ Misol 3: Sonlar yig'indisi

1 dan n gacha bo'lgan barcha sonlarning yig'indisini topish:

```python
def yigindi(n):
    """1 dan n gacha bo'lgan sonlarning yig'indisi"""
    
    # BASE CASE
    if n == 1:
        return 1
    
    # RECURSIVE CASE
    return n + yigindi(n - 1)

# Sinovlar
print(f"1 dan 5 gacha: {yigindi(5)}")    # 15 (1+2+3+4+5)
print(f"1 dan 10 gacha: {yigindi(10)}")  # 55
print(f"1 dan 100 gacha: {yigindi(100)}")# 5050
```

**Expected output:**
```
1 dan 5 gacha: 15
1 dan 10 gacha: 55
1 dan 100 gacha: 5050
```

**Jarayon (yigindi(5)):**
```
yigindi(5)
    → 5 + yigindi(4)
        → 4 + yigindi(3)
            → 3 + yigindi(2)
                → 2 + yigindi(1)
                    → 1 (BASE CASE)
                → 2 + 1 = 3
            → 3 + 3 = 6
        → 4 + 6 = 10
    → 5 + 10 = 15
```

---

### ⚠️ Xavfli: Infinite recursion (Cheksiz rekursiya)

Agar **base case yo'q bo'lsa** yoki **base case ga yetilmasa**, rekursiya to'xtamaydi!

```python
# ❌ XATO — Base case yo'q
def cheksiz(n):
    print(n)
    cheksiz(n - 1)  # Hech qachon to'xtamaydi!

# cheksiz(5)  # RecursionError: maximum recursion depth exceeded
```

**To'g'ri variant:**

```python
# ✅ TO'G'RI — Base case bor
def to_g_ri(n):
    if n == 0:  # TO'XTASH SHARTI
        return
    print(n)
    to_g_ri(n - 1)

to_g_ri(5)  # 5, 4, 3, 2, 1 — keyin to'xtaydi
```

---

### Rekursiya qachon ishlatiladi?

✅ **Yaxshi ishlatish:**
- Daraxt strukturalari (directories, family tree)
- Matematik formulalar (faktorial, Fibonacci)
- Bo'linish va zabt qilish (Divide and Conquer) algoritmlari
- Backtracking algoritmlari

❌ **Yomon ishlatish:**
- Oddiy sikllar o'rniga (loop yaxshiroq)
- Katta sonlar uchun (stack overflow)
- Tezlik muhim bo'lganda (rekursiya sekinroq)

---

## 10) Funksiya ichida sikllar (while + for)

### 🔁 while bilan funksiyalar

**Misol 1: Sonni teskari chiqarish**

```python
def teskari_chop(n):
    """n dan 1 gacha sonlarni chop etadi"""
    while n > 0:  # n 0 dan katta bo'lguncha
        print(n, end=" ")  # Sonni chop et
        n -= 1  # n ni kamaytir
    print()  # Yangi qatorga o'tish

teskari_chop(10)
teskari_chop(5)
```

**Expected output:**
```
10 9 8 7 6 5 4 3 2 1 
5 4 3 2 1 
```

**Misol 2: Parolni tekshirish**

```python
def parol_tekshir():
    """To'g'ri parol kiritilgunga qadar so'raydi"""
    togri_parol = "python123"
    urinishlar = 3
    
    while urinishlar > 0:
        parol = input("Parolni kiriting: ")
        
        if parol == togri_parol:
            print("✅ Parol to'g'ri! Xush kelibsiz!")
            return True  # Funksiya to'xtaydi
        else:
            urinishlar -= 1
            if urinishlar > 0:
                print(f"❌ Noto'g'ri! Qolgan urinishlar: {urinishlar}")
            else:
                print("❌ Barcha urinishlar tugadi!")
    
    return False

# parol_tekshir()  # Ishga tushirish uchun kommentdan chiqaring
```

---

### 🔂 for bilan funksiyalar

**Misol 1: Ro'yxatdagi juft sonlar**

```python
def juft_sonlar(royxat):
    """Ro'yxatdagi juft sonlarni qaytaradi"""
    juftlar = []  # Bo'sh ro'yxat
    
    for son in royxat:  # Har bir son ustida
        if son % 2 == 0:  # Agar juft bo'lsa
            juftlar.append(son)  # Ro'yxatga qo'sh
    
    return juftlar

sonlar = [1, 2, 3, 4, 5, 6, 7, 8, 9, 10]
print(juft_sonlar(sonlar))  # [2, 4, 6, 8, 10]

sonlar2 = [15, 22, 31, 44, 55, 66]
print(juft_sonlar(sonlar2))  # [22, 44, 66]
```

**Expected output:**
```
[2, 4, 6, 8, 10]
[22, 44, 66]
```

**Misol 2: Baholarning o'rtacha qiymati**

```python
def ortacha_ball(baholar):
    """Baholarning o'rtacha qiymatini hisoblaydi"""
    if len(baholar) == 0:  # Bo'sh ro'yxat tekshiruvi
        return 0
    
    jami = 0
    for ball in baholar:  # Har bir ball ustida
        jami += ball  # Yig'indiga qo'sh
    
    ortacha = jami / len(baholar)  # O'rtacha qiymat
    return ortacha

talaba1 = [85, 90, 78, 92, 88]
print(f"O'rtacha: {ortacha_ball(talaba1):.2f}")  # 86.60

talaba2 = [100, 95, 98]
print(f"O'rtacha: {ortacha_ball(talaba2):.2f}")  # 97.67

talaba3 = []
print(f"O'rtacha: {ortacha_ball(talaba3):.2f}")  # 0.00
```

**Expected output:**
```
O'rtacha: 86.60
O'rtacha: 97.67
O'rtacha: 0.00
```

---

### 🔍 Qidiruv funksiyalari

**Misol: Elementni qidirish**

```python
def element_topish(royxat, qiymat):
    """Elementning ro'yxatdagi indeksini topadi"""
    
    for indeks in range(len(royxat)):  # Indekslar ustida
        if royxat[indeks] == qiymat:  # Agar topilsa
            return indeks  # Indeksni qaytaradi
    
    return -1  # Topilmasa -1 qaytaradi

mevalar = ["olma", "banan", "uzum", "anor"]

print(element_topish(mevalar, "uzum"))   # 2
print(element_topish(mevalar, "banan"))  # 1
print(element_topish(mevalar, "qovun"))  # -1 (yo'q)
```

**Expected output:**
```
2
1
-1
```

---

### 📊 Hisoblash funksiyalari

**Misol: So'zlar soni**

```python
def sozlar_soni(matn):
    """Matndagi so'zlar sonini qaytaradi"""
    if len(matn) == 0:  # Bo'sh matn
        return 0
    
    sozlar = matn.split()  # Bo'sh joy bo'yicha ajratish
    return len(sozlar)

matn1 = "Python dasturlash tili juda qiziqarli"
print(f"So'zlar soni: {sozlar_soni(matn1)}")  # 5

matn2 = "Salom"
print(f"So'zlar soni: {sozlar_soni(matn2)}")  # 1

matn3 = ""
print(f"So'zlar soni: {sozlar_soni(matn3)}")  # 0
```

**Expected output:**
```
So'zlar soni: 5
So'zlar soni: 1
So'zlar soni: 0
```

---

## 11) Xatolar — 15+ keng tarqalgan xato

### ❌ XATO 1: Funksiya nomini noto'g'ri yozish

```python
# ❌ NOTO'G'RI
def SalomBerish():  # Katta harf bilan boshlangan
    print("Salom")

# ✅ TO'G'RI
def salom_berish():  # snake_case
    print("Salom")
```

**Sabab:** Python'da funksiya nomlari kichik harfda, so'zlar orasida _ bo'lishi kerak.

---

### ❌ XATO 2: return ni unutish

```python
# ❌ NOTO'G'RI
def qoshish(a, b):
    natija = a + b  # return yo'q!

javob = qoshish(5, 3)
print(javob)  # None

# ✅ TO'G'RI
def qoshish(a, b):
    return a + b  # return mavjud

javob = qoshish(5, 3)
print(javob)  # 8
```

**Sabab:** `return` bo'lmasa, funksiya `None` qaytaradi.

---

### ❌ XATO 3: return ni noto'g'ri joyga qo'yish

```python
# ❌ NOTO'G'RI
def faktorial(n):
    return 1  # Darhol 1 qaytaradi!
    if n == 0:
        return 1
    return n * faktorial(n - 1)

# ✅ TO'G'RI
def faktorial(n):
    if n == 0:  # Avval shartni tekshir
        return 1
    return n * faktorial(n - 1)
```

---

### ❌ XATO 4: Mutable default argument

```python
# ❌ NOTO'G'RI — Ro'yxat default qiymat
def qosh(element, royxat=[]):
    royxat.append(element)
    return royxat

print(qosh(1))  # [1]
print(qosh(2))  # [1, 2] — XATO! [2] bo'lishi kerak!

# ✅ TO'G'RI — None ishlatish
def qosh(element, royxat=None):
    if royxat is None:
        royxat = []
    royxat.append(element)
    return royxat

print(qosh(1))  # [1]
print(qosh(2))  # [2] — TO'G'RI!
```

**Sabab:** Default ro'yxat funksiya yaratilganda bitta marta yaratiladi va hammada bir xil bo'lib qoladi.

---

### ❌ XATO 5: Rekursiyada base case yo'q

```python
# ❌ NOTO'G'RI — Infinite loop
def hisoblash(n):
    return n + hisoblash(n - 1)  # Base case yo'q!

# ✅ TO'G'RI — Base case mavjud
def hisoblash(n):
    if n == 0:  # Base case
        return 0
    return n + hisoblash(n - 1)
```

**Sabab:** Base case bo'lmasa, rekursiya hech qachon to'xtamaydi.

---

### ❌ XATO 6: Haddan ortiq parametr

```python
# ❌ NOTO'G'RI — Ko'p parametr berilgan
def qoshish(a, b):
    return a + b

print(qoshish(1, 2, 3))  # TypeError: takes 2 positional arguments but 3 were given

# ✅ TO'G'RI — To'g'ri miqdorda parametr
print(qoshish(1, 2))  # 3
```

**Sabab:** Funksiya 2 ta parametr kutadi, lekin 3 ta berilgan.

---

### ❌ XATO 7: *args va **kwargs ni chalkashtirish

```python
# ❌ NOTO'G'RI
def test(*kwargs):  # * o'rniga ** bo'lishi kerak
    print(kwargs)

test(ism="Ali", yosh=20)  # TypeError

# ✅ TO'G'RI
def test(**kwargs):  # Keyword arguments uchun **
    print(kwargs)

test(ism="Ali", yosh=20)  # {'ism': 'Ali', 'yosh': 20}
```

**Sabab:** `*args` — tuple, `**kwargs` — dictionary.

---

### ❌ XATO 8: Global o'zgaruvchini noto'g'ri ishlatish

```python
hisob = 0

# ❌ NOTO'G'RI
def oshir():
    hisob += 1  # UnboundLocalError
    return hisob

# ✅ TO'G'RI
def oshir():
    global hisob
    hisob += 1
    return hisob
```

**Sabab:** Global o'zgaruvchini o'zgartirish uchun `global` kalit so'zi kerak.

---

### ❌ XATO 9: Lambda ni noto'g'ri ishlatish

```python
# ❌ NOTO'G'RI — Lambda ko'p qatorli bo'lolmaydi
kvadrat = lambda x:
    natija = x ** 2
    return natija

# ✅ TO'G'RI — Lambda faqat bir qatorli
kvadrat = lambda x: x ** 2
```

**Sabab:** Lambda faqat bitta ifoda bo'lishi mumkin.

---

### ❌ XATO 10: Funksiyani chaqirishda qavslarni unutish

```python
def salom():
    print("Salom!")

# ❌ NOTO'G'RI
salom  # Funksiya chaqirilmadi, faqat funksiya obyekti

# ✅ TO'G'RI
salom()  # Funksiya chaqirildi
```

---

### ❌ XATO 11: Indentation xatosi

```python
# ❌ NOTO'G'RI
def test():
print("Xato")  # IndentationError

# ✅ TO'G'RI
def test():
    print("To'g'ri")  # 4 ta bo'sh joy
```

---

### ❌ XATO 12: Parametr va argument sonini moslashtirib bo'lmaydi

```python
# ❌ NOTO'G'RI
def funksiya(a, b, c):
    return a + b + c

funksiya(1, 2)  # TypeError: missing 1 required positional argument

# ✅ TO'G'RI
funksiya(1, 2, 3)  # 6
```

---

### ❌ XATO 13: print va return ni adashtirish

```python
# ❌ NOTO'G'RI — print qaytarmaydi
def qoshish(a, b):
    print(a + b)  # Faqat ekranga chiqaradi

natija = qoshish(5, 3)  # 8 chiqadi
print(natija * 2)  # TypeError: None ni ko'paytirish mumkin emas

# ✅ TO'G'RI — return ishlatish
def qoshish(a, b):
    return a + b

natija = qoshish(5, 3)
print(natija * 2)  # 16
```

---

### ❌ XATO 14: Funksiya ichida o'zgaruvchini e'lon qilmasdan ishlatish

```python
# ❌ NOTO'G'RI
def hisoblash():
    print(x)  # NameError: x is not defined

# ✅ TO'G'RI
def hisoblash():
    x = 10
    print(x)
```

---

### ❌ XATO 15: Funksiyani e'lon qilmasdan chaqirish

```python
# ❌ NOTO'G'RI
salom()  # NameError: name 'salom' is not defined

def salom():
    print("Salom")

# ✅ TO'G'RI — Avval e'lon qilish
def salom():
    print("Salom")

salom()  # Keyin chaqirish
```

---

## 12) AMALIYOT — 25 ta amaliy masala

#### **Masala 1: Salomlashish funksiyasi**

**Vazifa:** Ismni qabul qilib, salomlashuvchi funksiya yozing.


**Expected output:**
```
Assalomu alaykum, Ali!
Assalomu alaykum, Madina!
```


---

#### **Masala 2: Katta sonni topish**

**Vazifa:** Ikki sondan kattasini qaytaruvchi funksiya.

**Expected output:**
```
20
50
15
```

---

#### **Masala 3: Teskari matn**

**Vazifa:** Matnni teskari qilib qaytaruvchi funksiya.

**Expected output:**
```
nohtyP
molaS
54321
```

---

#### **Masala 4: Ro'yxat yig'indisi**

**Vazifa:** Ro'yxatdagi sonlarning yig'indisini hisoblaydigan funksiya.

**Expected output:**
```
15
60
0
```
---

#### **Masala 5: Katta harfga o'girish**

**Vazifa:** Matnning har bir so'zini katta harf bilan boshlaydigan funksiya.

**Expected output:**
```
Salom Dunyo
Python Dasturlash
Ali Valiyev
```
---

#### **Masala 6: Tubmi yoki yo'qmi**

**Vazifa:** Sonning tub ekanligini tekshiruvchi funksiya.

**Expected output:**
```
True
False
False
True
```
---

#### **Masala 7: Takrorlanuvchi harflar**

**Vazifa:** Matndagi har bir harfning necha marta takrorlanganini hisoblash.

**Expected output:**
```
{'h': 1, 'e': 1, 'l': 2, 'o': 1}
{'p': 1, 'y': 1, 't': 1, 'h': 1, 'o': 1, 'n': 1}
```
---

#### **Masala 8: Palindrom tekshiruvi**

**Vazifa:** Matnning palindrom ekanligini tekshiruvchi funksiya.

**Expected output:**
```
True
True
False
True
```

---

#### **Masala 9: List comprehension bilan kvadratlar**

**Vazifa:** Ro'yxatdagi har bir sonning kvadratini topuvchi funksiya.


**Expected output:**
```
[1, 4, 9, 16, 25]
[100, 400, 900]
```

---

#### **Masala 10: Ro'yxatni filterlash**

**Vazifa:** Ro'yxatdan musbat sonlarni ajratib oluvchi funksiya.

**Expected output:**
```
[1, 3, 5]
[]
[5, 10, 15]
```

---

#### **Masala 11: Faktorial (iterativ)**

**Vazifa:** Faktorialni sikl yordamida hisoblash.

**Expected output:**
```
120
1
3628800
```

---

#### **Masala 12: Dictionary manipulation**

**Vazifa:** Ikki dictionary ni birlashtiruvchi funksiya.

**Expected output:**
```
{'a': 1, 'b': 2, 'c': 3, 'd': 4}
{'a': 20, 'b': 30}
```
---

#### **Masala 13: Fibonacci ketma-ketligi (iterativ)**

**Vazifa:** Birinchi n ta Fibonacci sonini qaytaruvchi funksiya.

**Expected output:**
```
[0, 1, 1, 2, 3, 5, 8, 13, 21, 34]
[0, 1, 1, 2, 3]
[0]
```
---

#### **Masala 14: Nested list flatten**

**Vazifa:** Ichma-ich ro'yxatni tekis ro'yxatga aylantirish.

**Expected output:**
```
[1, 2, 3, 4, 5, 6]
[1, 2, 3, 4, 5]
```
---

#### **Masala 15: Anagram tekshiruvi**

**Vazifa:** Ikki so'zning anagram ekanligini tekshirish.

**Expected output:**
```
True
False
True
```

---

#### **Masala 16: List dan dublikatlarni o'chirish**

**Vazifa:** Ro'yxatdan takrorlanuvchi elementlarni olib tashlash, tartibni saqlash.


**Expected output:**
```
[1, 2, 3, 4, 5]
['a', 'b', 'c']
```

---

#### **Masala 17: Eng ko'p takrorlangan element**

**Vazifa:** Ro'yxatda eng ko'p takrorlangan elementni topish.


**Expected output:**
```
3
a
```

---

#### **Masala 18: Zip bilan ishlash**

**Vazifa:** Ikkita ro'yxatni tuple'lar ro'yxatiga aylantirish.

**Expected output:**
```
[('Ali', 20), ('Vali', 21), ('Hasan', 19)]
```

---

#### **Masala 19: Decorator yaratish**

**Vazifa:** Funksiya ishlash vaqtini o'lchovchi decorator.

**Expected output:**
```
yigindi 0.01234 soniyada ishladi (taxminiy)
500000500000
```

---

#### **Masala 20: Generator funksiya**

**Vazifa:** Fibonacci sonlarini generator sifatida qaytarish.

**Expected output:**
```
0 1 1 2 3 5 8 13 21 34 
```

---

#### **Masala 21: Merge Sort**

**Vazifa:** Merge sort algoritmi yordamida ro'yxatni tartiblash.

**Expected output:**
```
[11, 12, 22, 25, 34, 64, 90]
```

---

#### **Masala 22: Memoization bilan Fibonacci**

**Vazifa:** Memoization yordamida Fibonacci ni optimallashtrish.

**Expected output:**
```
12586269025
354224848179261915075
```

---

#### **Masala 23: Binary Search**

**Vazifa:** Binary search algoritmi.

**Expected output:**
```
3
5
-1
```

---

#### **Masala 24: JSON bilan ishlash**

**Vazifa:** JSON ma'lumotlarini o'qish va yozish.

**Expected output:**
```
[{'ism': 'Ali', 'yosh': 20, 'ball': 85}, {'ism': 'Vali', 'yosh': 19, 'ball': 92}]
```

---

#### **Masala 25: Class va funksiyalarni birlashtirish**

**Vazifa:** Talaba klassini yaratish va funksiyalar bilan ishlash.

**Expected output:**
```
Barcha talabalar:
Ali (20 yosh) - O'rtacha: 87.67
Vali (19 yosh) - O'rtacha: 92.00
Hasan (21 yosh) - O'rtacha: 80.00

Eng yaxshi talaba:
Vali (19 yosh) - O'rtacha: 92.00
```

---

## 13) Test savollari — 20 ta

### **1. Funksiya qanday e'lon qilinadi?**
A) function salom()  
B) def salom():  
C) func salom()  
D) define salom()  


---

### **2. Quyidagi kodning natijasi nima?**
```python
def test():
    return 5
    print("Salom")

test()
```
A) 5  
B) Salom  
C) 5 va Salom  
D) Xato  


---

### **3. Lambda funksiya nima?**
A) Oddiy funksiya  
B) Bir qatorli anonim funksiya  
C) Rekursiv funksiya  
D) Generator  


---

### **4. Global o'zgaruvchini funksiya ichida o'zgartirish uchun nima kerak?**
A) global kalit so'zi  
B) nonlocal kalit so'zi  
C) Hech narsa kerak emas  
D) return  


---

### **5. Quyidagi kodda xato bormi?**
```python
def qoshish(a, b=5, c):
    return a + b + c
```
A) Yo'q  
B) Ha, default parametr oxirida bo'lishi kerak  
C) Ha, return xato  
D) Ha, parametrlar noto'g'ri  


---

### **6. *args nima qaytaradi?**
A) List  
B) Dictionary  
C) Tuple  
D) Set  


---

### **7. Quyidagi kodning natijasi?**
```python
def test(x=[]):
    x.append(1)
    return x

print(test())
print(test())
```
A) [1] va [1]  
B) [1] va [1, 1]  
C) Xato  
D) [] va [1]  


---

### **8. Rekursiyada base case nima?**
A) Funksiyaning o'zini chaqirish  
B) To'xtash sharti  
C) Parametr  
D) Return qiymati  


---

### **9. filter() funksiyasi nima qiladi?**
A) Elementlarni o'zgartiradi  
B) Elementlarni saralaydi  
C) Elementlarni tartiblaydi  
D) Ro'yxat yaratadi  


---

### **10. Quyidagi kodning natijasi?**
```python
kvadrat = lambda x: x ** 2
print(kvadrat(5))
```
A) 10  
B) 25  
C) 5  
D) Xato  


---

### **11-20. Qisqa javobli savollar:**

11. **Funksiyaning return qiymati bo'lmasa nima qaytaradi?**  

12. **Funksiya ichida yaratilgan o'zgaruvchi qanday scope ga tegishli?**  

13. **yield kalit so'zi nimada ishlatiladi?**  

14. **Decorator nima?**  

15. **map() funksiyasi nima qiladi?**  

16. **Funksiyaning parametr va argumenti orasidagi farq nima?**  

17. **Rekursiya qachon to'xtaydi?**  

18. **sorted() funksiyasi key parametrida nima ishlatiladi?**  

19. **__name__ == "__main__" nima uchun ishlatiladi?**  

20. **Funksiya bir nechta qiymat qaytarishi mumkinmi?**  

---

## 14) Xulosa

### Bugun nimalarni o'rgandik?

1. **Funksiya asoslari**
   - Funksiya nima va nega kerak
   - Sintaksis va struktura
   - Parametrlar va argumentlar

2. **Return va print farqi**
   - return qiymat qaytaradi
   - print faqat ekranga chiqaradi

3. **Parametrlar turlari**
   - Oddiy parametrlar
   - Default parametrlar
   - *args — tuple
   - **kwargs — dictionary

4. **Scope (O'zgaruvchilar doirasi)**
   - Local va global scope
   - global kalit so'zi
   - Shadowing muammosi

5. **Lambda funksiyalar**
   - Bir qatorli funksiyalar
   - filter(), map(), sorted() bilan ishlash

6. **Rekursiya**
   - Base case va recursive case
   - Faktorial, Fibonacci
   - Call stack

7. **Sikllar bilan funksiyalar**
   - while va for bilan ishlash
   - Qidiruv va hisoblash

8. **Xatolar**
   - 15+ keng tarqalgan xato va ularning yechimlari

9. **Amaliyot**
   - 25 ta turli darajadagi masala
   - Kod yozish, debug qilish, test qilish

---
---

### ✅ Talaba bilishi shart bo'lgan 10 ta asosiy qoida

1. **Funksiya — bu qayta ishlatiladigan kod bloki**
   - DRY printsipini qo'llang

2. **return va print — bu turli narsalar**
   - return qaytaradi, print chiqaradi

3. **Parametr ≠ Argument**
   - Parametr ta'rifda, argument chaqirishda

4. **Default parametrlar oxirida bo'ladi**
   - `def func(a, b=5)` ✅  
   - `def func(a=5, b)` ❌

5. **Mutable default argumentlardan qoching**
   - `def func(x=[])` — XAVFLI!  
   - `def func(x=None)` — XAVFSIZ

6. **Global o'zgaruvchilarni kam ishlating**
   - Parametrlar orqali ma'lumot uzating

7. **Rekursiyada base case majburiy**
   - Aks holda — infinite loop

8. **Lambda faqat bir qatorli bo'ladi**
   - `lambda x: x ** 2` ✅  
   - Ko'p qatorli kod ❌

9. **Funksiyaning vazifasi aniq bo'lishi kerak**
   - Bitta funksiya — bitta vazifa

10. **Kodingizni test qiling**
    - Turli xil input'lar bilan sinang
    - Edge case'larni tekshiring

---

> "Funksiyalar — dasturlashning asosi. Ularni yaxshi bilsangiz, har qanday murakkab dasturni kichik qismlarga bo'lib, oson yecha olasiz!"

# Python dasturlash tilidagi FUNKSIYALAR bo'yicha to'liq dars tugadi!