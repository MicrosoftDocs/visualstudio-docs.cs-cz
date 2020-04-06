---
title: Kontext projektu | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- projects [Visual Studio SDK], opening items
ms.assetid: d1803f4a-24eb-44b0-b5d2-cb40c15534be
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 51e411f0bca361f96cdffcfd89498908fd21d441
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80706586"
---
# <a name="project-context"></a>Kontext projektu
Když uživatel přidá nebo pracuje s projekty a položkami projektu, ide používá pojem kontextu projektu k určení, jak by měly být provedeny různé operace.

 Soubory jsou obvykle standardní objekty projektu, které uživatel explicitně vytvoří výběrem příkazu **Nový projekt** nebo zpřístupníte výběrem příkazu **Otevřít projekt** v nabídce **Soubor.** V těchto případech jsou soubory vytvářeny a otevřeny v kontextu projektu a typ projektu definuje kontext pro úpravy dokumentu.

 Některé projekty poskytují velmi bohatý kontext. Projekt například spravuje databázové připojení s rozsahem projektu, programový obor názvů nebo databázové připojení s rozsahem projektu pro datovou vazbu. Uživatel může často otevírat soubory nebo připojení k databázi přímo pomocí určitého objektu projektu, například položky projektu zobrazené v Průzkumníku řešení.

 Jindy kontext projektu položky není explicitně zadán. Například kontext položky není k dispozici, když uživatel otevře soubor výběrem příkazu **Otevřít existující soubor** v nabídce **Soubor,** když ladicí program pracuje se souborem nebo když uživatel klepne na příkaz **Najít v souborech** v dialogovém okně Najít a **nahradit.** Chcete-li zpracovat tyto <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument> situace, ide volání ke správě procesu hledání nejlepší projekt otevřít dokument.

## <a name="see-also"></a>Viz také
- [Priorita projektu](../../extensibility/internals/project-priority.md)
- [Přidávání šablon projektů a položek projektů](../../extensibility/internals/adding-project-and-project-item-templates.md)
