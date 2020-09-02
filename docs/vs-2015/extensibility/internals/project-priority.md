---
title: Priorita projektu | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- projects [Visual Studio SDK], opening items
ms.assetid: 9f707592-2fb6-4f75-9269-f6d4700a998e
caps.latest.revision: 12
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: b012136c30f72cfdddadfc1a370ed76f567afffd
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "62429909"
---
# <a name="project-priority"></a>Priorita projektu
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Položka projektu je obvykle členem pouze jednoho projektu v řešení. Proto může rozhraní IDE snadno určit, který projekt se má použít k otevření položky. Pokud je však položka členem více než jednoho projektu, rozhraní IDE používá schéma priority k určení nejvhodnějšího projektu pro otevření položky.  
  
 Následující seznam uvádí schéma priority projektu:  
  
- Rozhraní IDE volá <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject2.IsDocumentInProject%2A> metodu pro každý projekt v řešení a určí, zda je dokument členem daného projektu.  
  
- Pokud je dokument členem projektu, projekt reaguje na prioritu, kterou projekt přiřadí podle jeho manipulace s tímto dokumentem. Například jazykový projekt reaguje s vysokou prioritou pro své jazykové zdrojové soubory, ale reaguje s nižší prioritou pro nerozpoznaný typ souboru, který se nepoužívá jako součást procesu sestavení.  
  
- Projekty, které poskytují vlastní editory nebo návrháře specifické pro projekt pro dokument, také dostanou vysokou prioritu.  
  
- <xref:Microsoft.VisualStudio.Shell.Interop.VSDOCUMENTPRIORITY>Výčet poskytuje hodnoty priority dokumentu.  
  
- Projekt, který určuje nejvyšší prioritu, je dán kontextem pro otevření dokumentu. Pokud dva projekty vrací stejné prioritní hodnoty, je upřednostňován aktivní projekt. Pokud žádný projekt v řešení nereaguje na to, že může otevřít dokument, rozhraní IDE vloží dokument do projektu různé soubory. Další informace naleznete v tématu [různé soubory projektu](../../extensibility/internals/miscellaneous-files-project.md).  
  
## <a name="see-also"></a>Viz také  
 [Projekt různých souborů](../../extensibility/internals/miscellaneous-files-project.md)   
 [Postupy: otevření editorů pro otevřené dokumenty](../../extensibility/how-to-open-editors-for-open-documents.md)   
 [Přidávání šablon projektů a položek projektů](../../extensibility/internals/adding-project-and-project-item-templates.md)
