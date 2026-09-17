<div align="center">

# nuwa-trusted-firmware-a

**Realtek Ameba customized [Trusted Firmware-A](https://www.trustedfirmware.org/projects/tf-a/), part of the [Nuwa Zephyr SDK](https://github.com/Ameba-AIoT/nuwa).**

[![License](https://badgen.net/badge/License/BSD%203-Clause/lightgrey)](dco.txt)

</div>

This repository contains Realtek's customized TF-A for the **RTL8730E** SoC. It provides the secure world firmware stages that run before the Zephyr kernel, enabling trusted boot and EL3 runtime services on the Cortex-A32 core.

## Boot Flow

```
BL1 (ROM) → BL2 (trusted boot) → BL31 (EL3 runtime) → Zephyr (Normal World)
```

| Stage | Role |
|:----- |:---- |
| BL1   | First-stage bootloader (ROM) |
| BL2   | Trusted boot: loads and authenticates subsequent images |
| BL31  | EL3 runtime firmware: provides PSCI, SMC services to Zephyr |

## Usage

This repository is fetched automatically when initializing the Nuwa SDK:

```bash
west init -m https://github.com/Ameba-AIoT/nuwa.git && west update
```

TF-A is built automatically as part of the sysbuild flow. See the [Nuwa SDK](https://github.com/Ameba-AIoT/nuwa) for documentation.
