---
title: Ladění a proces hostování | Microsoft Docs
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
- debugging [Visual Studio], hosting process
- hosting process
ms.assetid: d0f0b9a6-2a6e-463d-b6ea-9518ee727933
caps.latest.revision: 13
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 10f3968367b188203671fa6bfff48bc482efe4f7
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "68157900"
---
# <a name="debugging-and-the-hosting-process"></a>Ladění a proces hostování
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Proces hostování sady Visual Studio vylepšuje výkon ladicího programu a umožňuje nové funkce ladicího programu, jako je například ladění částečného vztahu důvěryhodnosti a vyhodnocení výrazu v době návrhu. V případě potřeby můžete hostitelský proces zakázat. Další informace naleznete v tématu [How to: Disable a hosting Process](../ide/how-to-disable-the-hosting-process.md). Následující části popisují některé rozdíly mezi laděním s a bez hostujícího procesu.  
  
## <a name="partial-trust-debugging-and-click-once-security"></a>Ladění s částečným vztahem důvěryhodnosti a zabezpečení po kliknutí  
 Ladění s částečným vztahem důvěryhodnosti vyžaduje hostující proces. Pokud zakážete hostující proces, ladění s částečným vztahem důvěryhodnosti nebude fungovat ani v případě, že je na stránce **zabezpečení** **vlastností projektu**povoleno zabezpečení s částečnou důvěryhodností. Další informace naleznete v tématu [How to: Disable a proces hostování](../ide/how-to-disable-the-hosting-process.md) a [Postup: ladění aplikace s částečnou důvěryhodností](../debugger/how-to-debug-a-partial-trust-application.md).  
  
## <a name="design-time-expression-evaluation"></a>Vyhodnocení výrazu pro dobu návrhu  
 Výraz při návrhu vždy používá hostitelský proces. Zakázání hostitelského procesu ve **vlastnostech projektu** zakáže vyhodnocení výrazu v době návrhu pro projekty knihovny tříd. Pro jiné typy projektů není vyhodnocení výrazu v době návrhu zakázáno. Místo toho Visual Studio spustí skutečný spustitelný soubor a použije ho pro vyhodnocení v době návrhu bez hostujícího procesu. Tento rozdíl může způsobit odlišné výsledky.  
  
## <a name="appdomaincurrentdomainfriendlyname-differences"></a>Rozdíly v AppDomain. CurrentDomain. FriendlyName  
 `AppDomain.CurrentDomain.FriendlyName` vrátí různé výsledky v závislosti na tom, zda je povolen hostitelský proces. Pokud zavoláte `AppDomain.CurrentDomain.FriendlyName` s povoleným hostitelským procesem, vrátí *APP_NAME* `.vhost.exe` . Pokud je zavoláte, je hostitelský proces zakázán, vrátí *APP_NAME* `.exe` .  
  
## <a name="assemblygetcallingassemblyfullname-differences"></a>Assembly. GetCallingAssembly (). Nafullname rozdíly  
 `Assembly.GetCallingAssembly().FullName` vrátí různé výsledky v závislosti na tom, zda je povolen hostitelský proces. Pokud zavoláte `Assembly.GetCallingAssembly().FullName` s povoleným hostitelským procesem, vrátí se `mscorlib` . Pokud zavoláte `Assembly.GetCallingAssembly().FullName` se zakázaným hostitelským procesem, vrátí název aplikace.  
  
## <a name="see-also"></a>Viz také  
 [Hostitelský proces (vshost.exe)](../ide/hosting-process-vshost-exe.md)   
 [Postupy: ladění aplikace s částečnou důvěryhodností](../debugger/how-to-debug-a-partial-trust-application.md)   
 [Postupy: Zákaz procesu hostování](../ide/how-to-disable-the-hosting-process.md)
