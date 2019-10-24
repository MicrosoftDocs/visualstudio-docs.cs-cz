---
title: Kontext projektu | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- projects [Visual Studio SDK], opening items
ms.assetid: d1803f4a-24eb-44b0-b5d2-cb40c15534be
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 8afa595a264f218fcc20f18de1c261a9ead6e030
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/22/2019
ms.locfileid: "72725774"
---
# <a name="project-context"></a>Kontext projektu
Když uživatel přidá nebo funguje s projekty a položkami projektu, rozhraní IDE použije pojem kontext projektu k určení, jak se mají provádět různé operace.

 Obvykle jsou soubory standardními objekty projektu, které uživatel explicitně vytvoří výběrem příkazu **Nový projekt** nebo zpřístupněním v nabídce **soubor** výběrem příkazu **Otevřít projekt** . V těchto případech jsou soubory vytvořeny a otevřeny v kontextu projektu a typ projektu definuje kontext pro úpravy dokumentu.

 Některé projekty poskytují velmi bohatý kontext. Projekt například spravuje databázové rozhraní, programový obor názvů nebo připojení databáze v oboru projektu pro datovou vazbu. Uživatel může často otevřít soubory nebo databázová připojení přímo pomocí konkrétního objektu projektu, jako je například položka projektu zobrazená v Průzkumník řešení.

 V jinou dobu není kontext projektu položky explicitně zadán. Například kontext položky není k dispozici, když uživatel otevře soubor výběrem příkazu **otevřít existující soubor** v nabídce **soubor** , když ladicí program pracuje na souboru nebo když uživatel klikne na příkaz **najít v souborech** v části  **Dialogové okno Najít a nahradit** . Za účelem zpracování těchto situací volá rozhraní IDE <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument> ke správě procesu hledání nejlepšího projektu pro otevření dokumentu.

## <a name="see-also"></a>Viz také:
- [Priorita projektu](../../extensibility/internals/project-priority.md)
- [Přidávání šablon projektů a položek projektů](../../extensibility/internals/adding-project-and-project-item-templates.md)