---
title: MSBuild. targets – soubory | Microsoft Docs
ms.date: 02/24/2017
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- .targets files
- MSBuild, .targets files
ms.assetid: f6d98eb4-d2fa-49b7-8e3c-bae1ca3cf596
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 4dc5df9c4eba4195400b6a41fa50a5c88257d70e
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/01/2020
ms.locfileid: "75566550"
---
# <a name="msbuild-targets-files"></a>MSBuild. targets – soubory
[!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] obsahuje několik souborů *. targets* , které obsahují položky, vlastnosti, cíle a úkoly pro běžné scénáře. Tyto soubory se automaticky importují do většiny [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] souborů projektu, aby se zjednodušila údržba a čitelnost.

 Projekty obvykle importují jeden nebo více souborů *. targets* pro definování svého procesu sestavení. Například [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] projekt vytvořený pomocí [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] importuje *Microsoft. CSharp. targets* , který importuje *Microsoft. Common. targets*. Samotný projekt [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] bude definovat položky a vlastnosti specifické pro daný projekt, ale standardní pravidla sestavení pro [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] projekt jsou definována v importovaných souborech *. targets* .

 Hodnota `$(MSBuildToolsPath)` Určuje cestu těchto běžných souborů *. targets* . Pokud je `ToolsVersion` 4,0, soubory jsou v následujícím umístění: *\<WindowsInstallationPath > \Microsoft.NET\Framework\v4.0.30319\\*

> [!NOTE]
> Informace o tom, jak vytvořit vlastní cíle, najdete v tématu [cíle](../msbuild/msbuild-targets.md). Informace o použití prvku `Import` pro vložení souboru projektu do jiného souboru projektu naleznete v tématu [Import element (MSBuild)](../msbuild/import-element-msbuild.md) a [How to: use the Target in a Multiple Project Files](../msbuild/how-to-use-the-same-target-in-multiple-project-files.md).

## <a name="common-targets-files"></a>Společné soubory. targets

| soubor *. targets* | Popis |
|---------------------------------| - |
| *Microsoft. Common. targets* | Definuje kroky ve standardním procesu sestavení pro projekty [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] a [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)].<br /><br /> Importováno soubory *Microsoft. CSharp. targets* a *Microsoft. VisualBasic. targets* , které zahrnují následující příkaz: `<Import Project="Microsoft.Common.targets" />` |
| *Microsoft.CSharp.targets* | Definuje kroky ve standardním procesu sestavení pro vizuální C# projekty.<br /><br /> Importováno pomocí C# souborů Visual Project ( *. csproj*), které zahrnují následující příkaz: `<Import Project="$(MSBuildToolsPath)\Microsoft.CSharp.targets" />` |
| *Microsoft.VisualBasic.targets* | Definuje kroky ve standardním procesu sestavení pro projekty Visual Basic.<br /><br /> Importováno pomocí Visual Basic soubory projektu ( *. vbproj*), které zahrnují následující příkaz: `<Import Project="$(MSBuildToolsPath)\Microsoft.VisualBasic.targets" />` |

## <a name="directorybuildtargets"></a>Directory. Build. targets
*Directory. Build. targets* je uživatelsky definovaný soubor, který poskytuje přizpůsobení projektům v adresáři. Tento soubor se automaticky naimportuje z *Microsoft. Common. targets* , pokud vlastnost **ImportDirectoryBuildTargets** není nastavená na **false**. Další informace získáte [přizpůsobením sestavení](customize-your-build.md).

## <a name="see-also"></a>Viz také:
- [Import – element (MSBuild)](../msbuild/import-element-msbuild.md)
- [Referenční dokumentace nástroje MSBuild](../msbuild/msbuild-reference.md)
- [MSBuild](../msbuild/msbuild.md)
