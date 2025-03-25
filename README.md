# EXP.NO.7-Simulation-of-Digital-Modulation-Techniques
7. Simulation of Digital Modulation Techniques Such as
   i) Amplitude Shift Keying (ASK)
   ii) Frequency Shift Keying (FSK)
   iii) Phase Shift Keying (PSK)

# AIM
To implement and verify the Digital Modulation Techniques Such as Amplitude Shift Keying,Frequency Shift Keying and Phase Shift Keying using python.

# SOFTWARE REQUIRED
Python 

# ALGORITHMS

Step 1: Define Parameters  
- Input binary data sequence.  
- Define bit duration, sampling rate, and carrier amplitude.  
- Set carrier frequency`fc` (for ASK & PSK).  
- Define two frequencies`f1` & `f0` for FSK.  
- Set phase shift values for PSK (e.g., `0°` for `1`, `180°` for `0`).  

Step 2: Generate Time Vector
- Compute the time vector based on bit duration and sampling rate.  

Step 3: Generate Message Signal  
- Convert the binary sequence into a waveform by repeating each bit over its duration.  

Step 4: Generate Carrier Signal(s)

Step 5: Perform Modulation
- ASK:Multiply message signal with carrier signal.  
- FSK:Select appropriate frequency for each bit.  
- PSK: Adjust phase based on bit value.  

Step 6: Plot the Signals
- Display message signal, carrier signal, and modulated signal.  


# PROGRAM

i)Amplitude Shift Keying (ASK):
 
import numpy as np 
import matplotlib.pyplot as plt 
# Parameters 
data = [1, 0, 1, 0, 1, 1, 0, 1] # Binary data to be transmitted 
bit_duration = 1 # Duration of each bit in seconds 
fc = 10 # Carrier frequency in Hz 
amplitude = 2 # Carrier amplitude 
sampling_rate = 1000 # Number of samples per second 
# Time vector 
t = np.arange(0, bit_duration * len(data), 1/sampling_rate) 
# Message signal 
message_signal = np.repeat(data, sampling_rate * bit_duration) 
# Carrier signal 
carrier_signal = amplitude * np.sin(2 * np.pi * fc * t) 
# ASK modulation 
ask_signal = amplitude * message_signal * np.sin(2 * np.pi * fc * t) 
# Plotting 
plt.figure(figsize=(12, 8)) 
plt.subplot(3, 1, 1) 
plt.plot(t, message_signal) 
plt.title('Message Signal') 
plt.xlabel('Time') 
plt.ylabel('Amplitude') 
plt.subplot(3, 1, 2) 
plt.plot(t, carrier_signal) 
plt.title('Carrier Signal') 
plt.xlabel('Time') 
plt.ylabel('Amplitude') 
plt.subplot(3, 1, 3) 
plt.plot(t, ask_signal) 
plt.title('ASK Signal') 
plt.xlabel('Time') 
plt.ylabel('Amplitude') 
plt.tight_layout() 
plt.show() 

ii)Frequency Shift Keying (FSK):

import numpy as np 
import matplotlib.pyplot as plt 
# Parameters 
data = [1, 0, 1, 0, 1, 1, 0, 1] # Binary data to be transmitted 
bit_duration = 1 # Duration of each bit in seconds 
fc1 = 15 # Frequency for binary 1 in Hz 
fc0 = 10 # Frequency for binary 0 in Hz 
amplitude = 2 # Carrier amplitude 
sampling_rate = 1000 # Number of samples per second 
# Time vector 
t = np.arange(0, bit_duration * len(data), 1/sampling_rate) 
# Message signal 
message_signal = np.repeat(data, sampling_rate * bit_duration) 
# FSK modulation 
fsk_signal = [] 
for bit in data: 
if bit == 1: 
fsk_signal.extend(amplitude * np.sin(2 * np.pi * fc1 * np.arange(0, bit_duration, 1/sampling_rate))) 
else: 
fsk_signal.extend(amplitude * np.sin(2 * np.pi * fc0 * np.arange(0, bit_duration, 1/sampling_rate))) 
fsk_signal = np.array(fsk_signal) 
# Plotting 
plt.figure(figsize=(12, 8)) 
plt.subplot(3, 1, 1) 
plt.plot(t, message_signal) 
plt.title('Message Signal') 
plt.xlabel('Time') 
plt.ylabel('Amplitude') 
plt.subplot(3, 1, 2) 
plt.plot(t, amplitude * np.sin(2 * np.pi * fc1 * t), label='Carrier for 1') 
plt.plot(t, amplitude * np.sin(2 * np.pi * fc0 * t), label='Carrier for 0') 
plt.title('Carrier Signals') 
plt.xlabel('Time') 
plt.ylabel('Amplitude') 
plt.legend() 
plt.subplot(3, 1, 3) 
plt.plot(t, fsk_signal) 
plt.title('FSK Signal') 
plt.xlabel('Time') 
plt.ylabel('Amplitude') 
plt.tight_layout() 
plt.show()

 iii) Phase Shift Keying (PSK)

 import numpy as np 
import matplotlib.pyplot as plt 
# Parameters 
data = [1, 0, 1, 0, 1, 1, 0, 1] # Binary data to be transmitted 
bit_duration = 1 # Duration of each bit in seconds 
fc = 10 # Carrier frequency in Hz 
amplitude = 2 # Carrier amplitude 
sampling_rate = 1000 # Number of samples per second 
# Time vector 
t = np.arange(0, bit_duration * len(data), 1/sampling_rate) 
# Message signal 
message_signal = np.repeat(data, sampling_rate * bit_duration) 
# PSK modulation 
psk_signal = [] 
for bit in data: 
if bit == 1: 
psk_signal.extend(amplitude * np.sin(2 * np.pi * fc * np.arange(0, bit_duration, 1/sampling_rate))) 
else: 
psk_signal.extend(amplitude * np.sin(2 * np.pi * fc * np.arange(0, bit_duration, 1/sampling_rate) + 
np.pi)) 
psk_signal = np.array(psk_signal) 
# Plotting 
plt.figure(figsize=(12, 8)) 
plt.subplot(3, 1, 1) 
plt.plot(t, message_signal) 
plt.title('Message Signal') 
plt.xlabel('Time') 
plt.ylabel('Amplitude') 
plt.subplot(3, 1, 2) 
plt.plot(t, amplitude * np.sin(2 * np.pi * fc * t)) 
plt.title('Carrier Signal') 
plt.xlabel('Time') 
plt.ylabel('Amplitude') 
plt.subplot(3, 1, 3) 
plt.plot(t, psk_signal)  
plt.title('PSK Signal') 
plt.xlabel('Time') 
plt.ylabel('Amplitude') 
plt.tight_layout() 
plt.show()

# OUTPUT
Amplitude Shift Keying (ASK):
![image](https://github.com/user-attachments/assets/9fdd4995-913e-46be-9daa-dfba1265ab85)

Frequency Shift Keying (FSK):
![image](https://github.com/user-attachments/assets/78a8d727-8aed-460f-a1ea-4516033dc65d)

Phase Shift Keying (PSK):
![image](https://github.com/user-attachments/assets/bca9a0b9-4ae4-42c6-87e0-70053c3e6a69)

 
# RESULT / CONCLUSIONS
Hence the Digital Modulation Techniques Such as Amplitude Shift Keying,Frequency Shift Keying and Phase Shift Keying are verified using python.
