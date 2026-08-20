<p align="center"><img src="https://raw.githubusercontent.com/go-desktop/brand/main/social/go-desktop.png" alt="go-desktop" width="720"></p>

# go-desktop

**A map of one pure-Go ecosystem — 287 organisations, 564 public code repositories,
no C anywhere.**

This organisation holds no library of its own. It is the front door: an index of
every organisation in the ecosystem, grouped by what the code does, so that a
capability can be found without knowing which organisation happens to own it.

Every library here is written in Go and compiled with `CGO_ENABLED=0`. That is not
a stylistic preference — it is what makes one binary cross-compile to six
architectures, run inside a browser as WebAssembly, and boot on bare metal without
a libc. Where a good pure-Go library already exists it is used rather than
rewritten; where the only option was a C library behind cgo, the capability was
rebuilt.

The ecosystem is split into **one organisation per domain and one repository per
capability**, so a program that needs an ext4 reader takes an ext4 reader and not a
storage framework.

🌐 **[go-desktop.github.io](https://go-desktop.github.io/)** — the same map, browsable.

## What every repository is held to

| | |
| --- | --- |
| **`CGO_ENABLED=0`** | No cgo, and no shelling out to a command-line tool in place of a library. A dependency is a Go module or it is written. |
| **Six 64-bit targets** | amd64, arm64, riscv64, loong64, ppc64le, s390x — native where runners exist, under qemu-user otherwise. s390x is big-endian, which keeps every on-disk and on-wire encoding honest. |
| **100% statement coverage** | A CI gate, error branches included. A skipped test is not a passing one: jobs fail when a toolchain is missing rather than turning green quietly. |
| **Measured, not asserted** | Performance claims come with a benchmark against the reference implementation; format claims come with a byte comparison against it. Decoders are fuzzed. |
| **One landing, one docs site** | A Hugo landing at `<org>.github.io` and versioned MkDocs Material docs at `<org>.github.io/docs/`, same brand, light/dark/system theme toggle. |
| **BSD-3-Clause** | Every repository, every organisation. |

## Desktop & widgets

One widget toolkit, every surface it paints on, and the platform plumbing a real desktop needs.

| Organisation | Repos | What it holds |
| --- | --- | --- |
| [`go-widgets`](https://github.com/go-widgets) | 16 | The widget toolkit and every surface it paints on: the painter seam, MVVM, a declarative skin engine, a terminal back-end, a native window on X11, Wayland, Cocoa and Win32, a real Android APK, and a desktop shell. |
| [`go-freedesktop`](https://github.com/go-freedesktop) | 8 | freedesktop.org integration — .desktop entries, icon themes, shared MIME info, application associations, the menu tree, desktop notifications and Secret Service. |
| [`go-iconoir`](https://github.com/go-iconoir) | 1 | The whole Iconoir set — 1,671 SVGs embedded and rendered to anti-aliased coverage masks for the toolkit painter. |
| [`go-thumbnail`](https://github.com/go-thumbnail) | 1 | The freedesktop Thumbnail Managing Standard cache. |
| [`go-keyring`](https://github.com/go-keyring) | 1 | One secret store over macOS Keychain, Windows Credential Manager and Linux Secret Service — no cgo, no CLI exec. |
| [`go-macos`](https://github.com/go-macos) | 3 | The macOS foundation: the shared Objective-C runtime bridge over purego, plus Keychain and notifications. |
| [`go-mswin`](https://github.com/go-mswin) | 2 | The Windows foundation: Win32 bindings and WinRT interop on combase — peer of go-macos/objc. |
| [`wasmdesk`](https://github.com/wasmdesk) | 7 | A desktop in the browser — a Wayland-inspired compositor and window manager, a dock, a login portal, OCI app packaging and a coreutils suite. |

## Graphics, images & media

The 2D socle everything above draws through, and the pixels and frames it moves.

| Organisation | Repos | What it holds |
| --- | --- | --- |
| [`go-gfx`](https://github.com/go-gfx) | 1 | The shared 2D socle: an anti-aliased vector rasteriser, a raster surface, colour, geometry, resampling, and SVG to bitmap. |
| [`go-images`](https://github.com/go-images) | 1 | Image processing at scikit-image scope. |
| [`go-avkit`](https://github.com/go-avkit) | 1 | An audio/video toolkit — MP4/ISO-BMFF and Matroska/WebM demuxing. |

## Documents, typesetting & fonts

Turning a document into pages: fonts, breaking, shaping, TeX, PDF, and one rich-document model.

| Organisation | Repos | What it holds |
| --- | --- | --- |
| [`go-tex`](https://github.com/go-tex) | 5 | A TeX engine — mouth and gullet, math mode to SVG, a PDF-figure rasteriser, and a fetcher that gets a document the class files it asks for without redistributing any. |
| [`go-typeset`](https://github.com/go-typeset) | 3 | The typesetting algorithms on their own, with no TeX vocabulary in the API: Knuth-Plass line breaking, Liang hyphenation, the Unicode bidirectional algorithm. |
| [`go-opentype`](https://github.com/go-opentype) | 3 | The font format: TrueType/OpenType parsing and anti-aliased rasterisation, a HarfBuzz-lite complex-text shaper, and legible fonts ready to import. |
| [`go-synctex`](https://github.com/go-synctex) | 1 | TeX's SyncTeX — the source-to-PDF correspondence, both ways. |
| [`go-pdfkit`](https://github.com/go-pdfkit) | 1 | A PDF 1.7 writer: font subsetting and embedding for TrueType and CFF, graphics, images, shaped text. |
| [`go-richdoc`](https://github.com/go-richdoc) | 3 | One rich-document model, and the converters that read and write it. |
| [`go-odf`](https://github.com/go-odf) | 1 | OpenDocument Text, in and out of the richdoc model. |
| [`go-rtf`](https://github.com/go-rtf) | 1 | RTF, in and out of the richdoc model. |

## Markup, templating & text

Reading and writing the formats documents arrive in, and the engines that scan them.

| Organisation | Repos | What it holds |
| --- | --- | --- |
| [`go-commonmark`](https://github.com/go-commonmark) | 1 | Strict CommonMark 0.31.2 to HTML — all 652 spec examples. |
| [`go-kramdown`](https://github.com/go-kramdown) | 1 | kramdown-flavoured Markdown, as Jekyll uses it. |
| [`go-nokogiri`](https://github.com/go-nokogiri) | 1 | HTML and XML: parse, query, mutate, serialise. |
| [`go-xslt`](https://github.com/go-xslt) | 1 | XSLT transformation. |
| [`go-scss`](https://github.com/go-scss) | 1 | A Sass/SCSS compiler with Dart-Sass-compatible output — the engine behind the Ruby sass gem. |
| [`go-mustache`](https://github.com/go-mustache) | 1 | Logic-less Mustache templating, spec-faithful. |
| [`go-liquid`](https://github.com/go-liquid) | 1 | Shopify's Liquid template engine, gem-faithful. |
| [`go-rouge`](https://github.com/go-rouge) | 1 | A Rouge/Pygments-class syntax highlighter — per-language lexers, token types, named themes. |
| [`go-regexp`](https://github.com/go-regexp) | 1 | An Onigmo engine shaped like the standard library's regexp, with the lookaround and backreferences RE2 cannot do. |
| [`go-datetime`](https://github.com/go-datetime) | 1 | A lenient parser for the dates people actually write. |

## Web & transports

Rendering a page without a browser, and carrying gRPC where gRPC does not go.

| Organisation | Repos | What it holds |
| --- | --- | --- |
| [`go-webengine`](https://github.com/go-webengine) | 2 | A headless web engine: HTML and CSS laid out and painted to an image, with no Chromium — plus a service that streams those frames to a thin client. |
| [`go-browserhttp`](https://github.com/go-browserhttp) | 1 | An http.Client that presents a Chrome TLS fingerprint. |
| [`go-lsp-bridge`](https://github.com/go-lsp-bridge) | 1 | A WebSocket-to-stdio bridge for JSON-RPC language-server traffic. |
| [`grpc-transports`](https://github.com/grpc-transports) | 5 | gRPC where it is not supposed to go: over SSH, WireGuard, vsock, WebSocket and WebRTC. |

## Realtime collaboration

Many people, one document, no server deciding who won.

| Organisation | Repos | What it holds |
| --- | --- | --- |
| [`go-crdt`](https://github.com/go-crdt) | 2 | A replicated text document and the service that carries it between the people editing it — the same merge logic on the server and in the browser, via js/wasm. |
| [`go-yjs-relay`](https://github.com/go-yjs-relay) | 1 | A Yjs y-websocket relay hub, transport-agnostic. |

## Ruby, in Go

A Ruby virtual machine, its object model, and one organisation per gem it needs.

| Organisation | Repos | What it holds |
| --- | --- | --- |
| [`go-embedded-ruby`](https://github.com/go-embedded-ruby) | 1 | The Ruby virtual machine — YARV bytecode, the object model, the core library, and the rbgo interpreter. |
| [`go-composites`](https://github.com/go-composites) | 31 | Ruby's numeric tower, collections, time and dates as composition-oriented building blocks: Result-based, Null-Object, never nil. |
| [`go-ruby-widgets`](https://github.com/go-ruby-widgets) | 3 | MVVM, widgets and a terminal toolkit, addressable from Ruby. |
| [`go-vet-analyzers`](https://github.com/go-vet-analyzers) | 2 | go vet analyzers that make the ecosystem's invariants a compile-time matter. |

## CPU, SIMD & numerics

Getting the machine's width out of pure Go, on all six 64-bit targets.

| Organisation | Repos | What it holds |
| --- | --- | --- |
| [`go-asmgen`](https://github.com/go-asmgen) | 1 | Ergonomic generation of Go-compatible Plan 9 assembly for every 64-bit Go target. |
| [`go-simd`](https://github.com/go-simd) | 22 | SIMD kernels on all six of Go's 64-bit targets — codecs, hashes, string scans, bitsets, float and int8 dot products. |
| [`go-ndarray`](https://github.com/go-ndarray) | 1 | A numpy-shaped n-dimensional array, with GEMM at vecLib parity. |
| [`go-fft`](https://github.com/go-fft) | 1 | Fast Fourier transforms at numpy and scipy accuracy, without FFTW. |

## Compression, delta & erasure

Making bytes smaller, sending only what changed, and surviving what is lost.

| Organisation | Repos | What it holds |
| --- | --- | --- |
| [`go-compressions`](https://github.com/go-compressions) | 8 | LZFSE, LZ4, deflate and BLAKE3, with the CLIs that go with them. |
| [`go-deltasync`](https://github.com/go-deltasync) | 6 | Delta transfer: zsync2, rdiff, zchunk, vcdiff, bita — and the one content-defined chunker they all import. |
| [`go-erasure`](https://github.com/go-erasure) | 2 | Erasure coding: Reed-Solomon over GF(2^16), and the Mojette transform. |

## Storage, volumes & filesystems

From a block device to a mounted filesystem, without a C library anywhere.

| Organisation | Repos | What it holds |
| --- | --- | --- |
| [`go-volumes`](https://github.com/go-volumes) | 9 | The block layer — a device contract, NBD, pools, replicas, S3, an OCI image as a block device, GPT and MBR, and parse-hardening guards. |
| [`go-filesystems`](https://github.com/go-filesystems) | 17 | Filesystem-format drivers — ext4, xfs, btrfs, zfs, apfs, ntfs, exfat, fat32, iso9660, squashfs and more — plus UEFI variable management and a format prober. |
| [`go-diskimages`](https://github.com/go-diskimages) | 6 | Disk-image formats: qcow2, raw, dmg, tart-oci, in either direction. |
| [`go-fsctl`](https://github.com/go-fsctl) | 6 | Linux kernel ioctl wrappers — zfs, btrfs, loop, device-mapper, block, copy-on-write clones. |
| [`go-fde`](https://github.com/go-fde) | 4 | Full-disk encryption: LUKS, APFS, and the plumbing that opens them. |
| [`go-encryptions`](https://github.com/go-encryptions) | 3 | The modes underneath: CCM, XTS, ZFS crypto. |

## Firmware, boot & trust

What runs before the kernel, and how you prove what ran.

| Organisation | Repos | What it holds |
| --- | --- | --- |
| [`go-tpm2`](https://github.com/go-tpm2) | 8 | TPM 2.0 end to end: transports, the command layer, EFI_TCG2, measured boot, event-log replay and remote attestation. |
| [`go-coff`](https://github.com/go-coff) | 4 | PE/COFF for UEFI — an object-to-EFI linker, a signing and conversion CLI, and a self-extracting EFI packer. |
| [`go-bootloaders`](https://github.com/go-bootloaders) | 2 | GRUB and systemd-boot tooling, composed on the storage, UEFI and TPM stacks rather than reimplementing them. |
| [`cloud-boot`](https://github.com/cloud-boot) | 7 | Booting the machine: a TamaGo UEFI payload, a unified kernel image, an init, kernels, ISOs, SEV-SNP. |
| [`nano-container-linux`](https://github.com/nano-container-linux) | 7 | A minimal container host — OCI initrd and PXE boot, a DNS daemon, an OpenPubKey agent. |

## Packaging & supply chain

Building every dependency from source, signing it, and saying where it came from.

| Organisation | Repos | What it holds |
| --- | --- | --- |
| [`go-pkgx`](https://github.com/go-pkgx) | 8 | A pure-Go pkgx: the package manager, the bottle installer, the bk recipe builder, and the CI factory that publishes signed bottles. |
| [`go-attest`](https://github.com/go-attest) | 2 | SPDX and CycloneDX SBOMs, SLSA provenance, and Ed25519 signing that is minisign- and cosign-interoperable from one keypair. |
| [`go-versions`](https://github.com/go-versions) | 1 | Loose, pkgx-compatible semantic versions and ranges, CalVer included. |

## Virtualisation, cloud & network

microVMs, guest drivers, supervision, coordination and the network between them.

| Organisation | Repos | What it holds |
| --- | --- | --- |
| [`openweft`](https://github.com/openweft) | 70 | weft — a Go-native microVM cloud: drivers, network, block storage, HA services, runners, clients, native apps, and the loom editor built on it. |
| [`go-virtio`](https://github.com/go-virtio) | 13 | Guest virtio drivers: net, blk, gpu with virgl and Venus, console, rng, vsock, balloon, fs, sound, input. |
| [`go-proc`](https://github.com/go-proc) | 2 | A PID-1 subreaper and process supervisor, and the restart state machine that decides when to try again. |
| [`go-coord`](https://github.com/go-coord) | 1 | Cross-host coordination on etcd v3: host liveness, watches, leader election. |
| [`go-net-dhcp`](https://github.com/go-net-dhcp) | 1 | A dependency-free DHCPv4 server library. |
| [`go-net-health`](https://github.com/go-net-health) | 1 | Active health probes — stateless TCP and HTTP checks folded into a rolling verdict. |
| [`cloud-pool-managers`](https://github.com/cloud-pool-managers) | 1 | VM pool management. |
| [`claimward`](https://github.com/claimward) | 6 | A WireGuard VPN with OIDC: the server, the client, and desktop apps for macOS, Linux and Windows. |

## Configuration management

The Puppet stack, in Go, without a Ruby runtime.

| Organisation | Repos | What it holds |
| --- | --- | --- |
| [`go-puppet`](https://github.com/go-puppet) | 1 | The Puppet language and its catalogue compiler. |
| [`go-pcore`](https://github.com/go-pcore) | 1 | Puppet's Pcore type system: type calculus, parser, value model, assignability lattice. |
| [`go-puppetdb`](https://github.com/go-puppetdb) | 1 | PuppetDB. |
| [`go-puppet-bolt`](https://github.com/go-puppet-bolt) | 1 | Bolt — task and plan orchestration over SSH and WinRM. |
| [`go-facter`](https://github.com/go-facter) | 1 | Fact collection. |
| [`go-hiera`](https://github.com/go-hiera) | 1 | Hierarchical data lookup. |
| [`go-eyaml`](https://github.com/go-eyaml) | 1 | eyaml — encrypted values inside Hiera data. |
| [`go-hocon`](https://github.com/go-hocon) | 1 | HOCON configuration. |
| [`go-augeas`](https://github.com/go-augeas) | 1 | The Augeas engine: a config tree, path expressions and lenses. |

## News, social & feeds

One reader, and a client per source it reads.

| Organisation | Repos | What it holds |
| --- | --- | --- |
| [`go-news-reader`](https://github.com/go-news-reader) | 1 | A multi-source news and social aggregator with a go-widgets interface — Reddit, RSS, Hacker News, Usenet, Mastodon, Lemmy, Bluesky and more in one reader. |
| [`go-syndication`](https://github.com/go-syndication) | 1 | RSS, Atom and JSON Feed: parse and fetch. |
| [`go-newsgroups`](https://github.com/go-newsgroups) | 5 | Usenet, whole: NNTP, yEnc, Newznab, NZB, PAR2. |
| [`go-reddit`](https://github.com/go-reddit) | 2 | A Reddit read client, and a reader built on it. |
| [`go-mastodon`](https://github.com/go-mastodon) | 1 | A Mastodon read client. |
| [`go-lemmy`](https://github.com/go-lemmy) | 1 | A Lemmy read client. |
| [`go-hackernews`](https://github.com/go-hackernews) | 1 | A Hacker News read client. |
| [`go-atproto`](https://github.com/go-atproto) | 1 | A Bluesky / AT Protocol read client. |
| [`go-birdsite`](https://github.com/go-birdsite) | 1 | A best-effort read client for public Twitter/X timelines. |
| [`go-instagram`](https://github.com/go-instagram) | 1 | A best-effort read client for public Instagram profiles. |
| [`go-tiktok`](https://github.com/go-tiktok) | 1 | A best-effort read client for public TikTok profiles. |

## Games

Two engines hand-ported to pure Go, one of them onto bare metal.

| Organisation | Repos | What it holds |
| --- | --- | --- |
| [`go-quake1`](https://github.com/go-quake1) | 1 | Quake 1, hand-ported from tyrquake, with a bare-metal target. |
| [`go-doom`](https://github.com/go-doom) | 1 | DOOM, hand-ported through the gore lineage, with a TamaGo bare-metal back-end. |

## Ruby gems — one organisation each

The Ruby virtual machine is only useful with a library around it. Each gem it
needs is reimplemented in pure Go in its own `go-ruby-*` organisation: the
standard library, Rails and its dependencies, the testing stack, the Puppet
stack, database drivers, serialisation formats and template engines. Every one of
them is byte-compared against MRI where a byte comparison is meaningful.

<details><summary><strong>196 gem organisations</strong> — click to expand</summary>

[`aasm`](https://github.com/go-ruby-aasm) · [`abbrev`](https://github.com/go-ruby-abbrev) · [`acme`](https://github.com/go-ruby-acme) · [`actioncable`](https://github.com/go-ruby-actioncable) · [`actionmailer`](https://github.com/go-ruby-actionmailer) · [`actionpack`](https://github.com/go-ruby-actionpack) · [`actionview`](https://github.com/go-ruby-actionview) · [`activejob`](https://github.com/go-ruby-activejob) · [`activeldap`](https://github.com/go-ruby-activeldap) · [`activemodel`](https://github.com/go-ruby-activemodel) · [`activerecord`](https://github.com/go-ruby-activerecord) · [`activestorage`](https://github.com/go-ruby-activestorage) · [`activesupport`](https://github.com/go-ruby-activesupport) · [`addressable`](https://github.com/go-ruby-addressable) · [`age`](https://github.com/go-ruby-age) · [`arrow`](https://github.com/go-ruby-arrow) · [`async`](https://github.com/go-ruby-async) · [`augeas`](https://github.com/go-ruby-augeas) · [`base64`](https://github.com/go-ruby-base64) · [`bbolt`](https://github.com/go-ruby-bbolt) · [`bcrypt`](https://github.com/go-ruby-bcrypt) · [`benchmark`](https://github.com/go-ruby-benchmark) · [`bigdecimal`](https://github.com/go-ruby-bigdecimal) · [`bleve`](https://github.com/go-ruby-bleve) · [`builder`](https://github.com/go-ruby-builder) · [`bundler`](https://github.com/go-ruby-bundler) · [`cancancan`](https://github.com/go-ruby-cancancan) · [`capistrano`](https://github.com/go-ruby-capistrano) · [`capybara`](https://github.com/go-ruby-capybara) · [`cgi`](https://github.com/go-ruby-cgi) · [`chronic`](https://github.com/go-ruby-chronic) · [`cmath`](https://github.com/go-ruby-cmath) · [`commonmark`](https://github.com/go-ruby-commonmark) · [`complex`](https://github.com/go-ruby-complex) · [`concurrent-ruby`](https://github.com/go-ruby-concurrent-ruby) · [`confd`](https://github.com/go-ruby-confd) · [`connection-pool`](https://github.com/go-ruby-connection-pool) · [`csv`](https://github.com/go-ruby-csv) · [`date`](https://github.com/go-ruby-date) · [`deep-merge`](https://github.com/go-ruby-deep-merge) · [`devise`](https://github.com/go-ruby-devise) · [`did-you-mean`](https://github.com/go-ruby-did-you-mean) · [`digest`](https://github.com/go-ruby-digest) · [`dotenv`](https://github.com/go-ruby-dotenv) · [`dry-struct`](https://github.com/go-ruby-dry-struct) · [`dry-types`](https://github.com/go-ruby-dry-types) · [`dry-validation`](https://github.com/go-ruby-dry-validation) · [`erasure`](https://github.com/go-ruby-erasure) · [`erb`](https://github.com/go-ruby-erb) · [`erubi`](https://github.com/go-ruby-erubi) · [`etcd`](https://github.com/go-ruby-etcd) · [`excon`](https://github.com/go-ruby-excon) · [`facter`](https://github.com/go-ruby-facter) · [`factory-bot`](https://github.com/go-ruby-factory-bot) · [`faker`](https://github.com/go-ruby-faker) · [`faraday`](https://github.com/go-ruby-faraday) · [`fast-gettext`](https://github.com/go-ruby-fast-gettext) · [`fast-gettext-locale`](https://github.com/go-ruby-fast-gettext-locale) · [`find`](https://github.com/go-ruby-find) · [`format`](https://github.com/go-ruby-format) · [`friendly-id`](https://github.com/go-ruby-friendly-id) · [`fsctl`](https://github.com/go-ruby-fsctl) · [`getoptlong`](https://github.com/go-ruby-getoptlong) · [`grape`](https://github.com/go-ruby-grape) · [`graphql`](https://github.com/go-ruby-graphql) · [`grpc`](https://github.com/go-ruby-grpc) · [`haml`](https://github.com/go-ruby-haml) · [`hanami`](https://github.com/go-ruby-hanami) · [`hcl2`](https://github.com/go-ruby-hcl2) · [`hiera`](https://github.com/go-ruby-hiera) · [`hiera-eyaml`](https://github.com/go-ruby-hiera-eyaml) · [`hocon`](https://github.com/go-ruby-hocon) · [`http`](https://github.com/go-ruby-http) · [`httparty`](https://github.com/go-ruby-httparty) · [`i18n`](https://github.com/go-ruby-i18n) · [`images`](https://github.com/go-ruby-images) · [`ipaddr`](https://github.com/go-ruby-ipaddr) · [`irb`](https://github.com/go-ruby-irb) · [`jbuilder`](https://github.com/go-ruby-jbuilder) · [`jekyll`](https://github.com/go-ruby-jekyll) · [`json`](https://github.com/go-ruby-json) · [`jwt`](https://github.com/go-ruby-jwt) · [`kafka`](https://github.com/go-ruby-kafka) · [`kaminari`](https://github.com/go-ruby-kaminari) · [`kramdown`](https://github.com/go-ruby-kramdown) · [`ldap`](https://github.com/go-ruby-ldap) · [`liquid`](https://github.com/go-ruby-liquid) · [`logger`](https://github.com/go-ruby-logger) · [`mail`](https://github.com/go-ruby-mail) · [`marshal`](https://github.com/go-ruby-marshal) · [`matrix`](https://github.com/go-ruby-matrix) · [`mime-types`](https://github.com/go-ruby-mime-types) · [`minitest`](https://github.com/go-ruby-minitest) · [`money`](https://github.com/go-ruby-money) · [`mongodb`](https://github.com/go-ruby-mongodb) · [`msgpack`](https://github.com/go-ruby-msgpack) · [`multi-json`](https://github.com/go-ruby-multi-json) · [`mustache`](https://github.com/go-ruby-mustache) · [`mysql`](https://github.com/go-ruby-mysql) · [`nats`](https://github.com/go-ruby-nats) · [`net-ftp`](https://github.com/go-ruby-net-ftp) · [`net-http`](https://github.com/go-ruby-net-http) · [`net-imap`](https://github.com/go-ruby-net-imap) · [`net-pop`](https://github.com/go-ruby-net-pop) · [`net-s3`](https://github.com/go-ruby-net-s3) · [`net-sftp`](https://github.com/go-ruby-net-sftp) · [`net-smtp`](https://github.com/go-ruby-net-smtp) · [`nokogiri`](https://github.com/go-ruby-nokogiri) · [`oauth2`](https://github.com/go-ruby-oauth2) · [`observer`](https://github.com/go-ruby-observer) · [`oidc`](https://github.com/go-ruby-oidc) · [`omniauth`](https://github.com/go-ruby-omniauth) · [`openbao`](https://github.com/go-ruby-openbao) · [`openssl`](https://github.com/go-ruby-openssl) · [`openstack`](https://github.com/go-ruby-openstack) · [`opentelemetry`](https://github.com/go-ruby-opentelemetry) · [`opentype`](https://github.com/go-ruby-opentype) · [`optparse`](https://github.com/go-ruby-optparse) · [`ostruct`](https://github.com/go-ruby-ostruct) · [`pagy`](https://github.com/go-ruby-pagy) · [`paper-trail`](https://github.com/go-ruby-paper-trail) · [`parquet`](https://github.com/go-ruby-parquet) · [`parser`](https://github.com/go-ruby-parser) · [`pathname`](https://github.com/go-ruby-pathname) · [`pg`](https://github.com/go-ruby-pg) · [`prawn`](https://github.com/go-ruby-prawn) · [`prettyprint`](https://github.com/go-ruby-prettyprint) · [`prime`](https://github.com/go-ruby-prime) · [`protobuf`](https://github.com/go-ruby-protobuf) · [`pstore`](https://github.com/go-ruby-pstore) · [`public-suffix`](https://github.com/go-ruby-public-suffix) · [`puma`](https://github.com/go-ruby-puma) · [`pundit`](https://github.com/go-ruby-pundit) · [`puppet`](https://github.com/go-ruby-puppet) · [`puppet-resource-api`](https://github.com/go-ruby-puppet-resource-api) · [`racc`](https://github.com/go-ruby-racc) · [`rack`](https://github.com/go-ruby-rack) · [`rails`](https://github.com/go-ruby-rails) · [`railties`](https://github.com/go-ruby-railties) · [`rake`](https://github.com/go-ruby-rake) · [`ransack`](https://github.com/go-ruby-ransack) · [`rational`](https://github.com/go-ruby-rational) · [`rdoc`](https://github.com/go-ruby-rdoc) · [`reddit`](https://github.com/go-ruby-reddit) · [`redis`](https://github.com/go-ruby-redis) · [`regexp`](https://github.com/go-ruby-regexp) · [`reline`](https://github.com/go-ruby-reline) · [`resolv`](https://github.com/go-ruby-resolv) · [`resque`](https://github.com/go-ruby-resque) · [`rexml`](https://github.com/go-ruby-rexml) · [`roda`](https://github.com/go-ruby-roda) · [`rolify`](https://github.com/go-ruby-rolify) · [`rouge`](https://github.com/go-ruby-rouge) · [`rqrcode`](https://github.com/go-ruby-rqrcode) · [`rspec`](https://github.com/go-ruby-rspec) · [`rss`](https://github.com/go-ruby-rss) · [`rubocop`](https://github.com/go-ruby-rubocop) · [`rubygems`](https://github.com/go-ruby-rubygems) · [`saml`](https://github.com/go-ruby-saml) · [`sass`](https://github.com/go-ruby-sass) · [`scanf`](https://github.com/go-ruby-scanf) · [`securerandom`](https://github.com/go-ruby-securerandom) · [`semantic-puppet`](https://github.com/go-ruby-semantic-puppet) · [`sequel`](https://github.com/go-ruby-sequel) · [`set`](https://github.com/go-ruby-set) · [`shellwords`](https://github.com/go-ruby-shellwords) · [`shrine`](https://github.com/go-ruby-shrine) · [`sidekiq`](https://github.com/go-ruby-sidekiq) · [`simplecov`](https://github.com/go-ruby-simplecov) · [`sinatra`](https://github.com/go-ruby-sinatra) · [`slim`](https://github.com/go-ruby-slim) · [`sodium`](https://github.com/go-ruby-sodium) · [`sqlite3`](https://github.com/go-ruby-sqlite3) · [`stdlib`](https://github.com/go-ruby-stdlib) · [`stringio`](https://github.com/go-ruby-stringio) · [`strscan`](https://github.com/go-ruby-strscan) · [`syslog`](https://github.com/go-ruby-syslog) · [`thor`](https://github.com/go-ruby-thor) · [`time`](https://github.com/go-ruby-time) · [`timecop`](https://github.com/go-ruby-timecop) · [`toml`](https://github.com/go-ruby-toml) · [`tsort`](https://github.com/go-ruby-tsort) · [`typhoeus`](https://github.com/go-ruby-typhoeus) · [`tzinfo`](https://github.com/go-ruby-tzinfo) · [`unicode-normalize`](https://github.com/go-ruby-unicode-normalize) · [`uri`](https://github.com/go-ruby-uri) · [`vcr`](https://github.com/go-ruby-vcr) · [`warden`](https://github.com/go-ruby-warden) · [`webauthn`](https://github.com/go-ruby-webauthn) · [`webmock`](https://github.com/go-ruby-webmock) · [`webrick`](https://github.com/go-ruby-webrick) · [`xslt`](https://github.com/go-ruby-xslt) · [`yaml`](https://github.com/go-ruby-yaml) · [`zeitwerk`](https://github.com/go-ruby-zeitwerk) · [`zlib`](https://github.com/go-ruby-zlib)


</details>

## Held, not yet built

These organisation names are reserved and empty. They are listed so the map has
no silent gaps — an empty organisation is not a shipped one.

[`go-graphdrawing`](https://github.com/go-graphdrawing) · [`go-grub`](https://github.com/go-grub) · [`go-quake2`](https://github.com/go-quake2) · [`go-quake3`](https://github.com/go-quake3) · [`go-sicp`](https://github.com/go-sicp) · [`go-ruby-atproto`](https://github.com/go-ruby-atproto) · [`go-ruby-birdsite`](https://github.com/go-ruby-birdsite) · [`go-ruby-hackernews`](https://github.com/go-ruby-hackernews) · [`go-ruby-instagram`](https://github.com/go-ruby-instagram) · [`go-ruby-mastodon`](https://github.com/go-ruby-mastodon) · [`go-ruby-newsgroups`](https://github.com/go-ruby-newsgroups) · [`go-ruby-syndication`](https://github.com/go-ruby-syndication) · [`go-ruby-tiktok`](https://github.com/go-ruby-tiktok)

## Not in this map

Two sibling stacks are deliberately **not** Go, and are not counted above:
Separately, a handful of organisations hold research-computing and OpenStack
operations work in shell, HCL and Python rather than Go.

---

Counts are the public repositories that hold code; brand, docs and landing
repositories are excluded. BSD-3-Clause · brand assets in
[go-desktop/brand](https://github.com/go-desktop/brand).
