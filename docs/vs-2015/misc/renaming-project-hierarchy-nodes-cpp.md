---
title: Přejmenování uzlů hierarchie projektu (C++) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: devlang-csharp
ms.topic: conceptual
helpviewer_keywords:
- HierUtil7 sample [Visual Studio SDK], renaming project nodes
- project nodes, renaming in HierUtil7 sample
ms.assetid: cea5968e-e9f8-41a5-b068-622df542247c
caps.latest.revision: 12
manager: jillfra
ms.openlocfilehash: c7ad43fe1fd0e22cd94194d3079761de812b6ced
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "65686591"
---
# <a name="renaming-project-hierarchy-nodes-c"></a>Přejmenování uzlů hierarchie projektu (C++)
Uzel hierarchie složky projektu můžete přejmenovat pomocí HierUtil7 projektu Framework pro nespravovaný kód C++. Další informace najdete v tématu [HierUtil7 Sample](https://msdn.microsoft.com/29c15184-a70c-4813-86c2-fb1d47442d11).  
  
## <a name="expanding-the-hierarchy-node"></a>Rozbalení uzlu hierarchie  
  
#### <a name="to-expand-the-hierarchy-node-and-rename-the-folder"></a>Rozbalení uzlu hierarchie a přejmenování složky  
  
1. Vyberte uzel hierarchie pomocí následující metody:  
  
    ```  
    IfFailGo(pNode->ExtExpand(EXPF_SelectItem, GUID_MacroExplorer));  
    ```  
  
     `pNode` je kontejner hierarchie odpovídající složce a `EXPF_SelectItem` je z <xref:Microsoft.VisualStudio.Shell.Interop.EXPANDFLAGS> výčtu. `GUID_MacroExplorer`Je konstanta GUID definovaná v vsshell. idl a je příkladem pro `rguidPersistenceSlot` signaturu funkce `ExtExpand` definované v Hu_node. h.  
  
    ```  
    HRESULT ExtExpand(EXPANDFLAGS expandflags, REFGUID rguidPersistenceSlot = GUID_SolutionExplorer) const;  
    ```  
  
     Soubor Hu_node. h můžete najít ve složce, \<installation root> \Program Files\VSIP 8.0 \ EnvSDK\common\hierutil7:  
  
2. Přejmenujte složku publikováním příkazu přejmenovat pomocí <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.PostExecCommand%2A>  
  
    ```  
    IfFailGo(srpVsUIShell->PostExecCommand(&guidVSStd97, cmdidRename, 0, NULL));  
    ```  
  
     `srpVsUIShell` je <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell> ukazatel: `<IVsUIShell>``srpVsUIShell` . `guiVSStd97` je jedinečný identifikátor skupiny příkazů, do které příkaz `cmdidRename` patří, definovaný v Vsshlids. h.  
  
## <a name="see-also"></a>Viz také  
 [Vytváření typů projektů](../extensibility/internals/creating-project-types.md)   
 [Ukázky VSSDK](../misc/vssdk-samples.md)