# How to allow the usage of the AAC audio codec for bluetooth audio devices on Ubuntu 24.04

Explains why the AAC audio codec support for bluetooth audio devices isn't available on a Ubuntu 24.04 system, and how to fix it on your own.

\#pipewire \#ubuntu \#bluetooth \#a2dp \#fdk-aac

![Screenshot of the audio device profile selection interface of the bluetooth audio device after applying the workaround](docs-assets/after.png "Screenshot of the audio device profile selection interface of the bluetooth audio device after applying the workaround")

<https://gitlab.com/brlin/aac-bluetooth-audio-codec-on-ubuntu-2404>  
[![The GitLab CI pipeline status badge of the project's `main` branch](https://gitlab.com/brlin/aac-bluetooth-audio-codec-on-ubuntu-2404/badges/main/pipeline.svg?ignore_skipped=true "Click here to check out the comprehensive status of the GitLab CI pipelines")](https://gitlab.com/brlin/aac-bluetooth-audio-codec-on-ubuntu-2404/-/pipelines) [![GitHub Actions workflow status badge](https://github.com/brlin-tw/aac-bluetooth-audio-codec-on-ubuntu-2404/actions/workflows/check-potential-problems.yml/badge.svg "GitHub Actions workflow status")](https://github.com/brlin-tw/aac-bluetooth-audio-codec-on-ubuntu-2404/actions/workflows/check-potential-problems.yml) [![pre-commit enabled badge](https://img.shields.io/badge/pre--commit-enabled-brightgreen?logo=pre-commit&logoColor=white "This project uses pre-commit to check potential problems")](https://pre-commit.com/) [![REUSE Specification compliance badge](https://api.reuse.software/badge/gitlab.com/brlin/aac-bluetooth-audio-codec-on-ubuntu-2404 "This project complies to the REUSE specification to decrease software licensing costs")](https://api.reuse.software/info/gitlab.com/brlin/aac-bluetooth-audio-codec-on-ubuntu-2404)

[TOC]

## The problem

The AAC audio codec support for bluetooth audio devices isn't available under Ubuntu 24.04 by default:

![Screenshot of the audio device profile selection interface of a Bose NC 700 bluetooth headphone, notice that only SBC codecs A2DP profiles are available for selection.](https://hackmd.io/_uploads/SkgNS4i30.png "Screenshot of the audio device profile selection interface of a Bose NC 700 bluetooth headphone, notice that only SBC codecs A2DP profiles are available for selection.")

This is due to the fact that the FDK-AAC package that provides the support [has a patent-related clause in their BSD-like custom license](https://fedoraproject.org/wiki/Licensing/FDK-AAC), which makes it incompatible with the licenses of the consumer packages(e.g. PulseAudio/Pipewire) and thus can't be legally distributed when linked(it will considered to be violating license terms at either ends).

The FDK-AAC package distributed in Ubuntu is in fact [a stripped-down fork](https://gitlab.freedesktop.org/wtaymans/fdk-aac-stripped) that removes features which the related patents aren't expired yet, which, [as far as Fedora concerned](https://lists.fedoraproject.org/archives/list/legal@lists.fedoraproject.org/thread/OVW25JRWOKOLVMW3XGUX7E4OXFUR2RCG/), is considered free from the license incompatibility problems.  However [the package hasn't moved to the main component of the Ubuntu software archive component yet](https://bugs.launchpad.net/ubuntu/+source/fdk-aac-free/+bug/1977614) and as a result, it cannot be linked by the consumer packages(as they are also required to be included in the Ubuntu installation media, which requires all software to be from the `main` and `restricted` software archive components).

## The solution

The following actions may help the bug be resolved:

* Vote and subscribe to the following Ubuntu bugs:
    + [Bug #1991936 “No AAC codec for Pipewire on Ubuntu Kinetic” : Bugs : pipewire package : Ubuntu](https://bugs.launchpad.net/ubuntu/+source/pipewire/+bug/1991936)
    + [Bug #1977614 “\[MIR\] fdk-aac-free” : Bugs : fdk-aac-free package : Ubuntu](https://bugs.launchpad.net/ubuntu/+source/fdk-aac-free/+bug/1977614)
* Subscribe to the following Debian bug:
    + [#1021370 - pipewire: build with bluez5-codec-aac=enabled - Debian Bug report logs](https://bugs.debian.org/cgi-bin/bugreport.cgi?bug=1021370)
    + [#981285 - Please move fdk-aac to main - Debian Bug report logs](https://bugs.debian.org/cgi-bin/bugreport.cgi?bug=981285)

## References

The following external materials are referenced during the writing of this howto:

* [Bug #1977614 “\[MIR\] fdk-aac-free” : Bugs : fdk-aac-free package : Ubuntu](https://bugs.launchpad.net/ubuntu/+source/fdk-aac-free/+bug/1977614)  
  A Ubuntu bug report to migrate the fdk-aac-free package(currently in the `universe` component) to the `main` Ubuntu software archive component.
* [#981285 - Please move fdk-aac to main - Debian Bug report logs](https://bugs.debian.org/cgi-bin/bugreport.cgi?bug=981285)  
  A Debian bug port to move the fdk-aac package to the `main` Debian software archive component, it contains discussion regarding the compatibility of the FDK-AAC license with the GPL licenses used in consumer packages.
* [Licensing/FDK-AAC - Fedora Project Wiki](https://fedoraproject.org/wiki/Licensing/FDK-AAC)  
  Explains the characteristics of the FDK-AAC license.
* [Regarding GPL compatibility of fdk-aac - legal - Fedora mailing-lists](https://lists.fedoraproject.org/archives/list/legal@lists.fedoraproject.org/thread/OVW25JRWOKOLVMW3XGUX7E4OXFUR2RCG/)  
  Explains whether GPL compatibility should be concerned in the Fedora's distribution of the fdk-aac package in the Fedora GNU+Linux distribution.
* [Enable PipeWire on Ubuntu 22.04](https://gist.github.com/the-spyke/2de98b22ff4f978ebf0650c90e82027e)  
  Similar problem but for Ubuntu 22.04.

## Licensing

This write-up is licensed under [the 4.0 international version (or any of its more recent versions you prefer) of the Creative Commons Attribution-SharedAlike license](https://creativecommons.org/licenses/by-sa/4.0/deed.en).

If you have any needs that require rights that are not granted by this license, contact <buo.ren.lin+legal@gmail.com> for inquiry.
