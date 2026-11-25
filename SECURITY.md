# Reporting Security Issues

The Dependency-Track team and community take security bugs seriously.
We appreciate your efforts to responsibly disclose your findings,
and will make every effort to acknowledge your contributions.

Not every bug is a vulnerability.
Before you report, check your finding against the [vulnerability brocards](#vulnerability-brocards),
and prepare a [proof of concept](#proof-of-concept).
Reports without a proof of concept, or that a brocard rules out without rebuttal,
are closed without further discussion.

## How to Report

Report the issue through the **Report a vulnerability** button on the **Security** tab of the affected repository.
If you cannot use GitHub, email:

* [security@dependencytrack.org](mailto:security@dependencytrack.org),
* [steve.springett@owasp.org](mailto:steve.springett@owasp.org), and
* [niklas.duester@owasp.org](mailto:niklas.duester@owasp.org)

and include the word "SECURITY" in the subject line. Email reports must contain the same information as the form.

Send one finding per report. Do not open public issues or pull requests for vulnerabilities.

The Dependency-Track team will send a response indicating the next steps in handling your report.
After the initial reply to your report,
the security team will keep you informed of the progress towards a fix and full announcement,
and may ask for additional information or guidance.

Report security bugs in third-party modules to the person or team maintaining the module.

## Vulnerability Brocards

The [vulnerability brocards](https://vulnbrocards.com/brocards/) are rules of thumb for triaging reports.
We apply them to every report we receive. Check your finding against each one before you send it:

* [VB001: No vulnerability report without a threat model](https://vulnbrocards.com/brocards/vb001-no-vuln-report-without-threat-model/).
  State what the attacker controls before the attack, and what they gain after it.
* [VB002: No exploit from the heavens](https://vulnbrocards.com/brocards/vb002-no-exploit-from-heavens/).
  If the attack requires control over the deployment, such as its hosts, database, or configuration,
  or administrator permissions, such as `ACCESS_MANAGEMENT` or `SYSTEM_CONFIGURATION`,
  the attacker already has more than the attack gives them.
* [VB003: No vulnerability outside of usage](https://vulnbrocards.com/brocards/vb003-no-vuln-outside-of-usage/).
  A vulnerable dependency or internal method is only a vulnerability in Dependency-Track
  if Dependency-Track reaches it.
  Scanner output, including Dependency-Track's own, is not a report.
  For dependency updates without demonstrated impact, open a regular issue or pull request instead.
* [VB004: No vulnerability from standard behavior](https://vulnbrocards.com/brocards/vb004-no-vuln-from-standard-behavior/).
  Behavior that a specification, such as CycloneDX, requires is a matter for the specification.
* [VB005: No vulnerability from documented behavior](https://vulnbrocards.com/brocards/vb005-no-vuln-from-documented-behavior/).
  Behavior that the documentation describes, including its security implications, is not a vulnerability.
* [VB006: No cure worse than the disease](https://vulnbrocards.com/brocards/vb006-no-cure-worse-than-disease/).
  We will not accept a fix that costs users more than the issue it addresses.
* [VB007: The report is neither necessary nor sufficient](https://vulnbrocards.com/brocards/vb007-report-neither-necessary-nor-sufficient/).
  A CVE in a dependency does not by itself make Dependency-Track vulnerable.

The brocards are filters, not verdicts.
If you believe one does not apply to your finding, say which one and why in your report.

## Proof of Concept

Every report must include a proof of concept, either as written steps or as a script.
It must reproduce the issue against a running Dependency-Track instance, on the latest release or the `main` branch.
A description of what the code might do is not a proof of concept.

Include:

* The version or commit you tested, and any non-default configuration.
* The attacker's starting position: unauthenticated, or the exact permissions they hold.
* The steps or script, with the requests sent and the responses received.
  If the attack needs a file, such as a crafted BOM, include it as text or a script that generates it.
  Do not attach binaries.
* What you observed, and what you believe an attacker gains from it. Keep the two apart.
