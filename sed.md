
String replace (global - all instances in file)
sed -i.bak 's/beta.kubernetes.io/kubernetes.io/g' complete-demo.yaml
  -i -> in-place update (update file)
  -i[xyz] -> in-place update but create a backup file with the "xyz" extension


Sure! Below are the `sed` command examples with more detailed explanations.

---

### 1. **Replace a Word in a File (Basic Substitution)**
   ```bash
   sed 's/oldword/newword/' file.txt
   ```
   - `s/oldword/newword/` → This tells `sed` to substitute `oldword` with `newword`.
   - Without the `g` flag, only the **first occurrence** of `oldword` in each line is replaced.
   - Example:
     ```bash
     echo "apple banana apple" | sed 's/apple/orange/'
     ```
     Output:
     ```
     orange banana apple
     ```

---

### 2. **Replace All Occurrences in a Line (Global Substitution)**
   ```bash
   sed 's/oldword/newword/g' file.txt
   ```
   - The `g` (global) flag ensures **all occurrences** in each line are replaced.
   - Example:
     ```bash
     echo "apple banana apple" | sed 's/apple/orange/g'
     ```
     Output:
     ```
     orange banana orange
     ```

---

### 3. **Edit a File In-Place**
   ```bash
   sed -i 's/oldword/newword/g' file.txt
   ```
   - `-i` → Edits the file **in place**, meaning the changes are saved to `file.txt` directly.
   - Without `-i`, `sed` prints to stdout and does not modify the file.

---

### 4. **Delete Specific Lines**
   ```bash
   sed '5d' file.txt
   ```
   - `5d` → Deletes line **5** from the file.
   - To delete a **range of lines**:
     ```bash
     sed '2,4d' file.txt
     ```
     This removes lines **2 to 4**.

---

### 5. **Remove Blank Lines**
   ```bash
   sed '/^$/d' file.txt
   ```
   - `^$` → Matches an **empty line** (line with nothing between start `^` and end `$`).
   - `d` → Deletes those lines.

---

### 6. **Replace Only in Lines Matching a Pattern**
   ```bash
   sed '/pattern/s/oldword/newword/g' file.txt
   ```
   - `/pattern/` → Restricts the substitution only to lines **containing `pattern`**.
   - Example:
     ```bash
     echo -e "foo bar\napple banana" | sed '/apple/s/banana/grape/'
     ```
     Output:
     ```
     foo bar
     apple grape
     ```

---

### 7. **Print Specific Lines**
   ```bash
   sed -n '5p' file.txt
   ```
   - `-n` → Suppresses default output.
   - `5p` → Prints only **line 5**.
   - To print a range:
     ```bash
     sed -n '3,7p' file.txt
     ```

---

### 8. **Insert a Line Before a Matching Line**
   ```bash
   sed '/pattern/i This is a new line' file.txt
   ```
   - `/pattern/` → Finds lines matching `pattern`.
   - `i` → Inserts the text **before** those lines.
   - Example:
     ```bash
     echo -e "apple\nbanana" | sed '/banana/i ---INSERTED LINE---'
     ```
     Output:
     ```
     apple
     ---INSERTED LINE---
     banana
     ```

---

### 9. **Append a Line After a Matching Line**
   ```bash
   sed '/pattern/a This is a new line' file.txt
   ```
   - `a` → Appends the text **after** the matched lines.

---

### 10. **Replace a Whole Line Containing a Pattern**
   ```bash
   sed '/pattern/c This line is replaced' file.txt
   ```
   - `c` → Completely **replaces** the matched line.
   - Example:
     ```bash
     echo -e "apple\nbanana" | sed '/banana/c This is a fruit'
     ```
     Output:
     ```
     apple
     This is a fruit
     ```

---

### 11. **Use Backreferences for Advanced Substitutions**
   ```bash
   echo "Hello 12345" | sed 's/\([0-9]\+\)/(&)/'
   ```
   - `\([0-9]\+\)` → Captures **one or more** digits.
   - `\1` → References the matched number.
   - Output:
     ```
     Hello (12345)
     ```

---

### 12. **Swap Two Words in a Line**
   ```bash
   echo "foo bar" | sed 's/\(foo\) \(bar\)/\2 \1/'
   ```
   - `\(foo\) \(bar\)` → Captures `foo` and `bar` separately.
   - `\2 \1` → Swaps their positions.
   - Output:
     ```
     bar foo
     ```

---

### 13. **Remove Trailing Whitespace**
   ```bash
   sed 's/[[:space:]]*$//' file.txt
   ```
   - `[[:space:]]*` → Matches **any whitespace characters**.
   - `$` → Ensures it’s at the **end of the line**.

---

### 14. **Replace a Character at a Specific Position**
   ```bash
   sed 's/\(^.\{3\}\)X/\1Y/' file.txt
   ```
   - `^.\{3\}` → Matches the **first 3 characters**.
   - `X` → The 4th character.
   - `Y` → Replaces it.

---

### 15. **Modify Only Lines Between Two Patterns**
   ```bash
   sed '/start/,/end/s/foo/bar/g' file.txt
   ```
   - `/start/,/end/` → Restricts modifications to lines between `start` and `end`.

---

### 16. **Extract Email Addresses from a File**
   ```bash
   sed -n 's/.*\([a-zA-Z0-9._%+-]\+@[a-zA-Z0-9.-]\+\.[a-zA-Z]\+\).*/\1/p' file.txt
   ```
   - Uses regex to extract **email addresses**.

---

### 17. **Add a Comma After Every 3 Digits (Thousands Separator)**
   ```bash
   echo "1234567890" | sed ':a;s/\B[0-9]\{3\}\>/,&/;ta'
   ```
   - Adds commas for readability.
   - Output:
     ```
     1,234,567,890
     ```

---

