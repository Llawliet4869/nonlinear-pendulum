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
