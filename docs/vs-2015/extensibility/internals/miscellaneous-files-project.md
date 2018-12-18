---
title: Různé soubory projektu | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- files, adding existing files to solutions
- Miscellaneous Files project
- Solution Items folder
- files, opening with Miscellaneous Files project
ms.assetid: 93a278a8-d4f4-400b-8945-4f1b0a2b5bac
caps.latest.revision: 14
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: e5786eb21813125237a35ed185542b5f73bdc839
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/16/2018
ms.locfileid: "51777887"
---
# <a name="miscellaneous-files-project"></a>Projekt Ostatní soubory
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Když uživatel otevře položky projektu, rozhraní IDE přiřadí různé soubory projektu všechny položky, které nejsou členy všechny projekty v řešení.  
  
 Projekty přehrát významnou roli při určování, které editor se používá, když uživatel otevře položku projektu. Chcete-li otevřít určité soubory pomocí editoru specifické pro projekt nebo standardní editor nelze navrhovat projektu.  
  
 Editor specifické pro projekt obvykle vyžaduje, aby uživatel zvláštní znalosti, nebo použít speciální rozhraní z projektu. Další informace najdete v tématu [jak: otevřít editoru pro konkrétní projekt](../../extensibility/how-to-open-project-specific-editors.md).  
  
 Standardní editor můžete otevřít libovolný soubor s konkrétní příponou v každém projektu. Uživatel může upravit některé standardní editory, jako [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] textový editor pro projekty, ale stále zachovat jejich veřejné znak. Standardní editory jsou vytvářeny instalační sadou <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A> metody.  
  
 Pokud žádný projekt v řešení odpoví, že jej otevřete položku projektu, rozhraní IDE poskytuje zvláštní projekt s názvem, který otevře všechny soubory projektu různých souborů.  
  
 Tento projekt poskytuje pro otevření souboru mimo kontext projektu. Během zpracování <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenDocumentViaProject%2A> metody ostatních souborech projektu vždy odpovídá s velmi nízkou prioritou. Různé soubory projektu proto vždy výnosy do jakéhokoli projektu s vyšší prioritou, který můžete otevřít soubory.  
  
 Různé soubory projektu nevyžaduje, aby uživatel nemusel vytvářet pomocí **nový projekt** dialogové okno. Navíc různé soubory projektu trvale nespravuje seznam členů projektu. Volitelná funkce používá k zaznamenání seznamu naposledy použitých souborů pro každého uživatele.  
  
## <a name="see-also"></a>Viz také  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument>   
 <xref:Microsoft.VisualStudio.Shell.Interop.VSDOCUMENTPRIORITY>   
 [Postupy: otevření editoru pro konkrétní projekt](../../extensibility/how-to-open-project-specific-editors.md)   
 [Postupy: otevření standardních editorů](../../extensibility/how-to-open-standard-editors.md)   
 [Přidání projektu a šablony položek projektu](../../extensibility/internals/adding-project-and-project-item-templates.md)   
 [Přidávání šablon projektů a položek projektů](../../extensibility/internals/adding-project-and-project-item-templates.md)

