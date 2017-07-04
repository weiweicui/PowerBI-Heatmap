---
layout: default
title: PowerBI - Heatmap Custom Visual
image_sliders:
  - slider1
---

[comment]: # (checklist: )
[comment]: # (a. _data/sliders.yml: change the images)
[comment]: # (b. _incudes/disqus_comments.html: change the forum id)
[comment]: # (c. index.md: title and content)

# Background

Heat maps are a type of visualization to show data density on a map. They are particularly helpful when you have a lot of (e.g., tens of thousands of) data points on the map and are mainly interested in their overall distribution. Technically, in a heatmap, data points are aggregated locally and mapped to colors (either gradient or quantile), so that we can make better sense of the density of the data from the colors while still being able to see and use the map.

{% include slider.html selector="slider1" %}

# Where to Get It

This visual has been submitted to Office Store and will appear there shortly. Meanwhile, you can find them in the [_dist_](https://github.com/weiweicui/PowerBI-Heatmap/tree/master/dist) folder of this [_repo_](https://github.com/weiweicui/PowerBI-Heatmap).

# How to Use
* Required fields:
  * **Location (ID)**: Values in this field are used to identify different geo-coordinates. They may be treated as addresses (or zip codes) and used to query geo-locations (through [Bing Maps REST Services](https://msdn.microsoft.com/en-us/library/ff701713.aspx)) if latitude/longitude are not specified. Please note that integer values in this field are directly treated as zip codes when geocoding.
* Optional fields:
  * **Latitude/Longitude**: These fields specify the geo-locations of data points. If both are specified, the geocoding will not happen.
  * **Value**: This field specifies the exact values associated to the addresses. They have to be numerical. The default value is 1.
  * **Group**: Data points will be split into groups based on this field. If this field is set. **Group** and **Animation** features will be enabled in the format panel. For example, if your data points have timestamps, you can group them based on the timestamps, then either 1) selectively show the heatmap for some specific timestamps or 2) run an animation to see the heatmap changing over time.
* Special settings:
  * **Renderer - Type**: You can choose between `Heat` and `Contour`.
  * **Renderer - Radius**: It defines how close two data points can be aggregated together. If you like to see more details, you may reduce the value.
  * **Renderer - Measure**: It defines the strategy to find the largest aggregated value based on data point groups, which will further determine the color mapping scheme. For example (please note that each group can find its max aggregated value independently):
    * **Average**: Choose the average of all max values (each group may have one).
    * **Highest**: Choose the largest of max values.
    * **Sum**: Choose the sum of all the max values. This is the default option.
    * **First/Last**: Sort all groups, then choose the max value of the first/last group.
    * **Manual**: Directly take the user input.
  * **Contour map**: Customize the color mapping scheme for the `Contour` type. Here you can give at-most five thresholds to set different colors. The thresholds can be set
      * either relative to the max aggregated value that is decided by **Renderer - Measure**,
      * or using absolute values.
  * **Heat map**: Customize the color mapping scheme for the `Heat` type. You need to give five values between 0 and 1 (relative to the aforementioned max aggregated value) and five colors.
  * **Animation - Freezing/Morphing**: How long (in seconds) the playback will pause for each group or animate from one group to the next one.
  * **Map - Language**: Choose a specific language for the background map.
  * **Map - Cache**: Store the geocoding results, so they can be reused when you open the report next time. Otherwise, the geocoding process will be repeated, which is quite slow. But caching many locations also may increase your file size.

* Need more help? Please leave a comment below.
