# HP 8018A checkout procedure

This procedure covers safety inspection, initial power-up, functional
checks, and performance screening for HP 8018A data generators. Use it for
initial evaluation, return to service, or checks following repair. Select
the applicable manual revision and option procedures for the instrument
being tested.

Work through the stages in order. Stop at a failed safety check,
investigate the cause, and repeat affected checks after repair. Record
measurements, observations, and untested functions as the checkout
proceeds. A completed functional checkout does not establish full
calibration compliance.

## Manual, applicability, and limitations

Reference manual:
[HP 8018A Data Generator Operating and Service Manual, 08018-90003, November 1980](8018A%20Data%20Generator%20Operating%20and%20Service%20Manual.pdf).

References below give printed page/section identifiers and **one-based PDF
page numbers** for the bundled scan. The scan splits some foldouts across
several pages; PDF page numbers can differ in other copies.

| Reference | Location in the bundled PDF | Use |
| --- | --- | --- |
| Title page | PDF 4 | Serial-number applicability |
| Table 1-1, p. 1-2 | PDF 12 | Test equipment |
| Table 1-2, pp. 1-3 through 1-5 | PDF 13-15 | Specifications and operating modes |
| Section II, pp. 2-1 and 2-2; Figure 2-1 | PDF 16-17 | Line selection, fuse, protective ground, environment |
| Figure 3-1 and its control descriptions | PDF 18-20 | Front/rear controls and connectors |
| Section VIII, p. 8-1, paragraphs 8-4 through 8-13 | PDF 21 | Service precautions and after-service safety checks |
| Table 8-2, p. 8-2 | PDF 22 | Troubleshooting map |
| Service Block 1, p. 8-5 | PDF 25 | Initial fault isolation and cycle-input trap |
| Service Block 3, pp. 8-27 and 8-28 | PDF 51-52 | Internal, external, and manual clock; cycle inputs |
| Service Block 4 | PDF 61-71 | Formatting, word/data/mixed modes, cycling |
| Service Block 5, Table 8-5-1 | PDF 87-91 | Memory organization and serialization |
| Service Block 6, pp. 8-63 and 8-64 | PDF 107-108 | Data/sync outputs and pause-bit setting |
| Service Block 8, p. 8-73; Service Sheet 14 | PDF 124-126 | Power supply theory, measurement order, schematic |
| Service Sheet 15 | PDF 127-129 | Fan circuit |

**The bundled scan is incomplete.** After the Figure 3-1 control
descriptions it jumps directly to Section VIII. It lacks the detailed
Section III operating instructions, Section IV performance-test procedures,
Sections V-VII (adjustments, parts, backdating), and the listed option
appendices. The contents pages name those sections, but do not supply their
procedures. The checks below are a bench checkout derived from the
available specifications, control descriptions, and service information;
they are not a reproduction of HP's missing operator checks or a full
calibration.

The title page applies directly to serial **1826 G 00706 and higher**,
subject to applicable Manual Changes supplements. Earlier instruments
require Section VII backdating. Record the actual serial and board
revisions before using component locations or considering adjustments; the
needed supplements/backdating are absent here.

Obtain the missing operating, performance-test, adjustment, and backdating
material before performing checks that depend on it. Options 001 and 002
also require the applicable option instructions, published separately as
manual 08018-90002.

## 1. Prepare the bench and record the instrument

| Item | Record |
| --- | --- |
| Serial number; asset identifier | |
| Installed options; rear connectors | |
| Visible modifications or previous repairs | |
| Line selector positions; fuse markings | |
| Power cord condition | |
| Technician; date; ambient temperature | |
| Scope/probes; DMM; counter; pulse source | |
| Terminations/attenuators and their ratings | |
| Internal A3S1, A3S2, A7S1 positions, if inspected | |

Required measurement capabilities:

- Grounded bench outlet, sound three-conductor power cord, accessible power
  disconnect, and AC current/power monitor. An adjustable/current-limited
  AC source is optional service equipment, not a substitute for the safety
  checks.
- DMM for continuity and DC measurements. Electrical-safety test equipment
  and a qualified operator for the cabinet/line isolation check, especially
  after mains-related work. For supply checks, provide DC voltage and
  ripple measurement capabilities with documented accuracy and bandwidth.
- Oscilloscope with at least two channels and DC coupling; four channels
  simplify simultaneous data and sync observations. Use short 50-ohm BNC
  cables and correctly rated 50-ohm loads and attenuators. For transition
  measurements, the complete measurement chain must resolve 6 ns edges with
  sufficient bandwidth and known uncertainty. Refer to Table 1-1 for HP's
  original test-equipment requirements.
- Counter covering at least 50 MHz; pulse source covering the desired
  external-clock tests with controllable level, offset, and width. A logic
  analyzer is useful for long memory patterns, provided its inputs are
  protected and compatible with the measured voltage levels.
- For internal inspection/service: insulated tools and suitable meter/probe
  clips. Work with covers removed and power applied is for service-trained
  personnel (paragraph 8-5).

Use PASS, FAIL, NOT TESTED, or N/A for each result. An
equipment/documentation limitation is NOT TESTED, rather than a pass.
Photograph the original condition before cleaning, reseating, or changing
anything.

## 2. Unpowered inspection and safety gate

Disconnect the line cord and all signal cables. Before touching internal
circuitry, verify that stored charge has dissipated using appropriate
service practice; an unplugged instrument can retain hazardous voltages.

- [ ] Inspect the enclosure, handles/feet, front panel, BNCs, controls,
      line inlet, cord, and fuse holder for impact damage, loose parts,
      contamination, or improvised repairs.
- [ ] Allow a cold or damp instrument to reach dry room conditions before
      proceeding. Keep ventilation openings clear.
- [ ] Have a service-trained person inspect the interior before first
      power: damaged insulation, burned/discolored parts, arcing,
      corrosion, loose hardware, leaking/bulging capacitors, and cracked
      mains-suppression components. Identify any line-connected capacitor
      from the circuit before selecting a replacement; use the appropriate
      safety-rated replacement.
- [ ] Inspect the transformer, selector wiring, fuse wiring,
      protective-earth connections, power-supply boards, fan, and
      heatsinks. Check board seating, coax/ribbon connections, and the
      board clamp. Correct an observed defect before energizing; do not
      disturb every connection as a first step.
- [ ] With the cord attached to the instrument but unplugged from the
      outlet, measure protective-earth continuity from the plug earth pin
      to the chassis and exposed panels. Compensate for lead resistance and
      flex the cord while measuring. The manual calls for zero ohms: expect
      a stable reading indistinguishable from the shorted-lead baseline. An
      open, intermittent, or appreciable unexplained resistance is a stop
      condition (p. 2-1; paragraph 8-9).
- [ ] Verify cabinet/line isolation with the appropriate electrical-safety
      procedure and record its test conditions and acceptance criterion.
      Paragraph 8-10 requires an IEC/VDE check but gives no test voltage or
      numerical limit here. A DMM resistance reading alone does not
      establish insulation integrity; do not invent a megohmmeter/hipot
      setting from this procedure.
- [ ] Measure the available line voltage and set **both** rear
      voltage-selector switches to the matching nominal setting using
      Figure 2-1. Do this while disconnected from line power.
- [ ] Verify fuse value, type, physical size, and voltage rating against
      the instrument markings and applicable manual revision. Figure 2-1
      specifies **2 A for 100/120 V** and **1 A for 220/240 V**; the Figure
      3-1 description explicitly calls the 1 A fuse slow-blow. Do not infer
      an unspecified 2 A time characteristic from this scan, fit a larger
      fuse, or bypass a fuse.
- [ ] Record internal input configuration if accessible: A3S1 selects
      clock-input impedance, A3S2 selects cycle-input impedance, and A7S1
      selects the pause/end-bit state. Change internal switches only with
      line power removed, then restore covers.
- [ ] Reinstall protective covers and confirm the cord/ground/fuse checks
      still pass after any work.

**Gate:** proceed only when there is no unresolved safety defect. After any
repair, perform the complete after-service checks in paragraphs 8-6 through
8-13, including ground, isolation, fuse, covers, and internal connections.

## 3. First power and supply health

Keep all external equipment and loads disconnected initially. Protective
earth must remain connected. If an autotransformer is used, observe the
manual's grounded-common-terminal warning (p. 2-1); it provides no
isolation. The manual does not prescribe a capacitor-reforming or prolonged
low-voltage startup procedure.

The installation text specifies nominal 100/120/220/240 V, +5%/-10%, 48-66
Hz. Table 1-2 instead gives 48-440 Hz and 230 VA maximum, versus 120 VA in
Section II. For this checkout use ordinary 50/60 Hz within the selected
voltage range, size bench power equipment for at least the larger 230 VA
figure, and record actual current/power. Neither conflicting figure is a
useful stand-alone fault threshold.

1. Set LINE off. Select INT CLOCK, AUTO cycle, WORD mode, N=01/M=16 (format
   thumbwheels **0116**), A PAR B, NRZ on A and B, the lowest
   variable-amplitude range, amplitude vernier minimum, and A source
   impedance 50 ohms. Disconnect HP-IB and card-reader accessories.
2. Apply the selected nominal line voltage with current/power monitoring.
   Observe the first 10-30 seconds, then the next two minutes. Check the
   line indicator, fan operation/air movement, unusual hum, odor, smoke,
   arcing, and abnormal heating. Fan movement may require a technician's
   observation; do not insert anything through the vents.
3. **Switch off immediately** for smoke, arcing, a blown fuse, stalled fan,
   rapid heating, or sustained abnormal current. Disconnect power and
   investigate. Do not repeatedly replace a fuse and retry. A failed line
   lamp alone does not prove the instrument is unpowered.
4. If stable, continue under observation and record input current/power at
   startup, 2 minutes, and 10 minutes. A short observation period
   establishes only initial stability.

Recommended technician check before extended operation: verify the main
supplies at the identified test points. Attach clips with power
disconnected, use chassis/board ground as shown in the schematic, and keep
clear of line circuitry. Do not adjust a trimmer to conceal a fault.

| Measurement order | Nominal rail | Cold DC | Warm DC | Ripple/measurement bandwidth | Result |
| --- | --- | --- | --- | --- | --- |
| 1 | +25 V | | | | |
| 2 | +5 V | | | | |
| 3 | -5.2 V | | | | |

Service Block 8 explicitly gives this order because the rails depend on
preceding references. Its opening paragraph prints **+2.5 V**, but the
remainder of the text and Service Sheet 14 identify **+25 V**. Use the
schematic and actual rail labels. The missing Section V prevents quoting HP
rail/ripple tolerances from this copy; record measured values and
investigate a missing, wrong-polarity, unstable, or materially off-nominal
rail before continuing. If internal measurements are unavailable, mark them
NOT TESTED.

## 4. Connect measuring equipment safely

Table 1-2 specifies external **50-ohm loads** for output measurements. DATA
A and its complement share the amplitude controls; DATA B and the sync
outputs do not share A's variable-amplitude setting.

- Start with low amplitude. Before connecting a scope's internal 50-ohm
  input, check its maximum DC voltage, pulse voltage, and power ratings.
  Use an external load/attenuator and a high-impedance scope input when
  needed. Never combine an external 50-ohm feedthrough with an enabled
  internal 50-ohm termination.
- The variable A outputs can be much larger than ordinary logic inputs
  tolerate. A 7.5 V steady level across 50 ohms dissipates **1.125 W**; 15
  V across 50 ohms dissipates **4.5 W**. Rate loads and attenuators for the
  worst actual voltage and duty cycle, with margin. HP's equipment table
  calls for a 20 dB attenuator rated above 4.5 W.
- Open-circuit voltages from a 50-ohm source approximately double. Do not
  compare a high-impedance measurement directly with a 50-ohm-loaded
  specification.
- Use one known termination per measured path and record any attenuation
  factor. Check cables/loads before diagnosing overshoot or a low output
  level.
- Leave DUTs, logic analyzers, and frequency-counter inputs disconnected
  until the signal levels have been measured and their input ratings
  checked. Never connect two active outputs together.

## 5. Basic clock, memory, and outputs

Use the settings from Stage 3 and set the internal bit rate to
approximately **1 kbit/s**, measured at CLOCK. Press LOCAL/RESET if needed
to restore local control. LOAD/FETCH can briefly interrupt generation;
assess steady operation after the operation completes. Memory contents at
power-up are unspecified for this checkout.

### 5.1 Establish output activity

- [ ] Connect CLOCK to a suitably terminated scope input. Confirm a
      repetitive waveform and smooth frequency change with the bit-rate
      vernier.
- [ ] Select channel A and CHANNEL CLEAR. Confirm DATA A low and
      complementary DATA A high in NRZ; use protected inputs on both
      connectors. Select CHANNEL SET and confirm the states reverse.
- [ ] Select channel B and repeat CLEAR/SET on DATA B. Confirm that
      changing A memory does not overwrite B, and vice versa.
- [ ] Record low/high levels and waveforms. If CLOCK/sync signals exist but
      data does not respond, continue diagnosis using the symptom table
      below rather than adjusting the oscillator.

### 5.2 LOAD, FETCH, and a recognizable pattern

Maintain WORD mode, N=01, M=16, A PAR B; select row 1-16 and WORD ADDRESS
**01**.

1. Select A. Set the buffer LEDs to **1010101010101010** and press LOAD
   WORD.
2. Change several buffer switches without loading, then press FETCH WORD.
   Confirm the stored pattern returns to the LEDs. Merely seeing the
   switches' current pattern is not a memory-readback test.
3. Observe DATA A and its complement while triggering on FIRST BIT. Confirm
   the 16-bit frame, bit order, and complementary NRZ states. At a 1 kbit/s
   clock, this alternating data pattern repeats at 500 Hz; CLOCK remains at
   1 kHz.
4. Select B and load **1100110011001100** at address 01. Fetch it and
   observe DATA B. Verify that A retains its original pattern.
5. Repeat with all-zero, all-one, walking-one, and walking-zero patterns.
   Exercise every data-programming button and LED. Change the buffer before
   each FETCH.
6. Set N=02/M=32 (**0232**). In each channel, load and fetch distinct
   first- and second-half patterns using ROW ADDRESS 1-16 and 17-32 at word
   addresses 01 and 02. Confirm both rows and word addresses remain
   distinct in the output.

The control descriptions explain loading two 16-bit halves; they do not
supply the missing detailed instructions for programming arbitrary words
longer than 32 bits. Keep this initial content test at 16/32 bits, and
defer any uncertain long-word loading sequence until those instructions are
available.

### 5.3 RZ/NRZ and synchronization

Use N=02/M=16 (**0216**), different known words at addresses 01/02, and a
measured 1 kbit/s clock.

| Check | Expected observation | Result |
| --- | --- | --- |
| A and B NRZ | Adjacent ones stay high across the bit boundary | |
| A RZ, B NRZ; then reverse | Ones on the selected RZ channel return to zero within each bit; the other channel retains its format | |
| CLOCK | One clock pulse per bit, approximately half a clock period wide | |
| WORD TRIGGER | First bit of each 16-bit word; repetition 62.5 Hz | |
| FIRST BIT | First bit of each 32-bit frame; repetition 31.25 Hz | |
| LAST BIT | Last bit of that frame; also 31.25 Hz | |
| A complement | Opposite data states in NRZ; record RZ behavior separately | |

Confirm timing with multi-channel captures or swap the same calibrated
measurement path between outputs. Trigger markers identify bit positions;
allow the specified output-to-clock skew when judging edges. See Table 1-2
and Service Block 6.

## 6. Lengths, memory capacity, and channel serialization

Start at 1-10 kbit/s so a complete frame can be acquired without ambiguity.
RESET to the start after changing a mode or length. Choose the bit rate
from measured CLOCK, not the printed range marking alone.

- [ ] In WORD mode, change N and M separately; verify `bits/frame = N * M`,
      `FIRST BIT rate = bit rate / (N * M)`, and
      `WORD TRIGGER rate = bit rate / M`. Try N/M = 1/3, 2/16, 3/17, and
      4/32. Also exercise the upper thumbwheel digits with legal
      combinations such as 1/99 and 99/3. Keep the total within the
      selected channel capacity.
- [ ] In DATA mode, all four format digits specify stream length. Check 3,
      16, 17, 99, 100, 1023, and 1024 bits in parallel-channel operation.
      Count clock intervals between frame markers, or measure
      `frame period * bit rate`. Confirm FIRST/LAST alignment at the
      boundaries, not just a plausible repetition frequency.
- [ ] Check memory-wide CLEAR and SET on both full 1024-bit channels, using
      NRZ. Verify independently that one channel's operation leaves the
      other unchanged.
- [ ] For address/content coverage, use WORD mode N=32/M=32 (**3232**) to
      fill each 1024-bit channel with distinct, address-dependent words.
      Load/fetch both halves of all 32 words, with different patterns on A
      and B; capture an entire output frame and compare it with the written
      list. Repeat with inverted patterns. This bench memory test is
      derived from the documented memory organization; it does not replace
      HP's Section IV performance-test procedure.
- [ ] Select A SER B / 1x2048, DATA mode length **2048**. First set A
      memory all zero and B all one in parallel mode, then serialize: DATA
      A should contain 1024 zeros followed by 1024 ones, with a 2048-bit
      frame. Repeat with the states reversed. Check the joins at bits
      1024/1025 and 2048/1.
- [ ] Serialize the address-dependent contents and compare all 2048 bits
      with the concatenated A/B pattern list. Restore A PAR B afterward and
      confirm independent outputs again.

Service Block 4 says DATA-mode loading uses 16-bit units; until the missing
operating instructions are obtained, program the known contents in the
tested WORD-mode arrangement above rather than guessing DATA-mode
addressing. If a particular mode transition changes the observed memory
mapping, record it and resolve the operating sequence before declaring a
RAM failure.

## 7. Cycling, manual clock, and external inputs

These are separate controls: the **MAN clock pushbutton** supplies
individual clock edges in EXT(-)/MAN clock mode; the **RESET/MAN toggle**
supplies a cycle command in BIT/WORD/FRAME cycle mode.

### 7.1 Manual cycling

Use INT CLOCK at about 1 kbit/s, known two-word contents, N=02/M=16, and a
scope capture long enough to include an entire burst.

- [ ] AUTO: frames repeat continuously.
- [ ] BIT: each RESET/MAN cycle command advances one bit; subsequent
      commands continue the pattern.
- [ ] WORD: each manual cycle command delivers one complete 16-bit word,
      then stops. The next command continues with the next word.
- [ ] FRAME: each manual cycle command delivers the complete 32-bit frame,
      then stops.
- [ ] RESET: the next generated bit starts the frame at bit 1.

Allow a burst to finish before issuing another command. Record the pause
state: A7S1 can select a zero/one between words/frames in NRZ, or an extra
end bit in RZ (Table 1-2; Service Block 6). Do not count that behavior as
an unexpected stored data bit.

**Known setup trap:** if A3S2 is in its TTL/high-impedance position, an
open CYCLE INPUT can read high and prevent selection of BIT/WORD/FRAME
(Service Block 1). Verify the recorded switch position and hold that input
at a valid low with a suitable termination/driver, or have a technician
select the 50-ohm position with power disconnected, before diagnosing cycle
logic.

### 7.2 Manual clock

- [ ] Select AUTO cycle and EXT(-)/MAN clock mode, remove the external
      clock source, and use the MAN clock pushbutton to step through a
      known pattern.
- [ ] Confirm one bit advances per press and there is no free-running
      progression between presses. Restore INT CLOCK afterward.

### 7.3 External clock and cycle input

Measure the source waveform **at the loaded instrument input** before
testing. Avoid generator-display errors caused by a 50-ohm/high-impedance
setting mismatch. The following starting waveforms exceed the manual's
minimum amplitudes without testing overload protection.

| Input/configuration | Starting waveform at the input | Manual limits relevant to the test |
| --- | --- | --- |
| EXT(+) CLOCK, A3S1 at 50 ohms | 0 to +2 V, 1 kHz, 50% duty | Positive-going crossing, nominal +0.5 V trigger, minimum 1.0 V pulse amplitude |
| EXT(-) CLOCK, A3S1 at 50 ohms | -2 to 0 V, 1 kHz, 50% duty | Positive-going crossing, nominal -1.2 V trigger, minimum 0.8 V pulse amplitude |
| CYCLE INPUT, A3S2 at 50 ohms | 0 to +2 V, initially isolated 100 us pulses | Positive-going crossing, nominal +0.5 V trigger, minimum 1.0 V amplitude and 10 ns pulse width |

- [ ] With AUTO selected, confirm that both external clock settings advance
      the data pattern at the applied clock rate. EXT(-) denotes the
      negative-level input range; the specified triggering slope is still
      positive.
- [ ] Increase external clock frequency in steps supported by the pulse
      source and scope. The 50-ohm path is specified through 50 MHz, or 40
      MHz in MIXED mode; the clock pulse-width minimum is 6 ns typical, and
      HP notes that width adjustment may be needed at 30-50 MHz.
- [ ] For the TTL clock-input configuration, verify logic levels and the
      documented 40 MHz maximum separately. EXT(-) requires A3S1 in the
      50-ohm position (Service Block 3).
- [ ] Return to INT CLOCK and apply separated CYCLE INPUT pulses in BIT,
      WORD, and FRAME modes. BIT input is also a gate: begin with a high
      time shorter than one bit period, then test a sustained high gate.
      For WORD/FRAME choose a high time shorter than the selected burst and
      leave enough low time for completion before the next pulse.
- [ ] Hold CYCLE INPUT high, then return it low. BIT stops bit progression;
      WORD/FRAME finish the current word/frame before stopping. Confirm
      correct continuation on the next command.

Inputs are protected to +/-7 V; the manual's 0-16 V condition is allowed
only with current limited to 20 mA. These are protection limits, not
checkout drive targets. Do not deliberately test the protection circuits.
For TTL cycle input the minimum pulse width is 15 ns, and the
source-impedance condition is below 4 kilohms. Mark high-speed or threshold
tests NOT TESTED if suitable sources are unavailable.

## 8. PRBS and MIXED modes

PRBS and MIXED generation are Channel A functions. Select A PAR B for
clarity, use protected 50-ohm measurement paths, and begin at a measured
100 kbit/s.

- [ ] Select PRBS, set the PRBS exponent using the WORD ADDRESS thumbwheels
      per Figure 3-1, and observe DATA A and rear PRBS TRIG. Confirm
      repeatable patterns, rather than merely a noisy-looking waveform.

| n | Expected PRBS length, 2^n - 1 | Expected PRBS TRIG period at 100 kbit/s | Result |
| --- | --- | --- | --- |
| 9 | 511 bits | 5.11 ms | |
| 10 | 1023 bits | 10.23 ms | |
| 15 | 32767 bits | 327.67 ms | |
| 20 | 1048575 bits | 10.48575 s | |

- [ ] With adequate acquisition memory, verify a full sequence length and
      that it repeats after the expected number of clocks. A visual
      activity check alone does not verify the PRBS polynomial or every
      bit.
- [ ] Select MIXED by pressing WORD MODE and PRBS together. Use N=02/M=16
      and recognizable programmed words with n=9. Confirm that a PRBS
      segment is inserted after the odd-numbered programmed word and that
      the programmed words remain recognizable.
- [ ] Confirm the frame repeats and document the word/PRBS boundaries. Do
      not use the pure-PRBS rear trigger behavior as a MIXED-mode
      acceptance criterion: Table 1-2 excludes that output's identifying
      function in MIXED mode.
- [ ] Repeat at higher rates only after the low-rate behavior is
      understood. **MIXED is limited to 40 MHz.** Record any uncertain
      boundary/timing issue for comparison with the missing
      operating/performance procedures.

## 9. Output levels, bit-rate coverage, and waveform quality

Perform these checks after initial stability and basic functions pass.
Record cold and warm readings before considering adjustment. Recheck the
load/attenuator ratings whenever amplitude or source impedance changes.

### 9.1 DC and amplitude

- [ ] With A source impedance 50 ohms and a 50-ohm load, exercise all three
      variable-amplitude ranges and the vernier on DATA A and its
      complement. Check CLEAR/SET levels and a repetitive pattern. The
      specified overall amplitude span is **1.25-7.5 V**; the variable-mode
      low level is **0 V +/-10% of amplitude**.
- [ ] Record the vernier endpoints in each range, dropouts,
      discontinuities, and differences between normal/complementary A
      outputs.
- [ ] Select the high source-impedance position and check with the same
      documented load arrangement. Table 1-2 gives a nominal **1 kilohm
      source**, a **2.5-15 V** amplitude span, and a **40 MHz** maximum. Do
      not substitute an open-circuit measurement for the table's loaded
      specification.
- [ ] Select ECL with source impedance 50 ohms and a 50-ohm load. Record
      both levels and amplitude on A and its complement before connecting
      ECL equipment. ECL levels are internally adjustable: the table gives
      a low-level adjustment range of **-1.7 to +0.8 V** and an amplitude
      adjustment range of **0.45-1.05 V**. Those ranges are not a nominal
      ECL calibration target or tolerance; do not adjust them without the
      applicable procedure and required receiver levels.
- [ ] On DATA B and CLOCK, verify amplitude **at least 2.4 V** and low
      level **0 V +/-200 mV**. On FIRST BIT, LAST BIT, WORD TRIGGER, and
      PRBS TRIG, verify amplitude **at least 1.2 V** and low level **0 V
      +/-200 mV**, in their applicable modes. All are 50-ohm-loaded values.

### 9.2 Frequency and pulse shape

- [ ] Check all five bit-rate ranges and smooth vernier operation. Record
      overlapping coverage near 50 Hz, 500 Hz, 5 kHz, 50 kHz, 500 kHz, 5
      MHz, and 50 MHz as reachable. These are bench coverage points, not
      calibrated dial-accuracy requirements.
- [ ] At low, medium, and maximum appropriate rate, inspect CLOCK and data
      with isolated ones and alternating bits. Look for missing/double
      bits, amplitude loss, excessive ringing, and malformed RZ pulses.
- [ ] Compare low-rate and maximum-rate amplitudes using the same load:
      Table 1-2 limits reduction to **10%** for variable A, DATA B, and
      CLOCK; **15%** for ECL A. Use 40 MHz for high-source-impedance A or
      MIXED mode, rather than demanding 50 MHz there.
- [ ] Measure transitions with a sufficiently fast, properly terminated
      scope/attenuator chain. Limits in Table 1-2: **6 ns** for
      50-ohm-source A, B, CLOCK, and FIRST/LAST/WORD sync; **8 ns** for
      high-source-impedance A. Do not assign a transition limit to PRBS
      TRIG where the table leaves it blank.
- [ ] Measure perturbation relative to pulse amplitude: **10%** for
      variable A; **15%** for ECL A, DATA B, CLOCK, and FIRST/LAST/WORD
      sync. Save the traces and measurement definitions; the detailed HP
      overshoot/ringing setup is missing.
- [ ] Check data and FIRST/LAST/WORD sync timing relative to CLOCK against
      the table's **+/-3 ns** relation, accounting for cable/probe skew.
      Confirm RZ/sync pulse widths are approximately half a clock period;
      the absent Section IV procedure prevents claiming a full pulse-width
      calibration.
- [ ] If suitable timing instrumentation is available, record period jitter
      and the measurement method. Table 1-2 states **0.2% + 50 ps**; the
      missing Section IV setup leaves its exact evaluation conditions
      unavailable. Treat the result as a screening observation until the HP
      method is recovered.

The oscilloscope, probes, cables, and attenuators contribute to the
measured transition time. Record the measurement-chain bandwidth and
uncertainty. Mark an inconclusive specification check NOT TESTED rather
than failing the generator solely on an edge measurement limited by the
measurement system.

## 10. Options, warm operation, and closeout

- [ ] If Option 001 HP-IB is fitted, first complete local checkout with its
      cable removed. Record the option/address. After obtaining manual
      08018-90002 or the missing appendix, test remote programming of known
      patterns/lengths, remote start/stop, and return to local; compare the
      physical output with the requested data. Do not invent command syntax
      or require modern SCPI identity queries.
- [ ] If Option 002 card reader is present, defer its functional connection
      until its correct supply pinout and procedure are available. The rear
      connector is described as a +5 V card-reader supply, but that is
      insufficient to establish its pinout. Option 002 requires Option 001.
      Absent options are N/A.
- [ ] Run the covered instrument under observation for **30-60 minutes**
      with a representative pattern and appropriately rated loads. This
      duration is a bench observation interval, not an HP-specified warm-up
      time. Check fan operation and repeat clock, amplitude, LOAD/FETCH,
      and high-rate checks after warming; record drift and intermittent
      controls.
- [ ] Switch off, unplug, and perform a final inspection after charge has
      dissipated. Investigate any new odor, discoloration, or heat damage.
      After service, repeat paragraphs 8-6 through 8-13.
- [ ] Leave A at minimum variable amplitude, identify any remaining
      limitations on a tag, and disconnect signal and option cables. Record
      the final selector/fuse configuration.

| Test/result record | Settings; load; expected result | Measured result/evidence | PASS / FAIL / NOT TESTED / N/A |
| --- | --- | --- | --- |
| Safety/earth/isolation/fuse | | | |
| Startup current/power/fan | | | |
| Supplies, cold/warm/ripple | | | |
| A/complement/B levels | | | |
| LOAD/FETCH, rows, addresses | | | |
| Full memory and serialization | | | |
| Word/data lengths and sync | | | |
| RZ/NRZ and cycle modes | | | |
| Manual/external clocks and cycle input | | | |
| PRBS/MIXED | | | |
| Rate coverage, edges, skew, jitter | | | |
| Options and warm soak | | | |

Final disposition: **unsafe / repair required / functional with listed
limitations / functional checkout passed**. List every untested item.
Reserve **meets all HP specifications** for completion of the applicable
Section IV performance tests with suitable equipment, serial-specific
documentation, and recorded results.

## Fault-isolation guide

Use this after recording a reproducible failure. Check settings, input
termination, cables, and loads first; remove power before reseating boards
or changing internal switches. A fault association is a starting point, not
proof of a failed assembly.

| Symptom | First checks and manual destination |
| --- | --- |
| Fuse opens, no rails, or widespread instability | Stop; verify line selection/fuse and inspect mains/rectifier/supply area. Service Block 8; Sheets 14-15. Do not trim a bad supply into apparent operation. |
| No fan or abnormal heating | Stop extended operation; inspect fan and A21 circuit, Sheet 15. |
| No CLOCK or sync | Confirm INT/AUTO and no active LOAD/FETCH; check supplies, A3 rate generation, then A4 formatting and A7 sync. Blocks 1, 3, 4, 6. |
| CLOCK works, frame timing ignores thumbwheels | Check legal N/M/length and local control; A11 thumbwheels, A9 routing, A4 counters. Block 4. |
| Sync correct, LOAD/FETCH wrong | Confirm selected channel/row/address and local control; A2 control ASM, A13/A14 register/LED path, A6/A12 memory. Blocks 1, 2, 5, 7. |
| A output bad but B and sync good | Check A amplitude, source impedance, format, and load; A8 output amplifier. Block 6. |
| One channel or a repeating set of bit positions fails | Compare readback with output and record exact bit indices; A6/A12 organization in Table 8-5-1. First four bits use flip-flops, later bits use interleaved RAM. Block 5. |
| BIT/WORD/FRAME cannot be selected | Check open TTL-configured CYCLE INPUT / A3S2 before replacing logic. Block 1, p. 8-5. |
| Failure only at high rates | Verify waveform/termination and measurement bandwidth first, then supplies, A3 timing, A4/A7 formatting/sync, A6/A12 memory, A8 amplifier. |

The service manual includes invasive board-removal/jumper troubleshooting
methods. They are repair procedures for a qualified technician after fault
isolation, not steps in this initial checkout. Obtain the missing
adjustment/backdating material before attempting calibration changes.
