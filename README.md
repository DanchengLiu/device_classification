# device_classification
implemented some baselines and playgrounds in Jupyter Notebook for device classification. Code written in Python, Keras

# overleaf
Please see the overleaf document for this project at: https://www.overleaf.com/6941841442wypfhpjtdprf

I have not yet started to write for this project. However, the references might be interest of whoever continues with this project.

# brief discription

Nowadays, more and more devices benefit from the development of wireless communication infanstructures and communicate with each other using various protocols, including Wi-Fi. 
However, with the increasing need of communication comes with the increasing need for security. As more and more sensitive information are shared through wireless communications, adverserial attackers often fake their identities and request those sensitive information from service providers.
At the same time, it is often impratical for most service providers to perform advanced security checking to validate each of the incoming request due to efficency concerns. Thus, it is critically important for the service provider to have an accurate and efficient method of identify the transimtter on the other side of communication.
RF fingerprinting, the official terminology of the above need, refers to the interesting fact that each of the device are phyiscally different due to circuit-level differences. As a result, even if they send the same information, the signal patterns received on the receiver side will still be different.
Thus, recent attention has shifted to the possibility of identifying a transmitter's identity using the underlying unique characteristics from the signals that it sends out. 

With the development of deep neural networks, we have seen a lot of excellent works on separating and classifying the identities of transmitters using various architectures. However, several questions remain in this field:
#### 1. DNNs are heavily data driven. It is known that if we have abundant data, we can enjoy a DNN classifier that accurately predicts almost anything. However, RF signals are an area where huge number of data points are often hard to be obtained due to expense limitations. As a result, we need to find a model that works well with limited data points available to the training phase.
#### 2. As shown by performed experiments (see figures in the Colab files and summary folder), there is a huge gap between classification on the source and target datasets. This problem is particularly severe when the number of data points availabe for training is limited. This is commonly known as domain tranfer problem in machine learning (ML) community, and such problem poses strong practical concerns to the DNN applicability. We need to find a ML model that works robustly under this problem setting and close the gap between source and target datasets.
#### 3. It is also known that complex models generally have better performance. However, efficiency is a huge concern for this type of problem for two reasons. First, current technologies are shifting the attention to distributed computing on edge devices. Complex model might require large memory space and computing power, which is often not achievable by edge devices. Second, complex models require a lot longer time to classify incoming requests. For real-time service providers, long latency often means failure of service.

In summary, these three needs call for a robust, efficient ML model that can correctly classify a transmitter's identity with as few training samples as possible.

#  technical discussions
1. This GitHub repo contains rerun of the model from the dataset paper, as well as implementation of some classical models. It is not hard to see that recurrent models are much better than convolutional models. This is the expected behavior in ML signal area. Due to the time-series nature of RF signals, recurrent models often perform better. However, this is at the cost of time efficiency. LSTM models are slower than CNN of the same parameter size. This could be an important argument in favor of the models designed in our paper (see 3 of above section).

2. Interestingly, attention does not seem to help in this task. There could be two justifications. First, I use a third-party implementation of attention layer, which could be naive or incorrect. If you are interested, you can switch to your own implementation, and see if the results change. Second, distinct characteristics of each transmitter are embedded evenly in each of the time stamps. Thus, attention does not focus on any of the particular time stamp. If you are interested in this, you can try printing out the atttention weights and see if they are even.

3. There are some future directions that I think could be promising.
First, no matter what happens to the other scenarios, if you train the model on only one receiver, the generalization ability of all models are very poor. This is very strange, and it indicates great potential of improvement. HD computing is ususally suitable for this kind of task because you have the freedom of designing the encoding function, which allows you to manually extract features that will be used for classification. I suggest to consider the time-series nature of the data and design encoding functions around that. Also, ID-level could be useful.
Second, if you can come up with a neat encoding that parallelizes well, HD should be faster than CNN. Besides, HD is hardware friendly, which brings another advantage compared to DNN networks if you put it on a specialized FPGA design.
Third, if HD really does not work on this task, as a final step, you could think about how to do feature engineering such that CNN also generalizes to the extend of LSTM (without sacrificing the effciency)

# contact
I will not be always available during the summer, but you may still contact me if you need to discuss the project and ideas. You can contact me at d1liu@ucsd.edu. Please also cc daninboston2000@gmail.com and 1171910390@qq.com in case UCSD and gmail does not work in my country.
