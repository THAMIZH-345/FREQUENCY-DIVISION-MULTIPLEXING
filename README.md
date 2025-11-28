# FREQUENCY-DIVISION-MULTIPLEXING
# AIM
To implement Frequency Division Multiplexing (FDM) for six different message signals using Scilab, generate the multiplexed signal, and perform demultiplexing to recover all the original message signals. The experiment also includes plotting the message signals, multiplexed signal, and demultiplexed signals.
# APPARATUS REQUIRED
   1. Computer System
   2. Scilab Software
# ALGORITHM
  1. Set sampling frequency, time duration, and time vector.
  2. Generate six message signals with different frequencies.
  3. Assign six different carrier frequencies.
  4. Perform DSB-SC modulation by multiplying each message with its carrier.
  5. Add all modulated signals to form the multiplexed FDM signal.
  6. For each channel, multiply the multiplexed signal with the same carrier (demodulation).
  7. Apply a low-pass filter to extract the recovered message.
  8. Plot message signals, multiplexed signal, and recovered signals.
# THEORY
Frequency Division Multiplexing (FDM) is a technique in which multiple message signals are transmitted simultaneously over a single communication channel by assigning each signal a different carrier frequency. Each message modulates its own carrier, and all modulated signals are added to form the multiplexed signal. Since the carrier frequencies are well separated, the signals do not overlap in the frequency domain.

At the receiver, each signal is recovered by multiplying the multiplexed signal with the corresponding carrier (coherent demodulation) and passing it through a low-pass filter to extract the original baseband message. FDM is widely used in radio broadcasting, telephone systems, and cable TV.
# PROGRAM
```ASM
clc;
clear;
close;
fs = 50000;
t = 0:1/fs:0.05;
fm = [100,200,300,400,500,600];
m1 = cos(2*%pi*fm(1)*t);
m2 = cos(2*%pi*fm(2)*t);
m3 = cos(2*%pi*fm(3)*t);
m4 = cos(2*%pi*fm(4)*t);
m5 = cos(2*%pi*fm(5)*t);
m6 = cos(2*%pi*fm(6)*t);
figure(1);
subplot(6,1,1);plot(t,m1);
subplot(6,1,2);plot(t,m2);
subplot(6,1,3);plot(t,m3);
subplot(6,1,4);plot(t,m4);
subplot(6,1,5);plot(t,m5);
subplot(6,1,6);plot(t,m6);
fc = [2000,4000,6000,8000,10000,12000];
c1 = cos(2*%pi*fc(1)*t);
c2 = cos(2*%pi*fc(2)*t);
c3 = cos(2*%pi*fc(3)*t);
c4 = cos(2*%pi*fc(4)*t);
c5 = cos(2*%pi*fc(5)*t);
c6 = cos(2*%pi*fc(6)*t);
s1 = m1.*c1;
s2 = m2.*c2;
s3 = m3.*c3;
s4 = m4.*c4;
s5 = m5.*c5;
s6 = m6.*c6;
multiplex = s1+s2+s3+s4+s5+s6;
figure(2);
plot(t,multiplex);
r1 = multiplex.*c1;
r2 = multiplex.*c2;
r3 = multiplex.*c3;
r4 = multiplex.*c4;
r5 = multiplex.*c5;
r6 = multiplex.*c6;
N = 200; // smoothing window for LPF
h = ones(1,N)/N;
demod1 = conv(r1,h,'same');
demod2 = conv(r2,h,'same');
demod3 = conv(r3,h,'same');
demod4 = conv(r4,h,'same');
demod5 = conv(r5,h,'same');
demod6 = conv(r6,h,'same');
figure(3);
subplot(6,1,1);plot(t,demod1);
subplot(6,1,2);plot(t,demod2);
subplot(6,1,3);plot(t,demod3);
subplot(6,1,4);plot(t,demod4);
subplot(6,1,5);plot(t,demod5);
subplot(6,1,6);plot(t,demod6);
```
# OUTPUT WAVEFORM

<img width="792" height="704" alt="image" src="https://github.com/user-attachments/assets/ab188927-07be-4794-bcf6-b186dc821e09" />

<img width="750" height="695" alt="image" src="https://github.com/user-attachments/assets/d7c71f14-d76c-482a-849b-6ebdbb5b6f53" />

<img width="760" height="708" alt="image" src="https://github.com/user-attachments/assets/a8d93568-32b0-414e-8c28-2a565878d703" />

# CALCULATION

<img width="1200" height="1600" alt="image" src="https://github.com/user-attachments/assets/e31c6c8c-546d-4c9d-9c18-d6092f379602" />

# RESULT
Six different message signals were generated and modulated using FDM. All modulated signals were added to form a multiplexed FDM signal. Each message was successfully recovered using coherent demodulation followed by low-pass filtering. The plots confirmed accurate multiplexing and demultiplexing.
