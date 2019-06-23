# Repro steps

1. `pnpm i -store pnpm-store --frozen-lockfile`

Lockfile is up-to-date, resolution step is skipped
Already up-to-date

2. `cp .\projects\sp-application-base-step2.tgz .\projects\sp-application-base.tgz`

3. `pnpm i -store pnpm-store --frozen-lockfile`

Lockfile is up-to-date, resolution step is skipped
Already up-to-date

4. `rimraf .\node_modules\ .\pnpm-store\`

5. `pnpm i -store pnpm-store --frozen-lockfile`
Lockfile is up-to-date, resolution step is skipped
Packages: +11
+++++++++++
 WARN  Fetching file:projects/sp-application-base.tgz failed!
 ERROR  sha512-***== integrity checksum failed when using sha512: wanted sha512-***== but got sha512-***==. (262 bytes)

# Expected behavior

* Step 3 should fail saying that lockfile is out of date
* Step 5 should fail saying that lockfile is out of date

# Actual behavior

* Step 3 passes by saying that lockfile is up to date
* Step 5 says lockfile is out of date, but fails during install