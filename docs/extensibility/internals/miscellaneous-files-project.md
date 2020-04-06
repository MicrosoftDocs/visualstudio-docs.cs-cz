---
title: Různé soubory projektu | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- files, adding existing files to solutions
- Miscellaneous Files project
- Solution Items folder
- files, opening with Miscellaneous Files project
ms.assetid: 93a278a8-d4f4-400b-8945-4f1b0a2b5bac
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 95cc1312fb7b381e1e20df834698480295fadcc8
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80707101"
---
# <a name="miscellaneous-files-project"></a>Projekt Ostatní soubory
Když uživatel otevře položky projektu, ide přiřadí různé soubory projektu všechny položky, které nejsou členy žádné projekty v řešení.

 Projekty hrají významnou roli při určování, který editor se používá, když uživatel otevře položku projektu. Projekt může být navržen tak, aby otevíral určité soubory pomocí editoru specifického pro projekt nebo standardního editoru.

 Editor specifický pro projekt obvykle vyžaduje, aby uživatel měl zvláštní znalosti nebo používal speciální rozhraní z projektu. Další informace naleznete v [tématu How to: Open Project-Specific Editors](../../extensibility/how-to-open-project-specific-editors.md).

 Standardní editor můžete otevřít libovolný soubor konkrétní přípony v libovolném projektu. Uživatel může přizpůsobit některé standardní editory, například [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] textový editor, pro projekty, ale stále si zachová svůj veřejný charakter. Standardní editory jsou vytvářeny pomocí <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A> metody.

 Pokud žádný projekt v řešení odpoví, že může otevřít položku projektu, ide poskytuje speciální projekt s názvem Různé soubory projektu, který otevře libovolný soubor.

 Tento speciální projekt umožňuje otevření souboru mimo kontext projektu. Během zpracování <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenDocumentViaProject%2A> metody různé soubory projektu vždy reaguje s velmi nízkou prioritou. Proto různé soubory projektu vždy výnosy do jakékoli vyšší prioritu projektu, který může otevřít soubory.

 Projekt Různé soubory nevyžaduje, aby jej uživatel explicitně vytvořil pomocí dialogového okna **Nový projekt.** Také různé soubory projektu není trvale spravovat seznam členů projektu. Používá volitelnou funkci pro záznam seznamu naposledy použitých souborů pro každého uživatele.

## <a name="see-also"></a>Viz také
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument>
- <xref:Microsoft.VisualStudio.Shell.Interop.VSDOCUMENTPRIORITY>
- [Postupy: Otevření editoru pro konkrétní projekt](../../extensibility/how-to-open-project-specific-editors.md)
- [Postupy: Otevření standardních editorů](../../extensibility/how-to-open-standard-editors.md)
- [Přidávání šablon projektů a položek projektů](../../extensibility/internals/adding-project-and-project-item-templates.md)
- [Přidávání šablon projektů a položek projektů](../../extensibility/internals/adding-project-and-project-item-templates.md)
