---
title: Začínáme s rozšířením ladicího programu | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- getting started, Debugging SDK
- debugging [Debugging SDK], getting started
- Debugging SDK, getting started
ms.assetid: d6ce6f43-1409-4bf7-93cd-f3464ca23504
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 153db8889c78890a31a2e8003e6aa95ed24a02eb
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "80738592"
---
# <a name="get-started-with-debugger-extensibility"></a>Začínáme s rozšířením ladicího programu
[!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)]Poskytuje informace, které potřebujete k vytvoření a přizpůsobení komponent ladicího programu používaných pro ladění programů v rámci [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] prostředí.

 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] ladění přidalo vylepšení odvozená od rozsáhlého testování použitelnosti provedeného v předchozích [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] ladicích programech. Ladění můžete použít [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] ke krokování s vícejazyčnými aplikacemi nebo můžete implementovat průběžné úpravy proměnných při ladění aplikací a vícejazyčných řešení.

 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] ladění se provádí mimo proces s laděným programem a je proto méně rušivý v prostoru procesu aplikace. V důsledku toho je snazší psát komponenty, které pracují s ladicím programem, aniž by to ovlivnilo váš ladicí program.

 Abyste mohli nejlépe využít [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)] , měli byste být obeznámeni s následujícími položkami:

- [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]Integrované vývojové prostředí (IDE)

- Programovací jazyk C++

- ATL COM

## <a name="in-this-section"></a>V této části
 [Plán pro rozšíření ladicího programu](../../extensibility/debugger/roadmap-for-extending-the-debugger.md) Popisuje proces implementace ladění v produktu v závislosti na vašem kompilátoru a jeho výstupu.

 [Komponenty ladicího programu](../../extensibility/debugger/debugger-components.md) Poskytuje přehled [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] komponent ladění, které zahrnují modul ladění (de), vyhodnocovací filtr výrazů (EE) a popisovač symbolů (SH).

 [Koncepty ladicího programu](../../extensibility/debugger/debugger-concepts.md) Popisuje hlavní koncepty architektury ladění.

 [Kontexty ladicího programu](../../extensibility/debugger/debugger-contexts.md) Vysvětluje, jak ladicí stroj (DE) funguje současně v rámci kódu, dokumentace a kontextů hodnocení výrazů. Popisuje pro každý ze tří kontextů, umístění, umístění nebo hodnocení, které jsou pro něj relevantní.

 [Úlohy ladění](../../extensibility/debugger/debugging-tasks.md) Obsahuje odkazy na různé úlohy ladění, jako je například spuštění programu a vyhodnocování výrazů.
