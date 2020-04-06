---
title: Začínáme s rozšiřitelností ladicího programu | Dokumenty společnosti Microsoft
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
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80738592"
---
# <a name="get-started-with-debugger-extensibility"></a>Začínáme s rozšiřitelností ladicího programu
Poskytuje [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)] informace, které potřebujete k vytvoření a přizpůsobení součástí ladicího programu [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] používaných k ladění programů z prostředí.

 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]ladění přidalvylepšení odvozené z rozsáhlé testování použitelnosti provádí [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] na předchozí ladicí program. Ladění můžete [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] použít k procházení vícejazyčné aplikace nebo můžete implementovat průběžné úpravy proměnných při ladění aplikací a vícejazyčných řešení.

 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]ladění je spuštěnmimo proces s programem, který je laděn, a proto je méně rušivý v prostoru procesu aplikace. V důsledku toho je snazší psát součásti, které interagují s ladicím programem bez ovlivnění ladicího programu.

 Chcete-li [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)]nejlépe používat , měli byste být obeznámeni s následujícími položkami:

- Integrované [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] vývojové prostředí (IDE)

- Programovací jazyk C++

- Koma z ATL

## <a name="in-this-section"></a>V tomto oddílu
 [Plán rozšíření ladicího programu](../../extensibility/debugger/roadmap-for-extending-the-debugger.md) Popisuje proces implementace ladění v produktu, v závislosti na kompilátoru a jeho výstupu.

 [Součásti ladicího programu](../../extensibility/debugger/debugger-components.md) Obsahuje přehled ladicích [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] součástí, které zahrnují ladicí modul (DE), vyhodnocení výrazu (EE) a obslužnou rutinu symbolu (SH).

 [Koncepty ladicích programů](../../extensibility/debugger/debugger-concepts.md) Popisuje hlavní ladění architektonických konceptů.

 [Kontexty ladicího programu](../../extensibility/debugger/debugger-contexts.md) Vysvětluje, jak ladicí modul (DE) pracuje současně v kontextu kódování kódu, dokumentace a výrazu. Popisuje pro každý ze tří kontextů umístění, umístění nebo hodnocení, které jsou pro něj relevantní.

 [Ladění úkolů](../../extensibility/debugger/debugging-tasks.md) Obsahuje odkazy na různé úlohy ladění, jako je například spuštění programu a vyhodnocení výrazů.
