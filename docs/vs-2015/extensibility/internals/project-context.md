---
title: Kontext projektu | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- projects [Visual Studio SDK], opening items
ms.assetid: d1803f4a-24eb-44b0-b5d2-cb40c15534be
caps.latest.revision: 11
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: d4ee4da5fdea63cf1bdd33554c72f6dac30d0334
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "62429935"
---
# <a name="project-context"></a>Kontext projektu
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Když uživatel přidá nebo funguje s projekty a položkami projektu, rozhraní IDE použije pojem kontext projektu k určení, jak se mají provádět různé operace.  
  
 Obvykle jsou soubory standardními objekty projektu, které uživatel explicitně vytvoří výběrem příkazu **Nový projekt** nebo zpřístupněním v nabídce **soubor** výběrem příkazu **Otevřít projekt** . V těchto případech jsou soubory vytvořeny a otevřeny v kontextu projektu a typ projektu definuje kontext pro úpravy dokumentu.  
  
 Některé projekty poskytují velmi bohatý kontext. Projekt například spravuje databázové rozhraní, programový obor názvů nebo připojení databáze v oboru projektu pro datovou vazbu. Uživatel může často otevřít soubory nebo databázová připojení přímo pomocí konkrétního objektu projektu, jako je například položka projektu zobrazená v Průzkumník řešení.  
  
 V jinou dobu není kontext projektu položky explicitně zadán. Například kontext položky není k dispozici, když uživatel otevře soubor výběrem příkazu **otevřít existující soubor** v nabídce **soubor** , když ladicí program pracuje na souboru nebo když uživatel klikne na příkaz **najít v souborech** v dialogovém okně **Najít a nahradit** . Za účelem zpracování těchto situací volá rozhraní IDE <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument> ke správě procesu hledání nejlepšího projektu pro otevření dokumentu.  
  
## <a name="see-also"></a>Viz také  
 [Priorita projektu](../../extensibility/internals/project-priority.md)   
 [Přidávání šablon projektů a položek projektů](../../extensibility/internals/adding-project-and-project-item-templates.md)
