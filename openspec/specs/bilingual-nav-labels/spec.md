# Bilingual Nav Labels Spec

## Purpose

Defines the requirements for bilingual (Chinese + English) navigation tab labels in the bottom nav bar.

## Requirements

### Requirement: Bilingual navigation tab labels
All 6 navigation tabs SHALL display a Chinese primary label and an English sub-label, stacked vertically below the tab icon.

#### Scenario: English sub-label visible on each tab
- **WHEN** the user views the bottom navigation bar
- **THEN** each tab SHALL show the Chinese label on one line and the English equivalent on the line below, in smaller grey text

#### Scenario: Correct label mapping
- **WHEN** the navigation bar is rendered
- **THEN** the label pairs SHALL be: 名單/Roster, 賽程/Schedule, 計分/Score, 戰績/Battle Record, 紀錄/Records, 說明/Guide

#### Scenario: English sub-label is visually subordinate
- **WHEN** both labels are displayed
- **THEN** the English sub-label SHALL be rendered at 8px or smaller, in a grey colour (#86868b), so the Chinese label remains visually dominant

### Requirement: 排名 tab renamed to 戰績
The navigation tab previously labelled 排名 (rankings) SHALL be relabelled to 戰績 (battle record), and the page title shown in the header when that tab is active SHALL also change to 戰績.

#### Scenario: Nav button shows 戰績
- **WHEN** the navigation bar is rendered
- **THEN** the fourth tab button SHALL display 戰績 (not 排名) as the Chinese label

#### Scenario: Page header shows 戰績 when tab is active
- **WHEN** the user navigates to the 戰績 tab
- **THEN** the `<h1 id="page-title">` element SHALL display 戰績
