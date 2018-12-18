---
title: Registrace generátorů tvořených jedním souborem | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- registration, custom tools
- custom tools, defining registry settings
ms.assetid: db7592c0-1273-4843-9617-6e2ddabb6ca8
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: a2e65a1ef3db913223d9248797d1cf4bd9c9ded6
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/23/2018
ms.locfileid: "49875993"
---
# <a name="registering-single-file-generators"></a>Registrace generátorů tvořených jedním souborem
Zpřístupnit ve vlastní nástroj [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)], je třeba jej zaregistrovat tak [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] lze vytvořit instanci a přidruží ji k konkrétní typ projektu.  
  
### <a name="to-register-a-custom-tool"></a>K registraci vlastního nástroje  
  
1. Buď registrovat vlastní nástroj knihovny DLL v [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] místního registru nebo v systémovém registru, v části HKEY_CLASSES_ROOT.  
  
    Například tady je registrační informace pro spravované MSDataSetGenerator vlastní nástroj, který se dodává s [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]:  
  
   ```  
   [HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\14.0\CLSID\{E76D53CC-3D4F-40A2-BD4D-4F3419755476}]  
   @="COM+ class: Microsoft.VSDesigner.CodeGenerator.TypedDataSourceGenerator.DataSourceGeneratorWrapper"  
   "InprocServer32"="C:\\WINDOWS\\system32\\mscoree.dll"  
   "ThreadingModel"="Both"  
   "Class"="Microsoft.VSDesigner.CodeGenerator.TypedDataSourceGenerator.DataSourceGeneratorWrapper"  
   "Assembly"="Microsoft.VSDesigner, Version=14.0.0.0, Culture=Neutral, PublicKeyToken=b03f5f7f11d50a3a"  
   ```  
  
2. Vytvořte klíč registru v požadovaný [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] hive v rámci generátorů\\*GUID* kde *GUID* identifikátor GUID určen systém projektu konkrétní jazyk nebo služby. Název klíče bude programový název vlastního nástroje. Vlastní nástroj klíč má následující hodnoty:  
  
   -   (Výchozí)  
  
        Volitelné. Poskytuje uživatelsky přívětivý popis vlastního nástroje. Tento parametr je nepovinný, ale doporučený.  
  
   -   IDENTIFIKÁTOR CLSID  
  
        Požadováno. Určuje identifikátor knihovně tříd rozhraní komponenty modelu COM, který implementuje <xref:Microsoft.VisualStudio.Shell.Interop.IVsSingleFileGenerator>.  
  
   -   GeneratesDesignTimeSource  
  
        Požadováno. Určuje, zda typy z soubory vytvořené jazykem tohoto vlastního nástroje jsou k dispozici pro vizuální návrháře. Hodnota tohoto parametru musí být 0 (nula) typy nejsou k dispozici pro vizuální návrháře nebo 1 (jeden) pro typy, které jsou k dispozici pro vizuální návrháře.  
  
   > [!NOTE]
   >  Je nutné zaregistrovat vlastní nástroj samostatně pro každý jazyk, pro které chcete vlastní nástroj být k dispozici.  
  
    Například MSDataSetGenerator registruje sama sebe jednou pro každý jazyk:  
  
   ```  
   [HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\14.0\Generators\{164b10b9-b200-11d0-8c61-00a0c91e29d5}\MSDataSetGenerator]  
   @="Microsoft VB Code Generator for XSD"  
   "CLSID"="{E76D53CC-3D4F-40a2-BD4D-4F3419755476}"  
   "GeneratesDesignTimeSource"=dword:00000001  
  
   [HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\14.0\Generators\{fae04ec1-301f-11d3-bf4b-00c04f79efbc}\MSDataSetGenerator]  
   @="Microsoft C# Code Generator for XSD"  
   "CLSID"="{E76D53CC-3D4F-40a2-BD4D-4F3419755476}"  
   "GeneratesDesignTimeSource"=dword:00000001  
   ```  
  
## <a name="see-also"></a>Viz také  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSingleFileGenerator>   
 [Implementace generátorů tvořených jedním souborem](../../extensibility/internals/implementing-single-file-generators.md)   
 [Zveřejnění typů pro vizuální návrhářské nástroje](../../extensibility/internals/exposing-types-to-visual-designers.md)   
 [Představení objektu BuildManager](https://msdn.microsoft.com/library/50080ec2-c1c9-412c-98ef-18d7f895e7fa)