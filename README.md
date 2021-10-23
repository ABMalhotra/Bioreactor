# Bioreactor
This code Creates a time dependent simulator of reactor temperature dependent on 4 heat sources (3 from `ThermalModels` and 1 from `ReactionModels`). The code accounts for coupling between cell growth and the heat generated (i.e. more cells produce more heat). The relevant physical properties of the reactor are stored in `ReactorState`. 

The following assumptions are made in this implementation that can be improved in future,

#### ReactorState:
1. Fluid properties (density, heat capacity) do not change with cell count. In reality, at higher cell counts, effective properties as a mean of fluid and cell properties would be better parameters.

#### ThermalModels:
1. Agitator rpm is constant and generates negligible heat. Can be improved by modeling change in viscosity (as cell count changes), its impact on rpm (if any), using experimental data on the specific agitator being employed.
2. Block is an isothermal source/sink and supplies/removes heat instantaneously. Physical models such as coolant flow, switching between heating and cooling etc can be included.
3. Fresh feed arrives at a constant flow rate. Simulator can include time dependent flow rates in the future.

#### ReactionModels:
1. The heat of reaction is assumed to be exothermic and dependent on number of cells present in the reactor. In reality, it should also be a function of food (glucose) concentration.
2. The heat of reaction is assumed to be constant at all temperatures. Enthalpy as a function of temperature can be implemented using thermodynamic data.
3. Temperature dependence of growth rates is modeled via simplistic approximation (from http://www.pfigueiredo.org/MAI13.pdf). More accurate expressions depending on available microbes and their past performance through machine-learning would be an excellent addition.
4. Cell death is not modelled, i.e. either growth happens from relation described in #3 or no growth happens. In reality, if temperature exceeds a threshold, cells should also die off.


