---
title: "EMM State of Device in CoreNetwork"
date: 2026-02-23
categories: [Core-Network]
url: /EMM-State-of-Device-in-CoreNetwork/
description: This will help to understand EPS Mobility Management (EMM) and EPS Connection Management (ECM).
draft: false
---

# Understanding MME States in the EPC: EMM vs. ECM
---------------------------------------------------

In the LTE Evolved Packet Core (EPC), the **Mobility Management Entity (MME)** is the brain of the control plane. To manage a device (UE) efficiently, the MME uses two parallel state machines: **EPS Mobility Management (EMM)** and **EPS Connection Management (ECM)**.

Think of it this way: **EMM** determines if you are "checked in" to the network, while **ECM** determines if you are "actively talking" to it.

* * * * *

1\. EPS Mobility Management (EMM)
---------------------------------

EMM states describe whether a UE is registered with the MME and authenticated to use the network.

#### **EMM-DEREGISTERED**

-   **The Scenario:** The phone is powered off, in airplane mode, or failed its initial attach.

-   **MME Knowledge:** The MME has no valid location or routing information for the UE.

-   **Status:** No IP address (EPS Bearer) is assigned.

#### **EMM-REGISTERED**

-   **The Scenario:** The UE has successfully performed an **Attach** or **Tracking Area Update (TAU)**.

-   **MME Knowledge:** The MME knows which **Tracking Area (TA)** the UE is currently in.

-   **Status:** The UE has an IP address and a "Default Bearer" assigned, even if it isn't sending data right now.

* * * * *

2\. EPS Connection Management (ECM)
-----------------------------------

ECM states describe the connectivity between the UE and the EPC. You can only have an ECM state if you are already in the `EMM-REGISTERED` state.

#### **ECM-IDLE**

-   **The Scenario:** The phone is on and registered, but it's in your pocket. No apps are actively using the data connection.

-   **Resources:** To save battery, the **Radio Resource Control (RRC)** connection and **S1-MME** signaling connections are released.

-   **Mobility:** The UE moves between cells using **Cell Reselection** (the phone decides where to go).

-   **MME Action:** If data arrives for the UE, the MME must **Page** the device across the entire Tracking Area to "wake it up."

#### **ECM-CONNECTED**

-   **The Scenario:** You are browsing the web, streaming a video, or the phone just responded to a page.

-   **Resources:** An active signaling connection exists (RRC + S1-MME), and the data path (S1-U) is established.

-   **Mobility:** The network manages movement via **Handover**.

-   **MME Knowledge:** The MME knows the specific **eNodeB** and **Cell ID** the UE is using.