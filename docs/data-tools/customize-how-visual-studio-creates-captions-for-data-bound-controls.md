---
title: Přizpůsobení popisků pro ovládací prvky vázané na data
description: Přizpůsobení způsobu, jakým Visual Studio vytváří titulky pro ovládací prvky vázané na data. Upravte chování inteligentního titulkování v okně zdroje dat. Vypnutí inteligentního titulkování
ms.custom: SEO-VS-2020
ms.date: 11/03/2017
ms.topic: how-to
helpviewer_keywords:
- Label captions, Data Sources window
- smart captions
- captions, data-bound
- Data Sources Window, label captions
ms.assetid: 6d4d15f8-4d78-42fd-af64-779ae98d62c8
author: ghogen
ms.author: ghogen
manager: jmartens
ms.workload:
- data-storage
ms.openlocfilehash: be9a6840c3b41b442e5019e08c4d2f4d2fa5c3dd
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99858992"
---
# <a name="customize-how-visual-studio-creates-captions-for-data-bound-controls"></a>Úprava způsobu, kterým Visual Studio vytváří titulky pro ovládací prvky vázané daty

Při přetahování položek z [okna zdroje dat](add-new-data-sources.md#data-sources-window) do návrháře se dorazí na zvláštní pozornost: názvy sloupců v popiscích titulků se přeformátují na čitelnější řetězec, když se zjistí dvě nebo více slov, která se mají zřetězit dohromady.

::: moniker range="vs-2017"

Způsob, jakým se tyto popisky vytvářejí, můžete přizpůsobit nastavením hodnot **SmartCaptionExpression**, **SmartCaptionReplacement** a **SmartCaptionSuffix** v klíči registru **HKEY_CURRENT_USER\Software\Microsoft\VisualStudio\15.0\Data Designers** .

::: moniker-end

::: moniker range=">=vs-2019"

Způsob, jakým se tyto popisky vytvářejí, můžete přizpůsobit nastavením hodnot **SmartCaptionExpression**, **SmartCaptionReplacement** a **SmartCaptionSuffix** v klíči registru **HKEY_CURRENT_USER\Software\Microsoft\VisualStudio\16.0\Data Designers** .

::: moniker-end

> [!NOTE]
> Tento klíč registru neexistuje, dokud jej nevytvoříte.

Inteligentní titulky jsou ovládány pomocí regulárního výrazu zadaného do hodnoty hodnoty **SmartCaptionExpression** . Přidání klíče registru **Návrháře dat** přepíše výchozí regulární výraz, který řídí popisky titulků. Další informace o regulárních výrazech naleznete v tématu [použití regulárních výrazů v sadě Visual Studio](../ide/using-regular-expressions-in-visual-studio.md).

Následující tabulka popisuje hodnoty registru, které řídí popisky titulků.

|Položka registru|Description|
|-------------------|-----------------|
|**SmartCaptionExpression**|Regulární výraz, který použijete pro shodu se vzorem.|
|**SmartCaptionReplacement**|Formát pro zobrazení všech skupin odpovídajících v **SmartCaptionExpression**.|
|**SmartCaptionSuffix**|Volitelný řetězec, který se má připojit ke konci titulku.|

Následující tabulka uvádí interní výchozí nastavení pro tyto hodnoty registru.

|Položka registru|Výchozí hodnota|Vysvětlení|
|-------------------|-------------------|-----------------|
|**SmartCaptionExpression**|**( \\ \p{ll}) ( \\ \p{Lu}) &#124;_ +**|Porovnává s malým znakem následovaným velkým znakem nebo podtržítkem.|
|**SmartCaptionReplacement**|**$1 $2**|**$1** představuje všechny znaky, které odpovídají v první závorce výrazu, a **$2** představuje všechny znaky, které odpovídají v druhých závorkách. Nahrazení je první shoda, mezera a druhá shoda.|
|**SmartCaptionSuffix**|**:**|Představuje znak připojený ke vrácenému řetězci. Například pokud je titulek `Company Name` , přípona ho udělá `Company Name:`|

> [!CAUTION]
> Při cokoli v editoru registru Buďte velmi opatrní. Před úpravou registru zazálohujte. Používáte-li Editor registru nesprávně, můžete způsobit vážné problémy, které mohou vyžadovat přeinstalaci operačního systému. Společnost Microsoft nezaručuje, že je možné vyřešit problémy, které jste vyzpůsobili pomocí Editoru registru nesprávně. Editor registru používáte na vlastní nebezpečí.
>
> Informace o zálohování, úpravách a obnovování registru najdete v tématu [informace o registru Windows pro pokročilé uživatele](https://support.microsoft.com/help/256986/windows-registry-information-for-advanced-users).

## <a name="modify-the-smart-captioning-behavior-of-the-data-sources-window"></a>Úprava chování inteligentního titulkování v okně zdroje dat

1. Otevřete příkazové okno kliknutím na **Start** a pak na **Spustit**.

2. `regedit`Do dialogového okna **Spustit** zadejte a klikněte na **OK**.

3. Rozbalte uzel **HKEY_CURRENT_USER**  >  **software**  >  **Microsoft**  >  **VisualStudio** .

::: moniker range="vs-2017"

4. Klikněte pravým tlačítkem na uzel **15,0** a vytvořte nový **klíč** s názvem `Data Designers` .

::: moniker-end

::: moniker range=">=vs-2019"

4. Klikněte pravým tlačítkem na uzel **16,0** a vytvořte nový **klíč** s názvem `Data Designers` .

::: moniker-end

5. Klikněte pravým tlačítkem myši na uzel **Návrháři dat** a vytvořte tři nové řetězcové hodnoty:

    - `SmartCaptionExpression`
    - `SmartCaptionReplacement`
    - `SmartCaptionSuffix`

6. Klikněte pravým tlačítkem na hodnotu **SmartCaptionExpression** a vyberte **Upravit**.

7. Zadejte regulární výraz, který má okno **zdroje dat** použít.

8. Klikněte pravým tlačítkem na hodnotu **SmartCaptionReplacement** a vyberte **Upravit**.

9. Zadejte řetězec pro nahrazení, který formátuje způsob, jakým chcete zobrazit vzorce odpovídající regulárnímu výrazu.

10. Klikněte pravým tlačítkem na hodnotu **SmartCaptionSuffix** a vyberte **Upravit**.

11. Zadejte libovolné znaky, které se mají zobrazit na konci titulku.

    Při příštím přetahování položek z okna **zdroje dat** se popisky titulků vytvoří pomocí nových hodnot registru.

## <a name="turn-off-the-smart-captioning-feature"></a>Vypnutí funkce inteligentního titulkování

1. Otevřete příkazové okno kliknutím na **Start** a pak na **Spustit**.

2. `regedit`Do dialogového okna **Spustit** zadejte a klikněte na **OK**.

3. Rozbalte uzel **HKEY_CURRENT_USER**  >  **software**  >  **Microsoft**  >  **VisualStudio** .

::: moniker range="vs-2017"

4. Klikněte pravým tlačítkem na uzel **15,0** a vytvořte nový **klíč** s názvem `Data Designers` .

::: moniker-end

::: moniker range=">=vs-2019"

4. Klikněte pravým tlačítkem na uzel **16,0** a vytvořte nový **klíč** s názvem `Data Designers` .

::: moniker-end

5. Klikněte pravým tlačítkem myši na uzel **Návrháři dat** a vytvořte tři nové řetězcové hodnoty:

    - `SmartCaptionExpression`
    - `SmartCaptionReplacement`
    - `SmartCaptionSuffix`

6. Klikněte pravým tlačítkem na položku **SmartCaptionExpression** a vyberte **Upravit**.

7. Jako `(.*)` hodnotu zadejte. To bude odpovídat celému řetězci.

8. Klikněte pravým tlačítkem na položku **SmartCaptionReplacement** a vyberte **Upravit**.

9. Jako `$1` hodnotu zadejte. Tím se nahradí řetězec odpovídající hodnotou, která je celým řetězcem, takže zůstane beze změny.

    Při příštím přetahování položek z okna **zdroje dat** jsou popisky titulků vytvořeny s nezměněnými titulky.

## <a name="see-also"></a>Viz také

- [Vytvoření vazby ovládacích prvků k datům v sadě Visual Studio](../data-tools/bind-controls-to-data-in-visual-studio.md)
