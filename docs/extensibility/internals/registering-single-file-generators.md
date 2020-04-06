---
title: Registrace generátorů jednotlivých souborů | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- registration, custom tools
- custom tools, defining registry settings
ms.assetid: db7592c0-1273-4843-9617-6e2ddabb6ca8
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 1cea2ebba4739695393447a36e9842ade1670954
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80705815"
---
# <a name="registering-single-file-generators"></a>Registrace generátorů tvořených jedním souborem
Chcete-li vlastní nástroj [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]zpřístupnit v aplikaci , musíte jej zaregistrovat, aby [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] jej bylo možné vytvořit k vytvoření instance a přidružit k určitému typu projektu.

### <a name="to-register-a-custom-tool"></a>Registrace vlastního nástroje

1. Zaregistrujte vlastní soubor DLL [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] nástroje buď v místním registru, nebo v systémovém registru v části HKEY_CLASSES_ROOT.

    Například zde je informace o registraci spravovaného vlastního nástroje MSDataSetGenerator, který je dodáván s [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]:

   ```
   [HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\14.0\CLSID\{E76D53CC-3D4F-40A2-BD4D-4F3419755476}]
   @="COM+ class: Microsoft.VSDesigner.CodeGenerator.TypedDataSourceGenerator.DataSourceGeneratorWrapper"
   "InprocServer32"="C:\\WINDOWS\\system32\\mscoree.dll"
   "ThreadingModel"="Both"
   "Class"="Microsoft.VSDesigner.CodeGenerator.TypedDataSourceGenerator.DataSourceGeneratorWrapper"
   "Assembly"="Microsoft.VSDesigner, Version=14.0.0.0, Culture=Neutral, PublicKeyToken=b03f5f7f11d50a3a"
   ```

2. Vytvořte klíč registru [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] v požadovaném\\podregistru v části*Identifikátor GUID* generátorů, kde *identifikátor GUID* je identifikátor GUID definovaný systémem nebo službou projektu konkrétního jazyka. Název klíče se stane programovým názvem vlastního nástroje. Vlastní klíč nástroje má následující hodnoty:

   - (Výchozí)

        Nepovinný parametr. Poskytuje uživatelsky přívětivý popis vlastního nástroje. Tento parametr je volitelný, ale doporučený.

   - Identifikátor clsid

        Povinná hodnota. Určuje identifikátor knihovny tříd komponenty MODELU COM, která implementuje <xref:Microsoft.VisualStudio.Shell.Interop.IVsSingleFileGenerator>.

   - GenerujedesignTimeSource

        Povinná hodnota. Označuje, zda jsou typy ze souborů vytvořených tímto vlastním nástrojem zpřístupněny vizuálním návrhářům. Hodnota tohoto parametru musí být (nula) 0 pro typy, které nejsou k dispozici vizuální návrháři nebo (jeden) 1 pro typy, které jsou k dispozici vizuální návrháři.

   > [!NOTE]
   > Vlastní nástroj je nutné zaregistrovat samostatně pro každý jazyk, pro který má být vlastní nástroj k dispozici.

    Například MSDataSetGenerator registruje sám jednou pro každý jazyk:

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
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsSingleFileGenerator>
- [Implementace generátorů tvořených jedním souborem](../../extensibility/internals/implementing-single-file-generators.md)
- [Zveřejnění typů pro vizuální návrháře](../../extensibility/internals/exposing-types-to-visual-designers.md)
- [Úvod k objektu BuildManager](https://msdn.microsoft.com/library/50080ec2-c1c9-412c-98ef-18d7f895e7fa)
