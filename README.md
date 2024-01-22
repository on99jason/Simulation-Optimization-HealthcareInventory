# Simulation-Optimization-HealthcareInventory
Github Page (R markdown file): https://on99genius.github.io/Simulation-Optimization-HealthcareInventory/

## Introduction
Due to the lack of appropriate preparedness and response plans, many healthcare providers in the US experienced a severe shortage of Personal Protective Equipment (PPE) during the COVID-19 pandemic. Inadequate PPE threatens the safety of frontline medical staff and negatively impacts the quality of care. The level of preparedness to combat unprecedented outbreaks directly depends on proactive planning, strategic thinking, and demand forecasting. 

Massachusetts General Hospital (Mass General) is the oldest and largest teaching hospital of  Harvard Medical School and the third-oldest general hospital in the US, with a capacity of 999 beds. 

## Objective 
Reduce average PPE storage while maintaining a satisfaction rate (98%) by adjusting PPE quantity per order and reorder points. COVID-19 patient data are retrieved from https://healthdata.gov/Hospital/COVID-19-Reported-Patient-Impact-and-Hospital-Capa/anag-cw7u

## Uncertainties
1. The number of COVID-19 patients could change. (e.g., in a large infectious disease outbreak or an epidemic in remission)
2. PPE lead time could change. (e.g., transportation disruptions and production shutdowns, resulting in changes in the timing of the arrival of supplies).

## Simulation (Monte Carlo Simulation)
Monte Carlo simulation is a mathematical technique that allows you to account for risk in quantitative analysis and decision-making. The method is used to model the probability of different outcomes in a process that cannot easily be predicted due to the intervention of random variables. Monte Carlo simulation performs risk analysis by building models of possible results by substituting a range of values - a probability distribution - for any factor with inherent uncertainty. 

After conducting Goodness-of-fit tests to compare the fitness of different probability distributions on random variables, the following probability distributions are found to be the best fit, respectively.

Patient Number - Lognormal Distribution\
Masks Lead Time - Triangular Distribution (1,4,1)\
Gowns Lead Time - Uniform Distribution (4,7)\
Gloves Lead TIme - Uniform Distribution (2,4)

## Optimization & Results
The applied optimization method is DEoptim() in R, which implements the Differential Evolution (DE) optimization algorithm. Differential Evolution is used to perform global optimization on a function within specific bounds. 

|                          | Masks | Gowns | Gloves | 
| ---                      | ---   | ---   | --- | 
| Optimal Reorder Point    | 203   | 378   | 989 | 
| Optimal Reorder Quantity | 182   | 316   | 847 |
| Avg. Inventory Level     | 141   | 231   | 577 | 

