### Parallels Desktop Crack (Parallels Desktop 18.1.1 53328 İçin)
- **Intel Desteği**
- **Apple Silicon Desteği (M1 & M2)**
- **Ağ Desteği**
- **USB Desteği**

### Kullanım Talimatları
1. Parallels Desktop'ı kurun.
   
   [Buradan indirin](https://download.parallels.com/desktop/v18/18.1.1-53328/ParallelsDesktop-18.1.1-53328.dmg).

2. Parallels hesabından çıkış yapın.
3. Bu repodaki dosyaları indirin.
4. Dosyaları çıkarın ve bu dizinde Terminal'i çalıştırın.
   
   ```bash
   chmod +x ./install.sh && sudo ./install.sh
   ```

   Eğer "Operation not permitted" (İşlem izni verilmedi) hatası alırsanız, Terminal uygulamanız için "Full Disk Access" (Tam Disk Erişimi) iznini etkinleştirin.

   **System Preferences ▸ Security & Privacy ▸ Privacy ▸ Full Disk Access**

   Eğer "codesign" hatası alırsanız, xcode komut satırı araçlarının kurulu olduğundan emin olun. Kurmak için şu komutu kullanın:

   ```bash
   xcode-select --install
   ```

   Kurulu olup olmadığını kontrol etmek için şu komutu kullanın:

   ```bash
   xcode-select -p
   ```

   Eğer /Library/Developer/CommandLineTools veya /Applications/Xcode.app/Contents/Developer çıktısını alırsanız, komut satırı araçları doğru bir şekilde yüklenmiştir.

### Manuel Kurulum
1. Parallels Desktop'ı açın ve hesabınızdan çıkış yapın.
2. Parallels Desktop'tan çıkış yapın.
3. **prl_disp_service** hizmetinin çalışmadığından emin olun.

   ```bash
   pkill -9 prl_disp_service
   ```

4. Cracked (kırılmış) **prl_disp_service** dosyasını kopyalayın:

   ```bash
   sudo cp -f prl_disp_service "/Applications/Parallels Desktop.app/Contents/MacOS/Parallels Service.app/Contents/MacOS/prl_disp_service"
   sudo chown root:wheel "/Applications/Parallels Desktop.app/Contents/MacOS/Parallels Service.app/Contents/MacOS/prl_disp_service"
   sudo chmod 755 "/Applications/Parallels Desktop.app/Contents/MacOS/Parallels Service.app/Contents/MacOS/prl_disp_service"
   ```

5. **licenses.json** dosyasını kopyalayın:

   ```bash
   sudo cp -f licenses.json "/Library/Preferences/Parallels/licenses.json"
   sudo chown root:wheel "/Library/Preferences/Parallels/licenses.json"
   sudo chmod 444 "/Library/Preferences/Parallels/licenses.json"
   sudo chflags uchg "/Library/Preferences/Parallels/licenses.json"
   sudo chflags schg "/Library/Preferences/Parallels/licenses.json"
   ```

6. **prl_disp_service** dosyasını imzalayın:

   ```bash
   sudo codesign -f -s - --timestamp=none --all-architectures --entitlements ParallelsService.entitlements "/Applications/Parallels Desktop.app/Contents/MacOS/Parallels Service.app/Contents/MacOS/prl_disp_service"
   ```

### Önemli Notlar
Parallels Desktop, müşteri bilgilerini veya günlük dosyalarını sunucuya yükleyebilir. Bunun olmasını engellemek için bir firewall (güvenlik duvarı), hosts dosyası veya özel DNS kullanabilirsiniz. Bu, yerleşik indiricinin çalışmasını engeller, ancak önceden oluşturulmuş sanal makineleri aşağıdaki bağlantılardan indirebilirsiniz.

#### Apple Silicon İçin
- https://update.parallels.com/desktop/v18/appliances_arm.xml
- https://update.parallels.com/desktop/v18/appliances_arm_Monterey.xml

#### Intel İçin
- https://update.parallels.com/desktop/v18/appliances.xml

### Hosts Dosyasını Düzenleme
Parallels Desktop aşağıdaki etki alanlarını kullanabilir, bu nedenle bunları **hosts** dosyanıza ekleyebilirsiniz:

```plaintext
127.0.0.1 download.parallels.com
127.0.0.1 update.parallels.com
127.0.0.1 desktop.parallels.com
127.0.0.1 download.parallels.com.cdn.cloudflare.net
127.0.0.1 update.parallels.com.cdn.cloudflare.net
127.0.0.1 desktop.parallels.com.cdn.cloudflare.net
127.0.0.1 www.parallels.cn
127.0.0.1 www.parallels.com
127.0.0.1 www.parallels.de
127.0.0.1 www.parallels.es
127.0.0.1 www.parallels.fr
127.0.0.1 www.parallels.nl
127.0.0.1 www.parallels.pt
127.0.0.1 www.parallels.ru
127.0.0.1 www.parallelskorea.com
127.0.0.1 reportus.parallels.com
127.0.0.1 parallels.cn
127.0.0.1 parallels.com
127.0.0.1 parallels.de
127.0.0.1 parallels.es
127.0.0.1 parallels.fr
127.0.0.1 parallels.nl
127.0.0.1 parallels.pt
127.0.0.1 parallels.ru
127.0.0.1 parallelskorea.com
127.0.0.1 pax-manager.myparallels.com
127.0.0.1 myparallels.com
127.0.0.1 my.parallels.com
```

**Hosts dosyasını kilitleme:**

```bash
sudo chflags uchg /etc/hosts
sudo chflags schg /etc/hosts
```

### AdGuardHome İçin
Aşağıdaki kuralları özel filtreleme kurallarınıza ekleyin:

```plaintext
||myparallels.com^$important
||parallels.cn^$important
||parallels.com^$important
||parallels.de^$important
||parallels.es^$important
||parallels.fr^$important
||parallels.nl^$important
||parallels.pt^$important
||parallels.ru^$important
||parallelskorea.com^$important
||parallels.com.cdn.cloudflare.net^$important
```

### SSS
**Neden prl_disp_service dosyası bu kadar büyük?**
- Bu, orijinal **prl_disp_service** dosyası için doğrudan yamanmış bir dosyadır.

**Bu crack güvenli mi?**
- Bu dosya açık kaynaklıdır. İstediğiniz herhangi bir hex dosya karşılaştırma aracını kullanarak **prl_disp_service** dosyasındaki değişiklikleri inceleyebilirsiniz.

**Kendim kırmak istiyorum.**
- **prl_disp_service.md** dosyasına göz atarak nasıl kırdığımı görebilirsiniz.


EN


### Parallels Desktop Crack (For Parallels Desktop 18.1.1 53328)
- **Intel Support**
- **Apple Silicon Support (M1 & M2)**
- **Network Support**
- **USB Support**

### Usage Instructions
1. Install Parallels Desktop.
   
   [Download from here](https://download.parallels.com/desktop/v18/18.1.1-53328/ParallelsDesktop-18.1.1-53328.dmg).

2. Exit from your Parallels account.
3. Download the files in this repository.
4. Extract the files and open Terminal in this directory.
   
   ```bash
   chmod +x ./install.sh && sudo ./install.sh
   ```

   If you encounter the "Operation not permitted" error, enable "Full Disk Access" permission for your Terminal app.

   **System Preferences ▸ Security & Privacy ▸ Privacy ▸ Full Disk Access**

   If you encounter a "codesign" error, ensure that Xcode command line tools are installed. Use the following command to install them:

   ```bash
   xcode-select --install
   ```

   To check if it’s installed, use this command:

   ```bash
   xcode-select -p
   ```

   If the output is /Library/Developer/CommandLineTools or /Applications/Xcode.app/Contents/Developer, the command line tools are installed correctly.

### Manual Installation
1. Open Parallels Desktop and log out of your account.
2. Exit Parallels Desktop.
3. Ensure that **prl_disp_service** is not running.

   ```bash
   pkill -9 prl_disp_service
   ```

4. Copy the cracked **prl_disp_service** file:

   ```bash
   sudo cp -f prl_disp_service "/Applications/Parallels Desktop.app/Contents/MacOS/Parallels Service.app/Contents/MacOS/prl_disp_service"
   sudo chown root:wheel "/Applications/Parallels Desktop.app/Contents/MacOS/Parallels Service.app/Contents/MacOS/prl_disp_service"
   sudo chmod 755 "/Applications/Parallels Desktop.app/Contents/MacOS/Parallels Service.app/Contents/MacOS/prl_disp_service"
   ```

5. Copy the **licenses.json** file:

   ```bash
   sudo cp -f licenses.json "/Library/Preferences/Parallels/licenses.json"
   sudo chown root:wheel "/Library/Preferences/Parallels/licenses.json"
   sudo chmod 444 "/Library/Preferences/Parallels/licenses.json"
   sudo chflags uchg "/Library/Preferences/Parallels/licenses.json"
   sudo chflags schg "/Library/Preferences/Parallels/licenses.json"
   ```

6. Sign the **prl_disp_service** file:

   ```bash
   sudo codesign -f -s - --timestamp=none --all-architectures --entitlements ParallelsService.entitlements "/Applications/Parallels Desktop.app/Contents/MacOS/Parallels Service.app/Contents/MacOS/prl_disp_service"
   ```

### Important Notes
Parallels Desktop may upload client information or log files to the server. To prevent this, you can use a firewall, modify the hosts file, or use a custom DNS. This may prevent the built-in downloader from working, but you can still download prebuilt virtual machines from the following links:

#### For Apple Silicon
- https://update.parallels.com/desktop/v18/appliances_arm.xml
- https://update.parallels.com/desktop/v18/appliances_arm_Monterey.xml

#### For Intel
- https://update.parallels.com/desktop/v18/appliances.xml

### Editing the Hosts File
Parallels Desktop might use the following domains, so you can block them by adding these entries to your **hosts** file:

```plaintext
127.0.0.1 download.parallels.com
127.0.0.1 update.parallels.com
127.0.0.1 desktop.parallels.com
127.0.0.1 download.parallels.com.cdn.cloudflare.net
127.0.0.1 update.parallels.com.cdn.cloudflare.net
127.0.0.1 desktop.parallels.com.cdn.cloudflare.net
127.0.0.1 www.parallels.cn
127.0.0.1 www.parallels.com
127.0.0.1 www.parallels.de
127.0.0.1 www.parallels.es
127.0.0.1 www.parallels.fr
127.0.0.1 www.parallels.nl
127.0.0.1 www.parallels.pt
127.0.0.1 www.parallels.ru
127.0.0.1 www.parallelskorea.com
127.0.0.1 reportus.parallels.com
127.0.0.1 parallels.cn
127.0.0.1 parallels.com
127.0.0.1 parallels.de
127.0.0.1 parallels.es
127.0.0.1 parallels.fr
127.0.0.1 parallels.nl
127.0.0.1 parallels.pt
127.0.0.1 parallels.ru
127.0.0.1 parallelskorea.com
127.0.0.1 pax-manager.myparallels.com
127.0.0.1 myparallels.com
127.0.0.1 my.parallels.com
```

**Locking the hosts file:**

```bash
sudo chflags uchg /etc/hosts
sudo chflags schg /etc/hosts
```

### For AdGuardHome
Add the following rules to your custom filtering rules:

```plaintext
||myparallels.com^$important
||parallels.cn^$important
||parallels.com^$important
||parallels.de^$important
||parallels.es^$important
||parallels.fr^$important
||parallels.nl^$important
||parallels.pt^$important
||parallels.ru^$important
||parallelskorea.com^$important
||parallels.com.cdn.cloudflare.net^$important
```

### FAQ
**Why is the prl_disp_service file so big?**
- It is a directly patched file for the original **prl_disp_service** file.

**Is this crack safe?**
- It’s open-source. You can use any hex file comparison tool to open **prl_disp_service** and see what has been modified.

**I want to crack it myself.**
- Check the **prl_disp_service.md** file to see how I cracked it.
