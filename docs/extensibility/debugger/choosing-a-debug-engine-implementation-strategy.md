---
title: Výběr strategie implementace ladicího modulu | Dokumenty společnosti Microsoft
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
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80739124"
---
# <a name="choose-a-debug-engine-implementation-strategy"></a>Zvolte strategii implementace ladicího modulu
Pomocí architektury za běhu určete strategii implementace ladicího modulu (DE). Můžete vytvořit ladicí modul v procesu do programu, který ladíte. Vytvořte ladicí modul v procesu do správce ladění relace sady Visual Studio (SDM). Nebo vytvořte ladicí modul mimo proces pro oba. Následující pokyny by vám měly pomoci vybrat si z těchto tří strategií.

## <a name="guidelines"></a>Pokyny
 I když je možné, aby DE být mimo proces pro sdm a program, který ladíte, obvykle není žádný důvod, aby tak učinily. Volání přes hranice procesu jsou relativně pomalé.

 Ladicí moduly jsou již k dispozici pro prostředí nativní ho dioda win32 a pro prostředí běžný jazyk run-time. Pokud máte nahradit DE pro obě prostředí, měli byste vytvořit DE v procesu s SDM.

 V opačném případě vytvoříte de v procesu s SDM nebo v procesu do programu, který ladíte. Budete muset zvážit, pokud vyhodnocení výrazu DE vyžaduje častý přístup k úložišti symbolů programu. Nebo pokud úložiště symbolů lze načíst do paměti pro rychlý přístup. Zvažte také následující přístupy:

- Pokud není mnoho volání mezi vyhodnocení výrazu a úložiště symbolů, nebo pokud úložiště symbolů lze číst do paměťového prostoru SDM, vytvořte DE v procesu SDM. Je nutné vrátit CLSID ladicí modul s SDM při připojení k programu. SDM používá tento CLSID k vytvoření instancí de v procesu.

- Pokud DE musí volat program pro přístup k úložišti symbolů, vytvořte DE v procesu s programem. V tomto případě program vytvoří instanci DE.

## <a name="see-also"></a>Viz také
- [Rozšiřitelnost ladicího programu visual studio](../../extensibility/debugger/visual-studio-debugger-extensibility.md)
