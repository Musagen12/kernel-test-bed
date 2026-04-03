# 🧪 Kernel Test Bed

> A lightweight, custom Linux kernel playground for testing features, patches, and configurations in isolation.

---

## 📌 Overview

This repository provides a minimal environment to:

- ⚙️ Test custom kernel builds
- 🧩 Experiment with kernel patches
- 🔍 Debug low-level behavior
- 🚀 Boot quickly using QEMU

> Intentionally simple and stripped down — built for experimentation, not production.

---

## 🧰 Requirements

Make sure your host system has:

| Tool | Purpose |
|------|---------|
| 🐧 Linux | Recommended host OS |
| 🖥️ QEMU | Virtualization / booting the kernel |
| `gcc` | C compiler |
| `make` | Build system |
| `flex` / `bison` | Lexer & parser tools |
| `libssl-dev` | SSL support |
| `libelf-dev` | ELF binary support |

Install build tools on Debian/Ubuntu:

```bash
sudo apt install gcc make flex bison libssl-dev libelf-dev qemu-system-x86
```

---

## 🚀 Getting Started

### 1️⃣ Clone the Repository

```bash
git clone https://github.com/Musagen12/kernel-test-bed.git
cd kernel-test-bed
```

### 2️⃣ Download the Root Filesystem

The root filesystem image is too large for Git (~2GB).

📥 Download `rootfs.img` from the **[latest release](https://github.com/Musagen12/kernel-test-bed/releases/latest)** and place it in the project root:

```
kernel-test-bed/
└── rootfs.img   ← place it here
```

### 3️⃣ Boot the Kernel

```bash
qemu-system-x86_64 \
  -kernel bzImage \
  -hda rootfs.img \
  -append "root=/dev/sda console=ttyS0" \
  -nographic
```

> 💡 Adjust flags depending on your architecture or hardware setup.

---

## 📁 Project Structure

```
kernel-test-bed/
├── 🧠 bzImage        # Compiled Linux kernel image
├── ⚙️  .config        # Kernel build configuration
├── 💽 rootfs.img     # Root filesystem (download from Releases)
└── 📄 README.md
```

---

## 🧠 Use Cases

- Kernel development practice
- Studying subsystems (memory management, scheduling, filesystems)
- Debugging kernel-level issues
- Trying out experimental patches

---

## ⚠️ Notes

- `rootfs.img` is **excluded from Git** due to its size (~2GB)
- Always download it from the [Releases page](https://github.com/Musagen12/kernel-test-bed/releases/latest)
- This environment is for **testing only** — not intended for production use

---

## 📜 License

[MIT](LICENSE) — do whatever you want, just don't blame anyone if it breaks 😄
