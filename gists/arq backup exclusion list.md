---
date created: Thursday, September 3rd 2026, 8:10:55 am
date modified: Thursday, September 3rd 2026, 8:13:12 am
tags:
  - arq
  - backup
  - macos
---

# arq backup exclusion list

I'm using [Arq Backup](https://www.arqbackup.com/) for offsite backups, the default file exclusion list is missing a lot of files when you're using different programming languages, package managers etc., so I'm documenting my exclusion list here which fits me well:

```
.DocumentRevisions-V100
.MobileBackups
.MobileBackups.trash
.Spotlight-V100
.TemporaryItems
.Trash
.Trashes
.dbfseventsd
.dropbox
.dropbox.cache
.fseventsd
.hotfiles.btree
.vol
Backups.backupdb
Cache
Caches
DerivedData
node_modules
Logs
*/iTunes/iTunes Media/Downloads
*/iTunes/iTunes Media/Podcasts
*/iTunes/Album Artwork
*/iTunes/Previous iTunes Libraries
*/Library/Application Support/CrashReporter
*/Library/Application Support/Dropbox
*/Library/Application Support/Google
*/Library/Application Support/MobileSync/Backup
*/Library/Application Support/com.apple.LaunchServicesTemplateApp.dv
*/Library/Biome
*/Library/Caches
*/Library/Containers/com.apple.mail/Data/Library/Mail Downloads
*/Library/Containers/com.apple.mail/Data/DataVaults
*/Library/Developer
*/Library/Google/GoogleSoftwareUpdate
*/Library/Metadata/CoreSpotlight
*/Library/Mirrors
*/Library/PubSub/Database
*/Library/PubSub/Downloads
*/Library/PubSub/Feeds
*/Library/Safari/Favicon Cache
*/Library/Safari/Icons.db
*/Library/Safari/Touch Icons Cache
*/Library/Safari/WebpageIcons.db
*/Library/Safari/HistoryIndex.sk
*/Library/VoiceTrigger/SAT
*/MailData/AvailableFeeds
*/MailData/BackingStoreUpdateJournal
*/MailData/Envelope Index
*/MailData/Envelope Index-journal
*/MailData/Envelope Index-shm
*/MailData/Envelope Index-wal
.cache
.npm
.DS_Store
.AppleDouble
*/Library/Application Support/*/Code Cache
*/Library/Application Support/*/GPUCache
*/Library/Application Support/*/DawnCache
*/Library/Application Support/*/GrShaderCache
*/Library/Application Support/*/ShaderCache
*/Library/Application Support/*/CachedData
*/Library/Application Support/*/Service Worker/CacheStorage
.venv
__pycache__
*.pyc
*.pyo
.pytest_cache
.mypy_cache
.ruff_cache
.pytype
.pyre
.hypothesis
.tox
.nox
.coverage
.coverage.*
__pypackages__
.eggs
*.egg-info
bower_components
.npm/_cacache
.npm/_logs
.npm/_npx
.pnpm-store
Library/pnpm/store
.yarn/berry/cache
.yarn/unplugged
.yarn/install-state.gz
.yarn/build-state.yml
.bun/install/cache
.turbo
.parcel-cache
.next/cache
.nuxt
.svelte-kit
.angular/cache
.vite
.eslintcache
.stylelintcache
.prettier-cache
.nyc_output
.sass-cache
*.tsbuildinfo
npm-debug.log*
yarn-debug.log*
yarn-error.log*
pnpm-debug.log*
vendor/bundle
.bundle/cache
.ruby-lsp
.yardoc
.rspec_status
.direnv
.terraform/providers
.terraform/modules
.terragrunt-cache
.wrangler/tmp
.gradle/caches
.gradle/daemon
.gradle/wrapper/dists
.m2/repository
.cargo/registry
.cargo/git/checkouts
.rustup/downloads
go/pkg/mod
.gem/ruby/*/cache
```
