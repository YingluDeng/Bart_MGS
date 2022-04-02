# Bart Morphing Geolocations onto Schematic Diagram (MGS)
## Introduction
The goal of the project is to transform the real world position of geographic coordinate system (latitude and longitude) onto the coordinate (x, y) of BART's rail track diagram.

<img src="https://github.com/YingluDeng/Bart_MGS/blob/main/demo/trail_system.png" />

# Table of contents:
<!-- After you have introduced your project, it is a good idea to add a **Table of contents** or **TOC** as **cool** people say it. This would make it easier for people to navigate through your README and find exactly what they are looking for.

Here is a sample TOC(*wow! such cool!*) that is actually the TOC for this README. -->

- [Scheduling Calls with Predictive Modeling](#scheduling-calls-with-predictive-modeling)
- [Demo-Preview](#demo-preview)
- [Problem Statement](#problem-statement)
- [Formulating Questions](#formulating-questions)
- [The Bart Data](#The-Bart-Data)
- [Solution](#solution)
- [Machine Learning System Design](#machine-learning-system-design)
- [Navigating the Repo](#navigating-the-repo)

# The Bart Data
This web page provides a list of all of the BART stations with their full names, abbreviations, latitude, longitude and addresses.
https://api.bart.gov/docs/stn/stns.aspx
<ul>
<li><b>bart_json.txt:</b> real bart location in latitude and longitude </li> 
<li><b>station_names_BART.csv:</b> bart station id and its corresponding name </li>
<li><b>AerialStructuresAndTrainControl.csv:</b> Input data in latitude and longitude </li>
</ul>
[(Back to top)](#table-of-contents)

## Visulization
* <b>Real Map Visulization (Google Map API)</b>
  * yellow dot: input data
  * purple dot: real bart location
<img src="https://github.com/YingluDeng/Bart_MGS/blob/main/demo/real_world.png" />
[(Back to top)](#table-of-contents)


