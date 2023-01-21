# Grabber
An OSINT tool for investigators to collect external assets. The tool will collect a list of users with first names, last names and job titles and output them to a CSV file. This data can then be used to perform password sprays and/or compile a list of emails for phishing. The list is designed to have a favor over collection, which means it will produce false positives instead of false negatives.

## How Does It Work
The tool generates Bing searches of LinkedIn using "Google Dorks" queries, attempting to locate results from LinkedIn. The tool allows you to send all requests via a proxy/proxies scraped from https://www.sslproxies.org/. Note: Requests are performed using HTTP for speed and consistency.

## Prerequisites

- Rust
- OpenSSL Dev library (for Linux libssl-dev)

### Rust

Install Rust:

```bash
curl --proto '=https' --tlsv1.2 -sSf https://sh.rustup.rs | sh
```

### OpenSSL Dev Library

For Linux:

```bash
sudo apt-get install libssl-dev
```

## Setup

Build the application on your local environment.

```bash
cargo build 
```

## Quick Start

Basic use:

```bash
./grabber -p <Company_Name>
```

This is the standard method as it performs scraping via proxy servers and as such reduces the chance of being IP banned during a scan.

## Usage
Usage of the tool follows the following format:

```bash
./grabber [-p -o <Output_File> -w <Word_List>] <Company_Name>
```

### Flags
`-p, --proxy`      Use this flag to scan via proxies. If set to true the scan WILL take much longer.

`-o, --output <Output>`        Name of the file to output to (CSV FORMAT).

`-w, --wordlist <WordList>`    Path to a wordlist file which can be used for the scan.