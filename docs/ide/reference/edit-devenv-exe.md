---
title: -Edit (devenv.exe)
description: Přečtěte si, jak použít přepínač příkazového řádku devenv k otevření zadaného souboru v existující instanci sady Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 12/10/2018
ms.topic: reference
helpviewer_keywords:
- Edit Devenv switch
- Devenv, /Edit switch
- /Edit Devenv switch
ms.assetid: 02b3d6e7-a2b1-4d83-a747-aa8c2fb758b7
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 45d0b1342ea0e53c4897881ebb5cfee0a7241d6b
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99882072"
---
# <a name="edit-devenvexe"></a>/Edit (devenv.exe)

Otevře zadaný soubor v existující instanci aplikace Visual Studio.

## <a name="syntax"></a>Syntaxe

```shell
devenv /Edit [File1[ FileN]...]
```

## <a name="arguments"></a>Argumenty

- *Soubor1*

  Nepovinný parametr. Soubor, který se má otevřít v existující instanci sady Visual Studio. Pokud žádná instance sady Visual Studio neexistuje, vytvoří se nová instance se zjednodušeným rozložením okna a nástroj otevře v nové instanci příkaz *Soubor1* .

- *FileN*

  Nepovinný parametr. Jeden nebo více dalších souborů, které mají být otevřeny v existující instanci aplikace Visual Studio.

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

## <a name="see-also"></a>Viz také

- [Devenv – přepínače příkazového řádku](../../ide/reference/devenv-command-line-switches.md)
