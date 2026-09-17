# IIR-FILTER-DESIGN
# EXP 3 A: DESIGN OF LOW PASS BUTTERWORTH FILTER USING BILINEAR TRANSFORMATION TECHNIQUE

# AIM: 
To perform design of Butterworth Filter Using Impulse Invariant and Bilinear Transformation Techniques using SCILAB.

# APPARATUS REQUIRED: 
PC installed with SCILAB. 

# PROGRAM:
```
clc ;
close ;
wp=input('Enter the pass band frequency (Radians )= ' );
ws=input('Enter the stop band frequency (Radians )= ' );
alphap=input( ' Enter the pass band attenuation (dB)=' );
alphas=input( ' Enter the stop band attenuation(dB)=' );
T=input('Enter the Value of sampling Time=');
//Pre warping- Bilinear Transformation
omegap=(2/T)*tan(wp/2);
disp(omegap,'omegap=');
omegas=(2/T)*tan(ws/2);
disp(omegas,'omegas=');
//Order of the filter
N=log10(((10^(0.1alphas))-1)/((10^(0.1alphap))-1))/(2*log10(omegas/omegap));
disp(N,'N=');
N=ceil(N);
disp(N,'Round off value of N=');
//Cut off frequency
omegac=omegap/(((10^(0.1alphap)) -1)^(1/(2 N)));
disp(omegac,'omegac=');
disp('Normalised Analog LPF Transfer function H(S)=');
hs_Normalised = analpf(N,'butt',[0,0],1);
disp(hs_Normalised);
disp('Analog LPF Transfer function H(S)=');
hs= analpf(N,'butt',[0,0],omegac);
disp(hs);
z=poly(0,'z');//Defining variable z
Hz=horner(hs,(2/ T)*((z -1)/(z+1)))// Bilinear Transformation
disp('Digital LPF Transfer function H(Z)=');
disp(Hz);
HW=frmag(Hz,512); // Frequency response
w=0:%pi/511:%pi ;
plot(w/%pi,abs(HW));
xlabel(' Normalized Digital Frequency w');
ylabel('Magnitude ');
title(' Frequency Response of Butterworth IIR LPF');
```

# CALCULATION:
<img width="899" height="1599" alt="WhatsApp Image 2026-09-15 at 08 51 27" src="https://github.com/user-attachments/assets/921b141d-e2e2-4e59-b661-f178d5371d0c" />
<img width="899" height="1599" alt="WhatsApp Image 2026-09-15 at 08 51 33" src="https://github.com/user-attachments/assets/c12554c4-23a1-4ffe-b472-2eea563dfbfa" />
<img width="899" height="1599" alt="WhatsApp Image 2026-09-15 at 08 51 37" src="https://github.com/user-attachments/assets/ee24bfc4-6eb5-474f-a806-b19e3efbaad4" />




# OUTPUT: 
<img width="1600" height="898" alt="WhatsApp Image 2026-08-08 at 08 49 55" src="https://github.com/user-attachments/assets/28bccdd2-691b-40c3-8862-aed108f7d60e" />

<img width="1600" height="901" alt="WhatsApp Image 2026-08-08 at 08 47 54" src="https://github.com/user-attachments/assets/741c1a0b-682b-4e9d-a521-5593265505ab" />

# RESULT: 

Thus, design of Butterworth Low pass IIR filter waveforms were plotted and output was verified.

