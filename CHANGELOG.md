# Changelog

All notable changes to Network Device Investigator will be documented in this file.

## Unreleased

### Added

- Initial Hermes skill definition.
- Common ports reference.
- Common vendors reference.
- IoT patterns reference.
- Camera vendors reference.
- Printer vendors reference.
- NAS vendors reference.
- Router vendors reference.
- Service banner reference.
- mDNS services reference.
- DHCP vendor classes reference.
- Risk scoring reference.
- Mystery IP camera example.
- Unknown printer example.
- NAS/file-server example.
- Device decision-tree reference.
- GitHub issue templates for fingerprints, examples, and corrections.
- Roadmap and outreach documentation.
- Contributing guide and MIT license.

### Changed

- Skill frontmatter uses lowercase hyphenated name: `network-device-investigator`.
- Scan guidance now uses safer tiers from passive evidence through deeper scans.
- README installation instructions now document full-folder Hermes installation so reference files are preserved.
- Internet-exposed admin risk wording now distinguishes High from Critical based on exploitability and sensitivity evidence.

### Security

- Added explicit defensive-only safety boundary.
- Added guidance against brute forcing, credential guessing, exploitation, persistence, and unauthorised access.
