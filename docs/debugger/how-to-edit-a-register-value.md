---
title: Jak upravit hodnotu registru | Microsoft Docs
ms.date: 11/04/2016
ms.topic: how-to
f1_keywords:
- vs.debug.register.edit
dev_langs:
- CSharp
- VB
- FSharp
- C++
- JScript
helpviewer_keywords:
- Registers window, editing register values
- register values
ms.assetid: e27b6bd8-e6d4-4f1d-8a86-9f4047bb1167
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 8f7a341fa3f8d41bf4788db5bb4b4957fd8cca81
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "85349819"
---
# <a name="how-to-edit-a-register-value-c-c-visual-basic-f"></a>Postupy: Úprava hodnoty registru (C#, C++, Visual Basic, F #)

Okno Registry je k dispozici pouze v případě, že je povoleno ladění na úrovni adresy v dialogovém okně **Možnosti** , uzel **ladění** .

### <a name="to-change-the-value-of-a-register"></a>Změna hodnoty registru

1. V okně **Registry** pomocí klávesy TAB nebo myši přesuňte kurzor na hodnotu, kterou chcete změnit. Když začnete psát, ukazatel se musí nacházet před hodnotou, kterou chcete přepsat.

2. Zadejte novou hodnotu.

    > [!CAUTION]
    > Změna hodnot registru (zejména v registrech EIP a EBP) může ovlivnit spuštění programu.

    > [!CAUTION]
    > Úpravy hodnot s plovoucí desetinnou čárkou mohou díky převodu komponenty zlomku z desítkové do binární soustavy způsobit drobné nepřesnosti. Dokonce i zdánlivě neškodného úpravy můžou mít za následek změny některých nejméně významných bitů v registru s plovoucí desetinnou čárkou.

## <a name="see-also"></a>Viz také
- [Postupy: Použití okna Registry](../debugger/how-to-use-the-registers-window.md)