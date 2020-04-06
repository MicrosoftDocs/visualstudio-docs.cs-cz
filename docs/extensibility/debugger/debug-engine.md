---
title: Ladicí modul | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debug engines
ms.assetid: 148b1efc-ca07-4d8e-bdfc-c723a760c620
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: a4cb00796f8db23a43cd81a06d80d0fac40f075e
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80739062"
---
# <a name="debug-engine"></a>Ladicí modul
Ladicí modul (DE) pracuje s interpretem nebo operačním systémem a poskytuje ladicí služby, jako je řízení provádění, zarážky a vyhodnocení výrazu. De je zodpovědný za sledování stavu programu, který je laděn. Chcete-li to provést, DE používá jakékoli metody, které jsou k dispozici v podporovanémodulu runtime, ať už z procesoru nebo z rozhraní API dodané modulu runtime.

 Například modul CLR (COMMON Language runtime) poskytuje mechanismy pro sledování spuštěného programu prostřednictvím rozhraní ICorDebugXXX. De, který podporuje CLR používá příslušné rozhraní ICorDebugXXX sledovat program spravovaného kódu, který je laděn. Potom sdělí všechny změny stavu správce ladění relace (SDM), který předá tyto informace [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] ide.

> [!NOTE]
> Ladicí modul cílí na konkrétní modul runtime, tj. CLR je runtime pro spravovaný kód a win32 runtime je pro nativní aplikace systému Windows. Pokud jazyk, který vytvoříte můžete cílit [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] jeden z těchto dvou modulů runtimes, již dodává potřebné ladicí motory. Vše, co musíte implementovat, je vyhodnocení výrazu.

## <a name="debug-engine-operation"></a>Ladění provozu motoru
 Monitorovací služby jsou implementovány prostřednictvím rozhraní DE a může způsobit ladicí balíček pro přechod mezi různými provozními režimy. Další informace naleznete v [tématu Provozní režimy](../../extensibility/debugger/operational-modes.md). Obvykle existuje pouze jedna implementace DE pro prostředí za běhu.

> [!NOTE]
> Zatímco existují samostatné de implementace pro Transact-SQL [!INCLUDE[jsprjscript](../../debugger/debug-interface-access/includes/jsprjscript_md.md)]a [!INCLUDE[jsprjscript](../../debugger/debug-interface-access/includes/jsprjscript_md.md)] , VBScript a sdílet jeden DE.

 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]ladění umožňuje ladění motorů spustit jedním ze dvou způsobů: buď ve [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] stejném procesu jako prostředí, nebo ve stejném procesu jako cílový program, který je laděn. Druhá forma obvykle dochází, když proces, který je laděn je ve skutečnosti skript spuštěný pod interpret. Ladicí modul musí mít důvěrné znalosti interpreta, aby bylo možné sledovat skript. V tomto případě je interpret ve skutečnosti runtime; ladicí moduly jsou pro konkrétní implementace modulu runtime. Kromě toho implementace jednoho DE lze rozdělit mezi hranice procesu a počítače (například vzdálené ladění).

 DE zpřístupňuje [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] ladění rozhraní. Veškerá komunikace probíhá prostřednictvím com. Zda je de načten v procesu, mimo proces nebo v jiném počítači, nemá vliv na komunikaci součástí.

 DE pracuje s komponentou vyhodnocení výrazu, aby DE pro daný běh ový čas pochopil syntaxi výrazů. DE také pracuje s komponentou obslužné rutiny symbolu pro přístup k informacím o symbolickéladění generované kompilátorem jazyka. Další informace naleznete v [tématu Vyhodnocení výrazu](../../extensibility/debugger/expression-evaluator.md) a [zprostředkovatel symbol .](../../extensibility/debugger/symbol-provider.md)

## <a name="see-also"></a>Viz také
- [Součásti ladicího programu](../../extensibility/debugger/debugger-components.md)
- [Vyhodnocení výrazu](../../extensibility/debugger/expression-evaluator.md)
- [Poskytovatel symbolů](../../extensibility/debugger/symbol-provider.md)
