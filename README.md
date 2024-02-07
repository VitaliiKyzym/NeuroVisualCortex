# Analyzing Layer Activation Differences in Visual Cortex when Stimulated with Lines of Different Orientations

The main purpose of the project was to use the [Biorealistic Model of Mouse Primary Cortex (V1)](https://www.cell.com/neuron/fulltext/S0896-6273(20)30067-2) from the Allen Institute to analyze differences in layer activation in the visual cortex when presented with stimuli of differing orientation. For this purpose, four stimuli bars (horizontal, vertical, diagonal1, diagonal2) were converted to spiketrains using the LGN model and then used to simulate the visual cortex. Custom visualization scrits were written to visualize the data being proccessed and statistical analysis (RMSE, KL Divergence, DTW) performed to determine the difference in total firing over time of the different layers with the stimuli presented. As a result, the project examined the division of the visual cortex layers in understanding low->high level features.

## Installing and Executing

Installing the packages

```
pip install -r requirements.txt
```

To execute the code, both notebooks in the directory do different things so run both.

## Results and Visualizations

The input stimuli consisted of four black bars on a white background in varying orientation. Particulary, four lines were used - A. horizontal, B. diagonal (135 deg), C. vertical and D. diagonal (45 deg) which are depicted in the figure below.

![Image Alt text](/figs/lines.png)

One key visualization introduced was the node firing raster which showed at which timestep a neuron was activated and which population it belonged to. By grouping the neurons into their respective population category, it was then possible to caculate the differences between the population responses over time to the different stimuli. Shown below is the raster for a horizontal bar stimulus on the L4 layer of the visual cortex.

![Image Alt text](/figs/RasterL4Horizontal.png)

Next, the total number of active neurons was calculated by summing up the activated neurons in every population of the specific layer. The total number of active neurons is simply the number of neurons firing at a specific timestep. To make this feature more comparable, instead of having a continous time axis, the time component was broken down into conserved time bins which comprised of 14 ms fragments. Thus, as shown below, the total number of neurons fired really depicts the total number of neurons active in a given time fragment which made comparison between different simulations easier.

![Image Alt text](/figs/diagonal-r2l L4.png)

Lastly, a number of statistical tools were used to analyze the neuronal activity when presented with different stimuli. Dynamic Time Warping (DTW) was one of the techniques and a visualization of the calculated difference in shown below.

![Image Alt text](/figs/warp.png)

Some results of the investigation as shown below. Two stimuli responses are compared with each other at a given time and the differences between their total neuronal firing throughout time is shown in subsequent columns as RMSE values. As expected, higher level layers had larger differences in the neural activation but interestingly, L2/3 and L6 had the highest RMSE values compared to the other layers.

![Image Alt text](/figs/rmse-results.png)



