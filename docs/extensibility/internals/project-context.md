---
title: Kontext projektu | Microsoft Docs
description: Přečtěte si, jak Visual Studio IDE používá kontext projektu k určení, jak provádět operace, když uživatel přidá nebo pracuje s projekty a položkami projektu.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- projects [Visual Studio SDK], opening items
ms.assetid: d1803f4a-24eb-44b0-b5d2-cb40c15534be
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 73e3c8a94607e7e0b31bacddac8e7f19b6139328
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/25/2021
ms.locfileid: "112899820"
---
# <a name="project-context"></a>Kontext projektu
Když uživatel přidá nebo funguje s projekty a položkami projektu, rozhraní IDE použije pojem kontext projektu k určení, jak se mají provádět různé operace.

 Obvykle jsou soubory standardními objekty projektu, které uživatel explicitně vytvoří výběrem příkazu **Nový projekt** nebo zpřístupněním v nabídce **soubor** výběrem příkazu **Otevřít projekt** . V těchto případech jsou soubory vytvořeny a otevřeny v kontextu projektu a typ projektu definuje kontext pro úpravy dokumentu.

 Některé projekty poskytují velmi bohatý kontext. Projekt například spravuje databázové rozhraní, programový obor názvů nebo připojení databáze v oboru projektu pro datovou vazbu. Uživatel může často otevřít soubory nebo databázová připojení přímo pomocí konkrétního objektu projektu, jako je například položka projektu zobrazená v Průzkumník řešení.

 V jinou dobu není kontext projektu položky explicitně zadán. Například kontext položky není k dispozici, když uživatel otevře soubor výběrem příkazu **otevřít existující soubor** v nabídce **soubor** , když ladicí program pracuje na souboru nebo když uživatel klikne na příkaz **najít v souborech** v dialogovém okně **Najít a nahradit** . Za účelem zpracování těchto situací volá rozhraní IDE <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument> ke správě procesu hledání nejlepšího projektu pro otevření dokumentu.

## <a name="see-also"></a>Viz také
- [Priorita projektu](../../extensibility/internals/project-priority.md)
- [Přidávání šablon projektů a položek projektů](../../extensibility/internals/adding-project-and-project-item-templates.md)
