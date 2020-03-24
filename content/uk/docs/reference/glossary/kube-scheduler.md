---
title: kube-scheduler
id: kube-scheduler
date: 2018-04-12
full_link: /docs/reference/generated/kube-scheduler/
short_description: >
#   Control Plane component that watches for newly created pods with no assigned node, and selects a node for them to run on.
  Компонент площини управління, що відстежує створені Поди, які ще не прив'язані до вузла, і обирає вузол, на якому вони працюватимуть.

aka:
tags:
- architecture
---
<!-- Control Plane component that watches for newly created pods with no assigned node, and selects a node for them to run on. -->
Компонент площини управління, що відстежує створені Поди, які ще не прив'язані до вузла, і обирає вузол, на якому вони працюватимуть.

<!--more-->

<!--Factors taken into account for scheduling decisions include individual and collective resource requirements, hardware/software/policy constraints, affinity and anti-affinity specifications, data locality, inter-workload interference and deadlines.
-->
При виборі вузла враховуються наступні фактори: індивідуальна і колективна потреба у ресурсах, обмеження за апаратним/програмним забезпеченням і політиками, характеристики афінності та антиафінності, локальність даних, завади у межах робочих навантажень і критичні терміни обслуговування.