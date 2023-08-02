---
title: "Operating System x86 in Rust"
date: 2022-08-07
# externalUrl: "https://github.com/fede-26/blog_os"
summary: "Small x86 kernel written in Rust and QEMU. The kernel can handle interrupts, and the video card. Several memory allocators have been implemented."
showReadingTime: true
# _build:
#   render: "false"
  # list: "local"
---

# Introduction

In the vast world of computer science and programming, there are few endeavors as challenging and rewarding as writing your own operating system. 
As a passionate developer, I embarked on a thrilling journey to create my very own kernel using Rust.
I chose to follow the tutorial at https://os.phil-opp.com and I developed "blog_os," a lightweight kernel designed for the x86 architecture. This article aims to take you through the exciting story of how blog_os came to life, highlighting the core features such as basic input/output, interrupt and exception handling, and various memory allocators.

# The Inspiration

The idea of writing my own operating system had always fascinated me. The prospect of working at such a low-level, understanding the intricate interactions between hardware and software, and creating a functional OS from scratch was an opportunity I couldn't resist. While browsing online, I stumbled upon the tutorial at https://os.phil-opp.com, which became the stepping stone of my project.

# Getting Started

The journey began by laying the groundwork for the kernel. The Rust programming language, with its emphasis on safety and zero-cost abstractions, was an ideal choice. Setting up the development environment, including the cross-compiler and bootloader, was crucial for targeting the x86 architecture.

# Memory-Mapped VGA for Input and Output

Early on, I encountered the challenge of communicating with the outside world through my kernel. The tutorial opted to use the memory-mapped VGA, a technique that allows direct access to the screen memory. By implementing a basic VGA text mode driver, I was able to achieve console output for the kernel, enabling me to print messages and interact with the user.

# Interrupt and Exception Handling

Next came the critical aspect of handling interrupts and exceptions. Interrupts are events triggered by external hardware (like keyboard input or timer) or software (system calls), requiring immediate attention from the kernel. Similarly, exceptions denote exceptional conditions like divide-by-zero or page faults. Implementing interrupt and exception handlers was essential for maintaining stability and preventing crashes.

Using a Rust's external crate for assembly support, I defined some Interrupt Service Routines (ISRs) and Exception Service Routines (ESRs), providing the kernel with the ability to respond appropriately to various interrupts and exceptions. This helped me regain control during critical events and handle them gracefully.

# Memory Allocation

Memory management is a core feature of any operating system. In blog_os, I explored different memory allocation strategies to make efficient use of available resources. Rust's ownership model and safe memory handling proved to be invaluable in this aspect.

# Challenges and Learnings

The journey was not without its challenges. Debugging low-level code can be particularly tricky, with little support for traditional tools. However, this process taught me invaluable lessons in debugging techniques, assembly-level analysis, and thorough testing.

Additionally, working with the x86 architecture meant dealing with its intricacies and peculiarities, making the learning curve steep yet exciting. I had to dive deep into processor manuals, understanding protected mode, segmentation, and paging to design a robust kernel.