---
layout: splash
title:  "IACS STAR Calculator"
permalink: /calculator/
head_scripts:
  - /assets/js/calc.js
---

        <div class="container">
            <h1>IACS System Testing and Assessment Rating Score Calculator</h1>
            <div class="row">
<div class="col-md-12">
    <div class="row">
        <div class="alert m-3" role="alert">
            Republish Score Vector: <input id="vector-input" type="text" size="70" /> <input type="button" onclick="update_form()" value="update"/>
        </div>
    </div>   
</div>    
<div class="col-md-6">             
    <h2>Likelihood Factors</h2>
    <div class="row">
        <div class="col-md-6">
            <h5>Threat Actor Factors</h5>
            <!--Threat Actor Skill level: How technically skilled is this group of threat actors? -->
            <h6>Skill Level</h6>
            <select class="custom-select custom-select-sm" id="sl" data-toggle="tooltip" data-placement="top" title="How technically skilled is this group of threat actors?">
                <option class="text-0" value="0">0 - N/A</option>
                <option class="text-1" value="1">1 - Limited Information Technology (IT), network, and no Operational Technology (OT) skills</option>
                <option class="text-2" value="2">2</option>
                <option class="text-3" value="3">3 - Moderate IT, limited network, and no OT technical skills</option>
                <option class="text-4" value="4">4</option>
                <option class="text-5" value="5">5 - Advanced IT, moderate network, and limited OT technical skills</option>
                <option class="text-6" value="6">6 - Advanced IT, advanced network, and moderate OT technical skills</option>
                <option class="text-7" value="7">7</option>
                <option class="text-8" value="8">8 - Advanced OT technical skills</option>
                <option class="text-9" value="9">9 - Security penetration skills and knowledge of OT technologies</option>
            </select>

            <!--Threat Actor Motive: How motivated of the threat actors once they obtain access to the control environment? An excellent guide for this is the Impact column of the [MITRE ATT&CK ICS Matrix](https://attack.mitre.org/matrices/ics/).-->
            <h6>Motive</h6>
            <select class="custom-select custom-select-sm" id="m" data-toggle="tooltip" data-placement="top" title="How motivated of the threat actors once they obtain access to the control environment?">
                <option class="text-0" value="0">0 - N/A</option>
                <option class="text-1" value="1">1 - No reward or intention to impact control environment</option>
                <option class="text-2" value="2">2 - Theft of operational data or equipment</option>
                <option class="text-3" value="3">3 - Create loss of view and control as a result of target-of-opportunity access to assets</option>
                <option class="text-4" value="4">4</option>
                <option class="text-5" value="5">5 - Limit access to file shares and prevent view and control using common malware</option>
                <option class="text-6" value="6">6 - Prevent view and control using specially designed malware</option>
                <option class="text-7" value="7">7</option>
                <option class="text-8" value="8">8 - Manipulate view and control using privileged remote access and/or specially designed malware</option>
                <option class="text-9" value="9">9 - Prevent operation of safety equipment or cause a catastrophic failure</option>
            </select>

            <!--Threat Actor Opportunity:  When accessing the control environment, how are the threat actors limited by deployed countermeasures?-->
            <h6>Opportunity</h6>
            <select class="custom-select custom-select-sm" id="o" data-toggle="tooltip" data-placement="top" title="When accessing the control environment, how are the threat actors limited by deployed countermeasures?">
                <option class="text-0" value="0">0 - Physical access and local authentication are required and response time is less than fifteen minutes</option>
                <option class="text-1" value="1">1 - Physical access and local authentication are required but response time is more than fifteen minutes</option>
                <option class="text-2" value="2">2</option>
                <option class="text-3" value="3">3 - Physical and remote access is possible, local authentication required, and active monitoring is enabled</option>
                <option class="text-4" value="4">4</option>
                <option class="text-5" value="5">5 - Limited logging of physical or remote access but administrative privileges are required to access network devices, systems, and applications</option>
                <option class="text-6" value="6">6 -Undetected physical or remote access but administrative privileges are required to access network devices, systems, and applications</option>
                <option class="text-7" value="7">7</option>
                <option class="text-8" value="8">8 - Undetected physical or remote access that provides requires authentication to some network devices, systems, and applications</option>
                <option class="text-9" value="9">9 - Undetected physical or remote access that provides elevated permissions to network devices, systems, and applications</option>
            </select>

            <!--Threat Actor Access: What is the physical or remote access capabilities achieved by successful exploitation within the process?-->
            <h6>Access</h6>
            <select class="custom-select custom-select-sm" id="a" data-toggle="tooltip" data-placement="top" title="What is the physical or remote access capabilities achieved by successful exploitation within the process?">
                <option class="text-0" value="0">0 - N/A</option>
                <option class="text-1" value="1">1 - Physical owner/operator users</option>
                <option class="text-2" value="2">2 - Physical vendor/integrator users</option>
                <option class="text-3" value="3">3 - Remote owner/operator users with MFA</option>
                <option class="text-4" value="4">4 - Remote vendor/integrator users with MFA</option>
                <option class="text-5" value="5">5 - Remote owner/operator users without MFA</option>
                <option class="text-6" value="6">6 - Remote vendor/integrator users without MFA</option>
                <option class="text-7" value="7">7 - Remote access without MFA or logging</option>
                <option class="text-8" value="8">8 - Physical malicious users</option>
                <option class="text-9" value="9">9 - Remote anonymous internet users</option>
            </select>
            <div class="alert m-3" role="alert">
                Threat Actor Factor: <span id="TAF"></span>
            </div>
        </div>
        <div class="col-md-6">
            <h5>Vulnerability Factors</h5>
            <!--Vulnerability/Ease of discovery: How easy is it for this group of threat actors to access the environment and discover the existence of the vulnerability? -->
            <h6>Ease of Discovery</h6>
            <select class="custom-select custom-select-sm" id="ea" data-toggle="tooltip" data-placement="top" title="How easy is it for this group of threat agents to discover this vulnerability?">
                <option class="text-0" value="0">0 - N/A</option>
                <option class="text-1" value="1">1 - Requires physical access to environment or OT device</option>
                <option class="text-2" value="2">2 - Requires physical access to environment or IT device</option>
                <option class="text-3" value="3">3 - Remotely accessible but countermeasures protecting OT technology</option>
                <option class="text-4" value="4">4 - Remotely accessible but countermeasures protecting IT technology</option>
                <option class="text-5" value="5">5</option>
                <option class="text-6" value="6">6 - Remotely accessible but no automated tools to discover for OT technology</option>
                <option class="text-7" value="7">7 - Remotely accessible but no automated tools to discover for IT technology</option>
                <option class="text-8" value="8">8 - Remotely accessible and automated tools available for IT technology</option>
                <option class="text-9" value="9">9 - Remotely accessible and automated tools available for OT technology</option>
            </select>

            <!--Vulnerability/Ease of exploit: How easy is it to actually exploit the vulnerability? -->
            <h6>Ease of Exploit</h6>
            <select class="custom-select custom-select-sm" id="ee" data-toggle="tooltip" data-placement="top" title="How easy is it for this group of threat agents to actually exploit this vulnerability?">
                <option class="text-0" value="0">0 - N/A</option>
                <option class="text-1" value="1">1 - No known proof of concept</option>
                <option class="text-2" value="2">2 - Countermeasures protecting OT technology</option>
                <option class="text-3" value="3">3 - Denial-of-Service possible but no code execution</option>
                <option class="text-4" value="4">4</option>
                <option class="text-5" value="5">5 - Custom scripts / tools can be made to exploit IT technology</option>
                <option class="text-6" value="6">6 - Custom scripts / tools can be made to exploit OT technology</option>
                <option class="text-7" value="7">7</option>
                <option class="text-8" value="8">8 - Automated tools available for IT technology</option>
                <option class="text-9" value="9">9 - Automated tools available for OT technology</option>
            </select>

            <!--Vulnerability/Awareness: How well known is this vulnerability?-->
            <h6>Awareness</h6>
            <select class="custom-select custom-select-sm" id="aw" data-toggle="tooltip" data-placement="top" title="How well known is this vulnerability to this group of threat agents?">
                <option class="text-0" value="0">0 - N/A</option>
                <option class="text-1" value="1">1 - Unknown OT Vulnerability</option>
                <option class="text-2" value="2">2 - Unknown IT Vulnerability</option>
                <option class="text-3" value="3">3 - Not publicly known but common configuration vulnerability</option>
                <option class="text-4" value="4">4</option>
                <option class="text-5" value="5">5 - Publicly identified on vendor website or within NVD Vulnerabilities database but no known exploit available</option>
                <option class="text-6" value="6">6 - Publicly identified on vendor website or within NVD Vulnerabilities database, no known exploit available but identified threat actor group can develop exploit</option>
                <option class="text-7" value="7">7</option>
                <option class="text-8" value="8">8 - Publicly identified on vendor website, vulnerability databases, and exploit available in public forums, i.e. Metasploit, Exploit-DB</option>
                <option class="text-9" value="9">9 - Public identified and in CISA Known Exploited Vulnerabilities Catalog</option>
            </select>

            <!--Detection/Response - How likely is an exploit to be detected?-->
            <h6>Intrusion Detection</h6>
            <select class="custom-select custom-select-sm" id="dr" data-toggle="tooltip" data-placement="top" title="How likely is an exploit to be detected?">
                <option class="text-0" value="0">0 - N/A</option>
                <option class="text-1" value="1">1 - Centrally logged with alerts and formal review and response plan</option>
                <option class="text-2" value="2">2</option>
                <option class="text-3" value="3">3 - Centrally logged with alerts and formal review but no response plan</option>
                <option class="text-4" value="4">4</option>
                <option class="text-5" value="5">5</option>
                <option class="text-6" value="6">6 - Centrally logged with alerts, but no formal review or response plan</option>
                <option class="text-7" value="7">7 - Centrally logged and without review</option>
                <option class="text-8" value="8">8 - Locally logged without review</option>
                <option class="text-9" value="9">9 - Not logged</option>
            </select>
            <div class="alert m-3" role="alert">
                Vulnerability Factor: <span id="VF"></span>
            </div>
        </div>
    </div>
    <div class="alert m-3" role="alert">
        Likelihood Factor: <span id="LF"></span>
    </div>
</div>
<div class="col-md-6">                
    <h2>Consequence Factors</h2>
    <div class="row">
        <div class="col-md-6">
            <h5>Technical Impact Factors</h5>
            <!--Loss of Confidentiality - How much data could be disclosed and how sensitive is it?-->
            <h6>Loss of Confidentiality</h6>
            <select class="custom-select custom-select-sm" id="lc" data-toggle="tooltip" data-placement="top" title="How much data could be disclosed and how sensitive is it?">
                <option class="text-0" value="0">0 - No data lost</option>
                <option class="text-1" value="1">1</option>
                <option class="text-2" value="2">2 - Minimal architecture configuration data disclosed</option>
                <option class="text-3" value="3">3</option>
                <option class="text-4" value="4">4 - Minimal network configuration data but no device configuration data disclosed</option>
                <option class="text-5" value="5">5</option>
                <option class="text-6" value="6">6 - Extensive network configuration data and some device configuration data disclosed</option>
                <option class="text-7" value="7">7 - Some process network and device configuration data disclosed</option>
                <option class="text-8" value="8">8</option>
                <option class="text-9" value="9">9 - All process network and device configuration data disclosed</option>
            </select>

            <!--Loss of Integrity - How is the process data changed and does it impact critical functions?-->
            <h6>Loss of Integrity</h6>
            <select class="custom-select custom-select-sm" id="li" data-toggle="tooltip" data-placement="top" title="How is the process data changed and does it impact critical functions?">
                <option class="text-0" value="0">0 - N/A</option>
                <option class="text-1" value="1">1 - Modification of historical data not used for control</option>
                <option class="text-2" value="2">2 - Modification of historical data used for control</option>
                <option class="text-3" value="3">3</option>
                <option class="text-4" value="4">4 - Local modification of set points used for non-critical functions</option>
                <option class="text-5" value="5">5 - Remote modification of set points used for non-critical functions</option>
                <option class="text-6" value="6">6 - Remote modification of device configurations used for non-critical functions</option>
                <option class="text-7" value="7">7 - Local modification of set points used for critical functions</option>
                <option class="text-8" value="8">8 - Remote modification of set points used for critical functions</option>
                <option class="text-9" value="9">9 - Remote modification of device configurations used for critical functions</option>
            </select>

            <!--Loss of Availability - How are production and safety services impacted?-->
            <h6>Loss of Availability</h6>
            <select class="custom-select custom-select-sm" id="la" data-toggle="tooltip" data-placement="top" title="How are production and safety services impacted?">
                <option class="text-0" value="0">0 - N/A</option>
                <option class="text-1" value="1">1 - Minimal production interruption and easily recoverable</option>
                <option class="text-2" value="2">2</option>
                <option class="text-3" value="3">3 - Device or service interrupted but process not impacted</option>
                <option class="text-4" value="4">4 - Production services temporarily interrupted by easily recoverable</option>
                <option class="text-5" value="5">5</option>
                <option class="text-6" value="6">6 - Production services interrupted but does not affect other processes</option>
                <option class="text-7" value="7">7 - Production services interrupted and impacts other processes</option>
                <option class="text-8" value="8">8 - All production services completely lost</option>
                <option class="text-9" value="9">9 - Loss of process safety functionality</option>
            </select>

            <!--Loss of Accountability - Are the threat actor actions traceable to an individual? -->
            <h6>Loss of Accountability</h6>
            <select class="custom-select custom-select-sm" id="lac" data-toggle="tooltip" data-placement="top" title="Are the threat actor actions traceable to an individual?">
                <option class="text-0" value="0">0 - N/A</option>
                <option class="text-1" value="1">1 - Central logging, Multifactor Authentication (MFA), and cameras</option>
                <option class="text-2" value="2">2 - Central logging, Multifactor Authentication (MFA), but no cameras</option>
                <option class="text-3" value="3">3 - Local logging, Multifactor Authentication (MFA), and cameras but no central logging</option>
                <option class="text-4" value="4">4</option>
                <option class="text-5" value="5">5 - Local logging and cameras but no MFA and no central logging</option>
                <option class="text-6" value="6">6</option>
                <option class="text-7" value="7">7 - Local logging but no MFA, no central logging, and no cameras</option>
                <option class="text-8" value="8">8</option>
                <option class="text-9" value="9">9 - No local or central logging, no MFA, and no cameras</option>
            </select>
            <div class="alert m-3" role="alert">
                Technical Impact Factor: <span id="TIF"></span>
            </div>
        </div>
        <div class="col-md-6">
            <h5>Safety Impact Factors</h5>
            <!--Environment Damage - How much damage to the local environment, plant or public, will be realized by successful exploitation?-->
            <h6>Environment Damage</h6>
            <select class="custom-select custom-select-sm" id="ed" data-toggle="tooltip" data-placement="top" title="How much damage to the local environment, plant or public, will be realized by successful exploitation?">
                <option class="text-0" value="0">0 - No environmental impact</option>
                <option class="text-1" value="1">1 - Environment damage limited by safety equipment, active, and passive protections</option>
                <option class="text-2" value="2">2 - Environment damage limited by active and passive protections</option>
                <option class="text-3" value="3">3</option>
                <option class="text-4" value="4">4 - Environment damage limited by passive protections only</option>
                <option class="text-5" value="5">5 - Safety equipment not remotely accessible and active and passive protections are in place</option>
                <option class="text-6" value="6">6</option>
                <option class="text-7" value="7">7 - Safety equipment remotely accessible but active and passive protections are sufficient</option>
                <option class="text-8" value="8">8 - Safety equipment remotely accessible and situation might overwhelm active protections but passive protections are sufficient</option>
                <option class="text-9" value="9">9 - Safety equipment on production network and situation might overwhelm active or passive protections</option>
            </select>

            <!--Process Damage - How much damage to the process equipment will be realized by successful exploitation?-->
            <h6>Process Damage</h6>
            <select class="custom-select custom-select-sm" id="pd" data-toggle="tooltip" data-placement="top" title="How much damage to the process equipment will be realized by successful exploitation?">
                <option class="text-0" value="0">0 - No devices can be damaged and configurations cannot be modified</option>
                <option class="text-1" value="1">1 - Device or monitoring systems / applications can be modified but do not damage device or process</option>
                <option class="text-2" value="2">2</option>
                <option class="text-3" value="3">3 - Device device configuration can be changed but easily recoverable</option>
                <option class="text-4" value="4">4 - Device damaged requiring manual update but limited impact to process</option>
                <option class="text-5" value="5">5</option>
                <option class="text-6" value="6">6 - Device damaged requiring manual update but significant impact to process</option>
                <option class="text-7" value="7">7 - Safety equipment configuration changed but limited impact to process</option>
                <option class="text-8" value="8">8 - Safety equipment damaged but limited impact to process</option>
                <option class="text-9" value="9">9 - Safety equipment damaged causing process failure or automatic shutdown</option>
            </select>

            <!--Safety Equipment - How well are digital safety equipment deployed and protected?-->
            <h6>Safety Equipment</h6>
            <select class="custom-select custom-select-sm" id="se" data-toggle="tooltip" data-placement="top" title="How well is digital safety equipment deployed and protected?">
                <option class="text-0" value="0">0 - Safety equipment not required for process</option>
                <option class="text-1" value="1">1 - Safety equipment required for process but not remotely accessible or on the same network as vulnerability</option>
                <option class="text-2" value="2">2 - Safety equipment required for process, remotely accessible, and requires MFA but not on the same network as vulnerability</option>
                <option class="text-3" value="3">3 - Safety equipment required for process and remotely accessible but does not require MFA and not on the same network as vulnerability</option>
                <option class="text-4" value="4">4 - Safety equipment required for process, remotely accessible, requires MFA, and on the same network as vulnerability</option>
                <option class="text-5" value="5">5 - Safety equipment required for process, remotely accessible, does not require MFA, and on the same network as vulnerability</option>
                <option class="text-6" value="6">6 - Safety equipment vulnerable and remotely accessible but requires MFA</option>
                <option class="text-7" value="7">7 - Safety equipment vulnerable and remotely accessible but requires authentication but no MFA</option>
                <option class="text-8" value="8">8 - Safety equipment vulnerable and remotely accessible but requires authentication but but default/hardcoded password in place and no MFA</option>
                <option class="text-9" value="9">9 - Safety equipment vulnerable, remotely accessible, and does not require authentication</option>
            </select>

            <!--Recoverability - How well is the organization / process team prepared to recover during successful exploitation?-->
            <h6>Recoverability</h6>
            <select class="custom-select custom-select-sm" id="r" data-toggle="tooltip" data-placement="top" title="How much personally identifiable information could be disclosed?">
                <option class="text-0" value="0">0 - Vulnerability will not require or limit recovery operations</option>
                <option class="text-1" value="1">1 - Process will automatically recover with no manual efforts</option>
                <option class="text-2" value="2">2 - Process will recover with minimal manual efforts</option>
                <option class="text-3" value="3">3</option>
                <option class="text-4" value="4">4 - Process will recover with extensive manual efforts</option>
                <option class="text-5" value="5">5</option>
                <option class="text-6" value="6">6 - Recovery not possible without vendor / integrator assistance</option>
                <option class="text-7" value="7">7 - Recovery not possible without limited government and vendor / integrator assistance</option>
                <option class="text-8" value="8">8 - Recovery not possible without moderate government and vendor / integrator assistance</option>
                <option class="text-9" value="9">9 - Recovery not possible without significant government and vendor / integrator assistance</option>
            </select>
            <div class="alert m-3" role="alert">
                Safety Impact Factor: <span id="SIF"></span>                
            </div>
        </div>
    </div>
    <div class="alert m-3" role="alert">
        Consequence Factor: <span id="CF"></span>        
    </div>
</div>
</div>
<div class="alert m-3" role="alert">
Overall Risk Severity: <span id="Risk"></span>
</div>
<div class="alert m-3" role="alert">
Score Vector: <a id="score" target="_blank"></a>
</div>

        </div>

This Risk Rating Calculator is based on [https://github.com/cutaway-security/IACS_STAR_Methodology](IACS System Testing and Assessment Rating (STAR) Methodology). To understand how to effectively use this calculator to score implementation vulnerabilities, please have the stakeholders and assessment team read the [https://iacs-star-calculator.com/html/methodology.html](methodology documentation) to understand the likelihood and consequence factors. Threat actor factor scores will, most likely, be consistent for all situations involving the System-Under-Consideration (SUC). Stakeholders may be required to accurately score the safety impact factors for each issue being reviewed.

This Risk Rating Calculator was generated using the example of [https://owasp-risk-rating.com/](OWASP's Risk Rating Calculator).

This project was developed and is supported by [https://www.cutawaysecurity.com](Cutaway Security, LLC.)