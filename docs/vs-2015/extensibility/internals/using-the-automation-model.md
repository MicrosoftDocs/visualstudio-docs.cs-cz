---
title: Použití modelu automatizace | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- automation [Visual Studio SDK], automation model
ms.assetid: 0c7f7889-fbfb-4b19-804f-b742138baecd
caps.latest.revision: 16
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 22ee836f5a4330c551181f01229e82eb14623fb8
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "65675212"
---
# <a name="using-the-automation-model"></a>Použití modelu automatizace
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Po připojení VSPackage ke službě Automation můžete získat vlastnosti a metody voláním <xref:EnvDTE.DTEClass.GetObject%2A> metody <xref:EnvDTE._DTE> objektu a předáním řetězce představujícího objekt, který chcete načíst.  
  
## <a name="obtaining-project-objects"></a>Získání objektů projektu  
 Níže jsou uvedeny dva příklady kódu, které ukazují, jak spotřebitel automatizace získává objekty automatizace projektu. Informace o tom, jak získat objekt DTE, naleznete v tématu [How to: Get References to the DTE and DTE2 Objects](https://msdn.microsoft.com/library/c92e3c8e-82e6-4a67-85da-e43c50ffd8e4).  
  
```vb  
Sub DoAutomation()  
    Dim MyProjects As Projects  
    MyProjects = DTE.GetObject("AcmeProject")  
End Sub  
```  
  
```cpp#  
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
  
 Následující kód Vypíše názvy všech vlastností v [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] možnosti **Obecné** prostředí v nabídce **nástroje** :  
  
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
 <xref:EnvDTE.DTEClass.GetObject%2A>
