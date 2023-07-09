
# Fordem | for democracy | برای مردم‌گردانی
## A censorship-resistant digital emocracy platform  
  
**What is Fordem?**  
Fordem, an abbreviation of ‘for democracy’, is a digital democracy and socio-political mobilisation platform, with participation, deliberation, and networking functionalities.  
Fordem app (WIP) forms independent WiFi-Direct & Bluetooth mesh networks when the internet and cellular networks are down, respects privacy and is oriented on data security. Fordem is a part of Fediverse and can be used as app on your smartphone or as desktop-client. Fordem aims to be the main channel for networking and conversations of resistance and resilience, social struggles and sociopolitical mobilisation, and it is there to make the voices of civil society movements heard and to maximise their impact.
  
**Who is behind the project?**
We are the developers of this censorship-resistant sociopolitical network. Our volunteer team is transnational, heterarchical and committed to human rights and fundamental freedoms. We met in a hackathon of Update Deutschland and joined forces and expanded globally because we were working on similar ideas. Organizationally, Fordem is a project of Transnational Community Federation e. V. (TCF). TCF is a non-profit, not-governmental heterarchical civic innovation Lab. With our interdisciplinary approach, we bring about positive changes in our communities around the world. We are active in various fields including promotion of education, democratic systems, and demarginalization. For more information check https://transcf.org 

**Fordem short-term goals:**  
Fordem is a tool which can help the development of any community since it can be adapted to the respective needs and contexts. In our first version we are invested in providing the Iranian political activists the tools they will need at each of the networking, deliberation and participation stages of their mobilisation along the ongoing Women, Life, Freedom revolution in Iran.  
Furthermore, we are invested in implementing Fordem in communities with a democratic gap in Germany. Our focus is on Heilbronn, a city with more than 54% of the population having (family) experiences with migration but form only 5% of the members of the municipal council. In the long term Fordem has the potential to be the tool for any community worldwide and connect an endless number of communities with each other. In this sense it can strengthen local communities while connecting them with the world. 
  
**How are we going to do that?**  
Fordem is an open-source platform. At its backend lies Nextodon, an extended version of Mastodon that we have written in C# with gRPC, crypto wallet, advanced votes, E2EE DMs and so on. As a mobile app, Fordem has large-scale mesh network formation abilities using WiFi, WFD and BT for the times of no internet, next to usual Mastodon. A DHT on the Nextodon takes care of synchronisation between databases of the networks that emerge from offline modes. 
  
**Activists will have the possibility to:**
- Identify themselves through a pseudonymisation process done by a trusted third party  
- Create and interactively flesh out their multifaceted profile and connect with people who strive for similar changes as they do  
- Organise events and meetings  
- Deliberate different aspects of the revolution Initiate and take part in polls and surveys and figure out the social choice  
- Form local mesh wireless networks when internet and electricity is shut down  
  

**Development approach and timeline:**


|Pipeline|version|Description|
|-	|-	|-									|
|Line i| V.1 | Mastodon App + Mastodon + Nextodon’s Registration|Authentication features|
|	|V.1.x| Fordem-specific features on top of Mastodon App + backend as above	|
| Line ii|V.2x|Feature-complete Fordem Flutter App + feature-complete Nextodon		|

**2023 Timeline:**  https://github.com/tcfev/Fordem/issues/168
    
Check the [`Feature List`](https://github.com/tcfev/Fordem/issues/85)  
Want to Join?: [`check here`](https://github.com/tcfev/Fordem/issues/61)  & [`this discussion`](https://github.com/tcfev/Fordem/discussions/52)  
`In case you have privacy concerns, create a new Github account first and then write to us or engage in discussions.`  
[`Project Documentation`](https://github.com/tcfev/Fordem-documentation) will help you understand how we organise the project. (Work in progress)
#
This repository deals with documentation and issue tracking of the 2 main components of the platform:
* [Nextodon](https://github.com/tcfev/nextodon)
* [Fordem App](https://github.com/tcfev/fordem-app)
#
* [Organisation & Component Overview](https://github.com/tcfev/fordem/blob/main/.assets/organisation.md)
	* Big picture (in Persian)
![Alt](.assets/big-picture-per.drawio.png)
* [Our Values & principles](https://github.com/tcfev/fordem/issues/57)
* [Protocols](https://github.com/tcfev/fordem/tree/main/.assets/.protocols)
#
**Platforms**
- Android, iOS, Web, Linux, Windows and MacOS
#
**Connected APIs**
- Part of Fediverse
#
**UI Design**  
* [Figma design](https://www.figma.com/file/VHFRoqXfhc2ThZQMZUXcje/%D8%A8%D8%B1%D8%A7%DB%8C-%D9%85%D8%B1%D8%AF%D9%85%E2%80%8C%D8%B3%D8%A7%D9%84%D8%A7%D8%B1%DB%8C%2Ff%C3%BCrDem?node-id=0%3A1)  
* [UX-flowchart](https://github.com/tcfev/Fordem/blob/main/.assets/ux-flowchart.md) - work-in-progress
* [Brand-identity](https://github.com/tcfev/Fordem/blob/main/.assets/brand-identity.md) - work-in-progress  
#
**Domain model - todo**  
#
**Standards - todo**  
- `Suggestion` for user-centred design processes and extension of UI/UX concept
    * `ISO 13407:1999.`
- `Suggestion` for design of the system architecture
    * `ISO/IEC 25010:2011, CD 25019.3`
---
** Digital democracy platforms and how Fordem stands out**  

Every digital democracy platform must have the following four core functionlities/features fully fledged in it: 
- `Transparency`
- `Networking`
- `Deliberation`
- `Participation`

**This makes Fordem unique:**  
* Next to the four core pillars mentioned above Fordem will offer:  
- `interest vector`
- `official, acquaintanceship and reputation-based pseudonymisation`  
- `peer-to-peer connectivity`  
- `decentralised storage`
- `onion-routing`
- `integrated crypto economy`
---
#### Platform architecture
![img](https://github.com/tcfev/Fordem/blob/main/.assets/Fordem-Architecture-Architecture.drawio.png)

---
#### P2P, DHT & Synchronization
We have two main parts that relate to the P2P functionalities  
- P2P mode  
- Local NoSQL database  
  
Once there is no internet connection available (and the app is set to discover or form mesh networks/other peers), if P2P connection is established, the local databases of the adjacent apps will be compared and synchronised. This can happen through a comparison of the lists of keys(UUIDs) of the two databases, and if there is a difference, a union of the differing key:values will be shared between the two apps. Goal here is to send as small yet meaningful pieces of data as the Mesh network can handle. The exchanged data will is end-to-end encrypted.
Here are the mesh protocol’s specification and situation of the peers, the defining factor.  
If the network is healthy, the size of the chunk of data that is going to be shared, increases.  
In version one synchronisation takes place between the databases of each two apps (with intermediary nodes or without) that have differing tables. In later versions, a more efficient method will be chosen.  
One main goal is to regularly check & report the level of synchronicity until the network is stabilised and all the data is available on all apps. However smaller chunks of fully synchronised data (individual entities) are still valuable.  
So, long story short, synchronising the NoSQL databases of the peers in the most efficient way is the goal.
  
![img](https://github.com/tcfev/Fordem/blob/main/.assets/Fordem-P2P-DHT-Diagramm.drawio.png)

---

## Roadmap
**internet**
 - [x] Mastadon compatibility API: A gRPC server written C# with REST extension compatible with Mastadon's REST API
 - [x] Port & Extend Mastadon's REST API with new features implemented in C# (as a micro service) 
 - [x] Generate Frontend -[Nextodon-ui](https://github.com/tcfev/nextodon-ui) & [Nextodon-ui](https://github.com/tcfev/nextodon-UI-old)
	 - Generate client-side API
	 - Develop UI for the Flutter App - just a scaffold. other UI Devs can then customize this.

**P2P**
- Embedd [nRF-Mesh-Library-Android](https://github.com/NordicSemiconductor/Android-nRF-Mesh-Library) 
- Embedd nRF-Mesh-Library-iOS
- Couple client-side APIs
- Implement Local Communication System over Wi-Fi Direct based on [Fuliang Li et al.](https://ieeexplore.ieee.org/document/9011605), António [Teófilo et al.](https://www.researchgate.net/publication/352213057_RedMesh_A_WiFi-Direct_Network_Formation_Algorithm_for_Large-Scale_Scenarios)

**Synchronization (DHT)** - todo

---
¹ Organizations/networks/individuals that are consistant with values around human rights and UN development goals. Also see: [Our Values & principles](https://github.com/tcfev/Fordem/issues/57)

