# Bart Morphing Geolocations onto Schematic Diagram (MGS)
# Introduction
The goal of the project is to transform the real world position of geographic coordinate system (latitude and longitude) onto the coordinate (x, y) of BART's rail track diagram.

<img src="https://github.com/YingluDeng/Bart_MGS/blob/main/demo/trail_system.png" />

# Table of contents:

- [Formulating Questions](#formulating-questions)
- [Datasets](#datasets)
- [Data Visulization](#data-visulization)
- [Algorithm Solution](#algorithm-solution)
- [Final Performance](#final-performance)

# Formulating Questions
The problem with morphing geolocations onto schematic diagram around one core idea: **How do we project the geolocation to the diagram more accurate?**

We can then break this down into two further questions: 
1) How can we convert the geolocation onto the diagram?
2) Where should we project the point on graph between two stations?

[(Back to top)](#table-of-contents)


# Datasets
This web page provides a list of all of the BART stations with their full names, abbreviations, latitude, longitude and addresses.
https://api.bart.gov/docs/stn/stns.aspx
<ul>
<li><b>bart_json.txt:</b> real bart location in latitude and longitude </li> 
<li><b>station_names_BART.csv:</b> bart station id and its corresponding name </li>
<li><b>AerialStructuresAndTrainControl.csv:</b> Input data in latitude and longitude </li>
</ul>

[(Back to top)](#table-of-contents)

# Data Visulization
* <b>Real Map Visulization (Google Map API)</b>
  * yellow dot: input geolocation data
  * purple dot: bart location
<img src="https://github.com/YingluDeng/Bart_MGS/blob/main/demo/real_world.png" />

* <b>Schematic Diagram with its corresponding bart station </b>
  * green dot: bart station
<img src="https://github.com/YingluDeng/Bart_MGS/blob/main/demo/diagram.png" />

[(Back to top)](#table-of-contents)


# Algorithm Solution
#### An algorithm solution that helps projecting the geolocation onto the diagram

The algorithm constist of two goals: 
1. Use a straight-forward way to project the real location on the graph.
2. Try to be efficient and save the run time for the algorithm.

> ## Steps:
>1. Calculating the distance between given point and bart station and find the  first closest and second closest bart id, and its distance.
>2. Project the given point onto the diagram by ratio calculation 
>    * ratio function: 
>       * ratio dist on real map & ratio dist on the diagram
>       * (distance between the given point to the cloest bart) / (two bart distance on real map) = dis / (two bart distance on the diagram)
>    * find a point along a line a certain distance away from another point
>       * https://math.stackexchange.com/questions/175896/finding-a-point-along-a-line-a-certain-distance-away-from-another-point
>       
>          <img src="https://github.com/YingluDeng/Bart_MGS/blob/main/demo/math%20explanation.png" />
>3. Draw all the projected points on the given diagram.
>4. Seperate station IDs into 12 groups and write them in a dictionary.
>    * Ideas: There are total 12 straight lines, we store the line-segment group name as key, and stations id on the corresponding line as value. Once we know the closest station for the given point, then we can target the specific line segment (key) based on its closest station id (value). Next, the final step is to project the point on closest line segment.
>5. Set the boundary so that the input data can only be in Bay Area.
>    * Example: If given an input geolocation in New York, the system will output "The input location is out of boundary, please try again."


[(Back to top)](#table-of-contents)

# Bug Explanation
If the given point is located in the line where the distances between two bart station are very uneven, it may cause the bug like the following example. 
<img src="https://github.com/YingluDeng/Bart_MGS/blob/main/demo/bug_exp.jpg" />

# Final Performance 
#### Project all the random generated geolocation on the schematic diagram 
<img src="https://github.com/YingluDeng/Bart_MGS/blob/main/demo/final%20performance.png" />

[(Back to top)](#table-of-contents)
