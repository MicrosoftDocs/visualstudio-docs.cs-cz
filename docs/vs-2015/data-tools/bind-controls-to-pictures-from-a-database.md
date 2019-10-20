---
title: Vytvoření vazby ovládacích prvků k obrázkům z databáze | Microsoft Docs
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
- images [Visual Basic], displaying on Windows Forms
- data binding [Windows Forms], pictures
- images [Visual Basic], data binding
- pictures, data binding
- pictures, dragging from Data Sources window
- Data Sources Window, setting controls to display images
- PictureBox control [Windows Forms], data binding
- images [Visual Basic], dragging from Data Sources window
ms.assetid: 9748815e-3556-49e8-86b1-c6aa593c6163
caps.latest.revision: 18
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 0b8f6ee192399c8af8a508b2f9c2817db954bb36
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/19/2019
ms.locfileid: "72673016"
---
# <a name="bind-controls-to-pictures-from-a-database"></a>Vytvoření vazby ovládacích prvků k obrázkům z databáze
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Okno **zdroje dat** můžete použít k vytvoření vazby obrázku v databázi k ovládacímu prvku ve vaší aplikaci. Můžete například navazovat obrázek k ovládacímu prvku <xref:System.Windows.Controls.Image> v aplikaci WPF nebo k ovládacímu prvku <xref:System.Windows.Forms.PictureBox> v aplikaci model Windows Forms.

 Obrázky v databázi jsou obvykle uloženy jako Bajtová pole. Položky v okně **zdroje dat** , které jsou uloženy jako pole bajtů, mají ve výchozím nastavení nastavený typ ovládacího prvku **none** , protože pole bajtů mohou obsahovat cokoli od jednoduchého pole bajtů ke spustitelnému souboru velké aplikace. Chcete-li vytvořit ovládací prvek vázaný na data pro položku bajtového pole v okně **zdroje dat** , které představuje obrázek, je nutné vybrat ovládací prvek, který chcete vytvořit.

 Následující postup předpokládá, že okno **zdroje dat** je již vyplněno položkou, která je svázána s vaší imagí.

## <a name="bind-a-picture-in-a-database-to-a-control"></a>Navázání obrázku v databázi k ovládacímu prvku

1. Ujistěte se, že návrhová plocha, do které chcete ovládací prvek přidat, je otevřená v Návrháři WPF nebo Návrhář formulářů.

2. V okně **zdroje dat** rozbalte požadovanou tabulku nebo objekt, abyste zobrazili její sloupce nebo vlastnosti.

3. Vyberte sloupec nebo vlastnost obsahující data obrázku a ze seznamu ovládacích prvků rozevírací seznam vyberte jeden z následujících ovládacích prvků:

    - Pokud je Návrhář WPF otevřený, vyberte **Obrázek**.

    - Pokud je otevřený Návrhář model Windows Forms, vyberte **PictureBox**.

    - Alternativně můžete vybrat jiný ovládací prvek, který podporuje datovou vazbu a který může zobrazovat obrázky. Pokud ovládací prvek, který chcete použít, není v seznamu dostupných ovládacích prvků, můžete ho přidat do seznamu a pak ho vybrat. Další informace najdete v tématu [Přidání vlastních ovládacích prvků do okna zdroje dat](../data-tools/add-custom-controls-to-the-data-sources-window.md).

## <a name="see-also"></a>Viz také
 [Vytvoření vazby ovládacích prvků WPF k datům v sadě Visual Studio](../data-tools/bind-wpf-controls-to-data-in-visual-studio1.md)
