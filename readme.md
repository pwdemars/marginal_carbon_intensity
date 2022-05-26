# Proposed Methodology for Estimating Marginal Carbon Intensity 

The problem of marginal carbon intensity is framed as fitting a function $y = f(D, X)$ where $y$ is the carbon intensity, $D$ represents demand net of uncontrollable renewables generation and $X$ includes exogenous variables such as time of day, renewables generation etc. representing the state of the power system. Importantly, we assume that $X$ contains variables which are to a large extent unaffected by changes in $D$. 

For a given state $X$, we can plot $y$ vs. $D$, the carbon intensity curve. The gradient of the line at any point indicates the marginal carbon intensity: 

![Carbon intensity curve](https://raw.githubusercontent.com/pwdemars/marginal_carbon_intensity/main/img/example_curve.png)

Underlying this model is the assumption that if we can control for changes in other power system variables, it is possible to calculate the impact that the change in load had on grid carbon intensity. In practice, this is likely to be a non-linear function of the change in load: if load increases enough to warrant an additional generator to be brought online, this may result in a step-change in the carbon intensity, whereas small changes that can be handled by ramping of committed generation can be handled by ramping committed generators. To represent this, a generalised additive model (GAMs) is used. These models use splines to produce a function which is a linear combination of smooth functions of predictors. GAMs are an attractive approach for this task as the results are interpretable: the marginal impact of any indepenent variable on carbon intensity can be extracted individually. Furthermore, the smoothness can be tuned, offering relatively intuitive results as compared with widely-used black-box methods. 

Overall, this methodology has the following advantages: 

- Non-linear relationships between net demand and carbon intensity are captured
- The method requires only system-level data; no requirement for more granular data on individual generators
- An arbitary number of relevant variables can be included in $X$ to control for 
- The impact of large and small changes in net demand $\Delta D$ can be easily calculated

As a top-down approach, the proposed model does not consider the complex dynamics of generator dispatch. While this is a limitation, bottom-up approaches are less generalisable across sytems due to the substantial data requirements. 

Possible improvements could be: 

- To use a more accurate carbon intensity signal (i.e. that from ElectricityMap!)