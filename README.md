# G-API-FAQs
These are frequently asked questions and answers on developing with the G-API.
<br><br>

**Q: What is `out_meta`? What is the boilerplate code we have to write in the G-API op and how does it fit into the big picture?** 
<br><br>
A: You'll find helpful information in the [G-API Kernel API Doc](https://docs.opencv.org/4.5.2/d0/d25/gapi_kernel_api.html). The **_Extra information_** section contains additional insights.
<br><br>

**Q: What happens if my neural network has more than one input? How do I configure the input layers so that I tell it which layer gets which input?**
<br><br>
A: This behavior hasn't been documented yet, but there are samples to illustrate those cases.
The documentation for those is currently under review here: https://github.com/opencv/opencv/pull/20112/files
<br><br>

**Q: Why can't I clone a `cv::Mat` into an output of a kernel instead of having to copy one from an input? I get a message about the kernel resizing a `Mat` but the error message is not helpful.**
<br><br>
A: That’s valid feedback, thank you. Generally we don’t have any programming guides for our backends’ extensions API – no rules for this are documented yet.
In this case, code reallocated an output buffer provided by the framework – and the framework complained about it.
G-API manages internal buffers automatically so if a reallocation like this happens, it means that either;
   - the kernel was written incorrectly, or 
   - the internal contract is broken.
<br><br>

**Q: When do I need to compose a `gmat_desc`?  And how do I do that?**
<br><br>
A: See the [GMatDesc Struct Reference](https://docs.opencv.org/4.5.2/d0/d82/structcv_1_1GMatDesc.html).  
Also see the **_Extra Information_** section of the [G-API Kernel API Doc](https://docs.opencv.org/4.5.2/d0/d25/gapi_kernel_api.html).
<br>
The API and code examples are still under development and we hope to add additional information in the future, as resources allow.
<br><br>
