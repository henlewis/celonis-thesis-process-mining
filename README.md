# Celonis Thesis Process Mining Dashboard

A solo process mining project built in **Celonis** to analyse a university master thesis submission, evaluation, defence, and archiving process.

The project uses event log data to reconstruct the real process flow, compare it against the expected thesis procedure, identify bottlenecks and deviations, test management hypotheses, and translate findings into operational recommendations.

**Final grade:** 20/20
**Author:** Henry Lewis
**Tool:** Celonis Process Intelligence
**Project type:** Process Mining / Business Process Intelligence / Operational Analytics

---

## Live Dashboard

The live Celonis dashboard can be accessed here:

[View Live Celonis Dashboard](https://academic-celonis-hntd5s.eu-2.celonis.cloud/package-manager/ui/views/ui/spaces/4edfb2eb-5117-435c-bea5-0d3652ecec04/packages/fc9b89a4-ec7a-48d0-b19f-e5e8f8acd4b7/nodes/e88b0f5c-947d-4c0a-9a72-24e6be564687?activeTabs=cover:0b57881e-6c58-408d-9bac-a16e2b3383eb&share=993546fd-8c03-4dbd-a728-b36d82af33d2&bookmark=false)

Access may depend on Celonis academic sharing permissions.

---

## Project Overview

The aim of this project was to analyse the **master thesis management process** at the fictional Tagus Institute of Technology and Management.

The process covers the full lifecycle from thesis submission to final notification, including:

* Thesis submission
* Course completion checks
* Supervisor approval
* NetPA registration
* Structure and reference review
* Plagiarism checking
* Jury proposal and validation
* Defence scheduling
* Defence completion
* Grade validation
* Final corrections
* Repository archiving
* Final student notification

The project was designed to answer the central question:

> How is the master thesis management process executed in practice, and which deviations, bottlenecks, or contextual factors explain the main process issues?

---

## Business Problem

The school management team was concerned that the thesis process was suffering from:

* Repeated correction loops
* Delays caused by structure, reference, and plagiarism issues
* Jury validation problems
* Defence rescheduling
* Lack of process transparency
* Differences in supervision practices
* Unclear reasons for process delays

Before the analysis, these issues were mostly based on internal perception. Process mining was used to replace assumptions with data-driven evidence.

---

## Dataset

The analysis was based on two connected data sources:

### Case Table

The case table provided one row per thesis case, including contextual information such as:

| Field            | Purpose                                                   |
| ---------------- | --------------------------------------------------------- |
| Case ID          | Unique thesis identifier                                  |
| Student number   | Student identifier                                        |
| Nationality      | Used to analyse scheduling patterns                       |
| Master programme | Used to compare corrections and performance               |
| Supervisor       | Used to analyse correction and rescheduling concentration |
| Gender           | Used to compare performance                               |
| Age              | Used to explore demographic performance differences       |
| Final grade      | Used as the student performance indicator                 |

### Event Log

The event log recorded the sequence of activities for each thesis case.

| Field     | Purpose                                            |
| --------- | -------------------------------------------------- |
| Case ID   | Connects events to each thesis case                |
| Timestamp | Orders events and supports throughput calculations |
| Activity  | Identifies each process step                       |
| Resource  | Identifies the actor responsible for the event     |

---

## Dataset Scope

| Metric                      |    Value |
| --------------------------- | -------: |
| Thesis cases analysed       |      500 |
| Events analysed             |    9,698 |
| Activities in dashboard     |       24 |
| Process variants identified |       41 |
| Happy path cases            |      119 |
| Cases with deviations       |      381 |
| Happy path conformance rate |    23.8% |
| Average throughput time     | 102 days |
| Cases with correction loops |      216 |

---

## Expected Happy Path

The expected thesis process was modelled as a 17-step happy path.

| Step | Expected Activity                 |
| ---: | --------------------------------- |
|    1 | Receive Thesis Submission         |
|    2 | Check Course Completion           |
|    3 | Confirm Final Supervisor Approval |
|    4 | Register Submission in NetPA      |
|    5 | Review Structure and References   |
|    6 | Check Plagiarism                  |
|    7 | Request Jury Proposal             |
|    8 | Receive Jury Proposal             |
|    9 | Validate Jury                     |
|   10 | Schedule Defense                  |
|   11 | Send Defense Invitation           |
|   12 | Conduct Defense                   |
|   13 | Receive Grades in NetPA           |
|   14 | Validate Grades                   |
|   15 | Check Need for Final Corrections  |
|   16 | Archive Thesis in Repository      |
|   17 | Send Final Notification           |

This expected path was used as the basis for conformance checking.

---

## Dashboard Structure

The final Celonis dashboard was organised into seven main pages.

| Dashboard Page               | Purpose                                                  |
| ---------------------------- | -------------------------------------------------------- |
| Cover                        | Executive overview with headline KPIs                    |
| Variant Explorer             | Shows process fragmentation and the most common variants |
| Process Explorer             | Visualises the real process flow and deviation points    |
| Conformance Checking         | Compares real execution against the ideal happy path     |
| Case Explorer / Demographics | Allows case-level and contextual exploration             |
| Hypothesis Testing           | Tests the six management hypotheses                      |
| Action Plan                  | Converts findings into practical improvement actions     |

---

## Key Findings

### 1. The Process Is Highly Variable

The dashboard identified **41 distinct process variants** across only **500 thesis cases**.

The most common path covered just **119 cases**, meaning only around **24%** of theses followed the dominant process path.

This shows that the official thesis process exists on paper, but the real process is much more fragmented in practice.

---

### 2. Happy Path Conformance Is Low

The Adherence Explorer showed a **23.8% happy path conformance rate**.

| Conformance Metric     | Value |
| ---------------------- | ----: |
| Happy path cases       |   119 |
| Cases with deviations  |   381 |
| Conformance rate       | 23.8% |
| Cases with corrections |   216 |

This means most thesis cases deviated from the expected process in some way.

---

### 3. Correction Loops Are the Largest Deviation Driver

The biggest issue was repeated correction activity.

| Deviation Type             | Cases Affected |
| -------------------------- | -------------: |
| Correction loops           |            216 |
| Final corrections required |            135 |
| Rescheduled defences       |             88 |
| Jury revisions             |             84 |
| Rejected submissions       |             46 |
| Failed defences            |             10 |

The largest improvement opportunity is therefore reducing avoidable rework before the process reaches later stages.

---

### 4. The Issue Is More About Process Consistency Than Student Performance

The analysis did not strongly support the idea that thesis problems were mainly caused by weaker students or demographic differences.

Instead, the evidence pointed toward:

* Differences in supervision practices
* Inconsistent pre-submission quality control
* Scheduling coordination issues
* Process monitoring gaps
* Rework loops that could be detected earlier

---

## Hypothesis Testing

The school director raised six hypotheses. The dashboard was used to evaluate each one.

| Hypothesis | Focus                           | Verdict            | Interpretation                                                     |
| ---------- | ------------------------------- | ------------------ | ------------------------------------------------------------------ |
| H1         | Supervisor correction variation | Confirmed          | Correction loops vary meaningfully by supervisor                   |
| H2         | Defence rescheduling drivers    | Partially rejected | Jury availability is not the only likely driver                    |
| H3         | Informatics correction rate     | Rejected           | Informatics was not the highest group for post-defence corrections |
| H4         | Correction loop persistence     | Weakly confirmed   | Initial corrections slightly increase final correction risk        |
| H5         | Demographic performance effect  | Rejected           | Grades were similar across demographic groups                      |
| H6         | Supervision practice effect     | Confirmed          | Issues cluster around certain supervisors                          |

The strongest evidence points to **process consistency and supervision practice**, rather than student performance.

---

## Management Recommendations

The final action plan focused on five practical improvement areas.

| Priority | Recommendation                   | Expected Value                                                                      |
| -------: | -------------------------------- | ----------------------------------------------------------------------------------- |
|        1 | Targeted supervisor development  | Reduce repeated correction loops by supporting supervisors with higher rework rates |
|        2 | Pre-submission quality checklist | Prevent avoidable structure, reference, formatting, and plagiarism issues           |
|        3 | Earlier jury formation           | Reduce jury revisions and defence rescheduling pressure                             |
|        4 | Real-time risk monitoring        | Flag cases with correction loops, reschedules, or final corrections earlier         |
|        5 | International scheduling support | Support student groups with higher rescheduling rates                               |

The main recommendation is not to redesign the entire thesis process, but to reduce avoidable variation in the existing process.

---

## Value Generated

This project demonstrates how process mining can support management decision-making by:

* Reconstructing the real process from event data
* Measuring process variation
* Identifying non-conforming cases
* Quantifying the scale of rework
* Testing management hypotheses
* Separating perception from evidence
* Highlighting where operational support is needed
* Turning process insights into targeted actions

The dashboard helps management move from reactive problem-solving to proactive thesis process monitoring.

---

## Tools and Methods Used

* Celonis Process Intelligence
* Process Mining
* Event Log Analysis
* Case Table Modelling
* Process Discovery
* Variant Analysis
* Conformance Checking
* Performance Analysis
* Hypothesis Testing
* KPI Dashboard Design
* Business Process Improvement
* PQL-based calculated metrics
* Management reporting

---

## Celonis Components Used

The dashboard made use of several Celonis process mining components, including:

* Variant Explorer
* Process Explorer
* Adherence Explorer
* Case Explorer
* KPI cards
* Performance Spectrum
* Activity frequency analysis
* Case-level drilldowns
* Hypothesis testing visualisations
* Risk monitoring table
* Management action plan page

---

## Files Included

| File                    | Description                                         |
| ----------------------- | --------------------------------------------------- |
| `CelonisDashboard.pdf`  | Exported PDF version of the final Celonis dashboard |
| `TITM REPORT.pdf`       | Full written process intelligence report            |
| `TITM PRESENTATION.pdf` | Final presentation summarising the project          |
| `README.md`             | Project documentation and portfolio summary         |

---

## Limitations

Several limitations should be considered when interpreting the results:

1. **Offline dataset**
   The dashboard is based on historical data rather than a live operational data feed.

2. **Missing reason codes**
   The event log records that an event happened, but not always why it happened. For example, it records defence rescheduling but not the exact reason behind every reschedule.

3. **Association, not causation**
   Patterns by supervisor or nationality should be interpreted as signals for further investigation, not direct proof of causality.

4. **Group size differences**
   Some demographic or programme groups are smaller than others, so average-based comparisons may be more volatile.

5. **Model-dependent conformance**
   Conformance results depend on how the expected happy path is defined.

---

## Key Skills Demonstrated

This project demonstrates experience in:

* Process mining
* Business process analysis
* Celonis dashboard development
* Event log modelling
* Conformance checking
* Variant analysis
* KPI design
* Operational analytics
* Management hypothesis testing
* Business recommendations
* Data storytelling
* Report writing
* Executive dashboard design
* Translating technical analysis into management action

---

## Project Status

Completed as a solo Process Intelligence project.

The final solution includes:

* A live Celonis dashboard
* A dashboard PDF export
* A full written report
* A presentation deck
* Evidence-based management recommendations

---

## Author

**Henry Lewis**

Bachelor’s in Data Science
NOVA IMS

---

## License

This repository is intended for educational and portfolio purposes.
