---
title: Nástroj MSBuild. Cílí na soubory | Dokumentace Microsoftu
ms.custom: ''
ms.date: 02/24/2017
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
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 3282495219e92da38fc90c9a98fa115791190d80
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/23/2018
ms.locfileid: "49834562"
---
# <a name="msbuild-targets-files"></a>MSBuild – soubory .targets
[!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] obsahuje několik *.targets* soubory, které obsahují položky, vlastnosti, cíle a úkoly pro běžné scénáře. Tyto soubory jsou automaticky importovány do většiny [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] soubory kvůli zjednodušení údržby a čitelnost projektu.  

 Projekty obvykle importují jeden nebo více *.targets* soubory pro definování jejich procesu sestavení. Například [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] projekt vytvořený v rámci [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] naimportuje *Microsoft.CSharp.targets* které importy *cílů Microsoft.Common.targets*. [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] Samotného projektu budou definovat položky a vlastnosti specifické pro daný projekt, ale standardní pravidla pro sestavení [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] projektu jsou definovány v importované *.targets* soubory.  

 `$(MSBuildToolsPath)` Hodnota Určuje cestu k těmto běžným *.targets* soubory. Pokud `ToolsVersion` 4.0, jsou soubory v následujícím umístění:  *\<WindowsInstallationPath > \Microsoft.NET\Framework\v4.0.30319\\*  

> [!NOTE]
>  Informace o tom, jak vytvořit vlastní cíle, naleznete v tématu [cíle](../msbuild/msbuild-targets.md). Informace o tom, jak používat `Import` element soubor projektu lze vložit do jiného souboru projektu, viz [Import – element (MSBuild)](../msbuild/import-element-msbuild.md) a [postupy: použití stejného cíle ve více souborech projektu](../msbuild/how-to-use-the-same-target-in-multiple-project-files.md).  

## <a name="common-targets-files"></a>Běžné soubory .targets  

| *.TARGETS* souboru | Popis |
|---------------------------------| - |
| *Cílů Microsoft.Common.targets* | Definuje kroky v procesu standardní sestavení pro [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] a [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] projekty.<br /><br /> Importované tímto seznamem *Microsoft.CSharp.targets* a *Microsoft.VisualBasic.targets* soubory, které zahrnují následující příkaz: `<Import Project="Microsoft.Common.targets" />` |
| *Microsoft.CSharp.targets* | Definuje kroky na standardní proces sestavení pro projekty Visual C#.<br /><br /> Importovaných projektovými soubory Visual C# (*.csproj*), mezi které patří následující příkaz: `<Import Project="$(MSBuildToolsPath)\Microsoft.CSharp.targets" />` |
| *Microsoft.VisualBasic.targets* | Definuje kroky na standardní proces sestavení pro projekty jazyka Visual Basic.<br /><br /> Importovaných projektovými soubory Visual Basic (*.vbproj*), mezi které patří následující příkaz: `<Import Project="$(MSBuildToolsPath)\Microsoft.VisualBasic.targets" />` |

## <a name="directorybuildtargets"></a>Directory.Build.targets
*Directory.Build.targets* je uživatelem definovaného souboru, který obsahuje vlastní nastavení pro projekty v adresáři. Tento soubor je automaticky importován z *cílů Microsoft.Common.targets* není-li vlastnost **ImportDirectoryBuildTargets** je nastavena na **false**.

## <a name="see-also"></a>Viz také:  
 [Import – element (MSBuild)](../msbuild/import-element-msbuild.md)   
 [Referenční dokumentace nástroje MSBuild](../msbuild/msbuild-reference.md)  
 [MSBuild](../msbuild/msbuild.md)
