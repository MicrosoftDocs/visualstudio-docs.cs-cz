---
title: -Out (devenv.exe)
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: reference
helpviewer_keywords:
- errors [Visual Studio], builds
- Devenv, /out switch
- builds [Visual Studio], logs
- error logs [Visual Studio], command-line build errors
- error logs [Visual Studio]
- /out Devenv switch
- out Devenv switch
- builds [Visual Studio], errors
- output files, build errors
ms.assetid: 9002d8c2-36d4-451c-b489-8f01932f31f7
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: a5778cb281ca6edcf8045620aee049b0f115a50a
ms.sourcegitcommit: 54c65f81a138fc1e8ff1826f7bd9dcec710618cc
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/19/2018
ms.locfileid: "51948241"
---
# <a name="out-devenvexe"></a>/Out (devenv.exe)
Určuje soubor k uložení a zobrazení chyb při spuštění, sestavování, znovu sestavit nebo nasadit řešení.

## <a name="syntax"></a>Syntaxe

```cmd
devenv /out FileName
```

## <a name="arguments"></a>Arguments
 `FileName`

 Požadováno. Cesta a název souboru, který se zobrazí chyby při vytváření spustitelného souboru.

## <a name="remarks"></a>Poznámky
 Pokud je zadaný název souboru, který neexistuje, vytvoří se soubor automaticky. Pokud soubor již existuje, výsledky jsou připojena k existující obsah souboru.

 Chyby sestavení příkazového řádku se zobrazují v **příkaz** okno a Tvůrce řešení zobrazení **výstup** okna. Tato možnost je užitečná, pokud jsou spuštěny bezobslužném sestavování a potřebujete pro zobrazení výsledků.

## <a name="example"></a>Příklad
 Tento příklad se spouští `MySolution` a zapíše chyby do souboru `MyErrorLog.txt`.

```cmd
devenv /run "C:\Documents and Settings\someuser\My Documents\Visual Studio\Projects\MySolution\MySolution.sln" /out "C:\MyErrorLog.txt"
```

## <a name="see-also"></a>Viz také

- [Přepínače příkazového řádku nástroje devenv](../../ide/reference/devenv-command-line-switches.md)
- [Nebo spuštění (devenv.exe)](../../ide/reference/run-devenv-exe.md)
- [/ Sestavení (devenv.exe)](../../ide/reference/build-devenv-exe.md)
- [/ Sestavení (devenv.exe)](../../ide/reference/rebuild-devenv-exe.md)
- [/ Nasazení (devenv.exe)](../../ide/reference/deploy-devenv-exe.md)