I=imread('g1.jpg');
imgray=rgb2gray(I);
figure,imshow(I);
figure,imhist(imgray);
r=0;
g=0;
y=0;
traffic_light='';
z=im2bw(imgray,0.3);


z=~z;
[h,w,s]=size(z);
treshold= floor(h/3);



for i=1:treshold
    for j=1:w
    if(z(i,j)==0)
        r=r+1;
        
    end
    end
end


for i=treshold+1:h-treshold
    for j=1:w
    if(z(i,j)==0)
        y=y+1;
        
    end
    end
end


for i=h-treshold+1:h
    for j=1:w
    if(z(i,j)==0)
        g=g+1;
        
    end
    end
end

figure,imshow(z)

if(r>g&&r>y)
    traffic_light='red';
elseif(g>r&&g>y)
    traffic_light='green';
elseif(y>r&&y>g)
    traffic_light='yellow';
end
traffic_light

