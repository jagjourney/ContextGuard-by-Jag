# ContextGuard Public Updates

ContextGuard updates are delivered through public release assets and signed
updater metadata when releases are available.

## What Public Releases Include

- installer assets
- release notes
- signed updater artifacts
- `latest.json` updater metadata
- public help and MCP documentation

The public repo does not host proprietary application source code.

## Update Safety

Automatic updates should use signed artifacts. The app should verify signatures
before installing an update and should show people what version is available
before relaunching.

## Future Update Service

Jag Journey may later move update delivery to a dedicated Jag update service
with stable/beta channels, phased rollouts, rollback support, and release health
checks. Signature verification should stay part of the client update flow.

## Support

ContextGuard is a free app from Jag Journey, LLC, built in a giving spirit to
help people work with AI more safely. If it helps, please star the public repo
or support continued development through Jag Journey donations.
