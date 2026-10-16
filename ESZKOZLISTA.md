# Kötelék – grafikai eszközlista és promptok (neon-pixel art, anime beütéssel)

Ez a lista ahhoz kell, hogy a generált képek **egymáshoz illjenek**, és én gond nélkül be tudjam építeni őket. A játék logikája nem változik, csak a rajzoló réteg: minden elem helyére egy kép kerül, a fény- és bloom-réteg marad fölötte.

---

## 1. Stílus-alap (ezt minden promptba bele kell tenni)

**Stílus-előtag (angolul, mert a képmodellek azt értik):**

```
pixel art game sprite, clean 1px outlines, limited neon synthwave palette, dark navy background,
anime-inspired chibi proportions, crisp pixels, no anti-aliasing, no blur, top-down view,
centered, single object, plain solid background color #0b0f1a
```

**Negatív prompt** (ahol van ilyen mező):
```
blurry, smooth shading, photorealistic, 3d render, text, watermark, multiple objects, cropped, gradient background, drop shadow
```

**Paletta** (a játék mostani színei – ezeket írd be a promptba, ha a modell engedi hex kódot):
- háttér / fal sötét: `#0b0f1a`, `#1b2238`, `#2a3454`
- kék játékos: `#4cc3ff` · narancs játékos: `#ffa23a` · zöld csapat: `#5be28a` · rózsaszín: `#ff6cb5`
- veszély piros: `#ff4d5e` · kristály cián: `#8fe8ff` · arany (kulcs, gomb): `#ffd54a` · lila (nyomólap/ajtó): `#c56cff` · türkiz (2. lap): `#6cffd8`

**Méretek:** a játék cellája **40×40 px**. A generátorok 512–1024 px-es képet adnak – ez jó: generálás után én kicsinyítem a pontos méretre (nearest-neighbor, hogy pixeles maradjon). Kérj **négyzetes** képet, az objektum a kép közepén, körülötte legalább 10% üres háttér.

**Egységesség-trükk:** az első jól sikerült képet (pl. a kék figurát) használd **referenciaként** a többinél (Midjourney: `--sref` vagy image prompt; Stable Diffusion: IP-Adapter / ugyanaz a seed; GPT-image: „in the exact same style as the attached image"). Minden elemet ugyanazzal az előtaggal és ugyanazzal a referenciával generálj, egy ülésben.

**Eszközjavaslat:** pixel arthoz a legkönnyebb egységes eredmény: Retro Diffusion (kifejezetten pixel art), vagy Stable Diffusion + pixel-art LoRA; Midjourney `--style raw` + a fenti előtag; GPT-image jó a karakterekhez. Varrat nélküli textúrához: Midjourney `--tile`, SD „tiling” kapcsoló.

---

## 2. Karakterek (a legfontosabb – ezekkel kezdd)

A két figura és a hat arc. **Egy lapon, egy promptban** a legjobb, hogy egyformák legyenek.

| # | Elem | Méret (végső) | Állapotok | Prompt (az előtag után) |
|---|---|---|---|---|
| K1 | Kék figura | 32×32 | normál, pislog, halott (X szem), feszül (nagy szem) | `cute round glowing blue slime-ball character, big expressive anime eyes with highlights, tiny smile, soft rim light, color #4cc3ff with lighter core` |
| K2 | Narancs figura | 32×32 | ugyanaz | ugyanaz, `color #ffa23a` |
| K3 | Zöld figura | 32×32 | ugyanaz | ugyanaz, `color #5be28a` |
| K4 | Rózsaszín figura | 32×32 | ugyanaz | ugyanaz, `color #ff6cb5` |
| K5 | Arc-kiegészítők | 32×32, átlátszó | napszemüveg, dühös szemöldök, macskafül, korona, robot-antenna | `sprite sheet of 5 small accessories for a round character: black sunglasses, angry eyebrows, cat ears, small golden crown, robot antenna with red light – each on transparent background, same scale` |

**Tipp:** kérj egy „character sheet” képet: `character sheet, 4 views of the same character: idle, blinking, surprised wide eyes, knocked out with X eyes` – ebből én kivágom az állapotokat.

A figurák mozgás-animációját (nyúlás-lapulás, pislogás) nem kell generálni, az kódból megy.

---

## 3. Tileset (falak, padló)

| # | Elem | Méret | Prompt |
|---|---|---|---|
| T1 | Fal csempe (varrat nélküli) | 40×40 | `seamless tileable dark metal wall tile, navy blue #1b2238 with subtle lighter top edge #2a3454, faint circuit-like engraved lines, sci-fi arena, pixel art, tileable` |
| T2 | Fal felső él | 40×8 | `thin glowing blue edge strip for a pixel art wall, #4cc3ff dim glow, tileable horizontally` |
| T3 | Padló csempe A és B (sakktábla) | 40×40 | `seamless tileable dark floor panel, very dark navy #0e1322, faint grid seam, pixel art, almost flat, low contrast` + egy 5%-kal világosabb változat |
| T4 | Háttér (a falak mögötti űr) | 960×600 | `dark synthwave void with faint distant stars and a soft nebula glow in blue and orange, very low contrast, pixel art, no horizon, no objects` |

A falak sarkait és éleit én rakom össze a csempéből (9-slice), nem kell külön kérni.

---

## 4. Pályaelemek (a cella közepén, átlátszó háttérrel)

| # | Elem | Méret | Állapotok | Prompt |
|---|---|---|---|---|
| E1 | Kristály | 28×28 | 1 (forog kódból) | `glowing cyan crystal gem, faceted, #8fe8ff with white highlight, pixel art, floating` |
| E2 | Kristálykapu (G) | 40×40 | zárt / nyitott (áttetsző) | `golden energy gate tile with diamond emblem, #ffd54a frame on dark, pixel art` |
| E3 | Cél mező | 40×40 | inaktív (halvány) / aktív (ragyog) | `green glowing teleporter pad tile, #5be28a rounded square with inner ring, pixel art` |
| E4 | Nyomólap | 32×32 | fel / lenyomva | `round pressure plate, purple #c56cff ring with dark center, slightly raised, pixel art` – kérj egy türkiz `#6cffd8` és egy rózsaszín `#ff6cb5` változatot is |
| E5 | Lapos ajtó (X/Y/Z) | 40×40 | zárt / nyitott keret | `energy door tile, purple #c56cff force field with X pattern inside a dark frame, pixel art` + türkiz és rózsaszín változat |
| E6 | Színes sáv (b / o) | 40×40 | – | `horizontal glowing stripes force field tile, blue #4cc3ff, pixel art` + narancs változat |
| E7 | Kulcs | 28×28 | – | `small golden key, #ffd54a, pixel art, slight glow` |
| E8 | Lakatos ajtó (K) | 40×40 | zárt | `locked door tile, dark bronze #8a6a2e with golden padlock icon, pixel art` |
| E9 | Sárga gomb | 32×32 | ki / be (ragyog) | `round yellow arcade button, #ffd54a, on dark base, pixel art` |
| E10 | Óra-ajtó (D) | 40×40 | zárt / nyitott | `timed door tile, dark gold frame with clock icon, pixel art` |
| E11 | Törékeny padló | 40×40 | ép / repedezik / lyuk | `cracked fragile floor tile, dark purple-grey #4a3a4a with pink crack lines #ffb0c0, pixel art` + egy „fekete lyuk, törött szélekkel” változat |
| E12 | Tüske | 40×40 | – | `floor spike trap tile, three red-pink spikes #ff4d5e on dark base #2a1018, pixel art, menacing` |

---

## 5. Ellenségek, gépek

| # | Elem | Méret | Prompt |
|---|---|---|---|
| V1 | Őrjárat (vörös gömb) | 30×30 | `angry red glowing orb enemy, #ff4d5e, small dark eyes, slight motion blur tail, anime chibi, pixel art` |
| V2 | Lézer-hub | 28×28 | `small rotating laser turret hub, dark grey disc #2a3450 with red core #ff4d5e and dashed ring, top-down, pixel art` |
| V3 | Löveg | 34×34 | `small sci-fi turret, dark grey body #2a3450, rotating barrel with red tip, top-down, pixel art` (a cső irányát kódból forgatom – kérd úgy, hogy a cső **jobbra** mutasson) |
| V4 | Lövedék | 12×12 | `small red-pink energy bullet with white core, pixel art` |

A lézersugár, a kötél és a részecskék maradnak kódból (azok így szebbek és olcsóbbak).

---

## 6. Felület, címkép

| # | Elem | Méret | Prompt |
|---|---|---|---|
| U1 | Címkép (főmenü háttér, Discord) | 1920×1080 | `key art: two cute chibi orb characters, one blue #4cc3ff one orange #ffa23a, connected by a glowing energy tether, running through a dark neon arena with red laser beams and cyan crystals, synthwave colors, anime style, dramatic lighting, pixel art inspired but detailed, wide composition, empty space at the top for a title` |
| U2 | Logó | 1024×512, átlátszó | `game logo text "KÖTELÉK", bold rounded letters, blue-to-orange neon gradient, glowing outline, dark background, clean, no extra text` – az ékezetet gyakran elrontják; ha nem megy, a szöveg marad kódból, csak egy embléma kell (`emblem of a glowing energy tether loop`) |
| U3 | Ikonok a menübe | 64×64, átlátszó | `set of 4 flat neon icons: globe, key, gamepad, trophy, blue outline #4cc3ff, pixel art` |
| U4 | Favicon | 64×64 | `tiny icon: two connected glowing dots, blue and orange, dark background` |

---

## 7. Hang (ha már AI – külön kör)

- Zene, 3 track, hurokra: **menü** (`dreamy synthwave, slow, 90 bpm, arpeggios, warm pads, loopable, no vocals`), **játék** (`focused synthwave, 120 bpm, driving bass, light arpeggios, loopable, no vocals`), **verseny** (`energetic synthwave, 135 bpm, punchy drums, loopable, no vocals`). Suno/Udio – nézd meg a licencet nyilvános használathoz.
- Hangeffektek (ElevenLabs SFX vagy hasonló): kristály felvétel (`short bright crystal chime`), kötélszakadás (`electric snap zap`), halál (`soft retro game over thud`), pálya teljesítve (`short victory jingle, 8-bit synth`), gomb (`chunky sci-fi button press`), ajtó (`sliding energy door`).

---

## 8. Átadás – így kérem a fájlokat

- **PNG, átlátszó háttér** (a tileset kivételével), az objektum középen, körülötte üres sáv.
- Fájlnév a táblázat jele szerint: `K1_kek.png`, `E4_nyomolap_fel.png`, `E4_nyomolap_le.png`, `T1_fal.png` …
- Eredeti generált méretben jöhet (512–1024 px), a végső méretre én kicsinyítem és paletta-tisztítom.
- Ha egy elem több állapotú, mehet külön képként vagy egy lapon – ha egy lapon, egy sorban, egyenlő távolsággal.

**Sorrend, amiben a legtöbbet ér:** 1) figurák (K1–K5) → 2) fal és padló (T1–T4) → 3) veszélyek (V1–V4, E12) → 4) többi pályaelem → 5) címkép és logó. Már az első kettő után látványosan más lesz a játék.
