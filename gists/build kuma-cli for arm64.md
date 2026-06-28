---
date created: Sunday, June 28th 2026, 9:37:28 am
date modified: Sunday, June 28th 2026, 9:49:54 am
tags:
  - cli
  - docker
  - uptime-kuma
  - kuma-cli
---

# build kuma-cli for arm64

there's a 3rd party cli utility for [uptime kuma](https://github.com/louislam/uptime-kuma) available to programmatically configure uptime kuma: [kuma-cli](https://crates.io/crates/kuma-cli/). It provides binaries for x86 linux and macos. Since I don't want/need rust/cargo installed on my computer, here's an easy way to compile `kuma-cli` for arm64 using docker and just get the `kuma-cli` executable as an artifact:

```shell
docker run --rm --user "$(id -u):$(id -g)" -v "$PWD:/out" -w /tmp rust:1.89 cargo install kuma-cli --version 2.0.0 --locked --root /out/
```

you might want to update version `2.0.0` to whatever is current ([see here](https://crates.io/crates/kuma-cli/)), same with the rust version, I used the one from their [`Dockerfile.cli`](https://github.com/BigBoot/AutoKuma/blob/master/Dockerfile.cli)
