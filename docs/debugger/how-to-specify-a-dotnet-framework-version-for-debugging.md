---
title: Určení verze rozhraní .NET Framework pro ladění | Dokumentace Microsoftu
ms.custom: seodec18
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- .NET Framework, specifying version for debugging
- debugging [Visual Studio], specifying .NET Framework version
ms.assetid: 7a4893ba-4620-4774-893f-378d4ca28893
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- dotnet
ms.openlocfilehash: 86289c9a93a0bb9e0f7756443d79f4a1a6dd38a6
ms.sourcegitcommit: 708f77071c73c95d212645b00fa943d45d35361b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/07/2018
ms.locfileid: "53056005"
---
# <a name="how-to-specify-a-net-framework-version-for-debugging-c-visual-basic-f"></a>Postupy: určení verze rozhraní .NET Framework pro ladění (C#, Visual Basic, F#)

Ladicí program sady Visual Studio podporuje ladění starších verzích Microsoft [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] stejně jako aktuální verze. Pokud spouštíte aplikaci ze sady Visual Studio, ladicí program může vždy identifikovat správnou verzi [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] pro aplikaci, kterou ladíte. Nicméně pokud aplikace je již spuštěn a spustit ladění pomocí **připojit k**, ladicí program, nemusí být vždy schopen identifikovat starší verzi [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)]. Pokud k tomu dojde, zobrazí se chybová zpráva s upozorněním,  

``` cmd 
The debugger has made an incorrect assumption about the [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] version your application is going to use.  
```

Ve výjimečných případech, kde se zobrazí tato chyba můžete nastavit klíče registru k označení k ladicímu programu, které verze se má použít.  
  
### <a name="to-specify-a-net-framework-version-for-debugging"></a>Chcete-li určit verzi rozhraní .NET Framework pro ladění  
  
1. Hledejte v adresáři Windows\Microsoft.NET\Framework vyhledání verzí rozhraní .NET Framework nainstalované v počítači. Čísla verzí vypadat přibližně takto:  
  
    `V1.1.4322`  
  
    Identifikujte na správné číslo verze a poznamenejte si ho.  
  
2. Spustit **Editor registru** (regedit).  
  
3. V **Editor registru**, otevřete složku HKEY_LOCAL_MACHINE.  
  
4. Přejděte do: HKEY_LOCAL_MACHINE\Software\Microsoft\VisualStudio\10.0\AD7Metrics\Engine\\{449EC4CC-30D2-4032-9256-EE18EB41B62B}  
  
    Pokud klíč neexistuje, klikněte pravým tlačítkem na HKEY_LOCAL_MACHINE\Software\Microsoft\VisualStudio\10.0\AD7Metrics\Engine a klikněte na tlačítko **nový klíč**. Pojmenujte nový klíč `{449EC4CC-30D2-4032-9256-EE18EB41B62B}`.  
  
5. Po přejití do {449EC4CC-30D2-4032-9256-EE18EB41B62B}, podívejte se **název** sloupce a najít CLRVersionForDebugging klíč.  
  
   1.  Pokud klíč neexistuje, klikněte pravým tlačítkem na {449EC4CC-30D2-4032-9256-EE18EB41B62B} a klikněte na tlačítko **novou řetězcovou hodnotu**. Klikněte pravým tlačítkem na novou řetězcovou hodnotu, klikněte na tlačítko **přejmenovat**a typ `CLRVersionForDebugging`.  
  
6. Dvakrát klikněte na panel **CLRVersionForDebugging**.  
  
7. V **Upravit řetězec** zadejte číslo verze rozhraní .NET Framework v **hodnotu** pole. Příklad: V1.1.4322  
  
8. Klikněte na tlačítko **OK**.  
  
9. Zavřít **Editor registru**.  
  
     Pokud se stále zobrazí chybová zpráva při zahájení ladění, ověřte, že zadáte číslo verze správně v registru. Dál ověřte, že používáte verzi [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] podporovaného Visual Studiem. Ladicí program je kompatibilní s aktuální verze rozhraní .NET Framework a předchozími verzemi, ale možná není dopředně kompatibilní s budoucí verze.  
  
## <a name="see-also"></a>Viz také  
 [Nastavení a příprava ladicího programu](../debugger/debugger-settings-and-preparation.md)