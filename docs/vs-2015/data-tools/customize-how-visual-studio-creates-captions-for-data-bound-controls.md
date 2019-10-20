---
title: Přizpůsobení způsobu, jakým Visual Studio 2015 vytvoří titulky pro ovládací prvky vázané na data | Microsoft Docs
titleSuffix: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-data-tools
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
- aspx
helpviewer_keywords:
- Label captions, Data Sources window
- smart captions
- captions, data-bound
- Data Sources Window, label captions
ms.assetid: 6d4d15f8-4d78-42fd-af64-779ae98d62c8
caps.latest.revision: 15
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 04f32fa0426039f50c0a0352ef0b04900d705a98
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/19/2019
ms.locfileid: "72657432"
---
# <a name="customize-how-visual-studio-creates-captions-for-data-bound-controls"></a>Úprava způsobu, kterým Visual Studio vytváří titulky pro ovládací prvky vázané daty
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Když přetáhnete položky z [okna zdroje dat](https://msdn.microsoft.com/library/0d20f699-cc95-45b3-8ecb-c7edf1f67992) do Návrhář formulářů, bude se věnovat zvláštní pozornost: názvy sloupců v popiscích titulků se přeformátují na čitelnější řetězec, když se zjistí dvě nebo více slov, která se mají zřetězit. spojit. Můžete přizpůsobit způsob vytváření těchto popisků nastavením hodnot **SmartCaptionExpression**, **SmartCaptionReplacement**a **SmartCaptionSuffix** v **HKEY_CURRENT_USER\Software\Microsoft\VisualStudio\. 10.0 \ klíč registru návrháře dat** .

> [!NOTE]
> Tento klíč registru neexistuje, dokud jej nevytvoříte.

 Inteligentní titulky jsou ovládány pomocí regulárního výrazu zadaného do hodnoty hodnoty **SmartCaptionExpression** . Přidání klíče registru **Návrháře dat** přepíše výchozí regulární výraz, který řídí popisky titulků. Další informace o regulárních výrazech naleznete v tématu [použití regulárních výrazů v sadě Visual Studio](../ide/using-regular-expressions-in-visual-studio.md).

 Následující tabulka popisuje hodnoty registru, které řídí popisky titulků.

|Položka registru|Popis|
|-------------------|-----------------|
|**SmartCaptionExpression**|Regulární výraz, který se používá ke spárování se vzorci.|
|**SmartCaptionReplacement**|Formát pro zobrazení všech skupin odpovídajících v **SmartCaptionExpression**.|
|**SmartCaptionSuffix**|Volitelný řetězec, který se má připojit ke konci titulku.|

 Následující tabulka uvádí interní výchozí nastavení pro tyto hodnoty registru.

|Položka registru|Výchozí hodnota|Vysvětlení|
|-------------------|-------------------|-----------------|
|**SmartCaptionExpression**|(\\ \p{Ll}) (\\ \p{Lu}) &#124;_+|Porovnává s malým znakem následovaným velkým znakem nebo podtržítkem.|
|**SmartCaptionReplacement**|$1 $2|$1 představuje všechny znaky, které odpovídají v první závorce výrazu, a $2 představuje všechny znaky, které odpovídají v druhých závorkách. Nahrazení je první shoda, mezera a druhá shoda.|
|**SmartCaptionSuffix**|:|Představuje znak připojený ke vrácenému řetězci. Například pokud je titulek `Company Name`, přípona ho umožňuje `Company Name:`|

> [!CAUTION]
> Při cokoli v editoru registru byste měli být velmi opatrní. Před úpravou registru zazálohujte. Používáte-li Editor registru nesprávně, můžete způsobit vážné problémy, které mohou vyžadovat přeinstalaci operačního systému. Společnost Microsoft nezaručuje, že je možné vyřešit problémy, které jste vyzpůsobili pomocí Editoru registru nesprávně. Editor registru používejte na vlastní riziko.
>
> Následující článek znalostní báze obsahuje pokyny pro zálohování, úpravy a obnovení registru: [Popis registru Microsoft Windows](http://support.microsoft.com/default.aspx?scid=kb;en-us;256986) (http://support.microsoft.com/default.aspx?scid=kb; en-US; 256986)

### <a name="to-modify-the-smart-captioning-behavior-of-the-data-sources-window"></a>Úprava chování inteligentního titulkování v okně zdroje dat

1. Otevřete příkazové okno kliknutím na **Start** a pak na **Spustit**.

2. Do dialogového okna **Spustit** zadejte `regedit` a klikněte na **OK**.

3. Rozbalte uzel **HKEY_CURRENT_USER** .

4. Rozbalte uzel **software** .

5. Rozbalte uzel **Microsoft** .

6. Rozbalte uzel **VisualStudio** .

7. Pravým tlačítkem myši klikněte na uzel **10,0** a vytvořte nový **klíč** s názvem `Data Designers`.

8. Klikněte pravým tlačítkem myši na uzel **Návrháři dat** a vytvořte novou **řetězcovou hodnotu** s názvem `SmartCaptionExpression`.

9. Klikněte pravým tlačítkem myši na uzel **Návrháři dat** a vytvořte novou **řetězcovou hodnotu** s názvem `SmartCaptionReplacement`.

10. Klikněte pravým tlačítkem myši na uzel **Návrháři dat** a vytvořte novou **řetězcovou hodnotu** s názvem `SmartCaptionSuffix`.

11. Klikněte pravým tlačítkem na položku **SmartCaptionExpression** a vyberte **Upravit**.

12. Zadejte regulární výraz, který má okno **zdroje dat** použít.

13. Klikněte pravým tlačítkem na položku **SmartCaptionReplacement** a vyberte **Upravit**.

14. Zadejte řetězec pro nahrazení, který formátuje způsob, jakým chcete zobrazit vzorce odpovídající regulárnímu výrazu.

15. Klikněte pravým tlačítkem na položku **SmartCaptionSuffix** a vyberte **Upravit**.

16. Zadejte libovolné znaky, které se mají zobrazit na konci titulku.

     Při příštím přetahování položek z okna **zdroje dat** se popisky titulků vytvoří pomocí nových hodnot registru.

### <a name="to-turn-off-the-smart-captioning-feature"></a>Vypnutí funkce inteligentního titulkování

1. Otevřete příkazové okno kliknutím na **Start** a pak na **Spustit**.

2. Do dialogového okna **Spustit** zadejte `regedit` a klikněte na **OK**.

3. Rozbalte uzel **HKEY_CURRENT_USER** .

4. Rozbalte uzel **software** .

5. Rozbalte uzel **Microsoft** .

6. Rozbalte uzel **VisualStudio** .

7. Pravým tlačítkem myši klikněte na uzel **10,0** a vytvořte nový **klíč** s názvem `Data Designers`.

8. Klikněte pravým tlačítkem myši na uzel **Návrháři dat** a vytvořte novou **řetězcovou hodnotu** s názvem `SmartCaptionExpression`.

9. Klikněte pravým tlačítkem myši na uzel **Návrháři dat** a vytvořte novou **řetězcovou hodnotu** s názvem `SmartCaptionReplacement`.

10. Klikněte pravým tlačítkem myši na uzel **Návrháři dat** a vytvořte novou **řetězcovou hodnotu** s názvem `SmartCaptionSuffix`.

11. Klikněte pravým tlačítkem na položku **SmartCaptionExpression** a vyberte **Upravit**.

12. Jako hodnotu zadejte `(.*)`. To bude odpovídat celému řetězci.

13. Klikněte pravým tlačítkem na položku **SmartCaptionReplacement** a vyberte **Upravit**.

14. Jako hodnotu zadejte `$1`. Tím se nahradí řetězec odpovídající hodnotou, která je celým řetězcem, takže zůstane beze změny.

     Při příštím přetahování položek z okna **zdroje dat** jsou popisky titulků vytvořeny s nezměněnými titulky.

## <a name="see-also"></a>Viz také
 [Vytvoření vazby ovládacích prvků k datům v sadě Visual Studio](../data-tools/bind-controls-to-data-in-visual-studio.md)
