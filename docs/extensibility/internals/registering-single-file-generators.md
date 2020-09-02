---
title: Registrují se generátory jednoho souboru | Microsoft Docs
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "80705815"
---
# <a name="registering-single-file-generators"></a>Registrace generátorů tvořených jedním souborem
Chcete-li zpřístupnit vlastní nástroj v nástroji [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] , je nutné jej zaregistrovat, aby jej bylo [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] možné vytvořit a přidružit ho k určitému typu projektu.

### <a name="to-register-a-custom-tool"></a>Registrace vlastního nástroje

1. Zaregistrujte vlastní knihovnu DLL nástrojů buď v [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] místním registru, nebo v systémovém registru, v části HKEY_CLASSES_ROOT.

    Tady je například registrační informace pro vlastní nástroj spravované MSDataSetGenerator, který se dodává s [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] :

   ```
   [HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\14.0\CLSID\{E76D53CC-3D4F-40A2-BD4D-4F3419755476}]
   @="COM+ class: Microsoft.VSDesigner.CodeGenerator.TypedDataSourceGenerator.DataSourceGeneratorWrapper"
   "InprocServer32"="C:\\WINDOWS\\system32\\mscoree.dll"
   "ThreadingModel"="Both"
   "Class"="Microsoft.VSDesigner.CodeGenerator.TypedDataSourceGenerator.DataSourceGeneratorWrapper"
   "Assembly"="Microsoft.VSDesigner, Version=14.0.0.0, Culture=Neutral, PublicKeyToken=b03f5f7f11d50a3a"
   ```

2. Vytvořte klíč registru v požadovaném [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] podregistru v části generátor \\ *GUID* , kde *GUID* je identifikátor GUID definovaný systémem projektu nebo službou konkrétního jazyka. Název klíče se bude programovým názvem vlastního nástroje. Klíč vlastního nástroje má následující hodnoty:

   - (Výchozí)

        Nepovinný parametr. Poskytuje uživatelsky přívětivý popis vlastního nástroje. Tento parametr je nepovinný, ale doporučený.

   - CLSID

        Povinná hodnota. Určuje identifikátor knihovny tříd součásti modelu COM, která implementuje <xref:Microsoft.VisualStudio.Shell.Interop.IVsSingleFileGenerator> .

   - GeneratesDesignTimeSource

        Povinná hodnota. Určuje, zda jsou typy ze souborů vytvořených tímto vlastním nástrojem zpřístupněny vizuálním návrhářům. Hodnota tohoto parametru musí být (nula) 0 pro typy, které nejsou k dispozici pro vizuální návrháře nebo (jedna) 1 pro typy, které jsou k dispozici pro vizuální návrháře.

   > [!NOTE]
   > Vlastní nástroj musíte zaregistrovat samostatně pro každý jazyk, pro který chcete, aby byl vlastní nástroj dostupný.

    Například MSDataSetGenerator registruje sebe sama pro každý jazyk:

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
- [Úvod do objektu BuildManager](https://msdn.microsoft.com/library/50080ec2-c1c9-412c-98ef-18d7f895e7fa)
