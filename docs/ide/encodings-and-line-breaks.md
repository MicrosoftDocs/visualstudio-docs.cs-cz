---
title: Kódování a zalomení řádků
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.Encoding
helpviewer_keywords:
- line breaks
- encoding
- Visual Studio, encoding
- editors, line breaks
- line break characters
- Visual Studio, line break characters
ms.assetid: 8f9b3ffc-7b8d-44f4-87cb-dc29105be12d
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 6448b553c1da9e697bca3860cb8507727c99cc08
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "75588587"
---
# <a name="encodings-and-line-endings"></a>Kódování a zakončení čar

Následující znaky jsou interpretovány jako konce řádků v sadě Visual Studio:

- CR LF: Návrat vozíku + posuv řádků, znaky Unicode 000D + 000A

- LF: Přívod řádku, znak Unicode 000A

- NEL: Další řádek, Unicode znak 0085

- LS: Oddělovač čar, znak Unicode 2028

- PS: Oddělovač odstavců, unicode znak 2029

Text, který je zkopírován z jiných aplikací, zachová původní znaky kódování a zalomení řádku. Pokud například zkopírujete text z poznámkového bloku a vložíte jej do textového souboru v sadě Visual Studio, má text stejné nastavení jako v poznámkovém bloku.

Když otevřete soubor s různými znaky zalomení řádku, může se zobrazit dialogové okno s dotazem, zda mají být normalizovány nekonzistentní znaky zalomení řádku a jaký typ zalomení řádků zvolit.

## <a name="advanced-save-options"></a>Rozšířené možnosti ukládání

Pomocí dialogového okna**Možnosti rozšířeného uložení** **souboru** > můžete určit požadovaný typ znaků zalomení řádku. Můžete také změnit kódování souboru se stejným nastavením.

![Dialogové okno Upřesnit možnosti uložení](media/line_endings.png)

> [!NOTE]
> Pokud v nabídce **Soubor** nevidíte **rozšířené možnosti ukládání,** můžete je přidat. Zvolte **Nástroje**, **Přizpůsobit**a pak zvolte kartu **Příkazy.** V rozevíracím seznamu **Panel nabídek** zvolte **Soubor**a pak zvolte tlačítko **Přidat příkaz.** V dialogovém okně **Přidat příkaz** v části **Kategorie**zvolte **Soubor**a potom v seznamu **Příkazy** zvolte **Upřesnit možnosti uložení**. Zvolte **OK** a pak zvolte tlačítko **Přesunout dolů,** chcete-li příkaz přesunout na libovolné místo v nabídce. Zvolte **Zavřít,** chcete-li zavřít dialogové okno **Přizpůsobit.** Další informace naleznete v [tématu Přizpůsobení nabídek a panelů nástrojů](../ide/how-to-customize-menus-and-toolbars-in-visual-studio.md#customizing_menu).
>
> Případně můžete získat přístup k dialogovému oknu **Upřesnit možnosti uložení** tak, že zvolíte **Soubor** > ** \<uložit soubor\> jako**. V dialogovém okně **Uložit soubor jako** zvolte rozevírací trojúhelník vedle tlačítka **Uložit** a zvolte Uložit **s kódováním**.

## <a name="see-also"></a>Viz také

- [Funkce editoru kódu](../ide/writing-code-in-the-code-and-text-editor.md)
