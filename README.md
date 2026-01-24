![Markuse arvuti asjad](mas_computers.png)

# Markuse arvuti asjad (süsteemifailid)

* Keel: Linuxi konfiguratsioonifailid
* Valmimise aasta: 2026
* Viimane uuendus: 24. jaanuar 2026

## Paigaldamise juhised

Paigalda arvutisse [Omarchy Linux](https://omarchy.org/). Kõigepealt klooni see hoidla mingisse kausta (git clone). Seejärel paigalda järgmised komponendid:

* **Buutimismenüü**
  * Vaadake, mis on failis boot/limine.conf ja võrrelge seda enda arvutis oleva /boot/limine.conf failiga
  * Asendage süsteemifailis kogu sisu enne `/+Omarchy` silti hoidlas oleva faili sisuga
  * Ärge muutke silti ega midagi sellele järgnevat
* **Buutimismenüü taustapilt**
  * Leidke üles EFI süsteemipartitsiooni haakepunkt (vaikesättena `/boot/EFI`)
  * Kopeerige taustapilt (EFI/limine/wallpaper.png) järgmisesse kausta: *esp*/limine
* **Buutimisheli**
  * Muuda systemd uniti sisu vastavalt riistvara ja tarkvara konfiguratsioonile: `nano etc/systemd/system/mas-chimes.service`
  * Kopeeri systemd unit: `cp etc/systemd/system/mas-chimes.service /etc/systemd/system`
  * Lisa käivitusheli ja sulgemisheli järgmistesse asukohtadesse: `~/.mas/startup_linux.wav` ja `~/.mas/shutdown.wav`
  * Käivita `systemctl daemon-reload` superkasutajana
  * Lülita teenus sisse: `systemctl enable mas-chimes`
* **Plymouth**
  * Kirjuta üle olemasolev `omarchy` teema: `sudo cp usr/share/plymouth/themes/omarchy/* /usr/share/plymouth/themes/omarchy`
  * Taasinstalli kernel: `sudo pacman -Syu linux`
  * Taaskäivita arvuti: `reboot`
