# PHYS-330 - Classical Mechanics - Fall 2017

## Homework 2

#### problem 3 hints

The following is a python code snippet which I used to find theta for max range.

there are two parts.  The function range calculates the range for a given theta.  The next part is a loop which does a search (like a binomial but different) to find the theta which gives the maximum range.  You can get this code working by editing one line of code indicated below.  

```python
import scipy.optimize as sci

def range(theta):
    # this function returns the range  of the projectile for a given theta
    vter = 1.0  # set units
    g = 1.0     # given in problem
    v0 = 1.0    # initial velocity

    def func(x): #this function return value of equation 2.39 in book
        return #you neeed to edit this#

    tau = vter/g
    v0x = v0*np.cos(theta) # x component of velocity
    v0y = v0*np.sin(theta) # y component of velocity
    return sci.newton(func,x0=.5,tol=1.0e-12)  #return root of equation 2.39


#below is a simple script which is reminicient of a binomial search
thetamax = np.pi # we know theta can't be this big to maximize R
thetamin = 0.0   # initializing theta
step = .01
flag = True      # change this to exit loop when we have found R
R = 0             # initial range.This will change as we find larger R
while flag == True:
        theta = thetamin + step  # update to new theta to test
        Rnew = range(theta)      # calculate range for current theta
        if Rnew < R:             # if xnew is less than current range
            step = step/2.0           # decrease step size
        else:                    # otherwise check rel error from previous theta and current theta
            if np.abs(theta-thetamin)/theta < 1.0e-10: # if relative error small enough stop
                print("theta for max displacement =",theta, "rad")
                flag = False
            else:     # otherwise update thetamin and new range
                thetamin = theta
                R = Rnew

```
