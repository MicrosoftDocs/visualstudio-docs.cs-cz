---
title: Chyby a upozornění XAML
description: Přečtěte si o chybách a upozorněních XAML v aplikaci Visual Studio, včetně způsobu, jakým jsou chyby zařazeny do kategorií, jak získat informace o chybách a jak najít možnosti jejich oprav.
ms.custom: SEO-VS-2020
ms.date: 03/06/2018
ms.topic: error-reference
ms.assetid: 34eac8a0-7ec5-4c40-b97a-0126ed367931
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 3b0c785bef80f59c165f251b2986f0db1eb8bc63
ms.sourcegitcommit: ba966327498a0f67d2df2291c60b62312f40d1d3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/06/2020
ms.locfileid: "93414474"
---
# <a name="xaml-errors-and-warnings"></a>Chyby a upozornění XAML

Při vytváření kódu XAML aplikace Visual Studio analyzuje kód při psaní. Při zjištění chyby se v řádku kódu zobrazí vlnovka. Najetí myší na vlnovku vám poskytne další informace o chybě nebo upozornění. V případě některých chyb a upozornění se zobrazí rychlá akce žárovky a pomocí **klávesy CTRL** + **.** Klávesová zkratka zobrazuje možnosti pro vyřešení problému.

## <a name="error-types"></a>Typy chyb

Na pozadí několik nástrojů analyzuje XAML paralelně. Chyby XAML jsou zařazeny do jednoho z následujících tří typů na základě nástroje, který zjistil chybu:

|**Zjistila se chyba**|**Formát kódu chyby**|**Verze sady Visual Studio**|
| - |-----------------| - |
|Služba jazyka XAML (Editor XAML)|XLSxxxx| Všechny verze |
|Návrhář XAML|XDGxxxx| Všechny verze | 
|Upravit a pokračovat (XAML)|XECxxxx| Visual Studio 2019 verze 16,1 nebo starší |
|Opětovné načítání XAML za provozu | XHRxxxx | Visual Studio 2019 verze 16,2 nebo novější |

Další podrobnosti o opětovném brandingu úpravy v jazyce XAML & pokračování jako XAML Hot Loading najdete v našem [poznámkách k verzi](/visualstudio/releases/2019/release-notes-v16.2#wpfuwp-tooling) .

> [!Note]
> Ne všechny chyby nebo upozornění mají odpovídající kód. Tyto chyby jsou obvykle Návrhář XAML chyby.

## <a name="suppress-xaml-designer-errors"></a>Potlačit chyby Návrhář XAML

Otevřete dialogové okno **Možnosti** tak, že vyberete **nástroje > možnosti** a pak vyberete **textový editor > XAML > různé**.

Zrušte zaškrtnuté políčko **Zobrazit chyby zjištěné návrhářem XAML** .

![Potlačit chyby Návrhář XAML](media/suppress_xaml_designer_errors.png)