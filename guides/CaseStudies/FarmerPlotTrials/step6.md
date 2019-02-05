---
layout: default
section: Case Study
subsection: Farmer Plot Trials
title: Generating outputs
permalink: /case-study/farmer-plot-trials/step-6
---

# Generating outputs

In this step we will using [Vega Voyager](/tools/voyager) to visually analyse our data and generate charts for reporting.

If you do not have the tool installed follow the link above for instructions.

## 1. Open Voyager

When you first open voyager you will be presented with a screen to load your data. Click the _Load_ button to proceed
![image](/assets/images/FarmerTrials/voyager-1.png)

## 2. Import our data

We will be using the data generated in the previous step. If you do not have it you can download it from the following link:
<a href="/assets/resources/Striga treatment results by county.csv" target="_blank">
Striga treatement results by county</a>

Import the data into voyager from the _Paster or Upload Data_ tab
![image](/assets/images/FarmerTrials/voyager-2.png)

You will be presented with a window containing lots of information, including:

1. A list of fields available for your data (you can also filter data here)
2. A set of options to control how your visualisation will look, depending on which data fields are given for each value
3. The current, _active_ visualisation as specified by your options (this will start blank as we haven't specified anything yet)
4. A list of _potential_ or possible visualisations that you might want to create (to help explore the data the software automatically creates additional visualisations by starting with the current active visualisation and adding one more variable to it)

![image](/assets/images/FarmerTrials/voyager-3.png)

This is very powerful, as with ease not only can we create our own visualisation but also see other graphs which may (or may not) be of interest. This is called **exploratory visual analysis**.

## 3. Create our first visualisation

There are many possible visualisations that could be created or explored, but for this example we will focus on creating one that will give us a breakdown of striga treatments and pest appearance by coounty.

The first proposed visualisation already shows our data grouped by county. This looks ideal, so we can click on the _specify_ button on it to apply that visualisation

![image](/assets/images/FarmerTrials/voyager-4.png)

## 4. Explore further visualisations

With our data now split by county, we will see a list of further visualisations that might be of interest

![image](/assets/images/FarmerTrials/voyager-5.png)

All the diagrams provide information, however not all will be useful for us.

For example the first related view colours the data by average _plot_data_id_. We can see that Busia, for example, has plots with lower numbers than Homabay, so likely the enumerators visited there first.

The second visualisation colours the data by reported level of striga after treatment. This is much more useful for our purposes, and so we will also add that specification. You can do this either by clicking on the diagram specify button, or manually using the fields on the left

![image](/assets/images/FarmerTrials/voyager-6.png)

Finally we want to also show separate graphs depending on the treatment. We can do this using _Facets_. Simply drag the _Strigatreatment_selected_ field to the _row Facet_, or locate the relevant visualisation from the right and click to specify

![image](/assets/images/FarmerTrials/voyager-7.png)

## 4. Customise the output

Our visualisation is nearly complete, however there are a few small adjustments we want to make.

First, we can see a few results for the treatment \N. This indicates the data was empty. We could consider whether to keep this in our database or remove it from the csv we imported, however what will be easiest (and likely best) for now is to simply omit from the visualisation.

You can use the _Filter_ button next to the _Strigatreatment_selected_ to exclude these values

![image](/assets/images/FarmerTrials/voyager-8.png)

Finally we want to make adjustment to the colour scale used as it is misleading. The data used categories 'red_light', 'yellow_light', 'green_light' to describe the prevalence of striga after the treatment. It would be ideal if we could colour the bars red/yellow/green accordingly, unfortunately the software does not give us the full ability to do this.

Instead we will simply pick the closest-matching preset colour scheme. _Set2_ should be a reasonable fit.

![image](/assets/images/FarmerTrials/voyager-9.png)

## 5. Export generated charts

Now we have our final chart all that is left to do is export it. Unfortunately the software does not currently have the ability to export the visualisations to an image file (hopefully future versions will), so for now the easiest way is just take a screenshot and crop appropriately.

_Prevalence of striga for each county by treatment_

![image](/assets/images/FarmerTrials/voyager-10.png)

From the chart we can see that the highest prevalence of striga was within the _FarmerOwnPractice_ treatment. It also appears that _Kisumu_ had low rates of striga throughout all interventions and both _lablab_ and _manure_ had very few _red_light_ cases overall.

We could of course quickly build more visualisations to explore the data in other ways.

<hr>

_Prevalence of striga for each treatment_

![image](/assets/images/FarmerTrials/voyager-11.png){:class="size--medium-large"}

It is clearer from this chart that Lablab and Manure had the fewest red_light cases.

<hr>

_Prevalence of striga for each treatment by county_

![image](/assets/images/FarmerTrials/voyager-12.png)

This chart shows that Kisumu had no _red_light_ cases within _FarmerOwnPractice_, and few within any other treatments. We can also see that in Vihiga _FarmerOwnPractice_ had high numbers of _red_light_ cases and all interventions low numbers.

Now we have our final chart all that is left to do is export it. Unfortunately the software does not currently have the ability to export the visualisations to an image file (hopefully future versions will), so for now the easiest way is just take a screenshot and crop appropriately

![image](/assets/images/FarmerTrials/voyager-10.png)

From the chart we can see that the highest prevalence of striga was within the _FarmerOwnPractice_ treatment, _Kisumu_ had low rates of striga throughout all interventions and both _lablab_ and _manure_ had very few _red_light_ cases.

We could of course quickly build more visualisations to explore the data in other ways.
