---
title: -UseEnv (devenv.exe)
ms.date: 01/10/2019
ms.topic: reference
f1_keywords:
- VC.Project.UseEnvVars.ExcludePath
- VC.Project.UseEnvVars.LibraryPath
- VC.Project.UseEnvVars.SourcePath
- VC.Project.UseEnvVars.Include
- VC.Project.UseEnvVars.Path
- VC.Project.UseEnvVars.ReferencePath
helpviewer_keywords:
- UseEnv switch
- /UseEnv Devenv switch
- Devenv, /UseEnv
ms.assetid: 2dd14603-a61b-42d2-ba31-427a0ee8a799
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 16443b30ccf6ba03a01df0234695d27e4cd909af
ms.sourcegitcommit: 88f576ac32af31613c1a10c1548275e1ce029f4f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/23/2019
ms.locfileid: "71186487"
---
# <a name="useenv-devenvexe"></a>/UseEnv (devenv.exe)

Spustí Visual Studio a načte určité proměnné prostředí pro kompilaci.

> [!NOTE]
> Tento přepínač je nainstalován se sadou **vývoj desktopových aplikací pomocí C++** pracovního vytížení.

## <a name="syntax"></a>Syntaxe

```shell
devenv /UseEnv {SolutionName|ProjectName}
```

## <a name="arguments"></a>Arguments

- *SolutionName*

  Úplná cesta a název souboru řešení.

- *ProjectName*

  Úplná cesta a název souboru projektu.

## <a name="remarks"></a>Poznámky

Tento přepínač ovlivňuje rozhraní IDE sady Visual Studio ve vlastnostech projektu pro **adresáře VC + +** . Pokud zadáte `/UseEnv` přepínač, uzel **adresáře VC + +** zobrazí hodnoty proměnných prostředí PATH, include, LIBPATH a lib. (Zobrazí se taky hodnoty pro **zdrojové adresáře** a **vyloučené adresáře**.) V opačném případě uzel nahradí proměnné prostředí pěti hodnotami adresáře: **Spustitelné adresáře**, **adresáře zahrnutí**, adresáře **odkazů**, **adresáře knihoven**a **adresáře knihovny WinRT**.

> [!TIP]
> Přístup k vlastnostem projektu získáte tak, že kliknete pravým tlačítkem na C++ projekt a vyberete **vlastnosti**. V dialogovém okně **stránky vlastností** vyberte možnost **Vlastnosti konfigurace** a potom **adresáře VC + +** .

Pokud je pro tento přepínač zadán název projektu, nástroj zobrazí proměnné prostředí pro všechny projekty v rámci nadřazeného řešení projektu.

## <a name="example"></a>Příklad

Následující příklad spustí sadu Visual Studio a načte proměnné prostředí na stránky `MySolution` vlastností řešení.

```shell
devenv.exe /useenv "%USERPROFILE%\source\repos\MySolution\MySolution.sln"
```

## <a name="see-also"></a>Viz také:

- [Přepínače příkazového řádku nástroje devenv](../../ide/reference/devenv-command-line-switches.md)
- [Stránka vlastností adresářů VC + + (Windows)](/cpp/build/reference/vcpp-directories-property-page)
