# nonlinear-pendulum
import numpy as np
from scipy import special
import matplotlib.pyplot as plt

phis = np.linspace(0, np.pi)

def T(phi):
    return 4*special.ellipk(np.sin(phi/2.0)**2)
                    
ts = T(phis)
 


plt.xlabel("phi0", size = 18)
plt.ylabel("T", size = 18)
plt.ylim(0,30)
plt.plot(phis, ts)


def psi(t, phi0):
    return special.ellipj(t, np.sin(phi0/2)**2)[3]

def sinepsi(t, phi0):
    return special.ellipj(t,np.sin(phi0/2)**2)[0]

def phinorm(x,phi0):
    return 2*np.arcsin(np.sin(phi0/2)*sinepsi(x*T(phi0), phi0))/phi0

phi0 = np.linspace(0.1, 1, 5)*np.pi
x = np.linspace(0,1,5)
flist = [lambda x: phinorm(x, phi0[i]) for i in range(5)]


flist[0]
