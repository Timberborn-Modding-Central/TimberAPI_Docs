---
# https://vitepress.dev/reference/default-theme-home-page
layout: home

hero:
  name: "TimberApi, WIP"
  text: "Documentation work in progress"
#  text: "Modding made easy"
  tagline: Timberborn unofficial modding API
  actions:
    - theme: brand
      text: Getting started
      link: /markdown-examples

features:
  - icon: 🛠️
    title: uibuilder
    details: Create your own visual element presets within code
    link: https://vueuse.org/
  - icon: 🔨️
    title: Tool & Tool Groups
    details: Create or customize tool & tool groups
    link: https://vueuse.org/
  - icon: 🔗️
    title: Entity Linker
    details: Attach buildings to each other
    link: https://vueuse.org/
---

<script setup>
import { VPTeamMembers } from 'vitepress/theme';

const members = [
  {
    avatar: 'https://github.com/KYPremco.png',
    name: 'TheBloodEyes',
    title: 'Creator',
    links: [
      { icon: 'github', link: 'https://github.com/KYPremco' },
    ]
  },
]
</script>

## Contributors

<VPTeamMembers size="small" :members="members" />
