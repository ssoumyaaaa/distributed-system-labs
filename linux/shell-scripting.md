# Shell Scripting in Linux

Shell scripting allows you to automate tasks in Linux using a sequence of commands written in a file. It is widely used in DevOps, CI/CD pipelines, and system automation.

---

## 🐚 What is a Shell Script?

A shell script is a text file containing Linux commands executed in sequence.

Example:

```bash
#!/bin/bash
echo "Hello Linux"
```

---

## 📌 Create a Script

```bash
touch script.sh
```

Edit file:

```bash
nano script.sh
```

---

## ▶️ Run a Script

### Method 1

```bash
bash script.sh
```

### Method 2

```bash
chmod +x script.sh
./script.sh
```

---

## 🔐 Shebang (Important)

```bash
#!/bin/bash
```

Tells system which interpreter to use.

---

## 📥 Variables

```bash
name="Linux"
echo $name
```

---

## 📊 User Input

```bash
echo "Enter your name:"
read name
echo "Hello $name"
```

---

## 🔁 If-Else Condition

```bash
if [ $a -gt $b ]
then
  echo "A is greater"
else
  echo "B is greater"
fi
```

---

## 🔄 Loops

### For loop

```bash
for i in 1 2 3
do
  echo $i
done
```

### While loop

```bash
i=1
while [ $i -le 5 ]
do
  echo $i
  i=$((i+1))
done
```

---

## 📌 Functions

```bash
function greet() {
  echo "Hello World"
}

greet
```

---

## 📂 File Check

```bash
if [ -f file.txt ]
then
  echo "File exists"
fi
```

---

## ⚙️ Exit Status

```bash
echo $?
```

- 0 → Success
- Non-zero → Error

---

## 🧠 Key Concepts

- Scripts automate repetitive tasks
- Shell scripts are executed line by line
- Bash is the most common shell
- Used in DevOps automation and CI/CD

---

## 🛠️ Practice

```bash
#!/bin/bash
echo "Starting script"
for i in 1 2 3
do
  echo "Number $i"
done
```

---

## 🎯 Why This Matters

- Automates server tasks
- Used in deployment pipelines
- Important for Kubernetes and Docker scripts
- Essential for system administration

---
