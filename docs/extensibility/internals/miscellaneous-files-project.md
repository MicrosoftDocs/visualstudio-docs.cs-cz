---
title: Projekt různých souborů | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- files, adding existing files to solutions
- Miscellaneous Files project
- Solution Items folder
- files, opening with Miscellaneous Files project
ms.assetid: 93a278a8-d4f4-400b-8945-4f1b0a2b5bac
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: c46126507ef9bb293bd0fa6771f53343ad6206f7
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/22/2019
ms.locfileid: "72726682"
---
# <a name="miscellaneous-files-project"></a>Projekt Ostatní soubory
Když uživatel otevře položky projektu, IDE přiřadí k různým souborům všechny položky, které nejsou členy žádného projektu v řešení.

 Projekty hrají významnou roli při určování, který Editor se používá, když uživatel otevře položku projektu. Projekt může být navržen pro otevření určitých souborů pomocí editoru specifického pro projekt nebo standardního editoru.

 Editor specifický pro projekt obvykle vyžaduje, aby uživatel měl zvláštní znalosti nebo aby v projektu používal speciální rozhraní. Další informace najdete v tématu [Postup: otevření editorů specifických pro projekt](../../extensibility/how-to-open-project-specific-editors.md).

 Standardní editor může otevřít libovolný soubor konkrétního rozšíření v jakémkoli projektu. Uživatel může přizpůsobit některé standardní editory, jako je [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] textový editor, pro projekty, ale zachovat jejich veřejný charakter. Standardní editory se vytvářejí pomocí metody <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A>.

 Pokud žádný projekt v řešení nereaguje na to, že může otevřít položku projektu, integrované vývojové prostředí (IDE) poskytuje speciální projekt nazvaný projekt různé soubory, který otevírá libovolný soubor.

 Tento speciální projekt poskytuje pro otevření souboru mimo kontext projektu. Při zpracování metody <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenDocumentViaProject%2A> se v projektech různých souborů vždy reaguje s velmi nízkou prioritou. Proto projekt různé soubory vždycky vyplyne do všech projektů s vyšší prioritou, které mohou otevírat soubory.

 Projekt různých souborů nevyžaduje, aby ho uživatel explicitně vytvořil pomocí dialogového okna **Nový projekt** . Také projekt různých souborů nespravuje trvale seznam členů projektu. K zaznamenání seznamu naposledy použitých souborů pro každého uživatele používá volitelnou funkci.

## <a name="see-also"></a>Viz také:
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument>
- <xref:Microsoft.VisualStudio.Shell.Interop.VSDOCUMENTPRIORITY>
- [Postupy: Otevření editoru pro konkrétní projekt](../../extensibility/how-to-open-project-specific-editors.md)
- [Postupy: Otevření standardních editorů](../../extensibility/how-to-open-standard-editors.md)
- [Přidávání šablon projektů a položek projektů](../../extensibility/internals/adding-project-and-project-item-templates.md)
- [Přidávání šablon projektů a položek projektů](../../extensibility/internals/adding-project-and-project-item-templates.md)