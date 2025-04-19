
# Everything to get nvidia working
 ### Maybe one day I'll automate this
### I'm not supporting or maintaining this so if you break its, thats on you

  

# Steps To Get NVIDIA Working
1. Disable nouveau driver
`sudo  nano  /etc/modprobe.d/blacklist-nouveau.conf`

  

2. Put this in the `blacklist-nouveau.conf`

    blacklist  nouveau
    options  nouveau  modeset=0

  

3. Then, regenerate initramfs
`sudo  mkinitcpio  -P`



4. Install the Proprietary NVIDIA Drivers
`sudo  pacman  -S  nvidia  nvidia-utils  nvidia-prime`

  
  

5. R E B O O T
`sudo  reboot`

  
  

# Verify drivers are loaded

`lsmod  |  grep  nvidia`

  

**If this shows nothing, something didn't work. This should respond with something like:**

    nvidia  git:(main)  ✗  lsmod  |  grep  nvidia
    nvidia_drm  135168  3
    nvidia_uvm  3792896  0
    nvidia_modeset  1830912  3  nvidia_drm
    nvidia  97095680  37  nvidia_uvm,nvidia_modeset
    drm_ttm_helper  16384  2  nvidia_drm,xe
    video  81920  3  xe,i915,nvidia_modeset

  
  

**Now, we can launch specific apps with prime-run to use the NVIDIA card**

`prime-run  firefox-development-edition`
`prime-run  kitty`

  

**Once you launch an app with prime-run, check and make sure it works with**:

`nvidia-smi`
