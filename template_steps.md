1. **Create VM via GUI**
   - Set a high VM ID; no media needed.
   - Enable QEMU Guest Agent.
   - Remove any disks.

2. **Add Cloud‑Init Drive**
   - Remove default CD/DVD.
   - Add Cloud‑Init drive under “Add” → set storage to `local`.

3. **Download and Import Cloud Image**
```bash
wget <cloud-image-url>.img
# resize optional
qm importdisk <VMID> <img-file> local-lvm
qm set <template_id> --serial0 socket --vga serial0
```
4. **Finishing touches**
    - Hardware -> Unused disk. Edit and add it
    - In options, disable network device and enable scsi device
    - Convert to template
