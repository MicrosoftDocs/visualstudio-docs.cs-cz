---
title: Upravit a pokračovat (Visual Basic) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- FSharp
- VB
- CSharp
- C++
- VB
helpviewer_keywords:
- Edit and Continue, 64-bit
- Edit and Continue [Visual Basic]
- debugging [Visual Basic], Edit and Continue
- Visual Basic, Edit and Continue
- 64-bit Edit and Continue
ms.assetid: 7e90f34f-e699-45ab-a4c9-a4b527c498c8
caps.latest.revision: 43
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 24782fee98cff09513ff2b4d1606f2be0bd9fbd2
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "62428554"
---
# <a name="edit-and-continue-visual-basic"></a>Upravit a pokračovat (Visual Basic)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Funkce upravit a pokračovat je funkcí pro [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] ladění, která umožňuje změnit kód, který je spuštěn v režimu pozastavení. Po použití úprav kódu můžete pokračovat v provádění kódu s novými úpravami na místě a zobrazit efekt.  
  
 Můžete použít funkci upravit a pokračovat pokaždé, když zadáte režim přerušení. V režimu pozastavení, ukazatel na instrukci, žlutá šipka v okně zdroje, odkazuje na řádek, který bude proveden Next, a bude umístěn v příkazu spustitelného v rámci metody nebo těla vlastnosti. V režimu pozastavení můžete provést téměř jakýkoli typ změny spustitelných příkazů a tato změna bude začleněna do podkladového projektu. V režimu pozastavení však obvykle není povoleno měnit příkazy deklarace, jako jsou veřejné metody, veřejné pole nebo deklarace tříd.  
  
 Když provedete neautorizovanou úpravu, je tato změna označena fialovým podtržením vlnovkou a v Seznam úkolů se zobrazí úkol. Pokud chcete pokračovat v používání operace Upravit a pokračovat, musíte zrušit neoprávněné úpravy. Některé neoprávněné úpravy mohou být povoleny, pokud jsou dokončeny mimo úpravy a pokračování. Pokud chcete uchovat výsledky takových neoprávněných úprav, je nutné zastavit ladění a restartovat aplikaci.  
  
 Příkaz Upravit a pokračovat je podporován pro 64 projekty, které cílí na .NET Framework 4.5.1.  
  
 Operace Upravit a pokračovat není podporována, pokud spustíte ladění pomocí **připojit k procesu**. Příkaz Upravit a pokračovat není podporován u optimalizovaného kódu, smíšeného spravovaného a nativního kódu nebo projektů kompaktního rozhraní (Smart Device).  
  
 Témata v této části poskytují další podrobnosti o tom, jak tuto funkci používat a jaké druhy změn nejsou povolené.  
  
## <a name="in-this-section"></a>V tomto oddílu  
 [Postupy: Použití úprav v režimu pozastavení pomocí operace Upravit a pokračovat](../debugger/how-to-apply-edits-in-break-mode-with-edit-and-continue.md)  
 Vysvětluje, jak použít úpravy kódu v režimu pozastavení.  
  
 [Nepodporované úpravy v operaci Upravit a pokračovat jazyka Visual Basic](../debugger/unsupported-edits-in-visual-basic-edit-and-continue.md)  
 Popisuje, jaké typy úprav nelze provést v možnosti [!INCLUDE[vb_current_short](../includes/vb-current-short-md.md)] Upravit a pokračovat.  
  
## <a name="related-sections"></a>Související oddíly  
 [Upravit a pokračovat](../debugger/edit-and-continue.md)  
 V této části najdete seznam témat pro úpravu a pokračování.
