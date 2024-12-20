<div align="center">

#  fill_form_tool

### *The robot that fills out forms so you don't have to.*

*Designed by **EVA**. Powered by caffeine. Tolerated by your mouse cursor.*

</div>

---

> *"It just works."*
> — your form, after 293 products, finally at peace.

---

##  What is this?

`fill_form_tool` is a tiny, fearless automation script. You give it a spreadsheet of products and a login page, and it sits down at your computer, takes the keyboard, and types like a tireless intern who never asks for a lunch break.

It opens Chrome, logs in, reads `produtos.csv`, and registers **all 293 products** — one by one, tab by tab, click by click — while you watch in quiet admiration (or mild terror, the first time).

---

##  Before You Begin

This script controls your **real mouse and keyboard**. It is not a metaphor. When it runs, your computer is *possessed* — gently, politely, but fully possessed.

A few sacred rules:

-  **Don't touch anything** while it runs. The robot does not negotiate.
-  **Coordinates are hardcoded** (`x=685, y=451` and friends). They were measured on *one specific screen*. Yours is probably different.
-  **Slam the mouse into a screen corner** to abort. PyAutoGUI's emergency brake. Memorize this. Love this.

---

##  Ingredients

```bash
pip install pyautogui pandas
```

You'll also need:
- `produtos.csv` — your product base (293 rows, 7 columns: `codigo`, `marca`, `tipo`, `categoria`, `preco_unitario`, `custo`, `obs`)
- A login page that accepts your credentials and a form that accepts your patience

---

##  How It Works

The script moves through five graceful acts:

| Step | What happens | Mood |
|------|-------------|------|
| **1. Open the stage** | Presses `win`, types `chrome`, opens the login URL | Curtains up |
| **2. Log in** | Clicks the email field, types email, `tab`, types password, clicks login | The handshake |
| **3. Read the data** | `pandas` loads `produtos.csv` into a tidy table | The homework |
| **4. Register each product** | Loops every row: click → type → `tab` → repeat → `enter` → scroll up | The marathon |
| **5. Repeat until done** | Does it again. And again. 293 times. Without complaint. | Zen |

---

##  The Calibration Ritual (do this first!)

The coordinates won't match your screen. Use the companion script to find the real ones:

```python
import time
import pyautogui

time.sleep(5)              # 5 seconds to hover over the field you want
print(pyautogui.position()) # prints (x, y) — write these down
pyautogui.scroll(200)
```

Run it, hover your cursor over each field, read the coordinates, and update the `pyautogui.click(x=..., y=...)` lines in `fill_form_tool.py`. Think of it as teaching the robot where its hands go.

---

##  Run It

```bash
python fill_form_tool.py
```

Then step away. Make tea. Watch a small machine do an honest day's work.

---

##  Notes from EVA

- Adjust `pyautogui.PAUSE` (currently `0.3`) if your site loads slowly — too fast and the robot types into the void.
- The `obs` column is checked for empty values before typing, because even robots respect blank fields.
- The final `pyautogui.scroll(5000)` resets the page to the top before the next product. Tidy.

---

<div align="center">

*Made with affection and a slightly haunted keyboard by **EVA**.*

** | Don't touch the mouse.**

</div>
