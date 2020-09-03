---
title: Přidání vlastních ovládacích prvků do okna zdroje dat | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-data-tools
ms.topic: conceptual
f1_keywords:
- vs.datasource.howtoaddcustomcontrol
dev_langs:
- VB
- CSharp
- C++
- aspx
helpviewer_keywords:
- Data Sources Window, adding controls
- controls [Visual Studio], adding to Data Sources Window
- DefaultBindingPropertyAttribute class, using
- LookupBindingPropertiesAttribute class, using
- ComplexBindingPropertiesAttribute class, using
- Data Sources Window, selecting controls
ms.assetid: 8c43e7d2-ba94-4d9b-96de-3aa971955afd
caps.latest.revision: 45
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 402e62602d99492730d3094965e76964cd5f8218
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "72673086"
---
# <a name="add-custom-controls-to-the-data-sources-window"></a>Přidání vlastních ovládacích prvků do okna zdrojů dat
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Když přetáhnete položku z okna **zdroje dat** na návrhovou plochu pro vytvoření ovládacího prvku vázaného na data, můžete vybrat typ ovládacího prvku, který vytvoříte. Každá položka v okně má rozevírací seznam, který zobrazuje ovládací prvky, ze kterých můžete vybírat. Sada ovládacích prvků přidružených k jednotlivým položkám je určena datovým typem položky. Pokud se ovládací prvek, který chcete vytvořit, v seznamu nezobrazí, můžete postupovat podle pokynů v tomto tématu a přidat ovládací prvek do seznamu.

 Další informace o výběru ovládacích prvků vázaných na data k vytvoření pro položky v okně **zdroje dat** naleznete v tématu [nastavení ovládacího prvku, který má být vytvořen při přetahování z okna zdroje dat](../data-tools/set-the-control-to-be-created-when-dragging-from-the-data-sources-window.md).

> [!NOTE]
> Dialogová okna a příkazy nabídek, které vidíte, se mohou lišit od těch popsaných v nápovědě v závislosti na aktivních nastaveních nebo edici. Chcete-li změnit nastavení, v nabídce **nástroje** vyberte **Nastavení importu a exportu**. Další informace naleznete v tématu [přizpůsobení nastavení vývoje v aplikaci Visual Studio](https://msdn.microsoft.com/22c4debb-4e31-47a8-8f19-16f328d7dcd3).

## <a name="customize-the-list-of-bindable-controls-for-a-data-type"></a><a name="customizinglist"></a> Přizpůsobení seznamu ovládacích prvků s možností vazby pro datový typ
 Chcete-li přidat nebo odebrat ovládací prvky ze seznamu dostupných ovládacích prvků pro položky v okně **zdroje dat** , které mají určitý datový typ, proveďte následující kroky.

#### <a name="to-select-the-controls-to-be-listed-for-a-data-type"></a>Výběr ovládacích prvků, které mají být uvedeny pro datový typ

1. Ujistěte se, že je Návrhář WPF nebo Návrhář formulářů otevřený.

2. V okně **zdroje dat** klikněte na položku, která je součástí zdroje dat, který jste přidali do okna, a poté klikněte na rozevírací nabídku položky.

3. V rozevírací nabídce klikněte na **přizpůsobit**. Otevře se jedna z následujících dialogových oken:

    - Pokud je Návrhář formulářů otevřené, otevře se stránka **přizpůsobení uživatelského rozhraní dat** v dialogovém okně **Možnosti** .

    - Pokud je Návrhář WPF otevřený, otevře se dialogové okno **přizpůsobit vazbu ovládacího prvku** .

4. V dialogovém okně vyberte v rozevíracím seznamu datový **typ** datový typ.

    - Chcete-li přizpůsobit seznam ovládacích prvků pro tabulku nebo objekt, vyberte **[seznam]**.

    - Chcete-li přizpůsobit seznam ovládacích prvků pro sloupec tabulky nebo vlastnost objektu, vyberte datový typ sloupce nebo vlastnosti v podkladovém úložišti dat.

    - Chcete-li upravit seznam ovládacích prvků pro zobrazení datových objektů, které mají uživatelem definované tvary, vyberte možnost **[jiné]**. Například vyberte **[Other]** , pokud vaše aplikace má vlastní ovládací prvek, který zobrazuje data z více než jedné vlastnosti konkrétního objektu.

5. V poli **přidružené ovládací prvky** vyberte všechny ovládací prvky, které mají být k dispozici pro vybraný datový typ, nebo zrušte výběr všech ovládacích prvků, které chcete ze seznamu odebrat.

    > [!NOTE]
    > Pokud ovládací prvek, který chcete vybrat, není zobrazen v poli **přidružené ovládací prvky** , je nutné přidat ovládací prvek do seznamu. Další informace najdete v tématu [Přidání ovládacích prvků do seznamu přidružených ovládacích prvků pro datový typ](#addingcontrols).

6. Klikněte na **OK**.

7. V okně **zdroje dat** klikněte na položku datového typu, ke kterému jste právě přidružit jeden nebo více ovládacích prvků, a poté klikněte na rozevírací nabídku položky.

     Ovládací prvky, které jste vybrali v poli **přidružené ovládací prvky** , se nyní zobrazí v rozevírací nabídce položky.

## <a name="addcontrols-to-the-list-of-associated-controls-for-a-data-type"></a><a name="addingcontrols"></a> Addcontrols se na seznam přidružených ovládacích prvků pro datový typ.
 Chcete-li přidružit ovládací prvek s datovým typem, ale ovládací prvek se nezobrazí v poli **přidružené ovládací prvky** , je nutné přidat ovládací prvek do seznamu. Ovládací prvek musí být umístěn v aktuálním řešení nebo v odkazovaném sestavení. Musí být také k dispozici v **sadě nástrojů**a mít atribut, který určuje chování vazby dat ovládacího prvku.

#### <a name="to-add-controls-to-the-list-of-associated-controls"></a>Přidání ovládacích prvků do seznamu přidružených ovládacích prvků

1. Požadovaný ovládací prvek přidejte do **panelu nástrojů** tak, že kliknete pravým tlačítkem myši na **panel nástrojů** a vyberete **možnost zvolit položky**.

     Ovládací prvek musí mít jeden z následujících atributů.

    |Atribut|Popis|
    |---------------|-----------------|
    |<xref:System.ComponentModel.DefaultBindingPropertyAttribute>|Implementujte tento atribut pro jednoduché ovládací prvky, které zobrazují jeden sloupec (nebo vlastnost) dat, jako je například <xref:System.Windows.Forms.TextBox> .|
    |<xref:System.ComponentModel.ComplexBindingPropertiesAttribute>|Implementujte tento atribut pro ovládací prvky, které zobrazují seznamy (nebo tabulky) dat, jako je například <xref:System.Windows.Forms.DataGridView> .|
    |<xref:System.ComponentModel.LookupBindingPropertiesAttribute>|Implementujte tento atribut pro ovládací prvky, které zobrazují seznamy (nebo tabulky) dat, ale také musí obsahovat jeden sloupec nebo vlastnost, jako je například <xref:System.Windows.Forms.ComboBox> .|

2. Pro model Windows Forms otevřete v dialogovém okně      **Možnosti** stránku **přizpůsobení uživatelského rozhraní dat** . Nebo pro WPF otevřete dialogové okno **přizpůsobit vazbu ovládacího prvku** . Další informace najdete v tématu [přizpůsobení seznamu ovládacích prvků s možností vazby pro datový typ](#customizinglist).

3. V poli **přidružené ovládací prvky** by se teď měl zobrazit ovládací prvek, který jste právě přidali do **sady nástrojů** .

    > [!NOTE]
    > Do seznamu přidružených ovládacích prvků mohou být přidány pouze ovládací prvky, které jsou umístěny v rámci aktuálního řešení nebo v odkazovaném sestavení. (Ovládací prvky musí také implementovat jeden z atributů datové vazby v předchozí tabulce.) Chcete-li vytvořit vazby dat k vlastnímu ovládacímu prvku, který není k dispozici v okně **zdroje dat** , přetáhněte ovládací prvek z **panelu nástrojů** na návrhovou plochu a potom přetáhněte položku k navázání z okna **zdroje dat** do ovládacího prvku.

## <a name="see-also"></a>Viz také
 [Vytvoření vazby ovládacích prvků k datům v sadě Visual Studio](../data-tools/bind-controls-to-data-in-visual-studio.md)
