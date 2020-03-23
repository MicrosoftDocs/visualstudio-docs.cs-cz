---
title: -LCID (devenv.exe)
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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: cabbf36adb5019543b3cfb72b0b0e56976517d2d
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "77557930"
---
# <a name="lcid-devenvexe"></a>/LCID (devenv.exe)

Nastaví výchozí jazyk používaný pro text, měnu a další hodnoty v rámci rozhraní IDE.

## <a name="syntax"></a>Syntaxe

```shell
devenv {/LCID|/L} LocaleID
```

## <a name="arguments"></a>Argumenty

- *Localeid*

  Povinná hodnota. Identifikátor národního prostředí (LCID) zadaného jazyka.

## <a name="remarks"></a>Poznámky

Načte rozhraní IDE a nastaví výchozí přirozený jazyk pro prostředí. Tato změna je mezi relacemi zachována a rozhraní IDE tuto změnu zobrazí v poli **Tools** > **Options** > **Environment** > International**Settings** > **Language.**

Pokud zadaný jazyk není v systému `/LCID` k dispozici, přepínač se ignoruje.

V následující tabulce jsou uvedeny kódy LCID jazyků podporovaných souborem Visual Studio.

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

Tento příklad načte ide s anglickými řetězci prostředků.

```shell
devenv /LCID 1033
```

## <a name="see-also"></a>Viz také

- [Devenv – přepínače příkazového řádku](../../ide/reference/devenv-command-line-switches.md)
- [Mezinárodní nastavení, Prostředí, dialogové okno Možnosti](../../ide/reference/international-settings-environment-options-dialog-box.md)
- [Přizpůsobení rozložení oken](../../ide/customizing-window-layouts-in-visual-studio.md)
