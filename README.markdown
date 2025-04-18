# Everything is in progress. Please check back later.

# FitX SDK

The FitX SDK is a next-generation toolkit for working with `.fitx` files, a fitness data format designed to improve upon Garmin’s FIT format. Forked from the Garmin FIT SDK, FitX introduces advanced compression, higher data frequencies, enhanced interoperability, and real-time streaming capabilities. We hope for a maximum of flexibility and customization without corporate control.

## Features

- **Smaller File Sizes**: Lossless compression (delta coding + heatshrink) reduces file sizes by \~50%, ideal for long activities like ultra-trails.
- **High-Frequency Data**: Supports up to 10Hz for metrics like heart rate and muscle oxygen.
- **Interoperability**: Exports to FIT, GPX, TCX, and includes metadata for modern tools (e.g., machine learning).
- **Real-Time Streaming**: Lightweight protocol for live tracking via ANT+/BLE.
- **FIT Compatibility**: Includes a converter for FIT-to-FitX and FitX-to-FIT.

## Installation

### Python

```bash
pip install fitx-sdk
```

### C/C++

Download the SDK and include `fitx.h` in your project:

```bash
git clone https://github.com/your-username/fitx-sdk.git
cd fitx-sdk/cpp
make
```

## Usage

### Reading a FitX File (Python)

```python
from fitx_sdk import FitxDecoder

decoder = FitxDecoder("activity.fitx")
messages = decoder.read()
print(messages["record"])  # Access GPS, heart rate, etc.
```

### Converting FIT to FitX

```python
from fitx_sdk import convert_fit_to_fitx

convert_fit_to_fitx("input.fit", "output.fitx")
```

### Real-Time Streaming (C++)

```cpp
#include "fitx_streamer.h"

FitxStreamer streamer;
FitxRecordMessage msg = { /* timestamp, heart_rate, gps */ };
streamer.send_packet(msg);
```

## Building FitX Files

- **File Structure**: Binary messages with a 16-byte header, compressed with delta coding + heatshrink.
- **Tools**: Use the FitX encoder to create `.fitx` files from raw data.

## Contributing

We welcome contributions! See CONTRIBUTING.md for details.

## License

This project is licensed under the same terms as the Garmin FIT SDK (see LICENSE). Modifications and FitX extensions are open-source under MIT.

## Credits

- Forked from the Garmin FIT SDK.
- Compression inspired by heatshrink.

## Contact

For issues or suggestions, open a GitHub issue or contact \[your-email@example.com\].
