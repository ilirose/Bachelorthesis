```
import matplotlib.pyplot as plt
import numpy as np
# Import statistics module
import statistics
# define functions 
# effect sizes
def effect_size(C, N, P, NP, lake): 
    n_pulse = np.log(statistics.mean(N)/statistics.mean(C))
    p_pulse = np.log(statistics.mean(P)/statistics.mean(C))
    np_pulse = np.log(statistics.mean(NP)/statistics.mean(C))
    return np.array([n_pulse, p_pulse, np_pulse])

# standard deviation for every nutrient pulse of a lake
def standarddev(array):
    return np.apply_along_axis(statistics.stdev, 0, array)

#insert data
# OGH 1
OGH1 = np.array([[5.65, 5.95, 6.05], [4.54,3.62,4.65],[4.55,	4.62,	4.86],[10.08,	9.04,	9.4]])
C_OGH1 = OGH1[0]
N_OGH1 = OGH1[1]
P_OGH1 = OGH1[2]
NP_OGH1 = OGH1[3]

# OGH 2
OGH2 = np.array([[8.05, 6.88, 7.72], [7.7, 6.76, 9.26], [11.36, 8.88, 4.62],[11.9, 14.29, 15.85]])
C_OGH2 = OGH2[0]
N_OGH2 = OGH2[1]
P_OGH2 = OGH2[2]
NP_OGH2 = OGH2[3]

# OGH 3
OGH3 = np.array([[3.38, 1.76, 2.17], [3.47,3.34,3.29],[3.16,4.28,3.4],[3.35,	4.42,6.63]])
C_OGH3 = OGH3[0]
N_OGH3 = OGH3[1]
P_OGH3 = OGH3[2]
NP_OGH3 = OGH3[3]

# OGH 4
OGH4 = np.array([[2.48,	2.95,	2.45], [3.39,	3.27,	4.13],[4.18,	6.57,	5.15],[3.87,	5.71,	5.0]])
C_OGH4 = OGH4[0]
N_OGH4 = OGH4[1]
P_OGH4 = OGH4[2]
NP_OGH4 = OGH4[3]

#create arrays with effect sizes
OGH1_es = effect_size(C_OGH1, N_OGH1, P_OGH1, NP_OGH1, "OGH1")
OGH2_es = effect_size(C_OGH2, N_OGH2, P_OGH2, NP_OGH2, "OGH2")
OGH3_es = effect_size(C_OGH3, N_OGH3, P_OGH3, NP_OGH3, "OGH3")
OGH4_es = effect_size(C_OGH4, N_OGH4, P_OGH4, NP_OGH4, "OGH4")

#create arrays with standard deviations
std1 = standarddev(OGH1)
std2 = standarddev(OGH2)
std3 = standarddev(OGH3)
std4 = standarddev(OGH4)

#plot the effect sizes
fig, axs = plt.subplots(2, 2, figsize=(10, 8))  # nrows, ncols

# Colors for N, P, NP data points
colors = ['blue', 'orange', 'green']


# OGH 1
for i in range(len(x)):
    axs[0, 0].errorbar(x[i], y1[i], yerr=std1[i], fmt='o', color=colors[i], capsize=5)
axs[0, 0].set_title('OGH 1')

# OGH 2
for i in range(len(x)):
    axs[0, 1].errorbar(x[i], y2[i], yerr=std2[i], fmt='o', color=colors[i], capsize=5)
axs[0, 1].set_title('OGH 2')

# OGH 3
for i in range(len(x)):
    axs[1, 0].errorbar(x[i], y3[i], yerr=std3[i], fmt='o', color=colors[i], capsize=5)
axs[1, 0].set_title('OGH 3')

# OGH 4
for i in range(len(x)):
    axs[1, 1].errorbar(x[i], y4[i], yerr=std4[i], fmt='o', color=colors[i], capsize=5)
axs[1, 1].set_title('OGH 4')

# Set x-ticks
plt.setp(axs, xticks=range(len(x)), xticklabels=x)

# Set y-label for all subplots
for ax in axs.flat:
    ax.set(ylabel='Effect Size (Log Ratio)')

plt.tight_layout()
plt.show()
```
