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
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 991886289ac2c2ee06e37476169dff6d2354a52e
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/19/2019
ms.locfileid: "72659982"
---
# <a name="lcid-devenvexe"></a>/LCID (devenv.exe)

Nastaví výchozí jazyk, který se používá pro text, měnu a jiné hodnoty v rámci integrovaného vývojového prostředí (IDE).

## <a name="syntax"></a>Syntaxe

```shell
devenv {/LCID|/L} LocaleID
```

## <a name="arguments"></a>Arguments

- *LocaleID*

  Požadováno. Identifikátor národního prostředí (LCID) jazyka, který zadáte.

## <a name="remarks"></a>Poznámky

Načte rozhraní IDE a nastaví výchozí přirozený jazyk pro prostředí. Tato změna je trvalá mezi relacemi a IDE tuto změnu zobrazuje v dialogovém okně **nástroje**  > **možnosti**  > **prostředí**  > **mezinárodní nastavení**  > **jazyk** .

Pokud zadaný jazyk není ve vašem systému k dispozici, přepínač `/LCID` se ignoruje.

V následující tabulce jsou uvedeny identifikátory LCID jazyků, které podporuje Visual Studio.

|Jazyk|IDENTIFIKÁTORY|
|--------------|----------|
|Čínština (zjednodušená)|2052|
|Čínština (tradiční)|1028|
|Angličtina|1033|
|Francouzština|1036|
|Němčina|1031|
|Italština|1040|
|Japonština|1041|
|Korejština|1042|
|Španělština|3082|

## <a name="example"></a>Příklad

Tento příklad načte integrované vývojové prostředí (IDE) s řetězci České prostředky.

```shell
devenv /LCID 1033
```

## <a name="see-also"></a>Viz také:

- [Přepínače příkazového řádku nástroje devenv](../../ide/reference/devenv-command-line-switches.md)
- [Mezinárodní nastavení, Prostředí, dialogové okno Možnosti](../../ide/reference/international-settings-environment-options-dialog-box.md)
- [Přizpůsobení rozložení oken](../../ide/customizing-window-layouts-in-visual-studio.md)