---
title: Vytvoření vazby ovládacích prvků k obrázkům z databáze
description: Použijte okno zdroje dat k vytvoření vazby obrázku v databázi k ovládacímu prvku v aplikaci Visual Studio.
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- images [Visual Basic], displaying on Windows Forms
- data binding [Windows Forms], pictures
- images [Visual Basic], data binding
- pictures, data binding
- pictures, dragging from Data Sources window
- Data Sources Window, setting controls to display images
- PictureBox control [Windows Forms], data binding
- images [Visual Basic], dragging from Data Sources window
ms.assetid: 9748815e-3556-49e8-86b1-c6aa593c6163
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: 6a2033bfe6719ccd325a2409d20fbb0e77d92926
ms.sourcegitcommit: 0893244403aae9187c9375ecf0e5c221c32c225b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/09/2020
ms.locfileid: "94382296"
---
# <a name="bind-controls-to-pictures-from-a-database"></a>Vytvoření vazby ovládacích prvků k obrázkům z databáze

Okno **zdroje dat** můžete použít k vytvoření vazby obrázku v databázi k ovládacímu prvku ve vaší aplikaci. Můžete například navazovat obrázek k <xref:System.Windows.Controls.Image> ovládacímu prvku v aplikaci WPF nebo k <xref:System.Windows.Forms.PictureBox> ovládacímu prvku v model Windows Forms aplikaci.

Obrázky v databázi jsou obvykle uloženy jako Bajtová pole. Položky v okně **zdroje dat** , které jsou uloženy jako pole bajtů, mají ve výchozím nastavení nastavený typ ovládacího prvku **none** , protože pole bajtů mohou obsahovat cokoli od jednoduchého pole bajtů ke spustitelnému souboru velké aplikace. Chcete-li vytvořit ovládací prvek vázaný na data pro položku bajtového pole v okně **zdroje dat** , které představuje obrázek, je nutné vybrat ovládací prvek, který chcete vytvořit.

Následující postup předpokládá, že okno **zdroje dat** je již vyplněno položkou, která je svázána s vaší imagí.

## <a name="to-bind-a-picture-in-a-database-to-a-control"></a>Vytvoření vazby obrázku v databázi k ovládacímu prvku

1. Ujistěte se, že návrhová plocha, do které chcete ovládací prvek přidat, je otevřená v Návrháři WPF nebo Návrhář formulářů.

2. V okně **zdroje dat** rozbalte požadovanou tabulku nebo objekt, abyste zobrazili její sloupce nebo vlastnosti.

   > [!TIP]
   > Pokud není okno **zdroje dat** otevřené, otevřete ho výběrem možnosti **Zobrazit**  >  **ostatní**  >  **zdroje dat** Windows.

3. Vyberte sloupec nebo vlastnost obsahující data obrázku a ze seznamu ovládacích prvků rozevírací seznam vyberte jeden z následujících ovládacích prvků:

    - Pokud je Návrhář WPF otevřený, vyberte **Obrázek**.

    - Pokud je otevřený Návrhář model Windows Forms, vyberte **PictureBox**.

    - Alternativně můžete vybrat jiný ovládací prvek, který podporuje datovou vazbu a který může zobrazovat obrázky. Pokud ovládací prvek, který chcete použít, není v seznamu dostupných ovládacích prvků, můžete ho přidat do seznamu a pak ho vybrat. Další informace najdete v tématu [Přidání vlastních ovládacích prvků do okna zdroje dat](../data-tools/add-custom-controls-to-the-data-sources-window.md).

## <a name="see-also"></a>Viz také

- [Vytvoření vazby ovládacích prvků WPF k datům v sadě Visual Studio](../data-tools/bind-wpf-controls-to-data-in-visual-studio.md)
