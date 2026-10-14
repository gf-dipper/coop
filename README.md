# Kötelék – 2 fős coop ügyességi játék a böngészőben

Két játékos, egy energiakötél. Ha túl messze kerültök egymástól, elszakad, és a pálya elölről indul.
30 pálya, 5 világ (alapok → gépezet → veszély → fejtörő → kihívás), kb. 1,5–2 óra két embernek.

Egyetlen fájl az egész (`index.html`), nem kell hozzá saját szerver: a két gép közvetlenül,
böngészőből kapcsolódik egymáshoz (WebRTC, PeerJS). GitHub Pages csak a fájlt szolgálja ki.

## Feltöltés GitHubra (kb. 3 perc)

1. GitHubon **New repository** → név pl. `kotelek` → Public → Create.
2. **Add file → Upload files** → húzd be az `index.html`-t → Commit changes.
3. A repo **Settings → Pages** menüjében: *Source: Deploy from a branch*, *Branch: main* / *(root)* → Save.
4. 1–2 perc múlva él a játék itt: `https://<felhasználóneved>.github.io/kotelek/`
   (a Pages oldalon kiírja a pontos címet).

Ha később módosítod az `index.html`-t, csak töltsd fel újra ugyanoda.

## Így játsszatok

1. Mindketten nyissátok meg a linket (asztali böngésző, Chrome/Edge/Firefox).
2. Az egyikőtök: **Szoba létrehozása** → kap egy 4 betűs kódot → elküldi a másiknak.
3. A másik: **Csatlakozás kóddal** → beírja → Mehet.
4. A szoba gazdája látja, hogy a társa csatlakozott, és elindítja (akár a pályaválasztóból is).

- Mozgás: **WASD** vagy **nyilak**.
- **Esc** (a szoba gazdájánál): szünet, pálya újra, pálya átugrása, főmenü.
- A célmezőre **mindkettőtöknek** rá kell állnia, miután minden kristályt összeszedtetek.
- A legjobb idők a gazda gépén mentődnek (böngésző tároló), a pályaválasztóban látszanak a csillagok.

## Pályaelemek

| Elem | Mit csinál |
|---|---|
| Kristály (kék gyémánt) | Mind kell, különben zárva a sárga kristálykapu |
| Nyomólap (lila/türkiz kör) | Amíg valaki rajta áll, nyitva az azonos színű ajtó |
| Kék / narancs sáv | Csak az adott színű játékos mehet át |
| Kulcs | Felveszed, és a lakatos ajtónak nekimenve kinyitod |
| Sárga gomb | 4,5 másodpercre kinyitja az óra-ajtót |
| Tüske, vörös gömb, lézer, löveg | Érintés = a pálya elölről |

## Ha nem jön létre a kapcsolat

- Mindkét gépen HTTPS-en fusson (a GitHub Pages ilyen) – fájlból (`file://`) megnyitva nem fog menni.
- Nagyon szigorú céges/iskolai hálózat vagy VPN blokkolhatja a WebRTC-t; próbáljátok mobilnetről vagy otthonról.
- Ha a kód „nem található”: a gazda oldalán nyitva kell lennie a lobbynak, és a kódot pontosan kell beírni.
- Teszteléshez van **Egy gépen** mód is: kék = WASD, narancs = nyilak.
