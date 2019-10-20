---
title: -Edit (devenv.exe)
ms.date: 12/10/2018
ms.topic: reference
helpviewer_keywords:
- Edit Devenv switch
- Devenv, /Edit switch
- /Edit Devenv switch
ms.assetid: 02b3d6e7-a2b1-4d83-a747-aa8c2fb758b7
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 37d49dd7d191ad470639debc50fbed23d5066233
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/19/2019
ms.locfileid: "72654489"
---
# <a name="edit-devenvexe"></a>/Edit (devenv.exe)

Otevře zadaný soubor v existující instanci aplikace Visual Studio.

## <a name="syntax"></a>Syntaxe

```shell
devenv /Edit [File1[ FileN]...]
```

## <a name="arguments"></a>Arguments

- *Soubor1*

  Volitelné. Soubor, který se má otevřít v existující instanci sady Visual Studio. Pokud žádná instance sady Visual Studio neexistuje, vytvoří se nová instance se zjednodušeným rozložením okna a nástroj otevře v nové instanci příkaz *Soubor1* .

- *FileN*

  Volitelné. Jeden nebo více dalších souborů, které mají být otevřeny v existující instanci aplikace Visual Studio.

## <a name="remarks"></a>Poznámky

Pokud není zadán soubor, existující instance sady Visual Studio obdrží fokus. Pokud není zadán žádný soubor a instance aplikace Visual Studio neexistuje, nástroj vytvoří instanci s zjednodušeným rozložením okna.

Pokud je existující instance sady Visual Studio v modálním stavu, otevře se soubor v existující instanci, když Visual Studio ukončí modální stav. Tato situace může nastat například v případě, že je [dialogové okno Možnosti](../../ide/reference/options-dialog-box-visual-studio.md) otevřené.

Je-li otevřeno více než jedna instance sady Visual Studio, soubor je otevřen v naposledy otevřené instanci.

## <a name="example"></a>Příklad

První příklad otevře soubor `MyFile.cs` v existující instanci aplikace Visual Studio. Pokud instance sady Visual Studio neexistuje, nástroj otevře soubor v nové instanci. Druhý příklad je podobný, s tím rozdílem, že otevírá tři soubory místo pouze jednoho souboru.

```shell
devenv /edit MyFile.cs

devenv /edit MyFile1.cs MyFile2.cs MyFile3.cs
```

## <a name="see-also"></a>Viz také:

- [Přepínače příkazového řádku nástroje devenv](../../ide/reference/devenv-command-line-switches.md)
