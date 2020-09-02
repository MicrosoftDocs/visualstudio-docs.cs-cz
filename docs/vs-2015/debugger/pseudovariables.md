---
title: Pseudoproměnné | Microsoft Docs
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
- Watch window, pseudovariables
- debugging [Visual Studio], pseudovariables
- pseudovariables
ms.assetid: fae84f68-2138-4144-9bd4-c9e271b6182a
caps.latest.revision: 40
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: e9ce72d69cb64b0421771324803a785546fa884f
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "65693755"
---
# <a name="pseudovariables"></a>Pseudoproměnné
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Pseudoproměnné jsou výrazy používané k zobrazení určitých informací v okně proměnných nebo v dialogovém okně **QuickWatch** . Pseudoproměnnou můžete zadat stejným způsobem, jako byste zadali normální proměnnou. Pseudoproměnné nejsou proměnné, ale neodpovídají názvům proměnných v programu.  
  
## <a name="example"></a>Příklad  
 Předpokládejme, že píšete aplikaci nativního kódu a chcete zobrazit počet popisovačů přidělených ve vaší aplikaci. V okně **kukátko** můžete do sloupce **název** zadat následující pseudoproměnnou a pak ho vyhodnotit stisknutím klávesy ENTER:  
  
```  
$handles  
```  
  
 V nativním kódu můžete použít Pseudoproměnné uvedené v této tabulce:  
  
|Pseudoproměnnou|Funkce|  
|--------------------|--------------|  
|`$err`|Zobrazí poslední chybovou hodnotu nastavenou funkcí SetLastError. Zobrazená hodnota představuje to, co by Funkce GetLastError vrátila.<br /><br /> Slouží `$err,hr` k zobrazení Dekódovatelné formy této hodnoty. Pokud například poslední chyba byla 3, `$err,hr` zobrazí se `ERROR_PATH_NOT_FOUND : The system cannot find the path specified.`|  
|`$handles`|Zobrazuje počet popisovačů přidělených ve vaší aplikaci.|  
|`$vframe`|Zobrazí adresu aktuálního rámce zásobníku.|  
|`$tid`|Zobrazuje ID vlákna pro aktuální vlákno.|  
|`$env`|Zobrazí blok prostředí v prohlížeči řetězců.|  
|`$cmdline`|Zobrazí řetězec příkazového řádku, který spustil program.|  
|`$pid`|Zobrazí ID procesu.|  
|`$`*registrace*<br /><br /> nebo<br /><br /> `@`*registrace*|Zobrazí *obsah registru Register.*<br /><br /> V normálním případě lze obsah registru zobrazit pouze zadáním názvu registru. Jedinou dobu, kterou potřebujete použít k použití této syntaxe, je, když název registru převede název proměnné. Pokud je název registru stejný jako název proměnné v aktuálním oboru, ladicí program interpretuje název jako název proměnné. To je v případě, že se nachází `$` v *registru Register* nebo `@` *Register* .|  
|`$clk`|Zobrazí čas v časovém cyklu.|  
|`$user`|Zobrazí strukturu s informacemi o účtu pro účet, na kterém je aplikace spuštěná. Z bezpečnostních důvodů se nezobrazuje informace o hesle.|  
|`$exceptionstack`|Zobrazí trasování zásobníku aktuální výjimky prostředí Windows Runtime. `$ exceptionstack` funguje jenom v aplikacích pro Store, které běží na Windows 8.1 nebo novějším. `$ exceptionstack` není podporováno pro výjimky jazyka C++ a.|  
|`$ReturnValue`|Zobrazuje návratovou hodnotu metody .NET Framework. Viz [Kontrola návratových hodnot volání metod](https://msdn.microsoft.com/library/e3245b37-8e2e-4200-ba84-133726e95f1f) .|  
  
 V jazyce C# a Visual Basic můžete použít Pseudoproměnné uvedené v této tabulce:  
  
|Pseudoproměnnou|Funkce|  
|--------------------|--------------|  
|`$exception`|Zobrazí informace o poslední výjimce. Pokud nedojde k žádné výjimce, vyhodnotí se `$exception` zobrazí chybová zpráva.<br /><br /> Pouze v jazyce Visual C#, pokud je zakázán pomocník výjimek, `$exception` je automaticky přidán do okna **místní** hodnoty, pokud dojde k výjimce.|  
|`$user`|Zobrazí strukturu s informacemi o účtu pro účet, na kterém je aplikace spuštěná. Z bezpečnostních důvodů se nezobrazuje informace o hesle.|  
  
 V Visual Basic můžete použít Pseudoproměnné uvedené v následující tabulce:  
  
|Pseudoproměnnou|Funkce|  
|--------------------|--------------|  
|`$delete` nebo `$$delete`|Odstraní implicitní proměnnou, která byla vytvořena v **příkazovém** okně. Syntaxe je `$delete,` *Proměnná* nebo `$delete,` *Proměnná* .`.`|  
|`$objectids` nebo `$listobjectids`|Zobrazí všechna aktivní ID objektů jako podřízené objekty určeného výrazu. Syntaxe je `$objectid,` *výraz* nebo `$listobjectids,` *výraz* .`.`|  
|`$` *N* `#`|Zobrazí objekt s ID objektu větším než *N*.|  
|`$dynamic`|Zobrazí speciální uzel **dynamického zobrazení** pro objekt, který implementuje rozhraní `IDynamicMetaObjectProvider` . Prostředí. Syntaxe je `$dynamic,` *Object*. Tato funkce se vztahuje pouze na kód, který používá .NET Framework verze 4. Viz [dynamické zobrazení](https://msdn.microsoft.com/library/4c851b17-2c12-46a0-9828-eb6ea6f5c563).|  
  
## <a name="see-also"></a>Viz také  
 [Kukátko a QuickWatch okna](../debugger/watch-and-quickwatch-windows.md)   
 [Okna proměnných](https://msdn.microsoft.com/library/ce0a67f6-2502-4b7a-ba45-cc32f8aeba3e)
