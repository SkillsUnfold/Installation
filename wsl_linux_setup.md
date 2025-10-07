# Overview

Many scientific and bioinformatics tools are easiest to use on Linux.
While some Conda packages do not support Windows natively, **Windows
Subsystem for Linux (WSL2)** lets you run Linux directly on Windows
without a virtual machine or dual boot. This guide shows you how to set
up **WSL2**, **MobaXterm** (for graphical apps), **Conda**, **Mamba**,
and the X11 libraries needed for tools like **RStudio**.

> **What you’ll get**
>
> -   A working Linux environment on Windows (Ubuntu via WSL2).
> -   Fast package management with Conda + Mamba.
> -   Graphical (X11) support through MobaXterm so you can launch GUI
>     apps from WSL.

------------------------------------------------------------------------

# Prerequisites

-   Windows 10 (2004 or later) or Windows 11 with administrator access.
-   Stable internet connection.
-   ~5–10 GB free disk space.

------------------------------------------------------------------------

# Step 1 — Install Windows Subsystem for Linux (WSL2)

Follow Microsoft’s official instructions to install WSL2 and a Linux
distribution (Ubuntu is recommended).

-   Open **PowerShell as Administrator** and run (Microsoft docs will
    guide you through this):

<!-- -->

    # In an elevated PowerShell window (Admin)
    wsl --install

-   If prompted, reboot your computer.
-   Launch **Ubuntu** from the Start Menu and set a username/password.

> If you need the full guide, see Microsoft’s page:
> <https://docs.microsoft.com/en-us/windows/wsl/install-win10>

------------------------------------------------------------------------

# Step 2 — Install MobaXterm (Graphical Terminal for Windows)

Download and **install** MobaXterm (choose the **Installer** version,
not the portable one).

-   <https://mobaxterm.mobatek.net>

Open MobaXterm after installation.

------------------------------------------------------------------------

# Step 3 — Connect MobaXterm to Your WSL

1.  Open **MobaXterm**.
2.  In the **left panel**, you should see your WSL distro (e.g.,
    `Ubuntu (WSL)`).  
    Double-click it to open a terminal.
3.  If you don’t see it or cannot connect, enable SSH inside WSL and
    start the SSH service.  
    (Stop after the step “Start or restart the SSH service”; later steps
    are optional.)

------------------------------------------------------------------------

# Step 4 — Install Conda (Miniconda) in WSL (Linux)

In the MobaXterm **WSL terminal** (Ubuntu), download and install
**Miniconda**:

    # Download the latest Miniconda installer for Linux (x86_64)
    wget https://repo.anaconda.com/miniconda/Miniconda3-latest-Linux-x86_64.sh

    # Run the installer
    sh Miniconda3-latest-Linux-x86_64.sh

Follow the on-screen prompts (answer **yes** to initialize Conda). Then
**restart** your terminal and run:

    # Initialize Conda for your shell
    conda init

> After restarting the terminal, you should see `(base)` appear in your
> prompt.

------------------------------------------------------------------------

# Step 5 — Install Mamba (Faster Conda)

`mamba` is a drop-in, faster replacement for `conda` in most commands:

    conda install -n base -c conda-forge mamba

------------------------------------------------------------------------

# Step 6 — Install X11 Libraries (for GUI apps like RStudio)

Install the system libraries required to run graphical Linux
applications under WSL:

    sudo apt-get update
    sudo apt-get install -y   libgl1-mesa-glx libegl1-mesa libxrandr2 libxss1   libxcursor1 libxcomposite1 libasound2 libxi6 libxtst6

> If you see missing-library errors when launching a GUI program, come
> back and install the suggested packages here.

------------------------------------------------------------------------

# Step 7 — Restart and Reconnect

1.  Close **MobaXterm** and reopen it.
2.  Double-click your **WSL (Ubuntu)** session in the left panel.
3.  You are now ready to create environments and install Linux-only
    tools with Conda/Mamba.

------------------------------------------------------------------------

# (Optional) Quick Test

Create a small test environment:

    # Create and activate a test environment
    mamba create -n test-env python=3.11 -y
    conda activate test-env

    # Verify Python
    python -V

------------------------------------------------------------------------

# Notes & Tips

-   **File locations:** Your Windows files are accessible in WSL at
    `/mnt/c/Users/<YourName>/...`  
-   **Performance:** Keep large Conda environments and datasets on the
    WSL (Linux) filesystem (e.g., `/home/<user>`) for best speed.
-   **RStudio GUI:** You can run RStudio Server or desktop variants; for
    desktop, MobaXterm’s X11 makes it possible. If you prefer a
    browser-based setup, RStudio Server inside WSL is another good
    option.
-   **Troubleshooting SSH:** If MobaXterm doesn’t list WSL
    automatically, ensure the SSH service is running and that your WSL
    instance is up to date.
-   **Security:** Only enable passwordless SSH if you understand the
    implications. Default settings are fine for most users.

------------------------------------------------------------------------

# You’re Done!

You now have a Linux-ready environment on Windows with Conda/Mamba and
X11 support.  
This setup is robust for bioinformatics and data science workflows that
expect a Linux stack.
