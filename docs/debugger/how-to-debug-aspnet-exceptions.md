---
title: Ladění výjimek ASP.NET | Microsoft Docs
Description: Naučte se konfigurovat tak, aby ladicí program přestal v aplikaci ASP.NET reagovat na neošetřené výjimky. Můžete zajistit, že dojde k přerušení v kódu, který není systémem.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
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
manager: jmartens
ms.workload:
- aspnet
ms.openlocfilehash: 00823fd1a5029cb45b91a6beb4168f8a9cbd999a
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99913255"
---
# <a name="how-to-debug-aspnet-exceptions"></a>Postupy: Ladění výjimek ASP.NET
Výjimky ladění jsou důležitou součástí vývoje robustní [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] aplikace. Obecné informace o ladění výjimek naleznete v tématu [Správa výjimek pomocí ladicího programu](../debugger/managing-exceptions-with-the-debugger.md).

 Chcete-li ladit neošetřené [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] výjimky, je nutné zajistit, aby byl ladicí program pro ně ukončen. [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)]Modul runtime má obslužnou rutinu výjimky nejvyšší úrovně. Proto ladicí program se ve výchozím nastavení nikdy nerozdělí na neošetřené výjimky. Chcete-li přerušit ladicí program, pokud je vyvolána výjimka, je nutné vybrat možnost **přerušit, pokud je výjimka: vyvoláno** nastavení pro tuto konkrétní výjimku v dialogovém okně **výjimky** .

 Pokud jste povolili Pouze můj kód, **přerušit, pokud je výjimka: vyvolána** nezpůsobí přerušení ladicího programu, pokud je vyvolána výjimka v metodě .NET nebo jiném systémovém kódu. Místo toho se provádění pokračuje, dokud ladicí program nedosáhne kódu, který není systémovým kódem, a pak se přeruší. V důsledku toho není nutné krokovat kód systému, pokud dojde k výjimce.

 Pouze můj kód poskytuje další možnost, která může být ještě užitečnější: **přerušit, pokud je výjimka: Neošetřená uživatelem**. Pokud pro výjimku zvolíte toto nastavení, ladicí program přeruší provádění v uživatelském kódu, ale pouze v případě, že výjimka není zachycena a zpracována uživatelským kódem. Toto nastavení má za následek negaci efektu [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] obslužné rutiny výjimky nejvyšší úrovně, protože tato obslužná rutina je v neuživatelském kódu.

### <a name="to-enable-debugging-of-aspnet-exceptions-with-just-my-code"></a>Povolení ladění výjimek ASP.NET pomocí Pouze můj kód

1. V nabídce **ladění** klikněte na **výjimky**.

     Zobrazí se dialogové okno **výjimky** .

2. Na řádku **výjimky společného jazykového modulu runtime** vyberte možnost **vyvoláno** nebo **neošetřeno uživatelem**.

     Chcete-li použít nastavení **neošetřené uživatelem** , **pouze můj kód** nutné povolit.

### <a name="to-use-best-practices-for-aspnet-exception-handling"></a>Použití osvědčených postupů pro zpracování výjimek ASP.NET

- Umístěte `try ... catch` bloky kolem kódu, který může vyvolat výjimky, které můžete odhadnout a zjistit, jak se má zpracovat. Například pokud aplikace provádí volání webové služby XML nebo přímo do SQL Server, měl by být tento kód v rámci **Try... bloky catch** , protože existuje mnoho výjimek, ke kterým může dojít.

## <a name="see-also"></a>Viz také
- [Ladění aplikací ASP.NET](../debugger/how-to-enable-debugging-for-aspnet-applications.md)