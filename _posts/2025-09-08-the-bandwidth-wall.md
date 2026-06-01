---
layout: post
title: "The Bandwidth Wall: Why Optical Interconnects Are Hardware's Next Big Bet"
date: 2025-09-08
---

Every decade or so, computing hits a wall. Not in the sense that progress stops — it doesn't — but in the sense that the bottleneck shifts. In the 1980s, the wall was raw compute: we needed faster transistors. In the 2000s, it was power density: chips were getting hot enough to fry eggs, and Dennard scaling was dying. Now, in the 2020s, the wall is bandwidth.

The problem is simple to state: we have more compute than we can feed. A modern AI accelerator can perform hundreds of teraops per second, but its memory bandwidth is measured in terabytes per second — a ratio that leaves the chip idle far more than anyone wants to admit. Move up a level, from chip to package to rack, and the mismatch compounds. Electrical interconnects — the copper wires and differential pairs that have served us since the beginning — are hitting fundamental physical limits.

## Why copper is running out of road

A high-speed electrical link faces three enemies: loss, power, and density. At 100 Gbps, a few inches of copper trace can attenuate a signal by 30 dB or more. Equalizers can compensate, but they burn power — and at the densities required for modern AI clusters, the power budget for I/O is not a rounding error. It is a first-class design constraint.

The deeper issue is that these problems are correlated. Going faster makes the loss worse, which demands more aggressive equalization, which costs more power, which demands more cooling, which limits the density you can achieve in a rack. You cannot optimize one variable without worsening the others.

This is the bandwidth wall in practical terms: not a hard limit, but a regime where every marginal gain in bandwidth requires disproportionate investment in power and engineering effort.

## What optical interconnects promise

Light doesn't have the same problems. An optical signal traveling through a fiber or a silicon waveguide experiences negligible frequency-dependent loss — the attenuation doesn't spike at 50 GHz the way it does in copper. This means that, in principle, you can run an optical link at very high speeds with much lower equalization overhead.

There are other advantages. Optical links can carry multiple wavelengths simultaneously — wavelength-division multiplexing, or WDM — letting you run parallel data streams on a single fiber without the crosstalk that plagues dense electrical routing. And because photons don't induce electromagnetic interference the way electrons do, you can pack links tightly without the signal integrity nightmares that come with high-density copper.

The pitch from optical interconnect advocates is essentially: same bandwidth, much less power, better scaling. On paper, it's a compelling argument.

## The hard part: silicon photonics

The obstacle is integration. Fiber optics have been used in telecommunications for decades, but those systems work over kilometers, tolerate significant component cost, and can be assembled by hand. A datacenter-scale optical interconnect needs to be cheap, manufacturable in volume, and — increasingly — integrated directly with the silicon logic it serves.

Silicon photonics is the attempt to solve this problem by building optical components on silicon wafers using CMOS-compatible processes. The idea is that if you can use the same tools and factories that make processors to make photonic components, you get all the cost and scale advantages of the semiconductor industry.

The progress has been real. Silicon ring resonators, Mach-Zehnder modulators, and germanium photodetectors can all be fabricated on-die. Companies like Intel, Ayar Labs, and Lightmatter are building systems that integrate photonic chiplets or co-packaged optics directly with compute dies.

But the challenges are equally real. Silicon is a bad light emitter — you need to bond III-V materials (like InP or GaAs) to get efficient lasers, and heterogeneous integration is expensive and difficult. Temperature sensitivity is another headache: silicon ring resonators drift in response to thermal changes that are unavoidable in a compute environment, demanding active control loops that add complexity and power consumption. And coupling light efficiently between a fiber, a waveguide, and a photodetector is a precision engineering problem that doesn't get easier as you scale.

## Where the interesting work is

The research agenda in this space is, in my view, focused on three things.

The first is the transceiver architecture: how do you design the analog front end — the drivers, amplifiers, and equalizers — when the channel is optical rather than electrical? The noise sources are different, the nonlinearities are different, and the bandwidth available is different. Getting this right requires rethinking approaches that were developed for copper.

The second is co-design: how do you optimize the photonic and electronic components jointly? A silicon photonic modulator and the CMOS driver that feeds it have tightly coupled performance tradeoffs. Designing them in isolation leaves performance on the table; designing them together requires tools and methodologies that are still being developed.

The third is the system-level question: where in the memory hierarchy do optical interconnects make sense? The answer almost certainly isn't "everywhere." Chip-to-chip within a package, package-to-package on a board, rack-to-rack in a datacenter — each scale has a different cost and engineering tradeoff. Understanding where optical links are the right answer, and where they're overkill, is a practically important question that isn't fully settled.

---

These are the problems I think about. Not all of them will be solved cleanly, and some of what looks like a bottleneck today will be routed around by a different architectural choice entirely. But the bandwidth wall is real, optical interconnects are one of the more credible paths through it, and the engineering is hard enough to be interesting.

That's usually a good sign.
