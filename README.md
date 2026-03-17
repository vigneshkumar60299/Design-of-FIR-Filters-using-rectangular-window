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


n = 0:N-1;
subplot(2,1,1);
plot(n, h, 'o-');
xlabel('n');
ylabel('h(n)');
title('Impulse Response (Rectangular Window)');
xgrid();

Nfft = 1024;
h_padded = [h, zeros(1, Nfft - N)];
H = fft(h_padded, -1);

f = (0:Nfft-1) / Nfft;

subplot(2,1,2);
plot(f, abs(H));
xlabel('Normalized Frequency');
ylabel('Magnitude');
title('Frequency Response (Rectangular Window)');
xgrid();
disp("Filter Coefficients:");
disp(h(:)');

```



# OUTPUT
<img width="1919" height="940" alt="Screenshot 2026-03-17 134511" src="https://github.com/user-attachments/assets/8051a09a-4dd1-47b7-a4c5-b727a1f3ed2d" />


# RESULT
The FIR filter designed using the rectangular window shows the magnitude response with normalized frequency on the x-axis and magnitude on the y-axis, exhibiting a clear passband, transition band, and stopband.
