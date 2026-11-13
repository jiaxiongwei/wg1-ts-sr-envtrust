Appendix II Reference environment measurement data model
========================================================

(This appendix is not an integral part of this Recommendation.)

This appendix provides an example JSON reference implementation of the reference environment measurement data model described in Clause 9.2.6. The field semantics and structural attributes defined in this appendix align strictly with the security requirements specified in Clause 8.1.

.. code-block:: json

    {
      "measurement": {
        "schemaVersion": "1.0",
        "measurementId": "meas-20260831-001",
        "environmentType": "TEE",
        "securityLevel": "hardwareIsolated",
        "teeTechnology": "Intel SGX",
        "teeVersion": "2.0",
        "integrityMeasurements": [
          {
            "measurementType": "MRENCLAVE",
            "algorithm": "SHA-256",
            "value": "a1b2c3d4e5f67890a1b2c3d4e5f67890a1b2c3d4e5f67890a1b2c3d4e5f67890"
          },
          {
            "measurementType": "MRSIGNER",
            "algorithm": "SHA-256",
            "value": "f6e5d4c3b2a19078f6e5d4c3b2a19078f6e5d4c3b2a19078f6e5d4c3b2a19078"
          },
          {
            "measurementType": "BIOS",
            "algorithm": "SHA-384",
            "value": "b1c2d3e4f5a6b7c8d9e0f1a2b3c4d5e6f7a8b9c0d1e2f3a4b5c6d7e8f9a0b1c2"
          }
        ],
        "platformIdentity": {
          "platformId": "platform-12345-abcde",
          "manufacturer": "Example Corp",
          "model": "SecureServer X200",
          "firmwareVersion": "2.3.1"
        },
        "runtimeContext": {
          "agentId": "did:example:agent-67890",
          "runtimeVersion": "1.2.3",
          "osName": "Ubuntu",
          "osVersion": "22.04 LTS"
        },
        "temporalInfo": {
          "measurementTime": "2026-08-31T10:00:00Z",
          "notBefore": "2026-08-31T10:00:00Z",
          "notAfter": "2026-08-31T11:00:00Z"
        },
        "attestationMechanism": "SGX",
        "extensions": {
          "sgxEpcSize": "128MB",
          "isvProductId": "1",
          "isvSvn": "2"
        }
      },
      "signature": {
        "algorithm": "ES256",
        "value": "base64-encoded-signature-bytes-here",
        "certificateChain": [
          "base64-encoded-cert-1",
          "base64-encoded-cert-2"
        ]
      },
      "attestationMetadata": {
        "attestationId": "attest-20260831-001",
        "attestationVersion": "1.0",
        "challengeNonce": "nonce-12345-abcde",
        "verifierPublicKey": "base64-encoded-public-key"
      }
    }
