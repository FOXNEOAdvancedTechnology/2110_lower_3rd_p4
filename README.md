# 2110_lower_3rd_P4
=====================

This P4 program allows the on-switch mixing of certain raster
rows (a.k.a. scan lines) from one SMPTE ST 2110-20 flow with
certain raster rows from another 2110-20 flow.  (It probably
also works with the very similar RFC 4175).  The resulting
combined flow has its destination IP address restamped.

A potential use for this would be the "hard switching" of a
lower third graphic.

Only the first Sample Row Data (SRD) header in a packet is
examined.  This technique would work best with 2110-20 systems
that only have data from a single raster row in a packet.

commands_2110_lower_3rd.txt: BMv2 CLI commands example to set
up a lower third
Rows 0-480 come from the flow with DST IP 239.0.0.1
Rows 481-719 come from the flow with DST IP 239.0.0.2
The resulting output flow is restamped with DST IP 239.0.0.3

2110_lower_3rd_screenshot.png: Wireshark screenshot showing
how the switch output flows change from source 10.10.10.11
at lines (aka rows) up to 480, then starting with line 481
the source comes from 10.10.10.12.

lower_3rd.jpg: Actual mixture of two live ST 2110-20 video
sources, split at line 520 in a 720p59.94 signal.

If you need a SMPTE ST 2110-20 Wireshark dissector, see:
https://github.com/NEOAdvancedTechnology/smpte2110-20-dissector

Note this P4 program has now been developed for a Tofino target.
