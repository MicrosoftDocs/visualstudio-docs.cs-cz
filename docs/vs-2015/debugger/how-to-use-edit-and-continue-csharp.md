---
title: 'Postupy: použití funkce upravit a pokračovat (C#) | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- Edit and Continue [C#], about Edit and Continue
ms.assetid: 40e136d8-a08c-43bd-b313-fb821c55eb3c
caps.latest.revision: 22
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 39137d5fe60a3c91c8fd3904e797eb83420a8f5d
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "64807204"
---
# <a name="how-to-use-edit-and-continue-c"></a>Postupy: Použití operace Upravit a pokračovat (C#)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Při úpravách a pokračování pro jazyk C# můžete provádět změny kódu v režimu pozastavení při ladění. Změny lze použít bez nutnosti zastavit a znovu spustit ladicí relaci.  
  
 Funkce upravit a pokračovat je vyvolána automaticky, když provedete změny v režimu pozastavení, pak zvolíte příkaz pro spuštění ladicího programu, například **pokračovat**, **Krok**nebo **nastavit další příkaz**, nebo vyhodnotit funkci v okně ladicího programu.  
  
> [!NOTE]
> Příkaz Upravit a pokračovat není podporován při ladění kompaktního rozhraní, optimalizovaného kódu, smíšeného nativního/spravovaného kódu nebo SQL Server kódu integrace modulu CLR (Common Language Runtime). Pokud se pokusíte použít změny kódu v jednom z těchto scénářů, ladicí program vloží dialogové okno s vysvětlením, že příkaz Upravit a pokračovat není podporován.  
  
### <a name="to-invoke-edit-and-continue-automatically"></a>Automatické vyvolání úpravy a pokračování  
  
1. V režimu pozastavení proveďte změnu zdrojového kódu.  
  
2. V nabídce **ladění** klikněte na možnost **pokračovat**, **Krok**nebo **nastavit další příkaz** nebo vyhodnotit funkci v okně ladicího programu.  
  
     Nový kód je zkompilován a ladění pokračuje s novým kódem. V části Upravit a pokračovat nejsou podporovány některé změny. Další informace naleznete v tématu [podporované změny kódu (C#)](../debugger/supported-code-changes-csharp.md).  
  
### <a name="to-enabledisable-edit-and-continue"></a>Povolení nebo zakázání úprav a pokračování  
  
1. V nabídce **Tools** (Nástroje) klikněte na **Options** (Možnosti).  
  
2. V dialogovém okně **Možnosti** rozbalte uzel **ladění** a vyberte možnost **Upravit a pokračovat**.  
  
3. V dialogovém okně **Možnosti** pro **úpravu a pokračování** zaškrtněte nebo zrušte zaškrtnutí políčka **Povolit úpravy a pokračování** .  
  
     Nastavení se projeví po restartování ladicí relace.  
  
## <a name="see-also"></a>Viz také  
 [Upravit a pokračovat (Visual C#)](../debugger/edit-and-continue-visual-csharp.md)   
 [Podporované změny kódu (C#)](../debugger/supported-code-changes-csharp.md)   
 [Chyby a upozornění operace Upravit a pokračovat (C#)](../misc/edit-and-continue-errors-and-warnings-csharp.md)
