---
title: Filtrování dialogového okna AddItem pro vnořené projekty | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- filtering, nested projects
- nested projects, AddItem dialog box filtering
ms.assetid: 5b3e352e-7f18-4f66-be16-b0ad55637ce5
caps.latest.revision: 13
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 7bb98eac2bc481aa5e3652144dfbcadf70430d04
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "62538093"
---
# <a name="filtering-the-additem-dialog-box-for-nested-projects"></a>Filtrování dialogového okna Přidat položku pro vnořené projekty
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Když zobrazíte dialogové okno **AddItem** pro vnořený projekt, nadřazený projekt může určovat, jaké položky se zobrazí v dialogovém okně.  
  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFilterAddProjectItemDlg2>Rozhraní umožňuje filtrovat uzly, které budou v dialogovém okně **AddItem** . Když podřízený projekt zobrazí dialogové okno **AddItem** , nadřazený objekt může implementovat `IVsFilterAddProjectItemDlg` rozhraní a filtrovat položky, které by jinak byly zobrazeny v projektu dítěte.  
  
 Pokud jsou projekty seskupeny podle funkce v rámci konkrétních nadřazených projektů, můžete implementovat, `IVsFilterAddProjectItemDlg` když uživatel vybere **položku Přidat projekt** v místní nabídce ve vnořeném projektu. Implementace `IvsFilterAddProjectItemDlg displays` pouze položek projektu nebo souborů specifických pro tuto skupinu. Položky projektu pro jiné skupiny jsou filtrovány mimo dialogové okno, a to i v případě, že jsou uloženy ve stejném adresáři.  
  
 Když uživatel otevře dialogové okno **AddItem** pro podřízenou položku, `IVsFilterAddProjectItemDlg` je volána implementace rozhraní nadřazeného projektu.  
  
 `IVsFilterAddProjectItemDlg`Rozhraní může také implementovat filtrování podle kategorie. Další informace naleznete v tématu [Přidání položek do dialogových oken Přidat novou položku](../../extensibility/internals/adding-items-to-the-add-new-item-dialog-boxes.md) a [Registrace šablon projektů a položek](../../extensibility/internals/registering-project-and-item-templates.md).  
  
## <a name="see-also"></a>Viz také  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFilterAddProjectItemDlg2>   
 [Přidávání položek do dialogových oken Přidat novou položku](../../extensibility/internals/adding-items-to-the-add-new-item-dialog-boxes.md)   
 [Registrace šablon projektů a položek](../../extensibility/internals/registering-project-and-item-templates.md)   
 [Vnoření projektů](../../extensibility/internals/nesting-projects.md)
