---
title: Multiple Object Tracking using Particle Filter
date: 2015-11-04 17:34:50
categories: 
- Projects
cover_index: /images/mot/index.jpg
cover_detail: /images/mot/banner.jpg
---
I implemented multiple object tracking using particle filter based on paper (M. D. Breitenstein, F. Reichlin, B. Leibe, E. Koller-Meier and L. Van Gool  *Online multiperson tracking-by-detection from a single, uncalibrated camera*,  IEEE Trans. Pattern Anal. Mach. Intell.,  vol. 33,  no. 9,  pp.1820 -1833 2011). <!-- more --> I was using C++ and OpenCV and doing offline tracking to implement the code. Instead of using condensation function from OpenCV, I was implementing particle filter from scratch and trying to tackle occlusion problem.


<figure class="images-row">
<img style="display: inline;" src="/images/mot/1.jpg" width="300"><img style="display: inline;" src="/images/mot/2.jpg" width="300"><img style="display: inline;" src="/images/mot/3.jpg" width="300">
<figcaption>
Screenshot of 81st, 91st, and 101st frame from PETS09-S2L1 dataset without occlusion handling.
</figcaption>
</figure>

<figure class="images-row">
<img style="display: inline;" src="/images/mot/1o.jpg" width="300"><img style="display: inline;" src="/images/mot/2o.jpg" width="300"><img style="display: inline;" src="/images/mot/3o.jpg" width="300">
<figcaption>
Screenshot of 81st, 91st, and 101st frame from PETS09-S2L1 dataset with occlusion handling.
</figcaption>
</figure>

<hr>
- Date: April 2015 to Juli 2015
- A Project of Visual Computing Lab Course, Department of Computer Graphics, University of Bonn, Germany
