---
title: Plán pro rozšíření ladicího programu | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], roadmap
- Debugging SDK, roadmap
ms.assetid: 1f4096a8-f7aa-4dfa-84e1-6d59263e70bb
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 9d97a7edd62540d12a0a60d15b3179ca0a623c26
ms.sourcegitcommit: 4b29efeb3a5f05888422417c4ee236e07197fb94
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/11/2020
ms.locfileid: "90011824"
---
# <a name="roadmap-for-extending-the-debugger"></a>Plán pro rozšíření ladicího programu
Tato dokumentace poskytuje návod a referenční informace pro rozšíření [!INCLUDE[vs_current_short](../../code-quality/includes/vs_current_short_md.md)] ladicího programu pomocí nástroje [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)] .

 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] dokumentace k ladění obsahuje ukázky, ucelený odkaz a několik reprezentativních scénářů, které ukazují typický způsob přizpůsobení ladicího programu.

 Kompilátor a jeho výstup určují, co je potřeba k nastavení ladění v produktu. Pokud váš kompilátor:

- Cílí na nativní operační systém Windows a zapisuje a *. Soubor PDB* , můžete ladit programy pomocí modulu ladění nativního kódu (de), který je integrován do [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] . Není nutné implementovat filtr DE nebo Expression. Vyhodnocovací filtr výrazů je napsán pro syntaxi programovacího jazyka C++.

- Vytváří výstup jazyka MSIL (Microsoft Intermediate Language), můžete ladit programy pomocí spravovaného modulu ladění kódu DE, který je také integrován do [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] . Proto potřebujete pouze implementovat vyhodnocení výrazu. K dispozici je vyhodnocení ukázkového výrazu. Další informace najdete v následujících tématech:

   [Vyhodnocení výrazu](../../extensibility/debugger/expression-evaluation-visual-studio-debugging-sdk.md)

   [Vyhodnocení výrazů](../../extensibility/debugger/evaluating-expressions.md)

   [Kontext vyhodnocení výrazu](../../extensibility/debugger/expression-evaluation-context.md)

   [Vyhodnocení výrazu v režimu přerušení](../../extensibility/debugger/expression-evaluation-in-break-mode.md)

   [Napsání vyhodnocovacího filtru výrazů společného jazykového modulu runtime](../../extensibility/debugger/writing-a-common-language-runtime-expression-evaluator.md)

- Cílí na speciální operační systém nebo jiné prostředí za běhu, musíte napsat vlastní DE. K dispozici je kurz, který vytvoří jednoduchý DE using ATL COM. Další informace najdete v následujících tématech:

   [Vytvoření vlastního ladicího stroje](../../extensibility/debugger/creating-a-custom-debug-engine.md)

   [Kurz: sestavení ladicího stroje pomocí ATL COM](/previous-versions/bb147024(v=vs.90))

   [Implementace dodavatele portu](../../extensibility/debugger/implementing-a-port-supplier.md)

   [ukázky](../../extensibility/debugger/visual-studio-debugging-samples.md)

## <a name="see-also"></a>Viz také:
- [Začínáme](../../extensibility/debugger/getting-started-with-debugger-extensibility.md)