---
title: 'Postupy: ladění výjimek ASP.NET | Microsoft Docs'
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
- debugging [Visual Studio], ASP.NET exceptions
- ASP.NET, exceptions
- exceptions, ASP.NET
ms.assetid: 1810096e-de8c-435e-be3d-f365d0cd0a6a
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- aspnet
ms.openlocfilehash: 5923818e93170ded1f857ac20d42cd6134aed5d3
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2018
ms.locfileid: "31476153"
---
# <a name="how-to-debug-aspnet-exceptions"></a>Postupy: Ladění výjimek ASP.NET
Ladění výjimek, je důležitou součástí vývoje robustní [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] aplikace. Obecné informace o tom, jak ladit výjimky je v [Správa výjimek pomocí ladicího programu](../debugger/managing-exceptions-with-the-debugger.md).  
  
 Chcete-li ladit neošetřená [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] výjimky, ujistěte se, že pro ně zastaví ladicí program. [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] Runtime má obslužná rutina výjimky nejvyšší úrovně. Proto ladicího programu nikdy dělí na neošetřených výjimek ve výchozím nastavení. Pokud chcete rozdělit na ladicí program, když je vyvolána výjimka, je nutné vybrat **přerušení po výjimku: vyvolána** nastavení pro tuto konkrétní výjimka v **výjimky** dialogové okno.  
  
 Pokud jste povolili pouze můj kód **přerušení po výjimku: vyvolána** nezpůsobí ladicí program na přerušení okamžitě, pokud je vyvolána výjimka v metodě rozhraní .NET Framework nebo jiný kód systému. Místo toho provádění pokračuje, dokud není ladicího programu dotkne nesystémové kód, pak to naruší. Výsledkem je, že nemáte ke kroku prostřednictvím kódu systému, když dojde k výjimce.  
  
 Pouze můj kód vám dává jinou možnost, která může být i užitečnější: **přerušení po výjimku: neošetřené uživatelem**. Pokud zvolíte toto nastavení pro výjimku, bude ladicí program proniknout spuštění uživatelského kódu, ale pouze v případě, že není výjimka zachycena a zpracovávat pomocí uživatelského kódu. Toto nastavení Neguje účinku nejvyšší úrovně [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] obslužná rutina výjimky, protože tuto obslužnou rutinu je v jiné uživatelského kódu.  
  
### <a name="to-enable-debugging-of-aspnet-exceptions-with-just-my-code"></a>Pokud chcete povolit ladění výjimek ASP.NET s pouze můj kód  
  
1.  Na **ladění** nabídky, klikněte na tlačítko **výjimky**.  
  
     **Výjimky** zobrazí se dialogové okno.  
  
2.  Na **výjimky modulu CLR** řádek, vyberte **vyvolaná** nebo **neošetřené uživatelem**.  
  
     Použít **neošetřené uživatelem** nastavení, **pouze můj kód** musí být povolené...  
  
### <a name="to-use-best-practices-for-aspnet-exception-handling"></a>Chcete-li použijte osvědčené postupy pro zpracování výjimek ASP.NET  
  
-   Místní `try ... catch` bloky kolem kód, který lze vyvolat výjimky, kterou můžete předvídat a vědět, jak zpracovat. Například pokud aplikace je volání webové služby XML nebo přímo k serveru SQL Server, tento kód by měl být v **try... catch** blokuje, protože nejsou k dispozici množství výjimky, které se můžou vyskytnout.

## <a name="see-also"></a>Viz také
[Ladění aplikací ASP.NET](../debugger/how-to-enable-debugging-for-aspnet-applications.md)