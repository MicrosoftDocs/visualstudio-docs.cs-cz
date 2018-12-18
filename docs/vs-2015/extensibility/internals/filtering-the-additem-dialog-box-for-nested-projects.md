---
title: Filtrování dialogového okna pro vnořené projekty | Dokumentace Microsoftu
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
- filtering, nested projects
- nested projects, AddItem dialog box filtering
ms.assetid: 5b3e352e-7f18-4f66-be16-b0ad55637ce5
caps.latest.revision: 13
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 363ba8e38ae2de445bd18bb9378d48aa4d824298
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/16/2018
ms.locfileid: "51769763"
---
# <a name="filtering-the-additem-dialog-box-for-nested-projects"></a>Filtrování dialogového okna Přidat položku pro vnořené projekty
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Při zobrazení **AddItem** dialogové okno pro vnořený projekt nadřazený projekt můžete řídit, které položky se zobrazí v dialogovém okně.  
  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFilterAddProjectItemDlg2> Rozhraní umožňuje filtrovat uzly, které bude mít **AddItem** dialogové okno. Pokud podřízený projekt zobrazí **AddItem** dialogovém okně můžete implementovat nadřazené `IVsFilterAddProjectItemDlg` rozhraní a filtrování položek, které by jinak zobrazeného v prvku projektu.  
  
 Pokud projekty jsou seskupeny podle funkce v rámci určité nadřazené projektů, můžete implementovat `IVsFilterAddProjectItemDlg` když uživatel vybere **přidat položku projektu** v místní nabídce v vnořený projekt. Implementace `IvsFilterAddProjectItemDlg displays` projektu pouze položky, nebo soubory specifické pro tuto skupinu. Položky projektu pro jiné skupiny, jsou odfiltrovány z dialogu, i v případě, že jsou uložené ve stejném adresáři.  
  
 Když uživatel otevře **AddItem** dialogové okno pro podřízený, nadřazené projektu provádění `IVsFilterAddProjectItemDlg` je názvem rozhraní.  
  
 `IVsFilterAddProjectItemDlg` Rozhraní můžete taky implementovat pomocí filtrování podle kategorie. Další informace najdete v tématu [přidání položky, které chcete přidat novou položku dialogových oknech](../../extensibility/internals/adding-items-to-the-add-new-item-dialog-boxes.md) a [registrace projektů a šablon položek](../../extensibility/internals/registering-project-and-item-templates.md).  
  
## <a name="see-also"></a>Viz také  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFilterAddProjectItemDlg2>   
 [Přidávání položek do přidání nové položky v dialogových oknech](../../extensibility/internals/adding-items-to-the-add-new-item-dialog-boxes.md)   
 [Registrace šablon projektů a položek](../../extensibility/internals/registering-project-and-item-templates.md)   
 [Vnoření projektů](../../extensibility/internals/nesting-projects.md)

