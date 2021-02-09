---
title: Dialogové okno vybrat typ kódu | Microsoft Docs
description: Seznamte se s dialogovým oknem vybrat typ kódu v aplikaci Visual Studio. Chcete-li otevřít toto dialogové okno, otevřete dialogové okno připojit k procesu a pak klikněte na tlačítko vybrat.
ms.custom: SEO-VS-2020
ms.date: 06/12/2020
ms.topic: reference
f1_keywords:
- vs.debug.selectengines
dev_langs:
- CSharp
- VB
- FSharp
- C++
- JScript
- SQL
helpviewer_keywords:
- debugging [Visual Studio], engine selection
- debugger, engine selection
- debugging engine selection dialog box
no-loc:
- Blazor WebAssembly
ms.assetid: 932269fe-94e3-43cb-8931-078f31afd177
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 7fb7b7625e8e08e291f4f27606d03f9066828e0a
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99903487"
---
# <a name="select-code-type-dialog-box"></a>Dialogové okno Vybrat typ kódu

Chcete-li otevřít toto dialogové okno, otevřete dialogové okno **připojit k procesu** a pak klikněte na tlačítko **Vybrat** .

**Automaticky určit typ kódu pro ladění** Příslušný ladicí program se vybere na základě druhu kódu, na kterém je spuštěný.

**Ladit tyto typy kódu:** Z poskytnutého seznamu vyberte typ (typy) kódu, který chcete ladit. To může být užitečné při [řešení potíží s nezdařeným připojením](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md#BKMK_Troubleshoot_attach_errors). Tato možnost omezuje detekci pouze na typy kódu, které chcete ladit.

::: moniker range=">=vs-2019"
- Blazor WebAssembly – Na straně klienta Blazor WebAssembly
- GPU – software pro emulátor – kód C++ běžící na emulátoru softwaru GPU
- JavaScript (Chrome) – JavaScript běžící v Chrome
- JavaScript (Microsoft Edge-chrom) – JavaScript běžící v Microsoft Edge na bázi Chromu pro Windows 10
- Ladicí program JavaScriptu CDP (V3) – DevTools Protocol verze 3, který se používá pro ladění v klientovi CDP
- Spravované (CoreCLR) – .NET Core
- Spravované (nativní kompilace) – kód C++/CLR
- Managed (v 3.5, v 3.0, v 2.0) – kód .NET Framework pro .NET Framework 2,0 a vyšší (až 3,5)
- Spravované (v. 4.6, v 4.5, v 4.0) – kód .NET Framework .NET Framework 4,0 a vyšší
- Nativní – C/C++
- Node.js ladění – kód hostovaný modulem runtime Node.js
- Python – Python 
- Skript – určuje obecný ladicí program skriptu pro JavaScript. Použijte více omezující možnosti, pokud se vztahují na váš scénář, jako je například JavaScript (Chrome).
- T-SQL-Transact-SQL
- Unity – Unity
- Spravovaný režim kompatibility – určuje starší ladicí program pro spravovaný kód, který se obvykle používá pro ladění ve smíšeném režimu s C++/CLR Code (umožňuje upravit a pokračovat pro smíšený režim) nebo pro podporu rozšíření, která cílí na starší verzi ladicího programu. Ve většině scénářů ladění ve smíšeném režimu vyberte **nativní** a odpovídající typy **spravovaných** kódů místo spravovaného režimu kompatibility.
::: moniker-end

Ve většině scénářů není podporováno připojení více ladicích programů ve stejné relaci ladění. To lze provést pomocí druhé instance aplikace Visual Studio.

## <a name="see-also"></a>Viz také
- [Zabezpečení ladicího programu](../debugger/debugger-security.md)
- [Připojení ke spuštěným procesům](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md)
