# Trunk-Based Development

## Overview
Trunk-Based Development (TBD) is a streamlined branching strategy that promotes a single shared branch called "trunk" (or `main`) and eliminates long-living branches. Developers integrate their changes frequently into the trunk, enabling continuous integration and rapid releases. This approach emphasizes small, incremental changes and robust automated testing.

**Best suited for**: Experienced teams, continuous deployment, fast-paced environments, and organizations with strong DevOps practices.

## Core Principles

- **Single source of truth** - One main branch (trunk) that everyone works from
- **Frequent integration** - Commit to trunk multiple times per day
- **Small incremental changes** - Break features into small, mergeable pieces
- **Short-lived branches** - Feature branches last hours or 1-2 days maximum (for larger teams)
- **Feature flags** - Deploy incomplete features hidden behind toggles
- **Robust CI/CD** - Automated testing and deployment pipelines are critical
- **Fast feedback** - Quick builds and tests to validate changes immediately

## Branching Strategy

### Trunk Branch (`main`)
- **Purpose**: Single integration point, always deployable to production
- **Protection**: Protected, requires automated tests to pass
- **Activity**: High-frequency commits (multiple per day per developer)
- **Deployment**: Continuously deployed to production
- **Rules**: 
  - Must always be in deployable state
  - All commits trigger CI/CD pipeline
  - Failed builds must be fixed immediately
  - Represents latest production-ready code

### Two Implementation Variations

#### 1. Small Team Approach (1-10 developers)
- **Direct commits to trunk** - No feature branches
- **Commit frequency** - Multiple times daily
- **Pre-commit testing** - Run tests locally before push
- **Pair programming** - Optional, reduces need for code review

#### 2. Scaled Approach (10+ developers)
- **Short-lived feature branches** - Maximum 1-2 days
- **Naming**: `feature/small-change` or developer initials
- **Created from**: `trunk`
- **Merged into**: `trunk` via Pull Request
- **Delete immediately** after merge

### Release Branches (`release/*`) - Optional
- **Purpose**: Support production releases that need patches
- **Naming Convention**: `release/v1.2.x`
- **Created from**: Specific commit on `trunk`
- **Lifespan**: Until version is deprecated
- **Use case**: Only when supporting multiple production versions
- **Rule**: Cherry-pick fixes from trunk, don't develop here
