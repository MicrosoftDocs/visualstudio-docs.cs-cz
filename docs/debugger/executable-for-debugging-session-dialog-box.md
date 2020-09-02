---
title: Spustitelný soubor pro relaci ladění – dialogové okno | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- vs.debug.exefordebug
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- executable files, specifying when debugging
- DLLs, debugging
- debugger, Executable for Debugging Session dialog box
- Executable for Debugging Session dialog box
ms.assetid: c0ddbe32-b99f-4425-acf1-f48842804f56
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 92cf53ed499318d60c8da5147685e3f0f340e404
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "72736241"
---
# <a name="executable-for-debugging-session-dialog-box"></a>Dialogové okno Spustitelný soubor pro relaci ladění

Toto dialogové okno se zobrazí, když se pokusíte ladit knihovnu DLL, pro kterou není zadán spustitelný soubor. Visual Studio nemůže spustit knihovnu DLL přímo. Místo toho Visual Studio spustí zadaný spustitelný soubor. Můžete ladit knihovnu DLL, pokud je volána spustitelným souborem.

 **Název spustitelného souboru** Zadejte název cesty ke spustitelnému souboru, který volá knihovnu DLL, kterou ladíte.

 **Adresa URL, na které je možné přistupovat k projektu (pouze server ATL)** Pokud ladíte knihovnu DLL serveru ATL, zadejte adresu URL, na které lze projekt najít.

 Po zadání těchto nastavení jsou uložena na stránkách vlastností projektu, takže je nebudete muset znovu zadávat pro následné relace ladění. Pokud potřebujete změnit nastavení, můžete otevřít stránky vlastností a změnit hodnoty. Další informace o určení spustitelného souboru pro relaci ladění naleznete v tématu [ladění knihoven DLL](../debugger/how-to-debug-from-a-dll-project.md).

## <a name="see-also"></a>Viz také

- [Ladění v sadě Visual Studio](../debugger/index.yml)
- [První seznámení s ladicím programem](../debugger/debugger-feature-tour.md)