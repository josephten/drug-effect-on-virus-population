# drug-effect-on-virus-population
###Project overview

My aim is to Design and implement a stochastic simulation of patient and population dynamics on python and reach a conclusion about treatment regimens based on the simulation results.

###Data sources 

the primary data sources used for this analysis is "ocw.mit.edu" file, containing details about the max probabilty that a virus particle reproduces with and without drugs and probabilty of mutations in a virus particles offspring.

###Tools

Python

###Exploratory data analysis

EDA involved exploring the simulations performed to answer key questions such as;

- The percentage of patients cured using treatment drugs compared to without treatment drugs.
- Number of patients cured if there was a delay in the treatment.

###Data analysis

```Python
 pylab.plot(list([float('{0:.1f}'.format(i)) for i in data_avg]), label = r'Non-resistant population')
    pylab.plot(list([float('{0:.1f}'.format(j)) for j in data1_avg]), label = r'drug Resistant population')
    pylab.xlabel(r'Number of steps')
    pylab.ylabel(r'Average Virus Population')
    pylab.title(r'Virus Simulation in Patient')
    pylab.legend()
    pylab.show()
```
###results/findings
Based on the analysis, we recommend the follwoing
