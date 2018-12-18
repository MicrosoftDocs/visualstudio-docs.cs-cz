---
title: Nastavit vazbu dialogové okno ovládacího prvku | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vs.datasource.datauicustomization
dev_langs:
- VB
- CSharp
- C++
- aspx
helpviewer_keywords:
- Customize Control Binding dialog box
ms.assetid: abcc0be3-a18e-4f47-b354-d6b0c618e087
caps.latest.revision: 9
author: gewarren
ms.author: gewarren
manager: ghogen
robots: noindex,nofollow
ms.openlocfilehash: 8ca2da23040f3e7a57fe5da2ff8b87cc7fc38099
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/23/2018
ms.locfileid: "49889701"
---
# <a name="customize-control-binding-dialog-box"></a>Dialogové okno Nastavit vazbu ovládacího prvku
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Použití **přizpůsobit vazbu ovládacího prvku** dialogové okno k určení, jaké ovládací prvky jsou k dispozici pro položky v [okna zdroje dat](http://msdn.microsoft.com/library/0d20f699-cc95-45b3-8ecb-c7edf1f67992).  
  
 Každá položka v **zdroje dat** okno má přidružený seznam ovládacích prvků, které mohou být vázány na položce. Ovládací prvky, které jsou k dispozici pro každou položku jsou určeny typem dat položky. Každý typ dat obsahuje seznam platný přidružených ovládacích prvcích, které jsou definované v tomto dialogovém okně včetně výchozí ovládací prvek.  
  
 Před přetažením položky na návrhovou plochu vytvoříte ovládací prvek vázaný na data, můžete vybrat který ovládací prvek k vytvoření. Pokud přetáhnete položku ze **zdroje dat** okno na návrhovou plochu bez výběru ovládacího prvku, výchozího ovládacího prvku pro datový typ vybrané položky je přidán na návrhovou plochu.  
  
 Další informace o tom, jak používat toto dialogové okno přizpůsobení ovládacích prvků pro položky v seznamu **zdroje dat** okna, naleznete v tématu [přidání vlastních ovládacích prvků do okna zdroje dat](../data-tools/add-custom-controls-to-the-data-sources-window.md).  
  
## <a name="uielement-list"></a>Seznam prvků uživatelského rozhraní  
 **Datový typ**  
 Zobrazí seznam typů, které spojují s ovládacími prvky:  
  
- Tabulky, entity a objekty jsou reprezentovány ve formě **[seznam]** typy.  
  
- Sloupce nebo veřejné vlastnosti entit a objekty jsou reprezentovány jako skutečný datový typ sloupce nebo vlastnosti podkladových dat v úložišti.  
  
- Objekty s uživatelem definované tvary jsou reprezentovány ve formě **[Další]**. Například pokud vaše aplikace má vlastní ovládací prvek, který zobrazuje data z více než jednu vlastnost objektu, vyberte **[Další]** datový typ pro ovládací prvek.  
  
  **Přidružené ovládací prvky**  
  Zobrazí seznam ovládacích prvků, které můžete přiřadit konkrétní datového typu. Pokud chcete přidružit k datovému typu vybranému v konkrétní ovládací prvek **datový typ** seznam, zaškrtněte odpovídající políčko. Zrušte zaškrtnutí políčka k odebrání přidružení. Checked ovládací prvky se zobrazí v místní nabídce předložený **zdroje dat** okno pro položku typu přidružená data.  
  
  Můžete přidat ovládací prvky do seznamu tak, že přidáte ovládací prvky, které mají jeden z několika atributů datové vazby, které mají **nástrojů**. Další informace najdete v tématu [přidání vlastních ovládacích prvků do okna zdroje dat](../data-tools/add-custom-controls-to-the-data-sources-window.md).  
  
  **Nastavit výchozí**  
  Přiřadí vybraný ovládací prvek typu jako výchozí pro položky vybrané datového typu. Výchozí ovládací prvek se zobrazí jako první výběru v místní nabídce předložený **zdroje dat** okno pro položku. Jako výchozí pro datový typ je možné přiřadit pouze jeden ovládací prvek typu.  
  
  **Vymazat výchozí**  
  Odebere označení jako výchozí pro vybraný datový typ ovládacího prvku. Pokud není žádná výchozí nastavení pro vybraný datový typ **[Žádný]** se zobrazí jako první výběru v místní nabídce předložený **zdroje dat** okno pro položky z přidruženého typu.  
  
## <a name="see-also"></a>Viz také  
 [Okno zdroje dat](http://msdn.microsoft.com/library/0d20f699-cc95-45b3-8ecb-c7edf1f67992)   
 [Přidat nové zdroje dat](../data-tools/add-new-data-sources.md)   
 [Vytvoření vazby ovládacích prvků Windows Forms k datům v sadě Visual Studio](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)   
 [Přidání vlastních ovládacích prvků do okna zdroje dat](../data-tools/add-custom-controls-to-the-data-sources-window.md)   
 [Nastavení ovládacího prvku, který má být vytvořen při přetažení z okna zdrojů dat](../data-tools/set-the-control-to-be-created-when-dragging-from-the-data-sources-window.md)