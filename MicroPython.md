# MicroPython Roadmap: From Zero to Sensors, Embedded Devices and Reliable IoT — Windows, Linux and macOS

*60 sessions | 10 weeks | approximately 190 hours | MicroPython, RP2/Pico W or ESP32, Thonny, mpremote and safe 3.3 V circuits*

Learn **MicroPython from zero**, including Python syntax, board firmware, GPIO, sensors, timers, file storage, networking and reliable embedded behavior. Finish with a documented real-device project. Unlike desktop Python, MicroPython runs **on a microcontroller** with restricted RAM, storage and libraries. You write code on a Windows, Linux or macOS computer and send it to a supported board. The course uses an **RP2040/RP2350 Pico W/Pico 2 W** as the clearest example; supported **ESP32 boards** are a complete alternative when you adapt their pins, firmware and peripherals from the correct board docs.

**Platform scope:** Windows, Linux and macOS are the **host computer operating systems** for Thonny, Python and `mpremote`. The code runs on MicroPython firmware **on the board**; this is not a Windows/macOS app. A non-wireless Pico or ESP board can do the offline sessions, but choose a Wi-Fi capable board for the networking sessions or use the clearly marked **serial-only alternative**. Peripheral availability varies by port and firmware: do not assume identical pins, `network`, PWM duty methods, TLS support or I2C bus numbering across Pico and ESP32.

## How one session works

A **day** means one study session, not necessarily one calendar day. Sessions 1–5 of each week take about **3 hours**; the sixth is a **4-hour project and review**. Work in order within a language. If alternating languages, finish the current session before switching.

| Minutes | Block | What you do |
|---:|---|---|
| 10 | Recall | Rebuild a small piece of the previous session from memory. |
| 40 | Learn | Read the specific topic, type examples, explain them in your own words. |
| 90 | Build | Write today's program independently, with at least three test inputs. |
| 30 | Break it | Introduce one deliberate bug, reproduce it, diagnose it, then fix it. |
| 10 | Save | Run the available checks, commit the work, and write 3 journal lines: learned / confused / next step. |

**Completion rule:** do not check off a session merely for reading about a topic. The program must run on the intended platform, expected edge cases must behave correctly, tests or hardware checks must pass where relevant, and you must be able to explain your solution without copying. If stuck for 20 minutes, record what you expected and what happened, minimize the example, and consult the official docs. Hardware sessions can replace the 30-minute bug exercise with a safe fault-injection test; **never deliberately short a circuit or exceed a board's electrical limits**.

## Start here — hardware and software (about 60–120 minutes)

**Recommended minimum kit:** one supported MicroPython board (**Raspberry Pi Pico W / Pico 2 W**, or an **ESP32 development board** with documented MicroPython support), a known-good **USB data cable**, breadboard, a few male-to-male jumper wires, **LED + suitable series resistor** (for example 220–1,000 Ω at 3.3 V for a typical LED), pushbutton, **3.3 V compatible** analog sensor or potentiometer, and an I2C sensor (optional until week 4). A USB cable that provides charging only will not transfer code. **A multimeter is recommended** before connecting unfamiliar peripherals.

**Electrical safety (mandatory):**

- Use **3.3 V logic** and verify the **specific board and sensor datasheets**. Do **not** connect 5 V directly to a GPIO pin that is not 5 V tolerant. Do not connect mains voltage, high-current loads, heaters or motors directly to microcontroller pins; suitable driver modules and separate power design are outside the beginner labs.
- Disconnect USB/power **before rewiring**. Check pin number vs **physical pin position**; GP-number labels (Pico), GPIO-number labels (ESP32), `Pin(...)` IDs and board silkscreens may differ. Always connect a resistor in series with a standard external LED.
- Connect a shared ground for low-voltage external circuits where required. Avoid powering a board simultaneously from multiple unverified sources.

**Install host tools:**

1. Install **Thonny** from <https://thonny.org/> on Windows/Linux/macOS and select the appropriate **MicroPython interpreter and serial port** in its settings.
2. Download **stable firmware for your exact board** from <https://micropython.org/download/>. **Pico/Pico W/Pico 2 W:** choose the matching RP2 `.uf2`, hold **BOOTSEL** while connecting and copy the firmware to the appearing device, following official board instructions. **ESP32:** select the exact ESP32 variant and follow its matching `esptool` flashing procedure; do **not** flash a Pico UF2 to an ESP32.
3. Optional but recommended: install desktop Python and `mpremote` using `python -m pip install mpremote` (or `pipx install mpremote`), based on the official <https://docs.micropython.org/en/latest/reference/mpremote.html>. Run `mpremote connect list`, then `mpremote` to open an on-device REPL. On Windows, port is usually `COM...`; on Linux, `/dev/ttyACM...` or `/dev/ttyUSB...`; on macOS, `/dev/cu.usb...` or similar. Access permissions and drivers differ.
4. Open a MicroPython REPL and run `import sys; print(sys.implementation)`; use `import os; print(os.uname())` when supported. **Write down your board model, firmware release, USB port, voltage and available peripherals** in `board-notes.md`.
5. Create `micropython-roadmap/` with a `host_tests/`, `device/`, `wiring/`, `journal.md`, and `week-01/`…`week-10/`. Run `git init`. Never commit Wi-Fi passwords in any `secrets.py` or config file.

**Host-specific troubleshooting:** Windows may require a USB serial driver for some ESP32 boards; Linux may need your user added to the appropriate serial-device group; macOS may ask permission for a USB accessory. Thonny and `mpremote` usually cannot hold the **same serial port at the same time**: disconnect one before opening the other.

**Board-specific starter wiring:** Prefer a **built-in LED** first; use `Pin("LED")` only when your RP2 board firmware supports that alias. On ESP32, check its board's LED GPIO; many boards lack a user LED. For external LED use a verified GPIO, series resistor and ground. Where network tasks are marked **Wi-Fi**, the alternative is to exchange JSON over the USB serial connection.

## First program — MicroPython REPL

On a firmware version supporting the RP2 `LED` alias (common on Pico/Pico W), type:

```python
from machine import Pin
import time

led = Pin("LED", Pin.OUT)
for _ in range(5):
    led.toggle()
    time.sleep_ms(250)
led.off()
```

**Not every ESP32 firmware uses `"LED"`.** On ESP32 use a documented GPIO from the board schematic instead, and remember some on-board LEDs are active-low. If no LED is available, begin with `print("Hello from MicroPython")` and use `Pin(...)` only after reading the board pinout.

**Device command workflow:** `mpremote run blink.py` runs a *host* file on the board without persisting it. To persist a startup script, `mpremote fs cp main.py :main.py` copies to the board; an incorrect `main.py` can auto-run on each boot, so learn **Ctrl+C interrupt / safe recovery** before saving it. Files written to the board are not automatically kept in your host Git repo.

---

## Part 1 — Python fundamentals and safe GPIO

### Week 1 — MicroPython setup, values and control flow (sessions 1–6)

| Day | Learn | Build | Done when |
|---:|---|---|---|
| **1** | REPL, firmware vs host interpreter, `.py`, `print`, comments and serial connection. | Print board info and a 3-line greeting. | Reconnect after reset and explain where code runs. |
| **2** | Variables, integers, floats, Booleans, strings and `type`. | Temperature and voltage unit converter in REPL. | Correct on zero, negative and decimal inputs. |
| **3** | `if`, `elif`, `else`, comparisons and Boolean logic. | Threshold-based simulated temperature alarm. | Exact boundary produces expected state. |
| **4** | `for`, `while`, `range`, `break`, time delays and loops. | Countdowns, FizzBuzz and timed serial messages. | Explain why a tight infinite loop can block controls. |
| **5** | Functions, return values, scope and `None`. | `is_even`, `clamp` and `to_celsius` helpers. | Reused functions tested with three cases each. |
| **6** | **Project and review:** safe first device project. | Board info menu plus blink or print-only fallback. | Board recovers after reset; no accidental endless boot loop. |

**Break it this week:** Feed a nonnumber into a conversion; create a controlled zero-division error and explain the traceback.

### Week 2 — Data types, files and GPIO (sessions 7–12)

| Day | Learn | Build | Done when |
|---:|---|---|---|
| **7** | Lists, tuples, dictionaries, `len`, indexes and bounds. | Store and summarize 20 sensor readings. | Empty and long arrays handled. |
| **8** | Strings, format, split, bytes vs `str`. | Parse `temp=24.7` serial input. | Invalid commands rejected with clear messages. |
| **9** | `machine.Pin`, inputs vs outputs, external LED circuit. | Blink a safe LED and read a pushbutton. | Wiring diagram, GPIO ID and resistor documented. |
| **10** | Pull-ups/pull-downs, active-low inputs and debouncing. | Button-triggered counter with software debounce. | Single press yields one event consistently. |
| **11** | `try`/`except`, module imports and smaller code files. | Extract hardware-independent parser module. | Parser runs on host Python with tests or checks. |
| **12** | **Project and review:** interactive gadget. | Press button to change LED flash speed or log event. | No phantom presses; correct action after restart. |

**Break it this week:** Swap software polarity in a sandbox example to diagnose active-low behavior; do not rewire while powered.

### Week 3 — ADC, PWM and time-based logic (sessions 13–18)

| Day | Learn | Build | Done when |
|---:|---|---|---|
| **13** | Analog vs digital signals, `ADC`, raw readings and voltage range. | Read a 3.3 V compatible sensor or potentiometer. | Values stay within documented pin range. |
| **14** | Scaling and calibration, noise, moving average. | Smooth ADC samples and show calibrated values. | Three known approximate positions behave correctly. |
| **15** | PWM concept, duty cycle and board-supported methods. | Fade external LED using documented PWM API. | No over-current, dim/bright steps visible. |
| **16** | Nonblocking timers with `ticks_ms`/`ticks_diff`, avoiding overflow mistakes. | Blink LED while polling a button. | Button responds without waiting for long sleep. |
| **17** | Finite state machines: idle, measuring, alert and recover. | Implement a threshold alarm with hysteresis. | No rapid state chatter near threshold. |
| **18** | **Checkpoint 0:** input-to-output device. | Button + analog threshold + LED/Buzzer substitute on supported hardware. | Demonstrate 10 scenarios, record pinout and tag `micropython-p1`. |

**Break it this week:** Introduce a sensor value just above and below a threshold, then add hysteresis.

## Part 2 — Hardware interfaces, files and reliability

### Week 4 — I2C, SPI and sensor drivers (sessions 19–24)

| Day | Learn | Build | Done when |
|---:|---|---|---|
| **19** | I2C basics: SDA/SCL, addresses, pull-ups and bus scanning. | Scan a supported I2C bus for a sensor. | Address matches verified device documentation. |
| **20** | Read documented registers or use a board-compatible driver. | Collect temperature/pressure/light readings. | Units and raw vs converted values explained. |
| **21** | SPI basics: clock/data/chip-select and bus speed. | Inspect an SPI display/storage module, or emulate message formatting if none. | Explain SPI vs I2C and label pins. |
| **22** | Data validation, sensor disconnection and recovery. | Show clear error when sensor is unplugged *after powering down*. | Program recovers on reconnection. |
| **23** | Modular drivers, mocks and on-device integration checks. | Make sensor interface `read()` swappable with fake. | Host logic tests pass without `machine` module. |
| **24** | **Project and review:** mini sensor station. | Sensor reading + alarm + serial log. | Bad-read handling, timing and circuit diagram documented. |

### Week 5 — Storage, memory and resilience (sessions 25–30)

| Day | Learn | Build | Done when |
|---:|---|---|---|
| **25** | Microcontroller flash storage, `boot.py` vs `main.py`, filesystem. | Persist simple configuration as JSON. | Restart preserves settings; corrupted file handled. |
| **26** | Low-memory Python: allocation, `gc.collect`, bytes/bytearray and limits. | Measure free memory before/after repeated sampling. | No unbounded data collection during 10-minute run. |
| **27** | Ring buffers, sampling rates, data loss and batching. | Fixed-size rolling average of measurements. | Buffer stays bounded and timestamps monotonic within session. |
| **28** | Power failures, atomic-ish write patterns, wear considerations. | Save settings only when changed and recover from incomplete file. | No per-sample flash writes. |
| **29** | Watchdogs and resets concept (`machine.WDT` if supported); startup failure recovery. | Build a safe watchdog experiment or simulate reset. | Project cannot become unrecoverably stuck at boot. |
| **30** | **Project and review:** offline logger. | Store rolling sensor readings with limited file writes. | Endures controlled software reboot and low-memory conditions. |

**Break it this week:** Write malformed JSON and simulate loss of one record; practice backup-and-recovery rather than corrupting critical firmware.

### Week 6 — Debugging and host/device testing (sessions 31–36)

| Day | Learn | Build | Done when |
|---:|---|---|---|
| **31** | USB serial tools, traceback reading, `mpremote` run/copy/REPL. | Execute local test script without auto-saving. | Tell difference between running and deploying. |
| **32** | Host pure-logic tests using CPython `unittest` or `pytest`. | Test parser, averaging and state machine with fakes. | At least 20 host tests pass. |
| **33** | On-device smoke tests, hardware invariants and fixtures. | Write checklist for each GPIO/sensor behavior. | Every hardware check has expected output. |
| **34** | Timing and latency: `ticks_us`, sample rates and jitter. | Measure 100 sampling intervals. | Report min/max and missed targets. |
| **35** | Exception logging, failure injection and recovery strategy. | Simulate sensor timeout and malformed config. | Board keeps reporting status without uncontrolled reboot loop. |
| **36** | **Checkpoint 1:** stable device firmware. | Sensor logger with bounds, recoverable errors and host tests. | 15-minute demo, no runaway memory, tag `micropython-p2`. |

## Part 3 — Connected and concurrent embedded systems

### Week 7 — Networking or serial protocol alternative (sessions 37–42)

| Day | Learn | Build | Done when |
|---:|---|---|---|
| **37** | Wi-Fi board checks, `network.WLAN` and connection states; serial-only fallback. | Connect to private test Wi-Fi or open local serial link. | Timeouts and reconnect logic demonstrated. |
| **38** | IP, HTTP requests and sockets with available firmware modules. | Fetch JSON from a controlled endpoint or serial JSON message. | Invalid response or disconnect handled. |
| **39** | IoT message formats, timestamps and schema versioning. | Emit `{version, reading, status}`-style JSON payload. | Desktop script validates payload schema. |
| **40** | Connectivity retry/backoff and queueing offline data. | Buffer a bounded number of unsent readings. | Network drop never causes a tight retry loop. |
| **41** | TLS/certificate limitations and secret handling; no sensitive data to unsupported network endpoint. | Add config file outside Git and optional secure transport when supported. | No real credentials printed or committed. |
| **42** | **Project and review:** connected dashboard feed. | Send sensor readings to a host dashboard or over USB serial. | 5-minute interruption recovers without data corruption. |

**Break it this week:** Disable your own Wi-Fi AP or unplug the USB serial device (after stopping transfers) and verify bounded retry and recovery.

### Week 8 — Scheduling and embedded concurrency (sessions 43–48)

| Day | Learn | Build | Done when |
|---:|---|---|---|
| **43** | `asyncio` on MicroPython (formerly `uasyncio` in older releases); coroutines and event loop. | Blink LED and poll sensor concurrently. | Neither task blocks the other for seconds. |
| **44** | Cooperative cancellation, task lifetime and exceptions. | Start/stop monitoring task from a button/command. | Every task terminates cleanly. |
| **45** | Interrupts vs callbacks, shared variables and `micropython.schedule` concept. | Button edge as event flag, process work in main loop. | No allocation-heavy work inside interrupt handler. |
| **46** | Timers, sample scheduling and budget calculations. | Collect 1 Hz samples with jitter notes. | Busy work does not starve button input. |
| **47** | Energy budgets, sleep states, voltage/current measurement (optional). | Implement low-activity mode and wake-up plan. | Document measured or estimated duty cycle honestly. |
| **48** | **Project and review:** reactive sensor system. | Event-loop-based logger with alarm and optional network task. | Controlled restart, stable response and time-budget log. |

### Week 9 — Deployment, robustness and security (sessions 49–54)

| Day | Learn | Build | Done when |
|---:|---|---|---|
| **49** | Source vs deployed filesystem, packaging modules, file layout. | Make release copy commands and clean-device setup script. | Same version recreated from repository. |
| **50** | Firmware/port capability checks and configuration migration. | Detect board and missing peripherals gracefully. | Clear error rather than unhandled ImportError. |
| **51** | Network hygiene: trusted local endpoints, credentials, OTA update risk. | Threat-review your own demo device. | No hard-coded secrets or exposed unauthenticated control endpoint. |
| **52** | Reliability: soak tests, reboots, memory and connection monitoring. | Run 30-minute device soak test. | Memory trend and reset count recorded. |
| **53** | Documentation, wiring diagrams, parts list and troubleshooting. | Write illustrated pin table and recovery procedure. | Another person can recreate safe wiring. |
| **54** | **Checkpoint 2:** release candidate. | Board sensor monitor with logging, retries and at least 20 host tests. | 30-minute soak passed, README and `micropython-p3` tag. |

## Part 4 — Capstone and device handoff

### Week 10 — Capstone: reproducible real-device build (sessions 55–60)

| Day | Learn | Build | Done when |
|---:|---|---|---|
| **55** | Choose scope: environmental monitor, light sensor logger or desk alarm. | One-page acceptance plan with exact board and pin map. | Five measurable device behaviors defined. |
| **56** | Assemble and validate safe hardware. | Create pin table, measure supply and test each component alone. | No unknown voltage inputs or floating connections. |
| **57** | Implement application core with testable modules. | Sensor reads, alarm state, bounded buffer and validation. | Host tests pass and device reflects known values. |
| **58** | Add offline persistence and optional networking/serial output. | Export a schema-versioned record stream. | Disconnect/reconnect does not corrupt data. |
| **59** | Soak test, safe recovery and documentation. | Test failure injection, reboot, low-memory and recovery steps. | A second person can flash and run from README. |
| **60** | **Final review and device release:** handoff and demo. | Tag `micropython-v1`, record short demonstration, publish repo and wiring. | Physical board survives a 30-minute demo; behavior reproducible. |

---

## Checkpoints — do not move forward with gaps

| Gate | Session | Pass condition | If you miss it |
|---|---:|---|---|
| Checkpoint 0 | 18 | Safe input/output demo using a documented pinout, threshold and alarm state. | Repeat GPIO, ADC and timing exercises. |
| Checkpoint 1 | 36 | Stable sensor logger with host tests, documented memory usage and safe restart. | Redo parsing, storage and recovery. |
| Checkpoint 2 | 54 | Release candidate with 20+ host tests, sensor mock, wiring docs and 30-minute soak test. | Repair failures or use serial-only path where networking unsupported. |
| Capstone | 60 | Another person can flash exact firmware, wire safe circuit, run demo and recover boot faults. | Document and fix any unresolved hardware-dependent behavior. |

## Final capstone — a portable, board-aware sensor monitor

Create a **real embedded sensor monitor** that reads a 3.3 V compatible sensor, keeps a bounded rolling sample window, drives an LED alarm using thresholds and hysteresis, stores configuration safely, and sends timestamped or monotonic-time tagged readings **over local Wi-Fi or a USB serial JSON feed**. Implement a simple desktop script to capture and display messages, or build a small local dashboard. Include a board-specific wiring diagram and a clearly documented alternative where a peripheral does not exist.

**Minimum acceptance test:** use a supported stable firmware for the *exact* board; flash it; verify pinout; run host tests; run on-device sensor checks; disconnect the network/serial link safely and recover; reboot without losing configuration; complete a **30-minute soak test** and record dropped samples, min/max latency and memory observations. Publish `requirements` or installation steps for host tools, firmware version, `main.py` and deployment commands. A video alone is not sufficient evidence: include the runnable source and test log.

**Two valid routes:** **Wi-Fi route:** Pico W/Pico 2 W or compatible ESP32 with `network` support. **Offline route:** any compatible MicroPython board, with USB serial JSON and no reliance on Wi-Fi. Be explicit about the route used; **never fabricate hardware measurements**.

**Optional next tracks:** low-power battery design (with proper protection), native `rp2` PIO where supported, ESP32 deep sleep, BLE when board/firmware support it, safe OTA design, or a custom C driver. These are outside the beginner capstone.

## Resources

| Resource | Use it for | Cost |
|---|---|---|
| [Official MicroPython downloads](https://micropython.org/download/) | Firmware selected by **exact board model** and stable release. | Free software |
| [MicroPython documentation](https://docs.micropython.org/en/latest/) | Language differences, `machine`, `network`, `asyncio`, examples. | Free |
| [RP2 quick reference](https://docs.micropython.org/en/latest/rp2/quickref.html) | Pico/Pico W pins and peripheral API. | Free |
| [ESP32 quick reference](https://docs.micropython.org/en/latest/esp32/quickref.html) | ESP32 differences, peripherals, pins and functionality. | Free |
| [mpremote docs](https://docs.micropython.org/en/latest/reference/mpremote.html) | Running, copying and debugging programs over serial. | Free |
| [Thonny](https://thonny.org/) | Beginner host editor and on-device REPL. | Free |
| [Raspberry Pi Pico documentation](https://www.raspberrypi.com/documentation/microcontrollers/pico-series.html) | Physical pinouts and electrical specifications. | Free |
| [ESP32 documentation](https://docs.espressif.com/projects/esp-idf/en/latest/esp32/) | Chip electrical capabilities and board-related notes; confirm your module variant. | Free |

**Hardware costs:** firmware and editor are free; boards, sensors, breadboards, multimeters, wires and other parts must be obtained separately. Verify current firmware and pin support before copying examples from tutorials using another board.

## What you can do next

You can flash firmware, talk to a board over USB, write and test MicroPython modules, read GPIO/sensors, manage timing and bounded memory, and ship a safe small embedded application. To progress professionally, study electrical engineering fundamentals (power, ground, input protection, pull-ups), C/C++ embedded systems, device datasheets, real-time design, hardware-in-the-loop testing and secure update strategies. Always keep circuit safety more important than code completion.

