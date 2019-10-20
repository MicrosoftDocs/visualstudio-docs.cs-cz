---
title: 'Postupy: zákaz procesu hostování | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
helpviewer_keywords:
- hosting process, disabling
- vshost.exe, disabling the hosting process
ms.assetid: 9157488d-737f-454b-8d8d-36f99de38bb0
caps.latest.revision: 12
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 95dcd7da113bfe996d00e617b7c8e2f9b68864d7
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/19/2019
ms.locfileid: "72667977"
---
# <a name="how-to-disable-the-hosting-process"></a>Postupy: Zákaz procesu hostování
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Je-li povolen hostitelský proces, mohou být volání určitých rozhraní API ovlivněna. V těchto případech je pro vrácení správných výsledků nutné hostitelský proces zakázat.

### <a name="to-disable-the-hosting-process"></a>Zakázání hostitelského procesu

1. Otevřete projekt spustitelné aplikace v aplikaci [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]. Projekty, které nevytváří spustitelné soubory (například knihovny tříd nebo projekty služeb) tuto možnost nemají.

2. V nabídce **projekt** klikněte na příkaz **vlastnosti**.

3. Klikněte na kartu **ladění** .

4. Zrušte zaškrtnutí políčka **Povolit hostující proces sady Visual Studio** .

   Je-li hostitelský proces zakázán, nebudou k dispozici některé funkce pro ladění nebo může dojít k poklesu výkonu. Další informace naleznete v tématu [ladění a hostující proces](../debugger/debugging-and-the-hosting-process.md).

   Obecně, pokud je hostitelský proces zakázán, platí:

- Čas potřebný ke spuštění ladění aplikací [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] se zvýší.

- Vyhodnocení výrazu v době návrhu není k dispozici.

- Ladění v částečném vztahu důvěryhodnosti není k dispozici.

## <a name="see-also"></a>Viz také
 [Ladění a hostující](../debugger/debugging-and-the-hosting-process.md) proces [hostování procesu (vshost. exe)](../ide/hosting-process-vshost-exe.md) [během vývoje aplikace](https://msdn.microsoft.com/c9497d62-3b7b-4449-88e8-cf27acc9efe6)
