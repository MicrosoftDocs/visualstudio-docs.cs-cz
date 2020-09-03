---
title: Znaky kódování a zalomení řádku
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "75588587"
---
# <a name="encodings-and-line-endings"></a>Kódování a konce řádků

Následující znaky jsou interpretovány jako zalomení řádků v aplikaci Visual Studio:

- CR LF: návrat vozík + řádek, znaky Unicode 000D + 000A

- LF: line feed, 000A znaků Unicode

- NEL: další řádek, znak Unicode 0085

- LS: oddělovač řádků, znak Unicode 2028

- PS: oddělovač odstavců, znak Unicode 2029

Text, který je zkopírován z jiných aplikací, uchovává původní kódování a znaky zalomení řádku. Například pokud kopírujete text z programu Poznámkový blok a vložíte ho do textového souboru v aplikaci Visual Studio, text má stejné nastavení jako v poznámkovém bloku.

Když otevřete soubor, který obsahuje jiné znaky zalomení řádku, může se zobrazit dialogové okno s dotazem, zda by měly být nekonzistentní znaky konců řádků normalizovány a jaký typ konců řádků zvolit.

## <a name="advanced-save-options"></a>Rozšířené možnosti uložení

Pomocí **File**  >  dialogového okna**Upřesnit možnosti uložení** můžete určit typ znaků konce řádku, které chcete. Můžete také změnit kódování souboru se stejným nastavením.

![Dialogové okno Upřesnit možnosti uložení](media/line_endings.png)

> [!NOTE]
> Pokud nevidíte **možnost Upřesnit možnosti uložení** v nabídce **soubor** , můžete ji přidat. Zvolte **nástroje**, **přizpůsobit**a pak zvolte kartu **příkazy** . V rozevíracím seznamu **panel nabídek** zvolte možnost **soubor**a poté klikněte na tlačítko **Přidat příkaz** . V dialogovém okně **Přidat příkaz** v části **kategorie**zvolte možnost **soubor**a potom v seznamu **příkazy** zvolte **možnost Upřesnit možnosti uložení**. Zvolte **OK** a pak zvolte tlačítko **Přesunout dolů** a přesuňte příkaz na libovolné místo v nabídce. Kliknutím na tlačítko **Zavřít** zavřete dialogové okno **přizpůsobit** . Další informace najdete v tématu [přizpůsobení nabídek a panelů nástrojů](../ide/how-to-customize-menus-and-toolbars-in-visual-studio.md#customizing_menu).
>
> Alternativně můžete k dialogovému oknu **Upřesnit možnosti uložení** získat přístup tak, že kliknete na **soubor**  >  **Uložit \<file\> jako**. V dialogovém okně **Uložit soubor jako** vyberte trojúhelník rozevíracího seznamu vedle tlačítka **Uložit** a vyberte **Uložit s kódováním**.

## <a name="see-also"></a>Viz také

- [Funkce editoru kódu](../ide/writing-code-in-the-code-and-text-editor.md)
