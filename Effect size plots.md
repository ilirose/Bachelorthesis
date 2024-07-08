The following code has been written to calculate and plot the effect sizes of all bioassays. 

```python
import matplotlib.pyplot as plt
import numpy as np
import statistics

# function for effect sizes
def effect_size(C, N, P, NP, lake): 
    n_pulse = np.log(statistics.mean(N)/statistics.mean(C))
    p_pulse = np.log(statistics.mean(P)/statistics.mean(C))
    np_pulse = np.log(statistics.mean(NP)/statistics.mean(C))
    return np.array([n_pulse, p_pulse, np_pulse])

# standard deviation function for every nutrient pulse of a lake
def standarddev(array):
    return np.apply_along_axis(statistics.stdev, 0, array)

# Bioassay 7.4.
OGH1 = np.array([[5.65, 5.95, 6.05], [4.54,3.62,4.65],[4.55,	4.62,	4.86],[10.08,	9.04,	9.4]])
C_OGH1 = OGH1[0]
N_OGH1 = OGH1[1]
P_OGH1 = OGH1[2]
NP_OGH1 = OGH1[3]

OGH2 = np.array([[8.05, 6.88, 7.72], [7.7, 6.76, 9.26], [11.36, 8.88, 4.62],[11.9, 14.29, 15.85]])
C_OGH2 = OGH2[0]
N_OGH2 = OGH2[1]
P_OGH2 = OGH2[2]
NP_OGH2 = OGH2[3]

OGH3 = np.array([[3.38, 1.76, 2.17], [3.47,3.34,3.29],[3.16,4.28,3.4],[3.35,	4.42,6.63]])
C_OGH3 = OGH3[0]
N_OGH3 = OGH3[1]
P_OGH3 = OGH3[2]
NP_OGH3 = OGH3[3]

OGH4 = np.array([[2.48,	2.95,	2.45], [3.39,	3.27,	4.13],[4.18,	6.57,	5.15],[3.87,	5.71,	5.0]])
C_OGH4 = OGH4[0]
N_OGH4 = OGH4[1]
P_OGH4 = OGH4[2]
NP_OGH4 = OGH4[3]

#Bioassay 22.4.
OGH1_224 = np.array([[5.03, 4.6,4.89], [4.74,4.61,6.1],[3.81,6.23,6.83],[8.85,8.35,12.87]])
C_OGH1_224 = OGH1_224[0]
N_OGH1_224 = OGH1_224[1]
P_OGH1_224 = OGH1_224[2]
NP_OGH1_224 = OGH1_224[3]

OGH2_224 = np.array([[5.93	,5.86	,6.24],[5.86	,5.76	,5.07],[10.64,	14.32	,5.88],[16.8	,23.79	,11.51]])
C_OGH2_224 = OGH2_224[0]
N_OGH2_224 = OGH2_224[1]
P_OGH2_224 = OGH2_224[2]
NP_OGH2_224 = OGH2_224[3]

OGH3_224 = np.array([[8.98,	6.85,	5.53],[7.86,	5.47,	9.45],[8.57,	19.67	,11.11],[10.72, 7.44	,26.34]])
C_OGH3_224 = OGH3_224[0]
N_OGH3_224 = OGH3_224[1]
P_OGH3_224 = OGH3_224[2]
NP_OGH3_224 = OGH3_224[3]
           
OGH4_224 = np.array([[5.26,	4.07,	4.47],[3.65,	4.37,	4.93],[8.89,	8.42	,7.5],[7.97	,8.49	,6.72]])
C_OGH4_224 = OGH4_224[0]
N_OGH4_224 = OGH4_224[1]
P_OGH4_224 = OGH4_224[2]
NP_OGH4_224 = OGH4_224[3]
           
# Bioassay 3.5.
OGH2_35 = np.array([[3.37,3.08,2.6],[3,3.31,3.63],[1.09,4.55,8.01],[6.08,4.62,5.7]])
C_OGH2_35 = OGH2_35[0]
N_OGH2_35 = OGH2_35[1]
P_OGH2_35 = OGH2_35[2]
NP_OGH2_35 = OGH2_35[3]

#create arrays with effect sizes
#OGH1
OGH1_es = effect_size(C_OGH1, N_OGH1, P_OGH1, NP_OGH1, "OGH1")
OGH1_224_es = effect_size(C_OGH1_224, N_OGH1_224, P_OGH1_224, NP_OGH1_224, "OGH1 22.04.2024")

#OGH2
OGH2_es = effect_size(C_OGH2, N_OGH2, P_OGH2, NP_OGH2, "OGH2")
OGH2_224_es = effect_size(C_OGH2_224, N_OGH2_224, P_OGH2_224, NP_OGH2_224, "OGH2 22.04.2024")
OGH2_35_es = effect_size(C_OGH2_35, N_OGH2_35, P_OGH2_35, NP_OGH2_35, "OGH2 03.05.2024")

#OGH3
OGH3_es = effect_size(C_OGH3, N_OGH3, P_OGH3, NP_OGH3, "OGH3")
OGH3_224_es = effect_size(C_OGH3_224, N_OGH3_224, P_OGH3_224, NP_OGH3_224, "OGH3 22.04.2024")

#OHJ4
OGH4_es = effect_size(C_OGH4, N_OGH4, P_OGH4, NP_OGH4, "OGH4")
OGH4_224_es = effect_size(C_OGH4_224, N_OGH4_224, P_OGH4_224, NP_OGH4_224, "OGH4 22.04.2024")

#create arrays with standard deviations
std1 = standarddev(OGH1)
std1_224 = standarddev(OGH1_224)

std2 = standarddev(OGH2)
std2_224 = standarddev(OGH2_224)
std2_35 = standarddev(OGH2_35)

std3 = standarddev(OGH3)
std3_224 = standarddev(OGH3_224)

std4 = standarddev(OGH4)
std4_224 = standarddev(OGH4_224)
print(OGH1_es)

#define the x-ticks
x = ["N", "P", "NP"]

#define the y-vaues
y1 = OGH1_es
y2 = OGH2_es
y3 = OGH3_es
y4 = OGH4_es
y1_224 = OGH1_224_es
y2_224 = OGH2_224_es
y3_224 = OGH3_224_es
y4_224 = OGH4_224_es
y2_35 = OGH2_35_es
```
The plotting of ES for the OGH lakes follows. 

OGH 1: 
```python
#OGH 1
fig, axs = plt.subplots(1, 2, figsize=(10, 4))  # nrows, ncols

# Colors for N, P, NP data points
colors = ['blue', 'orange', 'green']

# OGH 1 07.04.24
for i in range(len(x)):
    axs[0].errorbar(x[i], y1[i], yerr=std1[i], fmt='o', color=colors[i], capsize=5)
axs[0].set_title('A')

#OGH 1 22.04.2024
for i in range(len(x)):
    axs[1].errorbar(x[i], y1_224[i], yerr=std1_224[i], fmt='o', color=colors[i], capsize=5)
axs[1].set_title('B')

plt.setp(axs, xticks=range(len(x)), xticklabels=x)

axs[0].set(ylabel="ES")
    
plt.tight_layout()
plt.show()
```
OGH 2:
```python
# OGH  2
fig, axs = plt.subplots(1, 3, figsize=(10, 3))  # nrows, ncols

# Colors for N, P, NP data points
colors = ['blue', 'orange', 'green']

#OGH2 7.4.
for i in range(len(x)):
    axs[0].errorbar(x[i], y2[i], yerr=std2[i], fmt='o', color=colors[i], capsize=5)
axs[0].set_title('C')

#OGH2 22.4.
for i in range(len(x)):
    axs[1].errorbar(x[i], y2_224[i], yerr=std2_224[i], fmt='o', color=colors[i], capsize=5)
axs[1].set_title('D')

#OGH2 3.5.
for i in range(len(x)):
    axs[2].errorbar(x[i], y2_35[i], yerr=std2_35[i], fmt='o', color=colors[i], capsize=5)
axs[2].set_title('E')

plt.setp(axs, xticks=range(len(x)), xticklabels=x)
axs[0].set(ylabel="ES")

plt.tight_layout()
plt.show()
```
OGH 3: 
```python
#OGH 3 
fig, axs = plt.subplots(1, 2, figsize=(10, 4))  # nrows, ncols

# Colors for N, P, NP data points
colors = ['blue', 'orange', 'green']
# OGH 3 7.4.
for i in range(len(x)):
    axs[0].errorbar(x[i], y3[i], yerr=std3[i], fmt='o', color=colors[i], capsize=5)
axs[0].set_title('F')

# OGH 3 22.4.
for i in range(len(x)):
    axs[1].errorbar(x[i], y3_224[i], yerr=std3_224[i], fmt='o', color=colors[i], capsize=5)
axs[1].set_title('G')

plt.setp(axs, xticks=range(len(x)), xticklabels=x)

axs[0].set(ylabel="ES")
plt.tight_layout()
plt.show()
```
OGH 4: 
```
# OGH 4
fig, axs = plt.subplots(1, 2, figsize=(10, 4))  # nrows, ncols

# Colors for N, P, NP data points
colors = ['blue', 'orange', 'green']

#OGH 4 7.4.
for i in range(len(x)):
    axs[0].errorbar(x[i], y4[i], yerr=std4[i], fmt='o', color=colors[i], capsize=5)
axs[0].set_title('H')

#OGH 4 22.4.
for i in range(len(x)):
    axs[1].errorbar(x[i], y4_224[i], yerr=std4_224[i], fmt='o', color=colors[i], capsize=5)
axs[1].set_title('I')

plt.setp(axs, xticks=range(len(x)), xticklabels=x)

axs[0].set(ylabel="ES")

plt.tight_layout()
plt.show()
```
Below is the data itegration and plotting of the SeeonS lakes.
```
#Effect Sizes für natürliche Seen in SeeonS

#Bansee
ba = np.array([[51.58,51.15,45.43], [51.3,47.72,45.07],[66.62,68.53,54.45],[71.57,72.15,70.52]])
C_ba = ba[0]
N_ba= ba[1]
P_ba = ba[2]
NP_ba = ba[3]

#Brunnsee
br = np.array([[5.01,5.42,4.88], [4.29,5.16,5.33], [7.31,7.59,7.13],[7.03,7.42,7.33]])
C_br = br[0]
N_br = br[1]
P_br = br[2]
NP_br = br[3]

#Klostersee
kl = np.array([[0.42,0.41,0.47], [0.48,0.63,0.54],[1.89,1.26,1.52],[1.87,1.34,2.06]])
C_kl = kl[0]
N_kl = kl[1]
P_kl = kl[2]
NP_kl = kl[3]

#create arrays with effect sizes
ba_es = effect_size(C_ba, N_ba, P_ba, NP_ba, "Bansee")
br_es = effect_size(C_br, N_br, P_br, NP_br, "Brunnsee")
kl_es = effect_size(C_kl, N_kl, P_kl, NP_kl, "Klostersee")

#create arrays with standard deviations
std_ba = standarddev(ba)
std_br = standarddev(br)
std_kl = standarddev(kl)
print(std_ba,std_br,std_kl)

#defining y-values
yba = ba_es
ybr = br_es
ykl = kl_es
```
Now follows the plotting. 
```
fig, axs = plt.subplots(1, 3, figsize=(10, 3))  # nrows, ncols

# Colors for N, P, NP data points
colors = ['blue', 'orange', 'green']

# Bansee
for i in range(len(x)):
    axs[0].errorbar(x[i], yba[i], yerr=std_ba[i], fmt='o', color=colors[i], capsize=5)
axs[0].set_title('J')

# Brunnsee
for i in range(len(x)):
    axs[1].errorbar(x[i], ybr[i], yerr=std_br[i], fmt='o', color=colors[i], capsize=5)
axs[1].set_title('K')

# Klostersee
for i in range(len(x)):
    axs[2].errorbar(x[i], ykl[i], yerr=std_kl[i], fmt='o', color=colors[i], capsize=5)
axs[2].set_title('L')

plt.setp(axs, xticks=range(len(x)), xticklabels=x)
axs[0].set(ylabel="ES")

plt.tight_layout()
plt.show()
```
