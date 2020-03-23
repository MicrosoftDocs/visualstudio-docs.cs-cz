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
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 35808b27964b3ca8fa0488f1be2ce6dc5530b3dd
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "75596391"
---
# <a name="useenv-devenvexe"></a>/UseEnv (devenv.exe)

Spustí visual studio a načte určité proměnné prostředí pro kompilaci.

> [!NOTE]
> Tento přepínač je nainstalován s vývojem plochy s úlohou **C++.**

## <a name="syntax"></a>Syntaxe

```shell
devenv /UseEnv {SolutionName|ProjectName}
```

## <a name="arguments"></a>Argumenty

- *SolutionName*

  Úplná cesta a název souboru řešení.

- *Projectname*

  Úplná cesta a název souboru projektu.

## <a name="remarks"></a>Poznámky

Tento přepínač ovlivňuje ide sady Visual Studio ve vlastnostech projektu pro **adresáře VC++**. Pokud zadáte `/UseEnv` přepínač, uzel **Adresáře VC++** zobrazí hodnoty pro proměnné prostředí PATH, INCLUDE, LIBPATH a LIB. (Zobrazuje také hodnoty pro **zdrojové adresáře** a **vyloučit adresáře**.) V opačném případě uzel nahradí proměnné prostředí pěti hodnotami adresářů: **spustitelné adresáře**, **zahrnout adresáře**, **referenční adresáře**, **adresáře knihovny**a **adresáře WinRT knihovny**.

> [!TIP]
> Přístup k vlastnostem projektu získáte klepnutím pravým tlačítkem myši na projekt jazyka C++ a výběrem **příkazu Vlastnosti**. V dialogovém okně **Stránky vlastností** vyberte **Vlastnosti konfigurace** a potom **adresáře VC++**.

Pokud je pomocí tohoto přepínače zadán název projektu, nástroj zobrazí proměnné prostředí pro všechny projekty v rámci nadřazeného řešení projektu.

## <a name="example"></a>Příklad

Následující příklad spustí visual studio a načte proměnné `MySolution` prostředí do stránek vlastností řešení.

```shell
devenv.exe /useenv "%USERPROFILE%\source\repos\MySolution\MySolution.sln"
```

## <a name="see-also"></a>Viz také

- [Devenv – přepínače příkazového řádku](../../ide/reference/devenv-command-line-switches.md)
- [Stránka vlastností adresářů VC++ (Windows)](/cpp/build/reference/vcpp-directories-property-page)
