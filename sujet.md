# Practical Session #1: Introduction

1. Find in news sources a general public article reporting the discovery of a software bug. Describe the bug. If possible, say whether the bug is local or global and describe the failure that manifested its presence. Explain the repercussions of the bug for clients/consumers and the company or entity behind the faulty program. Speculate whether, in your opinion, testing the right scenario would have helped to discover the fault.

2. Apache Commons projects are known for the quality of their code and development practices. They use dedicated issue tracking systems to discuss and follow the evolution of bugs and new features. The following link https://issues.apache.org/jira/projects/COLLECTIONS/issues/COLLECTIONS-794?filter=doneissues points to the issues considered as solved for the Apache Commons Collections project. Among those issues find one that corresponds to a bug that has been solved. Classify the bug as local or global. Explain the bug and the solution. Did the contributors of the project add new tests to ensure that the bug is detected if it reappears in the future?

3. Netflix is famous, among other things we love, for the popularization of *Chaos Engineering*, a fault-tolerance verification technique. The company has implemented protocols to test their entire system in production by simulating faults such as a server shutdown. During these experiments they evaluate the system's capabilities of delivering content under different conditions. The technique was described in [a paper](https://arxiv.org/ftp/arxiv/papers/1702/1702.05843.pdf) published in 2016. Read the paper and briefly explain what are the concrete experiments they perform, what are the requirements for these experiments, what are the variables they observe and what are the main results they obtained. Is Netflix the only company performing these experiments? Speculate how these experiments could be carried in other organizations in terms of the kind of experiment that could be performed and the system variables to observe during the experiments.

4. [WebAssembly](https://webassembly.org/) has become the fourth official language supported by web browsers. The language was born from a joint effort of the major players in the Web. Its creators presented their design decisions and the formal specification in [a scientific paper](https://people.mpi-sws.org/~rossberg/papers/Haas,%20Rossberg,%20Schuff,%20Titzer,%20Gohman,%20Wagner,%20Zakai,%20Bastien,%20Holman%20-%20Bringing%20the%20Web%20up%20to%20Speed%20with%20WebAssembly.pdf) published in 2018. The goal of the language is to be a low level, safe and portable compilation target for the Web and other embedding environments. The authors say that it is the first industrial strength language designed with formal semantics from the start. This evidences the feasibility of constructive approaches in this area. Read the paper and explain what are the main advantages of having a formal specification for WebAssembly. In your opinion, does this mean that WebAssembly implementations should not be tested? 

5.  Shortly after the appearance of WebAssembly another paper proposed a mechanized specification of the language using Isabelle. The paper can be consulted here: https://www.cl.cam.ac.uk/~caw77/papers/mechanising-and-verifying-the-webassembly-specification.pdf. This mechanized specification complements the first formalization attempt from the paper. According to the author of this second paper, what are the main advantages of the mechanized specification? Did it help improving the original formal specification of the language? What other artifacts were derived from this mechanized specification? How did the author verify the specification? Does this new specification removes the need for testing?

## Answers

### 1. Article reporting the discovery of a software bug : [Lien CNN Article](https://edition.cnn.com/2019/01/29/tech/facetime-bug-teen-discovery/index.html)

The article is titled "This 14-year old found Apple’s FaceTime bug before it went viral " and it was published on CNN website on January 30, 2019. 

The bug allowed a caller to hear the audio from the recipient's iPhone before they answered the call, and in some cases, even see video from the recipient's phone. The issue was discovered by a 14-year-old boy from Arizona, who was trying to set up a group chat in FaceTime with his friends. When he realized he could hear audio from a friend's phone before the friend had even answered the call.

Apple initially responded to the bug by disabling the group chat feature in FaceTime, and later released a software update to fix the issue. The article notes that the incident raised questions about how thoroughly Apple tests its software before releasing it to the public, and whether the company is doing enough to prioritize user privacy and security.

This highlighted the need to conduct rigorous testing before launching any feature on a consumer product. This would have enabled Apple to fix the bug before customers were affected and before it had a negative impact on the company's image.

### 2. The collection bug 814 :  [Lien bug](https://issues.apache.org/jira/projects/COLLECTIONS/issues/COLLECTIONS-814?filter=doneissues&orderby=updated+DESC)

The collection bug 814  is a local bug that occurred when the CollectionUtils.removeAll() method is called with an empty first parameter, but the method does not throw the appropriate NullPointerException. Instead, it throws an IllegalArgumentException, which does not clearly reflect the issue.

The solution to this bug involves updating the CollectionUtils.removeAll() method to throw the appropriate NullPointerException when called with an empty first parameter. To do this, the developers modified the code to include a null check on the first parameter before performing any operations. If the first parameter is null, then the correct exception is thrown. The project contributors added new tests to ensure that the bug is detected if it reoccurs in the future.

### 3. Netflix : Chaos Engineering

experiments conducted by Netflix can be : 

- Terminating virtual machine instances,
- Injecting latency into requests between services,
- Failing requests
- Using malformed values in runtime configuration parameters,
- Failing internal services,
- Making an entire Amazon region unavailable.

To successfully conduct Chaos Engineering experiments, it is important to build a hypothesis around steady state behavior, vary real-world events, run experiments in production, and automate experiments to run continuously.

During Chaos Engineering experiments, Netflix engineers closely monitor variables such as SPS (stream starts per second) and new account signups per second to identify unexpected changes that may indicate a problem with the system. They also observe request latency and CPU utilization to detect any signs of degraded mode operation that may not be apparent from the user's perspective.

Through their Chaos Engineering experiments, Netflix found that their system was able to provide content even under difficult conditions, demonstrating its resilience. They also discovered that Chaos Engineering tests were more effective in improving system reliability than traditional failover tests.

Many other companies, such as Amazon, Google, Facebook, and Microsoft, have also adopted this technique to improve the reliability of their systems. By simulating outages such as server failure, network congestion, or system overload. The system variables to be observed during experiments may include response times.

### 4. WebAssembly : Formal Specification

#### the main advantages of having a formal specification for WebAssembly.

*Clarity and understanding*: A formal specification provides a precise and explicit definition of the syntax, semantics, and behavior of the language. This helps developers better understand how to use WebAssembly effectively and avoid costly programming errors.

*Interoperability*: A formal specification ensures that all implementations of WebAssembly follow the same rules, making it easier to achieve interoperability between different platforms and tools. Developers can be assured that their code will work the same way on all platforms that support WebAssembly.

*Security*:  Specifications can include strict rules for memory manipulation, exception handling, and access to system resources. This can help reduce the risk of security vulnerabilities and exploits. Developers can use the specification to ensure that their code adheres to WebAssembly security policies.

#### does this mean that WebAssembly implementations should not be tested?

This does not mean that WebAssembly implementations should not be tested. Testing allows for verifying that the implementation adheres to the established rules in the specification and that it works correctly in different contexts. 

### 5. Isabelle/HOL

The mechanized specification indeed helped to improve the original formal specification of the language by identifying several design errors and providing formal proofs of their correction. By using formal verification tools, it is possible to mathematically prove the correctness of the specification.

The author verified the specification using a formal verification tool called Isabelle/HOL. The formal proofs generated by this tool ensure that the specification is correct and consistent.

However, testing is still necessary, they can identify programming errors that are not covered by the formal specification.


[CNN Article](https://edition.cnn.com/2019/01/29/tech/facetime-bug-teen-discovery/index.html)


The article is titled "This 14-year old found Apple’s FaceTime bug before it went viral " and it was published on CNN website on January 30, 2019. 
The bug allowed a caller to hear the audio from the recipient's iPhone before they answered the call, and in some cases, even see video from the recipient's phone. The issue was discovered by a 14-year-old boy from Arizona, who was trying to set up a group chat in FaceTime with his friends. When he realized he could hear audio from a friend's phone before the friend had even answered the call.
Apple initially responded to the bug by disabling the group chat feature in FaceTime, and later released a software update to fix the issue. The article notes that the incident raised questions about how thoroughly Apple tests its software before releasing it to the public, and whether the company is doing enough to prioritize user privacy and security.
This highlighted the need to conduct rigorous testing before launching any feature on a consumer product. This would have enabled Apple to fix the bug before customers were affected and before it had a negative impact on the company's image.













