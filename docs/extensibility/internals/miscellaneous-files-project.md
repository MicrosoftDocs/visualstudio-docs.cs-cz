---
title: Ostatní soubory projektu | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- files, adding existing files to solutions
- Miscellaneous Files project
- Solution Items folder
- files, opening with Miscellaneous Files project
ms.assetid: 93a278a8-d4f4-400b-8945-4f1b0a2b5bac
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: a637b37590a0aaf321a4e04896b2cbe12c29691f
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/16/2018
ms.locfileid: "31129974"
---
# <a name="miscellaneous-files-project"></a>Ostatní soubory projektu
Když uživatel otevře položky projektu, rozhraní IDE přiřadí různé soubory projektu všechny položky, které nejsou členy žádné projekty v řešení.  
  
 Projekty přehrát významnou roli při určování, které editor se používá, když uživatel otevře položka projektu. Chcete-li otevřít určité soubory pomocí editoru specifické pro projekt nebo standardního editoru lze navrhnout projektu.  
  
 Editor specifické pro projekt se obvykle vyžaduje, aby uživatel mít speciální znalosti nebo použít speciální rozhraní z projektu. Další informace najdete v tématu [postup: Otevřete projekt konkrétní editory](../../extensibility/how-to-open-project-specific-editors.md).  
  
 Standardní editor můžete otevřít libovolný soubor s konkrétní příponou ve všech projektech. Uživatel může přizpůsobit některé standardní editory, jako [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] textový editor, pro projekty i nadále však zachovat jejich veřejné znak. Standardní editory se vytváří pomocí <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A> metoda.  
  
 Pokud žádný projekt v řešení odpoví, aby ji mohli otevřít položka projektu, rozhraní IDE poskytuje speciální projekt s názvem různé soubory projektu, který otevře všechny soubory.  
  
 Tento projekt speciální poskytuje pro otevření souboru mimo kontext projektu. Během zpracování <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenDocumentViaProject%2A> metoda, ostatní soubory projektu vždy odpovídá s velmi nízkou prioritu. Ostatní soubory projektu proto vždy jsou pro všechny s vyšší prioritou projekt, který můžete otevřít soubory.  
  
 Ostatní soubory projektu nevyžaduje žádný uživatel nemusel vytvářet její **nový projekt** dialogové okno. Navíc různé soubory projektu trvale nespravuje seznam členů projektu. Volitelná funkce používá k zaznamenání seznam naposledy použitých souborů pro každého uživatele.  
  
## <a name="see-also"></a>Viz také  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument>   
 <xref:Microsoft.VisualStudio.Shell.Interop.VSDOCUMENTPRIORITY>   
 [Postupy: otevření projektu konkrétní editory](../../extensibility/how-to-open-project-specific-editors.md)   
 [Postupy: otevření standardní editory](../../extensibility/how-to-open-standard-editors.md)   
 [Přidání projektů a šablon položek projektu](../../extensibility/internals/adding-project-and-project-item-templates.md)   
 [Přidávání šablon projektů a položek projektů](../../extensibility/internals/adding-project-and-project-item-templates.md)