---
title: Plán pro rozšíření ladicího programu | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], roadmap
- Debugging SDK, roadmap
ms.assetid: 1f4096a8-f7aa-4dfa-84e1-6d59263e70bb
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 7527d142b27e5b49bcf133429dc232614bad04a2
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/23/2018
ms.locfileid: "49942670"
---
# <a name="roadmap-for-extending-the-debugger"></a>Plán pro rozšíření ladicího programu
Tato dokumentace obsahuje průvodce a referenční informace k rozšíření [!INCLUDE[vs_current_short](../../code-quality/includes/vs_current_short_md.md)] ladicí program se [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)].  
  
 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] ladění dokumentace obsahuje ukázky, komplexní referenční informace a několik reprezentativní scénářů, které ukazují obvyklé způsoby přizpůsobení ladicí program.  
  
 Kompilátor a její výstup zjistit, co je potřeba k nastavení ladění produktu. Pokud váš kompilátor:  
  
- Cílí na nativní operační systém Windows a zapíše *. Soubor PDB* soubor, můžete ladit programy s modul ladění nativního kódu (DE), která je součástí [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]. Není nutné implementovat DE nebo výraz Chyba při vyhodnocování. Chyba při vyhodnocování výrazu je určené pro syntaxi programovací jazyk C++.  
  
- Vytvoří Microsoft intermediate language (MSIL) výstup, můžete ladit programy s modul ladění spravovaného kódu DE, která je také součástí [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]. Proto potřebujete pouze implementace vyhodnocovače výrazů. Vyhodnocovací filtr výrazů ukázka poskytuje za vás. Další informace naleznete v následujících tématech:  
  
   [Vyhodnocení výrazu](../../extensibility/debugger/expression-evaluation-visual-studio-debugging-sdk.md)  
  
   [Vyhodnocování výrazů](../../extensibility/debugger/evaluating-expressions.md)  
  
   [Kontext vyhodnocení výrazu](../../extensibility/debugger/expression-evaluation-context.md)  
  
   [Vyhodnocení výrazu v režimu pozastavení](../../extensibility/debugger/expression-evaluation-in-break-mode.md)  
  
   [Zápis běžné vyhodnocovač výrazů modulu runtime jazyka](../../extensibility/debugger/writing-a-common-language-runtime-expression-evaluator.md)  
  
- Cíle a nechráněný operačního systému nebo jiné běhové prostředí, budete muset napsat vlastní DE. Kurz, který vytvoří jednoduchý DE pomocí knihovny ATL modelu COM je k dispozici. Další informace naleznete v následujících tématech:  
  
   [Vytvoření vlastního ladicího stroje](../../extensibility/debugger/creating-a-custom-debug-engine.md)  
  
   [Kurz: Vytvoření ladicího stroje pomocí knihovny ATL modelu COM](https://msdn.microsoft.com/library/9097b71e-1fe7-48f7-bc00-009e25940c24)  
  
   [Implementace dodavatele portu](../../extensibility/debugger/implementing-a-port-supplier.md)  
  
   [Ukázky](../../extensibility/debugger/visual-studio-debugging-samples.md)  
  
## <a name="see-also"></a>Viz také:  
 [Začínáme](../../extensibility/debugger/getting-started-with-debugger-extensibility.md)