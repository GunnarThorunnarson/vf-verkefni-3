# SSH uppsetning á Raspberry Pi Zero W (Wi-Fi)

Þessar breytingar fara fram á SD-kortinu sem notað er með Raspberry Pi-tölvunni, eftir að stýrikerfið hefur verið brennt á það (á boot partition).

## SSH

Búa til tóma skrá í rót sem heitir `ssh` (`touch ssh`).

## Hostname

Breyta innihaldi `/etc/hostname` í það hostname sem er valið.

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
