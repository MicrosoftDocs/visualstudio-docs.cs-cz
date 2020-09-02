---
title: Výběr strategie implementace ladicího modulu | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debug engines, implementation strategies
ms.assetid: 90458fdd-2d34-4f10-82dc-6d8f31b66d8b
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 05e66975a2d41108d3d9fb469da9e4a36a10d8d2
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "80739124"
---
# <a name="choose-a-debug-engine-implementation-strategy"></a>Zvolit strategii implementace ladicího modulu
Pomocí architektury za běhu určete strategii implementace ladicího modulu (DE). Ladicí modul můžete vytvořit v procesu do programu, který ladíte. Vytvořte ladicí modul v procesu do programu Správce ladění relací sady Visual Studio (SDM). Nebo můžete vytvořit ladicí modul mimo proces pro oba. Následující pokyny vám pomohou vybrat si z těchto tří strategií.

## <a name="guidelines"></a>Pokyny
 I když je možné, že DE by byl proces pro SDM i pro program, který ladíte, neexistuje žádný důvod. Volání napříč hranicemi procesů jsou poměrně pomalá.

 Moduly ladění jsou již k dispozici pro prostředí Win32 Native runtime a pro prostředí programu Common Language Runtime. Pokud je nutné nahradit DE pro každé prostředí, měli byste vytvořit DE in-Process s modelem SDM.

 V opačném případě buď vytvořte v rámci procesu, který ladíte, do modelu SDM nebo v procesu proces. Musíte zvážit, jestli vyhodnocení výrazu DE vyžaduje častý přístup k úložišti symbolů programu. Nebo, pokud úložiště symbolů lze načíst do paměti pro rychlý přístup. Vezměte v úvahu také následující přístupy:

- Pokud mezi vyhodnocovacím filtrem výrazů a úložištěm symbolů neexistují žádná volání, nebo pokud lze úložiště symbolů načíst do paměťového prostoru SDM, vytvořte v procesu SDM proces DE in-Process. Je nutné, abyste při připojení k vašemu programu vrátili CLSID ladicího stroje do modelu SDM. Model SDM používá tento identifikátor CLSID k vytvoření instance v procesu DE.

- Pokud DE musí volat program pro přístup k úložišti symbolů, vytvořte v programu příkaz DE in-Process. V tomto případě program vytvoří instanci DE.

## <a name="see-also"></a>Viz také
- [Rozšiřitelnost ladicího programu sady Visual Studio](../../extensibility/debugger/visual-studio-debugger-extensibility.md)
