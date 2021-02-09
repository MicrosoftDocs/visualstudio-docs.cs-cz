---
title: -LCID (devenv.exe)
description: Naučte se, jak použít přepínač příkazového řádku devenv pro LCID k nastavení výchozího jazyka používaného pro text, měnu a jiné hodnoty v rámci rozhraní IDE.
ms.custom: SEO-VS-2020
ms.date: 12/10/2018
ms.topic: reference
helpviewer_keywords:
- language default
- locale IDs, setting for IDE
- Devenv, /L switch
- Devenv, /LCID switch
- locale IDs
- L Devenv switch
- /L Devenv switch
- LCID devenv switch
- /LCID Devenv switch
ms.assetid: 3a3f4e70-ea66-4351-9d62-acb1dec30e8e
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 3e5aad581babafe882fccc13e8594aa60437d9df
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99852138"
---
# <a name="lcid-devenvexe"></a>/LCID (devenv.exe)

Nastaví výchozí jazyk, který se používá pro text, měnu a jiné hodnoty v rámci integrovaného vývojového prostředí (IDE).

## <a name="syntax"></a>Syntaxe

```shell
devenv {/LCID|/L} LocaleID
```

## <a name="arguments"></a>Argumenty

- *LocaleID*

  Povinná hodnota. Identifikátor národního prostředí (LCID) jazyka, který zadáte.

## <a name="remarks"></a>Poznámky

Načte rozhraní IDE a nastaví výchozí přirozený jazyk pro prostředí. Tato změna je trvalá mezi relacemi a IDE tuto změnu zobrazuje v   >    >    >  poli jazyk možností **nastavení prostředí mezinárodní nastavení**  >   .

Pokud zadaný jazyk není ve vašem systému k dispozici, `/LCID` přepínač se ignoruje.

V následující tabulce jsou uvedeny identifikátory LCID jazyků, které podporuje Visual Studio.

|Jazyk|LCID|
|--------------|----------|
|Čínština (zjednodušená)|2052|
|Čínština (tradiční)|1028|
|Čeština|1029|
|Angličtina|1033|
|Francouzština|1036|
|Němčina|1031|
|Italština|1040|
|Japonština|1041|
|Korejština|1042|
|Polština|1045|
|Portugalština (Brazílie)|1046|
|Ruština|1049|
|Španělština|3082|
|Turečtina|1055

## <a name="example"></a>Příklad

Tento příklad načte integrované vývojové prostředí (IDE) s řetězci České prostředky.

```shell
devenv /LCID 1033
```

## <a name="see-also"></a>Viz také

- [Devenv – přepínače příkazového řádku](../../ide/reference/devenv-command-line-switches.md)
- [Mezinárodní nastavení, Prostředí, dialogové okno Možnosti](../../ide/reference/international-settings-environment-options-dialog-box.md)
- [Přizpůsobení rozložení oken](../../ide/customizing-window-layouts-in-visual-studio.md)
