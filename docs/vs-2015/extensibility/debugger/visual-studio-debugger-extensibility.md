---
title: Rozšiřitelnost ladicího programu sady Visual Studio | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- debugging [Visual Studio], Debugging SDK
- Debugging SDK
ms.assetid: c088b6a2-c3ad-446b-830d-9c6f41b2934b
caps.latest.revision: 33
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 8b5e9e7a3db38b5138f6392ff89f3a3bb4a13303
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/16/2018
ms.locfileid: "51743499"
---
# <a name="visual-studio-debugger-extensibility"></a>Rozšiřitelnost programu Visual Studio Debugger
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Visual Studio obsahuje ladicí program kód plně interaktivní zdroje, poskytuje efektivní a snadno použitelné nástroje pro sledování chyby v kódu ve svém programu. Ladicí program má úplnou podporu jazyka Visual Basic, C#, C/C++ a JavaScript. Nicméně s [!INCLUDE[vsipsdk](../../includes/vsipsdk-md.md)], která je k dispozici [Microsoft Download Center](http://go.microsoft.com/fwlink/?LinkId=214453),, jiných programovacích jazycích může být podporovaný v ladicím programu pomocí stejné bohaté funkce.  
  
 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] Ladicí program pro ladění součásti, které se následně specifické pro jazyk, který se právě ladí běžné front-endu (to znamená, uživatelského rozhraní). Pro nové jazyky, všechny, které je nezbytné pro podporu podle [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] ladicí program je vytvoření potřebné komponenty back-end, jako je například ladicí stroj (DE). Tady [!INCLUDE[vsipsdk](../../includes/vsipsdk-md.md)] je k dispozici ve.  
  
 [!INCLUDE[vsipsdk](../../includes/vsipsdk-md.md)] Zahrnuje úplný odkaz na všechny [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] prvky potřebný k vytvoření nové DE. Kromě toho existují ukázek a kurzů, které vám pomůžou vám pomůžou začít.  
  
 Začátku do konce vzorku systému projektu jazyka s podporu ladění, najdete v článku [IronPython ukázkové](http://msdn.microsoft.com/en-us/4c41695c-12c1-4670-b43b-d8d84c9e4089).  
  
 Následující části popisují, jak rozšířit pomocí ladicího programu [!INCLUDE[vsipsdk](../../includes/vsipsdk-md.md)].  
  
## <a name="in-this-section"></a>V tomto oddílu  
 [Začínáme](../../extensibility/debugger/getting-started-with-debugger-extensibility.md)  
 Popisuje, co [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] ladění nabídky a způsobu jejich instalace sady SDK.  
  
 [Vytvoření vlastního ladicího stroje](../../extensibility/debugger/creating-a-custom-debug-engine.md)  
 Vlastní proces DE od přípravy programu pro Německo do odpojení DE dokumenty.  
  
 [Zápis pro vyhodnocovač výrazů modulu CLR](../../extensibility/debugger/writing-a-common-language-runtime-expression-evaluator.md)  
 Vysvětluje, zda je nutné napsat vyhodnocovače výrazů.  
  
 [Výběr strategie implementace ladicího stroje](../../extensibility/debugger/choosing-a-debug-engine-implementation-strategy.md)  
 Popisuje, jak implementovat vaše DE.  
  
 [Referenční informace](../../extensibility/debugger/reference/reference-visual-studio-debugging-apis.md)  
 Dokumenty [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] ladění v rozhraní API.  
  
 [Ukázky](../../extensibility/debugger/visual-studio-debugging-samples.md)  
 Obsahuje odkazy na ukázky Chyba při vyhodnocování výrazu modulu runtime běžné jazyka a ukázku ladicí stroj.

