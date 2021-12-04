# Code-To-Plot-Bending-Moment-Shear-Stress-For-Simply-Supported-Beam

Ayaz Shariff

# code to find out bending moment and shear stress acting upon a simple supported bar

import numpy as np

import matplotlib.pyplot as plt

P = 1000

L = 10

a = 5

R1 = P*(L-a)/L

R2 = P*a/L

l = np.linspace(0,L,100)

X = []

SF = []

M = []

%%
for x in l:
    
    if x <= a:
        
        m = R1*x
        
        sf = R1
    
    elif x > a:
        
        m = (R1*x) - (P*(x-a))
        
        sf = (R1-P) #or simplr -R2

    M.append(m)
    
    X.append(x)
    
    SF.append(sf)
    
  
%%
plt.subplot(2,1,1)

plt.plot(X,M)

plt.plot([0,L],[0,0])

plt.title("Bending Moment Diagram")

plt.xlabel("Length in m")

plt.ylabel("Bending Moment in Nm")

%%

plt.subplot(2,1,2)

plt.plot(X,SF)

plt.plot([0,L],[0,0])

plt.plot([0,0],[0,R1], [L,L],[0,-R2]) #([xi ,xi],[yi,yi], [xf,xf],[yf,yf])

plt.title("Shear Force Diagram")

plt.xlabel("Length in m")

plt.ylabel("Shear Force in N")


%%
plt.show()


