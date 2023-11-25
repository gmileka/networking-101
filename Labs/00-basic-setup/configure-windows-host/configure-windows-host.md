# Configure Windows Host

#### Make a Windows machine ping-able

```bash
- Start | Settings | Windows Security | Firewall & network protection | Advanced settings
- This opens up: Windows Defender Firewall with Advanced Security
  - Inbound Rules | File and Printer Sharing (Echo Request - ICMPv4-In)
    - Update Domain/Private/Public to Enabled=Yes
- 
```

----

[Basic Setup](../basic-setup.md)