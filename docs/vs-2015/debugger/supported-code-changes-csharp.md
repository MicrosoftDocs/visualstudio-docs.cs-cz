---
title: Podporované změny kódu (C#) | Dokumentace Microsoftu
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
- Edit and Continue [C#], supported code changes
ms.assetid: c7a48ea9-5a7f-4328-a9d7-f0e76fac399d
caps.latest.revision: 30
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 1d028c35ea5d0f00dd8206fbfe0b086c9dbed067
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/16/2018
ms.locfileid: "51724658"
---
# <a name="supported-code-changes-c"></a>Podporované změny kódu (C#)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Upravit a pokračovat zpracovává většinu typů změn kódu uvnitř těla metody. Během ladění, ale nejde použít většinu změn mimo těl metod a několik změn v rámci těla metod. Nepodporované změny použít, musíte Zastavit ladění a znovu s novou verzi kódu.  
  
 Následující změny nejde použít u kódu jazyka C# během relace ladění:  
  
-   Změny aktuálního příkazu nebo jiné aktivní příkaz.  
  
     Aktivní příkazy zahrnout všechny příkazy, funkce v zásobníku volání, které byly volány zobrazíte aktuální příkaz.  
  
     Aktuální příkaz je označena žlutým pozadím v okně zdroje. Jiné aktivní příkazy jsou označené nástrojem pozadí označeno šedou barvou a jsou jen pro čtení. Tyto výchozí barvy lze změnit v **možnosti** dialogové okno.  
  
-   Změna podpisu typu.  
  
-   Přidání anonymní metody, který explicitně zaznamenává proměnnou, která se nezachytila dřív.  
  
-   Přidání, odebrání nebo změna atributů.  
  
-   Přidání, odebrání nebo změna `using` direktivy.  
  
-   Přidávání `foreach`, `using`, nebo `lock` kolem aktivního příkazu.  
  
## <a name="unsafe-code"></a>Nezabezpečený kód  
 Změny nezabezpečeného kódu obsahovat stejná omezení jako změny bezpečný kód, jeden další omezení: Upravit a pokračovat nepodporuje změny nebezpečný kód, který ukončí v rámci metody, která obsahuje `stackalloc` operátor.  
  
## <a name="exceptions"></a>Výjimky  
 Upravit a pokračovat podporuje změny `catch` a `finally` blokuje, s tím rozdílem, že přidáte `catch` nebo `finally` block kolem aktivního příkazu není povolený.  
  
## <a name="unsupported-scenarios"></a>Nepodporované scénáře  
 Upravit a pokračovat není k dispozici v následujících scénářích ladění:  
  
-   Ladění LINQ kódu za určitých okolností. Další informace najdete v tématu [ladění LINQ](../debugger/debugging-linq.md).  
  
    -   Zachycení proměnné, která se nezachytila dřív.  
  
    -   Změna typu výrazu dotazu (například vyberte a = > vyberte nový {A =};)  
  
    -   Odebrání `where` , který obsahuje aktivní příkaz.  
  
    -   Odebrání `let` , který obsahuje aktivní příkaz.  
  
    -   Odebrání `join` , který obsahuje aktivní příkaz.  
  
    -   Odebrání `orderby` , který obsahuje aktivní příkaz.  
  
-   Ladění ve smíšeném režimu (nativní a spravovaná).  
  
-   Ladění SQL.  
  
-   Ladění zotavení po havárii. Watson s výpisem paměti.  
  
-   Úprava kódu po neošetřené výjimky, když "**vrátit zásobník volání v případě neošetřených výjimek**" není vybraná možnost.  
  
-   Ladění aplikace vložený modul runtime.  
  
-   Ladění aplikace, která má **připojit k** místo spouštění aplikace výběrem **Start** z **ladění** nabídky.  
  
-   Ladění optimalizovaného kódu.  
  
-   Ladění starou verzi kódu po nové verze se nepovedlo sestavit kvůli chybám sestavení.  
  
## <a name="see-also"></a>Viz také  
 [Upravit a pokračovat (Visual C#)](../debugger/edit-and-continue-visual-csharp.md)   
 [Postupy: Použití operace Upravit a pokračovat (C#)](../debugger/how-to-use-edit-and-continue-csharp.md)



