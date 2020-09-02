---
title: Ladění modelu COM a ActiveX | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.debug.com
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- COM, debugging
- debugging ActiveX applications
- debugging [Visual Studio], COM
- debugging COM containers
- ActiveX controls, debugging
ms.assetid: 3260b2a7-3239-493d-9271-aedf705c13c7
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 0a818cfde2996b26bd9d5f31b128e41f2a9fe2e1
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "73188679"
---
# <a name="com-and-activex-debugging"></a>Ladění modelů COM a prvků ActiveX
V této části najdete tipy pro ladění aplikací modelu COM a ovládacích prvků ActiveX.

## <a name="in-this-section"></a>V tomto oddílu
 [Ladění serveru a kontejneru modelu COM](../debugger/com-server-and-container-debugging.md) Zmiňuje zvláštní požadavky při ladění aplikací modelu COM. Problémy zahrnují: ladění serveru COM a kontejneru pomocí dvou projektů v rámci stejného řešení, trasování do volání, která přecházejí mezi hranicemi procesů, nastavení zarážek ve funkcích zpětného volání a krokování napříč a do kontejnerů a serverů.

 [Postupy: ladění ovládacího prvku ActiveX](../debugger/how-to-debug-an-activex-control.md) Obsahuje informace o ladění ovládacích prvků ActiveX. To zahrnuje: zadání kontejneru pro relaci ladění, abyste viděli, jak se kód v ovládacím prvku ActiveX spustí, když se zahájí ladění ovládacího prvku ActiveX vázaného na data, simulace konkrétního kontejneru a krokování do kódu kontejneru.

 [Nástroje pro ladění modelu COM](../debugger/com-debugging-tools.md) Zobrazí seznam prohlížečů a ukázkových aplikací, které mohou být užitečné při ladění aplikace modelu COM.

## <a name="related-sections"></a>Související oddíly
 [První pohled na ladicí program](../debugger/debugger-feature-tour.md) Obsahuje odkazy na větší části dokumentace ladění. Informace zahrnují: co je nového v ladicím programu, nastavení a přípravu, zarážky, zpracování výjimek, úpravy a pokračování, ladění spravovaného kódu, ladění projektů C++, ladění modelu COM a ActiveX, ladění knihoven DLL, ladění SQL a odkazy na uživatelské rozhraní.

## <a name="see-also"></a>Viz také

- [Zabezpečení ladicího programu](../debugger/debugger-security.md)
- [Úvod do modelu COM](/cpp/atl/introduction-to-com)
- [Ovládací prvky ActiveX](/cpp/mfc/activex-controls)
- [Aplikace serveru SDI](com-server-and-container-debugging.md)