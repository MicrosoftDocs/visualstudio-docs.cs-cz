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
ms.openlocfilehash: 3faa9ca73592722a950f9914437884c33122070e
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "77633353"
---
# <a name="msbuild-targets-files"></a>MSBuild – soubory .targets

Nástroj MSBuild obsahuje několik souborů *. targets* , které obsahují položky, vlastnosti, cíle a úkoly pro běžné scénáře. Tyto soubory se automaticky importují do většiny souborů projektu sady Visual Studio, aby se zjednodušila údržba a čitelnost.

 Projekty obvykle importují jeden nebo více souborů *. targets* pro definování svého procesu sestavení. Například projekt C# vytvořený v aplikaci Visual Studio bude importovat *Microsoft. CSharp. targets* , který importuje *Microsoft. Common. targets*. Samotný projekt C# bude definovat položky a vlastnosti specifické pro daný projekt, ale standardní pravidla sestavení pro projekt C# jsou definována v importovaných souborech *. targets* .

 `$(MSBuildToolsPath)`Hodnota určuje cestu těchto běžných souborů *. targets* . Pokud `ToolsVersion` je 4,0, soubory jsou v následujícím umístění: * \<WindowsInstallationPath> \Microsoft.NET\Framework\v4.0.30319 \\ *

> [!NOTE]
> Informace o tom, jak vytvořit vlastní cíle, najdete v tématu [cíle](../msbuild/msbuild-targets.md). Informace o tom, jak použít `Import` element pro vložení souboru projektu do jiného souboru projektu, naleznete v tématu [Import element (MSBuild)](../msbuild/import-element-msbuild.md) a [How to: použijte stejný cíl ve více souborech projektu](../msbuild/how-to-use-the-same-target-in-multiple-project-files.md).

## <a name="common-targets-files"></a>Společné soubory. targets

| soubor *. targets* | Popis |
|---------------------------------| - |
| *Microsoft. Common. targets* | Definuje kroky ve standardním procesu sestavení pro projekty Visual Basic a C#.<br /><br /> Importováno soubory *Microsoft. CSharp. targets* a *Microsoft. VisualBasic. targets* , které zahrnují následující příkaz: `<Import Project="Microsoft.Common.targets" />` |
| *Microsoft. CSharp. targets* | Definuje kroky v procesu standardního sestavení pro projekty v jazyce Visual C#.<br /><br /> Importováno soubory projektu jazyka Visual C# (*. csproj*), které zahrnují následující příkaz: `<Import Project="$(MSBuildToolsPath)\Microsoft.CSharp.targets" />` |
| *Microsoft. VisualBasic. targets* | Definuje kroky ve standardním procesu sestavení pro projekty Visual Basic.<br /><br /> Importováno pomocí Visual Basic soubory projektu (*. vbproj*), které zahrnují následující příkaz: `<Import Project="$(MSBuildToolsPath)\Microsoft.VisualBasic.targets" />` |

## <a name="directorybuildtargets"></a>Directory. Build. targets

*Directory. Build. targets* je uživatelsky definovaný soubor, který poskytuje přizpůsobení projektům v adresáři. Tento soubor se automaticky naimportuje z *Microsoft. Common. targets* , pokud vlastnost **ImportDirectoryBuildTargets** není nastavená na **false**. Další informace získáte [přizpůsobením sestavení](customize-your-build.md).

## <a name="see-also"></a>Viz také

- [Import – element (MSBuild)](../msbuild/import-element-msbuild.md)
- [Referenční dokumentace nástroje MSBuild](../msbuild/msbuild-reference.md)
- [Nástroji](../msbuild/msbuild.md)
