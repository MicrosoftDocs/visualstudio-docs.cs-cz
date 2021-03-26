---
title: Použití modelu automatizace | Microsoft Docs
description: Naučte se, jak získat vlastnosti a metody rozhraní VSPackage po připojení k modelu automatizace.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- automation [Visual Studio SDK], automation model
ms.assetid: 0c7f7889-fbfb-4b19-804f-b742138baecd
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: a25936e0be16231bbe315a2bd29a0d495115f392
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/25/2021
ms.locfileid: "105085803"
---
# <a name="using-the-automation-model"></a>Použití modelu automatizace
Po připojení VSPackage ke službě Automation můžete získat vlastnosti a metody voláním <xref:EnvDTE.DTEClass.GetObject%2A> metody <xref:EnvDTE._DTE> objektu a předáním řetězce představujícího objekt, který chcete načíst.

## <a name="obtaining-project-objects"></a>Získání objektů projektu
 Níže jsou uvedeny dva příklady kódu, které ukazují, jak spotřebitel automatizace získává objekty automatizace projektu. Informace o tom, jak získat objekt DTE, naleznete v tématu [How to: Get References to the DTE and DTE2 Objects](/previous-versions/68shb4dw(v=vs.140)).

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

 Následující kód Vypíše názvy všech vlastností v [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] možnosti **Obecné** prostředí v nabídce **nástroje** :

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