# Proposed Methodology for Estimating Marginal Carbon Intensity 

The problem of marginal carbon intensity is framed as fitting a function $y = f(D, X)$ where $y$ is the carbon intensity, $D$ represents demand net of uncontrollable renewables generation and $X$ represents other exogenous variables such as time of day, renewables generation etc. representing the state of the power system. Importantly, we assume that $X$ contains variables which are to a large extent unaffected by changes in $D$.

For a given state $X$, we can then plot $y$ vs. $D$, like so:

INSERT IMAGE

This approach has two important benefits: 

- Non-linear relationships between net demand and carbon intensity can be captured
- An arbitary number of relevant variables can be included in $X$
- The impact of large and small changes in net load $\Delta D$ can be easily calculated

Since this curve depends on many variables which probably cannot be controlled for in $X$, model accuracy is likely to decrease over time (we can verify this). As a result, we train the model in a rolling fashion, on the last month of data. 

Underlying this methodology is the assumption that if we can control for changes in other power system variables, it is possible to calculate the impact that the change in load had on grid carbon intensity. In practice, this is likely to be a non-linear function of the change in load: if load increases enough to warrant an additional generator to be brought online, this may result in a step-change in the carbon intensity, whereas small changes that can be handled by ramping of committed generation can be handled by ramping committed generators.
