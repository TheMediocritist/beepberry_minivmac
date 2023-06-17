# Mini-vMac for Beepberry

Requires: 
    * SDL2
    * [snag](https://github.com/TheMediocritist/snag) or similar tool to copy accellerated framebuffer to Sharp Memory LCD framebuffer 

### 1. Download source code from https://www.gryphel.com/c/minivmac/download.html
```
wget https://www.gryphel.com/d/minivmac/minivmac-36.04/minivmac-36.04.src.tgz
```

### 2. Build setup tool
```
gcc setup/tool.c -o setup_t
```

### 3. Create and run setup script
```
./setup_t -t larm -cpu arm -api sd2 -hres 384 -vres 240 -depth 0 -speed 1 -mem 4M -sound 1 > setup.sh
chmod +x setup.sh
./setup.sh
```

### 4. Build minivmac
```
make
```

### 5. Download, unzip and rename BIOS
```
sudo apt-get install p7zip
wget http://hampa.ch/pub/software/ROM/Macintosh%2068K/4D1F8172%20-%20Macintosh%20Plus%20-%20Rev%203.7z
p7zip -d "4D1F8172 - Macintosh Plus - Rev 3.7z"
mv '4D1F8172 - Macintosh Plus - Rev 3.rom' vMac.ROM
```

### 6. Download, unzip and rename disk image
```
wget http://toughdev.com/public/old_mac_softs.zip
unzip old_mac_softs.zip
cd old_mac_softs
unzip hfv500M_sys755_clean.zip  
mv hfv500M_sys755_clean.dsk ..disk1.dsk
cd ..
```

### 7. Set user permissions to allow keyboard and mouse input to SDL2
```
sudo usermod -aG input `myname`
```

### 8. Run
```
./minivmac
```
