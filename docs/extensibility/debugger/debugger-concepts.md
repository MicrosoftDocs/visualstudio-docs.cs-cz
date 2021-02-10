---
title: Koncepty ladicího programu | Microsoft Docs
description: Přečtěte si o konceptech architektury, které se používají při navrhování balíčku ladění sady Visual Studio, který vám může pomáhat s vytvářením na tomto balíčku.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK]
ms.assetid: 2d371d38-f1a0-4a9a-8ea3-100e8c0149b7
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 5202ebdb621121e63adbdf5118cb0848689adde6
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99952405"
---
# <a name="debugger-concepts"></a>Koncepty ladicího programu
Chcete-li vytvořit balíček ladění sady Visual Studio, je třeba znát koncepty architektury používané při navrhování balíčku.

## <a name="in-this-section"></a>V této části
 [Relace ladění](../../extensibility/debugger/debug-session.md) Vysvětluje roli relace v architektuře ladění.

 [Servery](../../extensibility/debugger/servers-visual-studio-sdk.md) Definuje, co je server v architektuře ladění, v abstraktních i fyzických výrazech.

 [Dodavatelé portů](../../extensibility/debugger/port-suppliers.md) Definuje, co dodavatel portu je z pohledu architektury ladění.

 [Porty](../../extensibility/debugger/ports.md) Definuje port, který je z pohledu architektury ladění.

 [Procesy](../../extensibility/debugger/processes.md) Definuje, co proces je z pohledu architektury ladění.

 [Uzly programu](../../extensibility/debugger/program-nodes.md) Definuje uzel programu z pohledu architektury ladění, včetně toho, jak se může identifikovat a procesu, ve kterém je spuštěný.

 [Programy](../../extensibility/debugger/programs.md) Definuje program z pohledu architektury ladění.

 [Vlákna](../../extensibility/debugger/threads.md) Definuje charakteristiky vláken z hlediska architektury ladění.

 [Rámce zásobníku](../../extensibility/debugger/stack-frames.md) Definuje rámec zásobníku v souvislosti s architekturou ladění. Rámec zásobníku je abstrakcí zásobníku, který poskytuje kontext spuštění vlákna.

 [Moduly](../../extensibility/debugger/modules.md) Definuje modul v závislosti na architektuře ladění jako fyzický kontejner kódu, jako je například spustitelný soubor nebo knihovna DLL.

 [Zarážky](../../extensibility/debugger/breakpoints-visual-studio-sdk.md) Definuje tři typy zarážek – nevyřízené, vázané a chybové – v souvislosti s architekturou ladění.

## <a name="related-sections"></a>Související oddíly
 [Kontexty ladicího programu](../../extensibility/debugger/debugger-contexts.md) Vysvětluje, jak ladicí stroj (DE) funguje současně v rámci kódu, dokumentace a kontextů hodnocení výrazů. Popisuje pro každý ze tří kontextů, umístění, umístění nebo hodnocení, které jsou pro něj relevantní.

 [Komponenty ladicího programu](../../extensibility/debugger/debugger-components.md) Poskytuje přehled komponent pro ladění sady Visual Studio, které zahrnují modul ladění (DE), vyhodnocovací filtr výrazů (EE) a popisovač symbolů (SH).

 [Úlohy ladění](../../extensibility/debugger/debugging-tasks.md) Obsahuje odkazy na různé úlohy ladění, jako je například spuštění programu a vyhodnocování výrazů.
