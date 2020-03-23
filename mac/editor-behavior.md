---
title: Formátování kódu
description: Tento článek popisuje různé možnosti, které lze použít k úpravě chování textového editoru v sadě Visual Studio for Mac
author: cobey
ms.author: cobey
ms.date: 05/06/2018
ms.assetid: 81EE4460-26EB-4BB0-9297-932E1F88E4B8
ms.openlocfilehash: 20363d5497ea5897cb2685ca838da44b8c21d3df
ms.sourcegitcommit: 2975d722a6d6e45f7887b05e9b526e91cffb0bcf
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/20/2020
ms.locfileid: "67823176"
---
# <a name="editor-behavior"></a>Chování editoru

Editor chování lze nastavit tak, aby kód, který má být formátován, jak je napsáno. Tyto akce jsou nastaveny v části **Předvolby > sady Visual Studio > textový editor > chování**a některé z více běžně používaných funkcí jsou popsány níže:

![Možnosti chování editoru](media/source-editor-image9.png)

* Odpovídající uzavírací svorky lze přidat automaticky do kódu při vytváření nových tříd, metod nebo vlastností. Je-li vybrána tato `{` možnost, `}`bude psaní automaticky přidávat .
* Průběžně formátování kódu je spouštěno stisknutím znaku, například středníkem nebo závorkami, které budou emulují nastavené předvolby formátování.
* Můžete také zvolit formátování souboru při jeho uložení, což umožňuje psaní kódu podle potřeby a ponechá ide zodpovědný za formátování kódu, jak je nastaveno existující předvolby.
* Odsazení lze nastavit na žádné, automatické nebo inteligentní. Tyto následující:
  * Žádný - nastaví stříška na začátek dalšího řádku
  * Auto - nastaví stříška na stejný sloupec na dalším řádku
  * Smart - odrážky na následujícím řádku na základě kódu
* Chování rozdělení textu se liší mezi ose a pro účely navigace textový editor potřebuje vědět, kde slova začínají nebo končí. Formátování lze nastavit na Unix nebo Windows.

Můžete také nastavit pravidla formátování pro XML, CSS, HTML a JSON.

## <a name="see-also"></a>Viz také

- [Předvolby stylu kódu (Visual Studio ve Windows)](/visualstudio/ide/code-styles-and-quick-actions)
