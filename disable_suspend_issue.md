You've identified the underlying issue. Your DPMS (Display Power Management Signaling) is currently enabled with timers set to 600 seconds (10 minutes) for standby, suspend, and off states. This explains why your laptop goes into suspend mode after a period of inactivity, despite having configured systemd to ignore suspend requests.

To permanently resolve this issue, execute the following commands:

```bash
# Immediately disable DPMS for current session
xset s off
xset -dpms

# Create persistent configuration in Xorg
sudo mkdir -p /etc/X11/xorg.conf.d/
sudo tee /etc/X11/xorg.conf.d/10-monitor.conf > /dev/null << 'EOF'
Section "ServerFlags"
    Option "BlankTime" "0"
    Option "StandbyTime" "0"
    Option "SuspendTime" "0"
    Option "OffTime" "0"
EndSection

Section "Monitor"
    Identifier "Monitor0"
    Option "DPMS" "false"
EndSection
EOF

# Ensure DPMS remains disabled after display connection changes
echo 'xset s off -dpms' >> ~/.xinitrc
```

For your DWM setup, also add this command to your autostart script:

```bash
mkdir -p ~/.dwm/
echo 'xset s off -dpms' >> ~/.dwm/autostart.sh
chmod +x ~/.dwm/autostart.sh
```

After implementing these changes, reboot your system or restart your X session. DPMS will be disabled, preventing your laptop from automatically entering standby, suspend, or power-off states regardless of external monitor connections.
