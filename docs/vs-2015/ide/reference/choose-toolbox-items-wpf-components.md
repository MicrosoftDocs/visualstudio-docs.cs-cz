---
title: Zvolit položky panelu nástrojů, komponenty WPF | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- vs.chooseitems.wpfcomponents
helpviewer_keywords:
- WPF Components tab, Choose Toolbox Items dialog box
- Choose Toolbox Items dialog box, WPF Components tab
ms.assetid: 6ce1d178-88c0-4295-8915-59fdeedabb11
caps.latest.revision: 17
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 5c7967635d8e5d64907587fcd1a9b4d84a31d569
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/19/2019
ms.locfileid: "72660919"
---
# <a name="choose-toolbox-items-wpf-components"></a>Výběr položek sady nástrojů, součásti WPF
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Tato karta dialogového okna **zvolit položky sady nástrojů** zobrazí seznam ovládacích prvků Windows Presentation Foundation (WPF), které jsou k dispozici v místním počítači. Chcete-li zobrazit tento seznam, vyberte možnost **zvolit položky sady nástrojů** v nabídce **nástroje** , chcete-li zobrazit dialogové okno **zvolit položky sady nástrojů** a pak vyberte kartu **komponenty WPF** . Pokud chcete uvedené součásti seřadit, vyberte libovolné záhlaví sloupce.

- Pokud je vybráno zaškrtávací políčko vedle komponenty, zobrazí se v **sadě nástrojů**ikona této součásti.

  > [!TIP]
  > Chcete-li přidat instanci ovládacího prvku WPF do dokumentu projektu otevřeného pro úpravy, přetáhněte ikonu **panelu nástrojů** na zobrazení Návrh plochu. Výchozí značky a kód pro komponentu jsou vloženy do projektu, který je připraven k úpravám. Další informace naleznete v tématu [How to: manage a Window panel nástrojů](https://msdn.microsoft.com/a022c3fe-298c-4a59-a48f-b050da90ebc2) a [How to: manipulace s kartami nástrojů](https://msdn.microsoft.com/21285050-cadd-455a-b1f5-a2289a89c4db).

- Pokud je zaškrtnutí políčka vedle komponenty vymazáno, bude z **panelu nástrojů** odebrána odpovídající ikona.

  > [!NOTE]
  > Součásti .NET Framework nainstalované v počítači zůstávají dostupné bez ohledu na to, jestli jsou ikony pro ně zobrazené v sadě **nástrojů**.

  Sloupce na kartě **komponenty WPF** obsahují následující informace:

  Název obsahuje seznam názvů ovládacích prvků WPF, pro které existují položky v registru počítače.

  Obor názvů zobrazuje hierarchii oboru názvů [knihovny tříd NIB: .NET Framework](https://msdn.microsoft.com/6c4f3a62-6a0f-41f2-9d52-ee0b13686f29) , který definuje strukturu komponenty. Pokud chcete zobrazit seznam dostupných součástí v rámci každého oboru názvů .NET Framework nainstalovaného v počítači, seřaďte tento sloupec.

  Název sestavení zobrazuje název .NET Framework sestavení, které obsahuje obor názvů pro jednotlivé komponenty. Pokud chcete zobrazit seznam oborů názvů obsažených v každém .NET Framework sestavení nainstalovaném na vašem počítači, proveďte řazení v tomto sloupci.

  Adresář zobrazuje umístění sestavení .NET Framework. Výchozím umístěním pro všechna sestavení je globální mezipaměť sestavení (GAC). Další informace o globální mezipaměti sestavení (GAC) najdete v tématu [práce se sestaveními a globální mezipamětí sestavení](https://msdn.microsoft.com/library/8a18e5c2-d41d-49ef-abcb-7c27e2469433).

## <a name="uielement-list"></a>Seznam prvků uživatelského rozhraní
 **Filtr** Filtruje seznam ovládacích prvků WPF v závislosti na řetězci, který zadáte do textového pole. Zobrazí se všechny shody ze všech čtyř sloupců.

 **Vymazat** Vymaže řetězec filtru.

 **Procházet** Otevře dialogové okno **otevřít** , které umožňuje přejít na sestavení, která obsahují ovládací prvky WPF. Použijte k načtení sestavení, která nejsou umístěna v globální mezipaměti sestavení (GAC).

 **Jazyk** Zobrazuje lokalizovaný jazyk sestavení, který obsahuje vybraný ovládací prvek WPF.

## <a name="limitations"></a>Omezení
 Přidání vlastního ovládacího prvku nebo <xref:System.Windows.Controls.UserControl> do panelu nástrojů má následující omezení.

- Funguje pouze pro vlastní ovládací prvky definované mimo aktuální projekt.

- Se neaktualizuje správně při změně konfigurace řešení z ladění na verzi nebo z verze na ladění. Důvodem je, že odkaz není odkazem na projekt, ale je místo toho pro sestavení na disku. Pokud je ovládací prvek součástí aktuálního řešení, při změně z ladění na verzi je váš projekt nadále odkazovat na ladicí verzi ovládacího prvku.

  Navíc platí, že pokud jsou metadata návrhu použita na vlastní ovládací prvek a tato metadata určují, že [ToolboxBrowsableAttribute](/previous-versions/visualstudio/visual-studio-2010/bb547991(v=vs.100)) je nastavena na `false`, ovládací prvek se nezobrazí v sadě nástrojů.

  Můžete odkazovat na ovládací prvky přímo v zobrazení XAML mapováním oboru názvů a sestavení pro váš ovládací prvek. Další informace naleznete v tématu [How to: import oboru názvů do jazyka XAML](https://msdn.microsoft.com/6cda7c7a-369c-47dd-9c2d-13a35dcf737c).

## <a name="see-also"></a>Viz také:

- [Dialogové okno zvolit položky sady nástrojů (Visual Studio)](https://msdn.microsoft.com/bd07835f-18a8-433e-bccc-7141f65263bb)
- [Panel nástrojů](../../ide/reference/toolbox.md)
- [Postupy: použití ovládacího prvku WPF třetí strany v aplikaci WPF](https://msdn.microsoft.com/f4c0b601-3818-4f9f-85e5-77905f3b427f)
- [Návrhář WPF](https://msdn.microsoft.com/c6c65214-8411-4e16-b254-163ed4099c26)