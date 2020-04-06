---
title: Vytvoření vlastního ladicího modulu | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debug engines, implementing
- debug engines, custom
- debugging [Debugging SDK], custom debug engines
ms.assetid: 52794238-6fae-451c-bf1c-99f344c6f173
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: a350d640fffcc6e09cf8f981c797b97071a0cacf
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80739038"
---
# <a name="create-a-custom-debug-engine"></a>Vytvoření vlastního ladicího stroje
Ladicí modul (DE) je součást, která umožňuje ladění konkrétních architektur za běhu. Obvykle existuje pouze jedna implementace DE pro prostředí za běhu.

> [!NOTE]
> Zatímco existují samostatné de implementace pro Transact-SQL a JScript, VBScript a JScript sdílejí jeden DE.

 De spolupracuje s interpretu nebo operačního systému poskytovat takové ladicí služby jako řízení provádění, zarážky a vyhodnocení výrazu. Tyto služby jsou implementovány prostřednictvím rozhraní DE a může způsobit ladicí program přechodu mezi různými provozními režimy. Další informace naleznete v [tématu Provozní režimy](../../extensibility/debugger/operational-modes.md).

 Vytvoření DE se skládá z následujících kroků:

1. Registrace DE v sadě Visual Studio

2. Povolení odlažení programu

3. Implementace řízení provádění a vyhodnocení stavu

4. Odesílání událostí

5. Nastavit ukončení a odpojení

## <a name="in-this-section"></a>V tomto oddílu
 [Registrace vlastního ladicího stroje](../../extensibility/debugger/registering-a-custom-debug-engine.md) Vysvětluje kroky potřebné k registraci ladicí modul s Visual Studio tak, aby jej lze použít.

 [Povolení odlažení programu](../../extensibility/debugger/enabling-a-program-to-be-debugged.md) Vysvětluje, že předtím, než de můžete ladit program, musíte nejprve spustit DE nebo jej připojit k existujícímu programu.

 [Implementace řízení provádění a vyhodnocení stavu](../../extensibility/debugger/execution-control-and-state-evaluation.md) Popisuje, proč ladění aplikace vyžaduje implementaci funkcí řízení spuštění.

 [Odeslat události](../../extensibility/debugger/sending-events.md) Popisuje komunikaci mezi ladicím programem a DE jako model událostí založený na modelu DCOM.

 [Nastavit ukončení a odpojení](../../extensibility/debugger/termination-and-detaching.md) Vysvětluje, jak dosáhnout normální ukončení, což znamená, že neexistují žádné zarážky, výjimky, chyby za běhu nebo nekonečné smyčky v aplikaci, která má být laděna.

 [Volání událostí ladicího programu](../../extensibility/debugger/calling-debugger-events.md) Dokumentuje pořadí volání událostí, ke kterým dochází v relaci ladění.

 [Postup: Ladění vlastního ladicího modulu](../../extensibility/debugger/how-to-debug-a-custom-debug-engine.md) Vysvětluje, jak ladit vlastní DE.

## <a name="see-also"></a>Viz také
- [Rozšiřitelnost ladicího programu visual studio](../../extensibility/debugger/visual-studio-debugger-extensibility.md)
