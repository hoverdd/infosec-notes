---
title: "Sysmon Event ID Reference"
draft: false
---

A practical reference of commonly used Sysmon Event IDs, useful for threat hunting, incident response, and general Windows forensics.

---

## 📘 Common Sysmon Event IDs

| Event ID | Description                        | Typical Use Case                                |
|----------|------------------------------------|--------------------------------------------------|
| 1        | Process creation                   | Detect suspicious process execution             |
| 3        | Network connection                 | Monitor outbound/inbound connections            |
| 6        | Driver loaded                      | Identify loading of unsigned or unusual drivers |
| 7        | Image loaded (DLLs)                | Track DLL hijacking or sideloading              |
| 8        | CreateRemoteThread                 | Detect code injection between processes         |
| 10       | Process access (OpenProcess)       | Useful for detecting injection/persistence      |
| 11       | File created                       | Monitor suspicious file creation                |
| 12–13    | Registry key/value set             | Persistence mechanisms via registry             |
| 15       | File stream created (ADS)          | Alternate Data Streams usage                    |
| 22       | DNS query                          | Reveal suspicious domain lookups                |
| 23       | File delete                        | Track removal of potential artifacts            |

---

## 🔧 Tools for Viewing `.evtx` Logs on Linux

- [`python-evtx`](https://github.com/williballenthin/python-evtx): `evtx_dump file.evtx`
- [`EvtxECmd`](https://ericzimmerman.github.io/): Full parsing with `mono EvtxECmd.exe`
- [`Chainsaw`](https://github.com/WithSecureLabs/chainsaw): Sigma-based detection and hunting  
- [`EVTX Format Explore`](https://omerbenamram.github.io/evtx/)  
A zero-install, browser-based viewer for Windows `.evtx` event log files.  
Perfect for quickly inspecting logs on any platform, including Linux — no setup required.
---

## 📝 Tips

- Use `Chainsaw hunt` to apply Sigma rules automatically.
- Prioritize event IDs: **1**, **3**, **7**, **10**, **12**, **22**.
- Keep in mind time correlation between events is key in real-world hunting.

---
