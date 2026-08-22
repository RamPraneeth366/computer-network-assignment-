**CO4 AT2** <br>
**Comparative Study of IDS and IPS** <br>
**Name:** T. Ram Praneeth Reddy <br>
**Register No:** 192512056

---

**1. Aim** <br>
To study the working mechanisms, structural differences, and implementation methods of Intrusion Detection Systems (IDS) and Intrusion Prevention Systems (IPS) in computer networks.

---

**2. Problem Statement** <br>
Enterprise networks regularly deal with malicious traffic, worms, and unauthorized access attempts. Security engineers need reliable mechanisms to identify and neutralize these threats. Choosing between passive monitoring (IDS) and active blocking (IPS) is critical, as an incorrect choice can either leave network systems exposed to exploits or cause network outages by mistakenly dropping legitimate user packets.

---

**3. Overview of Technologies**

* **Intrusion Detection System (IDS):** <br>
  An IDS is a passive monitoring tool. It takes a mirrored copy of network traffic via a switch SPAN port or network tap and inspects the packets. It uses signature detection (comparing against known threat patterns) and anomaly detection (checking against baseline network behavior). Since it is connected out-of-band, it cannot stop packets on its own; it only raises alerts and logs details for the administrator.

* **Intrusion Prevention System (IPS):** <br>
  An IPS uses similar inspection engines but is placed inline directly in the main traffic path. Because every packet must pass through the device, an IPS can inspect and actively drop malicious packets, reset connections, or block IP addresses in real time.

---

**4. Deployment Architectures**

* **Out-of-Band Setup (IDS):** <br>
  The IDS sensor is wired to a SPAN or mirror port on the core switch. It only receives duplicate frames. If the IDS device fails, crashes, or gets overloaded, live user traffic continues through the switch without interruption.

* **Inline Setup (IPS):** <br>
  The IPS sits directly between the firewall and the internal local network. All traffic physically flows through the unit. While this guarantees that bad packets are stopped before entering internal subnets, hardware failure or rule misconfiguration can throttle or halt legitimate enterprise operations.

---

**5. Pros and Cons**

* **Intrusion Detection System (IDS):**
  * **Pros:** No risk of blocking genuine traffic, zero added latency on the primary link, and helpful for network forensics and audit compliance.
  * **Cons:** Cannot stop an active attack automatically, needs manual monitoring to take action, and often creates alert fatigue.

* **Intrusion Prevention System (IPS):**
  * **Pros:** Automatically stops attacks in real time, reduces response delay, and protects critical perimeter services effectively.
  * **Cons:** Can block valid business traffic due to false positives, adds slight latency, and acts as a potential single point of failure if not configured with bypass mechanisms.

---

**6. Implementation Guidelines**

* **When to deploy IDS:** In internal core networks, sensitive systems (such as medical or financial environments) where dropping real traffic is strictly unacceptable, and for long-term traffic logging.
* **When to deploy IPS:** At perimeter firewalls, external gateways, and in front of public-facing web servers to stop direct attacks immediately.
* **Hybrid Approach:** Standard network design uses both. The IPS is placed at the edge to block brute-force attempts and known exploits, while IDS sensors are placed internally to observe traffic trends without causing disruptions.

---

**7. Conclusion** <br>
IDS and IPS serve distinct but supporting roles in network security. IDS gives complete traffic visibility without risking uptime, while IPS prevents known threats from breaching the boundary. Using both in a layered setup provides both automated perimeter defense and internal threat visibility.
