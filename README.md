# Waybackurls: Unlocking Historical Recon for Bug Bounty Hunting  

In the ever-evolving field of bug bounty hunting, reconnaissance (or recon) is a critical phase. A successful recon strategy can make the difference between finding a high-severity vulnerability or coming up empty-handed. Among the plethora of tools available, **Waybackurls** stands out as one of the most effective tools for historical URL discovery.  

This repository provides a comprehensive guide to understanding, installing, and using Waybackurls effectively, along with an automated script for integrating it into your recon workflow.  

---

## Table of Contents  
- [What Is Waybackurls?](#what-is-waybackurls)  
- [Why Is Waybackurls Essential for Bug Bounty Hunters?](#why-is-waybackurls-essential-for-bug-bounty-hunters)  
- [Installing Waybackurls](#installing-waybackurls)  

---

## What Is Waybackurls?  

**Waybackurls** is a powerful open-source tool designed to fetch URLs archived in the **Wayback Machine** and other sources. Written in Go, it is fast, efficient, and commonly used by security researchers to uncover hidden endpoints, old directories, and forgotten assets that may still be live or reveal valuable insights.  

### Features of Waybackurls  
- Discover forgotten subdomains and pages.  
- Find endpoints that expose sensitive data.  
- Identify deprecated APIs and hidden parameters.  
- Explore attack surfaces beyond what’s visible today.  

---

## Why Is Waybackurls Essential for Bug Bounty Hunters?  

1. **Historical Insight**  
   The **Wayback Machine** archives snapshots of websites over time, offering opportunities to explore old assets that may still host vulnerabilities.  

2. **Enhanced Reconnaissance**  
   Complements modern scanning tools by providing access to archived data.  

3. **Increased Scope**  
   Reveals additional endpoints, parameters, and features that may no longer appear on the live website but remain accessible.  

---

## Installing Waybackurls  

### Prerequisites  
- **Go** installed on your system ([Download Go](https://golang.org)).  

### Installation Steps  
```bash
# Install waybackurls using Go
$ go install github.com/tomnomnom/waybackurls@latest

# Add Go binaries to your PATH
$ export PATH=$PATH:$(go env GOPATH)/bin
```

To verify the installation:
```
$ waybackurls -h
```
How to Use Waybackurls Effectively

Basic Usage

Fetch archived URLs for a specific domain:

```
$ echo "target.com" | waybackurls
```
Combine with Other Tools
Filter URLs with grep:

```
$ echo "target.com" | waybackurls | grep "php"
```
Remove duplicates:

```
$ echo "target.com" | waybackurls | sort -u
```
Test live URLs with httpx:

```
$ echo "target.com" | waybackurls | httpx -silent
```
Find hidden parameters:

```
$ echo "example.com" | waybackurls | grep "?"
```
Discover hidden directories:

```
$ echo "example.com" | waybackurls | grep "/admin"
```
