---
title: Úpravy s více kurzory
description: Při úpravách kódu v Visual Studio pro Mac vložte text do více umístění.
author: cobey
ms.author: cobey
ms.date: 08/19/2019
ms.openlocfilehash: a21bebda057a772017fa1481e18f9801d1fbcbdf
ms.sourcegitcommit: 8e123bcb21279f2770b28696995450270b4ec0e9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/25/2019
ms.locfileid: "75451445"
---
# <a name="multi-caret-editing"></a>Úpravy s více kurzory

Úpravy s více blikajícími kurzory umožňují přidávat _n_ číslic v jednom okamžiku. Když jste v režimu více blikajících kurzorů, můžete k dokumentu přidat další blikající kurzory buď pomocí kliknutí myší, nebo přes příkazy klávesnice. Primární stříška je označena červeným kurzorem, zatímco sekundární blikající kurzory jsou přítomny v barvě s světlou modrou. Režim úprav víceřádkového kurzoru je možné zakázat prostřednictvím `ESC`ho klíče.

## <a name="enabling-multi-caret-editing"></a>Povolení úprav více blikajících kurzorů

### <a name="keyboard"></a>Klávesnice

Můžete povolit režim více blikajících kurzorů přes klávesnici několika způsoby. Následující tabulka uvádí klávesové zkratky, které jsou k dispozici pro zadání konkrétních režimů úprav více blikajících kurzorů:

| Klávesová zkratka  | Akce                        | 
|---------| ------------------------------|
|  ⌥⇧.   | Vložit další vyhovující blikající kurzor    | 
|  ⌥⇧;   | Vložit blikající kurzory na všechny vyhovující | 
|  ⌥⇧,   | Odebrat poslední blikající kurzor             | 
|  ⌥⇧/   | Přesunout poslední blikající kurzor dolů          | 

Každé z těchto chování je ukotveno k aktuální pozici blikajícího kurzoru při vyvolání příkazu. Například pokud je blikající kurzor na začátku slova "Name" a vyvoláte "vložit blikající kurzory" na všechny vyhovující "(⌥ ⇧;) Každá instance slova "název" v aktuálním dokumentu bude mít vložen znak stříšky na začátek slova. Podobně platí, že pokud zavoláte příkaz "vložit další vyhovující blikající kurzor" (⌥ ⇧.), umístí se kurzor na další instanci slova "Name". Tento příkaz lze vyvolat několikrát.

![klávesnice s více blikajícími znaky](media/multi-caret-keyboard.gif)

## <a name="mousetouchpad"></a>Myš a touchpad

Pomocí kurzoru můžete zdarma vybrat konkrétní body vložení pro vaše více blikajících kurzorů. I když jsou klávesové zkratky vázány na vyhovující řetězce, můžete ručně vložit blikající kurzor na libovolné místo v dokumentu. Jakmile nastavíte blikající kurzory, každá z nich bude zobrazovat klíčovou položku, kterou zadáte na klávesnici.

Chcete-li použít myš k vložení více blikajících kurzorů, je nutné stisknout a podržet ⌘ ⌥ a kliknout na místo, kde chcete zadat blikající kurzory. Pokud jsou ⌘ klíče ⌥, budete v režimu vkládání. Pokud vložíte blikající kurzor do nesprávného umístění, můžete ho odebrat tak, že budete pokračovat ve ⌘ ⌥ a znovu kliknete na stejnou oblast. Až budete mít všechny blikající kurzory tam, kde je chcete, zastavte stisknutí klávesy ⌥ ⌘ a začněte psát. Následující obrázek GIF znázorňuje výběr sady bodů vložení i odebrání nesprávně nastavených bodů.

![myš s více blikajícími kurzory](media/multi-caret-mouse.gif)

## <a name="see-also"></a>Viz také:

- [Rychlé akce (Visual Studio ve Windows)](/visualstudio/ide/quick-actions)
- [Refaktoring kódu (Visual Studio ve Windows)](/visualstudio/ide/refactoring-in-visual-studio)
