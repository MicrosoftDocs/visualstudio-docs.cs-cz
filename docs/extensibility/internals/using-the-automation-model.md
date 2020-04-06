---
title: Používání modelu automatizace | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- automation [Visual Studio SDK], automation model
ms.assetid: 0c7f7889-fbfb-4b19-804f-b742138baecd
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 2b9d7bd789a41f7a5e801552ca07f9f228921867
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80704221"
---
# <a name="using-the-automation-model"></a>Použití modelu automatizace
Po připojení vspackage k automatizaci, můžete získat vlastnosti <xref:EnvDTE.DTEClass.GetObject%2A> a metody <xref:EnvDTE._DTE> voláním metody na objektu, předáním řetězec představující objekt, který chcete načíst.

## <a name="obtaining-project-objects"></a>Získání objektů projektu
 Následují dva příklady kódu, které ukazují, jak příjemce automatizace získá objekty automatizace projektu. Informace o tom, jak získat objekt DTE, naleznete v [tématu How to: Get References to the DTE and DTE2 Objects](https://msdn.microsoft.com/Library/c92e3c8e-82e6-4a67-85da-e43c50ffd8e4).

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

 V tomto okamžiku můžete použít standardní projektové objekty, které jsou součástí konkrétního balíčku VSPackage, k přesunutí v hierarchickém modelu.

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

 Následující kód uvádí názvy všech vlastností [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] v prostředí **Obecné** možnost v nabídce **Nástroje:**

```vb
dim objDTE
dim objEnv
set objDTE = CreateObject("VisualStudio.DTE")
set objEnv = objDTE.Properties("Environment", "General")
for each obj in ObjEnv
MsgBox obj.Name
Next

```

## <a name="see-also"></a>Viz také
- <xref:EnvDTE.DTEClass.GetObject%2A>
