### PlotQA Dataset Download Links

**Images**

`png` directory contains RGBA images of the scientific plots in `.png` format. The plot images are named as `0.png`, `1.png`, etc.

The plot images for different data splits can be downloaded from the following link:

[Train](https://drive.google.com/file/d/1AYuaPX-Lx7T0GZvnsPgN11Twq2FZbWXL/view?usp=sharing), [Validation](https://drive.google.com/file/d/1i74NRCEb-x44xqzAovuglex5d583qeiF/view?usp=sharing), [Test](https://drive.google.com/file/d/1D_WPUy91vOrFl6cJUkE55n3ZuB6Qrc4u/view?usp=sharing)

#
**Annotations**

`annotations.json` is a list of dictionaries where each dictionary represents the ground-truth annotations of a plot.
It consists the following fields:
```
models: It is a list of dictionaries. Depending on the type of the plot (single or 2,3,4-multi), 
	the length of the dictionary can vary from 1 to 4. Each dictionary contain the following keys-
		name: Label corresponding to each datapoint.
		color: Color corresponding to the `name` datapoint.
		bboxes: Each bounding box corresponding to the `name` datapoints in the plot.

type: Type of the plot (vbar_categorical, hbar_categorical, dot_line, line).

general_figure_info: It is a dictionary containng the following keys-
		title: Bounding box and the text corresponding to the title of the plot.
		x_axis: Bounding boxes, axis labels, ticks lables corresponding to the x-axis of the plot.
		y_axis: Bounding boxes, axis labels, ticks lables corresponding to the y-axis of the plot.
		legend: Bounding boxes, axis labels, ticks lables corresponding to the legend of the plot.
		plot_info: Bounding box corresponding to the plot.
		figure_info: Bounding box corresponding to the figure.
	
image_index: Image-index corresponding to each image.
```

The annotations for the plot images for different data splits can be downloaded from the following links:

[Train](https://drive.google.com/file/d/1VzWwxBVrlep17BGZU17GpLuGpwjyWbzq/view?usp=sharing), [Validation](https://drive.google.com/file/d/1CCp1tvMd62LfBrWa6pRdb1lpg68A2yFw/view?usp=sharing), [Test](https://drive.google.com/file/d/1ikiPqkDgxNilYsU5hbK03T4_x2eDmopP/view?usp=sharing)

#
**Question-Answer pairs**

`qa_pairs.json` is a list of dictionaries where each dictionary represents a question. Each question is represented using the following fields:
```
image_index: Image-index corresponding to the image on which this question is being asked.

question_string: Text of the question.

answer: Answer corresponding to the question `question_string`.

answer_bbox: Bounding box of the answer if the answer comes from the plot itself.

template: Template from which `question_string` is being instantiated.

type: Type of the plot (vbar_categorical, hbar_categorical, dot_line, line).
```

`qa_pairs_v1.json`: This .json file contains 8,190,674 number of question-answer pairs. 

The question-answer pairs for different data splits can be downloaded from the following links:

[Train](https://drive.google.com/file/d/1bBSUutd-Die27ZH3QTMVhBjW9l5hAwrr/view?usp=sharing), [Validation](https://drive.google.com/file/d/1yUjF_9Jgx720Kffef4_JDRt7lTHQZlKH/view?usp=sharing), [Test](https://drive.google.com/file/d/1pKujAjE4yMpSJ8gEQWIxdEyGkorJHeFm/view?usp=sharing)

`qa_pairs_v2.json`: This .json file is an extended version of the `qa_pairs_v1.json` which has 28,952,641 number of question-answer pairs.

The extended version of the question-answer pairs for different data splits can be downloaded from the following links:

[Train](https://drive.google.com/file/d/1UNvkdq1YJD_ne6D3zbWtoQij37AtfpNp/view?usp=sharing), [Validation](https://drive.google.com/file/d/1y9RwXSye2hnX0e2IlfSK34ESbeVblhH_/view?usp=sharing), [Test](https://drive.google.com/file/d/1OQBkoe_dpvFs-jnWAdRdxzh1-hgNd9bO/view?usp=sharing)

#
**Table QA stage**

To be updated soon

#
Please cite the following if you use the PlotQA dataset in your work:
```
@article{DBLP:journals/corr/abs-1909-00997,
  author    = {Nitesh Methani and
               Pritha Ganguly and
               Mitesh M. Khapra and
               Pratyush Kumar},
  title     = {PlotQA: Reasoning over Scientific Plots},
  journal   = {CoRR},
  volume    = {abs/1909.00997},
  year      = {2019},
  url       = {http://arxiv.org/abs/1909.00997},
  archivePrefix = {arXiv},
  eprint    = {1909.00997},
  timestamp = {Mon, 16 Sep 2019 17:27:14 +0200},
  biburl    = {https://dblp.org/rec/bib/journals/corr/abs-1909-00997},
  bibsource = {dblp computer science bibliography, https://dblp.org}
}
```

#
# Contact
If you have any questions, suggestions or comments about the dataset in the paper, feel free to contact us at:
Nitesh Methani (nmethani@cse.iitm.ac.in), Pritha Ganguly (prithag@cse.iitm.ac.in).
