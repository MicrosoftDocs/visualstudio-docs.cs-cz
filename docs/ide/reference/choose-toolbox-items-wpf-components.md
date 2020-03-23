---
title: Výběr položek sady nástrojů, součásti WPF
ms.date: 06/21/2017
ms.topic: reference
f1_keywords:
- vs.chooseitems.wpfcomponents
helpviewer_keywords:
- WPF Components tab, Choose Toolbox Items dialog box
- Choose Toolbox Items dialog box, WPF Components tab
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 731fe05e90e01c60f0a7ff3a14917d6d7625bc1e
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "75570554"
---
# <a name="choose-toolbox-items-wpf-components"></a>Výběr položek sady nástrojů, součásti WPF

Na této kartě dialogového okna **Zvolit položky panelu nástrojů** se zobrazí seznam ovládacích prvků WPF (Windows Presentation Foundation), které jsou k dispozici v místním počítači. Chcete-li tento seznam zobrazit, vyberte z nabídky **Nástroje** vybrat **položky panelu nástrojů,** chcete-li zobrazit dialogové okno **Zvolit položky panelu nástrojů,** a pak vyberte jeho kartu **Komponenty WPF.** Chcete-li uvedené součásti seřadit, vyberte libovolné záhlaví sloupce.

- Je-li zaškrtnuto políčko vedle součásti, zobrazí se v **panelu nástrojů**ikona této součásti .

    > [!TIP]
    > Chcete-li přidat ovládací prvek WPF do dokumentu projektu, který je otevřený pro úpravy, přetáhněte jeho ikonu **Panelu nástrojů** na povrch návrhového pohledu. Výchozí značky a kód pro komponentu jsou vloženy do projektu, připravené pro úpravu. Další informace naleznete v [tématu Toolbox](../../ide/reference/toolbox.md).

- Pokud políčko vedle součásti není zaškrtnuto, bude odpovídající ikona odebrána z **panelu nástrojů**.

    > [!NOTE]
    > Součásti .NET nainstalované v počítači zůstávají k dispozici bez ohledu na to, zda jsou ikony pro ně zobrazeny v **panelu nástrojů**.

Sloupce na kartě **Komponenty WPF** obsahují následující informace:

**Název**

Uvádí názvy ovládacích prvků WPF, pro které existují položky v registru počítače.

**Namespace**

Zobrazí hierarchii oboru názvů [rozhraní .NET API,](/dotnet/api/?view=netframework-4.7) který definuje strukturu komponenty. Seřazením podle tohoto sloupce zobrazíte seznam dostupných součástí v rámci každého oboru názvů .NET nainstalovaného v počítači.

**Název sestavení**

Zobrazí název sestavení .NET, které obsahuje obor názvů pro každou součást. Seřazením podle tohoto sloupce zobrazíte seznam oborů názvů obsažených v každém sestavení rozhraní .NET nainstalovaném v počítači.

**Adresář**

Zobrazí umístění sestavení .NET. Výchozí umístění pro všechna sestavení je globální mezipaměť sestavení. Další informace o globální mezipaměti sestavení naleznete v [tématu Práce s sestaveními a Globální mezipaměť sestavení](/dotnet/framework/app-domains/working-with-assemblies-and-the-gac).

## <a name="uielement-list"></a>Seznam prvků uživatelského rozhraní

### <a name="filter"></a>Filtr

Filtruje seznam ovládacích prvků WPF na základě řetězce, který zadáte v textovém poli. Zobrazí se všechny shody z některého ze čtyř sloupců.

**Vymazat**

Vymaže řetězec filtru.

**Procházet**

Otevře dialogové okno **Otevřít,** které umožňuje přejít na sestavení, která obsahují ovládací prvky WPF. Slouží k načtení sestavení, které nejsou umístěny v globální mezipaměti sestavení.

**Jazyk**

Zobrazuje lokalizovaný jazyk sestavení, který obsahuje vybraný ovládací prvek WPF.

## <a name="limitations"></a>Omezení

Přidání vlastního ovládacího prvku nebo <xref:System.Windows.Controls.UserControl> panelu nástrojů má následující omezení:

- Funguje pouze pro vlastní ovládací prvky definované mimo aktuální projekt.

- Neaktualizuje správně při změně konfigurace řešení z ladění na verzi nebo z verze na ladění. Důvodem je, že odkaz není odkaz na projekt, ale je pro sestavení na disku místo. Pokud je ovládací prvek součástí aktuálního řešení, při změně z ladění na verzi, váš projekt nadále odkazovat ladicí verze ovládacího prvku.

Kromě toho pokud je metadata návrhu použita na vlastní ovládací prvek a tato metadata určují, že atribut `false` [Microsoft.Windows.Design.ToolboxBrowsableAttribute](/previous-versions/visualstudio/visual-studio-2010/bb547991(v=vs.100)) je nastaven na , ovládací prvek se nezobrazí v panelu nástrojů.

Ovládací prvky můžete odkazovat přímo v zobrazení XAML mapováním oboru názvů a sestavení pro ovládací prvek.

## <a name="see-also"></a>Viz také

- [Sada nástrojů](../../ide/reference/toolbox.md)
- [Začínáme s WPF (Windows Presentation Foundation)](../../designers/getting-started-with-wpf.md)
