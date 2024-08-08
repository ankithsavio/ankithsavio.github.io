---
layout: page
title: Brain MRI Segmentation
description: 
img: /assets/img/brain-xray.jpg
importance: 3
---

Segmenting Brain MRI scan by utilizing image processing techniques. Used combination of boundary-based and region-based segmentation methods to identify five distinct tissue layers within a T1-weighted Brain MRI Image. There are two approaches that considers both 2D slices and the whole 3D volume of the MRI scan. 

The project repository : [Brain-MRI-Segmentation](https://github.com/ankithsavio/Brain-MRI-Segmentation)

<div class="row">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="assets/img/train_data.png" title="Training image" class="img-fluid rounded z-depth-1" %}
    </div>
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="assets/img/test_data.png" title="Testing image" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="caption">
    On the left, we have a slice of the MRI scan. Right, we have the pre-segmented image of the same slice.
</div>
<div class="row">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="assets/img/brain.gif" title="The Segmentation Process" class="img-fluid rounded z-depth-1 mx-auto d-block" width = "434" height = "362"%}
    </div>
</div>
<div class="caption">
    The results of the applications of various transformations.
</div>

The code is made available for both the 2D and 3D approach. It is important to note that the solution is very deterministic to the data used and therefore cannot be used for any other data out-of-the-box. However, I believe it is still valuable to learn the techniques of applications of image processing techniques to acheive segmentation and similar approach can be used for other types of MRI images.

<div class="row">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="assets/img/result_table.png" title="Results" class="img-fluid rounded z-depth-1 mx-auto d-block" width = "1606" height = "182"%}
    </div>
</div>
<div class="caption">
    Results for the various algorithms developed. Second column, we have Jaccard Score (JS). Third Column, we have Dice-Sørensen coefficient (DSC).
</div>

The results emphasises the use of whole volume of MRI scan to speed up the process. The following code be used to manually check the results.

{% raw %}

```html
import segmenter
# the 2D algorithms expects a index for the 2D slice to be considered
masks = segmenter.segment2d(i)

masks = segmenter.segment2d_ex(i)

# the 3D algorithm processes the whole 3D volume at once
masks = segmenter.segment3d()
```

{% endraw %}
