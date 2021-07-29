Earthquake, is one of the most devastating disasters in nature, especially in California. The left figrue shows the historic earthquakes with magnitude larger than 5.5 in the last 250 years. The eartqhuakes, especially these largest ones, can destroy even the most resistent buildings.  Particularly, the building response to ground shaking is closely associated with the frequency of seismic waves.  However, seismic records are oftentimes sparse for the extreme earthquakes near the fault. Therefore, determinstic, and sometime stochastic simulations are valuable to supplement the data, which is helpful to unveil underlysing physics, predict ground motion amplitudes, and most importantly, alleviate seismic hazard.



In terms the relationship between earthquake and frequency, for example, taller buildings are most sensitive to longer-period shaking; but the short buildings are most sensitive to high-frequency waves. Conventionally, researchers use deterministic methods for frequency below 1 Hz or so, and  duo to the exponentially increasing computational cost with frequency, stochastic methods are routinely applied for higher freqeunceis. With the advancement in computational resources these years, we are not capable of extending the frequency limit of physics-based determinstic simulations. 



Specifically, we face high-frequency challenges in the entire process of earthquake rupture and propagation, including source, path and site effects. They are generally of different spatial scale. We will talk about these three effects one by one.



First, we look at the path effects, including various model characteristics, like shallow low velocities, topogrpahy, anelastic attenuation. We start with the shallow low velocity.



In order to perform numerical simulations, we will need a reliable velocity model. The SCEC maintains a few state-of-art community velocity models (CVMs), containing P-wave velocity, S-wave velocity and density.  Among these CVMs, we use the CVM-S4.26M01, or CVM-S in short, which yields the best fit acording to Taborda et al's study in 2016. This map shows. the surface Vs from CVM-S. Blue means large velocities, up to 4650 m/s in this domain, and there are a bunch of low velocities in the basins. These CVMs are botained by incorporating verious source of measurements, including geological and geophysical measurements,  empirical rules, and tomography studies. The geological and geophysical measurements are the most accurate, but limited to certain regions, mostly very shallow basins. And the CVM-S cuts off this geotechnical layer at 350 m depth.  The empirical rules are relatively less accurate, but can be applied to a wider domain. mostly the deeper basins.The tomographiy studeies are of the largest scale, but typically have lower resolution,, especially near the surface.



With the velocity model, we will extensively study the 2014 M5.1 La Habar earthquake. This event was selected for a few reaons. First, it occured in the Los Angeles Basin, one of the most populated, and thus seismic  vulnerable areas. Second, it's of a moderate magnitude, so that we can ignore the nonlienar effects, which will otherwwise complicates our modeling. Third, we have a nice data coverage for this event, from 259 strong motion stations. 



This figure shows the velocity profiles for all the 259 stations, which obviously can be divided into two types, type A sites with low near-surface Vs, below 500 m/s; and type B sites with much larger surfcae Vs over 1500 m/s. Note that we are in Southern California, and here didn't experience any glacier striping, so there ought to be some weathered soil layers near the surface, which are unlikely to have such large surface Vs. Moreover, the profiles at type B sites remain constant in the top 500 m, which indicates appor constraints in the CVM-S, which is also supported by the location map that most type B sites are outside of the central basins, and we have sparser measurements in these regions.



The question is, if it is true that the velocities at type B sites are just that high? We simulated the ground motions and calculated the spectral accelerations at these sites up to 1 Hz. Here 1 Hz is chosen to avoid higher-frequency effects. The black curves depict the records, and blue curves for the simulations results. We do have a good fit at type A sites, and obviously type B sites are storngly underpredicted at freueqncy as low as 0.2-0.3 hz. It's completely ourside the 95% confidence interval. So there is veyr likely inaccuracy in the velocity model that causes this discrepancy. 



Reserachers have noticed the unrealistically high near-surface Vs and proposed several methods to constrain the shallow velocities, e.g. using the tiem-avearge Vs in the top 30 m, or Vs30. Ely et al in 2010 proposed a method to taper the velocity down to 350 m, to match the generic rock profiles reported in the literature. Their method has two important parameters, taper depth zt and vs30 from Vs30 maps. note that the Vs30 values in this domain do not exceed about 720 m/s, which is far less than the 4650 m/s we saw in the CVM-S.



There are, a few potential improvements for this method. FOr example, the taper depth of 350 m is determined by qualitive comparisons using the 2008 Chino Hills Eartqhauke. We would like to quantitatively evaluate this taper depth. Second, their. method always overrides the orignal shallow profiles. However, we have mentioned that in some regions, especially within the basins, the original profiles are obtained from geological and geophysical measurements, which are likely more accurate than the Vs30. So it would be ebetter to keep these geotechnical layers from being overwritten by the taper funciton.  Third, Ely et al 2010 used a Vs30 map generated 15 years ago, which is kind of outdated now. 

Among these three potential improvements, the third one is straightforward, and we will talk about the first two. 



Our goal is to determine the optimal value for zT and avoid overriding the profiles with good constraints. Therefore, we explore the profiles with different taper depths from 200 m to 1500 m. As you can see, the taper function always reduce the shallow velocities, because the Vs30 is always smaller than the surface Vs at ypte B sites from CVM-S. The larger zT is, the more velocity reduction is, though the reduction gradually gets saturated. For type A sites, however, we have to treat the profiles differently.  The idea is, whenever we encounter velocities in the CVM-S that are smaller than the taper profile,  for example, this dashed line of 1000 m taper depth, we leave the lower CMV-S velocities unchanged. In this way, the calculated profiles will not override the geotechinally-constrained low velocities.   We can also observe the sharp contrast at 350 m,  which is due to the mathematical processing when merging the geotechnical layer with the deepter velocity model in the CVM-S.  Now, we have the idea of modifying the probably inaccurate velocities, without losing the geotechnical information, the next step is to evaluate this method.



Before diving into the expensiive numerical simulations, it's betteer to conduct cheaper theoretical analysis. Let me briefly introduce a simplefied theoretical method, called SH1D, which will be used a lot in the subsequent sections. For a single site, we roughly know the subsurface shallow structure from direct or indirect measurements. For example, we know the surface sand layer is underlain by a gravel layer and then sand layer again, and the competent rock below the bedrock depth.The corresponding velocity profiles may look like these depth-dependent curves. If we have seismometers at both the surface and downhole site, we will find that the ground motions can look quite different within just a few hunderd of meters. This is called site amplification. and we use the SH1D solution to quantitatively describe this effect.



We stick with this layered, homogeneous approximation of the subsurace structure,,, and we assume a unit input pulse source from the bottom in the half space. We consider the horizontally polarized SH waves that propagate vertically through the layers and excite the ground motions at the surface. The resulting spectraum can be calculated theoretically, and the ratio between the sepctra at the surface and the downhole is called transfer funciton, which describes how seismic waves are modified by these horiizontal homogeneous layers. The advantage of this approach is it's very compuatioanlly inexpensive, yet it is sufficient to approximate the site response.  



We perform the Sh1D model and calculate the trasnfer functions for various taper profiles and CVM-S. The response ratio betwen these two represents the effects of tapering the velocity profile from CVM-S. The figure in the bottom shows the spectral ratio corresponding to the velocity profiles in the top panel. We see that greater taper depths leads to more velocity reduciton and thus stronger amplification. 

We also notice the de-amplification at type A sites, which we attribute to the presence of the sharp contrast at 350 m depth. As the taper depth increases, we will have a smoother transition at this depth, and thus less de-amplifcaiton 



To determine which taper depth if better in fitting the data, we superimpose the SH1D response ratio to the 3D simulation using the original CVM-S. The figure in the bottom shows the bias between various taper depth and the data. Positve values mean overprediction and negative for underprediction. Obviously, type B sites are strongly underprediceted with the original CVM-S,  as shown by the black curve, and a taper depth of about 500 - 1000 m will greatly improve the fit. In addition, we don't chagne much the fit at type A sites, as expected from the velocity profiles



With the guidance from the 1D analysis, we performed 3D simulatiosn using three taper depths, 350 m, which is the default taper depth in Ely et al 2010, as well as 700 and 1000 m. Consistent with the 1D analysis,  we don't see much change at type A sites,  but for type B sites, significant improvements are achieved by a 700 to 1000 m taper depth. After calculating the average bais, we find that the 1000 m taper depth yield the best overall fit. 



here we look at the PGV bias map for these 3D simulations. Blue means underprediction and is widely observed in the original CMV-S model. As the taper depth increases, the blue regions disappear,indicating an improvement in the fit. Nonehteless, we notice some spatial variability, For example, the San Bernardino Basin gets over predicted by the 1000 m of even the 350 m taper depth, which suggests a shallower low velocity layer. On the other hand, the west part of the Santa Ana Mountains still shows some underprediction and may suggest a even deeper taper depth than 1000 m. 



The conclusions. CVM-S tends to underpredicte the FAS at poorly-constrained type B sites, which is greatly imporved with our proposed velocty taper method. at the same time, we retain thee god fit at well-constrained type A sites. A uniform 1000 m taper depth is found to yeild the best fit, though some spatial. variability may further improve the method. Finally, the SH1D model serves as a good approximation for shallow low-velcoity effects.



With the tapered velocity model, we move to high-frequncy deterministic simulations, upt o 5 Hz, to explore these features,about how they affect ground motions, and trade off with each other. 



We first clarify the simulations parameters. The osurce is from Graves and Pitarka kinematic rupture generator 2016. We took an ensemble of 40 realizations and selected the one that best fits the Spectral accelerations within about 30 km from the source. We will investigate these features in turn, minimum veloloity, velocity taper, topgoraphy, anaelistic attenuation,.



Here is a movie of the amplitude of Vx in a ground motion simulation.

We can see that topgoraphy tends to scatter the seismic waves and causes more ripples. Also, seismic energy is trapped within the low-veloity basin, look at this edge, characterized by the strong velocity  constract 



We revist the low velcity effects due to the taper method, up to a higher frequency. The blue curves denote the mdoel with 1000 m taper depth and the red curve has no velocity ptaer. As expected from previous discussion below 1 Hz, the taper method reduces the shallow velocity and tends to ampilfy the PGV,  especially at farther distance, where most type B sites locate. the DUR is much less affected by the taper method. Also, the low velocity effects due to the taper are more remarkable at higher frequency .





Apart from the low veocity introducted by the taper method to take care of the unrealistically high velocities, there is another case of low-velcoity effects. Due to the computational limits, we have to leave out the lowest velocities in the mesh. Because to maintain sufficeintly  resovleable freqeuncy, we have to reduce the grid spacing for lower velocities. For example, reducing the minimum Vs from 500 m/s to 200 m/s will increase the compuational cost by 40 times. Therefore, we lamped the minimum Vs at 500 m/s, and used the SH1D model to represent the low-velocity effects.  In our siimulations, we use the velocity profiles denoted by this blue curve, though we know there are som elower velocities, denoted by this red curve. We calcutlet the Sh1D response ratio between these two curves and convolve with the3D simulation results at alll sites.  The green curve shows the convolved synthetics. We seee that compard to the orignal 3D simulation, this 1D correction can increase PGV by bout 32, but leave the wveformes almost unchanged. from the Fouerie amplitude spectra, we see that the 1D coreciton increase the groudn motion above about 0.8 Hz. 



Next, we show topographic effects. These maps show percent difference between the model. with topography and without topograpahy. The three rows are for PGV, DUR, and Arias intensity. And the three columns are for different freuquency bands. Red means amplification and blue means deamplification. So, topgoraphy tends to increase the PGV at mountain tops, and increase the DUR even below 1 hz. Particularly, the near-source regions experiences strong increase in the DUR, which is due to the presence of north end of the Santa Ana Mountains, whcih scatters and reflects the seismic wavs.  Finally, we observe energy accumulation at the front side of the mountains, and reductino on the other side.



What if the topography is couled with low velocities? Here is a density histogram of percent difference in PGV and topographic curvature. The top right corner means more amplification at steep areas, and the bototm left corner means deamplificaiton at flat areas. As we showed just now, topography tends to amplify ground motinos at mouttain tops, but previous studies tended to underestiamte such amplifcaiotn compared to recorded data. Here we provide a possible explanation. 



With the velocity taper, there are more low velcities near the surface, which represent the weathered soil in the mountain areas. As a result, the trend of amplification becomes more significant, which means the near-surface low velocities enhance the topographic amplification as the curvature increases.  This may partly explain why previous studies failed to predict the topographic amplification, because they didn't consider the shallow low velocitie in the mountain areas. 



The Anelastic attenuation, is another key parameter that contorls the ground motions. The quality factor Q is used to describe how much eneryg remains during propagation. A smaller Q means more energy loss of stronger attenuation. First, Q is typically a funciton of Velocity, There are various formulat for Qs-Vs relationship, the the common rule is that Qs increases with Vs, which means stiff rocks have larger quality factor and thus less attenuation. Q is also a fucntion of frequency. Normally, it is assumets that Q increases exponentially as freuqncy above some threshold, e.g. 1 hz. The power-law exponetn, gamma, remains somewhat uncertain up to now. With different Q models, the resulting groun motions can look very differently. We see that the commonly used gamma of 0.6 or larger seems to be incompatible with the data, and actually smaller Q fits the data better, especially for the horizontal components. 



Conclusions. We confirm that the low velcoities have significant influence on ground motions, and propsoed two approaches to account for low-velocity effects, both of them will increase the ground motion amplitudes.  Topography tends to increase the DUR within the basins, and in this case specifically near the source. It also inrease the PGV at mountain tops,  which is further enhanced by the presence of low velcoities.  As for the anealstic attenuation, we found that the commonly used power-lay exponent of 0.6 seesm to be too large according to the records. 



With so many words about shallow velocity structure, it seems we are ready for the site response. But hold on, we will discuss the larger-scale, lower-frequncy source effects first and leave the very high-frequency site effects to the end. Specifically, we will talk about the near-source plasticity, and propose a method, called EKS to emuilate nonlinear effects in the fault zone



We are very used to linear deformation, which means strain incresae proportionally with stress. Howeve, when the load exceeds some threshold, the strain may increase rapidly with little increse in stress. this is called plastic yielding. Our Finite difference code, AWP, implemented a trucker-prager plasticity machanism. Within the yield surface, the deformation is linear; on and outside the yield surface, the deformation is plastic, which means if the load is removed, the materials don't reverse back to their original status.  Roten et al. in 2017 performed a suite of dynamic nonlinear simulations and found that plastic yielding of hte fractured rocks in the fault zone may lead to off-fault deforamtion and shallow slip decificit, which are conssitent with the observations. 



If we look at the Peak Slip Rate on the fault using linear and onlinera simulations for an M7.8 scenario on the SAF, it's noticable that the plasticity changes the slip pattern. The blue curves show the PSR at the surface. Note the different scale. It's obvious that the linear case generates much larger slip rates and the nonlinear, especially the wesker Shale rock case, reduces the shallpw slip rate and thus slip on the shallow fault. The faultzone nonliearity is important for seismic hazard, but the problem is nonliearity is only supported in dynamic simulations, which are much more expensive than the kinematic simulations, which consider motions only 



We are very used to linear deformation, where strain increase proportionaly with stress. However, when the load exceeds some threshold, they strain may increase rapidly with littl increase in the stress. This is called plastic yielding. If the load is then removed, the material doesn't reverse back to its orignal status. Roten et al. in 2017 simulated a suite of dynamic nonlinear simulaitons and found that plastic yielding in the fault zone leads to off-fault deformation and shallow sli pdeficit, which are consistent with the observations. 



We performed linear and nonlinear simulations for a M7.8 scenario on the SAF. It's obvious that the plasticity changes the slip pattenr. The blue curves are the peak slip rates at the surface, note the diderent scales. The linear moel generates much larger PSR, and the nonlienra, especialy the weaker shale rock case, reduces the PSR and thus the slip on the fault. 

This fault zone nonlinearity is important for seismic hazard, but the problem is the plasticity is only supported in dynamic simulations, which is much more expensive than the kinematic simulations, which consider partical motions only.



It motivates us to invesitage an approach to account for plasticity in kinematic simulations. We plotted the avearged PSR along the strike for. the linear and onlinear models. It's clear the Shallow slip deficit occurs mainly in the shallow crust and the ratios between the nonlinera and linear models are similar between sandstone and shale. By trial and error, we found that the ratio curve can be approximated by a function of geological strength index and a normalization depth. This motivates us to scale the slip rate in the linear simulations to emulate the plastic effect.



The detailed procedure is shown in this figure. GIven the rock type and the depth of a subfualt, we can calculate the fitting ratio at this subfault, then we use a gaussian shape taper window to scale thesource time function.. This is our equivalent kinematic source. Considering the similarity between the EKS and nonlinera model, we would expect similar ground motions to be predicted. 

This figure shows the PGV maps for linear, nonlienra and EKS model. We can observe the reduction of PGV in the nonlinear and EKS model, which is quantitatively shown in these density histograms. At a certain occurence frequency, the linear model has the largest PGV, and the EKS model well predicted the PGV reduction for the nonlinear model.  This is also observed if we zoom into the LA basin specifically.



We can also plot the SA for these models at different periods. Similar reduction is observed for the nonlinear mdoels, and again well reproduced by the EKS model. The 2 s seems not a real high frequency, but with nonlinearity, we can onlyl afford to run dynamic simulations up to this freuqency limit, which is the reason why we need an EKS model. 



Furthermore, we also tested different rupture direction, as it may cause significant change on the ground motions according to literataure. These two figures show that, however, our EKS model still works well if the rupture direction is reversed.



Conclusions. The near-fault plasticity reduces the slip rates and thus slip on the fault, especially for the weaker rock case. This important nonlienar effect can be emulated by scaling the slip rate time histories. Our proposed EKS model is able to reproduce the ground motion reduction robustly for different rock strengths and rupture directions, while saving the compuational expense. 



Finally, we arrive at the site effects. There is an old saying in China, that "Covering ninety miles is still half-way to a one-hundred mile journey", this is very true for this talk, for my PhD, and for seismic waves. The very shallow few hunderds of meters structure can generate equally important influence

 Specifically, we will talk about the site effects due to the 3D velocity heterogeneities.



We first look at a Japanese site in Honbetsu, TKCH05. It belongs to KikNet site array, which has detailed geological dtructure and seismic records at both the surface and downhole site. Traditionally, people use SH1D model to predict thee site response, which in this case, fails to match the observed empirical transfer function, especially for the first peak. 

What's the reason behind it?  Remember the assumption in SH1D solution that the subsurface sturecture is composed of horizontal homogeneious layers. However, we recognize that the subsurface velocity strcuture has some lateral variations, which is likley relevant with the surface geomorphy, i.e. the topography tends to have larger veolocity, which gradually decreases as entering the valleys.  This motivates us to figure out an approach to construct a more realistic velocity model, with the help of surface topography information. 



For taht sake, we need first quantify the surface geomorphy. Here, we adopted a technique developed by Gallant and Dowling 2003, called MRVBF, which describes the surface flatness from the elevation model.  This provides us an approach to estiamte bedrock depth , which controls the subsurface velocity structure.    We adopted this formula to relate the MRVBF and bedrock depth. BY substituting the bedrock depth of the downhole site to the left, and the MRVBF of the borehole location to the right, the parameter D0 is determiend. WIth this equaiton, we can calculate the bedrock depth in the entire domain. 

