# Ultimate Password Strength Checker

## 🚀 Introduction
The **Ultimate Password Strength Checker** is a simple yet powerful web application built with [Streamlit](https://streamlit.io/). It allows users to evaluate their password strength and provides suggestions for improvement.

---

## 📌 Features
- 🔐 **Password Strength Checking** using regex-based validation.
- 🎨 **Custom UI Styling** with CSS for an enhanced user experience.
- 💡 **Real-time Suggestions** to improve weak passwords.
- 🎈 **Interactive Animations** for strong passwords.
- ✅ **User-Friendly Interface** built with Streamlit.

---

## 🛠️ Technologies Used
- **Python** 🐍
- **Streamlit** 🎨
- **Regular Expressions (re module)** 🔍
- **HTML & CSS (for UI customization)** 🖌️

---

## 📥 Installation & Setup
To run the project locally, follow these steps:

### 1️⃣ Clone the Repository
```bash
$ git clone https://github.com/your-username/password-strength-checker.git
$ cd password-strength-checker
```

### 2️⃣ Install Dependencies
```bash
$ pip install streamlit
```

### 3️⃣ Run the Application
```bash
$ streamlit run app.py
```

---

## 📜 Code Overview

### 1️⃣ Importing Required Libraries
```python
import streamlit as st
import re
```

- `streamlit` → A Python framework for creating web applications.
- `re` → A built-in module for handling regular expressions (used for password validation).

### 2️⃣ Setting the Page Configuration
```python
st.set_page_config(page_title="Ultimate Password Strength Checker", page_icon="🔐", layout="centered")
```
- Sets page title, icon, and layout.

### 3️⃣ Custom Styling with CSS
```python
st.markdown(
    """
    <style>
        .title { text-align: center; color: #4CAF50; font-size: 32px; }
        .subtitle { text-align: center; color: #666; font-size: 18px; }
        .stTextInput>div>div>input { border: 2px solid #4CAF50 !important; border-radius: 10px; }
        .stButton>button { background-color: #4CAF50 !important; color: white !important; border-radius: 10px; width: 100%; padding: 10px; }
    </style>
    """,
    unsafe_allow_html=True
)
```
- Enhances UI with better text alignment, colors, and button styling.

### 4️⃣ Creating the Password Input Field
```python
password = st.text_input("🔑 Enter your password:", type="password")
```
- Accepts password input while keeping it hidden.

### 5️⃣ Defining the Password Strength Checker Function
```python
def check_password_strength(password):
    score = 0
    feedback = []
```
- Evaluates password strength and returns a score with feedback.

### 6️⃣ Password Validation Criteria
```python
if len(password) >= 12:
    score += 2
elif len(password) >= 8:
    score += 1
else:
    feedback.append("❌ Password should be at least **8 characters** long.")
```
- Checks length (12+ chars → strong, 8-11 chars → moderate, <8 chars → weak).

```python
if re.search(r"[A-Z]", password) and re.search(r"[a-z]", password):
    score += 1
else:
    feedback.append("❌ Include **both uppercase and lowercase** letters.")
```
- Ensures a mix of uppercase and lowercase letters.

```python
if re.search(r"\d", password):
    score += 1
else:
    feedback.append("❌ Add at least **one number (0-9)**.")
```
- Checks for at least one digit.

```python
if re.search(r"[!@#$%^&*()_+=<>?/{}\[\]~-]", password):
    score += 1
else:
    feedback.append("❌ Include at least **one special character (!@#$%^&*)**.")
```
- Validates the presence of special characters.

### 7️⃣ Checking & Displaying Results
```python
if st.button("🔍 Check Password Strength"):
    if password:
        score, feedback = check_password_strength(password)
        st.subheader("🔒 Password Strength Result:")
```
- Runs password validation when the user clicks the button.

### 8️⃣ Showing Strength Levels
```python
if score >= 5:
    st.success("✅ Strong Password! Your password is highly secure.")
    st.balloons()
elif score == 3 or score == 4:
    st.warning("⚠️ Moderate Password - Consider adding more security features.")
else:
    st.error("❌ Weak Password - Improve it using the suggestions below.")
```
- **Strong Password (5+ points)** → Green ✅ Success Message + 🎈 Balloons.
- **Moderate Password (3-4 points)** → Yellow ⚠️ Warning.
- **Weak Password (0-2 points)** → Red ❌ Error Message.

### 9️⃣ Displaying Suggestions
```python
if feedback:
    st.info("💡 Suggestions to improve your password:")
    for tip in feedback:
        st.write(tip)
```
- Provides tips to strengthen weak/moderate passwords.

### 🔟 Handling Empty Password Field
```python
else:
    st.error("🚨 Please enter a password to check.")
```
- Displays an error if the field is empty.

### 🔚 Adding Footer
```python
st.markdown("""
---
<div style='text-align: center;'>
    Made with ❤️ by <b>Mohsin Raza</b>
</div>
""", unsafe_allow_html=True)
```
- Adds a personal credit at the bottom.

---

## 📷 Screenshots
(Include relevant screenshots of your app here.)

---

## 📜 License
This project is open-source and available under the [MIT License](LICENSE).

---

## 🌟 Contributing
Contributions are welcome! Feel free to fork the repository and submit a pull request.

---

## 🔗 Connect with Me
👤 **Mohsin Raza**  
📧 Email: mohsinraza332@gmail.com  
🔗 [LinkedIn](https://www.linkedin.com/in/mohsin-raza-a514392b6)  

