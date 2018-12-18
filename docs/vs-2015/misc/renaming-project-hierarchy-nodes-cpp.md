---
title: Přejmenování uzlů hierarchie projektu (C++) | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-csharp
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- HierUtil7 sample [Visual Studio SDK], renaming project nodes
- project nodes, renaming in HierUtil7 sample
ms.assetid: cea5968e-e9f8-41a5-b068-622df542247c
caps.latest.revision: 12
manager: douge
ms.openlocfilehash: 5b86096834b2a841b3fe35e1045bc3897bb7667f
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/12/2018
ms.locfileid: "49203759"
---
# <a name="renaming-project-hierarchy-nodes-c"></a>Přejmenování uzlů hierarchie projektu (C++)
Uzel hierarchie projektu složku můžete přejmenovat pomocí rozhraní projektu HierUtil7 nespravované jazyka c++. Další informace najdete v tématu [HierUtil7 ukázka](http://msdn.microsoft.com/en-us/29c15184-a70c-4813-86c2-fb1d47442d11).  
  
## <a name="expanding-the-hierarchy-node"></a>Rozbalení uzlu hierarchie  
  
#### <a name="to-expand-the-hierarchy-node-and-rename-the-folder"></a>Rozbalte uzel hierarchie a přejmenovat složku  
  
1.  Vyberte uzel hierarchie pomocí následující metody:  
  
    ```  
    IfFailGo(pNode->ExtExpand(EXPF_SelectItem, GUID_MacroExplorer));  
    ```  
  
     `pNode` je odpovídající složce hierarchie kontejneru a `EXPF_SelectItem` z <xref:Microsoft.VisualStudio.Shell.Interop.EXPANDFLAGS> výčtu. `GUID_MacroExplorer` Je identifikátor GUID konstanta definovaná v Vsshell.idl a je příklad `rguidPersistenceSlot` v signatuře funkce `ExtExpand`, definované v Hu_node.h.  
  
    ```  
    HRESULT ExtExpand(EXPANDFLAGS expandflags, REFGUID rguidPersistenceSlot = GUID_SolutionExplorer) const;  
    ```  
  
     Soubor Hu_node.h najdete ve složce \<kořenové instalace > \Program Files\VSIP 8.0\EnvSDK\common\hierutil7:  
  
2.  Tím, že publikuje příkaz rename s využitím přejmenujte složku <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.PostExecCommand%2A>  
  
    ```  
    IfFailGo(srpVsUIShell->PostExecCommand(&guidVSStd97, cmdidRename, 0, NULL));  
    ```  
  
     `srpVsUIShell` je <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell> ukazatel: `<IVsUIShell>``srpVsUIShell`. `guiVSStd97` Jedinečný identifikátor skupiny příkazů, ke kterému je příkaz `cmdidRename` patří, definované v Vsshlids.h.  
  
## <a name="see-also"></a>Viz také  
 [Vytváření typů projektů](../extensibility/internals/creating-project-types.md)   
 [Ukázky VSSDK](../misc/vssdk-samples.md)