# OpenDTU

[![OpenDTU Build](https://github.com/tbnobody/OpenDTU/actions/workflows/build.yml/badge.svg)](https://github.com/tbnobody/OpenDTU/actions/workflows/build.yml)
[![cpplint](https://github.com/tbnobody/OpenDTU/actions/workflows/cpplint.yml/badge.svg)](https://github.com/tbnobody/OpenDTU/actions/workflows/cpplint.yml)
[![Yarn Linting](https://github.com/tbnobody/OpenDTU/actions/workflows/yarnlint.yml/badge.svg)](https://github.com/tbnobody/OpenDTU/actions/workflows/yarnlint.yml)

## !! IMPORTANT UPGRADE NOTES !!

If you are upgrading from a version before 15.03.2023 you have to upgrade the partition table of the ESP32. Please follow the [this](docs/UpgradePartition.md) documentation!

## Background

This project was started from [this](https://www.mikrocontroller.net/topic/525778) discussion (Mikrocontroller.net).
It was the goal to replace the original Hoymiles DTU (Telemetry Gateway) with their cloud access. With a lot of reverse engineering the Hoymiles protocol was decrypted and analyzed.

## Documentation

The documentation can be found [here](https://tbnobody.github.io/OpenDTU-docs/).
Please feel free to support and create a PR in [this](https://github.com/tbnobody/OpenDTU-docs) repository to make the documentation even better.

## Breaking changes

Generated using: `git log --date=short --pretty=format:"* %h%x09%ad%x09%s" | grep BREAKING`

```code
* 1b637f08      2024-01-30      BREAKING CHANGE: Web API Endpoint /api/livedata/status and /api/prometheus/metrics
* e1564780      2024-01-30      BREAKING CHANGE: Web API Endpoint /api/livedata/status and /api/prometheus/metrics
* f0b5542c      2024-01-30      BREAKING CHANGE: Web API Endpoint /api/livedata/status and /api/prometheus/metrics
* c27ecc36      2024-01-29      BREAKING CHANGE: Web API Endpoint /api/livedata/status
* 71d1b3b       2023-11-07      BREAKING CHANGE: Home Assistant Auto Discovery to new naming scheme
* 04f62e0       2023-04-20      BREAKING CHANGE: Web API Endpoint /api/eventlog/status no nested serial object
* 59f43a8       2023-04-17      BREAKING CHANGE: Web API Endpoint /api/devinfo/status requires GET parameter inv=
* 318136d       2023-03-15      BREAKING CHANGE: Updated partition table: Make sure you have a configuration backup and completly reflash the device!
* 3b7aef6       2023-02-13      BREAKING CHANGE: Web API!
* d4c838a       2023-02-06      BREAKING CHANGE: Prometheus API!
* daf847e       2022-11-14      BREAKING CHANGE: Removed deprecated config parsing method
* 69b675b       2022-11-01      BREAKING CHANGE: Structure WebAPI /api/livedata/status changed
* 27ed4e3       2022-10-31      BREAKING: Change power factor from percent value to value between 0 and 1
```

## Currently supported Inverters

| Model                | Required RF Module | DC Inputs | MPP-Tracker | AC Phases |
| ---------------------| ------------------ | --------- | ----------- | --------- |
| Hoymiles HM-300-1T   | NRF24L01+          | 1         | 1           | 1         |
| Hoymiles HM-350-1T   | NRF24L01+          | 1         | 1           | 1         |
| Hoymiles HM-400-1T   | NRF24L01+          | 1         | 1           | 1         |
| Hoymiles HM-600-2T   | NRF24L01+          | 2         | 2           | 1         |
| Hoymiles HM-700-2T   | NRF24L01+          | 2         | 2           | 1         |
| Hoymiles HM-800-2T   | NRF24L01+          | 2         | 2           | 1         |
| Hoymiles HM-1000-4T  | NRF24L01+          | 4         | 2           | 1         |
| Hoymiles HM-1200-4T  | NRF24L01+          | 4         | 2           | 1         |
| Hoymiles HM-1500-4T  | NRF24L01+          | 4         | 2           | 1         |
| Hoymiles HMS-300-1T  | CMT2300A           | 1         | 1           | 1         |
| Hoymiles HMS-350-1T  | CMT2300A           | 1         | 1           | 1         |
| Hoymiles HMS-400-1T  | CMT2300A           | 1         | 1           | 1         |
| Hoymiles HMS-450-1T  | CMT2300A           | 1         | 1           | 1         |
| Hoymiles HMS-500-1T  | CMT2300A           | 1         | 1           | 1         |
| Hoymiles HMS-600-2T  | CMT2300A           | 2         | 2           | 1         |
| Hoymiles HMS-700-2T  | CMT2300A           | 2         | 2           | 1         |
| Hoymiles HMS-800-2T  | CMT2300A           | 2         | 2           | 1         |
| Hoymiles HMS-900-2T  | CMT2300A           | 2         | 2           | 1         |
| Hoymiles HMS-1000-2T | CMT2300A           | 2         | 2           | 1         |
| Hoymiles HMS-1600-4T | CMT2300A           | 4         | 4           | 1         |
| Hoymiles HMS-1800-4T | CMT2300A           | 4         | 4           | 1         |
| Hoymiles HMS-2000-4T | CMT2300A           | 4         | 4           | 1         |
| Hoymiles HMT-1600-4T | CMT2300A           | 4         | 2           | 3         |
| Hoymiles HMT-1800-4T | CMT2300A           | 4         | 2           | 3         |
| Hoymiles HMT-2000-4T | CMT2300A           | 4         | 2           | 3         |
| Hoymiles HMT-1800-6T | CMT2300A           | 6         | 3           | 3         |
| Hoymiles HMT-2250-6T | CMT2300A           | 6         | 3           | 3         |
| Solenso SOL-H350     | NRF24L01+          | 1         | 1           | 1         |
| Solenso SOL-H400     | NRF24L01+          | 1         | 1           | 1         |
| Solenso SOL-H800     | NRF24L01+          | 2         | 2           | 1         |
| TSUN TSOL-M350       | NRF24L01+          | 1         | 1           | 1         |
| TSUN TSOL-M800       | NRF24L01+          | 2         | 2           | 1         |
| TSUN TSOL-M1600      | NRF24L01+          | 4         | 2           | 1         |
| E-Star HERF-800      | NRF24L01+          | 2         | 2           | 1         |
| E-Star HERF-1600     | NRF24L01+          | 4         | 2           | 1         |
| E-Star HERF-1800     | NRF24L01+          | 4         | 2           | 1         |




## Examples (illustrative)

Zero feed-in (in German: Nulleinspeisung)

![Schematic01 zero feed-in](https://github.com/helgeerbe/OpenDTU-OnBattery/assets/129660360/0a8ff327-a3b9-4ce1-85fa-5c28a90e2d2a)

With Battery and DC charging via (up to two) Victron MPPT and (optional) Victron SmartShunt<br>
_Note: Due to the limitation of most ESP32 boards, you can only use two out of three Victron units, i.e. two Victron MPPTs or one Victron MPPT and a Victron SmartShunt. You can not use two Victron MPPTs and a Victron SmartShunt at the same time._

![Schematic02 - Victon+Battery](https://private-user-images.githubusercontent.com/4600384/326197341-c79089ef-9559-43b5-8281-56ce1262d062.png?jwt=eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJpc3MiOiJnaXRodWIuY29tIiwiYXVkIjoicmF3LmdpdGh1YnVzZXJjb250ZW50LmNvbSIsImtleSI6ImtleTUiLCJleHAiOjE3MTQ0MDY5MzYsIm5iZiI6MTcxNDQwNjYzNiwicGF0aCI6Ii80NjAwMzg0LzMyNjE5NzM0MS1jNzkwODllZi05NTU5LTQzYjUtODI4MS01NmNlMTI2MmQwNjIucG5nP1gtQW16LUFsZ29yaXRobT1BV1M0LUhNQUMtU0hBMjU2JlgtQW16LUNyZWRlbnRpYWw9QUtJQVZDT0RZTFNBNTNQUUs0WkElMkYyMDI0MDQyOSUyRnVzLWVhc3QtMSUyRnMzJTJGYXdzNF9yZXF1ZXN0JlgtQW16LURhdGU9MjAyNDA0MjlUMTYwMzU2WiZYLUFtei1FeHBpcmVzPTMwMCZYLUFtei1TaWduYXR1cmU9YzMzMmM3NmJjNjM0MWVjMTIyYWM4YjViZDc2MDdiZjNiODY3MmQ1NzQwMjFiMGI1NzNjOTZiZTBhYzUzYmQzMyZYLUFtei1TaWduZWRIZWFkZXJzPWhvc3QmYWN0b3JfaWQ9MCZrZXlfaWQ9MCZyZXBvX2lkPTAifQ.FJovXIs-lWVrvnEfwun_csCwIAnr5qCZHN8Aohnw1z8)

With Pylontech Battery and DC charging via (up to two) Victron MPPT

![Schematic03 - Victron+Pylontech](https://github.com/helgeerbe/OpenDTU-OnBattery/assets/129660360/48123826-1988-42f9-a702-91db203729f4)

With Battery and AC charging via Huawei Rectifier

![Schematic04 HuaweiR4850+Pylontech](https://github.com/helgeerbe/OpenDTU-OnBattery/assets/129660360/32bfe0f0-b07b-400c-b95c-8f1606671cd3)
