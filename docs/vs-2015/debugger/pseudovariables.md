---
title: Pseudoproměnné | Dokumentace Microsoftu
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
- Watch window, pseudovariables
- debugging [Visual Studio], pseudovariables
- pseudovariables
ms.assetid: fae84f68-2138-4144-9bd4-c9e271b6182a
caps.latest.revision: 40
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 79d2f47acfbd5a4b6adf6d5f679fb3b514679dab
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/16/2018
ms.locfileid: "51789496"
---
# <a name="pseudovariables"></a>Pseudoproměnné
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Pseudoproměnné jsou podmínky, které slouží k zobrazení určitých informací v okně proměnné nebo **QuickWatch** dialogové okno. Pseudoproměnnou můžete zadat stejným způsobem, zadali byste jako běžné proměnné. Pseudoproměnné nejsou proměnné, ale a nemusí odpovídat názvům proměnných v programu.  
  
## <a name="example"></a>Příklad  
 Předpokládejme, že píšete aplikaci v nativním kódu a chcete zjistit počet popisovačů přidělených v aplikaci. V **Watch** okna, můžete zadat následující pseudoproměnnou **název** sloupce, poté stiskem klávesy ENTER ji vyhodnotit:  
  
```  
$handles  
```  
  
 V nativním kódu můžete použít pseudoproměnné uvedené v této tabulce:  
  
|Pseudoproměnnou|Funkce|  
|--------------------|--------------|  
|`$err`|Zobrazí poslední chybovou hodnotu nastavenou pomocí funkce SetLastError. Zobrazená hodnota představuje, co by vrátila Funkce GetLastError.<br /><br /> Použití `$err,hr` Chcete-li zobrazit dekódovanou formu této hodnoty. Například, pokud byla poslední chyba 3 `$err,hr` zobrazí `ERROR_PATH_NOT_FOUND : The system cannot find the path specified.`|  
|`$handles`|Zobrazí počet popisovačů přidělených v aplikaci.|  
|`$vframe`|Zobrazí adresu aktuální rámec zásobníku.|  
|`$tid`|Zobrazí identifikátor ID vlákna pro aktuální vlákno.|  
|`$env`|Zobrazí zadaný blok prostředí v prohlížeči řetězce.|  
|`$cmdline`|Zobrazí řetězec příkazového řádku, který spustil program.|  
|`$pid`|Zobrazuje id procesu.|  
|`$` *registername –*<br /><br /> or<br /><br /> `@` *registername –*|Zobrazí obsah registru *registername –*.<br /><br /> Obsah registru za normálních okolností lze zobrazit pouze zadáním názvu registru. Je třeba použít tuto syntaxi se pouze když název registru přetíží název proměnné. Pokud název registru je stejný jako název proměnné v aktuálním oboru, ladicí program interpretuje název jako název proměnné. Právě to `$` *registername –* nebo `@` *registername –* se hodí.|  
|`$clk`|Zobrazí čas v hodinových cyklech.|  
|`$user`|Zobrazí se struktura s informacemi o účtu pro účet, který spouští aplikaci. Z bezpečnostních důvodů nejsou informace heslu zobrazeny.|  
|`$exceptionstack`|Zobrazí trasování zásobníku aktuální výjimky prostředí Windows Runtime. `$ exceptionstack` funguje pouze v aplikacích pro Store, které jsou v systému Windows 8.1 nebo novějším. `$ exceptionstack` není podporováno pro výjimky C++ a SHE|  
|`$ReturnValue`|Zobrazuje hodnotu vrácenou metody rozhraní .NET Framework. Zobrazit [Kontrola návratových hodnot volání metod](http://msdn.microsoft.com/library/e3245b37-8e2e-4200-ba84-133726e95f1f)|  
  
 V jazyce C# a Visual Basic můžete použít pseudoproměnné uvedené v této tabulce:  
  
|Pseudoproměnnou|Funkce|  
|--------------------|--------------|  
|`$exception`|Zobrazí informace o poslední výjimce. Pokud k žádné výjimce, hodnocení `$exception` zobrazí chybovou zprávu.<br /><br /> V jazyce Visual C#, zakázán Pomocník pro výjimky, `$exception` se automaticky přidá do **lokální** okno, když dojde k výjimce.|  
|`$user`|Zobrazí se struktura s informacemi o účtu pro účet, který spouští aplikaci. Z bezpečnostních důvodů nejsou informace heslu zobrazeny.|  
  
 V jazyce Visual Basic můžete použít pseudoproměnné uvedené v následující tabulce:  
  
|Pseudoproměnnou|Funkce|  
|--------------------|--------------|  
|`$delete` Nebo `$$delete`|Odstraní implicitní proměnné, který byl vytvořen v **okamžité** okna. Syntaxe je `$delete,` *proměnnou* nebo`$delete,` *proměnné*`.`|  
|`$objectids` Nebo `$listobjectids`|Zobrazí všechny aktivní ID objektů jako podřízené položky, z určeného výrazu. Syntaxe je `$objectid,` *výraz* nebo`$listobjectids,` *výraz*`.`|  
|`$` *N* `#`|Zobrazí objekt s ID objektu rovna *N*.|  
|`$dynamic`|Zobrazí zvláštní **dynamického zobrazení** uzlu pro objekt, který implementuje `IDynamicMetaObjectProvider`. rozhraní. Syntaxe je `$dynamic,` *objekt*. Tato funkce se vztahuje pouze na kód, který používá rozhraní .NET Framework verze 4. Zobrazit [dynamického zobrazení](http://msdn.microsoft.com/library/4c851b17-2c12-46a0-9828-eb6ea6f5c563).|  
  
## <a name="see-also"></a>Viz také  
 [Kukátko a Rychlé kukátko Windows](../debugger/watch-and-quickwatch-windows.md)   
 [Proměnné Windows](http://msdn.microsoft.com/library/ce0a67f6-2502-4b7a-ba45-cc32f8aeba3e)





