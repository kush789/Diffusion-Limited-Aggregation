# Diffusion-Limited-Aggregation

An implementation of the Diffusion Limited Aggregation algorithm on a 2D grid with a central point attractor. A detailed description of the algorithm is present [here](http://paulbourke.net/fractals/dla/). We also suggest a technique to estimate the stickiness factor `k` for a given aggregate from a DLA output.

We make an optimization to initialize a new particle at the minimum bounding cirlce of the aggregate, rather than the square boundary of the grid. Proof of correctness for the same (under some assumptions) can be found in the file `Optimization Proof.pdf`

<img src="k=1.gif" width="250" height="250" /> <img src="k=0.5.gif" width="250" height="250" /> <img src="k=0.1.gif" width="250" height="250" /><br />
<br />
Output of our DLA implementation at various number of particles. Stickiness factor 1.0, 0.5, 0.1 respectively.
<hr>

### Setting up
The only requirements are numpy, matplotlib and joblib. A requirements.txt file has been provided. Running the following command should suffice.

`pip install -r requirements.txt`

You can either run the notebooks, or import the `DLA` class from `dlaClass.py` for your experiments.

### Stickiness Estimation

We try to estimate stickiness by trying to find a nice propoerty of the aggregate (in our case, the surface area), which is monotonic and has a high correlation with the stickiness factor. We then try to model this property as a function of the stickiness factor `k`. 

A detailed analysis can be found in `DLA stickiness analysis.ipynb`. Some exapmles of k estimations on unseen aggregates can be found in `Estimate k.ipynb`.

### Simulation Data

We ran 15 simulations for `n` in `range(100, 20001, 100)`, for values of k in linspace(1e-3, 5e-2, 40) and recorded (n, k, surface area) tuples. All this data can be found in the directories `logFiles` and `logFiles2`. We ran 2 simulations where we ranged the number of particles from 100 to 80000. This data can be found in the directory `logFiles80k`.






