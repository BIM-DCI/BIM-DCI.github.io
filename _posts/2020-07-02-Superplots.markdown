---
layout: post
title:  "Data Visualization for High Throughput Microscopy"
date:   2020-07-02
categories: dataviz, hcs, high-throughput microscopy
---

Plotting data and statistical analysis of high-throughput microscopy (HTM) experiments is not straightforward for most microscopists and different from the way other biological experiments are usually handled. The difficulty with HTM data is that it is usually a combination of single cell data, image-level data, well/treatment-level data and plate/experiment-level data. To get accurate data on the effect of your treatment you take many images of many cells and analyze these images on a per-cell basis. But the correct way to test the effect statistically is not to treat each cell but rather treat each treatment independently. After all we should assume that each cell in each treated well received the same concentration of the same drug. So for statistical testing we need to take the mean or median values for all the cells in a well, but this feels a bit like throwing out the baby with the bathwater. In fact, according to the [*Central Limit Theorem*](https://en.wikipedia.org/wiki/Central_limit_theorem), if you take multiple samples from a distribution, the distribution of the means of these samples tend towards a normal distribution, no matter what distribution the original samples were taken from. This means that you per-cell data might have odd distributions that are lost when you do the statistics on the mean values of multiple experiments. Another piece of information that that you might want to retain when taking the means of multiple experiments is if there is a certain trend for the measurements within one experiment compared to other experiments. For example if all values for one experiments are slightly higher than for the same treatments in another experiment.

To take into account both cell-level data and experiment-level data, this paper [Superplots: Communicating reproducibility and variability in cell biology](https://rupress.org/jcb/article/219/6/e202001064/151717/SuperPlots-Communicating-reproducibility-and) by Lord et al. published in the Journal of Cell Biology in April 2020 introduces the *Superplot* for accurately plotting both cell-level variability and experimental reproducibility. This is from Fig 1S, an example of a Superplot:

<img src="{{site.baseurl}}/assets/jcb_202001064_figs1_crop.png" height = "500">

You can see the average values for three experiments, in this case they trend in the same direction (what they call *"day-to-day variability"*), the mean of the averages plus standard error and the distribution of the underlying per-cell data in the violinplot in the background.

<img src="{{site.baseurl}}/assets/avg_box_no_border_edit.png">
