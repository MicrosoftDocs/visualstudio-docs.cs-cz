---
title: Návrh aplikací pro Windows Forms
ms.date: 08/09/2019
ms.topic: conceptual
helpviewer_keywords:
- Windows Forms Designer
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.openlocfilehash: 171cdffa569b342bdbc7dd0da1c8da218e1d622c
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "75589887"
---
# <a name="windows-forms-designer-overview"></a>Přehled nástroje Návrhář formulářů

Návrhář windows forms v sadě Visual Studio poskytuje řešení rychlého vývoje pro vytváření aplikací založených na formulářích Windows. Návrhář windows forms umožňuje snadno přidat ovládací prvky do formuláře, uspořádat je a napsat kód pro jejich události. Další informace o windows forms najdete v [tématu Windows Forms overview](/dotnet/framework/winforms/windows-forms-overview).

## <a name="functionality"></a>Funkce

Pomocí návrháře můžete:

- Přidejte do formuláře součásti, ovládací prvky dat nebo ovládací prvky založené na systému Windows.

- Poklepejte na formulář v návrháři `Load` a napište kód v události pro tento formulář nebo poklepejte na ovládací prvek ve formuláři a napište kód pro výchozí událost ovládacího prvku.

- Upravte vlastnost Text ovládacího prvku výběrem ovládacího prvku a zadáním názvu.

- Upravte umístění vybraného ovládacího prvku jeho přesunutím pomocí myši nebo kláves se šipkami. Podobně upravte umístění přesněji pomocí kláves Ctrl a kláves se šipkami. Nakonec upravte velikost ovládacího prvku pomocí kláves Shift a kláves se šipkami.

- Vyberte více ovládacích prvků tak, že při klepnutí vyberete **shift** nebo **ctrl.** Při použití **svěšení Shift**+click je prvním vybraným ovládacím prvkem dominantní ovládací prvek při zarovnání nebo manipulaci s velikostí. Při použití **ctrl**+click je dominantní poslední vybraný ovládací prvek, takže dominantní ovládací prvek se mění s každým novým přidaným ovládacím prvkem. Případně můžete vybrat více ovládacích prvků přetažením obdélníku výběru kolem ovládacích prvků, které chcete vybrat.

> [!NOTE]
> Pomocí Návrháře formulářů systému Windows, nikoli editoru prostředků, proveďte změny v souboru prostředku formuláře (*.resx).* Pokud upravíte soubor Resx založený na formuláři, zobrazí se upozornění, že změny provedené v Editoru prostředků mohou být ztraceny. Důvodem je, že Návrhář formulářů systému Windows generuje soubor Resx.

## <a name="see-also"></a>Viz také

- [Windows Forms – přehled](/dotnet/framework/winforms/windows-forms-overview)
- [Windows Forms – ovládací prvky](/dotnet/framework/winforms/controls/)
- [Vstup uživatele ve Formulářích Systému Windows](/dotnet/framework/winforms/user-input-in-windows-forms)
- [Datová vazba ve Windows Forms](/dotnet/framework/winforms/windows-forms-data-binding)
- [Vylepšení aplikací pro Windows Forms](/dotnet/framework/winforms/advanced/)
- <xref:System.Windows.Forms?displayProperty=fullName>Odkaz na rozhraní API
