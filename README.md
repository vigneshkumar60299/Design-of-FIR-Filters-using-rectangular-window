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

N = 41;                  
wc = 0.4 * %pi;         
alpha = (N - 1) / 2;    

hd = zeros(1, N);

for n = 0:N-1
    if (n - alpha) == 0 then
        hd(n+1) = wc / %pi;
    else
        hd(n+1) = sin(wc * (n - alpha)) / (%pi * (n - alpha));
    end
end

w = ones(1, N);

h = hd .* w;

Nfft = 1024;
h_padded = [h, zeros(1, Nfft - N)];

H = fft(h_padded, -1);

f = (0:Nfft-1) / Nfft;

plot(f, abs(H));
xlabel('Normalized Frequency');
ylabel('Magnitude');
title('Low Pass FIR Filter using Rectangular Window');
xgrid();

disp("Filter Coefficients:");
disp(h);

```



# OUTPUT
<img width="1919" height="935" alt="Screenshot 2026-03-17 132811" src="https://github.com/user-attachments/assets/9e2440db-9412-40f3-95bc-b3640a892837" />


# RESULT
The FIR filter designed using the rectangular window shows the magnitude response with normalized frequency on the x-axis and magnitude on the y-axis, exhibiting a clear passband, transition band, and stopband.
