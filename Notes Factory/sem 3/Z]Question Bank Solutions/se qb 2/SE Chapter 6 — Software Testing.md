# SE Chapter 6 — Software Testing (6-Mark Answers) 
> [!caution] just to be safe the answers are wrriten as per 6 marks instead of 4 marks


> [!check] Read this context before answering the questions
>
> Software testing checks whether software meets requirements and works correctly. In a test case, provide the input, state the expected result, run the software, record the actual result, and mark the status as **Pass** or **Fail**. 
The actual result and status below are sample results for a correctly functioning system; during real testing, record what the software actually does.
>
> **Test case format used in these notes:** Test Case ID | Input | Expected Result | Actual Result | Status. A **Technique** column is added where it helps explain how the test case was designed.
>
> **Status rule:** Pass = actual result matches expected result. Fail = actual result differs from expected result. If the test has not been executed, write **Not Run** rather than inventing an actual result.
>
> **Testing levels in brief:** Unit testing checks one component; 
integration testing checks communication between components/modules; 
system testing checks the complete application;
>  acceptance testing checks whether it meets user needs.
> Alpha testing is internal and controlled;
> beta testing is performed by selected real users in real-world conditions.

## Quick Navigation

### Group 1 — Alpha and Beta Testing
| Full question | Jump to answer |
|---|---|
| Differentiate between Alpha Testing and Beta Testing based on testing environment, participants, objectives, and timing, with suitable examples. | <a href="#alpha-beta-difference">Go to answer</a> |
| Analyze the role of Alpha and Beta Testing in the software release cycle. Explain how each contributes to software quality assurance. | <a href="#alpha-beta-role">Go to answer</a> |
| Explain Alpha Testing and describe its environment, participants, objectives, and importance before product release. | <a href="#alpha-testing">Go to answer</a> |
| Explain Beta Testing and describe its main objective and role in obtaining feedback from real users. | <a href="#beta-testing">Go to answer</a> |
| Analyze the role of Beta Testing in an AI-based Sugarcane Irrigation Prediction System. Explain how farmer feedback can help improve the system before final deployment. | <a href="#sugarcane-beta">Go to answer</a> |
| Explain how Alpha Testing and Beta Testing can be applied to an AI-based Urine Test Health Monitoring System before its final deployment. | <a href="#urine-alpha-beta">Go to answer</a> |

## Group 1 — Alpha and Beta Testing

<p id="alpha-beta-difference"></p>

### 1. Differentiate between Alpha Testing and Beta Testing based on testing environment, participants, objectives, and timing, with suitable examples.

| Basis | Alpha Testing | Beta Testing |
|---|---|---|
| Environment | Controlled environment, usually at the developer's site | Real-world environment outside the development team |
| Participants | Developers, QA team and internal stakeholders | Selected real users or target customers |
| Objective | Find major defects, crashes and functional problems | Find remaining defects and collect usability feedback |
| Timing | Before beta testing | After alpha testing and before final release |
| Example | QA team tests a health app in the company's lab | Patients and healthcare staff try the app in normal use |

**Conclusion:** Alpha testing finds defects internally, while beta testing checks the product with real users and real-world conditions.

<p id="alpha-beta-role"></p>

### 2. Analyze the role of Alpha and Beta Testing in the software release cycle. Explain how each contributes to software quality assurance.

1. **Alpha testing:** Internal testers examine functionality, stability, usability and major defects in a controlled environment.
2. **Defect correction:** The development team fixes issues reported during alpha testing and retests the corrections.
3. **Beta testing:** A selected group of real users tries the nearly complete product in real-world conditions.
4. **Feedback collection:** Users report practical problems, confusing features, compatibility issues and improvement suggestions.
5. **Final improvement:** Developers use the feedback to correct defects and improve the product before release.

**Conclusion:** Alpha testing improves technical quality; beta testing improves real-world suitability and user satisfaction. Together, they reduce release risk.

<p id="alpha-testing"></p>

### 3. Explain Alpha Testing and describe its environment, participants, objectives, and importance before product release.

**Alpha testing** is acceptance testing performed by internal teams at the developer's site before the software is released to external users.

1. **Environment:** It takes place in a controlled environment using prepared test data and test cases.
2. **Participants:** Developers, QA engineers and internal stakeholders take part.
3. **Objectives:** Find functional defects, crashes, usability problems and stability issues.
4. **Process:** Review requirements, prepare test cases, execute tests, log defects, fix them and retest.
5. **Importance:** It detects major problems early, improves reliability and reduces the risk of failure during beta testing or release.

**Example:** The internal QA team tests login, report generation and abnormal-input handling in a health-monitoring application before giving it to external users.

<p id="beta-testing"></p>

### 4. Explain Beta Testing and describe its main objective and role in obtaining feedback from real users.

**Beta testing** is testing a nearly complete software product by real users in real-world conditions before final release.

1. **Participants:** Selected target users or customers outside the development team.
2. **Environment:** The application is used on users' actual devices, networks and workflows.
3. **Objective:** Discover remaining bugs, usability issues, compatibility problems and performance concerns.
4. **Feedback:** Users report errors, confusing workflows and features that need improvement.
5. **Process:** Recruit users, distribute the beta version, collect reports, analyse feedback, fix issues and prepare the release.

**Example:** Farmers use a beta irrigation-advisory app on their farms and report whether its recommendations are understandable and practical.

**Conclusion:** Beta testing verifies how well the software works for real users and helps improve it before final deployment.

<p id="sugarcane-beta"></p>

### 5. Analyze the role of Beta Testing in an AI-based Sugarcane Irrigation Prediction System. Explain how farmer feedback can help improve the system before final deployment.

**Purpose:** Beta testing checks whether the irrigation system's predictions and recommendations are useful under real farming conditions.

| Test Case ID | Input | Expected Result | Actual Result | Status |
|---|---|---|---|---|
| SB-01 | Soil moisture is low and weather is dry | System recommends irrigation | System recommends irrigation | Pass |
| SB-02 | Soil moisture is high and rain is forecast | System avoids an unnecessary irrigation recommendation | System avoids unnecessary irrigation | Pass |
| SB-03 | Sensor reading is missing | System displays a sensor-data warning instead of an unsafe recommendation | Warning is displayed | Pass |
| SB-04 | Farmer changes the crop stage | Recommendation updates using the selected crop stage | Recommendation updates | Pass |

**How farmer feedback helps:**
1. Farmers report whether recommendations match actual soil and crop conditions.
2. They identify unclear alerts, inconvenient timing and missing information.
3. Their reports help reveal sensor, connectivity and usability problems.
4. Developers analyse feedback, improve the model or interface, and retest before final deployment.

**Conclusion:** Beta testing evaluates real-world usefulness; agronomists and system owners should review safety-critical recommendations before release.

<p id="urine-alpha-beta"></p>

### 6. Explain how Alpha Testing and Beta Testing can be applied to an AI-based Urine Test Health Monitoring System before its final deployment.

**Alpha testing — internal and controlled**

| Test Case ID | Input | Expected Result | Actual Result | Status |
|---|---|---|---|---|
| UA-01 | Valid sample result values | System processes values and displays the result summary | Summary is displayed | Pass |
| UA-02 | Required sample field is missing | System requests the missing value | Validation message appears | Pass |
| UA-03 | Invalid value or unsupported format | System rejects the input and explains the error | Input is rejected | Pass |

Developers and QA staff test input validation, calculations, access control, privacy, error handling and report generation.

**Beta testing — real-world evaluation**

| Test Case ID | Input | Expected Result | Actual Result | Status |
|---|---|---|---|---|
| UB-01 | User enters a valid test report | Report is saved and shown to the authorised user | Report is saved and shown | Pass |
| UB-02 | User tries to open another person's record without permission | Access is denied | Access is denied | Pass |
| UB-03 | User views an abnormal result | System explains the result appropriately and advises consultation with a qualified clinician | Guidance is displayed | Pass |

Real users and authorised healthcare professionals assess usability, clarity, device compatibility and workflow. Medical interpretation must be clinically validated; the system should not present AI output as a confirmed diagnosis.

---

### Group 2 — Testing Strategies and Software Quality
| Full question | Jump to answer |
|---|---|
| Analyze different strategies for conventional software testing and explain how they help improve software quality. | <a href="#conventional-strategy">Go to answer</a> |
| Analyze the difference between strategic testing and ad-hoc testing. Explain how a systematic testing strategy improves software quality. | <a href="#strategic-ad-hoc">Go to answer</a> |
| Explain Unit Testing and describe its purpose, scope, and the role of developers in performing it. | <a href="#unit-testing">Go to answer</a> |
| Explain how Unit Testing can be applied to an AI-based Thermal Battery Monitoring System. Give examples of components or functions that can be tested independently. | <a href="#battery-unit">Go to answer</a> |
| Analyze suitable testing strategies for an AI-based Satellite Monitoring System. Consider telemetry data processing, anomaly detection, and alert generation. Justify your answer. | <a href="#satellite-strategy">Go to answer</a> |

## Group 2 — Testing Strategies and Software Quality

<p id="conventional-strategy"></p>

### 7. Analyze different strategies for conventional software testing and explain how they help improve software quality.

Conventional software testing proceeds from small components to the complete system.

1. **Unit testing:** Tests individual functions, methods or modules independently.
2. **Integration testing:** Tests communication and data exchange between connected modules.
3. **Validation testing:** Checks whether the software satisfies user and customer requirements.
4. **System testing:** Tests the complete integrated application, including performance, security and recovery where applicable.
5. **Acceptance testing:** Confirms that the product is suitable for the intended users and business needs.

Testing scope becomes broader as development progresses. Finding defects early reduces debugging effort, prevents failures from spreading across modules and improves reliability.

**Example:** In an irrigation system, test the sensor-reading function first, then sensor-to-prediction integration, then the complete recommendation and notification workflow.

<p id="strategic-ad-hoc"></p>

### 8. Analyze the difference between strategic testing and ad-hoc testing. Explain how a systematic testing strategy improves software quality.


| Basis | Strategic / Systematic Testing | Ad-hoc Testing |
| --- | --- | --- |
| 1. Planning | Planned using requirements, risks and test objectives | Performed informally without detailed planning |
| 2. Test cases | Uses documented test cases | Test cases may not be documented |
| 3. Coverage | Coverage can be measured and tracked | Coverage is difficult to measure |
| 4. Execution | Follows a defined testing process | Tester explores the software freely |
| 5. Repeatability | Tests can be repeated easily after changes | Tests are harder to reproduce |
| 6. Purpose | Ensures systematic quality assurance and regression testing | Helps discover unexpected defects quickly |

A systematic strategy assigns test levels, priorities, data, environments and exit criteria. It improves traceability, repeatability and coverage. Ad-hoc testing can supplement it, but should not replace planned testing.

1.  Better test coverage: Ensures that important features and requirements are tested.
    
2.  Early defect detection: Identifies errors before they become costly to fix.
    
3.  Repeatability: Allows tests to be repeated after software changes.
    
4.  Traceability: Connects test cases with software requirements.
    
5.  Reduced risk: Helps identify critical defects before release.
    
6.  Improved reliability: Ensures the software behaves consistently and meets user expectations.
    

Example: In an AI-based Heat Wave Monitoring System, testers prepare test cases for normal temperatures, extreme temperatures and missing sensor data. They verify that alerts are generated correctly and errors are handled safely. After fixing defects, they repeat the tests to ensure the system works correctly.

Conclusion: A systematic testing strategy improves software quality by increasing test coverage, detecting defects early and ensuring reliable software before release.
<p id="unit-testing"></p>

### 9. Explain Unit Testing and describe its purpose, scope, and the role of developers in performing it.

**Unit testing** checks the smallest testable software component independently, such as a function, method, class or module.

1. **Purpose:** Detect coding and logic errors early.
2. **Scope:** One component is tested in isolation, often using mock data or stubs for dependencies.
3. **Developer's role:** Write test cases, run tests, compare actual and expected results, debug failures and retest fixes.
4. **Benefits:** Makes defects easier to locate, supports safe code changes and reduces the cost of fixing errors later.
5. **Example:** Test a function that converts a sensor reading into a battery-temperature status without connecting the entire monitoring application.

Unit testing does not replace integration or system testing because a correct component may still fail when connected to other components.

<p id="battery-unit"></p>

### 10. Explain how Unit Testing can be applied to an AI-based Thermal Battery Monitoring System. Give examples of components or functions that can be tested independently.

Unit testing checks each function independently before combining the complete battery-monitoring system.

| Test Case ID | Input | Expected Result | Actual Result | Status | Technique |
|---|---|---|---|---|---|
| TB-U01 | Temperature = 45°C; warning threshold = 50°C | Status is Normal | Status is Normal | Pass | Boundary/condition check |
| TB-U02 | Temperature = 55°C; warning threshold = 50°C | Overheating warning is returned | Overheating warning is returned | Pass | Condition testing |
| TB-U03 | Temperature input is missing | Function returns a validation error | Validation error is returned | Pass | Negative testing |
| TB-U04 | Sensor reading = 150°C, allowed range is -20°C to 120°C | Reading is rejected or flagged as out of range | Reading is flagged | Pass | Boundary value analysis |
| TB-U05 | Valid feature values supplied to prediction function | Function returns a valid prediction in the defined output format | Valid prediction is returned | Pass | Unit / output validation |

**Components to test independently:** sensor-value validation, temperature conversion, threshold comparison, prediction preprocessing, anomaly-score calculation and alert-message formatting.

The expected thresholds and outputs must come from the system specification and validated model behaviour. These sample values illustrate the test format, not a medical or engineering safety standard.

<p id="satellite-strategy"></p>

### 11. Analyze suitable testing strategies for an AI-based Satellite Monitoring System. Consider telemetry data processing, anomaly detection, and alert generation. Justify your answer.

Use a layered strategy because satellite monitoring depends on data accuracy, AI predictions and timely alerts.

1. **Unit testing:** Test telemetry parsing, missing-value handling, unit conversion and anomaly-score functions independently.
2. **Integration testing:** Verify that telemetry is correctly passed to the anomaly-detection model and that its output reaches the alert service.
3. **System testing:** Test the complete flow from telemetry ingestion to dashboard and alert generation.
4. **Performance and reliability testing:** Check high telemetry volume, delayed messages, network interruptions and recovery.
5. **Acceptance testing:** Confirm with system operators that alerts are understandable, timely and useful.

**Justification:** Unit tests find local logic errors, integration tests detect data-flow issues, and end-to-end tests verify that anomalies produce the correct operational alert. AI models should also be evaluated against labelled normal and anomalous data, with false positives and false negatives measured.

---

### Group 3 — Black Box, White Box, Static and Dynamic Testing
| Full question | Jump to answer |
|---|---|
| Compare White Box Testing and Black Box Testing based on techniques, objectives, advantages, limitations, and suitable applications. Give examples. | <a href="#white-black">Go to answer</a> |
| Analyze the limitations of Black Box Testing and explain how White Box Testing can complement it in large-scale software applications. | <a href="#black-limitations">Go to answer</a> |
| Differentiate between Static Testing and Dynamic Testing and explain when each method is appropriate. | <a href="#static-dynamic">Go to answer</a> |
| Explain White Box Testing and describe the types of programming errors that it can help identify. | <a href="#white-box">Go to answer</a> |
| Explain Black Box Testing and describe how requirements and specifications are used to design test cases. | <a href="#black-box">Go to answer</a> |
| Compare Verification and Validation in software testing and explain their importance with suitable examples. | <a href="#verification-validation">Go to answer</a> |
| Compare Verification and Validation for an AI-based Urine Test Health Monitoring System. Give suitable examples of activities performed during each. | <a href="#urine-vv">Go to answer</a> |

## Group 3 — Black Box, White Box, Static and Dynamic Testing

<p id="white-black"></p>

### 12. Compare White Box Testing and Black Box Testing based on techniques, objectives, advantages, limitations, and suitable applications. Give examples.

| Basis | White Box Testing | Black Box Testing |
|---|---|---|
| Knowledge | Requires knowledge of internal code and logic | Does not require knowledge of internal code |
| Focus | Statements, branches, conditions, paths and loops | Inputs, outputs and external behaviour |
| Techniques | Statement coverage, branch coverage, path testing, condition testing | Equivalence partitioning, boundary value analysis, error guessing, state-transition testing |
| Advantages | Finds logic errors and unexecuted code paths | Checks functionality from the user's perspective |
| Limitations | Requires code access and technical skill; complete path coverage may be impractical | Cannot directly show which internal code path caused a defect |
| Example | Test every branch of a battery-overheat decision function | Enter high temperature and verify that the system displays an alert |

**Conclusion:** Both methods complement each other: black box testing checks required behaviour, while white box testing checks internal implementation and logic.

<p id="black-limitations"></p>

### 13. Analyze the limitations of Black Box Testing and explain how White Box Testing can complement it in large-scale software applications.

**Limitations of Black Box Testing:**
1. It cannot directly inspect internal code or logic.
2. It may miss untested paths, branches and internal conditions.
3. Test cases depend on the completeness of requirements.
4. A large input space makes exhaustive testing impractical.
5. It may reveal a failure without identifying its exact internal cause.

**How White Box Testing complements it:**
1. Statement and branch coverage reveal untested code.
2. Condition and path testing examine internal decision logic.
3. Unit tests help isolate the component causing a defect.
4. Combining both approaches checks both external behaviour and internal implementation.

**Example:** Black box tests verify that a satellite alert appears for anomalous telemetry; white box tests check the threshold logic and branches that decide whether the alert is triggered.

<p id="static-dynamic"></p>

### 14. Differentiate between Static Testing and Dynamic Testing and explain when each method is appropriate.

| Basis | Static Testing | Dynamic Testing |
|---|---|---|
| Execution | Code is not executed | Software is executed |
| Main focus | Documents, requirements, design and source code | Runtime behaviour and actual outputs |
| Methods | Reviews, walkthroughs, inspections, static analysis | Unit, integration, system and acceptance tests |
| Defects found | Ambiguous requirements, coding-standard violations, unreachable code and design issues | Incorrect outputs, crashes, runtime errors and performance problems |
| When suitable | Early in development and during code review | Once executable software or a testable build is available |
| Example | Review the battery alarm algorithm before running it | Enter a high temperature and check whether an alarm appears |

**Conclusion:** Static testing can find defects early without execution; dynamic testing confirms actual behaviour when the software runs. Both are needed.

<p id="white-box"></p>

### 15. Explain White Box Testing and describe the types of programming errors that it can help identify.

**White Box Testing** examines internal program structure and logic. The tester knows how the code is written and designs tests to exercise statements, branches, conditions and paths.

**Techniques:**
1. **Statement coverage:** Execute each statement at least once.
2. **Branch coverage:** Test each decision outcome, such as true and false.
3. **Condition testing:** Test individual Boolean conditions.
4. **Path testing:** Exercise selected execution paths through the code.
5. **Loop testing:** Check loop behaviour for zero, one and multiple iterations where applicable.

**Errors identified:** Incorrect conditions, wrong calculations, off-by-one loop errors, unreachable code, incorrect variable use, unhandled exceptions and some security weaknesses.

**Example:** For `if (temperature > threshold)`, test values below, equal to and above the threshold to check whether the intended branch executes. White box testing cannot prove the complete absence of defects, but it improves code-level coverage.

<p id="black-box"></p>

### 16. Explain Black Box Testing and describe how requirements and specifications are used to design test cases.

**Black Box Testing** checks software functionality by supplying inputs and comparing actual outputs with expected outputs, without inspecting the internal code.

**How requirements become test cases:**
1. Identify each functional requirement and its acceptance criteria.
2. Identify valid, invalid and boundary inputs.
3. Write test cases with input, expected result and a unique ID.
4. Execute each case and record actual result and status.
5. Report failures and retest after correction.

**Common techniques:** Equivalence partitioning, boundary value analysis, error guessing, cause-effect graphing and state-transition testing.

**Example requirement:** Soil moisture must be between 0% and 100%.

| Test Case ID | Input | Expected Result | Actual Result | Status | Technique |
|---|---|---|---|---|---|
| BB-01 | 40% | Accept the value | Value accepted | Pass | Equivalence partitioning |
| BB-02 | -1% | Reject as below range | Value rejected | Pass | Boundary value analysis |
| BB-03 | 101% | Reject as above range | Value rejected | Pass | Boundary value analysis |
| BB-04 | Missing value | Show a validation message | Message shown | Pass | Error guessing |

This process makes testing traceable to the written requirements.

<p id="verification-validation"></p>

### 17. Compare Verification and Validation in software testing and explain their importance with suitable examples.

| Basis | Verification | Validation |
|---|---|---|
| Main question | Are we building the product correctly? | Are we building the right product? |
| Focus | Requirements, design, code and standards | Actual product behaviour and user needs |
| Common activities | Reviews, inspections, walkthroughs and static analysis | Executing tests, system testing and user acceptance testing |
| Execution | Often performed without executing the software | Usually involves executing the software |
| Example | Review the banking transfer design against the requirement | Transfer money in the running application and check the balance |

**Importance:**
1. Detects defects at different stages.
2. Checks conformance to requirements and design standards.
3. Confirms the finished software meets user needs.
4. Reduces rework and improves quality.

**Conclusion:** Verification checks work products during development; validation checks whether the resulting product meets its intended purpose.

<p id="urine-vv"></p>

### 18. Compare Verification and Validation for an AI-based Urine Test Health Monitoring System. Give suitable examples of activities performed during each.

| Verification activities — checking work products | Validation activities — checking running software |
|---|---|
| Review requirements for supported urine-test fields and units | Enter a valid test report and verify it is displayed correctly |
| Inspect the design of result processing and access permissions | Check that an unauthorised user cannot access a patient's record |
| Review code and test cases for missing-value handling | Enter incomplete data and verify that a clear warning appears |
| Check that documented safety and privacy rules are reflected in the design | Ask authorised healthcare users to evaluate report clarity and workflow |

**Explanation:** Verification checks whether requirements, design and implementation work products follow specifications. Validation runs the system to see whether it works as intended for users.

**Conclusion:** Both are essential. Clinical interpretation, privacy controls and user-facing health messages must be reviewed and validated before deployment.

---

### Group 4 — Manual and Automated Testing; Strategic and Ad-Hoc Testing
| Full question | Jump to answer |
|---|---|
| Compare Manual Testing and Automated Testing based on cost, speed, accuracy, maintenance, and suitable applications, with examples. | <a href="#manual-automated">Go to answer</a> |
| Analyze the limitations of Manual Testing for a real-time Heat Wave Monitoring System and explain how automated testing can improve testing efficiency. | <a href="#heatwave-automation">Go to answer</a> |

## Group 4 — Manual and Automated Testing; Strategic and Ad-Hoc Testing

<p id="manual-automated"></p>

### 19. Compare Manual Testing and Automated Testing based on cost, speed, accuracy, maintenance, and suitable applications, with examples.

| Basis | Manual Testing | Automated Testing |
|---|---|---|
| Execution | Tester performs steps manually | Scripts/tools execute test steps |
| Initial cost | Usually lower for small or one-time tests | Higher due to tool and script setup |
| Speed | Slower for repeated large test sets | Fast for repeated and large test sets |
| Accuracy | Can be affected by human error or inconsistency | Repeatable, but scripts and assertions can still be wrong |
| Maintenance | Test instructions and test data need updates | Scripts, selectors and test data need updates |
| Best suited for | Exploratory testing, usability and one-off checks | Regression, repetitive, load and frequent data checks |
| Example | Tester explores a new dashboard and judges clarity | Script checks thousands of sensor readings against expected validation rules |

**Conclusion:** Automated testing improves repeatability and speed for frequent tests; manual testing remains useful for exploration and human judgement. A good project uses both.

<p id="heatwave-automation"></p>

### 20. Analyze the limitations of Manual Testing for a real-time Heat Wave Monitoring System and explain how automated testing can improve testing efficiency.

**Limitations of manual testing:**
1. A person cannot continuously check every incoming sensor reading at large scale.
2. Repeated tests are slow and may produce inconsistent results.
3. Rare combinations of temperature, humidity and missing data can be missed.
4. Manual execution may delay detection of broken alert logic.
5. Large regression suites are expensive to repeat after each change.

**How automation helps:**
1. Automatically test data validation and threshold rules.
2. Replay recorded sensor data to test normal, extreme and missing readings.
3. Run regression tests whenever the model or alert logic changes.
4. Simulate high data volume and verify alert latency.
5. Automatically compare actual outputs with expected results and log failures.

**Example test cases:**

| Test Case ID | Input | Expected Result | Actual Result | Status | Technique |
|---|---|---|---|---|---|
| HW-01 | Temperature crosses configured heat-alert threshold | Heat alert is generated | Alert generated | Pass | Boundary/functional test |
| HW-02 | Sensor sends missing temperature | Data-quality warning is recorded; no unsafe prediction is made | Warning recorded | Pass | Negative test |
| HW-03 | Large batch of valid readings | System processes readings within specified response-time limit | Within limit | Pass | Performance test |
| HW-04 | Duplicate sensor message | Duplicate is handled according to the system rule | Duplicate handled | Pass | Integration/regression test |

Automation improves speed, consistency and monitoring coverage, but human review is still needed for alert usefulness and operational safety.

---

### Group 5 — Scenario-Based Test Case Design
| Full question | Jump to answer |
|---|---|
| An AI-based Heat Wave Monitoring and Prediction System generates incorrect heat-wave alerts. Analyze how Black Box and White Box Testing can be used to identify the problem. | <a href="#heatwave-black-white">Go to answer</a> |
| Analyze suitable Black Box Testing techniques for an AI-based Satellite Monitoring System and explain how test cases can be derived from system requirements. | <a href="#satellite-black-box">Go to answer</a> |
| An AI-based Satellite Monitoring System receives telemetry data continuously. Analyze which testing techniques should be used to verify data processing, anomaly detection, and alert generation. Justify your answer. | <a href="#satellite-telemetry">Go to answer</a> |

## Group 5 — Scenario-Based Test Case Design

<p id="heatwave-black-white"></p>

### 21. An AI-based Heat Wave Monitoring and Prediction System generates incorrect heat-wave alerts. Analyze how Black Box and White Box Testing can be used to identify the problem.

**Black Box Testing** checks the system using inputs and expected behaviour without inspecting code. **White Box Testing** checks internal threshold logic, conditions and model-processing paths.

| Test Case ID | Input | Expected Result | Actual Result | Status | Technique |
|---|---|---|---|---|---|
| HW-BB01 | Temperature and humidity below configured alert criteria | No heat-wave alert | No alert | Pass | Black box / functional |
| HW-BB02 | Input meets configured alert criteria | Heat-wave alert is generated | Alert generated | Pass | Black box / boundary |
| HW-BB03 | Temperature field is missing | Data-quality warning appears | Warning appears | Pass | Black box / error guessing |
| HW-WB01 | Test values immediately below, equal to and above threshold | Correct branch executes for each value | Correct branches execute | Pass | White box / branch testing |
| HW-WB02 | Valid and invalid sensor values pass through validation function | Invalid values are rejected or flagged | Invalid values flagged | Pass | White box / condition testing |

**Analysis:** If external inputs and outputs are wrong, black box tests reproduce the failure. White box tests then inspect the internal conditions and paths. For AI predictions, also evaluate labelled historical data and measure false-positive and false-negative rates. If the model is correct but alerts are wrong, investigate the threshold or alert integration logic.

<p id="satellite-black-box"></p>

### 22. Analyze suitable Black Box Testing techniques for an AI-based Satellite Monitoring System and explain how test cases can be derived from system requirements.

Requirements might state that the system accepts valid telemetry, detects anomalies and sends alerts within a specified time. Test cases can be derived using equivalence partitioning, boundary value analysis, error guessing and state-transition testing.

| Test Case ID | Input | Expected Result | Actual Result | Status | Technique |
|---|---|---|---|---|---|
| SAT-01 | Valid telemetry within normal range | Data is accepted and classified as normal | Data accepted as normal | Pass | Equivalence partitioning |
| SAT-02 | Telemetry value at the configured limit | System follows the documented boundary rule | Boundary rule followed | Pass | Boundary value analysis |
| SAT-03 | Telemetry outside valid range | Value is rejected or flagged | Value flagged | Pass | Boundary value analysis |
| SAT-04 | Missing or corrupted telemetry field | Data-quality error is logged; invalid input is not silently treated as normal | Error logged | Pass | Error guessing |
| SAT-05 | Validated anomaly detected | Alert is generated and recorded | Alert generated | Pass | Functional testing |
| SAT-06 | Telemetry stream is temporarily interrupted and then restored | System handles interruption and resumes according to requirements | Stream resumes | Pass | State-transition testing |

**Conclusion:** Requirements define the inputs, expected classifications, error responses and alert rules. Test cases should cover normal, boundary, invalid and failure-recovery conditions.

<p id="satellite-telemetry"></p>

### 23. An AI-based Satellite Monitoring System receives telemetry data continuously. Analyze which testing techniques should be used to verify data processing, anomaly detection, and alert generation. Justify your answer.

Use multiple techniques because the system includes data ingestion, AI analysis and alert delivery.

1. **Unit testing:** Test parsing, unit conversion, missing-value handling and alert formatting separately.
2. **Black box testing:** Provide known normal and anomalous telemetry and compare outputs with expected classifications.
3. **Boundary value analysis:** Test values around configured telemetry limits and alert thresholds.
4. **Integration testing:** Verify that parsed telemetry reaches the model and that anomaly results reach the alert service.
5. **Performance and reliability testing:** Simulate continuous high-volume data, delayed messages, duplicates and temporary network failures.
6. **Regression testing:** Repeat tests after changes to preprocessing, model versions or alert rules.

| Test Case ID | Input | Expected Result | Actual Result | Status | Technique |
|---|---|---|---|---|---|
| SAT-T01 | Valid telemetry packet | Values are parsed and stored correctly | Parsed and stored correctly | Pass | Unit / functional |
| SAT-T02 | Labelled anomalous telemetry sample | Model/system flags it according to the validated test expectation | Flagged as expected | Pass | Black box / model evaluation |
| SAT-T03 | Value immediately below/at/above configured threshold | Output follows the documented threshold rule | Rule followed | Pass | Boundary value analysis |
| SAT-T04 | High-rate telemetry stream | Processing and alerts meet specified latency and throughput targets | Targets met | Pass | Performance testing |
| SAT-T05 | Anomaly output generated while alert service is connected | Correct alert is delivered and logged | Alert delivered and logged | Pass | Integration testing |

**Justification:** Unit tests isolate logic defects, black box tests assess observable behaviour, integration tests check data flow, and performance tests verify continuous operation. AI quality should be assessed with representative labelled data rather than assuming every prediction is correct.

---

## Last-Minute Revision

| Concept | Remember |
|---|---|
| Alpha testing | Internal testers; controlled environment; before beta |
| Beta testing | Real users; real-world conditions; feedback before release |
| Unit testing | One function, class or module |
| Integration testing | Communication between modules |
| System testing | Complete integrated application |
| Verification | Are we building the product correctly? |
| Validation | Are we building the right product? |
| Static testing | Review/inspect without executing software |
| Dynamic testing | Execute software and compare actual vs expected results |
| Black box | Test inputs and outputs against requirements |
| White box | Test internal code, branches, conditions and paths |
| Boundary value analysis | Test at and around input limits |
| Equivalence partitioning | Test representative values from input groups |
| Manual testing | Human execution; useful for exploration/usability |
| Automated testing | Scripted repeatable checks; useful for regression/scale |
| Test case | ID + input + expected result + actual result + status |
| Pass / Fail | Actual matches expected / actual differs from expected |

> **Important for exam tables:** Use realistic sample outputs and mark them Pass only when the actual result matches the expected result. If the question asks you to design test cases rather than execute them, write “Not Run” in Actual Result and Status as appropriate, or clearly state that the table shows assumed successful execution.
