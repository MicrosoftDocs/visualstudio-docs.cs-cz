---
title: Filtrování dialogového okna AddItem pro vnořené projekty | Microsoft Docs
description: Přečtěte si, jak filtrovat dialogové okno AddItem pro vnořený projekt v aplikaci Visual Studio implementací rozhraní IVsFilterAddProjectItemDlg nadřazeného projektu.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- filtering, nested projects
- nested projects, AddItem dialog box filtering
ms.assetid: 5b3e352e-7f18-4f66-be16-b0ad55637ce5
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 668a1c3bae34caa2dc6a12def2bcee56765adbb1
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99886948"
---
# <a name="filter-the-additem-dialog-box-for-nested-projects"></a>Filtrování dialogového okna AddItem pro vnořené projekty
Když zobrazíte dialogové okno **AddItem** pro vnořený projekt, nadřazený projekt může určovat, jaké položky se zobrazí v dialogovém okně.

 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFilterAddProjectItemDlg2>Rozhraní umožňuje filtrovat uzly, které budou v dialogovém okně **AddItem** . Když podřízený projekt zobrazí dialogové okno **AddItem** , nadřazený objekt může implementovat `IVsFilterAddProjectItemDlg` rozhraní a filtrovat položky, které by jinak byly zobrazeny v projektu dítěte.

 Pokud jsou projekty seskupeny podle funkce v rámci konkrétních nadřazených projektů, můžete implementovat, `IVsFilterAddProjectItemDlg` když uživatel vybere **položku Přidat projekt** v místní nabídce ve vnořeném projektu. Implementace `IvsFilterAddProjectItemDlg displays` pouze položek projektu nebo souborů specifických pro tuto skupinu. Položky projektu pro jiné skupiny jsou filtrovány mimo dialogové okno, a to i v případě, že jsou uloženy ve stejném adresáři.

 Když uživatel otevře dialogové okno **AddItem** pro podřízenou položku, `IVsFilterAddProjectItemDlg` je volána implementace rozhraní nadřazeného projektu.

 `IVsFilterAddProjectItemDlg`Rozhraní může také implementovat filtrování podle kategorie. Další informace naleznete v tématu [Přidání položek do dialogového okna Přidat novou položku](../../extensibility/internals/adding-items-to-the-add-new-item-dialog-boxes.md) a [Registrace šablon projektů a položek](../../extensibility/internals/registering-project-and-item-templates.md).

## <a name="see-also"></a>Viz také
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsFilterAddProjectItemDlg2>
- [Přidání položek do dialogového okna Přidat novou položku](../../extensibility/internals/adding-items-to-the-add-new-item-dialog-boxes.md)
- [Registrace šablon projektů a položek](../../extensibility/internals/registering-project-and-item-templates.md)
- [Vnořit projekty](../../extensibility/internals/nesting-projects.md)
