---
title: Podporované změny kódu (C#) | Microsoft Docs
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
- Edit and Continue [C#], supported code changes
ms.assetid: c7a48ea9-5a7f-4328-a9d7-f0e76fac399d
caps.latest.revision: 30
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 6fc02c11a4ebceea431fc06a1bd1cfdb1063097d
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "67823542"
---
# <a name="supported-code-changes-c"></a>Podporované změny kódu (C#)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Upravit a pokračovat zpracovává většinu typů změn kódu v rámci těla metody. Většina změn mimo tělo metody a několik změn v rámci těla metod nelze použít během ladění. Chcete-li použít tyto nepodporované změny, je nutné zastavit ladění a restartovat s novou verzí kódu.  
  
 Následující změny nelze použít na kód jazyka C# během relace ladění:  
  
- Změny aktuálního příkazu nebo jakéhokoli jiného aktivního příkazu.  
  
     Aktivní příkazy zahrnují všechny příkazy ve funkcích v zásobníku volání, které byly volány pro získání na aktuální příkaz.  
  
     Aktuální příkaz je označen žlutým pozadím v okně zdroje. Další aktivní příkazy jsou označeny šedým pozadím a jsou jen pro čtení. Tyto výchozí barvy lze změnit v dialogovém okně **Možnosti** .  
  
- Změna podpisu typu.  
  
- Přidání anonymní metody, která zachytává proměnnou, která nebyla zachycena před.  
  
- Přidávání, odebírání a změna atributů.  
  
- Přidání, odebrání nebo změna `using` direktiv.  
  
- Přidání `foreach` , `using` nebo `lock` kolem aktivního příkazu.  
  
## <a name="unsafe-code"></a>Nezabezpečený kód  
 Změny v nebezpečném kódu mají stejná omezení jako změny v bezpečném kódu s jedním dalším omezením: příkaz Upravit a pokračovat nepodporuje změny nezabezpečeného kódu, který ukončuje v rámci metody, která obsahuje `stackalloc` operátor.  
  
## <a name="exceptions"></a>Výjimky  
 Příkaz Upravit a pokračovat podporuje změny `catch` `finally` v blocích a. s tím rozdílem, že přidávání `catch` nebo `finally` blokování kolem aktivního příkazu není povoleno.  
  
## <a name="unsupported-scenarios"></a>Nepodporované scénáře  
 Úpravy a pokračování nejsou k dispozici v následujících scénářích ladění:  
  
- Ladění kódu LINQ za určitých okolností. Další informace naleznete v tématu [Ladění LINQ](../debugger/debugging-linq.md).  
  
  - Zachycení proměnné, která nebyla zachycena před.  

  - Mění se typ výrazu dotazu (např. Vyberte a => vyberte nový {A = a};)  

  - Odebrání typu `where` , který obsahuje aktivní příkaz.  

  - Odebrání typu `let` , který obsahuje aktivní příkaz.  

  - Odebrání typu `join` , který obsahuje aktivní příkaz.  

  - Odebrání objektu `orderby` , který obsahuje aktivní příkaz.  
  
- Ladění ve smíšeném režimu (nativní/spravované)  
  
- Ladění SQL.  
  
- Ladění výpisu nástroje Dr. Watson.  
  
- Úprava kódu po neošetřené výjimce v případě, že není vybrána možnost "**unwind zásobníku volání v neošetřených výjimkách**".  
  
- Ladění vložené aplikace modulu runtime.  
  
- Ladění aplikace, která se **připojí k** místo spuštění aplikace, pomocí příkazu **Start** z nabídky **ladění** .  
  
- Ladění optimalizovaného kódu.  
  
- Ladění staré verze kódu po neúspěšném sestavení nové verze z důvodu chyb sestavení.  
  
## <a name="see-also"></a>Viz také  
 [Upravit a pokračovat (Visual C#)](../debugger/edit-and-continue-visual-csharp.md)   
 [Postupy: Použití operace Upravit a pokračovat (C#)](../debugger/how-to-use-edit-and-continue-csharp.md)
