# Fix Google Services Accessibility on- buntu DNS Configuration Guide

This guide provides steps to resolve issues with accessing Google services on Ubuntu by configuring your DNS settings.

## Steps

1. **Open your terminal**

2. **Check DNS Configuration:**
   ```bash
   resolvectl status
   ```

3. **Edit DNS Configuration:**
   ```bash
   sudo nano /etc/systemd/resolved.conf
   ```

4. **Set Google DNS and Fallback DNS:**
   Add or modify these lines in the configuration file:
   ```
   [Resolve]
   DNS=8.8.8.8 8.8.4.4
   FallbackDNS=1.1.1.1 1.0.0.1
   ```
   Save and exit (In nano: Ctrl+X, then Y, then Enter)

5. **Restart the systemd-resolved Service:**
   ```bash
   sudo systemctl restart systemd-resolved
   ```

6. **Reboot your system:**
   ```bash
   sudo reboot
   ```

7. **Verify the changes:**
   After reboot, open terminal and run:
   ```bash
   resolvectl status
   ```

8. **Test the connection:**
   Open your web browser and go to [google.com](https://google.com)

## Troubleshooting

If issues persist:
- Ensure the configuration file was saved correctly
- Check your internet connection
- Try flushing your DNS cache:
  ```bash
  sudo systemd-resolve --flush-caches
  ```
- Temporarily disable any VPNs or proxy service

- 
## Contributing
If you find this guide helpful, please consider starring the repository. For issues or suggestions, please open an issue in this GitHub repository.
