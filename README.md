# HF packet test audio

`hf-packet-test-10-packets.wav` is the test signal used to check 300 baud HF receive on the Pocket Pico (branch `hf-receive`, pull request pfiliberti/pico_tnc#10).

- 10 AX.25 UI packets, `N7WDZ>TEST:Pico HF receive test packet 1 of 10` through `10 of 10`
- 300 baud AFSK, mark 1600 Hz, space 1800 Hz (the usual HF packet tones)
- Made with Direwolf `gen_packets -B 300`, 48 kHz, 16 bit mono, 2 s of silence between packets, 46 s long

## How it was used

1. Play the file into a transmitter's audio input (here a Yaesu FT-710 in DATA-L on 14.105 MHz, 10 W into a dummy load). Keep the audio low enough that ALC barely moves; too much drive distorts the tones.
2. Listen with the receiver and Pocket Pico (here an IC-718 on 14.105 MHz LSB), with `MONITOR ON` at the TNC prompt.
3. Count the packets the Pico prints. The firmware on `hf-receive` decoded 10 of 10, even with the two radios about 70 Hz apart.

Direwolf's `atest -B 300 hf-packet-test-10-packets.wav` decodes all 10 straight from the file, which is a quick check that the file is good.

73, Gene N7WDZ
