# LTspice-filter
lowpass:
RC Low Pass Filter
Circuit:
Input voltage: Vin
Resistor: R
Capacitor: C
Output voltage across capacitor: Vout
Capacitor Impedance:
Xc = 1 / (j * omega * C)
Voltage Division:
Vout = Vin * (Xc / (R + Xc))
      Vin
       │
       │
       R
       │────────── Vout
       │
       C
       │
      GND
Substitute Xc:
Vout = Vin * ( (1 / (j * omega * C)) / (R + (1 / (j * omega * C))) )
Simplified:
Vout = Vin * (1 / (1 + j * omega * R * C))
Transfer Function:
H(jw) = Vout / Vin = 1 / (1 + j * omega * R * C)
condition at cutoff:
|H(jw)| = 1 / sqrt(2)   (≈ 0.707 of Vin)
omega_c = 1 / (R * C)
Cutoff frequency (fc) = 1 / (2 * pi * R * C)
for bandpass filters:
RC Band-Pass Filter (HPF + LPF)
Cutoff Frequencies
Lower cutoff frequency:
fL = 1 / (2 * pi * R1 * C1)
Higher cutoff frequency:
fH = 1 / (2 * pi * R2 * C2)
Working
For f < fL
HPF blocks the signal → C1 acts as an open circuit
For f > fH
LPF blocks the signal → C2 acts as a short circuit (output goes to ground)
Only frequencies in the range:
fL < f < fH are passed → Band-pass behavior
System Representation
Time domain:
y(t) = x(t)convolved(h1(t) convolve h2(t))
Frequency domain:
Y(jw) = X(jw) * H1(jw) * H2(jw)
High Pass Filter
Output equation:
Vout = Vin * R1 / (R1 + 1 / (jwC1))
Transfer function:
H1(jw) = (jw * R1 * C1) / (1 + jw * R1 * C1)
Low Pass Filter
Transfer function:
H2(jw) = 1 / (1 + jw * R2 * C2)
Overall Transfer Function
Band-pass:
HB(jw) = H1(jw) * H2(jw)
Final form:
HB(jw) = (jw * R1 * C1) / [(1 + jw * R1 * C1)(1 + jw * R2 * C2)]
        HPF                  LPF
Vin ──||───●────R2────●──── Vout
       C1   |          |
            R1         C2
            |          |
           GND        GND
