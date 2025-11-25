# EXP 6 : SPEECH RECOGNITION USING SCILAB

**NAME   : NANCY CAROLEINE P R**

**REG NO : 212223060181** 

## AIM: 

To perform and verify multirate DSP without function using SCILAB.

## APPARATUS REQUIRED: 
PC installed with SCILAB. 

## PROGRAM : 
## DECIMATION
```
// Parameters
N = 100;              // Number of samples
f = 0.05;             // Normalized frequency (cycles/sample)
n = 0:N-1;            // Discrete time index

// Generate discrete sine wave
x = sin(2 * %pi * f * n);

// Decimate by factor M = 3
M = 3;
x_dec = x(1:M:$);      // Keep every 3rd sample
n_dec = n(1:M:$);      // Corresponding time index

// Compute FFT
X = fft(x);                    // FFT of original signal
X_dec = fft(x_dec);            // FFT of decimated signal

// Frequency axes
f_axis = (0:N-1)/N;            // Normalized frequency for original
N_dec = length(x_dec);
f_axis_dec = (0:N_dec-1)/N_dec; // For decimated signal

// === Plot all 4 in one figure ===
scf(0);
clf();
subplot(2,2,1);
plot2d3(n, x, style=5); // stem plot for original signal
title("Original Discrete-Time Sine Signal");
xlabel("Sample Index n");
ylabel("Amplitude");

subplot(2,2,2);
plot2d3(n_dec, x_dec, style=5); // stem plot for decimated signal
title("Decimated Signal (Factor 3)");
xlabel("Sample Index n");
ylabel("Amplitude");

subplot(2,2,3);
plot(f_axis, abs(X));
title("Frequency Spectrum of Original Signal");
xlabel("Normalized Frequency");
ylabel("Magnitude");

subplot(2,2,4);
plot(f_axis_dec, abs(X_dec));
title("Frequency Spectrum of Decimated Signal");
xlabel("Normalized Frequency");
ylabel("Magnitude");

```
## INTERPOLATION
```
// Parameters
N = 100;              // Number of original samples
f = 0.05;             // Normalized frequency (cycles/sample)
n = 0:N-1;            // Discrete time index

// Generate discrete cosine signal
x = cos(2 * %pi * f * n);

// Interpolation by factor L = 2
L = 2;
x_interp = zeros(1, L * N);
x_interp(1:L:$) = x;  // Insert original samples, zeros in between

// Optional: Apply low-pass filter to smooth interpolated signal
// Simple FIR filter (moving average)
h = [0.5 0.5];  // 2-tap averaging filter
x_interp_filtered = conv(x_interp, h, 'same');

// New time index for interpolated signal
n_interp = 0:(L*N - 1);

// === Compute FFT ===
X = fft(x);                          // Original signal FFT
X_interp = fft(x_interp_filtered);   // Interpolated signal FFT

// Frequency axes
f_axis = (0:N-1)/N;
f_axis_interp = (0:length(x_interp_filtered)-1)/length(x_interp_filtered);

// === Plot all 4 in one figure ===
scf(0);
clf();
subplot(2,2,1);
plot2d3(n, x, style=5);
title("Original Discrete-Time Cosine Signal");
xlabel("Sample Index n");
ylabel("Amplitude");

subplot(2,2,2);
plot2d3(n_interp, x_interp_filtered, style=5);
title("Interpolated Signal (Factor 2)");
xlabel("Sample Index n");
ylabel("Amplitude");

subplot(2,2,3);
plot(f_axis, abs(X));
title("Frequency Spectrum of Original Signal");
xlabel("Normalized Frequency");
ylabel("Magnitude");

subplot(2,2,4);
plot(f_axis_interp, abs(X_interp));
title("Frequency Spectrum of Interpolated Signal");
xlabel("Normalized Frequency");
ylabel("Magnitude");


```

## OUTPUT: 

**DECIMATION**

<img width="1920" height="1080" alt="Screenshot (390)" src="https://github.com/user-attachments/assets/2216c44f-58d3-41ba-b1fd-b679b1ff008f" />

**INTERPOLATION**

<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/e1bc029f-26e1-4054-9b05-98837b3a83a1" />

## RESULT: 
Thus the decimation process by a factor M and interpolation process by a factor L using 
SCILAB was implemented. 
