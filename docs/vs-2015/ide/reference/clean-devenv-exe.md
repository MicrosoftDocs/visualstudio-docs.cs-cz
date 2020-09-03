---
title: -Clean (devenv.exe) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
helpviewer_keywords:
- builds [Team System], cleaning files
- clean Devenv switch
- /clean Devenv switch
- Devenv, /clean switch
ms.assetid: 79929dfd-22c9-4cec-a0d0-a16f15b8f7e4
caps.latest.revision: 15
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 043e9373f242523b7925a9ae775be6789f7cfc20
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "72660875"
---
# <a name="clean-devenvexe"></a>/Clean (devenv.exe)
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Vyčistí všechny zprostředkující soubory a výstupní adresáře.

## <a name="syntax"></a>Syntaxe

```
devenv FileName /Clean [ /project projectnameorfile [/projectconfig name ] ]
```

## <a name="arguments"></a>Argumenty
 `FileName` Požadovanou. Úplná cesta a název souboru řešení nebo souboru projektu.

 /Project je `ProjName` nepovinný. Cesta a název souboru projektu v rámci řešení. Můžete zadat relativní cestu ze `SolutionName` složky do souboru projektu nebo zobrazovaný název projektu nebo úplnou cestu a název souboru projektu.

 /ProjectConfig je `ProjConfigName` nepovinný. Název konfigurace sestavení projektu, který má být použit při čištění `/project` pojmenovaného.

## <a name="remarks"></a>Poznámky
 Tento přepínač provádí stejnou funkci jako příkaz v nabídce **Vyčistit řešení** v integrovaném vývojovém prostředí (IDE).

 Uzavřete řetězce, které obsahují mezery, do dvojitých uvozovek.

 Souhrnné informace o vyčištění a sestavení, včetně chyb, lze zobrazit v **příkazovém** okně nebo v jakémkoli souboru protokolu, který je zadán s `/out` přepínačem.

## <a name="example"></a>Příklad
 První příklad vyčistí `MySolution` řešení pomocí výchozí konfigurace zadané v souboru řešení.

 Druhý příklad vyčistí projekt `CSharpConsoleApp` pomocí `Debug` konfigurace sestavení projektu v rámci `Debug` Konfigurace řešení `MySolution` .

```
Devenv "C:\Documents and Settings\someuser\My Documents\Visual Studio\Projects\MySolution\MySolution.sln" /Clean

devenv "C:\Documents and Settings\someuser\My Documents\Visual Studio\Projects\MySolution\MySolution.sln" /Clean /project "CSharpWinApp\CSharpWinApp.csproj" /projectconfig "Debug"
```

## <a name="see-also"></a>Viz také
 [Přepínač příkazového řádku devenv](../../ide/reference/devenv-command-line-switches.md) [/Build (devenv.exe)](../../ide/reference/build-devenv-exe.md) [/Rebuild (devenv.exe)](../../ide/reference/rebuild-devenv-exe.md) [/out (devenv.exe)](../../ide/reference/out-devenv-exe.md)
