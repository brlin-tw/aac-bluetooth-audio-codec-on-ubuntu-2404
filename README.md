# How to allow the usage of the AAC audio codec for bluetooth audio devices on Ubuntu 24.04

Explains why the AAC audio codec support for bluetooth audio devices isn't available on a Ubuntu 24.04 system, and how to fix it on your own.

\#pipewire \#ubuntu \#bluetooth \#a2dp \#fdk-aac

![Screenshot of the audio device profile selection interface of the bluetooth audio device after applying the workaround](docs-assets/after.png "Screenshot of the audio device profile selection interface of the bluetooth audio device after applying the workaround")

<https://gitlab.com/brlin/aac-bluetooth-audio-codec-on-ubuntu-2404>  
[![The GitLab CI pipeline status badge of the project's `main` branch](https://gitlab.com/brlin/aac-bluetooth-audio-codec-on-ubuntu-2404/badges/main/pipeline.svg?ignore_skipped=true "Click here to check out the comprehensive status of the GitLab CI pipelines")](https://gitlab.com/brlin/aac-bluetooth-audio-codec-on-ubuntu-2404/-/pipelines) [![GitHub Actions workflow status badge](https://github.com/brlin-tw/aac-bluetooth-audio-codec-on-ubuntu-2404/actions/workflows/check-potential-problems.yml/badge.svg "GitHub Actions workflow status")](https://github.com/brlin-tw/aac-bluetooth-audio-codec-on-ubuntu-2404/actions/workflows/check-potential-problems.yml) [![pre-commit enabled badge](https://img.shields.io/badge/pre--commit-enabled-brightgreen?logo=pre-commit&logoColor=white "This project uses pre-commit to check potential problems")](https://pre-commit.com/) [![REUSE Specification compliance badge](https://api.reuse.software/badge/gitlab.com/brlin/aac-bluetooth-audio-codec-on-ubuntu-2404 "This project complies to the REUSE specification to decrease software licensing costs")](https://api.reuse.software/info/gitlab.com/brlin/aac-bluetooth-audio-codec-on-ubuntu-2404)

[TOC]

## Licensing

This write-up is licensed under [the 4.0 international version (or any of its more recent versions you prefer) of the Creative Commons Attribution-SharedAlike license](https://creativecommons.org/licenses/by-sa/4.0/deed.en).

If you have any needs that require rights that are not granted by this license, contact <buo.ren.lin+legal@gmail.com> for inquiry.
