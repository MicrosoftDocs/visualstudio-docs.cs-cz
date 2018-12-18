---
title: Vytvoření vazby ovládacích prvků k obrázkům z databáze
ms.date: 11/04/2016
ms.topic: conceptual
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
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: d93ca95a67bc3816d8d65a799282dc6c7969e093
ms.sourcegitcommit: 81e9d90843ead658bc73b30c869f25921d99e116
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/26/2018
ms.locfileid: "52304909"
---
# <a name="bind-controls-to-pictures-from-a-database"></a>Vytvoření vazby ovládacích prvků k obrázkům z databáze

Můžete použít **zdroje dat** okno vytvořit vazbu bitovou kopii do databáze na ovládací prvek ve vaší aplikaci. Například můžete vytvořit vazbu obrázku, který má <xref:System.Windows.Controls.Image> ovládací prvek v aplikaci WPF nebo na <xref:System.Windows.Forms.PictureBox> ovládacího prvku v aplikaci Windows Forms.

Obrázky v databázi jsou většinou uložena jako pole bajtů. Položky v **zdroje dat** nastaveno okno, které jsou uloženy jako pole bajtů mít pod kontrolou zadejte **žádný** ve výchozím nastavení, protože pole bajtů může obsahovat cokoli od jednoduchých pole bajtů na spustitelný soubor velké aplikace. Chcete-li vytvořit ovládací prvek vázaný na data pro položku pole bajtů v **zdroje dat** okna, která představuje obrázek, je nutné vybrat ovládacího prvku k vytvoření.

Následující postup předpokládá, že **zdroje dat** okno je již naplněný položku, která je vázána na bitové kopie.

## <a name="to-bind-a-picture-in-a-database-to-a-control"></a>K vytvoření vazby obrázek v databázi do ovládacího prvku

1.  Ujistěte se, že chcete přidat ovládací prvek na návrhové ploše je otevřený Návrhář WPF nebo Návrhář formulářů Windows.

2.  V **zdroje dat** okna, rozbalte položku požadovanou tabulku nebo objektu zobrazíte její sloupce nebo vlastnosti.

   > [!TIP]
   > Pokud **zdroje dat** okno není otevřeno, otevřete ho tak, že vyberete **zobrazení** > **ostatní Windows** > **zdroje dat**.

3.  Vyberte sloupec nebo vlastnost, která obsahuje image data a vyberte jednu z následujících ovládacích prvků z jeho ovládací prvek rozevírací seznam:

    - Pokud je otevřený Návrhář WPF, vyberte **Image**.

    - Pokud je otevřený Návrhář formulářů Windows, vyberte **PictureBox**.

    - Alternativně můžete vybrat jiného ovládacího prvku, který podporuje datovou vazbu a, která můžete zobrazit obrázky. Pokud není ovládací prvek, který chcete použít v seznamu dostupných ovládacích prvků, můžete ho přidat do seznamu a vyberte tuto možnost. Další informace najdete v tématu [přidání vlastních ovládacích prvků do okna zdroje dat](../data-tools/add-custom-controls-to-the-data-sources-window.md).

## <a name="see-also"></a>Viz také:

- [Vytvoření vazby ovládacích prvků WPF k datům v sadě Visual Studio](../data-tools/bind-wpf-controls-to-data-in-visual-studio.md)