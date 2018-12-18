---
title: Přidání vlastních ovládacích prvků do okna zdroje dat | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
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
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 7e84224d4ebd066891d4fdf90b4ad488a79cc0b1
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/12/2018
ms.locfileid: "49183635"
---
# <a name="add-custom-controls-to-the-data-sources-window"></a>Přidání vlastních ovládacích prvků do okna zdrojů dat
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

  
Při přetažení položky z **zdroje dat** okno na návrhovou plochu vytvoříte ovládací prvek vázaný na data, můžete vybrat typ ovládacího prvku, který vytvoříte. Každá položka v okně se rozevírací seznam, který se zobrazí ovládací prvky, které můžete vybrat z. Sadu ovládacích prvků, které jsou spojené s každou položku je určeno typem dat položky. Pokud ovládací prvek, který chcete vytvořit v seznamu nezobrazí, můžete podle pokynů v tomto tématu přidejte ovládací prvek do seznamu.  
  
 Další informace o výběru ovládacích prvků vázaných na data pro vytvoření pro položky v **zdroje dat** okna, naleznete v tématu [nastavení ovládacího prvku, který má být vytvořen při přetažení z okna zdroje dat](../data-tools/set-the-control-to-be-created-when-dragging-from-the-data-sources-window.md).  
  
> [!NOTE]
>  Dialogová okna a příkazy nabídek, které se zobrazí mohou lišit od těch popsaných v nápovědě v závislosti na aktivních nastaveních nebo edici. Chcete-li změnit nastavení na **nástroje** nabídce vyberte možnost **nastavení importu a exportu**. Další informace najdete v tématu [přizpůsobení nastavení pro vývoj v sadě Visual Studio](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
##  <a name="customizinglist"></a> Přizpůsobení seznamu s možností vazby ovládacích prvků pro datový typ  
 Přidání nebo odebrání ze seznamu dostupných ovládacích prvků pro položky v ovládacích prvcích **zdroje dat** okno, které mají určitý datový typ, proveďte následující kroky.  
  
#### <a name="to-select-the-controls-to-be-listed-for-a-data-type"></a>Chcete-li vybrat ovládací prvky pro uvedené pro datový typ  
  
1.  Ujistěte se, že je otevřený Návrhář WPF nebo Návrhář formulářů Windows.  
  
2.  V **zdroje dat** okna, klikněte na položku, která je součástí jste přidali do okna zdroje dat a potom klikněte na rozevírací nabídku pro položku.  
  
3.  V rozevírací nabídce klikněte na tlačítko **vlastní**. Jeden z následujících dialogových otevře:  
  
    -   Pokud je otevřený Návrhář formulářů Windows **přizpůsobení dat uživatelského rozhraní** stránku **možnosti** zobrazí se dialogové okno.  
  
    -   Pokud je otevřený Návrhář WPF **přizpůsobit vazbu ovládacího prvku** zobrazí se dialogové okno.  
  
4.  V dialogovém okně vyberte datový typ z **datový typ** rozevíracího seznamu.  
  
    -   Chcete-li upravit seznam ovládacích prvků pro tabulku nebo objektu, vyberte **[seznam]**.  
  
    -   Přizpůsobení seznamu ovládacích prvků pro sloupec tabulky nebo vlastnost objektu, vyberte datový typ sloupce nebo vlastnosti podkladových dat v úložišti.  
  
    -   Chcete-li upravit seznam ovládacích prvků pro zobrazení datových objektů, které mají uživatelem definované obrazce, vyberte **[Další]**. Vyberte například **[Další]** Pokud vaše aplikace má vlastní ovládací prvek, který zobrazuje data z více než jednu vlastnost určitého objektu.  
  
5.  V **související ovládací prvky** pole, vyberte každý ovládací prvek, který chcete mít k dispozici pro vybraný datový typ nebo zrušit výběr všech ovládacích prvků, které chcete odebrat ze seznamu.  
  
    > [!NOTE]
    >  Pokud ovládací prvek, který chcete vybrat nezobrazí v **související ovládací prvky** pole, je nutné přidat do seznamu ovládacího prvku. Další informace najdete v tématu [přidání ovládacích prvků do seznamu z přidružené ovládací prvky pro datový typ](#addingcontrols).  
  
6.  Klikněte na tlačítko **OK**.  
  
7.  V **zdroje dat** okna, klikněte na položku dat zadejte související jenom jeden nebo více ovládacích prvků a potom klikněte na rozevírací nabídku pro položku.  
  
     Ovládací prvky, které jste vybrali v **související ovládací prvky** pole se zobrazí v rozevírací nabídce pro položku.  
  
##  <a name="addingcontrols"></a> Addcontrols do seznamu přidružených ovládacích prvcích pro datový typ  
 Pokud chcete spojit s datovým typem ovládacího prvku, ale nezobrazí se v ovládacím prvku **související ovládací prvky** pole, je nutné přidat do seznamu ovládacího prvku. Ovládací prvek musí být umístěny v aktuálním řešení nebo v odkazovaném sestavení. Musí být také dostupná v **nástrojů**, a mít atribut, který určuje chování vazby dat ovládacího prvku.  
  
#### <a name="to-add-controls-to-the-list-of-associated-controls"></a>Přidání ovládacích prvků do seznamu přidružených ovládacích prvcích  
  
1.  Přidejte požadované ovládací prvek **nástrojů** kliknutím pravým tlačítkem myši **nástrojů** a vyberete **zvolit položky**.  
  
     Ovládací prvek musí mít jednu z následujících atributů.  
  
    |Atribut|Popis|  
    |---------------|-----------------|  
    |<xref:System.ComponentModel.DefaultBindingPropertyAttribute>|Implementace tohoto atributu na jednoduché ovládací prvky, které zobrazí jeden sloupec (nebo vlastnost) dat, například <xref:System.Windows.Forms.TextBox>.|  
    |<xref:System.ComponentModel.ComplexBindingPropertiesAttribute>|Implementace tohoto atributu na ovládací prvky, které se zobrazí seznamy (nebo tabulky) dat, například <xref:System.Windows.Forms.DataGridView>.|  
    |<xref:System.ComponentModel.LookupBindingPropertiesAttribute>|Implementace tohoto atributu na ovládací prvky, které se zobrazí seznamy (nebo tabulky) z dat, ale také potřeba k dispozici do jednoho sloupce nebo vlastnosti, například <xref:System.Windows.Forms.ComboBox>.|  
  
2.  Pro Windows Forms na **možnosti** dialogovém okně Otevřít **přizpůsobení dat uživatelského rozhraní** stránky. Nebo, WPF, otevřete **přizpůsobit vazbu ovládacího prvku** dialogové okno. Další informace najdete v tématu [přizpůsobení seznamu s možností vazby prvky pro datový typ](#customizinglist).  
  
3.  V **související ovládací prvky** pole ovládacího prvku, který jste právě přidali **nástrojů** by teď měl vypadat.  
  
    > [!NOTE]
    >  Pouze ovládací prvky, které jsou umístěny v aktuálním řešení nebo v odkazovaném sestavení lze přidat do seznamu přidružených ovládacích prvcích. (Ovládací prvky musí také implementovat jeden z atributů datové vazby v předchozí tabulce.) Vazba dat na vlastní ovládací prvek, který není k dispozici v **zdroje dat** okno, přetáhněte ovládací prvek z **nástrojů** na návrhovou plochu a pak přetáhněte položky k vytvoření vazby k z **dat Zdroje** okna do ovládacího prvku.  
  
## <a name="see-also"></a>Viz také  
 [Vytvoření vazby ovládacích prvků k datům v sadě Visual Studio](../data-tools/bind-controls-to-data-in-visual-studio.md)

