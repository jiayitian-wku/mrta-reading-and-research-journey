# Cross-Paper Comparison

| Dimension                       | A Formal                                                                                                                                                                                                                                                                                               | SOLD! | CBBA-PR |
| ------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | ----- | ------- |
| **Main Problem**                | How to formally define and classify Multi-Robot Task Allocation (MRTA) problems, and connect different MRTA classes to known optimization problems and solution methods.                                                                                                                               |       |         |
| **MRTA Setting**                | Proposes a three-axis taxonomy: **ST/MT × SR/MR × IA/TA**, giving **2×2×2 = 8 MRTA problem classes**.                                                                                                                                                                                                  |       |         |
| **Static / Dynamic**            | **Not simply static.** IA means the current assignment is considered at one instant, but allocation may still be repeated, iterative, or online. TA explicitly considers future assignments over time.                                                                                                 |       |         |
| **Centralized / Decentralized** | **Not fixed to one architecture.** The taxonomy classifies MRTA problems rather than prescribing a single centralized or decentralized algorithm; different methods can be used for different classes.                                                                                                 |       |         |
| **Main Method**                 | Formalizes MRTA using ideas from the **Optimal Assignment Problem (OAP)**, builds a taxonomy from three binary dimensions, and analyzes representative approaches for different problem classes.                                                                                                       |       |         |
| **Key Assumptions**             | Robot–task assignments can be evaluated through utility/cost; the structure of the allocation problem depends strongly on whether robots can perform one or multiple tasks, whether tasks require one or multiple robots, and whether future allocations must be considered.                           |       |         |
| **Main Guarantee**              | There is **no single universal guarantee for all MRTA problems**. For simpler classes such as **ST-SR-IA**, the problem can be reduced to classical assignment formulations for which efficient optimal algorithms exist. Guarantees become weaker or computationally harder for more complex classes. |       |         |
| **Main Limitation**             | The paper provides a **formal framework and taxonomy rather than one complete MRTA algorithm**. It does not present a unified simulation comparison across all eight classes, and real-world performance still depends heavily on how utility, communication, uncertainty, and dynamics are modeled.   |       |         |

## How the Three Papers Connect

### Paper 001 — A Formal Analysis and Taxonomy of Task Allocation in Multi-Robot Systems

This paper provides the **conceptual foundation** for the following papers.

My current understanding is:

**MRTA problem definition → taxonomy → identify the specific MRTA class → choose/design an appropriate allocation algorithm**

The paper is therefore mainly answering:

> **“What kind of MRTA problem are we solving?”**

rather than proposing one specific new task-allocation algorithm.

After reading the next two papers, I will use this taxonomy to determine:

* which MRTA class SOLD! belongs to;
* which MRTA class CBBA-PR belongs to;
* how their assumptions differ;
* why their algorithms are designed differently;
* and how they deal with increasingly dynamic task-allocation environments.

## Questions I Still Have

After completing Paper 001, my main remaining questions have shifted from understanding the taxonomy itself to understanding how it is used in later MRTA research:

1. How are modern MRTA algorithms mapped onto the eight taxonomy classes in practice?
2. Where exactly should **SOLD!** be placed in this taxonomy?
3. Where exactly should **CBBA-PR** be placed in this taxonomy?
4. How do later algorithms handle dynamic task arrivals, robot failures, and replanning beyond the basic taxonomy?
5. How important is the **utility model** in determining the quality of an MRTA solution?

These questions will be revisited while reading Papers 002 and 003.
