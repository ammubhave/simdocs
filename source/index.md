---
title: Simmons Docs

toc_footers:
  - <a href='mailto:simmons-tech@mit.edu'>Contact Simmons Tech</a>

search: true
---

# Introduction

Welcome to the Simmons Docs!

If you want to create a new page, checkout [Sample Docs](sample.html) for an example.

# Projects

## 7K Display
[simmons-tech-7k@mit.edu](mailto:simmons-tech-7k@mit.edu)

The paneled 144” display is shaped like the building and made up of twelve top-of-the-line Samsung LED displays, for a native 15.67 megapixels, far exceeding the highest 4K Aperture Cineon film standard. After downscaling for dots-per-inch consistency, the digital canvas it presents is 7440px by 1920px. It is powered by a single, custom-built (by residents) computer with two novelty graphics cards that leverage AMD’s Eyefinity technology to run the whole thing as one giant desktop. It is designed to be able to show anything, including images, video and interactive games across the entire surface.

## Public Website
[simmons-tech-website@mit.edu](mailto:simmons-tech-website@mit.edu)

The webite [simmons.mit.edu](http://simmons.mit.edu/) is the public face of simmons. It contains information for prospectives regarding CPW (i3 video, schedule, etc) as well as information about the dorm for the genral public. The site needs to be maintained with the ongoing activities of our dorm, as well as expanded to include informatino such as the Simmons Hall Constitution.

# Servers and Infrastructure
[simmons-tech-servers@mit.edu](mailto:simmons-tech-servers@mit.edu)

* **metal-gear**. This is our shiny 1U server, complete with 2 six-core 2.4Ghz processors, 40GB of RAM, 2 1TB hard drives, and space for 2 more. It runs a bunch of VMs using Xen. It's Debian Squeeze.
* **team-rocket**. This is the "Simmons Tech Athena Login Server". It's basically Linerva, but for Simmons. (That means it's Debian 6 as well)
* **maple-syrup**. This is the "Simmons Residents Athena Login Server". It's basically athena.dialup, but for Simmons. (That means it's Ubuntu 12.04)
* **waffle-house**. Aka simmons-dev, this is where projects that need web serving go for staging. It's currently running dormbase and the production dashboard. It runs Fedora 16
* **simmons-ipv6**. This provides IPv6 access to Simmons wired users. It runs Debian 6, and basically shouldn't need to be touched, it "just works".
* **simmons-sex**. The Simmons 7k Display machine. For some hilarious reason, Cosmos decided to name this thing simmons-sex. It runs Windows 7. 
