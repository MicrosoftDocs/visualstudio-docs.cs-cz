---
title: Plán pro rozšíření ladicího programu | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], roadmap
- Debugging SDK, roadmap
ms.assetid: 1f4096a8-f7aa-4dfa-84e1-6d59263e70bb
caps.latest.revision: 17
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 89a07bc5a5c4c8b7a6054b53610325c654355bc8
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "65695962"
---
# <a name="roadmap-for-extending-the-debugger"></a>Plán pro rozšíření ladicího programu
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Tato dokumentace poskytuje návod a referenční informace pro rozšíření [!INCLUDE[vs_current_short](../../includes/vs-current-short-md.md)] ladicího programu pomocí nástroje [!INCLUDE[vsipsdk](../../includes/vsipsdk-md.md)] .  
  
 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] dokumentace k ladění obsahuje ukázky, ucelený odkaz a několik reprezentativních scénářů, které ukazují typický způsob přizpůsobení ladicího programu.  
  
 Kompilátor a jeho výstup určují, co je potřeba k implementaci ladění v produktu. Pokud váš kompilátor:  
  
- Cílí na nativní operační systém Windows a zapisuje a. Soubor PDB, můžete ladit programy pomocí modulu ladění nativního kódu (DE), který je integrován do [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] . Není nutné implementovat filtr DE nebo Expression. Vyhodnocovací filtr výrazů je napsán pro syntaxi programovacího jazyka C++.  
  
- Vytváří výstup jazyka MSIL (Microsoft Intermediate Language), můžete ladit programy pomocí spravovaného modulu ladění kódu DE, který je také integrován do [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] . Proto potřebujete pouze implementovat vyhodnocení výrazu. K dispozici je vyhodnocení ukázkového výrazu. Další informace najdete v následujících tématech:  
  
     [Vyhodnocení výrazu](../../extensibility/debugger/expression-evaluation-visual-studio-debugging-sdk.md)  
  
     [Vyhodnocování výrazů](../../extensibility/debugger/evaluating-expressions.md)  
  
     [Kontext vyhodnocení výrazu](../../extensibility/debugger/expression-evaluation-context.md)  
  
     [Vyhodnocení výrazu v režimu přerušení](../../extensibility/debugger/expression-evaluation-in-break-mode.md)  
  
     [Zápis vyhodnocovače výrazů modulu CLR](../../extensibility/debugger/writing-a-common-language-runtime-expression-evaluator.md)  
  
- Cílí na speciální operační systém nebo jiné prostředí za běhu, musíte napsat vlastní DE. K dispozici je kurz, který vytvoří jednoduchý DE using ATL COM. Další informace najdete v následujících tématech:  
  
     [Vytvoření vlastního ladicího stroje](../../extensibility/debugger/creating-a-custom-debug-engine.md)  
  
     [Kurz: sestavení ladicího stroje pomocí ATL COM](https://msdn.microsoft.com/9097b71e-1fe7-48f7-bc00-009e25940c24)  
  
     [Implementace dodavatele portu](../../extensibility/debugger/implementing-a-port-supplier.md)  
  
     [ukázky](../../extensibility/debugger/visual-studio-debugging-samples.md)  
  
## <a name="see-also"></a>Viz také  
 [Začínáme](../../extensibility/debugger/getting-started-with-debugger-extensibility.md)
