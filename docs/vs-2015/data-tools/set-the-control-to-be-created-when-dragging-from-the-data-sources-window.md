---
title: Nastavení ovládacího prvku, který má být vytvořen při přetahování z okna zdroje dat | Microsoft Docs
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
- Data Sources Window, select controls
- Windows Forms, displaying data
- data [Visual Studio], displaying on Windows Forms
- data [Visual Studio], Data Sources window
ms.assetid: 20597ff8-0c98-43ec-8fb1-05376804ba48
caps.latest.revision: 34
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 222ecfa56b179379c2d007e8635e7b40d6b1b660
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "72655387"
---
# <a name="set-the-control-to-be-created-when-dragging-from-the-data-sources-window"></a>Nastavení ovládacího prvku, který má být vytvořen při přetažení z okna zdrojů dat
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Můžete vytvořit ovládací prvky vázané na data přetažením položek z okna **zdroje dat** do návrháře WPF nebo návrháře model Windows Forms. Každá položka v okně **zdroje dat** má výchozí ovládací prvek, který se vytvoří, když ho přetáhnete do návrháře. Můžete ale zvolit, že se má vytvořit jiný ovládací prvek.

## <a name="set-the-controls-to-be-created-for-data-tables-or-objects"></a>Nastavení ovládacích prvků, které mají být vytvořeny pro tabulky dat nebo pro objekty
 Před přetažením položek, které reprezentují tabulky dat nebo objekty z okna **zdroje dat** , můžete zvolit zobrazení všech dat v jednom ovládacím prvku nebo zobrazit jednotlivé sloupce nebo vlastnosti v samostatném ovládacím prvku.

 V tomto kontextu pojem *objekt* odkazuje na vlastní obchodní objekt, entitu (v model EDM (Entity Data Model)) nebo objekt vrácený službou.

#### <a name="to-set-the-controls-to-be-created-for-data-tables-or-objects"></a>Nastavení ovládacích prvků, které mají být vytvořeny pro tabulky dat nebo pro objekty

1. Ujistěte se, že je otevřený Návrhář WPF nebo Návrhář model Windows Forms.

2. V okně **zdroje dat** vyberte položku, která představuje datovou tabulku nebo objekt, který chcete nastavit.

3. Klikněte na rozevírací nabídku pro položku a potom v nabídce klikněte na jednu z následujících položek:

   - Chcete-li zobrazit jednotlivá datová pole v samostatném ovládacím prvku, klikněte na tlačítko **Podrobnosti**. Když přetáhnete datovou položku do návrháře, tato akce vytvoří jiný ovládací prvek vázaný na data pro každý sloupec nebo vlastnost nadřazené datové tabulky nebo objektu, spolu s popisky pro každý ovládací prvek.

   - Chcete-li zobrazit všechna data v jednom ovládacím prvku, vyberte jiný ovládací prvek v seznamu, jako je například **DataGrid** nebo **list** v aplikaci WPF nebo **DataGridView** v aplikaci model Windows Forms.

     Seznam dostupných ovládacích prvků závisí na tom, který Návrhář máte otevřený, na které verzi .NET Framework projekt cílí, a na tom, zda jste přidali vlastní ovládací prvky, které podporují datovou vazbu na **sadu nástrojů**. Pokud je ovládací prvek, který chcete vytvořit, v seznamu dostupných ovládacích prvků, můžete přidat ovládací prvek do seznamu. Další informace najdete v tématu [Přidání vlastních ovládacích prvků do okna zdroje dat](../data-tools/add-custom-controls-to-the-data-sources-window.md).

     Chcete-li se dozvědět, jak vytvořit vlastní ovládací prvek model Windows Forms, který lze přidat do seznamu ovládacích prvků pro tabulky dat nebo objekty v okně **zdroje dat** , přečtěte si téma [Vytvoření model Windows Forms uživatelského ovládacího prvku, který podporuje složitou datovou vazbu](../data-tools/create-a-windows-forms-user-control-that-supports-complex-data-binding.md).

## <a name="set-the-controls-to-be-created-for-data-columns-or-properties"></a>Nastavení ovládacích prvků, které se mají vytvořit pro datové sloupce nebo vlastnosti
 Před přetažením položky, která představuje sloupec nebo vlastnost objektu z okna **zdroje dat** do návrháře, lze nastavit ovládací prvek, který má být vytvořen.

#### <a name="to-set-the-controls-to-be-created-for-columns-or-properties"></a>Nastavení ovládacích prvků, které mají být vytvořeny pro sloupce nebo vlastnosti

1. Ujistěte se, že je otevřený Návrhář WPF nebo Návrhář model Windows Forms.

2. V okně **zdroje dat** rozbalte požadovanou tabulku nebo objekt, abyste zobrazili její sloupce nebo vlastnosti.

3. Vyberte jednotlivé sloupce nebo vlastnosti, u kterých chcete nastavit, aby byl ovládací prvek vytvořen.

4. Klikněte na rozevírací nabídku pro sloupec nebo vlastnost a potom vyberte ovládací prvek, který chcete vytvořit, když je položka přetažena do návrháře.

     Seznam dostupných ovládacích prvků závisí na tom, který Návrhář máte otevřený, na které verzi .NET Framework projekt cílí, a na které vlastní ovládací prvky, které podporují datové vazby, které jste přidali do **sady nástrojů**. Pokud je ovládací prvek, který chcete vytvořit, v seznamu dostupných ovládacích prvků, můžete přidat ovládací prvek do seznamu. Další informace najdete v tématu [Přidání vlastních ovládacích prvků do okna zdroje dat](../data-tools/add-custom-controls-to-the-data-sources-window.md).

     Chcete-li se dozvědět, jak vytvořit vlastní ovládací prvek, který lze přidat do seznamu ovládacích prvků pro datové sloupce nebo vlastnosti v okně **zdroje dat** , přečtěte si téma [Vytvoření model Windows Forms uživatelského ovládacího prvku, který podporuje jednoduchou datovou vazbu](../data-tools/create-a-windows-forms-user-control-that-supports-simple-data-binding.md).

     Pokud nechcete vytvořit ovládací prvek pro sloupec nebo vlastnost, v rozevírací nabídce vyberte **None (žádné** ). To je užitečné, pokud chcete přetáhnout nadřazenou tabulku nebo objekt do návrháře, ale nechcete zahrnout konkrétní sloupec nebo vlastnost.

## <a name="see-also"></a>Viz také
 [Vytvoření vazby ovládacích prvků k datům v sadě Visual Studio](../data-tools/bind-controls-to-data-in-visual-studio.md)
