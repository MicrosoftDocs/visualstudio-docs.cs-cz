---
title: 'Postupy: použití operace upravit a pokračovat (C#) | Dokumentace Microsoftu'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
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
manager: ghogen
ms.openlocfilehash: 4106a8bcaec8890192fdc33b9db0d66c12d8b07d
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/16/2018
ms.locfileid: "51789158"
---
# <a name="how-to-use-edit-and-continue-c"></a>Postupy: Použití operace Upravit a pokračovat (C#)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Pomocí funkce upravit a pokračovat pro jazyk C# můžete provést změny kódu v režimu pozastavení během ladění. Změny lze použít bez nutnosti zastavit a restartovat ladicí relaci.  
  
 Upravit a pokračovat je vyvolán automaticky, když změny v režimu pozastavení a pak zvolte možnost spuštění ladicího programu, jako příkaz **pokračovat**, **krok**, nebo **nastavit další příkaz**, nebo vyhodnotíte funkci v okně ladicího programu.  
  
> [!NOTE]
>  Upravit a pokračovat není podporovaná při ladění Compact Framework, optimalizovaného kódu, Smíšeného nativního/spravovaného kódu nebo systému SQL Server common language runtime (CLR) integrace kódu. Pokud se pokusíte použít kód změny v jednom z těchto scénářů, ladicí program umístí nahoru dialogové okno s vysvětlením, že funkce upravit a pokračovat není podporována.  
  
### <a name="to-invoke-edit-and-continue-automatically"></a>Vyvolání funkce upravit a pokračovat automaticky  
  
1.  V režimu pozastavení změňte zdrojový kód.  
  
2.  Z **ladění** nabídky, klikněte na tlačítko **pokračovat**, **krok**, nebo **nastavit další příkaz** nebo vyhodnotíte funkci v okně ladicího programu.  
  
     Nový kód je zkompilován a ladění pokračuje s novým kódem. Některé změny nejsou podporovány funkcemi upravit a pokračovat. Další informace najdete v tématu [podporované změny kódu (C#)](../debugger/supported-code-changes-csharp.md).  
  
### <a name="to-enabledisable-edit-and-continue"></a>Povolení nebo zakázání funkce upravit a pokračovat  
  
1.  Na **nástroje** nabídky, klikněte na tlačítko **možnosti**.  
  
2.  V **možnosti** dialogového okna rozbalte **ladění** uzel a vyberte možnost **upravit a pokračovat**.  
  
3.  V **možnosti** dialogové okno **upravit a pokračovat** stránce, zaškrtněte nebo zrušte zaškrtnutí **Povolit Editovat a pokračovat** zaškrtávací políčko.  
  
     Nastavení se projeví po restartování relace ladění.  
  
## <a name="see-also"></a>Viz také  
 [Upravit a pokračovat (Visual C#)](../debugger/edit-and-continue-visual-csharp.md)   
 [Podporované změny kódu (C#)](../debugger/supported-code-changes-csharp.md)   
 [Upravit a pokračovat chyby a upozornění (C#)](../misc/edit-and-continue-errors-and-warnings-csharp.md)



