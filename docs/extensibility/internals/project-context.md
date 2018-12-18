---
title: Projekt kontextu | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- projects [Visual Studio SDK], opening items
ms.assetid: d1803f4a-24eb-44b0-b5d2-cb40c15534be
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: d2f52260d63088d7673322f3c42d43d00184a9af
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/16/2018
ms.locfileid: "31134692"
---
# <a name="project-context"></a>Kontext projektu
Pokud uživatel přidá nebo funguje s projekty a položky projektu, rozhraní IDE představu o kontextu projektu používá k určení, jak budou různé operace by měla provést.  
  
 Soubory jsou obvykle standardní projektu objekty, které uživatel explicitně vytvoří výběrem **nový projekt** příkaz nebo zpřístupňují výběrem **otevřeného projektu** příkaz na  **Soubor** nabídky. V těchto případech soubory jsou vytvořeny a otevřít v kontextu projektu a typu projektu definuje kontext pro úpravy dokumentu.  
  
 Některé projekty poskytují velmi bohaté kontextu. Například projekt spravuje obor projektu, programová oboru názvů nebo připojení k databázi obor projektu pro datovou vazbu. Uživatele můžete často otevřít soubory nebo připojení k databázi přímo pomocí objekt určitém projektu, například položka projektu zobrazí v Průzkumníku řešení.  
  
 V jinou dobu není explicitně zadané položky kontextu projektu. Kontext položky, například není k dispozici, když uživatel otevře soubor výběrem **otevřete existující soubor** příkaz na **souboru** nabídky, když ladicí program funguje na soubor, nebo když uživatel klikne **Najít v souborech** v příkazu **najít a nahradit** dialogové okno. Pro zpracování těchto situacích volání IDE <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument> ke správě procesu nalezení nejlepší projektu k otevření dokumentu.  
  
## <a name="see-also"></a>Viz také  
 [Priorita projektu](../../extensibility/internals/project-priority.md)   
 [Přidávání šablon projektů a položek projektů](../../extensibility/internals/adding-project-and-project-item-templates.md)