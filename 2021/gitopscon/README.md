# Introducing libgitops: A programming model and Go runtime for any GitOps automation

## Metadata

- **Category:** How to solve edge cases around GitOps
- **Type:** Session Presentation
- **Technical Talk:** Yes
- **Skill Level:** Mid-Level

## Abstract

What if there was a client interface to Git; a SQL- or CRUD-like way to read from and write objects to Git? What if we treated Git more like other databases like MariaDB or etcd? What if writing data to Git from a Go program was straightforward, and object-oriented?

If this mindset shift took place, GitOps automation developers wouldn't focus as much on YAML serialization issues, traversing files/folders in Git, or remembering to “git fetch” periodically like they are forced to now, but could instead program applications interfacing with Git in an intention-driven way.

Abstracting away the thorny corner cases of writing to or reading from Git would make GitOps developers more productive, lead to fewer bugs (as complexity is centralized), and allow re-use of GitOps automation software “packages” across different environments, projects, and contexts.

libgitops is a library written in Go that implements this client interface for Git. It lets developers implement GitOps not only in Kubernetes environments, but anywhere. The programming model libgitops presents closely maps to the way Kubernetes operators work.

libgitops can be the core runtime powering e.g. GitOps-native UIs, pre-commit linters, drift monitoring agents, and “closed-loop” controllers that also write back to Git.

## Audience

This talk is targeted at Kubernetes Controller/Operator Developers, GitOps Automation Developers, Solution Architects, and those interested in new perspectives on how to program GitOps automations that simplify the lives of End Users.

Kubernetes Controller/Operator Developers are most likely familiar with either Kubebuilder or the Operator Framework SDK; that both build on top of controller-runtime. libgitops is also built on top of controller-runtime, but expands the use-case beyond Kubernetes to any system whose state can be described declaratively.

GitOps Automation Developers are struggling with the complex landscape of putting a declarative, Git-native automation pipeline together with maximum configurability but a minimal set of bugs. For them this talk will present a higher-level abstraction and programming model which allows them to be more productive by focusing on business logic.

Solution Architects who integrate existing GitOps open source projects into customers’ custom workflows find themselves writing the same automation logic over and over again, without an easy way to deduplicate and centralize. This talk will present a way to separate the “business logic” of an integration from its context; which allows sharing the logic across many customers’ contexts.

## Benefits to the Ecosystem

Currently, most (if not all?) GitOps tooling is designed with Kubernetes being the runtime system to which desired state information from Git is applied. That doesn’t have to be the case; GitOps philosophically is broader than “just” Kubernetes. However, Kubernetes has solved complex challenges around e.g. operator SDKs and API machinery management; innovations which haven’t propagated far outside of the Kubernetes project. 

As a GitOps automation developer not targeting Kubernetes you have to somehow solve those problems yourself, like parsing YAML (serialization), structuring the files (storage) and writing controllers (reconciliation). Without some kind of framework or change, GitOps adoption and further innovation is hindered. As a community we need to make it easier for newcomers to approach and be effective with GitOps automations anywhere.

If every GitOps automation were to write its own slightly different interface towards Git; bugs and limitations will be fragmented across the whole ecosystem. By centralizing common complex tasks (like serialization, storage and reconciliation), complexity can be managed and thus bugs reduced, which lead to a better experience for End Users.

libgitops could be a good candidate for a future OpenGitOps runtime library, time will tell.
