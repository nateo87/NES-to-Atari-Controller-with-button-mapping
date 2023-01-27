# NES-to-Atari-Controller-with-button-mapping
A way to make use of the start and select buttons when modding an NES controller to work with the Atari 9-pin standard.

When playing games on consoles/computers like the Atari 2600, Commodore 64, etc, I tend to eschew the joysticks of the era and opt instead for a gamepad. They're just a lot more comfortable to me and tend to be a lot nicer to left-handers like myself. Also, a lot of platforming games for these machines tend to use 'up' for jump, and that dog won't hunt, monsignor. For this purpose, I modded an NES controller to work with the Atari 9-pin standard, and had the A button wired to 'up' for jump and B for 'fire'.

But what if you want A to be used for fire instead, as is often in a lot of shooters designed for the NES? It feels weird to use the B button for that purpose. You could use a mechanical SPDT switch to change the mapping of the A button, but that requires drilling a hole in the case, and having a random switch sticking out of this otherwise cleanly designed controller would look, how you say, inelegant. But hey now - there's two perfectly good, otherwise unused buttons sitting right in the middle of the controller! Wouldn't it be nice if we could make use of those instead?

(Before I explain further - if you don't know the basics of how to mod an NES controller for use on the Atari standard and want to know what to expect, I can heartily recommend [this foolproof guide](https://raskulous.com/2020/02/convert-an-original-nes-controller-for-use-on-commodore-64-amiga-atari-and-many-others/) )

Most have the A button of the NES controller bridged over to the 'up' direction to act as a sort of jump button, but here instead, we'll be using a 7400 as an S-R latch which opens/closes one of two switching transistors. These transistors' collectors are each wired to a different input ('fire' and 'up'), and both emitters run out to the A button. Start and Select act as SET and RESET. To use Start and Select reliably as these toggles, it's also necessary to have them pulled high by way of a resistor (10k oughta do just fine). A decoupling capacitor for the 7400 also isn't a bad idea. 

Here's the schematic I did on KiCad to make a small PCB with SMD components in order to make the mod neat and tidy:
![schematic](https://github.com/nateo87/NES-to-Atari-Controller-with-button-mapping/blob/main/ButtonMappingSwapSchematic.png)

A 74HCT can be substituted for the LS variety without issue, and I don't believe the HC variety would cause issues either. And really, any old switching NPN transistor should work just fine. I use 2N2222s myself instead of 2N3904s just because I have so damn many of them. The whole circuit consumes very little current, and falls well under the recommened limit of 100mA on the Atari controller port.

Of course, using this tidy little PCB isn't strictly necessary; if you don't mind weaving a little spider's web of wires and hot glue, you can just tack the circuit to the back of the controller PCB using normal throughhole components! Mmmm, makeshift DIY...
