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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "75570554"
---
# <a name="choose-toolbox-items-wpf-components"></a>Výběr položek sady nástrojů, součásti WPF

Tato karta dialogového okna **zvolit položky sady nástrojů** zobrazí seznam ovládacích prvků Windows Presentation Foundation (WPF), které jsou k dispozici v místním počítači. Chcete-li zobrazit tento seznam, vyberte možnost **zvolit položky sady nástrojů** v nabídce **nástroje** , chcete-li zobrazit dialogové okno **zvolit položky sady nástrojů** a pak vyberte kartu **komponenty WPF** . Pokud chcete uvedené součásti seřadit, vyberte libovolné záhlaví sloupce.

- Pokud je vybráno zaškrtávací políčko vedle komponenty, zobrazí se v **sadě nástrojů**ikona této součásti.

    > [!TIP]
    > Chcete-li přidat ovládací prvek WPF do dokumentu projektu, který je otevřen pro úpravy, přetáhněte ikonu **panelu nástrojů** na zobrazení Návrh plochu. Výchozí značky a kód pro komponentu jsou vloženy do projektu, který je připraven k úpravám. Další informace najdete v tématu [Sada nástrojů](../../ide/reference/toolbox.md).

- Pokud je zaškrtnutí políčka vedle komponenty vymazáno, bude z **panelu nástrojů**odebrána odpovídající ikona.

    > [!NOTE]
    > Komponenty rozhraní .NET nainstalované v počítači zůstávají dostupné bez ohledu na to, zda jsou ikony pro ně zobrazeny v sadě **nástrojů**.

Sloupce na kartě **komponenty WPF** obsahují následující informace:

**Name**

Obsahuje seznam názvů ovládacích prvků WPF, pro které existují položky v registru počítače.

**Obor názvů**

Zobrazuje hierarchii oboru názvů [rozhraní .NET API](/dotnet/api/?view=netframework-4.7) , který definuje strukturu komponenty. Pokud chcete zobrazit seznam dostupných součástí v rámci každého oboru názvů .NET nainstalovaného v počítači, seřaďte tento sloupec.

**Název sestavení**

Zobrazuje název sestavení .NET, které zahrnuje obor názvů pro jednotlivé komponenty. Seřadit v tomto sloupci pro výpis oborů názvů obsažených v každém sestavení .NET nainstalovaném v počítači.

**Adresář**

Zobrazuje umístění sestavení .NET. Výchozím umístěním pro všechna sestavení je globální mezipaměť sestavení (GAC). Další informace o globální mezipaměti sestavení (GAC) najdete v tématu [práce se sestaveními a globální mezipamětí sestavení](/dotnet/framework/app-domains/working-with-assemblies-and-the-gac).

## <a name="uielement-list"></a>Seznam prvků uživatelského rozhraní

### <a name="filter"></a>Filtr

Filtruje seznam ovládacích prvků WPF v závislosti na řetězci, který zadáte do textového pole. Zobrazí se všechny shody ze všech čtyř sloupců.

**Vymazat**

Vymaže řetězec filtru.

**Procházet**

Otevře dialogové okno **otevřít** , které umožňuje přejít na sestavení, která obsahují ovládací prvky WPF. Použijte k načtení sestavení, která nejsou umístěna v globální mezipaměti sestavení (GAC).

**Jazyk**

Zobrazuje lokalizovaný jazyk sestavení, který obsahuje vybraný ovládací prvek WPF.

## <a name="limitations"></a>Omezení

Přidání vlastního ovládacího prvku nebo <xref:System.Windows.Controls.UserControl> sady nástrojů má následující omezení:

- Funguje pouze pro vlastní ovládací prvky definované mimo aktuální projekt.

- Se neaktualizuje správně při změně konfigurace řešení z ladění na verzi nebo z verze na ladění. Důvodem je, že odkaz není odkazem na projekt, ale je místo toho pro sestavení na disku. Pokud je ovládací prvek součástí aktuálního řešení, při změně z ladění na verzi je váš projekt nadále odkazovat na ladicí verzi ovládacího prvku.

Navíc platí, že pokud se pro vlastní ovládací prvek aplikují metadata pro dobu návrhu a tato metadata určují, že [Microsoft. Windows. Design. ToolboxBrowsableAttribute](/previous-versions/visualstudio/visual-studio-2010/bb547991(v=vs.100)) je nastaven na `false` , ovládací prvek se v sadě nástrojů nezobrazuje.

Můžete odkazovat na ovládací prvky přímo v zobrazení XAML mapováním oboru názvů a sestavení pro váš ovládací prvek.

## <a name="see-also"></a>Viz také

- [Sada nástrojů](../../ide/reference/toolbox.md)
- [Začínáme s WPF (Windows Presentation Foundation)](../../designers/getting-started-with-wpf.md)
