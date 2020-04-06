---
title: Filtrování dialogového okna Přidat položku pro vnořené projekty | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- filtering, nested projects
- nested projects, AddItem dialog box filtering
ms.assetid: 5b3e352e-7f18-4f66-be16-b0ad55637ce5
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 2bc97b6041f4844ff71fe1d38a7103e1219888be
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80708386"
---
# <a name="filter-the-additem-dialog-box-for-nested-projects"></a>Filtrování dialogového okna Přidat položku pro vnořené projekty
Když zobrazíte dialogové okno **AddItem** pro vnořený projekt, nadřazený projekt může řídit, jaké položky se zobrazí v dialogovém okně.

 Rozhraní <xref:Microsoft.VisualStudio.Shell.Interop.IVsFilterAddProjectItemDlg2> umožňuje filtrovat uzly, které budou v dialogovém okně **Přidat položku.** Když podřízený projekt zobrazí dialogové okno **AddItem,** nadřazený může implementovat `IVsFilterAddProjectItemDlg` rozhraní a filtrovat položky, které by jinak byly zobrazeny v projektu dítěte.

 Pokud jsou projekty seskupeny podle funkce pod `IVsFilterAddProjectItemDlg` konkrétní nadřazené projekty, můžete implementovat, když uživatel vybere **přidat položku projektu** v místní nabídce v vnořeném projektu. Implementace `IvsFilterAddProjectItemDlg displays` pouze položek projektu nebo souborů specifických pro danou skupinu. Položky projektu pro jiné skupiny jsou odfiltrovány z dialogového okna, i když jsou uloženy ve stejném adresáři.

 Když uživatel otevře dialogové okno **AddItem** pro podřízenou položku, volá se implementace `IVsFilterAddProjectItemDlg` rozhraní nadřazeného projektu.

 Rozhraní `IVsFilterAddProjectItemDlg` může také implementovat filtrování podle kategorie. Další informace naleznete v [tématu Přidání položek do dialogového okna Přidat novou položku](../../extensibility/internals/adding-items-to-the-add-new-item-dialog-boxes.md) a [Zaregistrovat šablony projektu a položek](../../extensibility/internals/registering-project-and-item-templates.md).

## <a name="see-also"></a>Viz také
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsFilterAddProjectItemDlg2>
- [Přidání položek do dialogového okna Přidat novou položku](../../extensibility/internals/adding-items-to-the-add-new-item-dialog-boxes.md)
- [Registrace šablon projektů a položek](../../extensibility/internals/registering-project-and-item-templates.md)
- [Projekty vnoření](../../extensibility/internals/nesting-projects.md)
