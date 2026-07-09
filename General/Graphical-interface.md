# How graphical desktop loads

'''
On GNOME-based systems, including Ubuntu, Fedora, and RHEL, the default display manager is GDM3 (GNOME Display Manager). KDE-based systems use SDDM (Simple Desktop Display Manager) on modern installations; older documentation may reference KDM as KDE's display manager, but KDM has been discontinued and replaced by SDDM on current distributions.

Under the hood, the display manager relies on a display server, the software that handles communication between your hardware and the graphical applications you run.

Historically, this role was filled by the X Window System (commonly called X or X11). While X originated in the mid-1980s, it has been a core component of Linux desktop environments since the kernel's inception in the early 1990s. While X served the Linux ecosystem reliably for decades, it was designed for a different era of computing, and over time its limitations in security, performance, and support for modern hardware have become increasingly difficult to work around.

Its successor is Wayland(opens in a new tab), which takes a more modern and architecturally cleaner approach to the same role. Wayland is now the default display server on most current distributions, including Ubuntu 22.04 and later, Fedora, and RHEL. If you are running an older distribution, such as Ubuntu 18.04 or CentOS 7, your system is likely still using X11, which continues to function reliably on those platforms.

For everyday use, the transition from X11 to Wayland is largely transparent. The desktop looks and behaves the same. The main differences are architectural: improved security, better support for high-resolution displays, fractional scaling, and more responsive input handling.

If the graphical desktop does not start automatically, it can be launched manually from a text console by starting the display manager directly. The command you use to accomplish this varies slightly depending on the distribution: on Ubuntu and some other Debian-based systems, the command is sudo systemctl start gdm3, while on Fedora, RHEL, and several other distributions, it is sudo systemctl start gdm. Either way, the result is the same: the display manager starts and the login screen is presented. The older startx command is also available on many systems and launches a desktop session directly, bypassing the login screen entirely. This approach is less common on modern installations but remains a useful fallback when the display manager cannot be started.
'''

# Desktop enviroments

'''One aspect of Linux that often surprises users coming from Windows or macOS is that the desktop itself is not a fixed component of the operating system. It is a separate, interchangeable component called a desktop environment, and there are several to choose from. It is even possible to install and switch between multiple desktop environments on the same system. This is one of Linux's defining characteristics, and one of the first things that sets it apart from other operating systems.

Every desktop environment is built around two core components:

•
A session manager, which starts and maintains the elements of the graphical session.

•
A window manager, which controls how windows are displayed, moved, resized, and decorated on screen.

These two components, along with a consistent set of bundled applications and utilities, are generally used together as a coordinated unit, and it is this combination that produces the seamless, unified experience the user sees as a desktop. Technically, components from different environments can be mixed, but in practice, most users work within a single, complete desktop environment.

GNOME
This course uses GNOME across all three Linux distribution families covered: Red Hat (Fedora, RHEL/CentOS), SUSE (openSUSE), and Debian (Ubuntu, Linux Mint). GNOME is the most widely deployed desktop environment in the Linux ecosystem and is the default on all of these distributions. Ubuntu 24.04, for example, ships with GNOME 46.


KDE Plasma

KDE Plasma is the other major desktop environment you are likely to encounter. It is more feature-rich and highly configurable, with a layout (a taskbar along the bottom, an application launcher, and a system tray) that will feel immediately familiar to users coming from Windows. KDE has traditionally been associated with SUSE and openSUSE, though openSUSE also offers a GNOME variant, which is the version used in this course.

Other Desktop Environments

The Linux ecosystem includes several additional desktop environments worth being aware of:

•
XFCE and LXQt are lightweight environments designed for older or lower-powered hardware. They are practical choices when system resources are limited.

•
Cinnamon is the default desktop on Linux Mint. It features a traditional layout (a taskbar along the bottom, a start menu, and a system tray) that will feel comfortable to users transitioning from Windows.

•
MATE is a continuation of the older GNOME 2 interface and is favored by users who prefer a more classical desktop experience.

If you are using any of these environments, your screen will look different from the examples shown in this course. That is entirely expected; the core concepts are consistent across all of them, and the workflows covered here translate directly regardless of which environment you are working in.

'''

# GNOME Tweaks
'''
GNOME's default Settings application is intentionally streamlined, and that simplicity comes at a cost. A significant number of options that users would reasonably expect to find there are simply not exposed. If you have searched for a particular setting and come up empty, you are not alone; this is one of the most common sources of frustration for both new and experienced GNOME users.

The solution is GNOME Tweaks (gnome-tweaks), a separate utility that provides access to a much wider range of configuration options. Among other things, it allows you to:

•
Adjust interface, document, and monospace fonts.

•
Modify window titlebar layouts and button placement.

•
Change icon themes, cursor themes, and legacy application (GTK) themes.

•
Configure keyboard behavior: for example, remapping the CapsLock key to function as an additional Ctrl key, a popular choice among users who rely heavily on keyboard shortcuts.

•
Manage startup applications.

•
Install and enable GNOME Shell extensions.

GNOME Tweaks is not installed by default on all distributions, but it is available in the software repositories of virtually every GNOME-based system. It can be installed from the App Center on Ubuntu, or via the terminal.

On Ubuntu and other Debian-based distributions, you can use the following command:
sudo apt install gnome-tweaks
On Fedora and other RHEL-based distributions, you can use the following command:


sudo dnf install gnome-tweaks
Once installed, launch it by searching for "Tweaks" in the application menu, or by pressing Alt+F2 and typing 'gnome-tweaks'. Given how often you may return to it, adding it to your Favorites bar is worth considering.

Note:
Older documentation may refer to this tool as gnome-tweak-tool, its original name. The utility is the same; only the name has changed in more recent versions.

GNOME Extensions

In recent versions of GNOME, some functionality previously handled by GNOME Tweaks has been moved into a dedicated tool called GNOME Extensions (gnome-extensions-app). This application manages GNOME Shell extensions — add-ons that modify or enhance the behavior of the desktop itself — and on some distributions, it also handles certain appearance settings.

Extensions can be browsed and installed from the GNOME Extensions website(opens in a new tab), which offers a large library of community-developed add-ons. Popular examples include extensions that restore a system tray, modify the top bar, improve window tiling, or bring back features that have been removed from GNOME's defaults over time.

In practice, GNOME Tweaks and GNOME Extensions are complementary tools. Tweaks handles appearance and behavioral settings; Extensions manages shell-level add-ons. You are likely to find yourself using both.
'''