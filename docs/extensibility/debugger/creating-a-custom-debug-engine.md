---
title: Vytvoření vlastního ladicího stroje | Microsoft Docs
description: Pomocí těchto článků se dozvíte, jak vytvořit ladicí stroj, který umožňuje ladit konkrétní architektury run-time.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- debug engines, implementing
- debug engines, custom
- debugging [Debugging SDK], custom debug engines
ms.assetid: 52794238-6fae-451c-bf1c-99f344c6f173
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: ef2a477a3a5027d7989c88a71d42b091cc69fbae
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/25/2021
ms.locfileid: "105067954"
---
# <a name="create-a-custom-debug-engine"></a>Vytvoření vlastního ladicího stroje
Ladicí stroj (DE) je komponenta, která umožňuje ladění konkrétní architektury run-time. Obvykle je k dispozici pouze jedna DE Implementation pro každé prostředí za běhu.

> [!NOTE]
> I když existují samostatné DE implementací pro Transact-SQL a JScript, VBScript a JScript sdílí jeden DE.

 DE funguje s překladačem nebo operačním systémem pro poskytování takových služeb ladění jako řízení spouštění, zarážky a vyhodnocení výrazu. Tyto služby jsou implementovány prostřednictvím rozhraní DE a mohou způsobit přechod ladicího programu mezi různými provozními režimy. Další informace najdete v tématu [provozní režimy](../../extensibility/debugger/operational-modes.md).

 Vytváření DE se skládá z následujících kroků:

1. Registrace DE se sadou Visual Studio

2. Povolit ladění programu

3. Implementovat řízení provádění a vyhodnocení stavu

4. Odesílání událostí

5. Nastavení ukončení a odpojení

## <a name="in-this-section"></a>V této části
 [Registrace vlastního ladicího stroje](../../extensibility/debugger/registering-a-custom-debug-engine.md) Vysvětluje kroky potřebné k registraci ladicího stroje se sadou Visual Studio, aby jej bylo možné použít.

 [Povolit ladění programu](../../extensibility/debugger/enabling-a-program-to-be-debugged.md) Vysvětluje, že před tím, než může příkaz DE ladit program, je třeba nejprve spustit příkaz DE nebo ho připojit k existujícímu programu.

 [Implementovat řízení provádění a vyhodnocení stavu](../../extensibility/debugger/execution-control-and-state-evaluation.md) Popisuje, proč ladění aplikace vyžaduje implementaci funkcí řízení spouštění.

 [Odeslat události](../../extensibility/debugger/sending-events.md) Popisuje komunikaci mezi ladicím programem a DE jako modelem události na základě modelu DCOM.

 [Nastavení ukončení a odpojení](../../extensibility/debugger/termination-and-detaching.md) Vysvětluje, jak dosáhnout normálního ukončení, což znamená, že neexistují žádné zarážky, výjimky, chyby za běhu nebo nekonečné smyčky v aplikaci, která se má ladit.

 [Události ladicího programu volání](../../extensibility/debugger/calling-debugger-events.md) Dokumentuje pořadí volání událostí, ke kterým došlo v relaci ladění.

 [Postupy: ladění vlastního ladicího stroje](../../extensibility/debugger/how-to-debug-a-custom-debug-engine.md) Vysvětluje, jak ladit vlastní DE.

## <a name="see-also"></a>Viz také
- [Rozšiřitelnost ladicího programu sady Visual Studio](../../extensibility/debugger/visual-studio-debugger-extensibility.md)
