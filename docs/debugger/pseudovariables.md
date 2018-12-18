---
title: Pseudovariables | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- Watch window, pseudovariables
- debugging [Visual Studio], pseudovariables
- pseudovariables
ms.assetid: fae84f68-2138-4144-9bd4-c9e271b6182a
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: af106709ca578abeab19c4f474548476efbeea57
ms.sourcegitcommit: 0bf2aff6abe485e3fe940f5344a62a885ad7f44e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/27/2018
ms.locfileid: "37057682"
---
# <a name="pseudovariables-in-the-visual-studio-debugger"></a>Pseudovariables v ladicím programu sady Visual Studio
Pseudovariables jsou podmínky, které slouží k zobrazení určité informace v okně proměnná nebo **QuickWatch** dialogové okno. Můžete zadat pseudovariable stejným způsobem, zadali byste normální proměnné. Pseudovariables není proměnné, ale a nemusí odpovídat názvy proměnných v programu.  
  
## <a name="example"></a>Příklad  
 Předpokládejme, že jsou psaní nativního kódu aplikace a chcete si prohlédnout počet popisovačů přidělené ve vaší aplikaci. V **sledovat** okně můžete zadat následující pseudovariable v **název** sloupec a poté stiskněte klávesu vrátit se k vyhodnocení:  
  
`$handles`
  
 V nativním kódu můžete použít pseudovariables uvedené v této tabulce:  
  
|Pseudovariable|Funkce|  
|--------------------|--------------|  
|`$err`|Zobrazí poslední chybovou hodnotu nastavit pomocí funkce SetLastError. Hodnota, která se zobrazí představuje, co by měla vrátit GetLastError funkce.<br /><br /> Použití `$err,hr` zobrazíte dekódované formu tuto hodnotu. Pokud byla chyba poslední 3, například `$err,hr` by zobrazení `ERROR_PATH_NOT_FOUND : The system cannot find the path specified.`|  
|`$handles`|Zobrazí počet popisovačů přidělené ve vaší aplikaci.|  
|`$vframe`|Zobrazí adresu aktuální rámec zásobníku.|  
|`$tid`|Zobrazí ID vlákna pro aktuální vlákno.|  
|`$env`|Zobrazí blok prostředí v prohlížeči řetězec.|  
|`$cmdline`|Zobrazí řetězec příkazového řádku, který spustí program.|  
|`$pid`|Zobrazí id procesu.|  
|`$` *registername*<br /><br /> or<br /><br /> `@` *registername*|Zobrazí obsah registru *registername*.<br /><br /> Za normálních okolností můžete zobrazit obsah registrace právě zadáním názvu registrace. Je třeba tuto syntaxi používají je pouze při registraci názvu přetížení název proměnné. Pokud název registrace je stejný jako název proměnné v aktuálním oboru, ladicího programu název interpretovat jako název proměnné. Když se `$` *registername* nebo `@` *registername* hodit.|  
|`$clk`|Zobrazí čas v hodinových cyklů.|  
|`$user`|Zobrazí struktura s informací o účtu pro účet spuštění aplikace. Z bezpečnostních důvodů se nezobrazí, informace o hesle.|  
|`$exceptionstack`|Zobrazí trasování zásobníku aktuální výjimky prostředí Windows Runtime. `$ exceptionstack` funguje pouze v aplikacích pro UPW. `$ exceptionstack` není podporováno pro C++ a SEH výjimky|  
|`$ReturnValue`|Zobrazí návratovou hodnotu metody rozhraní .NET Framework.|  
  
 V jazyce C# a Visual Basic můžete použít pseudovariables uvedené v této tabulce:  
  
|Pseudovariable|Funkce|  
|--------------------|--------------|  
|`$exception`|Zobrazí informace o poslední výjimka. Pokud žádná výjimka došlo, vyhodnocení `$exception` zobrazí chybovou zprávu.<br /><br /> V jazyce Visual C#, pokud je zakázáno Pomocníka pro výjimky, `$exception` se automaticky přidá do **místní hodnoty –** okno, když dojde k výjimce.|  
|`$user`|Zobrazí struktura s informací o účtu pro účet spuštění aplikace. Z bezpečnostních důvodů se nezobrazí, informace o hesle.|  
  
 V jazyce Visual Basic můžete použít pseudovariables uvedené v následující tabulce:  
  
|Pseudovariable|Funkce|  
|--------------------|--------------|  
|`$delete` nebo `$$delete`|Odstraní implicitní proměnné, který byl vytvořen v **Immediate** okno. Syntaxe je `$delete,` *proměnná* nebo`$delete,` *proměnné*`.`|  
|`$objectids` nebo `$listobjectids`|Zobrazí všechny aktivní ID objektů jako podřízené objekty, z určeného výrazu. Syntaxe je `$objectid,` *výraz* nebo`$listobjectids,` *výraz*`.`|  
|`$` *N* `#`|Zobrazí objekt s ID objektu rovna *N*.|  
|`$dynamic`|Zobrazí speciální **dynamického zobrazení** uzel pro objekt, který implementuje `IDynamicMetaObjectProvider`. rozhraní. Syntaxe je `$dynamic,` *objekt*. Tato funkce se vztahuje pouze na kód, který používá rozhraní .NET Framework verze 4.|  
  
## <a name="see-also"></a>Viz také  
 [Sledování a QuickWatch Windows](../debugger/watch-and-quickwatch-windows.md)   
 [Okna proměnných](../debugger/debugger-windows.md)