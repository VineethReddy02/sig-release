# Kubernetes Release Team: Release Notes

## Overview:

The Release Notes role is responsible for collecting and fine-tuning release-notes from the many contributions to Kubernetes between release cycles. This role is likely to find that work during the first several weeks of the release cycle is very laid back with the bulk of the tasks being completed at the end, once the release is firmed up.

## Prerequisites for Release Notes Lead and Shadows

### General Requirements

**Before continuing on to the Release Notes specific requirements listed below, please review and work through the tasks in the [Release Team Onboarding Guide](/release-team/release-team-onboarding.md).**

### Skills and Experience Requirments:

* Strong written and verbal communications skills
* A working knowledge of Kubernetes concepts
* Project management experience is helpful but not requried

### Time Requirements:

Compared to other release team roles, release notes is one of the least time
intensive roles.
#### Early and mid release cycle (weeks 1-8) ~1-5 hours/week
For the first few weeks, attending meetings and running the
[release-notes tool](https://github.com/kubernetes/release/tree/master/cmd/release-notes)
as well as updating the
[release-notes website](https://github.com/kubernetes-sigs/release-notes)
weekly to create an early draft of the release notes is all that is absolutely
required of the release team. The release lead will be responsible for introducing
shadows to the team and the release notes tool and may ask shadows to run it
and make the weekly update PR. The release notes lead should indicate pain
points and known issues to the shadows (if there are any) and work on strategies
for overcoming them to avoid their coalescence during the later weeks. If there
are potential fixes to the issues indicated and team members are keen, this time
can be used to address them. Fixes and automation of the process is very welcome
but not expected.

#### Late release cycle (weeks 9-12+) ~4-10 hours/week
This period has an increase in release team  meetings each week and there is
also significantly more work to do to ensure the release notes are in good
working order for the release. Once code freeze begins, the release notes draft
is transfered to a google doc which is made public to the Kubernetes community.
The doc will be edited by SIG leads and SIG members but will also be edited for
grammar and uniform style by the release notes team. The Release Notes team
should use the [template](relnotes-template.md) to organize the raw generated release notes
in the Google doc as best as possible and help to guide SIG leads and members in their further
editing of the release notes. The final edited release notes should follow this
template. The changelog must also be generated and the release notes tool must continue to be run on the release
branch in order to pull in any outstanding PRs that are merged between the
beginning of code freeze and the release. The same applies to the website, which
should always represent the same state as the markdown document.


## Tasks

- The Release Notes Lead and Shadows attend burn down meetings, SIG Release meetings and follow the [#sig-release](https://kubernetes.slack.com/messages/C2C40FMNF) Slack channel for relevant information throughout the release cycle.
- One member of the Release Notes Team should be responsible for [setting up and running](setup-tool.md) the [release-notes tool](https://github.com/kubernetes/release/tree/master/cmd/release-notes) to collect generated drafts of all release-notes identified in the current release -- improvements to the tool are always welcome!
- Drafts produced by the tool are copied to a file called `release-notes-draft.md` in the [releases folder](../../../releases) for the current release in the `sig-release` repo.
- The [release-notes website](https://github.com/kubernetes-sigs/release-notes)
  should be updated together with the markdown based version: The website uses the
  JSON output from the release-notes tool to render it online. We publish the
  intermediate version directly to the `master` branch to reflect the current
  state. For this, the currently deployed release notes have to be preserved.
  Contributions and enhancements to the website are very welcome, whereas the
  feature planning and bug tracking happens directly in the GitHub repository. A
  note to this deployment will be added to the final manually edited release
  notes markdown document.
- The Communications team will hold meetings to discuss blogposts and media releases regarding the release sometime before code freeze. Ensure that at least one person from the release notes team attends this meeting with the release lead and enhancements lead. The release notes team should ensure that the "Major Themes" identified in this meeting are reflected in the "Major Themes" section of the release notes. If no one is able to attend the meeting, reach out to the communications team, release lead or enhancements lead to ensure messaging around Major Themes is coordinated.
- If gentle nudging of SIG Leads is not effective in retrieving feedback/confirmation, the Release Notes Team can use a reasonable amount of creative liberty in completing the notes
- A ["Known Issues Umbrella Issue"](known-issues-bucket.md) for the release must be created by the release notes team in [kubernetes/kubernetes](https://github.com/kubernetes/kubernetes/issues/new) so issues can be collected for the "Known Issues" section of the release notes.
- The confirmed upon notes are cleaned up and copy edited by the release-notes team to ensure uniform language/style is used.
- An "External Dependencies" section should be currated which outlines how external dependency versions have changed since the last release
  - See [the 1.12 release notes](https://github.com/kubernetes/kubernetes/blob/master/CHANGELOG-1.12.md#external-dependencies) for an example
	- Note that there are [plans in the process to formalize and automate the process of aggregating the changes](https://github.com/kubernetes/community/issues/2234), but this is currently [a very manual process](https://github.com/kubernetes/sig-release/pull/398).
  - To update an entry in this section the following steps must be performed:
    - Pick an entry, for example "Default etcd server was updated to v3.2.24. (#68318)"
    - Open the linked PR 68318 and find which files and lines it modifies
    - Open the same files in the `kubernetes/kubernetes` master branch and see if the version changed from v3.2.24
    - Look at the history of the file and find which commit / PR changed the version
    - Update the entry with the new version and PR URL
    - Update the entry message accordingly - if the version has changed or it has been preserved between versions
  - The website [lwkd.info](http://lwkd.info/) has weekly Kubernetes updates that often include information about changes in dependencies under a "Version Updates" section
- Kubernetes is released with the completed notes!

## Tools

- [Release notes tool](https://github.com/kubernetes/release/tree/master/cmd/release-notes)
- [Release notes website](https://relnotes.k8s.io)
- [Hackmd](https://hackmd.io/)
- [LWKD](http://lwkd.info) *(consider contributing to LWKD as part of your role)*

## TODOs

Update this section at the end of each release for the next Release Notes Team.

### Post 1.15 TODOs

#### High Priority
- Include previous release notes (1.14 and prior) in [Release notes website](https://relnotes.k8s.io)
- Survey users and use Google analytics from the release notes website to continually improve the format of the UX of the release notes
- Investigate opportunities to improve release notes collection by changing the
  PR boilerplate and/or creating new labels to indicate deprecations and
  dependencies (as per [#668](https://github.com/kubernetes/sig-release/issues/668))
- Add links to relevant documentation in the release notes--especially the
  Major Themes (as per [#667](https://github.com/kubernetes/sig-release/issues/667))

#### If any team members have NLP experience:
- Implement functionality in release-notes tool to automatically process language in generated release notes file
  Goals:
    - Generate uniform style across release notes (ie. past tense, formatting)
    - Decrease copy editing time

## Release Milestone Activities:

### Week 1 - 2

- Begin running release-notes script for ongoing collection of release notes
    - Update the `release-notes-draft.md`
    - Update the website
- Begin attending release team meetings
- Informal intro meeting with release notes team to discuss contact information and logistics


### Weeks 3 - 8

- Begin attending burndown meetings
- Same as above


### Week 9

- Create Google Doc for generated release notes and share with release-notes team
- Create [known issues issue](known-issues-bucket.md) in `kubernetes/kubernetes` to capture known issues for the release
- Share created doc with release-team
- Send [an email to sig leads](sig-leads-email.md) to capture major themes from their sig
- Start determining major themes for release notes template to send to sig-leads


### Week 10

- Finalize lead and shadow roles for subsequent release
- Work with sig-leads to finalize major themes for release-notes
- Copy edit notes for spelling, grammar and uniform style


### Week 11

- Repeat previous tasks until final copy is complete
- Ensure "known issues" section is incorporated into final document

### Week 12

- Release day
- Copy notes from Google Doc to HackMD in markdown
- Final version of release notes committed for release

### Week 13

- Release retrospective participation
