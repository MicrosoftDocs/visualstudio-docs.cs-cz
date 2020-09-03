---
title: Jak použít příkaz Upravit a pokračovat (C#) | Microsoft Docs
ms.date: 10/04/2018
ms.topic: how-to
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- Edit and Continue [C#], about Edit and Continue
ms.assetid: 40e136d8-a08c-43bd-b313-fb821c55eb3c
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: a88cff54679ac0deae32bfeeff1dd96526f19ea7
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "85348857"
---
# <a name="how-to-use-edit-and-continue-c"></a>Postupy: Použití operace Upravit a pokračovat (C#)
Pomocí příkaz Upravit a pokračovat můžete provést a použít změny kódu v režimu pozastavení během ladění, aniž by bylo nutné zastavit a znovu spustit ladicí relaci.

Příkaz Upravit a pokračovat pro jazyk C# proběhne automaticky, když provedete změny kódu v režimu pozastavení, potom budete pokračovat v ladění pomocí příkazu **pokračovat**, **Krokovat**nebo **nastavit další příkaz**nebo vyhodnotit funkci v okně ladicího programu.

Další informace naleznete v tématu [Upravit a pokračovat (Visual C#)](../debugger/edit-and-continue-visual-csharp.md).

>[!NOTE]
>Příkaz Upravit a pokračovat není podporován pro optimalizovaný, smíšený nebo SQL Server kód pro integraci modulu CLR (Common Language Runtime). Informace o jiných nepodporovaných scénářích najdete v tématu [podporované změny kódu (C# a Visual Basic)](../debugger/supported-code-changes-csharp.md). Pokud se pokusíte upravit a pokračovat v jednom z těchto scénářů, zobrazí se okno se zprávou oznamující, že příkaz Upravit a pokračovat není podporován.

**Povolení nebo zakázání akce upravit a pokračovat:**

1. Pokud se nacházíte v relaci ladění, zastavte ladění (**ladění**  >  **zastaví ladění** nebo **SHIFT** + **F5**).

1. V **Tools**  >  **možnostech** nástrojů (nebo **Debug**  >  **Možnosti**ladění) > **Debugging**  >  **Obecné**ladění zaškrtněte nebo zrušte zaškrtnutí políčka **Povolit úpravy a pokračování** .

Nastavení se projeví při spuštění nebo opětovném spuštění relace ladění.

**Použití akce upravit a pokračovat:**

1. Během ladění v režimu pozastavení proveďte změnu zdrojového kódu.

1. V nabídce **ladění** klikněte na možnost **pokračovat**, **Krok**, nebo **nastavit další příkaz**nebo vyhodnoťte funkci v okně ladicího programu.

   Ladění pokračuje s novým kompilovaným kódem.

Některé typy změn kódu nejsou podporovány úpravou a pokračováním. Další informace najdete v tématu [podporované změny kódu (C# a Visual Basic)](../debugger/supported-code-changes-csharp.md).
