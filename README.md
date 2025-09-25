# SSB

EXP NO: 3	SSB-SC-AM MODULATION using SCILAB

AIM:

To write a program to perform SSBSC modulation and demodulation using SCI LAB and study its spectral characteristics

EQUIPMENTS REQUIRED

•	Computer with i3 Processor

•	SCI LAB

Note: Keep all the switch faults in off position


Algorithm
1.	Define Parameters:
•	Fs: Sampling frequency.
•	T: Duration of the signal.
•	Fc: Carrier frequency.
•	Fm: Frequency of the message signal.
•	Amplitude: Maximum amplitude of the message signal.
2.	Generate Signals:
•	Message Signal: The baseband signal that will be modulated.
•	Carrier Signal: A high-frequency signal used for modulation.
•	Analytic Signal: Constructed using the Hilbert transform to get the in-phase and quadrature components.
3.	SSBSC Modulation:
•	Modulated Signal: Create the SSBSC signal using the in-phase and quadrature components, modulated by the carrier.
4.	SSBSC Demodulation:
•	Mixing: Multiply the SSBSC signal with the carrier to retrieve the message signal.
•	Low-pass Filtering: Apply a low-pass filter to remove high-frequency components and recover the original message signal.
5.	Visualization:
•	Plot the message signal, carrier signal, SSBSC modulated signal, and the recovered signal after demodulation.


PROCEDURE

•	Refer Algorithms and write code for the experiment.
•	Open SCILAB in System
•	Type your code in New Editor
•	Save the file
 
•	Execute the code
•	If any Error, correct it in code and execute again
•	Verify the generated waveform using Tabulation and Model Waveform

Model Waveform

<img width="704" height="178" alt="image" src="https://github.com/user-attachments/assets/32ee29b3-0d95-4192-9762-972d50c05c90" />
<img width="706" height="167" alt="image" src="https://github.com/user-attachments/assets/bff0d8fd-d679-444e-af37-0b34585853c1" />

Program
```clc;
clear;
close;

// Parameters (your sir’s formula, with table value = 14)
Am = 14;       // Message amplitude
Ac = 28;       // Carrier amplitude (Am*2)
Fm = 10;       // Message frequency
Fc = 100;      // Carrier frequency (Fm*10)
Fs = 1000;     // Sampling frequency (Fc*10)
t  = 0:1/Fs:2/Fm;  // Time base (two message cycles)

// Message signal
m = Am * cos(2*%pi*Fm*t);
subplot(4,1,1);
plot(t, m);
xtitle("Message Signal");

// Carrier signal
c = Ac * cos(2*%pi*Fc*t);
subplot(4,1,2);
plot(t, c);
xtitle("Carrier Signal");

// ---- SSB-SC Modulation ----
// Analytic signal using Hilbert transform
mh = imag(hilbert(m));   // Hilbert transform of message

// Upper Sideband (USB)
ssb_usb = m .* cos(2*%pi*Fc*t) - mh .* sin(2*%pi*Fc*t);

// Lower Sideband (LSB)
//ssb_lsb = m .* cos(2*%pi*Fc*t) + mh .* sin(2*%pi*Fc*t);

subplot(4,1,3);
plot(t, ssb_usb);
xtitle("SSB-SC (USB) Signal");

// ---- Demodulation ----
demod = ssb_usb .* c;   // Coherent detection

// Simple Low-pass filter
N = 50;
h = ones(1,N)/N;
rec = conv(demod, h, "same");

subplot(4,1,4);
plot(t, rec);
xtitle("Demodulated Message Signal");
xgrid();
```

OUTPUT WAVEFORM
<img width="959" height="539" alt="image" src="https://github.com/user-attachments/assets/072304bc-fe21-4bf2-a88f-5a2d25023036" />


TABULATION









RESULT:

Thus, the SSB-SC-AM Modulation and Demodulation is experimentally done and the output is verified.





