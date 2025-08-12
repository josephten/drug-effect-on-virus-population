# Drug-effect-on-virus-population
### Project overview

My aim is to Design and implement a stochastic simulation of patient and population dynamics on python and reach a conclusion about treatment regimens based on the simulation results.

### Data sources 

the primary data sources used for this analysis is "ocw.mit.edu" file, containing details about the max probabilty that a virus particle reproduces with and without drugs and probabilty of mutations in a virus particles offspring.

### Tools

Python

### Exploratory data analysis

EDA involved exploring the simulations performed to answer the key question;

- The virus population after using treatment drugs compared to without treatment drugs.

### Data analysis

```Python
def simulationWithDrug(numViruses, maxPop, maxBirthProb, clearProb, resistances,
                       mutProb, numTrials):
   
    import numpy as np
    
    data = np.zeros(300)
    data1 = np.zeros(300)
    for i in range(numTrials):
        virus = ResistantVirus(maxBirthProb, clearProb, resistances, mutProb)
        viruses = [virus] * numViruses
        patient = TreatedPatient(viruses, maxPop)
        virus_count, resist_virus_count = [], []
        for j in range(150):
            patient.update()
            virus_count.append(patient.getTotalPop())
            resist_virus_count.append(patient.getResistPop(['guttagonol']))
        patient.addPrescription('guttagonol')
        for k in range(150):
            patient.update()
            virus_count.append(patient.getTotalPop())
            resist_virus_count.append(patient.getResistPop(['guttagonol']))
        data = data + virus_count
        data1 = data1 + resist_virus_count
    data_avg = data/numTrials
    data1_avg = data1/numTrials

 pylab.plot(list([float('{0:.1f}'.format(i)) for i in data_avg]), label = r'Non-resistant population')
    pylab.plot(list([float('{0:.1f}'.format(j)) for j in data1_avg]), label = r'drug Resistant population')
    pylab.xlabel(r'Number of steps')
    pylab.ylabel(r'Average Virus Population')
    pylab.title(r'Virus Simulation in Patient')
    pylab.legend()
    pylab.show()
```
### Results/findings

Based on the analysis, we found the following:

- the treatment drugs actually increase the virus particles by 1060% on average which is a huge amount.

- the no treatment drugs actually increased the amount of virus particles in the body aswell by also about 1000% on average.

- the virus seems to also spread about the same rate on both the drug and no treatment drugs, this is after around 150 hours for both.

So from this data the null hypothsis sees to be true, that is there is little evidence to suggest that there is a statistical significance between using the treatment drugs or not on the virus particle population.

### Recommendations

As the treatment drugs seem to have very little effect on the amount of virus particles we may need to create a new drug.

### Limitations

Just because the virus population seems to increase about the same with or without the treatment drugs, it doesn't neccearily mean they are both doing the same thing as the drugs could be increasing the virus population from a different virus that is actually healthy for the patient and helping fight off the orginal dangerous virus, and we didn't differentiate this in the analysis
