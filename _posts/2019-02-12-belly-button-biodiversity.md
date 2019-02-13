# Web Visualization Flask Full Stack Application
## Belly Button Biodiversity <https://belly-button-biodiversity-tj.herokuapp.com>

![Bacteria by filterforge.com](http://robdunnlab.com/wp-content/uploads/microbes-sem.jpg)

This project is to build an interactive dashboard to explore the [Belly Button Biodiversity DataSet](http://robdunnlab.com/projects/belly-button-biodiversity/).

## Part 1 - Plotly.js

Use Plotly.js to build interactive charts for your dashboard.

* Create a PIE chart that uses data from your samples route (`/samples/<sample>`) to display the top 10 samples.

  * Use `sample_values` as the values for the PIE chart

  * Use `otu_ids` as the labels for the pie chart

  * Use `otu_labels` as the hovertext for the chart


* Create a Bubble Chart that uses data from your samples route (`/samples/<sample>`) to display each sample.

  * Use `otu_ids` for the x values

  * Use `sample_values` for the y values

  * Use `sample_values` for the marker size

  * Use `otu_ids` for the marker colors

  * Use `otu_labels` for the text values


* Display the sample metadata from the route `/metadata/<sample>`

  * Display each key/value pair from the metadata JSON object somewhere on the page

* Adapt the Gauge Chart to plot the Weekly Washing Frequency obtained from the route `/wfreq/<sample>`


* Update all of the plots any time that a new sample is selected.


## Part 2 - Heroku

Deploy this Flask app to Heroku. <https://belly-button-biodiversity-tj.herokuapp.com>


- - -

## Flask API

Use Flask API starter code to serve the data needed for your plots.

*  metadata API: route `/metadata/<sample>`
*  sample API: route `/sample/<sample>`
*  wash freq. API: route `/wfreq/<sample>`


