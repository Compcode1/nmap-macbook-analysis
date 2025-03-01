This project was conducted to assess the security posture of a MacBook Air by leveraging Nmap scanning techniques. The goal was to analyze how different security configurations impact network visibility and exposure. By performing multiple scans under varying conditions, we were able to observe the role of macOS firewall settings, remote services, and stealth scanning techniques in system security.

**Key Phases & Findings**

1️⃣ Baseline Scan (Firewall Enabled, All Services Enabled)
Objective: Identify open ports and services while the firewall was enabled.
Findings:
Fewer ports were detected than expected.
The firewall actively blocked Nmap’s ability to see some services.
OS detection reported macOS 12 Monterey, despite the system running macOS Sonoma 14.6.1, highlighting limitations in network fingerprinting.

2️⃣ Firewall Disabled Scan (All Services Still Enabled)
Objective: Determine the firewall’s impact by running the scan again with the firewall turned off.
Findings:
Additional ports and services were revealed, confirming the firewall’s role in filtering traffic.
Services such as SSH (22), AirTunes (5000, 7000), and VNC (5900) became visible.
SMB and NetAssistant services appeared, further expanding the attack surface.

3️⃣ Re-Enabling Firewall While Keeping Services Active
Objective: See if the firewall’s protection would once again obscure certain services.
Findings:
The firewall successfully hid many ports again.
However, some services (AirTunes, VNC) remained detectable, likely due to their specific configurations.

4️⃣ Stealth Scan with Nmap SYN Scan (-sS -Pn -T4)
Objective: Test how stealth scanning techniques impact visibility.
Findings:
Stealth scanning revealed only two open ports (5000 and 7000) instead of the broader set detected in previous scans.
This indicates that macOS firewall settings and TCP handshake behavior limit visibility to more subtle scan types.
A stealth scan would likely bypass simple intrusion detection systems (IDS) that only log full TCP connections.
Conclusion & Takeaways
macOS Firewall is highly effective at reducing network exposure.

With the firewall on, many services remained hidden from external scans.
When disabled, additional services were immediately detected.
Nmap OS fingerprinting is not always accurate.

macOS was misidentified as Monterey 12 instead of Sonoma 14.6.1, due to how Apple implements network stack responses.
Stealth scanning techniques significantly reduce detection.

A SYN scan (-sS) identified only two ports, showing that even when services are open, certain scans might not detect them.
The attack surface can be minimized by disabling unnecessary services.

Features like AirTunes, VNC, and SSH expose remote access points.
If remote access is not needed, these services should be disabled for better security.
Final Thoughts
This project demonstrated how Nmap can be used to analyze a system’s security posture under different configurations.
By systematically modifying security settings and observing the results, we gained insight into:

The effectiveness of the firewall in blocking connections.
The impact of stealth scanning in network reconnaissance.
How open services contribute to potential attack surfaces.
While this project focused on local network scanning, similar techniques can be applied to larger-scale cybersecurity assessments, including penetration testing, vulnerability scanning, and enterprise security auditing.

Suggested Next Steps (For Future Exploration): ✅ Investigate Nmap scripting engine (NSE) for vulnerability scanning.
✅ Experiment with IPv6 scanning techniques (nmap -6).
✅ Use a packet analyzer (Wireshark) to monitor network traffic while scanning.
✅ Automate periodic scans with Python for continuous monitoring.

**Project Complete 🎯**

The experiment successfully mapped the attack surface, tested firewall effectiveness, and analyzed scan evasion techniques.
By applying these findings, security posture can be significantly improved through firewall enforcement, service minimization, and stealth detection awareness.

