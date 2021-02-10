---
title: Odesílání událostí | Microsoft Docs
description: Přečtěte si, jak ladicí program a ladicí modul používají model událostí založený na modelu DCOM. Události se odesílají jako objekty COM.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], sending events
ms.assetid: 064231e7-59b5-4437-8240-a23c0a7ec2a9
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: eb86be560f45941b1ca5eb04f38087c23c431fda
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99960855"
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
