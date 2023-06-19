# device_classification
implemented some baselines and playgrounds in Jupyter Notebook for device classification

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
1. 