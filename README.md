# EasyFeng

**Repeaters made easy for Baofeng radios.** EasyFeng programs repeater and airband channels into a Baofeng handheld from a web page, without fiddly menus or installing anything. It has big buttons and plain words, and it backs up the radio before every change.

**Try it:** https://sparks72.github.io/easyfeng/
You can press "Try with a pretend radio" to see everything work without a radio or cable.

## Supported radios

| Radio | Repeaters | Airband (AM, listen only) | 1750 Hz tone-burst setting |
|---|---|---|---|
| Baofeng K63 / K6 | ✓ | ✓ | ✓ |
| Baofeng UV-5R Mini | ✓ | ✓ | ✓ |
| Baofeng UV-17Pro | ✓ | — | — |

Older radios such as the UV-5R and BF-888 use a different cable protocol and are **not** supported.

## What you need

- **A PC with Chrome or Edge.** The page talks to the radio through the browser's Web Serial feature.
- **A Baofeng USB programming cable with the two-pin Kenwood-type plug.** A cable with an FTDI or CH340 chip works best. Cheap cables with copied Prolific chips often don't work on Windows. If the cable shows in Device Manager as "Unknown USB Device (Port Reset Failed)", the cable is faulty.

## How to use it

1. **Choose your radio.** Switch the radio off and plug in the cable. Fold the rubber cover right back and push the plug firmly home. Switch the radio on and turn the volume up a little.
2. **Read radio.** Pick the cable's COM port the first time. A backup of the whole radio is saved to your Downloads folder automatically.
3. **Pick repeaters.** Use the 2 m, 70 cm and airband tabs. They're sorted by distance from your locator. Edit any card, or add your own.
4. **Choose channels.** "Use the first free channels" avoids overwriting anything, and channels that would be replaced are shown in yellow.
5. **Write.** Only the changed channels are written. They're read back afterwards to check them.
6. **Restore** puts any backup back if needed.

Backups are standard CHIRP `.img` files, so CHIRP can open them too.

## Repeater list

The built-in list covers northern Germany around Fehmarn, plus OZ3REP on Lolland in Denmark. It comes from the repeatermap.de list (December 2022), RepeaterBook, afu-nord.de and the DL5SAF list (2019). Each card says how current its entry is. Repeaters change, so check before relying on one.

Not every repeater uses a CTCSS tone. Where a card shows one, the channel sends it. Otherwise the repeater opens on carrier or with the 1750 Hz burst.

## Testing and status

**Experimental.** Before each release, EasyFeng is checked against CHIRP's own drivers:

- Channel records match CHIRP byte for byte for every supported model, including airband channels.
- On 200 test blocks, the data scrambling used by the UV-5R Mini and UV-17Pro is identical to CHIRP's.
- The full read, write and restore sequence runs against a simulated radio for each model. CHIRP then reads the result back correctly.

It has **not** yet been tested on every real radio. The first time you use it, press **Read radio** and keep that backup before writing anything. Reports from real radios are welcome.

## Credits and licence

The cable protocol and memory layouts come from [CHIRP](https://chirpmyradio.com) (driver `baofeng_uv17Pro.py`), which is licensed under the GNU GPL version 2 or later. EasyFeng is offered under the same licence; see `LICENSE`.

Written by Paul Harrison, DJ0CU / G4ADF.

**EasyFeng is an independent, free tool. It is not made or endorsed by Baofeng.** Use it at your own risk. You are responsible for transmitting only on frequencies your licence allows.
