---
title: -Edit (devenv.exe)
ms.date: 12/10/2018
ms.topic: reference
helpviewer_keywords:
- Edit Devenv switch
- Devenv, /Edit switch
- /Edit Devenv switch
ms.assetid: 02b3d6e7-a2b1-4d83-a747-aa8c2fb758b7
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: d180d5a5d723d8085537f2993aac022d74df2c08
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "75595693"
---
# <a name="edit-devenvexe"></a>/Edit (devenv.exe)

Otevře zadaný soubor v existující instanci sady Visual Studio.

## <a name="syntax"></a>Syntaxe

```shell
devenv /Edit [File1[ FileN]...]
```

## <a name="arguments"></a>Argumenty

- *Soubor1*

  Nepovinný parametr. Soubor otevřít v existující instanci sady Visual Studio. Pokud neexistuje žádná instance sady Visual Studio, vytvoří se nová instance se zjednodušeným rozložením okna a nástroj otevře *soubor 1* v nové instanci.

- *Soubor N*

  Nepovinný parametr. Jeden nebo více dalších souborů, které chcete otevřít v existující instanci sady Visual Studio.

## <a name="remarks"></a>Poznámky

Pokud soubor není zadán, existující instance sady Visual Studio obdrží fokus. Pokud není zadán žádný soubor a neexistuje žádná instance sady Visual Studio, nástroj vytvoří instanci se zjednodušeným rozložením okna.

Pokud je existující instance sady Visual Studio v modálním stavu, soubor se otevře v existující instanci, když Visual Studio ukončí modální stav. K této situaci může například dojít, když je otevřeno [dialogové okno Možnosti.](../../ide/reference/options-dialog-box-visual-studio.md)

Pokud je otevřena více než jedna instance sady Visual Studio, soubor se otevře v naposledy otevřené instanci.

## <a name="example"></a>Příklad

První příklad otevře `MyFile.cs` soubor v existující instanci sady Visual Studio. Pokud instance sady Visual Studio neexistuje, nástroj otevře soubor v nové instanci. Druhý příklad je podobný s tím rozdílem, že otevře tři soubory namísto pouze jednoho souboru.

```shell
devenv /edit MyFile.cs

devenv /edit MyFile1.cs MyFile2.cs MyFile3.cs
```

## <a name="see-also"></a>Viz také

- [Devenv – přepínače příkazového řádku](../../ide/reference/devenv-command-line-switches.md)
