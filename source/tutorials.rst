Tutorials 
=========

==================
Configuring Agents
==================

Agents are configured on the Gateway in the PoC by the use of the
agent-config configmap in a Kubernetes environment and agent-config.yaml
when it's being run locally

Example Agent Config
--------------------

.. code-block:: yaml  

    meta:
        version: v1.0
    agents:
        - DB1:
            version: 1
            host: localhost
            port: 3500
            enabled: true
        - iota:
            version: 1
            host: localhost
            port: 4000
            enabled: true
        - hlf:
            version: 1
            scheme: grpc # the OSS doesn't yet support grpc
            host: 10.23.0.1
            port: 3241
            enabled: false


Parameters
----------

- meta: Contains metadata about the configuration
    - **version:** Version of the agentconfig. Currently can only be v1.0
- agents: Collection of available agents, with the key being the repoID
    - **version:** Version of the agent api. Integer, currently 1 exists
    - **scheme** (optional, defaults to http): The protocol over which the agent communicates, currently http is supported.
    - **host:** The hostname/ip-address where we can find the agent
    - **port:** The port on which the agent communicates
    - **enabled:** (optional, defaults to True) Determines if the agent is enabled
    - **supports-audit:** (optional, defaults to True) Determines whether the agent supports the audit API

The agent is configured to automatically reload the agent config if any
changes occur on the configmap or in the file-system


=================================================
Connecting Multiple Nodes to a MongoDB Repository
=================================================


==============================================
Connecting multiple nodes to IOTA MAM Channels
==============================================
