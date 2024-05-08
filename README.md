close all;
clear all;
[yy,fs]=audioread('C:\Program Files\MATLAB\MATLAB Production Server\R2015a\bin\work\data\1-11.wav');
yy=yy./(1*.01*abs(max(yy)));
yy1=yy(241:400);
N=160;
w=hamming(N);
y=yy1.*w;
% //computing cepstrum
y11=fft(y);
y1=log(abs(y11));
y2=ifft(y1);
figure;
subplot(2,2,1);
plot(yy1);
xlabel('sample index');
ylabel('amplitude');
title('s(n)');% speech segment with 20msec
subplot(2,2,2);
plot(y);
xlabel('sample index');
ylabel('amplitude');
title('x(n)');%windowed speech segment
subplot(2,2,3);
plot(y1(1:80));%log of |X(W)|
xlabel('sample index');
ylabel('amplitude');
title('log|X(W)|');
subplot(2,2,4);
plot(y2(1:80));%IDFT of log|X(W)| i.e cepstrum
xlabel('sample index');
ylabel('amplitude');
title('c(n)');
