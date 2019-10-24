---
title: Použití modelu automatizace | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- automation [Visual Studio SDK], automation model
ms.assetid: 0c7f7889-fbfb-4b19-804f-b742138baecd
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 4f1e1479232a684758359de7527f0c2fc9990cc7
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/22/2019
ms.locfileid: "72722093"
---
# <a name="using-the-automation-model"></a>Použití modelu automatizace
Po připojení VSPackage ke službě Automation můžete získat vlastnosti a metody voláním metody <xref:EnvDTE.DTEClass.GetObject%2A> na objektu <xref:EnvDTE._DTE> a předáním řetězce představujícího objekt, který chcete načíst.

## <a name="obtaining-project-objects"></a>Získání objektů projektu
 Níže jsou uvedeny dva příklady kódu, které ukazují, jak spotřebitel automatizace získává objekty automatizace projektu. Informace o tom, jak získat objekt DTE, naleznete v tématu [How to: Get References to the DTE and DTE2 Objects](https://msdn.microsoft.com/Library/c92e3c8e-82e6-4a67-85da-e43c50ffd8e4).

```vb
Sub DoAutomation()
    Dim MyProjects As Projects
    MyProjects = DTE.GetObject("AcmeProject")
End Sub
```

```cpp
void DoAutomation(void)
{
  CComQIPtr<Projects> pMyPkg; // Use an IDispatch-derived object type.
    pMyPkg = pDTE->GetObject("AcmeProjects");

   // The '=' performs a Query Interface.
   // Assumes pDTE is already available as a global.
   // Use pMyPkg to access your projects object's properties and methods.
}

```

 V tomto okamžiku můžete použít standardní objekty projektu, které jsou součástí konkrétního VSPackage, a přesunout tak model hierarchie dolů.

 Následující příklad kódu ukazuje, jak získat vlastní objekt, který je vlastností vlastního typu projektu.:

```vb
Dim MyPrj As Project
Dim MyPrjItem As ProjectItem
Dim objMyObject as MyExtendedObject

MyPrj = MyProjects.Item(1) 'use the Projects collection to get a project
objMyObject = MyPrj.Object 'You call .Object to get to special Project
                           'implementation
objMyObject.MySpecialMethodOrProperty
```

 Následující kód obsahuje seznam všech vlastností v možnosti [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] prostředí **Obecné** v nabídce **nástroje** :

```vb
dim objDTE
dim objEnv
set objDTE = CreateObject("VisualStudio.DTE")
set objEnv = objDTE.Properties("Environment", "General")
for each obj in ObjEnv
MsgBox obj.Name
Next

```

## <a name="see-also"></a>Viz také:
- <xref:EnvDTE.DTEClass.GetObject%2A>