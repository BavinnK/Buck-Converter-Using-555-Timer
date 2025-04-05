# Buck Converter Using 555 Timer

This project demonstrates a **DC-DC buck converter** using a **555 timer IC** as a PWM generator. The output of the 555 controls an **IRLZ44N N-channel MOSFET** to step down a **12V DC input** to a regulated **5V DC output**.

![hahahah](https://github.com/user-attachments/assets/64c9660b-16c9-43fe-ba47-6deffd8fa512)


---

## ⚡ Overview

This buck converter is designed to simulate stepping down **230V AC mains power** to a safe, low-voltage **5V DC**. Due to simulator limitations, the AC front-end has been simplified for practical simulation, but the design intention is fully explained.

---

## 🛠️ Full Real-World Design (Intended Flow)

In a real-world application, this converter would operate like so:

1. **AC Input Stage**
   - 230V RMS @ 50Hz (standard wall outlet for Kurdistan , etc...).
2. **Step-Down Transformer**
   - Reduces AC voltage from 230V to ~12V AC.
3. **Schottky Bridge Rectifier**
   - Converts AC to pulsating DC.
4. **Smoothing Filter**
   - A **10,000µF** polarized capacitor smooths out the ripples and delivers ~12V DC.
5. **Buck Converter Stage**
   - Steps 12V DC down to 5V DC using PWM switching.

> ⚠️ **Note**: The free version of Proteus simulation software does not allow adding too many components. Therefore, the AC-to-DC front-end was omitted in simulation, and a **12V DC source** was connected directly to the buck converter stage instead.

---

## 🔧 Circuit Description

- **555 Timer (U1)**: Configured in **astable mode** to generate PWM.
- **MOSFET (Q1 - IRLZ44N)**: Acts as a high-speed switch.
- **Inductor (L1)**: Stores and releases energy during switching cycles.
- **Diode (D1)**: A **Schottky diode** to minimize forward voltage drop and allow freewheeling current.
- **Capacitor (C3)**: Smooths out the pulsed output.
- **Load Resistor (R3)**: Simulates a typical resistive load (500Ω).

---

## 🔢 Frequency & Duty Cycle Calculation

**555 Timer in Astable Mode:**

\[
f \approx \frac{1.44}{(R1 + 2R2) \cdot C}
\]

Given:
- R1 = 1kΩ  
- R2 = 7kΩ  
- C = 10nF  

\[
f \approx \frac{1.44}{(1k + 2 \cdot 7k) \cdot 10nF} = \frac{1.44}{150k \cdot 10^{-9}} \approx 9600 \text{ Hz}
\]

- **PWM Frequency**: ~9.6 kHz

**Duty Cycle:**

\[
D = \frac{R1 + R2}{R1 + 2R2} = \frac{1k + 7k}{1k + 14k} = \frac{8k}{15k} \approx 53.3\%
\]

**Expected Output Voltage:**

\[
V_{out} = D \cdot V_{in} = 0.533 \cdot 12V \approx 6.4V
\]

However, taking into account switching losses and diode drop, the actual simulated output stabilizes closer to **5V DC**.
with 500 ohm load resistor.
---

## ✅ Simulation Results

- **Input**: 12V DC
- **Output**: ~5V DC (clean and stable)
- **Frequency**: ~9.6 kHz
- **Output Ripple**: Low, thanks to the 470µF filter capacitor
- **Load**: 500Ω resistive

---

## 🧪 Tools Used

- **Software**: Proteus 8 (Free Version)
- **Simulation Limitations**: Limited number of components, so AC rectification stage was not simulated

---



## 🔧 Future Improvements


- Add **feedback control** using an op-amp to regulate output more precisely.
- Include **thermal protection** and **voltage/current sensing**.
- Implement **soft start** to avoid inrush current.

---

## 📷 Screenshot

![screen](https://github.com/user-attachments/assets/e8797e33-f1a5-486c-b0e9-135ddbe2571c)


---



## 🤝 Contributions

Feel free to fork the repo and submit pull requests! Suggestions, improvements, and discussions are always welcome.

---

