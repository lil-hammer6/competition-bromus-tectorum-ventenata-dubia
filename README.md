### Clash of the Invaders: Competition Dynamics of Bromus tectorum and Ventenata dubia in an Addition Series Study
- Repository contains the analysis for paper https://doi.org/10.1002/ece3.71458
- Analysis was done using R Markdown

### About the project
- Competitive interactions between co-occurring invasive species can have detrimental impacts on native communities and cause counter-effective responses to management.
- The goal of this research was to elucidate competitive dynamics between Bromus tectorum and Ventenata dubia, two invasive winter annual grasses found in the western United States.
- Plants were grown in a full-factorial addition series design in the greenhouse for 10-weeks after which we recorded aboveground per capita biomass.
- We quantified:
  1. intraspecific competition on B. tectorum and V. dubia as the density of conspecifics increased
  2. interspecific competition between the two at varying proportions
 - We derived the intraspecific and interspecific competitive effects on each species with a nonlinear analysis and used these coefficients to determine relative competitive ability (RCA).
 - This was done using the nls package in R.
### Our models
- Models were based on the work by Spitters (1983), and Firbank and Watkinson (1988) 

We first determined mean biomass per plant when grown along a density gradient in monoculture. Where mean yield per plant (w) can be described by the equation:

w = w_m ( 1 + \alpha N)^ {-b} 
- w_m is the was the mean biomass of individuals grown alone
- \alpha was the area required to reach the biomass w_m
- N was the total density of plants at harvest
- b is thought to be the mean species-specific resource use efficiency
  
We then determined the mean biomass per plant when grown at increasing density and different proportions. Where mean biomass per plant of B. tectorum (w_B) or V. dubia (w_V) can be described by the equations:

w_V = w_{mV} ( 1 + \beta_{V}(N_{V}+ \alpha_{BV}N_B))^{-b_{V}}

w_B = w_{mB} ( 1 + \beta_{B}(N_{B}+ \alpha_{VB}N_V))^{-b_{B}}

where 
- wm_B was the mean biomass of B. tectorum individuals grown alone, 
- \beta_B was the slope of B. tectorum intraspecific competition, 
- \beta_V was the slope of V. dubia intraspecific competition, 
- \alpha_BV was the competition coefficient of the impact of V. dubia on B. tectorum, 
- \alpha_VB was the competition coefficient of the impact of B. tectorum on V. dubia, 
- \N_B was the density of B. tectorum at harvest, 
- \N_V was the density of V. dubia at harvest, and 
- b_B was thought to be the mean species-specific resource use efficiency of B. tectorum 
- b_V for V. dubia

- We first derived \alpha and b from Equation 1 using nonlinear least squares methods for our two species when grown in monocultures.
- We performed diagnostic tests and, due to heteroscedasticity of our data, filtered extreme outliers (defined as values outside of 1.5 times the interquartile range, i.e., outside of 95% of observations)
- Models were then refit with a natural log transformation.

- To determine the density thresholds at which species B. tectorum and species V. dubia demonstrated 50% and 75% reductions in biomass, we derived these thresholds from the models.
- Thresholds were calculated using the estimated parameters of the model and back transformed.
- Confidence intervals for the thresholds were obtained by propagating uncertainty in the parameter estimates through the back transformation process.

We then determined the RCA (Spitters, 1983; Rousch et al., 1989) using the intraspecific and interspecific competition coefficients using the equations:

RCA_B = \beta_B/\alpha_{BV}
RCA_V = \beta_V/\alpha_{VB}

- Relative competitive ability can be interpreted as the density equivalence between species. 
For example, if RCAB is 0.5, it would take two individuals of V. dubia to equal one individual's biomass of B. tectorum.

### Key results 
- Both species were more strongly impacted by interspecific competition than intraspecific competition, though neither species had an advantage over the other.
- We found that both reduced the other's biomass with similar number of individuals, ~1 for a 50% reduction in biomass and ~3.5 individuals for a 75% reduction, as the confidence intervals were overlapping.
- Bromus tectorum individuals were heavier than V. dubia, and mean weight did not differ much with intraspecific or interspecific competition.
- In contrast, V. dubia was half the weight when in interspecific versus intraspecific competition.
- Intraspecific competition impacted each species, except that V. dubia had a stronger impact on itself (conspecifics), with only two individuals required to reduce its own biomass by 50% compared with eight individuals for B. tectorum.
- Insight into the competitive interactions between these co-occurring invasive species provides vital information to inform management and how the invasion may change in the future.
- As our climate continues to change, new species will be interacting and new management responses will be needed: conducting an additive design study would help inform us of the patterns of these new interactions.
