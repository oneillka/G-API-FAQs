# G-API-FAQs
These are frequently asked questions on developing with the G-API for use with OpenVINO.


1. What is out_meta?
<details> 
Q: What is up with the boilerplate code we have to write in the G-API op and how does it fit into the big picture? 
<br><br>
A: You'll find helpful information in the [G-API Kernel API Doc](https://docs.opencv.org/4.5.2/d0/d25/gapi_kernel_api.html). The **Extra information** section contains additional insights.
</details>

2. Neural networks with more than one input?
<details>
Q: What happens if my neural network has more than one input? How do I configure the input layers so that I tell it which layer gets which input?
<br><br>
A: This behavior hasn't been documented yet, but samples provided to MSFT illustrate those cases.
The doxygen documentation for those is here on review: https://github.com/opencv/opencv/pull/20112/files
</details>

3. Can I clone a cv::Mat?
<details>
Q: Why can't I clone a cv::Mat into an output of a kernel instead of having to copyTo one from an input? I get a message about the kernel resizing a Mat or something, but the error message is not super helpful.
<br><br>
A: That’s valid feedback, thank you. Generally we don’t have any programming guides for our backends’ extensions API – no rules for this are documented yet.
In this case, code reallocated an output buffer provided by the framework – and the framework complained about it.
G-API manages internal buffers automatically so if a reallocation like this happens, it means that either;
  - A) the kernel was written incorrectly or 
  - B) the internal contract is broken.
</details>

4. How and when do I compose a gmat_desc?
</details>
Q: How do I compose a gmat_desc based on some input information? Really, how do I compose a gmat_desc at all, and when do I need to?
<br><br>
A: https://docs.opencv.org/4.5.2/d0/d82/structcv_1_1GMatDesc.html
The API and code examples are still under development and we hope to add additional information in the future, as resources allow.
The above mentioned “Kernel API/Extra information”.
</details>
