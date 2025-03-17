### 1. **Print Specific Columns from a File**
```bash
awk '{print $1, $3}' file.txt
```
- This prints the **first** and **third** columns of each line in `file.txt`, separated by a space.
- `$1`, `$2`, `$3`, etc., refer to columns (fields) in the input.

---

### 2. **Print Lines Matching a Pattern**
```bash
awk '/error/ {print}' log.txt
```
- This prints all lines from `log.txt` that contain the word **"error"**.
- The pattern `/error/` is a regex match.

---

### 3. **Filter Based on a Numeric Condition**
```bash
awk '$3 > 50 {print $1, $3}' data.txt
```
- This prints the first and third columns **only for rows where the third column is greater than 50**.

---

### 4. **Sum Values in a Column**
```bash
awk '{sum += $2} END {print "Total:", sum}' sales.txt
```
- This calculates the **sum of the second column** in `sales.txt`.
- The `END` block runs after all lines are processed, printing the total sum.

---

### 5. **Find the Average of a Column**
```bash
awk '{sum += $2; count++} END {if (count > 0) print "Average:", sum/count}' scores.txt
```
- This computes the **average of the second column**.
- It sums up the values and counts the rows, then calculates the average in the `END` block.

---

### 6. **Print Line Numbers**
```bash
awk '{print NR, $0}' file.txt
```
- This prints each line with its **line number** (`NR` stands for "Number of Records").

---

### 7. **Extract Unique Values**
```bash
awk '!seen[$1]++' file.txt
```
- This prints **unique values of the first column**.
- The `seen[$1]++` array keeps track of whether a value has been encountered before.

---

### 8. **Replace a Word in a File**
```bash
awk '{gsub(/oldword/, "newword"); print}' file.txt
```
- This **replaces** all occurrences of `oldword` with `newword` in each line.
- `gsub()` performs a global substitution.

---

### 9. **Print Only Even-Numbered Lines**
```bash
awk 'NR % 2 == 0' file.txt
```
- This prints **only even-numbered lines**.

---

### 10. **Find the Maximum Value in a Column**
```bash
awk 'NR == 1 || $2 > max {max = $2} END {print "Max:", max}' data.txt
```
- This finds the **maximum value in the second column**.
- The first row initializes `max`, and subsequent rows update it.

---

### 11. **Count the Number of Lines in a File**
```bash
awk 'END {print NR}' file.txt
```
- This prints the **total number of lines** in `file.txt`.
- `NR` represents the last line number processed.

---

### 12. **Extract Lines Within a Range**
```bash
awk 'NR >= 10 && NR <= 20' file.txt
```
- This extracts **lines from 10 to 20**.

---

### 13. **Format Output with Custom Delimiters**
```bash
awk -F ',' '{print $1, $3}' OFS=" | " data.csv
```
- `-F ','` sets the field separator to a comma (for CSV files).
- `OFS=" | "` sets the output field separator to `" | "`.

---

### 14. **Print Last Column of Each Line**
```bash
awk '{print $NF}' file.txt
```
- `$NF` refers to the **last column**.

---

### 15. **Count Frequency of Words in a File**
```bash
awk '{for (i=1; i<=NF; i++) freq[$i]++} END {for (word in freq) print word, freq[word]}' file.txt
```
- This counts the **occurrences of each word** in a file.

---

### 16. **Extract Fields Using Regex**
```bash
awk '$2 ~ /^[0-9]+$/' data.txt
```
- This selects lines where the **second column contains only numbers**.

---

### 17. **Perform Arithmetic Calculations**
```bash
echo "10 20" | awk '{print $1 + $2}'
```
- This computes **10 + 20** and prints `30`.

---

### 18. **Reverse Column Order**
```bash
awk '{for(i=NF; i>0; i--) printf "%s ", $i; print ""}' file.txt
```
- This **reverses the order of columns** in each line.


