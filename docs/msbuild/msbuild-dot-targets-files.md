---
title: MSBuild .targets Files | Dokumenty společnosti Microsoft
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
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "77633353"
---
# <a name="msbuild-targets-files"></a>Soubory MSBuild .targets

MSBuild obsahuje několik souborů *.targets,* které obsahují položky, vlastnosti, cíle a úkoly pro běžné scénáře. Tyto soubory jsou automaticky importovány do většiny souborů projektu sady Visual Studio pro zjednodušení údržby a čitelnosti.

 Projekty obvykle importují jeden nebo více souborů *.targets* k definování jejich procesu sestavení. Například projekt Jazyka C# vytvořený aplikací Visual Studio importuje *microsoft.csharp.targets,* který importuje *Microsoft.Common.targets*. Samotný projekt C# definuje položky a vlastnosti specifické pro tento projekt, ale standardní pravidla sestavení pro projekt Jazyka C# jsou definována v importovaných souborech *.targets.*

 Hodnota `$(MSBuildToolsPath)` určuje cestu těchto společných souborů *.targets.* Pokud `ToolsVersion` je 4.0, soubory jsou v následujícím umístění: * \<WindowsInstallationPath\\>\Microsoft.NET\Framework\v4.0.30319*

> [!NOTE]
> Informace o tom, jak vytvořit vlastní cíle, naleznete v [tématu Cíle](../msbuild/msbuild-targets.md). Informace o použití `Import` prvku k vložení souboru projektu do jiného souboru projektu naleznete v [tématech Import elementu (MSBuild)](../msbuild/import-element-msbuild.md) a [Postup: Použijte stejný cíl ve více souborech projektu](../msbuild/how-to-use-the-same-target-in-multiple-project-files.md).

## <a name="common-targets-files"></a>Běžné soubory .targets

| *Soubor .targets* | Popis |
|---------------------------------| - |
| *Microsoft.Common.targets* | Definuje kroky ve standardním procesu sestavení pro projekty jazyka A C#.<br /><br /> Importováno soubory *Microsoft.CSharp.targets* a *Microsoft.VisualBasic.targets,* které obsahují následující příkaz:`<Import Project="Microsoft.Common.targets" />` |
| *Cíle Microsoft.CSharp.* | Definuje kroky ve standardním procesu sestavení pro projekty Visual C#.<br /><br /> Importováno soubory projektu Visual C# (*.csproj*), které obsahují následující příkaz:`<Import Project="$(MSBuildToolsPath)\Microsoft.CSharp.targets" />` |
| *Microsoft.VisualBasic.targets* | Definuje kroky ve standardním procesu sestavení pro projekty jazyka.<br /><br /> Importováno soubory projektu jazyka Visual Basic (*.vbproj*), které obsahují následující příkaz:`<Import Project="$(MSBuildToolsPath)\Microsoft.VisualBasic.targets" />` |

## <a name="directorybuildtargets"></a>Directory.Build.targets

*Directory.Build.targets* je uživatelem definovaný soubor, který poskytuje vlastní nastavení projektům v adresáři. Tento soubor je automaticky importován z *microsoft.common.targets,* pokud vlastnost **ImportDirectoryBuildTargets** není nastavena na **false**. Další informace [například přizpůsobte sestavení](customize-your-build.md).

## <a name="see-also"></a>Viz také

- [Prvek importu (MSBuild)](../msbuild/import-element-msbuild.md)
- [Odkaz na sestavení msbuild](../msbuild/msbuild-reference.md)
- [Msbuild](../msbuild/msbuild.md)
