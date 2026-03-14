---
date created: Saturday, March 14th 2026, 8:39:01 am
date modified: Saturday, March 14th 2026, 8:42:02 am
tags:
  - openclaw
  - ai
  - llm
---

# openclaw cli cheatsheet

let's see how well this one ages! provided to you by ralphy, ralph (wiggum).

## health / status

```bash
openclaw status                       # quick health check
openclaw status --all                 # fuller read-only diagnosis
openclaw status --usage               # model/provider usage snapshot
openclaw doctor                       # find issues and suggest fixes
openclaw doctor --fix                 # apply recommended repairs
openclaw logs --follow                # tail gateway logs live
```

## gateway / service

```bash
openclaw gateway status               # check gateway service + reachability
openclaw gateway start                # start gateway service
openclaw gateway stop                 # stop gateway service
openclaw gateway restart              # restart gateway service
openclaw dashboard                    # open the control UI
```

## devices / nodes

```bash
openclaw devices list                 # list pending + paired devices
openclaw devices approve              # approve a pending device pairing
openclaw devices reject               # reject a pending device pairing
openclaw nodes status                 # list nodes with live status
openclaw nodes list                   # list pending + paired nodes
openclaw nodes camera snap --node ID  # take a photo from a paired node
```

## backups

```bash
openclaw backup create                # create a local backup archive
openclaw backup verify FILE           # verify a backup archive
```

## updates / install

```bash
openclaw update status                # show version + update channel status
openclaw update                       # update OpenClaw
openclaw update --dry-run             # preview update steps
curl -fsSL https://openclaw.ai/install.sh | bash -s -- --no-onboard
                                      # install/update without onboarding
```

## messaging / sessions

```bash
openclaw message send --channel telegram --target @mychat --message "hi"
                                      # send a message
openclaw sessions                     # list stored conversation sessions
openclaw memory search "query"        # search memory files
openclaw docs status                  # search docs from the CLI
```

## setup / rescue

```bash
openclaw configure                    # interactive setup/config wizard
openclaw onboard                      # onboarding wizard
openclaw qr                           # generate iOS pairing QR/setup code
openclaw reset                        # reset local config/state (careful)
openclaw uninstall                    # remove gateway service + local data
```

---

**Good first commands:**

```bash
openclaw status
openclaw doctor
openclaw gateway status
openclaw logs --follow
```
