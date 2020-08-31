# SSH uppsetning á Raspberry Pi (Wi-Fi)

Þessar leiðbeiningar miða við að notast sé við Linux eða annað stýrikerfi sem getur lesið og skrifað í Linux partitions (`ext4`). Þessar breytingar fara fram á SD-kortinu sem notað er með Raspberry Pi-tölvunni, eftir að stýrikerfið hefur verið brennt á það. Öll skref eiga við um `rootfs` partition-ið nema annað sé tekið fram.

## SSH

Búa til tóma skrá í rót á `boot` partition sem heitir `ssh` (`touch ssh`).

## Hostname

Breyta innihaldi `/etc/hostname` (á `rootfs`) í það hostname sem er valið.

Opna `/etc/hosts` og breyta línunni `127.0.0.1 raspberrypi` í `127.0.0.1 [valið hostname]`.

## Wi-Fi

Opna `/etc/wpa_supplicant/wpa_supplicant.conf` og bæta eftirfarandi línum við:

```conf
country=IS

network={
    ssid="Taekniskolinn"
    key_mgmt=NONE
}
```

Þegar þessu er lokið er hægt að setja SD-kortið í Raspberry Pi, tengja það við rafmagn og tengjast því í gegn um SSH með hostname-inu sem var valið og notandanum `pi`. Sjálfgefið lykilorð er `raspberry` en ráðlagt er að breyta því.

`ssh pi@hostname`
