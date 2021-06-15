# G-API-FAQs
These are frequently asked questions on developing with the G-API for use with OpenVINO.


1. What is out_meta?
<details> 
Q: What is up with the boilerplate code we have to write in the G-API op and how does it fit into the big picture? 
<br><br>
A: You'll find helpful information in the G-API Kernel Doc https://docs.opencv.org/4.5.2/d0/d25/gapi_kernel_api.html. See **Extra information**.
</details>

b.	What happens if my neural network has more than one input? How do I configure the input layers so that I tell it which layer gets which input?
We’re yet to document this behavior, but the samples we provided to MSFT back in 2020 illustrated those cases already.
The doxygen documentation for those is here on review: https://github.com/opencv/opencv/pull/20112/files

c.	Why can't I clone a cv::Mat into an output of a kernel instead of having to copyTo one from an input? I get a message about the kernel resizing a Mat or something, but again, the error message is not super helpful.

That’s a valid portion of feedback, generally we don’t have any programming guides for our backends’ extensions API – no rules to follow are documented.
In particular, what Max was faced that with his code he reallocated an output buffer which was provided by framework – and framework has complained about it.
G-API manages internal buffers automatically so if a reallocation like this happens, it means either kernel written incorrectly or internal contract is broken – so the error occurs.

d.	How do I compose a gmat_desc based on some input information? Really, how do I compose a gmat_desc at all, and when do I need to?
There are probably other things, but that's what I can think of now.

https://docs.opencv.org/4.5.2/d0/d82/structcv_1_1GMatDesc.html
It seems the API and code examples is never enough and we need to provide some explanation on the concept.
The above mentioned “Kernel API/Extra information” touches it a little bit, but I agree some better document is required.
