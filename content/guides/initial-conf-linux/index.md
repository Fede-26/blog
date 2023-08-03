---
title: "Things to do after installing Fedora Workstation (or any other linux distro)"
date: 2023-08-03T12:00:52+02:00
tags:
    - "Guides"
    - "Linux"
    - "Fedora"
langs: "English"
draft: false
showComments: true
---

# Introduction

Congratulations on successfully installing Fedora Linux on your PC! Fedora is a popular and user-friendly distribution of Linux, known for its stability, performance, and community support. Once you have completed the installation, there are a few essential configurations you should do to make the most of your Fedora experience. In this blog post, we'll guide you through the initial setup to ensure your system is secure, up-to-date, and ready for your needs.

# Enable Third-Party Repositories

After installation, open the Software app from the Applications menu. Go to the Software Repositories settings, and enable third-party repositories like RPM Fusion. This will provide access to additional software packages not available in the official Fedora repositories.
Do not enable any other repositories unless you know what you're doing.

# Update the System

Keeping your system up-to-date is crucial for security and performance. Open a terminal and run the following command to update your system:

```bash
sudo dnf update
```

This will fetch and install the latest updates, including bug fixes and security patches.

# Install Extension Manager

Fedora uses GNOME as the default desktop environment, and you can enhance its functionality through extensions. Install the Extension Manager app from Flatpak to manage your GNOME extensions easily. Run the following commands:

```bash
flatpak remote-add --if-not-exists flathub https://flathub.org/repo/flathub.flatpakrepo
flatpak install flathub com.mattjakeman.ExtensionManager
```

## OPTIONAL: Install GNOME Extensions

If you desire additional features for your GNOME desktop, consider installing extensions like "Blur My Shell" or "Just Perfection".
Open the *Extension Manager* to find and install the ones that best suit your needs.

# Disable Automatic Updates

By default, Fedora has automatic updates enabled, but you might prefer to manage updates manually. Open the Software app, go to the Updates settings, and disable automatic updates.

# Change the Shell to Fish

Fedora uses the Bash shell by default, but you can switch to Fish, a user-friendly and feature-rich shell. Install Fish using the following command:

```bash
sudo dnf install fish
```

After installation, set Fish as your default shell by running:

```bash
chsh -s /usr/bin/fish
```

Log out and log back in to apply the changes.

## OPTIONAL: Install Fisher

Fisher is a plugin manager for Fish, allowing you to install and manage various plugins. Install Fisher using the following command:

```bash
curl -sL https://raw.githubusercontent.com/jorgebucaran/fisher/main/functions/fisher.fish | source && fisher install jorgebucaran/fisher
```

# Install Topgrade

Topgrade is a useful tool for updating various package managers and running system maintenance tasks. Download the Topgrade executable from its GitHub repository and put it in the `~/.local/bin` directory. Here's how to do it:

1. Download the latest release from [github](https://github.com/topgrade-rs/topgrade/releases/);
2. Extract the archive and put the executable in the `~/.local/bin` directory;
3. Make the executable executable with `chmod +x ~/.local/bin/topgrade`;
4. Add the `~/.local/bin` directory to your `PATH` environment variable using this command: `fish_add_path ~/.local/bin`;
5. Run `topgrade` to update your system.

# Install asdf Version Manager

You may want to read this article if you're interested in using asdf:

{{< article link="/blog/guides/asdf-how-to/" >}}
<br>

# Configure the Firewall

Fedora comes with a built-in firewall called firewalld, providing essential network security. Enable the firewall and add necessary rules using the following commands:

```bash
sudo systemctl enable --now firewalld
sudo firewall-cmd --add-service=ssh --permanent  # Allowing SSH (optional)
sudo firewall-cmd --reload
```

Replace `ssh` with other services you wish to enable if needed.

# Configure Backup for Btrfs

If you have installed Fedora on a Btrfs filesystem, you can take advantage of its snapshot and rollback features for easy backups. The built-in tool for managing Btrfs snapshots is `snapper`. Install it using the following command:

```bash
sudo dnf install snapper
```

After installation, you can configure snapshot policies and schedule regular snapshots to ensure your data is protected.

# Conclusion

With these step-by-step configurations, your Fedora Linux PC is now ready for an optimal experience. The enabled repositories, updated system, custom shell, and additional extensions will enhance your productivity and usability. Disabling automatic updates, configuring the firewall, and setting up Btrfs backups contribute to a more secure and robust system.

Remember that Fedora Linux offers a wealth of possibilities, and as you explore further, you'll discover more tools and features tailored to your needs. Enjoy your Fedora journey, and happy computing!