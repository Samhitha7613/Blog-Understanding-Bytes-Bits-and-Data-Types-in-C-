If you’ve ever wondered how numbers are stored in C++ and what terms like signed, unsigned this guide is for you! Let’s break everything down step-by-step in the simplest way possible.

## What are Bits and Bytes?

- **Bit** = Smallest piece of data in computers (either `0` or `1` → like a light switch: OFF or ON)
- **Byte** = Group of 8 bits (1 Byte = 8 Bits)

| Bytes | Bits |
|-------|------|
| 1     | 8    |
| 2     | 16   |
| 4     | 32   |

---

## 🔢 Example: How Many Bytes Does `10000` Use?

To store `10000`, we must first convert it to **binary**:

| Step | Division             | Quotient | Remainder |
|------|----------------------|----------|-----------|
| 1    | 10000 ÷ 2            | 5000     | 0         |
| 2    | 5000 ÷ 2             | 2500     | 0         |
| 3    | 2500 ÷ 2             | 1250     | 0         |
| 4    | 1250 ÷ 2             | 625      | 0         |
| 5    | 625 ÷ 2              | 312      | 1         |
| 6    | 312 ÷ 2              | 156      | 0         |
| 7    | 156 ÷ 2              | 78       | 0         |
| 8    | 78 ÷ 2               | 39       | 0         |
| 9    | 39 ÷ 2               | 19       | 1         |
| 10   | 19 ÷ 2               | 9        | 1         |
| 11   | 9 ÷ 2                | 4        | 1         |
| 12   | 4 ÷ 2                | 2        | 0         |
| 13   | 2 ÷ 2                | 1        | 0         |
| 14   | 1 ÷ 2                | 0        | 1         |


Final Binary: `10011100010000` → **14 bits**

So `10000` needs **14 bits**, which fits inside **2 bytes (16 bits)**.  
We can use the `short` data type to store this.

---

## 📊 C++ Integer Types – Size, Range & Use Cases

| Type         | Bits | Bytes | Signed Range                                      | Unsigned Range                               |
|--------------|------|--------|--------------------------------------------------|----------------------------------------------|
| `char`       | 8    | 1      | –128 to 127                                      | 0 to 255                                      |
| `short`      | 16   | 2      | –32,768 to 32,767                                | 0 to 65,535                                   |
| `int`        | 32   | 4      | –2,147,483,648 to 2,147,483,647                  | 0 to 4,294,967,295                            |
| `long`       | 32   | 4      | Same as `int` (on most systems)                 | Same as `int`                                 |
| `long long`  | 64   | 8      | –9,223,372,036,854,775,808 to 9,223,372,036,854,775,807 | 0 to 18,446,744,073,709,551,615 |


### `char` – For Single Characters

- You want to store a single character like 'A', '5', or '#'
-Internally, it’s stored as a number using ASCII codes (e.g., 'A' = 65)

#### Use When:
- Saving memory with small numbers
- Embedded systems or memory-limited devices

#### Example:
```
char grade = 'A';
char symbol = '#';
```
------
### `short`
- **Size:** 2 bytes (16 bits)
- **Range:** –32,768 to 32,767

#### Use When:
- Saving memory with small numbers
- Embedded systems or memory-limited devices

#### Avoid For:
- Storing full words or big numbers
- Large values like bank balances

#### Example:

```
short age = 22;
short temp = -10;
```
------

### `int`

- **Size:** 4 bytes (32 bits)  
- **Range:** –2,147,483,648 to +2,147,483,647  

#### ✅ Use When:

- General-purpose integer storage  
- Loop counters, indexes, calculations  

#### 🧾 Example:

```
int population = 1000000;
int marks = 95;
```
------

### `long`

- **Size:**
  - 4 bytes on 32-bit systems  
  - 8 bytes on most 64-bit Linux/macOS systems  
- **Range:** Varies with size

#### ✅ Use When:
- You need bigger numbers than `int` but smaller than `long long`  
- Storing large IDs, timestamps

#### 🧾 Example:

```
long distance = 123456789;
```

> 💡 Note:
> Windows 64-bit uses LLP64 model: long = 4 bytes
Linux/macOS 64-bit use LP64 model: long = 8 bytes

------

### `long long`

- **Size:** 8 bytes (64 bits)

#### ✅ Use When:
- Handling very large numbers that don’t fit in `int` or `long`  
- Competitive programming, large calculations, finance

#### 🧾 Example:

```
long long bigAmount = 1000000000000;
```
---

## What Do Signed and Unsigned Mean?

Imagine a number line:

```
<---- -3 -2 -1 0 1 2 3 ---->
```

### 🔁 Signed
- Can hold both **negative and positive** numbers  
- Uses **one bit** to indicate the sign (`0` = positive, `1` = negative)  
- **For 2 bytes (16 bits):**  
  Range = **–32,768 to +32,767**

### ➕ Unsigned
- Can hold **only positive** numbers (including zero)  
- **All bits** are used to store the value  
- **For 2 bytes (16 bits):**  
  Range = **0 to 65,535**

### 🔓 Real-life Analogy

You have **16 lockers (bits)**:

- If storing **only positive numbers** (`unsigned`), **all 16 lockers** are used for the value.  
- If storing **positive and negative numbers** (`signed`), **1 locker** is used for the sign, and **15 lockers** are used for the number itself.


---

