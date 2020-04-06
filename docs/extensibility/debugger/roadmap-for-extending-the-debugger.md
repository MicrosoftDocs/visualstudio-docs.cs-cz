---
title: Plán rozšíření ladicího programu | Dokumenty společnosti Microsoft
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
ms.openlocfilehash: e809eeb6a1a5d2c24368932713d69c7199b5af38
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80713136"
---
# <a name="roadmap-for-extending-the-debugger"></a>Plán rozšíření ladicího programu
Tato dokumentace obsahuje pokyny a referenční [!INCLUDE[vs_current_short](../../code-quality/includes/vs_current_short_md.md)] informace pro [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)]rozšíření ladicího programu s .

 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]dokumentace ladění obsahuje ukázky, komplexní odkaz a několik reprezentativních scénářů, které ukazují typické způsoby přizpůsobení ladicího programu.

 Kompilátor a jeho výstup určují, co je nutné nastavit ladění v produktu. Pokud váš kompilátor:

- Cílí na nativní operační systém Windows a zapíše *. Pdb,* můžete ladit programy s nativním kódem ladicí [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]modul (DE), který je integrován do . Není nutné implementovat DE nebo vyhodnocení výrazu. Vyhodnocení výrazu je napsáno pro syntaxi programovacího jazyka C++.

- Vytvoří výstup zprostředkujícího jazyka Společnosti Microsoft (MSIL), můžete ladit programy pomocí modulu [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]ladění spravovaného kódu DE, který je také integrován do . Proto stačí implementovat vyhodnocení výrazu. K dispozici je vyhodnocení ukázkového výrazu. Další informace najdete v následujících tématech:

   [Vyhodnocení výrazu](../../extensibility/debugger/expression-evaluation-visual-studio-debugging-sdk.md)

   [Vyhodnocení výrazů](../../extensibility/debugger/evaluating-expressions.md)

   [Kontext vyhodnocení výrazu](../../extensibility/debugger/expression-evaluation-context.md)

   [Vyhodnocení výrazu v režimu přerušení](../../extensibility/debugger/expression-evaluation-in-break-mode.md)

   [Napsat hodnotitel exprese běžného běhu runtime](../../extensibility/debugger/writing-a-common-language-runtime-expression-evaluator.md)

- Cíle proprietární operační systém nebo jiné run-time prostředí, musíte napsat vlastní DE. Kurz, který vytvoří jednoduchý DE pomocí ATL COM je k dispozici. Další informace najdete v následujících tématech:

   [Vytvoření vlastního ladicího stroje](../../extensibility/debugger/creating-a-custom-debug-engine.md)

   [Kurz: Sestavení ladicího modulu pomocí služby ATL COM](https://msdn.microsoft.com/library/9097b71e-1fe7-48f7-bc00-009e25940c24)

   [Implementace dodavatele portů](../../extensibility/debugger/implementing-a-port-supplier.md)

   [ukázky](../../extensibility/debugger/visual-studio-debugging-samples.md)

## <a name="see-also"></a>Viz také
- [Začínáme](../../extensibility/debugger/getting-started-with-debugger-extensibility.md)
