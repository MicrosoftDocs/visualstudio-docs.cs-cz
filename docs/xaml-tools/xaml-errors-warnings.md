---
title: Chyby a upozornění XAML
ms.date: 03/06/2018
ms.topic: reference
ms.assetid: 34eac8a0-7ec5-4c40-b97a-0126ed367931
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 9b46bf15390f12e7fb0873c7e4c39abf94530821
ms.sourcegitcommit: 57d96de120e0574e506dfd80bb7adfbac73f96be
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/24/2020
ms.locfileid: "85330415"
---
# <a name="xaml-errors-and-warnings"></a>Chyby a upozornění XAML

Při vytváření kódu XAML aplikace Visual Studio analyzuje kód při psaní. Při zjištění chyby se v řádku kódu zobrazí vlnovka. Najetí myší na vlnovku vám poskytne další informace o chybě nebo upozornění. V případě některých chyb a upozornění se zobrazí rychlá akce žárovky a pomocí **klávesy CTRL** + **.** Klávesová zkratka zobrazuje možnosti pro vyřešení problému.

## <a name="error-types"></a>Typy chyb

Na pozadí několik nástrojů analyzuje XAML paralelně. Chyby XAML jsou zařazeny do jednoho z následujících tří typů na základě nástroje, který zjistil chybu:

|**Zjistila se chyba**|**Formát kódu chyby**|
| - |-----------------|
|Služba jazyka XAML (Editor XAML)|XLSxxxx|
|Návrhář XAML|XDGxxxx|
|Upravit a pokračovat v XAML|XECxxxx|

> [!Note]
> Ne všechny chyby nebo upozornění mají odpovídající kód. Tyto chyby jsou obvykle Návrhář XAML chyby.

## <a name="suppress-xaml-designer-errors"></a>Potlačit chyby Návrhář XAML

Otevřete dialogové okno **Možnosti** tak, že vyberete **nástroje > možnosti**a pak vyberete **textový editor > XAML > různé**.

Zrušte zaškrtnuté políčko **Zobrazit chyby zjištěné návrhářem XAML** .

![Potlačit chyby Návrhář XAML](media/suppress_xaml_designer_errors.png)
