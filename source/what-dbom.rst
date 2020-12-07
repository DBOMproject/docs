What is DBoM?
=============

The Digital Bill of Materials (DBoM) Consortium Linux Foundation project seeks to improve supply chain efficiency by enabling more effective attestation sharing among supply chain partners.

Pain Points:

-   No common method/standard to verify the origin of Hardware or
    Software components.
-   No way to detect malware installed during design and manufacturing.
-   No way to implement nation stated policies to block components from
    vendors deemed threat to national security.
-   Lack of clarity on origin of design of devices limits any trusted
    use case
-   No autonomous way to apply Federal government regulations on
    contractors to protect against counterfeit devices and compromised
    software.

DBoM Nodes enforce the policy structure established by the partners to an individual supply chain relationship. An individual DBoM Node can establish or subscribe to one or more channels. Channels can be created as:

-	Public: Broadcast attestations for public view (One to All)
-	Broadcast: Broadcast attestations for restricted view (One to Many)
-	Private: Shared among one or more based on agreed membership and access policies (Many to Many)

Attestations on these channels can include any data the partners in a given supply chain relationship choose. These may include Software Bill of Materials (SBOM), Hardware Bill of Materials (HBOM), known vulnerabilities, Indicators of Compromise (IOC), risk assessments, or any other information associated with an asset.

The Digital Bill of Materials for a given artifact is the stack of attestations on one or more channels that relate to that artifact. For example, a computer server in an enterprise data center may have the following attestations in its Digital Bill of Materials:

-	Operational events attested to automatically on a local Private channel maintained by the enterprise
-	Hardware content data attested to on Public channel maintained by the server vendor
-	Software Bill of Material data attested to on a Broadcast channel maintained by the server operating system vendor
-	Risk assessment data attested to on a Private channel maintained by a risk analysis services provider
-	Vulnerability notices attested to on a Private channel maintained by a Managed Services provider
-	Indicator of Compromise notices attested to on a Private channel maintained by an Information Sharing and Analysis Organization (ISAO)
-	Regulatory data attested to on a Broadcast channel by an industry regulatory agency
