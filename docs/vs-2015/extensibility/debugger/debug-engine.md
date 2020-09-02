---
title: Ladicí stroj | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- debug engines
ms.assetid: 148b1efc-ca07-4d8e-bdfc-c723a760c620
caps.latest.revision: 19
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 6e81a95cffebc9e26821b9cc6157627100343452
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "64807715"
---
# <a name="debug-engine"></a>Ladicí stroj
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Ladicí stroj (DE) spolupracuje s překladačem nebo operačním systémem, aby poskytoval služby ladění, jako je například řízení spouštění, zarážky a vyhodnocení výrazu. DE je zodpovědná za monitorování stavu programu, který se právě ladí. K tomuto účelu DE použije jakékoli metody, které jsou k dispozici v podporovaném modulu runtime, ať už z procesoru, nebo z rozhraní API dodaných modulem runtime.  
  
 Například modul CLR (Common Language Runtime) poskytuje mechanismy pro monitorování spuštěného programu prostřednictvím rozhraní ICorDebugXXX. DE, který podporuje modul CLR, používá odpovídající rozhraní ICorDebugXXX ke sledování laděného programu spravovaného kódu. Pak sdělí všechny změny stavu do Správce ladění relací (SDM), který předává tyto informace do [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] IDE.  
  
> [!NOTE]
> Ladicí stroj cílí na konkrétní modul runtime, tedy na systém, ve kterém se program laděně spouští. Modul CLR je modulem runtime pro spravovaný kód a modul runtime Win32 je pro nativní aplikace systému Windows. Pokud jazyk, který vytvoříte, může cílit na jeden z těchto dvou modulů runtime, [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] již jsou potřebné ladicí moduly. Vše, co musíte implementovat, je vyhodnocovací filtr výrazů.  
  
## <a name="debug-engine-operation"></a>Operace ladění stroje  
 Monitorovací služby jsou implementovány prostřednictvím rozhraní DE a mohou způsobit přechod ladicího balíčku mezi různými provozními režimy. Další informace najdete v tématu [provozní režimy](../../extensibility/debugger/operational-modes.md). Obvykle je k dispozici pouze jedna DE Implementation pro každé prostředí za běhu.  
  
> [!NOTE]
> I když existují samostatné DE implementací pro Transact-SQL a [!INCLUDE[jsprjscript](../../includes/jsprjscript-md.md)] VBScript a [!INCLUDE[jsprjscript](../../includes/jsprjscript-md.md)] sdílejí jeden de.  
  
 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] ladění umožňuje ladicím strojům spustit jeden ze dvou způsobů: buď ve stejném procesu jako [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] prostředí, nebo ve stejném procesu jako právě laděný cílový program. K druhému formuláři obvykle dochází v případě, že proces, který se právě ladí, je skript spuštěný v překladači a ladicí stroj musí mít Intimate znalosti interpreta, aby mohl skript monitorovat. Všimněte si, že v tomto případě je překladač skutečně modulem runtime; moduly ladění jsou určené pro konkrétní implementace modulu runtime. Kromě toho může být implementace jednoho DE rozdělena mezi hranice procesu a počítače (například vzdálené ladění).  
  
 DE zpřístupňuje [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] rozhraní ladění. Veškerá komunikace je prostřednictvím modelu COM. Bez ohledu na to, zda je DE načtena v procesu, mimo proces nebo na jiný počítač, nemá vliv na komunikaci součástí.  
  
 DE funguje s komponentou vyhodnocovacího filtru výrazů, která umožňuje nástroji DE pro konkrétní dobu běhu pochopit syntaxi výrazů. DE také spolupracuje s komponentou obslužné rutiny symbolů pro přístup k symbolickým ladicím informacím generovaným kompilátorem jazyka. Další informace najdete v tématu [vyhodnocovací filtr výrazů](../../extensibility/debugger/expression-evaluator.md) a [poskytovatel symbolů](../../extensibility/debugger/symbol-provider.md).  
  
## <a name="see-also"></a>Viz také  
 [Komponenty ladicího programu](../../extensibility/debugger/debugger-components.md)   
 [Vyhodnocení výrazu](../../extensibility/debugger/expression-evaluator.md)   
 [Poskytovatel symbolů](../../extensibility/debugger/symbol-provider.md)
