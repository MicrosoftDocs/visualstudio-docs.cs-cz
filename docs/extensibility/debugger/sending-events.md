---
title: Odesílání událostí | Microsoft Docs
description: Přečtěte si, jak ladicí program a ladicí modul používají model událostí založený na modelu DCOM. Události se odesílají jako objekty COM.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- debugging [Debugging SDK], sending events
ms.assetid: 064231e7-59b5-4437-8240-a23c0a7ec2a9
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 6e9af2618150df522a459e47f312c1dc1e6a220c
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/25/2021
ms.locfileid: "112902251"
---
# <a name="send-events"></a>Odesílání událostí
Mechanismus pro komunikaci mezi ladicím programem a modulem ladění (DE) je model událostí založený na modelu DCOM. Události jsou odesílány jako objekty modelu COM a každá událost má parametry, které určují:

- DE, která volala událost.

- Popis toho, co se stalo.

- Informace o procesu, programu a vlákně, které určují kontext, kde došlo k události. Proces se neposílá pro události odeslané z DE.

- Typ události, která určuje, zda je událost synchronní nebo asynchronní.

  Všechny události ladění jsou odesílány pomocí metody [IDebugEventCallback2:: Event](../../extensibility/debugger/reference/idebugeventcallback2-event.md).

## <a name="in-this-section"></a>V této části
 [Zdroje událostí](../../extensibility/debugger/event-sources-visual-studio-sdk.md) Vysvětluje dva zdroje událostí: modul ladění (DE) a správce ladění relace (SDM).

 [Podporované typy událostí](../../extensibility/debugger/supported-event-types.md) Popisuje aktuálně podporované typy událostí: asynchronní a synchronní.

 [Popisy událostí](../../extensibility/debugger/event-descriptions.md) Definuje události a důvody jejich použití.

## <a name="related-sections"></a>Související oddíly
 [Vytvoření vlastního ladicího stroje](../../extensibility/debugger/creating-a-custom-debug-engine.md) Popisuje, jak DE funguje s překladačem nebo operačním systémem pro poskytování služeb ladění.
