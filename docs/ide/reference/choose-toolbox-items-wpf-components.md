---
title: Výběr položek sady nástrojů, součásti WPF
ms.date: 06/21/2017
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- vs.chooseitems.wpfcomponents
helpviewer_keywords:
- WPF Components tab, Choose Toolbox Items dialog box
- Choose Toolbox Items dialog box, WPF Components tab
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 6d05e69acb414c08e752593fbfdb08246c3d14a2
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/26/2018
ms.locfileid: "31949617"
---
# <a name="choose-toolbox-items-wpf-components"></a>Výběr položek sady nástrojů, součásti WPF

Na této kartě z **výběr položek sady nástrojů** dialogové okno zobrazí seznam dostupných kontrolních mechanismů Windows Presentation Foundation (WPF) v místním počítači. Chcete-li zobrazit tento seznam, vyberte **výběr položek sady nástrojů** z **nástroje** nabídky k zobrazení **výběr položek sady nástrojů** dialogové okno a potom vyberte jeho **grafického subsystému WPF Součásti** kartě. Chcete-li seřadit uvedených součástí, vyberte záhlaví libovolného sloupce.

- Pokud je zaškrtnuto políčko vedle komponentu, ikona pro danou součást, zobrazí se v **sada nástrojů**.

    > [!TIP]
    > Chcete-li přidat ovládací prvek WPF do projektu dokument, který je otevřený pro úpravy, přetáhněte jeho **sada nástrojů** ikony na ploše zobrazení návrhu. Výchozí značky a kód pro součást jsou vloženy do projektu, můžete upravit. Další informace najdete v tématu [sada nástrojů](../../ide/reference/toolbox.md).

- Pokud není zaškrtnuto políčko vedle součásti, na odpovídající ikonu se odebere z **sada nástrojů**.

    > [!NOTE]
    > Součásti rozhraní .NET Framework v počítači nainstalována zůstanou dostupné, zda ikony pro ně zobrazí **sada nástrojů**.

Sloupce na **součásti WPF** karta obsahovat tyto informace:

**Jméno**

Zobrazí názvy ovládacích prvků WPF pro položky, které existují v registru počítače.

**obor názvů**

Zobrazuje hierarchii [rozhraní API třídy rozhraní .NET Framework](/dotnet/api/?view=netframework-4.7) obor názvů, který definuje strukturu součásti. Řazení v tomto sloupci seznam součástí, které jsou v rámci každý obor názvů rozhraní .NET Framework, který je nainstalován ve vašem počítači k dispozici.

**Název sestavení**

Zobrazí název sestavení rozhraní .NET Framework, která zahrnuje obor názvů pro jednotlivé komponenty. Řazení v tomto sloupci seznam obory názvů obsažené v každé sestavení rozhraní .NET Framework v počítači nainstalována.

**Adresář**

Zobrazí umístění sestavení rozhraní .NET Framework. Je výchozím umístěním pro všechny sestavení do globální mezipaměti sestavení. Další informace o globální mezipaměti sestavení, najdete v části [práce se sestaveními a globální mezipaměť sestavení](/dotnet/framework/app-domains/working-with-assemblies-and-the-gac).

## <a name="uielement-list"></a>Seznam prvků uživatelského rozhraní

### <a name="filter"></a>Filtr

Filtruje seznam ovládacích prvků WPF založené na řetězec, který zadáte do textového pole. Jsou uvedeny všechny shody z kteréhokoli čtyři sloupce.

**Zrušte zaškrtnutí**

Vymaže řetězec filtru.

**Procházet**

Otevře se **otevřete** dialogové okno, které umožňuje přejděte na sestavení, které obsahují ovládacích prvků WPF. Použijte k načtení sestavení, které nejsou umístěné v globální mezipaměti sestavení.

**Jazyk**

Zobrazuje lokalizovaného jazyka sestavení, které obsahuje vybraný ovládací prvek WPF.

## <a name="limitations"></a>Omezení

Přidání vlastního ovládacího prvku nebo <xref:System.Windows.Controls.UserControl> do sady nástrojů má následující omezení:

- Platí jenom pro vlastní ovládací prvky definované mimo aktuálního projektu.

- Nelze aktualizovat správně když změníte konfiguraci řešení z ladicí verze nebo verze pro ladění. Je to proto, že odkaz není odkaz na projekt, ale místo toho je pro sestavení na disku. Pokud ovládací prvek je součástí aktuální řešení, když změníte ladicí verze, pokračuje v projektu tak, aby odkazovaly ladicí verze ovládacího prvku.

Kromě toho, pokud je pro vlastní ovládací prvek a tato metadata návrhu metadata Určuje, že <xref:Microsoft.Windows.Design.ToolboxBrowsableAttribute> je nastaven na `false`, ovládacího prvku se nezobrazí v panelu nástrojů.

Vaše ovládací prvky přímo v jazyce XAML zobrazení můžete odkazovat pomocí mapování oboru názvů a sestavení pro ovládací prvek.

## <a name="see-also"></a>Viz také

- [Panel nástrojů](../../ide/reference/toolbox.md)
- [Začínáme s WPF](../../designers/getting-started-with-wpf.md)
