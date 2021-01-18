<h1 align='center'>Machine Learning Research Reproducibility Guide Book</h1>

<p align="center">
    <b>Visual Computing Group</br>Singapore University of Technology and Design<br/></b>
</p>

***[The following materials are compiled from various sources such as textbooks, lecture materials, conference talks, web resources and are shared for research purposes only. In the interest of brevity, every source is not cited. The compiler of these materials gratefully acknowledges all such sources. Please contact keshigeyan@sutd.edu.sg for any queries.]***

Predominant portion of contemporary machine learning research faces reproducibility and replication crisis. Though both terms are used interchangeably in the literature, we understand reproducibility as the gateway for replication. 

> Reproducibility is the ability to obtain closeness of the agreement between the results of measurements of the same measurand, carried out by using **identical methodology and identical artifacts** described in a scientific work. 
>
> Replication is the ability to obtain **consistent closeness** of the agreement between the results of measurements of the same measurand, carried out by using **identical methodology** described in a scientific work **across multiple relevant artifacts**.

This Guide book is written with the intention of helping researchers and engineers working in machine learning domains to publish reproducible research. We break research components into two for reproducibility purposes. 1) **Compulsory/ required components** and 2) **Optional components**. They are clearly explained in the upcoming sections. 

*Note: Please feel free to contribute/ correct any mistakes. If you are interested in understanding more, please refer to this talk on [Machine Learning Reproducibility, NeurIPS 2019](https://slideslive.com/38923790/machine-learning-reproducibility-an-update-from-the-neurips-2019-reproducibility-cochairs).* 



## Table of Contents

- [Required Components](#required-components)
  * [Data](#data)
    + [Datasets](#datasets)
    + [Data preprocessing techniques](#data-preprocessing-techniques)
    + [Data Splits](#data-splits)
  * [Proposed Research Method](#proposed-research-method)
  * [Hardware Environment](#hardware-environment)
    + [Computing Type](#computing-type)
    + [CPU](#cpu)
    + [GPU/ TPU](#gpu--tpu)
  * [Software Environment](#software-environment)
    + [OS](#os)
    + [Programming Languages](#programming-languages)
    + [Framework](#framework)
    + [Additional Software](#additional-software)
    + [Dependencies](#dependencies)
    + [Docker Images](#docker-images)
  * [License](#license)
  * [Results](#results)
    + [Quantitative Results](#quantitative-results)
    + [Qualitative Results](#qualitative-results)
  * [Hyper-parameters](#hyper-parameters)
    + [Randomization Control](#randomization-control)
  * [Time](#time)
    + [Training Time](#training-time)
    + [Inference Time](#inference-time)
  * [Code directory structure](#code-directory-structure)
  * [How to run the code?](#how-to-run-the-code-)
  * [Availability of pretrained weights](#availability-of-pretrained-weights)
  * [References](#references)
  * [Citation](#citation)
- [Optional Components](#optional-components)
  * [Acknowledgements](#acknowledgements)
  * [Conference Materials](#conference-materials)
  * [FAQ](#faq)



## Required Components

### Data

A large portion of machine learning code repositories do not include concrete information on data. We identify a list of key elements where authors should clearly address with respect to data to allow reproducibility.

#### Datasets

- Authors should publish or include links for the original data used for their research. Even if benchmark datasets are used (i.e.: ImageNet), including links to these data repositories to avoid any confusions.
- In instances where the authors cannot publish the data used for their research due to data confidentiality or other factors (i.e.: Medical data), this should clearly be mentioned in the code repository. 
- In order to alleviate data confidentiality issues, some authors publish synthetic data to evaluate their research methods.  In these instances, authors should clearly describe the process and methods used to generate these data.
- Licensing information for datasets should be strictly included (Even if benchmark datasets are used).



#### Data preprocessing techniques

- Most algorithms may require pre-processing techniques. So authors need to clearly describe all relevant information with respect to data preprocessing. Wherever possible, the authors should publish preprocessed data allowing to reproduce research results more easily.



#### Data Splits

- Clear splits of data used for training, validation and test should be published. Many code repositories do this by including a txt/ csv file describing the splits.

  

___

### Proposed Research Method

This section is generally deterministic. 

- The code should include clear implementation of proposed method (i.e.: architecture,  loss functions, evaluation metrics). 

- Complexity details (space, time and sample size) should be included.

- Any diagrams associated with proposed method can be included here. 

  

___

### Hardware Environment

With increasing data volumes and distributed training strategies, it is vital to include clear details on the hardware setup used to run the experiments. 

#### Computing Type

- Authors should indicate as to whether they used in-house machines, super-computing facilities or cloud computing instances to run their experiments. 

- They can provide additional information on specific cloud computing vendor (AWS/  GCP) to help other researchers working on similar problems.

  

#### CPU

- Authors should include clear details on the CPU configuration used for running the experiments.

  

#### GPU/ TPU

- Authors should include clear details on GPU/ TPU configuration used for running the experiments.

  

___

### Software Environment

#### OS

- Authors should include information on the list of operating systems (with version details) in which the code was tested.



#### Programming Languages

- Authors should include information on the list of programming language versions in which the code was tested. 



#### Framework

- For most machine learning applications, we use existing frameworks (Tensorflow, Pytorch, Caffe etc). Authors should include information on the list of frameworks/ framework versions in which the code was tested.



#### Additional Software

- If authors used any additional software (i.e.: Unity game engine for generating synthetic data), they should be clearly mentioned. If any proprietary software was used, include references to that as well. 
- Licensing information for any other additional software used should be mentioned.



#### Dependencies

- Most software libraries do not function standalone. Hence the list of dependencies need to be explicitly mentioned. i.e.: For python based projects, many repositories include dependencies as a text file. (requirements.txt)



#### Docker Images

- Containers are a way to package software in a format that can run isolated on a shared operating system. Authors can alternatively publish/ distribute docker images with source code, so that users do not need to worry about setting up dependencies.

  

___

### License

For your repository to truly be open source, you'll need to license it so that others are free to use, change, and distribute the software. So please add the corresponding license file to your code repository. This [tool](https://choosealicense.com/) can help you understand how to license your code.



___

### Results

#### Quantitative Results

- All quantitative results with relevant diagrams should be included. In many instances, including graphics from the corresponding scientific work can help here.
- Results that could not be included in the original publication (i.e.: due to page limit etc), can be included here.
- In many instances, final results are obtained by averaging over a number pf independent executions of the algorithm. Authors should include these information as well.



#### Qualitative Results

- Any quantitative results with relevant diagrams should be included. 

- Results that could not be included in the original publication (i.e.: due to page limit etc), can be included here.

  

___

### Hyper-parameters

Generally there are multiple stochastic elements associated with machine learning research. Hence precise information on final values of all hyper-parameters, methods used to obtain them and randomization control settings need to be included. 

#### Randomization Control

- Clear details on seed values to reproduce the results should be included.

  

___

### Time

Many research code repositories forget to address this factor. As we know, many machine learning algorithms are computationally very intensive and time-consuming. So clear details on the following should be included:

#### Training Time

Information on how long it takes to train a single model should be included. This should correspond to the hardware and software settings mentioned above.



#### Inference Time

Information on how long it takes to run inference need to be included (i.e.: Object detection inference time per image). This should correspond to the hardware and software settings mentioned above.



___

### Code directory structure

Most code repositories do not have a standard structure. Hence, we propose to follow a standard code directory structure to make reproducibility easier. (We also do understand that it may not be possible to follow this structure for all projects)

- /assets: contains GitHub readme resources (i.e. : images used in readme.md)

- /src : contains all source code files

- /data: contains required data

- /config: contains configuration files (if any)

- /output: contains any results or outputs

- requirements.txt: contains all software dependencies to run the code.

- LICENSE: License file

  

___

### How to run the code?

This is the most important section. Authors should clearly describe the steps on how to run the code and reproduce the results. 



___

### Availability of pretrained weights

Authors should mention whether pretrained weights are made available and describe the means of obtaining them. Having a single centralized cloud location to publish all the models belonging to the organization is often useful.



___

### References

Any references to code/ data obtained from from sources need to be citied here. (Not publication references).



___

### Citation

Citation information should be included here





## Optional Components

### Acknowledgements

Acknowledgements enable you to thank all those who have helped in carrying out the research. Please keep it concise. 



___

### Conference Materials

If the work was part of a conference, links to materials such as video presentations, poster and blogs can be included.



___

### Contact Information

Authors can optionally include any contact information for feedback or discussion.



___

### FAQ

Authors can also add a FAQ section to answer commonly asked queries.