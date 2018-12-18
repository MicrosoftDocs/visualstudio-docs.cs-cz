---
title: Upravit a pokračovat (Visual Basic) | Dokumentace Microsoftu
ms.custom: ''
ms.date: 10/11/2017
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- Edit and Continue, 64-bit
- Edit and Continue [Visual Basic]
- debugging [Visual Basic], Edit and Continue
- Visual Basic, Edit and Continue
- 64-bit Edit and Continue
ms.assetid: 7e90f34f-e699-45ab-a4c9-a4b527c498c8
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 290216d9baa2692b1cb05741f3b1afc22c74988c
ms.sourcegitcommit: 8cdc6e2ad2341f34bd6b02859a7c975daa0c9320
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/12/2018
ms.locfileid: "53307658"
---
# <a name="edit-and-continue-visual-basic"></a>Upravit a pokračovat (Visual Basic)
Upravit a pokračovat je funkce pro [!INCLUDE [vbprvb](../code-quality/includes/vbprvb_md.md)] ladění, která umožňuje změnit kód, zatímco je spuštěn v režimu pozastavení. Po použití úprav kódu, můžete pokračovat v provádění kódu pomocí nové úpravy na místě a vidět její účinek.  
  
 Můžete použít upravit a pokračovat funkci pokaždé, když zadáte režim přerušení. V režimu přerušení, ukazatele na instrukci, žlutá šipka v okně zdroje odkazuje na řádek obsahující spustitelný příkaz v těle metody nebo vlastnosti, které se bude proveden další.

 Upravit a pokračovat podporuje většina změn, které můžete chtít provést během relace ladění, ale existují některé výjimky. Další informace najdete v tématu [podporované změny kódu (C# a Visual Basic)](../debugger/supported-code-changes-csharp.md).   
  
 Pokud provedete úpravy neoprávněným, tato změna je označené fialovou vlnovkou a úlohy se zobrazí v seznamu úkolů. Pokud chcete pokračovat v používání funkce upravit a pokračovat, musíte vrátit neoprávněné úpravy. Některé úpravy, neoprávněným může být povoleno v případě aktivace mimo funkce upravit a pokračovat. Pokud chcete zachovat výsledky neoprávněné upravit, musíte Zastavit ladění a restartujte aplikaci.  
  
 Upravit a pokračovat je podporováno v aplikacích pro UPW pro Windows 10 a x86 a x64 aplikací určených pro rozhraní .NET Framework 4.6 klasické pracovní plochy nebo novější verze (jenom desktopové verze rozhraní .NET Framework je).

 > [!NOTE]
 > Nepodporované aplikace a platformy obsahují ASP.NET 5, Silverlight 5 a Windows 8.1.
  
 Upravit a pokračovat není podporována při spuštění ladění pomocí **připojit k procesu**. Upravit a pokračovat není podporována pro optimalizovaný kód nebo smíšené spravovaného a nativního kódu. Další informace najdete v tématu [podporované změny kódu (C# a Visual Basic)](../debugger/supported-code-changes-csharp.md).
  
 Témata v této části poskytují další podrobnosti o tom, jak používat tuto funkci a jaké druhy změny nejsou povoleny.  
  
## <a name="in-this-section"></a>V tomto oddílu  
 [Postupy: Použití úprav v režimu pozastavení pomocí operace upravit a pokračovat](../debugger/how-to-apply-edits-in-break-mode-with-edit-and-continue.md)  
 Vysvětluje, jak použít kód úprav v režimu pozastavení.  
  
 [Podporované změny kódu (C# a Visual Basic)](../debugger/supported-code-changes-csharp.md)   
 Popisuje, jaké typy úprav nelze provádět v [!INCLUDE [vb_current_short](../debugger/includes/vb_current_short_md.md)] upravit a pokračovat.  
  
## <a name="related-sections"></a>Související oddíly  
 [Operace Upravit a pokračovat](../debugger/edit-and-continue.md)  
 Obsahuje seznam témat, upravit a pokračovat.
