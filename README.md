# Design-of-FIR-Filters-using-rectangular-window
#          DESIGN OF LOW PASS FIR DIGITAL FILTER 

# AIM: 
          
  To generate design of low pass FIR digital filter using SCILAB 

# APPARATUS REQUIRED: 

  PC Installed with SCILAB 

# PROGRAM 
```
clc;
clear;
close;

N = input("Enter filter length = ");
wc = input("Enter cutoff frequency (in radians) = ");

alpha = (N-1)/2;
n = 0:N-1;

hd = zeros(1,N);
for i = 1:N
    if n(i) == alpha then
        hd(i) = wc/%pi;
    else
        hd(i) = sin(wc*(n(i)-alpha))/(%pi*(n(i)-alpha));
    end
end

w = ones(1,N);
h = hd .* w;

[H,f] = frmag(h,256);
fn = f/%pi;

plot(fn,abs(H));
xlabel("Normalized Frequency");
ylabel("Magnitude");
title("Frequency Response of FIR Filter using Rectangular Window");
```



# OUTPUT
<img width="1918" height="945" alt="Screenshot 2026-03-12 140232" src="https://github.com/user-attachments/assets/2beaf14b-edfb-4b94-9eac-657147d0d22e" />


# RESULT
The FIR filter designed using the rectangular window shows the magnitude response with normalized frequency on the x-axis and magnitude on the y-axis, exhibiting a clear passband, transition band, and stopband.
