---
title: Úpravy s více kurzory
description: Při úpravách kódu ve Visual Studiu pro Mac vložte text na více místech.
author: cobey
ms.author: cobey
ms.date: 08/19/2019
ms.openlocfilehash: a21bebda057a772017fa1481e18f9801d1fbcbdf
ms.sourcegitcommit: 2975d722a6d6e45f7887b05e9b526e91cffb0bcf
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/20/2020
ms.locfileid: "75451445"
---
# <a name="multi-caret-editing"></a>Úpravy s více kurzory

Multi-stříška editace umožňuje přidat _n_ počet bodů vložení najednou. V režimu s více stříškami můžete do dokumentu přidat další stříšky buď kliknutím myši, nebo pomocí klávesových příkazů. Primární stříška je označena červeným kurzorem, zatímco sekundární stříšky přítomné ve světle modré barvě. Režim úprav více stříšky `ESC` lze vypnout pomocí klíče.

## <a name="enabling-multi-caret-editing"></a>Povolení editace více stříšky

### <a name="keyboard"></a>Klávesnice

Režim více stříšky můžete povolit pomocí klávesnice několika způsoby. V následující tabulce jsou uvedeny klávesové zkratky, které jsou k dispozici pro zadávání určitých režimů úprav více stříšky:

| Hotkey  | Akce                        | 
|---------| ------------------------------|
|  ⌥⇧.   | Vložit další odpovídající stříšku    | 
|  ⌥⇧;   | Vložit stříšky na všech odpovídajících | 
|  ⌥⇧,   | Odstranit poslední stříšku             | 
|  ⌥⇧/   | Přesunout poslední stříšku dolů          | 

Každé z těchto chování jsou ukotveny na aktuální pozici stříšky při vyvolání příkazu. Například pokud stříška je na začátku slova "jméno" a vyvolat "Vložit stříšky vůbec odpovídající" (?? ;) každá instance slova "jméno" v aktuálním dokumentu bude mít stříšku vloženou na začátku slova. Podobně, pokud vyvoláte příkaz "Vložit další odpovídající stříšku" (??). Tento příkaz lze vyvolat vícekrát.

![multi-stříška klávesnice](media/multi-caret-keyboard.gif)

## <a name="mousetouchpad"></a>Myš/touchpad

Pomocí kurzoru, můžete uvolnit vybrat konkrétní kurzor bodů pro vaše více stříšky. Zatímco klávesové zkratky jsou vázány na odpovídající řetězce, můžete ručně vložit stříšku kdekoli v dokumentu s kurzorem. Jakmile jsou stříšky nastaveny, každý z nich bude echo klíčové položky, které zadáte na klávesnici.

Chcete-li použít myš pro vložení více stříšky, musíte stisknout a podržet a kliknout na místo, kam chcete zadávat stříšky. Budete v režimu vkládání, dokud jsou klávesy drženy. Pokud vložíte stříšku na nesprávné místo, můžete ji odstranit tak, že budete pokračovat v držení a znovu kliknete na stejnou oblast. Jakmile budete mít všechny stříšky umístěny tam, kde je chcete, přestaňte stisknout tlačítka a začněte psát. Následující soubor GIF ukazuje jak výběr sady bodů vložení, tak odebrání chybně nastavených bodů.

![multi-stříška myš](media/multi-caret-mouse.gif)

## <a name="see-also"></a>Viz také

- [Rychlé akce (Visual Studio ve Windows)](/visualstudio/ide/quick-actions)
- [Refaktoringový kód (Visual Studio v systému Windows)](/visualstudio/ide/refactoring-in-visual-studio)
