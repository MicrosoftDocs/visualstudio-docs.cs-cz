---
title: Spustitelný soubor pro relaci ladění – dialogové okno | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.debug.exefordebug
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- executable files, specifying when debugging
- DLLs, debugging
- debugger, Executable for Debugging Session dialog box
- Executable for Debugging Session dialog box
ms.assetid: c0ddbe32-b99f-4425-acf1-f48842804f56
caps.latest.revision: 11
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: c2ee71c5e23b0c5784cd2fe9b57b46fe28d41d30
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "68157459"
---
# <a name="executable-for-debugging-session-dialog-box"></a>Dialogové okno Spustitelný soubor pro relaci ladění
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Toto dialogové okno se zobrazí, když se pokusíte ladit knihovnu DLL, pro kterou není zadán spustitelný soubor. Visual Studio nemůže spustit knihovnu DLL přímo. Místo toho spustí zadaný spustitelný soubor. Můžete ladit knihovnu DLL, pokud je volána spustitelným souborem.  
  
 **Název spustitelného souboru**  
 Zadejte název cesty ke spustitelnému souboru, který volá knihovnu DLL, kterou ladíte.  
  
 **Adresa URL, na které je možné přistupovat k projektu (pouze server ATL)**  
 Pokud ladíte knihovnu DLL serveru ATL, zadejte adresu URL, na které lze projekt najít.  
  
 Po zadání těchto nastavení jsou uložena na stránkách vlastností projektu, takže je nebudete muset znovu zadávat pro následné relace ladění. Pokud potřebujete změnit nastavení, můžete otevřít stránky vlastností a změnit hodnoty. Další informace o určení spustitelného souboru pro relaci ladění naleznete v tématu [ladění knihoven DLL](../debugger/how-to-debug-native-dlls.md).  
  
## <a name="see-also"></a>Viz také  
 [Ladění v sadě Visual Studio](../debugger/debugging-in-visual-studio.md)
