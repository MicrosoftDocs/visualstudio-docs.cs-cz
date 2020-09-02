---
title: Nástroji. Soubory cílů | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: msbuild
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- .Targets files
- MSBuild, .Targets files
ms.assetid: f6d98eb4-d2fa-49b7-8e3c-bae1ca3cf596
caps.latest.revision: 20
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: bab229a3246ac91eaa652be67e98a68aab40e820
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "64811138"
---
# <a name="msbuild-targets-files"></a>MSBuild – soubory .Targets
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

[!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] obsahuje několik souborů. targets, které obsahují položky, vlastnosti, cíle a úkoly pro běžné scénáře. Tyto soubory jsou automaticky importovány do většiny [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] souborů projektu pro zjednodušení údržby a čitelnosti.  
  
 Projekty obvykle importují jeden nebo více souborů. targets pro definování svého procesu sestavení. Například [!INCLUDE[csprcs](../includes/csprcs-md.md)] projekt vytvořený pomocí [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] provede import Microsoft. CSharp. targets, který importuje Microsoft. Common. targets. [!INCLUDE[csprcs](../includes/csprcs-md.md)]Samotný projekt bude definovat položky a vlastnosti specifické pro daný projekt, ale standardní pravidla sestavení pro [!INCLUDE[csprcs](../includes/csprcs-md.md)] projekt jsou definována v importovaných souborech. targets.  
  
 `$(MSBuildToolsPath)`Hodnota určuje cestu těchto běžných souborů. targets. Pokud `ToolsVersion` je 4,0, soubory jsou v následujícím umístění: `WindowsInstallationPath\Microsoft.NET\Framework\v4.0.30319\`  
  
> [!NOTE]
> Informace o tom, jak vytvořit vlastní cíle, najdete v tématu [cíle](../msbuild/msbuild-targets.md). Informace o tom, jak použít `Import` element pro vložení souboru projektu do jiného souboru projektu, naleznete v tématu [Import element (MSBuild)](../msbuild/import-element-msbuild.md) a [How to: použijte stejný cíl ve více souborech projektu](../msbuild/how-to-use-the-same-target-in-multiple-project-files.md).  
  
## <a name="common-targets-files"></a>Obecný. Soubory cílů  
  
|. Soubor cílů|Popis|  
|-------------------|-----------------|  
|Microsoft. Common. targets|Definuje kroky ve standardním procesu sestavení pro [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] [!INCLUDE[csprcs](../includes/csprcs-md.md)] projekty a.<br /><br /> Importováno soubory Microsoft. CSharp. targets a Microsoft. VisualBasic. targets, které zahrnují následující příkaz: `<Import Project="Microsoft.Common.targets" />`|  
|Microsoft. CSharp. targets|Definuje kroky v procesu standardního sestavení pro projekty v jazyce Visual C#.<br /><br /> Importováno soubory projektu jazyka Visual C# (. csproj), které zahrnují následující příkaz: `<Import Project="$(MSBuildToolsPath)\Microsoft.CSharp.targets" />`|  
|Microsoft. VisualBasic. targets|Definuje kroky ve standardním procesu sestavení pro projekty Visual Basic.<br /><br /> Importováno pomocí Visual Basic soubory projektu (. vbproj), které zahrnují následující příkaz: `<Import Project="$(MSBuildToolsPath)\Microsoft.VisualBasic.targets" />`|  
  
## <a name="see-also"></a>Viz také  
 [Import – element (MSBuild)](../msbuild/import-element-msbuild.md)   
 [Referenční dokumentace nástroje MSBuild](../msbuild/msbuild-reference.md)  
 [Nástroji](msbuild.md)
