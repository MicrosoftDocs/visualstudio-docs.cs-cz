---
title: Chyby a upozornění XAML
ms.date: 03/06/2018
ms.topic: conceptual
ms.assetid: 34eac8a0-7ec5-4c40-b97a-0126ed367931
author: karann-msft
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: f8a36a91f40fd4857e50d5262c1598ee096697e7
ms.sourcegitcommit: 22deb247ad951e4971f27fdab413b158415d0584
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81276464"
---
# <a name="xaml-errors-and-warnings"></a>Chyby a upozornění XAML

Při vytváření XAML Visual Studio analyzuje kód při psaní. Vlnovka se zobrazí na řádku kódu, když je zjištěna chyba. Když najedete přes vlnovku, získáte další informace o chybě nebo upozornění. U některých chyb a upozornění se zobrazí žárovka S rychlou akcí a klávesa **Ctrl**+**.** klávesová zkratka zobrazí možnosti, jak problém vyřešit.

## <a name="error-types"></a>Typy chyb

Na pozadí analyzuje xaml paralelně více nástrojů. Chyby XAML jsou rozděleny do jednoho z následujících tří typů na základě nástroje, který chybu zjistil:

|**Byla zjištěna chyba**|**Formát kódu chyby**|
| - |-----------------|
|Jazyková služba XAML (editor XAML)|XLSxxxx|
|Návrhář XAML|XDGxxxx|
|Úpravy a pokračování xAML|XECxxxx|

> [!Note]
> Ne všechny chyby nebo upozornění mají odpovídající kód. Tyto chyby jsou obvykle chyby návrháře XAML.

## <a name="suppress-xaml-designer-errors"></a>Potlačit chyby návrháře XAML

Otevřete dialogové okno **Volby** tak, že vyberete **Nástroje > Možnosti**a pak vyberte **Textový editor > XAML > Různé**.

Zrušením zaškrtnutí políčka **Zobrazit chyby zjištěné návrhářem XAML.**

![Potlačit chyby návrháře XAML](media/suppress_xaml_designer_errors.png)
