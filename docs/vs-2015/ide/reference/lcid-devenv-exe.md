---
title: -LCID (devenv. exe) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
helpviewer_keywords:
- language default
- locale IDs, setting for IDE
- Devenv, /LCID switch
- locale IDs
- /l Devenv switch
- LCID devenv switch
- /lcid Devenv switch
ms.assetid: 3a3f4e70-ea66-4351-9d62-acb1dec30e8e
caps.latest.revision: 15
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: badb88abdf4b3ffd6140cb587b2b0add20630925
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/19/2019
ms.locfileid: "72672704"
---
# <a name="lcid-devenvexe"></a>/LCID (devenv.exe)
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Nastaví výchozí jazyk používaný pro text, měnu a jiné hodnoty v rámci integrovaného vývojového prostředí (IDE).

## <a name="syntax"></a>Syntaxe

```
devenv {/LCID|/l} LocaleID
```

## <a name="arguments"></a>Arguments
 `LocaleID` nutné. Identifikátor LCID (ID národního prostředí) jazyka, který zadáte.

## <a name="remarks"></a>Poznámky
 Načte rozhraní IDE a nastaví výchozí přirozený jazyk pro prostředí. Tato změna je trvalá mezi relacemi a odráží se v podokně **Nastavení mezinárodního** prostředí v dialogovém okně **Možnosti** v integrovaném vývojovém **prostředí** (IDE).

 Pokud zadaný jazyk není v systému uživatele k dispozici, přepínač/LCID se ignoruje.

 V následující tabulce jsou uvedeny identifikátory LCID jazyků podporované nástrojem [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)].

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

```
devenv /LCID 1033
```

## <a name="see-also"></a>Viz také
 [Parametry příkazového řádku devenv](../../ide/reference/devenv-command-line-switches.md) – [mezinárodní nastavení, prostředí, dialogové okno Možnosti](../../ide/reference/international-settings-environment-options-dialog-box.md) [přizpůsobení rozložení oken](../../ide/customizing-window-layouts-in-visual-studio.md)
