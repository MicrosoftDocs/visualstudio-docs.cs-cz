---
title: Kódování a řádku znaky konce
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
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/01/2020
ms.locfileid: "75588587"
---
# <a name="encodings-and-line-endings"></a>Kódování a řádku konce

Následující znaky jsou interpretovány jako zalomení řádků v sadě Visual Studio:

- CR-LF: Zalomení řádku a řádek informačního kanálu, znaky Unicode 000 D + 000A

- LF: LF, znak Unicode 000A

- NEL: Další řádek znak Unicode 0085

- LS: Oddělovač řádků, znak Unicode 2028

- PS: Oddělovač odstavců, znak Unicode 2029

Text, který se zkopíruje z jiné aplikace udržuje původní kódování a znaky konce řádku. Například při kopírování textu z programu Poznámkový blok a vložte ho do textového souboru v sadě Visual Studio, text má stejné nastavení, jako v poznámkovém bloku.

Při otevření souboru obsahujícího znaky konce řádku různých, může se zobrazit dialogové okno s dotazem, zda by měly být normalizovány znaky konců řádků nekonzistentní a jaký typ řádku dělí na tlačítko.

## <a name="advanced-save-options"></a>Pokročilé nastavení uložení

Můžete použít **souboru** > **pokročilé nastavení uložení** dialogové okno určit typ má znaky konce řádku. Můžete také změnit kódování souboru se stejným nastavením.

![Dialogové okno pokročilé nastavení uložení](media/line_endings.png)

> [!NOTE]
> Pokud nevidíte **pokročilé nastavení uložení** na **souboru** nabídku, můžete ho přidat. Zvolte **nástroje**, **přizpůsobit**a pak zvolte kartu **příkazy** . V rozevíracím seznamu **panel nabídek** zvolte možnost **soubor**a poté klikněte na tlačítko **Přidat příkaz** . V **přidat příkaz** dialogovém okně **kategorie**, zvolte **souboru**a pak v **příkazy** klikněte na položku  **Pokročilé nastavení uložení**. Zvolte **OK** a klikněte na tlačítko **přesunout dolů** tlačítko příkaz přesunout na libovolné místo v nabídce. Zvolte **zavřete** zavřete **vlastní** dialogové okno. Další informace najdete v tématu [přizpůsobení nabídek a panelů nástrojů](../ide/how-to-customize-menus-and-toolbars-in-visual-studio.md#customizing_menu).
>
> Alternativně můžete přistupovat **pokročilé nastavení uložení** dialogové okno výběrem **souboru** > **Uložit \<souboru\> jako**. V **uložit soubor jako** dialogové okno Vyberte trojúhelník rozevíracího seznamu vedle položky **Uložit** tlačítko a zvolte **uložit s kódováním**.

## <a name="see-also"></a>Viz také:

- [Funkce editoru kódu](../ide/writing-code-in-the-code-and-text-editor.md)
